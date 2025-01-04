---
title: 'Syntax Modification using Microsoft Roslyn'
date: 2013-08-23T17:56:00.000-05:00
draft: false
url: /2013/08/getting-started-with-microsoft-roslyn_9468.html
tags: 
- Microsoft Roslyn
- Syntax Trees
---

In the previous two posts we just used the analysis capabilities of Microsoft [Roslyn](http://msdn.microsoft.com/en-us/vstudio/roslyn.aspx "Microsoft® “Roslyn” CTP"). In other words, we only get information about the code under inspection, we never changed it. In this post we going to change the code through Roslyn.

Before we start we need to highlight that data structures that represent code under inspection in Roslyn APIs are immutable. This means that it cannot be changed after they are created (in order to safely share them between tools). This applies to syntax trees, compilations, symbols, semantic models, and every other data structure in the Roslyn API. Instead of modification, new objects are created based on specified differences to the old ones.

### Creating and Modifying Trees

We used _SyntaxTree_ before to create syntax trees from a code snippet. For creating a syntax tree bit-by-bit, you have to compose syntax nodes hierarchically in a bottom-up fashion. To create _SyntaxNodes_ you must use the _Syntax_ class factory methods. For each kind of node, token, or trivia there is a factory method which can be used to create an instance of that type.

In the following example we going to replace a using directive by a new one we create.

```
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Roslyn.Compilers;  
using Roslyn.Compilers.CSharp;  
using Roslyn.Services;  
using Roslyn.Services.CSharp;  
  
namespace RoslynDemo4  
{  
    class Program  
    {  
        static void Main(string\[\] args)  
        {  
            SyntaxTree tree = SyntaxTree.ParseText(  
@"using System;  
using System.Collections;  
using System.Linq;  
using System.Text;  
   
namespace HelloWorld  
{  
    class Program  
    {  
        static void Main(string\[\] args)  
        {  
            Console.WriteLine(""Hello, World!"");  
        }  
    }  
}");  
  
            var root = (CompilationUnitSyntax)tree.GetRoot();  
            // Get the old Using directive \[using System.Collections;\]  
            var oldUsing = root.Usings\[1\];  
  
            // Construct the new Using directive  
            NameSyntax name = Syntax.IdentifierName("System");  
            name = Syntax.QualifiedName(name, Syntax.IdentifierName("Collections"));  
            name = Syntax.QualifiedName(name, Syntax.IdentifierName("Generic"));  
            var newUsing = oldUsing.WithName(name);  
  
            // Replace the old Using directive by the new Using directive  
            root = root.ReplaceNode(oldUsing, newUsing);  
  
            SyntaxTree newTree = SyntaxTree.Create(root);  
            Console.WriteLine(newTree.ToString());  
            Console.ReadLine();  
        }  
    }  
}  

```  

_NameSyntax_ is the base class for the following names that can appear in C# code:  

  
*   _IdentifierNameSyntax_ which represents simple single identifier names like **System** and _Roslyn_  
    
*   _GenericNameSyntax_ which represents a generic type or method name such as _List<int>_  
    
*   _QualifiedNameSyntax_ which represents a qualified name of the form <left-name>.<right-identifier-or-generic-name> such as _System.IO_

  

In our example we constructed a NameSyntax to represent System.Collections.Generic incrementally. Then we used the ReplaceNode method to replace the _using System.Collections;_ directive with the _using System.Collections.Generic;_ directive. We then constructed a new SyntaxTree using the modified root and print it. You should see the modified HelloWorld program:[![fileFProjectsRoslynDemo4RoslynDemo4binDebugRoslynDemo4.EXE_2013-08-23_09-38-56](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi1IuLVhZBZ6LN3WoRjDZGQPFsHwpWdJ7PbZ9HyvaszSBrvPu4cfql-tZlZgpJF7BeJzceHf73Kd4NkspNta3iRKCPAfz2PZvyRIEblt9Bw9mFnehW02qiwvBvrArX5cZUvxKwdxuDxhQ/?imgmax=800 "fileFProjectsRoslynDemo4RoslynDemo4binDebugRoslynDemo4.EXE_2013-08-23_09-38-56")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh08zTkPcT1UebAHLez2iTsFKlvGG9AnVsiDgNPMoWoyl9qqCZdRe0X337hrGekks8JVpkoXdeA9cSEhmcmkPV-wOIa5aUg2DjXFxjZUhXcVAXokpFZeQUcqdM6n4JK0oAbmes6rQ5i6w/s1600-h/fileFProjectsRoslynDemo4RoslynDemo4binDebugRoslynDemo4.EXE_2013-08-23_09-38-56%25255B4%25255D.png)

  

### Modifying Syntax Trees using SyntaxRewriters

  

In a previous [post](http://ebeid-soliman.blogspot.com/2013/08/getting-started-with-microsoft-roslyn.html "Getting started with Microsoft Roslyn Syntax Analysis") we implemented our _SyntaxWalker_. Now we going to use the same technique and implement our _SyntaxRewriter_. Both SyntaxWalker and SyntaxRewriter are subclasses of SyntaxVisitor which recursively visit every node in the syntax tree starting from the passed node. The _SyntaxRewriter_ class can be used to apply a transformation to a specific type of _SyntaxNode_**.** It is also possible  to apply a set of transformations to multiple types of _SyntaxNode_ wherever they appear in a syntax tree. It uses [depth-first search](http://en.wikipedia.org/wiki/Depth-first_search "Depth-first search [Wikipedia]") algorithm for SyntaxTree traversal.

  

In the following example we will implement our own _SyntaxRewriter_ which will replace all variable declaration types with the _var_ type. Create a new Console application and add a new class myRewriter to it. Edit the myRewriter.cs to look like:

```
using System;  
using Roslyn.Compilers;  
using Roslyn.Compilers.CSharp;  
  
namespace RoslynDemo5  
{  
    class myRewriter : SyntaxRewriter  
    {  
        private readonly SemanticModel SemanticModel;  
  
        public myRewriter(SemanticModel semanticModel)  
        {  
            this.SemanticModel = semanticModel;  
        }  
  
        public override SyntaxNode VisitLocalDeclarationStatement(LocalDeclarationStatementSyntax node)  
        {  
            // To avoid the case of multiple variables in a single declaration like the following one  
            // Type variable1 = expression1,  
            //      variable2 = expression2;  
            if (node.Declaration.Variables.Count > 1)  
            {  
                return node;  
            }  
  
            // To avoid the case of case of a declation without an initializer like the following  
            // Type variable;  
            if (node.Declaration.Variables\[0\].Initializer == null)  
            {  
                return node;  
            }  
              
            // Get the first varaible in the declation  
            VariableDeclaratorSyntax declarator = node.Declaration.Variables.First();   
            // Get the Type used in the declaration  
            TypeSyntax variableTypeName = node.Declaration.Type;  
            // Bind the Type used in the declaration to a Symbol  
            TypeSymbol variableType = (TypeSymbol)SemanticModel.GetSymbolInfo(variableTypeName).Symbol;  
            // Get the whole intialization expression  
            TypeInfo initializerInfo = SemanticModel.GetTypeInfo(declarator.Initializer.Value);  
            if (variableType == initializerInfo.Type)  
            {  
                // Constructing a new Type with the same leading/trailing in the old type to maintain vertical whitespace and indentation  
                TypeSyntax varTypeName = Syntax.IdentifierName("var").  
                    WithLeadingTrivia(  
                    variableTypeName.GetLeadingTrivia()  
                    ).  
                    WithTrailingTrivia(  
                    variableTypeName.GetTrailingTrivia()  
                    );  
                // Do the replacement and return the new node  
                return node.ReplaceNode(variableTypeName, varTypeName);  
            }  
            else  
            {  
                return node;  
            }  
        }  
    }  
}  
  

```  

myRewriter class is simply inheriting from _SyntaxRewriter_ class and implments the _VisitLocalDeclarationStatment()_ method. This method is called by the _Visit_ method on _SyntaxRewriter_, which recursively visits a node and each of its children. The _VisitLocalDeclarationStatment_ method is called on local declaration statements only. It tokes the starting SyntaxNode, if you passed the tree root (as we will do) it will visit the the local declaration statements that exists in the whole program.

  

Our rewriter takes the semantic model under inspection in the constructor.

  

In the _VisitLocalDeclarationStatment_ method we check the declaration statement to filter out the cases that are not within our interest. For these cases we return the node unchanged.

  

For the cases we interested in, we retrieve the variable and the type used for its declaration. Get a symbol for the type and the whole initialization expression.

  

Then we check that the type used in the declaration is the type used in the initialization to avoid the situations where the declaration may be casting the initializer expression to a base class or interface. Removing the explicit type in these cases would change the semantics of a program.

  

Then we construct a new TypeSyntax representing the var type with any leading or trailing tivia (white spaces and tabs) to conserve the indentation. Then we replace the node and return the new node.

  

Let’s go back to our Main method in the Program.cs file. In order to use the myRewriter class, edit the Main method to look like:

```
 static void Main(string\[\] args)  
        {  
            // Create a test Compilation of our current project  
            Compilation test = CreateTestCompilation();  
  
            // Loop on each SyntaxTree in the Compilation  
            foreach (SyntaxTree sourceTree in test.SyntaxTrees)  
            {  
                // Get the tree SemanticModel  
                SemanticModel model = test.GetSemanticModel(sourceTree);  
                // intialize myRewriter using the tree SemanticModel  
                myRewriter rewriter = new myRewriter(model);  
                // put our rewriter into action  
                SyntaxNode newSource = rewriter.Visit(sourceTree.GetRoot());  
  
                if (newSource != sourceTree.GetRoot())  
                    Console.WriteLine(newSource.GetText().ToString());  
                Console.ReadLine();  
            }  
        }  

```  

Here we create a test _Compilation_ using CreateTestCompilation method, which we will add soon. We then loop for each _SyntaxTree_ in this test Compilation. For each SyntaxTree we get the _SemanticModel_ and pass it to our myRewriter constructor. Then we call the _Visit()_ method on the SyntaxTree root. This will cause our VisitLocalDeclarationStatement method to be called and do its syntax transformation task. If the new SyntaxTree is different than the old SyntaxTree, this means that we did syntax modifications and we print the new code.

  

Now it add the following method to your code inside Program.cs.

```
private static Compilation CreateTestCompilation()  
        {  
            SyntaxTree programTree = SyntaxTree.ParseFile(@"..\\..\\Program.cs");   
            SyntaxTree rewriterTree = SyntaxTree.ParseFile(@"..\\..\\myRewriter.cs");  
  
            List sourceTrees = new List();  
            sourceTrees.Add(programTree);  
            sourceTrees.Add(rewriterTree);  
  
            MetadataReference mscorlib = MetadataReference.CreateAssemblyReference("mscorlib");  
            MetadataReference roslynCompilers = MetadataReference.CreateAssemblyReference("Roslyn.Compilers");  
            MetadataReference csCompiler = MetadataReference.CreateAssemblyReference("Roslyn.Compilers.CSharp");  
  
            List references = new List();  
            references.Add(mscorlib);  
            references.Add(roslynCompilers);  
            references.Add(csCompiler);  
  
            return Compilation.Create("TransformationCS", null, sourceTrees, references);  
  
        }
```  

This method basically creates two _SyntaxTree_s of our project code. Then make a list of the required references for these source code files. Then it sum it all in the factory method _Compilation.Create()_ and return the resulted Compilation object.

  

When you run the project, you will see a modified version of the Program.cs file. Notice that our myRewriter class replaced the type used in all variables declarations to be of type _var_.

  

[![fileFProjectsRoslynDemo5RoslynDemo5binDebugRoslynDemo5.EXE_2013-08-23_13-28-40](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjecm38p6yJ4rvSvjZqrlsw1T0VUAFksT42PdSvpALdp29KePkpeQjP_IxbJQESqKO1GIJEQMYgFSdYwwF3HC-onhkB4oBfeR-6qU4hAlRH6aApq0ZkpXLGibybZkvz2f1G5WH4X9Ij8g/?imgmax=800 "fileFProjectsRoslynDemo5RoslynDemo5binDebugRoslynDemo5.EXE_2013-08-23_13-28-40")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiXUCVs_w6NYB1tIy3qbWHlgGzTGn-TIDUPpJHuJhfkcU5bqHTSAlw6gyt1ZnYsF5oX6ta0fdq5Yhz6t67xYIxovK6RJTg6E_hWBtJEpoXaEg39pTrzSsZhRKrZjPb4eqGVBZ4hEG708Q/s1600-h/fileFProjectsRoslynDemo5RoslynDemo5binDebugRoslynDemo5.EXE_2013-08-23_13-28-40%25255B4%25255D.png)

  

pressing Enter will bring the modified version of myRewriter.cs file, which have the same kind of change.

  

[![fileFProjectsRoslynDemo5RoslynDemo5binDebugRoslynDemo5.EXE_2013-08-23_17-33-15](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg8_PvcB4HxkkYzafS62Q5tA71r8EsxKd_eEaIoxH6_RAcaZZcf7p_mEJzqCpjwo6wVlydJ3QHolgNAqE5Z-a16XAkLHMixsPYivG2tEU_fJ1omaCutBMnIZ-T6rVlGg5oemmivMfrhEQ/?imgmax=800 "fileFProjectsRoslynDemo5RoslynDemo5binDebugRoslynDemo5.EXE_2013-08-23_17-33-15")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg6DzlpmKEKsZO1My-03wFEmonzExZGdKutESfbfXkQ4NkQEmsPigijbX8EvQrqJFWEGFQQMKetHEHz_hhApqtTAAlv-HeROi_GMnAWlRoLULDBIORwSeYqnLUUo0yRxDwFLj7Gy5j3tg/s1600-h/fileFProjectsRoslynDemo5RoslynDemo5binDebugRoslynDemo5.EXE_2013-08-23_17-33-15%25255B4%25255D.png)

  
  

We have used the Roslyn Compiler APIs to write our own _SyntaxRewriter_ that searches all files in a C# project for certain syntactic pattern, analyzes the semantics of source code that matches that pattern, and transforms it.

  

Now you can grab a paper and pencil, and start designing the next big thing in refactoring tools industry :)