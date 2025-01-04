---
title: 'Overview of Microsoft Roslyn – The first compiler-as-service product.'
date: 2013-08-19T21:00:00.000-05:00
draft: false
url: /2013/08/overview-of-microsoft-roslyn-first.html
tags: 
- Microsoft Roslyn
- Syntax Trees
- Compilers
---

### Introduction

From developer perspective, compilers are black boxes -- source code goes in one end, magic happens in the middle, and object files or assemblies come out the other end. During their job, compilers build up a deep understanding of our code. For decades this valuable information was unreachable.

The [Roslyn project](http://msdn.microsoft.com/en-us/vstudio/roslyn.aspx "Microsoft® “Roslyn” CTP") aims to open compilers for developers and offer it as services. Through Roslyn, compilers become services with APIs that can be used for code related tasks in your tools and applications.

In order to understand the APIs that Roslyn offers, we need to understand the general compiler phases:

1.  **The parse phase** where source is tokenized and parsed into syntax that follows the language grammar.
2.  **The declaration phase** where declarations from source and imported metadata are analyzed to form named symbols.
3.  **The binding phase** where identifiers in the code are matched to symbols.
4.  **The emitting phase** where all the information built up by the compiler is emitted as an assembly.

For each phase of these phases, Roslyn provides a set of APIs to access its services and an object model that allow access to the information at that phase.

1.  The parsing phase is exposed as a syntax tree
2.  The declaration phase as a hierarchical symbol table
3.  The binding phase as a model that exposes the result of the compiler’s semantic analysis
4.  The emit phase as an API that produces IL byte codes.

[![image](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEigm8ZflgjuRBH1fUhjMnrEHnWS72bZ2o52_i1qSCd_5ayccne6K7S4ZB1rxGbGqPPBPiCH2-tawEhu0qNNoT8A-CJ9tdYWPPUEhgEobj7HADy9J_6FBHvrZHkjk7Vd6jbs_EbE_oMuqg/?imgmax=800 "image")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjjkcQZnD8Dr-ke1q3pSIVNaumaJyVFZJyDSB0wnuEkCste7jPWkqlfCCIVzffoNUDCBxpkpJVZMPElFzVhcyMhaFTQdOjdgJjupq4dvKg1Mt8lxGs2LHYlIf9nmA0hjv2HVOpwHYa-sQ/s1600-h/image%25255B1%25255D.png)

### Rosyln API Layers

[![image](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhocT_STU2BmUA5tHTHJ0DBoEDaMeeJJ26pCqV6Il1TY1a_UObJCdP0nFf96U7NEEQoA8UcOJf9D-JNg0JWyJkhpFW7b9CGvoYnhlejrXvWHehntiZTnmMIN599lE0jqcbNJKaDcGTQ5Q/?imgmax=800 "image")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgLXgjHPvpjAwJ71PbPYlppU-cAkqGPT6i8jV8uEve50At3ahH3LV_TDoonQVm4aMInGsRrfoR0vcYAFHvhnBT2sEnNYla8mDnmTNEajMrbAQbZd8Zoc1A1uvIm0AOhPJOfMVZ6GDjoOw/s1600-h/image%25255B13%25255D.png)

1.  **Compiler APIs** contains a representation of a single invocation of a compiler (including assembly references, compiler options, and source code files) which provides the object models that corresponds to the compiler pahases.
    1.  **Scripting APIs** represents a runtime execution context for C# or VB piece of code. It contains a scripting engine that allows evaluation of expressions and statements as top-level constructs in programs.
2.  **Services APIs** represents the starting point for doing code analysis and refactoring over entire solutions by organizing all the information about the projects in a solution into single object model, offering you direct access to the compiler layer object models without needing to parse files, configure options or manage project to project dependencies. In addition, the services layer surfaces a set of commonly used APIs used when implementing code analysis and refactoring tools that function _within a host environment_ like the Visual Studio IDE.
3.  **Editor Services APIs** allows a user to easily extend Visual Studio IDE features (such as IntelliSense, refactorings, and code formatting). This layer has a dependency on the Visual Studio text editor and the Visual Studio software development kit (SDK).

### Working with Syntax

The fundamental data structure exposed by the Compiler APIs is the syntax tree. It represents the lexical and syntactic structure of source code, No part of the source code is understood without it first being identified. These trees enable tools to manipulate source code without editing it as text.

#### Syntax Trees Attributes

Syntax trees have three key attributes:

1.  **Full fidelity** which means that the syntax tree contains every piece of information found in the source text, every grammatical construct, every lexical token, and everything else in between including whitespace, comments, and preprocessor directives.
2.  **Round-trippable** which means that it can be traced back to the text it was parsed from and get the text representation of the sub-tree rooted at that node. This means that syntax trees can be used as a way to construct and edit source text. By creating a tree you have by implication created the equivalent source code, and by editing a syntax tree, making a new tree out of changes to an existing tree, you have effectively edited the source code.
3.  **Immutable and thread-safe which** means that after a tree is obtained, it is a snapshot of the current state of the code, and never changes. This allows multiple users to interact with the same syntax tree at the same time in different threads without locking or duplication.

#### Syntax Tree Elements

Each syntax tree is made up of _nodes, tokens,_ and _trivia._

*   **Syntax Nodes**: the primary elements of syntax trees. It represent syntactic constructs such as declarations, statements, clauses, and expressions. They are non-terminal nodes in the syntax tree, which means they always have other nodes and tokens as children. Each category of syntax nodes is represented by a separate class derived from _SyntaxNode_.

*   _Parent_ property returns the node parent.
*   _ChildNodes()_ returns a list of child nodes in sequential order based on its position in the source text. This list does not contain tokens.
*   _DescendantNodes(), DescendantTokens(), and DescendantTrivia()_ returns a list of child nodes in sequential order based on its position in the source text.
*   Each syntax node subclass exposes all the same children through strongly typed properties.

*   _BinaryExpressionSyntax_ node class

*   Property _Left/Right_ of type _ExpressionSyntax_
*   Property _OperatorToken_ of type _SyntaxToken_

*   IfStatementSyntax node class

*   Optional property _ElseClauseSyntax_ which returns null if the child is not present.

*   **Syntax Tokens** are the terminals of the language grammar, representing the smallest syntactic fragments of the code. They are never parents of other nodes or tokens. Syntax tokens consist of keywords, identifiers, literals, and punctuation.
*   **Syntax Trivia** represent the parts of the source text that are largely insignificant for normal understanding of the code, such as whitespace, comments, and preprocessor directives. Because trivia are not part of the normal language syntax and can appear anywhere between any two tokens, they are not included in the syntax tree as a child of a node. you can access them through token’s _LeadingTrivia_ or _TrailingTrivia_ collections.
*   **Spans** In order to make each node knows its position within the source text, each node has two properties of type _TextSpan_. A TextSpan object is the beginning position and a count of characters, both represented as integers. Each node has two TextSpan properties:

*   The _Span_ property is the text span from the start of the first token in the node’s sub-tree to the end of the last token. This span does not include any leading or trailing trivia.
*   The _FullSpan_ property is the text span that includes the node’s normal span, plus the span of any leading or trailing trivia.

*   **Kinds** Each node, token, or trivia has a _Kind_ property, of type _SyntaxKind_, that identifies the exact syntax element represented. The Kind property allows for easy disambiguation of syntax node types that share the same node class.
*   **Errors** When the parser encounters code that does not conform to the defined syntax of the language, it uses one of two techniques to create a syntax tree.

*   If the parser expects a particular kind of token, but does not find it, it may insert a _missing token_ into the syntax tree in the location that the token was expected. A missing token represents the actual token that was expected, but it has an empty span, and its _IsMissing_ property returns true.
*   The parser may skip tokens until it finds one where it can continue parsing. In this case, the skipped tokens that were skipped are attached as a trivia node with the kind _SkippedTokens_.

In this post we explored Microsoft Roslyn, an interesting product that offer the compiler as a service and opens a lot of doors in front of developers to develop code-focused tools and applications. In later posts we will gradually show Roslyn in action.