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

[<img src="http://lh4.ggpht.com/-ayDx3wwvFdk/Ugp-TrSfkdI/AAAAAAAAB2I/y6x2DbrwnE0/Options_2013-08-13_13-01-05_thumb%25255B2%25255D.png?imgmax=800" title="Options_2013-08-13_13-01-05" width="551" height="341" alt="Options_2013-08-13_13-01-05" />](http://lh6.ggpht.com/-F13ijoxl4e8/Ugp-TKg7cNI/AAAAAAAAB2A/vEMmjThJJhk/s1600-h/Options_2013-08-13_13-01-05%25255B4%25255D.png)

-   Now set a break point at any line of code inside your parameterized
    unit test.
-   Right click inside your parameterized unit test and select *Run Pex
    Explorations*.
-   You will see a dialog popping asking to attach a debugger.
-   Select your current Visual Studio instance.

[<img src="http://lh3.ggpht.com/-piAgugzJwG0/Ugp-U-sVhmI/AAAAAAAAB2Y/WeCEFk_g2ZE/Visual%252520Studio%252520Just-In-Time%252520Debugger_2013-08-13_13-17-20_thumb%25255B1%25255D.png?imgmax=800" title="Visual Studio Just-In-Time Debugger_2013-08-13_13-17-20" width="378" height="417" alt="Visual Studio Just-In-Time Debugger_2013-08-13_13-17-20" />](http://lh3.ggpht.com/-FMRznBkUlpo/Ugp-UekzsCI/AAAAAAAAB2Q/EQF3cgS6lrY/s1600-h/Visual%252520Studio%252520Just-In-Time%252520Debugger_2013-08-13_13-17-20%25255B3%25255D.png)

-   Once attached, press F5.
-   Now Visual Studio debugger will jump to your break point in the
    parameterized unit test and stop there. You can now step through you
    parameterized unit test code.

You will notice that parameter’s values are [those selected by
Pex](http://ebeid-soliman.blogspot.com/2013/04/why-pex-choose-these-inputs.html "Why Pex Choose These Inputs").
The debugger will run the parameterized unit test for each input
value(s) chosen by Pex, So you can inspect the PUT behavior against a
specific input value.
