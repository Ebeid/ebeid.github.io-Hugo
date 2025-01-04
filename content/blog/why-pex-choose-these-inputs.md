---
title: 'Why Pex Choose These Inputs'
date: 2013-04-25T03:00:00.000-05:00
draft: false
url: /2013/04/why-pex-choose-these-inputs.html
tags: 
- Microsoft Pex
---

In the example we gave in the previous post, it may seem that Pex chose random numbers as inputs for the Triang() method but it is not. But also its not all possible values for the inputs.

Actually, Pex generates test inputs by analyzing your program code, so it is called whitebox test generation (as opposed to blackbox test generation). For every statement in the code, Pex will eventually try to create a test input that will reach that statement. Pex will do a case analysis for every conditional branch in the code—for example, if statements, assertions, and all operations that can throw exceptions.

In other words, the number of test inputs that Pex generates depends on the number and possible combinations of conditional branches in the code (if interested to know more about that, search for [symbolic execution](http://en.wikipedia.org/wiki/Symbolic_execution)). Pex operates in a feedback loop: it executes the code multiple times and learns about the program behavior by monitoring the control and data flow.

After each run, Pex does the following:

*   Chooses a branch that was not covered previously.
*   Builds a constraint system that describes how to reach that branch.
*   Uses a constraint solver to determine new test inputs that fulfill the constraints, if any exist.

The test is executed again with the new inputs, and the process repeats. On each run, Pex might discover new code and dig deeper into the implementation. In this way, Pex explores the behavior of the code. 

Because our code doesn’t have any conditions that test zero length sides, Pex generated zero an input and also shows that our program is defective (because it considers a triangle with (0,0,0) as equilateral and (1,0,1) as isosceles). If we added the following lines of code after declaring triOut and before doing anything.

```
              
// A quick confirmation that it's a valid triangle              
if (Side1 <= 0 || Side2 <= 0 || Side3 <= 0)        
{  
 triOut = 4;  
 return (triOut);  
}  

```  

You will get a different set of test inputs from Pex that reveal more code path combinations.

  

[![ConsoleApplication2 - Microsoft Visual Studio_2013-04-24_13-06-48](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiTgNIXaBamP7OmmVOYoA_-E3tXask4iMLstkVgJBZrMp8qIgRKx-XQ6AGTKMBwyIbsXR1BuSThqQjXSq4LZYNXZJrdOVyDgBDK6M2o2_MFrC_S_GMRqx6Au_FDvNMqnDoOWx2EhA8vTw/?imgmax=800 "ConsoleApplication2 - Microsoft Visual Studio_2013-04-24_13-06-48")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjxh2KvPB7AKEx9pwoU-FRkma7sMJ65HhhsOCwsYBbuOnvJqLATul4gyLvdirQ9vAk6MZaQHo6z5k2xjzW8xlJi4Vra4Gv3o2zvdsRR6F3PzKBNXgSQTN65slJqEgOdkOz_KxjuAtmwHw/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-24_13-06-48%25255B3%25255D.jpg)

  

We mentioned before that pex generates test input by performing a symoblic analysis of the code under test. You can use the method **GetPathConditionString** of the **PexSymbolicValue** class to obtain a textual representation of the current path condition, a predicate (condition) that characterizes an execution path. The **ToString** method of **PexSymbolicValue** class gives you a textual representation of how a value was derived from the test input provided. To do so, add reference to Pex Framework dll (located at "C:\\Program Files\\Microsoft Moles\\PublicAssemblies\\Microsoft.Pex.Framework.dll"). Add **_using Microsoft.Pex.Framework;_** to your code then add the following code anywhere in your code to get details about the code path at that point.

```
  
 PexObserve.ValueForViewing("Condition", PexSymbolicValue.GetPathConditionString());  
 PexObserve.ValueForViewing("Return Value", PexSymbolicValue.ToString(Triang(1, 1, 1)) );  

```  

Here I added it into the Triang() method we used before. Run Pex and you will see the new columns added to the results populated with conditions that led to .

  

[![ConsoleApplication2 - Microsoft Visual Studio_2013-04-25_11-49-50](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhLzc2HFYSUpl9taRgSYa0aqpTJpEv2p7b3XtUWeM3ZtLaiNDNZhm2sQdl62w_NRzGoH03-1Vmj-t-k-u5tHaIT2jpVj7ZoFa_pvD_-pL9-Al0erDyGiYNRa8wqn9qR13yRXNBtR9ZXEg/?imgmax=800 "ConsoleApplication2 - Microsoft Visual Studio_2013-04-25_11-49-50")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjFYXoy7LVrlzCVGf7OgDXx_oUuiJ_kQvodyCEWLdF10f3LqHfg16Pb5O3y_NLFm9qHkXHL6-A8i1QXszuRCLY0QIlD84tM0CVn7I-9TeuVRydnLhLGf4Rv98pvDW-r-e88BQa1ahs3hQ/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-25_11-49-50%25255B4%25255D.jpg)

  

**ToRawString** method and **GetRawPathConditionString** method return expressions representing symbolic values and the path condition, formatted as [S-expressions](http://en.wikipedia.org/wiki/S-expression).

  

Method PexObserve.ValueForViewing can also be used to display the value picked by Pex for any variable at any point in your code.

  

The same engine Pex uses is now available as part of [Code Digger](http://research.microsoft.com/en-us/projects/codedigger/default.aspx), a Visual Studio 2012 extension. We will talk about it in a future post.