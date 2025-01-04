--- 
title: "Getting started with Microsoft Pex" 
date: '2013-04-24T03:06:00.000-05:00' 
tags: 
    - Microsoft Pex 
    - Parameterized Unit Tests 
    - Unit Tests 
    - NUnit 
modified_time: '2013-04-25T13:53:19.381-05:00' 
thumbnail: http://lh6.ggpht.com/-kcs1uvMR1qk/UXcGWPkiBOI/AAAAAAAABJk/DfC-HaT9Q2I/s72-c/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio\_2013-04-23\_16-45-40\_thumb%25255B4%25255D.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-8954316392130663203
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/04/getting-started-with-microsoft-pex.html
---

[Microsoft Pex](http://research.microsoft.com/en-us/projects/pex/) is a
[white box test generation for
.NET](http://research.microsoft.com/pubs/81193/fulltext.pdf) that came
out of Microsoft Research and have been successfully integrated into
Visual Studio 2010. It have been a result of collaborative work between
Microsoft Research and the [Automated Software Engineering Research
Group](https://sites.google.com/site/asergrp/) at [North Carolina State
University](http://www.ncsu.edu/) led by  [Dr. Tao
Xie](http://www.csc.ncsu.edu/faculty/xie/).

You can download and install Microsoft Pex for Visual Studio 2010 from
[here](http://research.microsoft.com/en-us/projects/pex/downloads.aspx).
We have talked in a previous
[post](http://ebeid-soliman.blogspot.com/2013/04/unit-tests-vs-parameterized-unit-tests.html)
about parameterized unit tests and the possibilities it brings. In this
post and the following we will explore Microsoft Pex and how it can help
you in understanding the input/output behavior of your code, finding
inputs that cause the code-under-test to crash, and exploring
parameterized unit tests to check whether your code implements the
desired functionality for all inputs.

### Running Pex for the First Time

In Visual Studio click <span class="underline">File</span> &gt; <span
class="underline">New</span> &gt; <span
class="underline">Project</span>. In the left pane of the New Project
dialog box, click <span class="underline">Visual C\#</span>. In the
center pane, click Console Application, pick a Name for it and click
<span class="underline">OK</span>. Replace your class Program with the
following class. It just the classic triangle classification program :

    class Program
        {
            public static String[] triTypes = { "", // Ignore 0.
                                                   "scalene", "isoscelese", "equilateral", "not a valid triangle"};
            public static String instructions = "This is the ancient TriType program.\nEnter three integers that represent the lengths of the sides of a triangle.\nThe triangle will be categorized as either scalene, isosceles, equilateral\n or invalid.\n";

            public static void Main()
            {
                int A, B, C;
                int T;

                Console.WriteLine(instructions);
                Console.WriteLine("Enter side 1: ");
                A = getN();
                Console.WriteLine("Enter side 2: ");
                B = getN();
                Console.WriteLine("Enter side 3: ");
                C = getN();
                T = Triang(A, B, C);

                Console.WriteLine("Result is: " + triTypes[T]);
                Console.ReadLine();
            }

            public static int Triang(int Side1, int Side2, int Side3)
            {
                int triOut;

                // triOut is output from the routine:
                //   Triang = 1 if triangle is scalene
                //   Triang = 2 if triangle is isosceles
                //   Triang = 3 if triangle is equilateral
                //   Triang = 4 if not a triangle

                // A quick confirmation that it's a valid triangle
                if (Side1 <= 0 || Side2 <= 0 || Side3 <= 0)
                {
                    triOut = 4;
                    return (triOut);
                }

                // Detect any sides of equal sides
                triOut = 0;
                if (Side1 == Side2)
                    triOut = triOut + 1;
                if (Side1 == Side3)
                    triOut = triOut + 2;
                if (Side2 == Side3)
                    triOut = triOut + 3;
                if (triOut == 0)
                {
                    if ((Side1 + Side2 <= Side3) || (Side2 + Side3 <= Side1) || (Side1 + Side3 <= Side2)) // confirm that it is a valid triangle 
                        triOut
    = 4;
                    else
                        triOut = 1;
                    return (triOut);
                }

                if (triOut > 3)
                    triOut = 3;
                else if ((triOut == 1) && (Side1 + Side2 > Side3))
                    triOut = 2;
                else if ((triOut == 2) && (Side1 + Side3 > Side2))
                    triOut = 2;
                else if ((triOut == 3) && (Side2 + Side3 > Side1))
                    triOut = 2;
                else
                    triOut = 4;
                return (triOut);
            }

  

In the <span class="underline">Build</span> menu, click <span
class="underline">Build Solution</span>.

  

To run Pex on your code, right-click in the body of the Triang method,
and click <span class="underline">Run Pex</span>. If this is your first
time running Pex, the <span class="underline">Pex: Select a Test
Framework</span> dialog box appears. You could select your preferred
test frame (Visual Studio Unit test, or NUnit)  and provide the
installation path for its, then click <span class="underline">OK</span>.
This dialog box will not appear again after you select the test
framework. After a brief pause, Pex shows the results of its analysis in
the Pex Exploration Results window. When you run Microsoft Pex on your
.NET code, Pex generates test cases by analyzing the code-under-test.
For every statement in the code, Pex will eventually try to create a
test input that will reach that statement. Pex will do a case analysis
for every conditional branch in the code—for example, if statements,
assertions, and all operations that can throw exceptions. Each row in
the table contains input/output values for the method under
consideration(Traing). In the Pex Exploration Results window, click one
row in the table on the left to see details in the right pane. You could
select these rows and save them as unit tests. These details also
displayed on the right in the <span class="underline">Pex
Explorer</span> pane as test cases.
[<img src="http://lh6.ggpht.com/-kcs1uvMR1qk/UXcGWPkiBOI/AAAAAAAABJk/DfC-HaT9Q2I/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-23_16-45-40_thumb%25255B4%25255D.jpg?imgmax=800" title="ConsoleApplication2 - Microsoft Visual Studio_2013-04-23_16-45-40" width="716" height="624" alt="ConsoleApplication2 - Microsoft Visual Studio_2013-04-23_16-45-40" />](http://lh5.ggpht.com/-kq8FaGAGRIg/UXcGV8HuX-I/AAAAAAAABJc/1T6cslBGBls/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-23_16-45-40%25255B6%25255D.jpg)

  

On the next post we will explain why Pex chose these values, and other
Pex stuff :)
