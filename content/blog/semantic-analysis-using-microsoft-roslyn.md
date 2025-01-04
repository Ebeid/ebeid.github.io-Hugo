---
title: 'Semantic Analysis using Microsoft Roslyn'
date: 2013-08-22T13:11:00.001-05:00
draft: false
url: /2013/08/getting-started-with-microsoft-roslyn_22.html
tags: 
- Microsoft Roslyn
- Syntax Trees
---

In a previous [post](http://ebeid-soliman.blogspot.com/2013/08/getting-started-with-microsoft-roslyn.html "Getting Started with Microsoft Rosyln Syntax Analysis") we talked about using Microsoft Rosyln Syntax API to deal with syntax text in terms of SyntaxTrees and SyntaxNodes. But as we we all know, a single source code or code snippet can’t make a useful program. 99% of the time we end up with many source code files that depend on so many externals: assembly references, namespace imports, or other code files. The meaning (semantic) of SyntaxNodes depend heavily on these externals and may change due changes in these externals even if its enclosing source code file have not been changed.

The _Compilation_ class help us deal with source text in the context of its dependents and externals. A _Compilation_ is analogous to a single project as seen by the compiler and represents everything needed to compile a Visual Basic or C# program such as assembly references, compiler options, and the set of source files to be compiled. With this context you can reason about the meaning of code. _Compilations_ allow you to find _Symbols_ – entities such as types, namespaces, members, and variables which names and other expressions refer to. The process of associating names and expressions with _Symbols_ is called _Binding_.

### Creating a Compilation

In this following example we will create a SyntaxTree for our traditional HelloWorld program. Then we created a _Compilation_ out of this _SyntaxTree_ and added a reference to MS Core Library.

```
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Roslyn.Compilers;  
using Roslyn.Compilers.CSharp;  
using Roslyn.Services;  
using Roslyn.Services.CSharp;  
  
namespace RoslynDemo3  
{  
    class Program  
    {  
        static void Main(string\[\] args)  
        {  
            SyntaxTree tree = SyntaxTree.ParseText(  
@"using System;  
using System.Collections.Generic;  
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
  
            Compilation compilation = Compilation.Create("HelloWorld")  
                             .AddReferences(MetadataReference.CreateAssemblyReference("mscorlib"))  
                             .AddSyntaxTrees(tree);  
  
            foreach (MetadataReference reference in compilation.ExternalReferences)  
                Console.WriteLine(reference.Display);  
  
            Console.ReadLine();  
        }  
    }  
}  

```  

You can supply all the syntax trees, assembly references, and options in one call or you can spread them out over multiple calls. To add the reference we just used the metadata name, which is the same name you find when you add a reference through Visual Studio’s Reference Manager.[![Reference Manager - RoslynDemo3_2013-08-22_09-54-14](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjJ_WRr_RsW749DfhmU_msIzc9caCaENjF4alD0Q75m2Q7aSIEEebgF_EQM3LFa0Td94DkGPSVkrpmeDL0_3TvcSmuj4cnqwuefEVJwIMIGtFOXW6cLZRch48eD7LETDKtEBHdzW3Pm1A/?imgmax=800 "Reference Manager - RoslynDemo3_2013-08-22_09-54-14")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjlG8hl6M60F-RXpALLD15LMJw1rPAUMhBS22zbXU46lr9CHPhbehLnsM-xaGRMj4ngWsjOcfMLWgNjFirA4W4Pc12GfdvL5u4XjLQnn7MQCAjrRBV2V_QWYMIdH5AInCEFJOomG8FhMg/s1600-h/Reference%252520Manager%252520-%252520RoslynDemo3_2013-08-22_09-54-14%25255B4%25255D.png)

  

Now when you run your program, you should get an output similar to the following:[![FProjectsRoslynDemo3RoslynDemo3binDebugRoslynDemo3.exe_2013-08-22_10-00-45](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEglpjg8gTf8C9rXZHJEDgU7x0lhAlM38ikWQVh4g_QUJHMZ9hkRsVQFca1w4YcVmeYt9QVsm62Q7KusBZdpmgtW6BgtouJBpja1XoIFGYTbzeXts_fOT9jWqqXoAeFkJScWIMNrhqfWTw/?imgmax=800 "FProjectsRoslynDemo3RoslynDemo3binDebugRoslynDemo3.exe_2013-08-22_10-00-45")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjPzoBhkHEg9vsk1187IMz6zxAUymR3gibhlaFKMFAeuwAxzU3Vfc613zLKael3WzniaLmDv_HHbyXfAQWw7pOZ2Rp2pPNll3HwjRSgiW3X3heMLEaTszN2tQJHvDCKh7c8Nmv1MdaRxw/s1600-h/FProjectsRoslynDemo3RoslynDemo3binDebugRoslynDemo3.exe_2013-08-22_10-00-45%25255B4%25255D.png)

  

### The SemanticModel

  

Once we have a _Compilation_ we can get a _SemanticModel_ for any _SyntaxTree_ in that **_Compilation_**. **SemanticModel**s can be queried to answer questions like “What names are in scope at this location?” “What members are accessible from this method?” “What variables are used in this block of text?” and “What does this name/expression refer to?”

  

In the following example we going to modify our example a little bit. We will get the semantic model of our HelloWorld program. Then use this model to get semantic Symbol that represents the first using statement (of type NameSpaceSymbol). Then we use that symbol to get a list of namespaces inside the System namespace.

```
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using Roslyn.Compilers;  
using Roslyn.Compilers.CSharp;  
using Roslyn.Services;  
using Roslyn.Services.CSharp;  
  
namespace RoslynDemo3  
{  
    class Program  
    {  
        static void Main(string\[\] args)  
        {  
            SyntaxTree tree = SyntaxTree.ParseText(  
@"using System;  
using System.Collections.Generic;  
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
  
            Compilation compilation = Compilation.Create("HelloWorld")  
                             .AddReferences(MetadataReference.CreateAssemblyReference("mscorlib"))  
                             .AddSyntaxTrees(tree);  
  
            var model = compilation.GetSemanticModel(tree);  
            var nameInfo = model.GetSymbolInfo(root.Usings\[0\].Name);  
            var systemSymbol = (NamespaceSymbol)nameInfo.Symbol;  
  
            foreach (var ns in systemSymbol.GetNamespaceMembers())  
                Console.WriteLine(ns.Name);  
            Console.ReadLine();  
        }  
    }  
}  

```  

When you run the above code you should get an output like the following:

  

[![FProjectsRoslynDemo3RoslynDemo3binDebugRoslynDemo3.exe_2013-08-22_13-23-45](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjRKVQdEUyjjXns7R1IFFR2-bleHREUsESwW5Dzs9VHVCi9DARW4VaBwU_lz-AKljxT0wyjVhpdFHQTVC2AND-ddsz2YQPCX26xCNW6fpiFlh7wSfJ1Jo12dbDYDdlyV1c17hSSk1atVA/?imgmax=800 "FProjectsRoslynDemo3RoslynDemo3binDebugRoslynDemo3.exe_2013-08-22_13-23-45")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhTS_Ac9CuyMjQsXKPpshENFEuFMrKfJdpXoBNVNVwcly0lMEMH6L7at4-2vnJHDhf_YMYhqSrG6-Sl7OYrhcyKlfwId4NgNW5gjGgZNoeOIyNxThQR_aVVK-Ni4pTOXOcuf57hSmIJ3g/s1600-h/FProjectsRoslynDemo3RoslynDemo3binDebugRoslynDemo3.exe_2013-08-22_13-23-45%25255B2%25255D.png)

  

You can also use the query methods we showed in the previous [post](http://ebeid-soliman.blogspot.com/2013/08/getting-started-with-microsoft-roslyn.html "Getting started with Microsoft Roslyn Syntax Analysis") to retrieve a certain node and then use the semantic model to get more information about that node. You could use the code below to get the node that represent the “Hello, World!” string in our code snippet, get information about its symbol type (System.String) , and even get information about the assembly that contains this type.

```
            var helloWorldString = root.DescendantNodes()  
                                       .OfType()  
                                       .First();  
            var literalInfo = model.GetTypeInfo(helloWorldString);  
            Console.WriteLine(literalInfo.Type.ContainingAssembly.BaseName);  

```  

or enumerate the public methods of the _System.String_ class

```
            var stringTypeSymbol = (NamedTypeSymbol)literalInfo.Type;  
   
            Console.Clear();  
            foreach (var name in (from method in stringTypeSymbol.GetMembers()  
                                                              .OfType()  
                               where method.ReturnType == stringTypeSymbol &&  
                                     method.DeclaredAccessibility ==   
                                                Accessibility.Public  
                               select method.Name).Distinct())  
            {  
                Console.WriteLine(name);  
            }  

```  

Somehow, we just scratched the surface of sematic analysis in this post. using both syntax and semantic analysis we can do more advanced and meaningful code focused tasks (which we will do in the next post).