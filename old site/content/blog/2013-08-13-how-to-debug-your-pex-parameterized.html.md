--- 
title: "How to debug your Pex parameterized unit tests" 
date: '2013-08-13T13:43:00.001-05:00' 
tags: 
    - Microsoft Pex 
modified_time: '2013-08-13T13:43:33.205-05:00' 
thumbnail: http://lh4.ggpht.com/-ayDx3wwvFdk/Ugp-TrSfkdI/AAAAAAAAB2I/y6x2DbrwnE0/s72-c/Options\_2013-08-13\_13-01-05\_thumb%25255B2%25255D.png?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-9074763932893251227
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/08/how-to-debug-your-pex-parameterized.html
---

We talked before about [Microsoft
Pex](http://ebeid-soliman.blogspot.com/2013/04/getting-started-with-microsoft-pex.html "Getting started with Microsoft Pex"),
and [how it choose the shown
inputs](http://ebeid-soliman.blogspot.com/2013/04/why-pex-choose-these-inputs.html "Why Pex Choose These Inputs").
We then talked more about [building blocks of parameterized unit
tests](http://ebeid-soliman.blogspot.com/2013/04/microsoft-pex-understanding-assumptions.html "Microsoft Pex: Understanding Assumptions, Assertions, and Test-Case Failures")
and its
[patterns](http://ebeid-soliman.blogspot.com/2013/05/parameterized-test-patterns-using.html "Parameterized Test Patterns using Microsoft Pex").

What we missed till now is how to debug your parameterized unit tests.
In order to debug your parameterized unit tests, do the following:

-   Go to Tools &gt;&gt; Options &gt;&gt; Pex &gt;&gt; Diagnostic.
-   Change the *BreakOnStart* option to *True.*

![alt text](/img/0012.png "Logo Title Text 1")

-   Now set a break point at any line of code inside your parameterized
    unit test.
-   Right click inside your parameterized unit test and select *Run Pex
    Explorations*.
-   You will see a dialog popping asking to attach a debugger.
-   Select your current Visual Studio instance.

![alt text](/img/0013.png "Logo Title Text 1")

-   Once attached, press F5.
-   Now Visual Studio debugger will jump to your break point in the
    parameterized unit test and stop there. You can now step through you
    parameterized unit test code.

You will notice that parameter’s values are [those selected by
Pex](http://ebeid-soliman.blogspot.com/2013/04/why-pex-choose-these-inputs.html "Why Pex Choose These Inputs").
The debugger will run the parameterized unit test for each input
value(s) chosen by Pex, So you can inspect the PUT behavior against a
specific input value.
