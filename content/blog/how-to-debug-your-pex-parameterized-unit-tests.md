---
title: 'How to debug your Pex parameterized unit tests'
date: 2013-08-13T13:43:00.001-05:00
draft: false
url: /2013/08/how-to-debug-your-pex-parameterized.html
tags: 
- Microsoft Pex
---

We talked before about [Microsoft Pex](http://ebeid-soliman.blogspot.com/2013/04/getting-started-with-microsoft-pex.html "Getting started with Microsoft Pex"), and [how it choose the shown inputs](http://ebeid-soliman.blogspot.com/2013/04/why-pex-choose-these-inputs.html "Why Pex Choose These Inputs"). We then talked more about [building blocks of parameterized unit tests](http://ebeid-soliman.blogspot.com/2013/04/microsoft-pex-understanding-assumptions.html "Microsoft Pex: Understanding Assumptions, Assertions, and Test-Case Failures") and its [patterns](http://ebeid-soliman.blogspot.com/2013/05/parameterized-test-patterns-using.html "Parameterized Test Patterns using Microsoft Pex").

What we missed till now is how to debug your parameterized unit tests. In order to debug your parameterized unit tests, do the following:

*   Go to Tools >> Options >> Pex >> Diagnostic.
*   Change the _BreakOnStart_ option to _True._

[![Options_2013-08-13_13-01-05](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEixeR3zghTBtxNaC__zrvvK5IF4NCjt9Qbtk06Pz38iMZzXNlkQITRkFCWr9_fgzTnxx97po3idxTHKReET7dw5OFYkbt2-5rE3M3g04vypjCvAPBxp8Me7VrgNTBiSq6KphZfbScAxLg/?imgmax=800 "Options_2013-08-13_13-01-05")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgfjj0As1W5DnJHPq6nqYDIxi-HX_TXxruEvloqBQLG8h0pTbYUAZ8DTJGuTUxSCtipVixFtlubjEQSegFaMniwQjdXXKMgP1TpxHgt3xXeNXD-qzO3-Mfag-Ou5ek0SQB_aKf44vGm-A/s1600-h/Options_2013-08-13_13-01-05%25255B4%25255D.png)

*   Now set a break point at any line of code inside your parameterized unit test.
*   Right click inside your parameterized unit test and select _Run Pex Explorations_.
*   You will see a dialog popping asking to attach a debugger.
*   Select your current Visual Studio instance.

[![Visual Studio Just-In-Time Debugger_2013-08-13_13-17-20](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhtqYUYkzFmWx9ec7Cfn5cTWi8YD40Xqml_VRQvEg53c57MO_rj3CfBtCIrcRLK7-Gelvi0ONYynwQuGpDU1wtFFReG_qkPv39B-mLvzgIP_Ax34Q__T593DfQ8UtGR97DY1JN4wUXPOQ/?imgmax=800 "Visual Studio Just-In-Time Debugger_2013-08-13_13-17-20")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEglFrIXq9Rohfv9pGbHOVZyGLmUPFrt8NWs6hwoSqFYAANYPFRGZ7LG_NCSTMTM6aGqKq_ia4sYlSY_mIzmx4loePKu8Y8jya5UFNV7K0EOyoF8FaN6fm1ZmTMJVSsRP2YtvJO-Dzikig/s1600-h/Visual%252520Studio%252520Just-In-Time%252520Debugger_2013-08-13_13-17-20%25255B3%25255D.png)

*   Once attached, press F5.
*   Now Visual Studio debugger will jump to your break point in the parameterized unit test and stop there. You can now step through you parameterized unit test code.

You will notice that parameter’s values are [those selected by Pex](http://ebeid-soliman.blogspot.com/2013/04/why-pex-choose-these-inputs.html "Why Pex Choose These Inputs"). The debugger will run the parameterized unit test for each input value(s) chosen by Pex, So you can inspect the PUT behavior against a specific input value.