---
title: 'Syntax Analysis using Microsoft Roslyn'
date: 2013-08-20T15:49:00.000-05:00
draft: false
url: /2013/08/getting-started-with-microsoft-roslyn.html
tags: 
- Microsoft Roslyn
- Syntax Trees
- Compilers
---

In a previous [post](http://ebeid-soliman.blogspot.com/2013/08/overview-of-microsoft-roslyn-first.html) we talked about Microsoft [Roslyn](http://msdn.microsoft.com/en-us/vstudio/roslyn.aspx "Microsoft® “Roslyn” CTP"). In this post will get our hands dirty with Roslyn syntax analysis in order to develop our first code-focused program. We will see how the SyntaxTree of HelloWorld program look like and how we can traverse and query it.

The **Syntax API** exposes the syntax trees the compilers use to understand Visual Basic and C# programs. They are produced by the same parser that runs when a project is built or a developer hits F5. The four primary building blocks of syntax trees are:

*   The **SyntaxTree** class, an instance of which represents an entire parse tree.
*   The **SyntaxNode** class, instances of which represent syntactic constructs such as declarations, statements, clauses, and expressions.
*   The **SyntaxToken** structure, which represents an individual keyword, identifier, operator, or punctuation.
*   And lastly the **SyntaxTrivia** structure, which represents syntactically insignificant bits of information such as the whitespace between tokens, preprocessor directives, and comments.

### Traversing Syntax Trees

First, download Microsoft Roslyn CTP from [here](http://www.microsoft.com/en-us/download/details.aspx?id=34685 "Microsoft Download Center"). and Install it.You will need [Visual Studio 2012](http://go.microsoft.com/fwlink/?linkid=255983) and [Visual Studio 2012 SDK](http://go.microsoft.com/?linkid=9810482) in order to install Roslyn.

Now open your Visual Studio 2012 and create a new Console Application project. Add the following to your project references

### [![Reference Manager - RoslynDemo1_2013-08-19_15-25-47](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiL9nDDypBvR5aSH1yTHC9Pg3qUBmyuZzoESTX0ZAIRt3duLZnUat27I7JSoH00lZrBBLWkfuk49i6BmlzT_bMFmrD6bs_Y5iS0BFknDpw5SxTl3rsRsM5ymOfyRYc3S-8xCxTuejZgPg/?imgmax=800 "Reference Manager - RoslynDemo1_2013-08-19_15-25-47")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEguF3b9tYuwvwMfE2vvp0KL_YIaq28_oor3VHGE7dlU3UGcMMoH52QSpU273WVOwLpnNj9V76tT-PTIPqq086kh_xgD-Z8VnpYmEr0PoyFErG3tuOkVvs9UFYbZjtb3H2yaCQPtIs1X_w/s1600-h/Reference%252520Manager%252520-%252520RoslynDemo1_2013-08-19_15-25-47%25255B3%25255D.png)

Now edit your code to look like:

```
using System;  
using System;  
using Roslyn.Compilers;  
using Roslyn.Compilers.CSharp;  
  
namespace RoslynDemo1  
{  
    class Program  
    {  
        static void Main(string\[\] args)  
        {  
            SyntaxTree tree = SyntaxTree.ParseText(  
                @"using System;  
   
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
  
            foreach (SyntaxNode node in tree.GetRoot().ChildNodesAndTokens())  
                PrintSyntaxTree(node);  
  
            Console.ReadLine();  
        }  
        static void PrintSyntaxTree(SyntaxNode node)  
        {  
            if (node != null)  
            {  
                Console.WriteLine(node.Kind + " | " + node.ToString());  
                foreach (SyntaxNode child in node.ChildNodes())  
                    PrintSyntaxTree(child);  
            }  
        }  
    }  
}  

```  

Now, run our program. You should see an output similar to the following:

  

[![fileFProjectsRoslynDemo1RoslynDemo1binDebugRoslynDemo1.EXE_2013-08-20_15-24-06](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEikuHdEXKinbsZYxeFu1woRzzw1Y2mgnsg1oHgJ8l5h8j7QIqB49kUneQ4EcqDqomKsWYfyT4fetvKqJi0CO7wRfCtYL4mRyfHAOMjJs0aQ8iXtQeB8f929sckmpAgwFFeiBvW668PPfw/?imgmax=800 "fileFProjectsRoslynDemo1RoslynDemo1binDebugRoslynDemo1.EXE_2013-08-20_15-24-06")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg_fDDkBlx8mZ1LzZrcbJnWI2uoiFbiado1WAKA5ANgDVa29kpNv7XeX2SoBAfgm87xd1Wq1Qy32an7ZqqkLVH2QBTYeVUN2D8CcbmJundWElkJ-aBjopSP6s3-27gcUb7zGTFUkIC6tw/s1600-h/fileFProjectsRoslynDemo1RoslynDemo1binDebugRoslynDemo1.EXE_2013-08-20_15-24-06%25255B3%25255D.png)

  

Now let’s explain what we already did. First, we included the needed namespaces. The common Syntax APIs are found in the Roslyn.Compilers and the Roslyn.Compilers.Common namespace, while the language specific Syntax APIs are found in Roslyn.Compilers.CSharp and Roslyn.Compilers.VisualBasic.

  

Second, we tried to get a syntax tree corresponding to our HelloWorld program using the _SyntaxTree.ParseText_ function, which produces a syntax tree by parsing the passed source code.

  

Third, in order to traverse the syntax tree we get its root, then get its child nodes. Then loop on these child nodes and their children recursively to print its kind and the string representation. C# node kind is on of the kinds in enum _Roslyn.Compilers.CSharp.SymbolKind_.

  

Inside the PrintSyntaxTree method, by playing in the order of node printing and the recursive call, you can apply your tree traversal logic. You can also inspect specific elements of the tree:

```
var root = (CompilationUnitSyntax)tree.GetRoot();   
var helloWorldDeclaration = (NamespaceDeclarationSyntax)root.Members\[0\];  
var programDeclaration = (TypeDeclarationSyntax)helloWorldDeclaration.Members\[0\];  
var mainDeclaration = (MethodDeclarationSyntax)programDeclaration.Members\[0\];  
var argsParameter = mainDeclaration.ParameterList.Parameters\[0\];  
Console.WriteLine(argsParameter.ToString() );  

```  

### Query Methods

  

In addition to traversing syntax trees you can also explore the syntax tree using the query methods defined on _SyntaxNode_. These methods are similar to XPath. You can also use these methods with LINQ to quickly find things in a tree. For example, the following statements uses a LINQ expression and the **DescendantNodes** method to locate the same parameter as in the previous example:

```
            var firstParameters = from methodDeclaration in root.DescendantNodes()  
                                                    .OfType()  
                                  where methodDeclaration.Identifier.ValueText == "Main"  
                                  select methodDeclaration.ParameterList.Parameters.First();  
  
            var argsParameter2 = firstParameters.Single();  
            Console.WriteLine(argsParameter2.ToString());  

```  

### SyntaxWalkers

  

If you want to find all nodes of a specific type in a syntax tree, for example, every property declaration in a file, you can do that by extending the _SyntaxWalker_ class and overriding the _VisitPropertyDeclaration_  method, you can process every property declaration in a syntax tree without knowing its structure beforehand.

  

Now let’s implement, as an example, a SyntaxWalker that examines the entire syntax tree and collects any using directives it find which aren’t importing a System namespace.

  

Create a new C# Console application and edit it to look like:

```
using System;  
using Roslyn.Compilers;  
using Roslyn.Compilers.CSharp;  
  
namespace RoslynDemo2  
{  
    class Program  
    {  
        static void Main(string\[\] args)  
        {  
            SyntaxTree tree = SyntaxTree.ParseText(  
@"using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Roslyn.Compilers;  
using Roslyn.Compilers.CSharp;  
   
namespace TopLevel  
{  
    using Microsoft;  
    using System.ComponentModel;  
   
    namespace Child1  
    {  
        using Microsoft.Win32;  
        using System.Runtime.InteropServices;  
   
        class Foo { }  
    }  
   
    namespace Child2  
    {  
        using System.CodeDom;  
        using Microsoft.CSharp;  
   
        class Bar { }  
    }  
}");  
  
            var root = (CompilationUnitSyntax)tree.GetRoot();  
        }  
    }  
}  

```  

As you noticed, this source text contains **using** directives scattered across four different locations: the file-level, in the top-level namespace, and in the two nested namespaces.

  

Now, add a new class to your project and edit it to look like the next code. Basically we inherit from the _SyntaxWalker_ class, and over the _VisitUsingDirective_ method. This method is called by _Visit_ method, which recursively visits a node and each of its children. VisitUsingDirective method is called for using directives only, inside it we collect the namespaces that starts with “System.” but not equal to “System”.

```
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Roslyn.Compilers;  
using Roslyn.Compilers.CSharp;  
  
namespace RoslynDemo2  
{  
    class myWalker : SyntaxWalker     
    {  
        public readonly List Usings = new List();  
  
        public override void VisitUsingDirective(UsingDirectiveSyntax node)  
        {  
            if (node.Name.GetText().ToString() != "System" &&  
                !node.Name.GetText().ToString().StartsWith("System."))  
            {  
                this.Usings.Add(node);  
            }  
        }  
    }  
}
```  

Now let’s go back to the _Main_ method and use our walker by adding the following code snippet to the end of Main method. Basically it passes the syntax tree root to _myWalker.Visit_ method, which internally call the _VisitUsingDirective_ method. Then we loop and print the collected usings.

  

When you run your program, you should see an output similar to the following:

  

[![fileFProjectsRoslynDemo2RoslynDemo2binDebugRoslynDemo2.EXE_2013-08-21_14-30-03](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj0j45bLI4Z8n9mrb59ZvyvAN1j0-7orNy-yiZsj1XCwcEUudYUSKrjQAr8hivQuBVfK45SOcHmP9E0gC-s9CD_SYEQuuEgZjhXj2mj_uNMlVfPEdnEYl4et7-8nMsJxveVea0IGO59KQ/?imgmax=800 "fileFProjectsRoslynDemo2RoslynDemo2binDebugRoslynDemo2.EXE_2013-08-21_14-30-03")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi3ztSpRMD3_GkKRYHcGryLCG7GEycYoRG5Wz_aAc9trP70ARPdfoJaqR_oBWGEUfL5L5scp3IaPLsi7OQNpXNITdtrgavbHalryjMursMWvZasSyjo9zdqn_8I_GzZxJC9e9VkiWHGLg/s1600-h/fileFProjectsRoslynDemo2RoslynDemo2binDebugRoslynDemo2.EXE_2013-08-21_14-30-03%25255B2%25255D.png)

  

In this post we gave a quick example about obtaining a SyntaxTree of HelloWorld program and explored its nodes. We also built a SyntaxWalker that walk the syntax tree and collect the nodes of our interest only. Later we will see how to fully manipulate SyntaxNodes and SyntaxTrees.