---
title: 'Type checking in programming languages'
date: 2009-03-04T08:44:00.001-06:00
draft: false
url: /2009/03/type-checking-in-programming-languages.html
---

To discuss type checking in programming languages we have to define type checking. Simply,**Type checking** is how type errors are checked.

Type checking could happen at compile-time or at run-time. When type checking happens at the compile-time it is called **Static Type Checking.** When type checking happens at the run-time it is called **Dynamic Type Checking.**

Programming Languages differs in

*   when they check types.
*   Were it enforces types or not.

Based on these two factors, programming languages could be classified from the type checking perspective into the following classes:

**Statically Typed Languages**

> In these languages, types are fixed at compile time. Most statically typed languages enforce this by requiring you to declare all variables with their data types before using them
> 
> C, Java, and C# are statically typed languages.

**Dynamically Typed Languages**

> In these languages, types are discovered at execution time; the opposite of statically typed languages. These languages figure out what type a variable is when you first assign it a value.
> 
> VBScript and Python are dynamically typed languages.

**Strongly Typed Languages**

> In these languages, types are always enforced. If you have an integer, you can’t treat it like a string without explicitly converting it.
> 
> Java and Python are strongly typed languages.

**Weakly Typed Languages**

> In these languages, types may be ignored; the opposite of strongly typed languages. In VBScript, you can concatenate the string ‘12’ and the integer 3 to get the string ‘123’, then treat that as the integer 123, all without any explicit conversion.
> 
> VBScript is weakly typed language.

Programming languages could be classified based on many other factors and differences which we may discuss in further posts.