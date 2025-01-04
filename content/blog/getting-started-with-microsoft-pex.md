---
title: 'Getting started with Microsoft Pex'
date: 2013-04-24T03:06:00.000-05:00
draft: false
url: /2013/04/getting-started-with-microsoft-pex.html
tags: 
- Microsoft Pex
- Parameterized Unit Tests
- Unit Tests
- NUnit
---

[Microsoft Pex](http://research.microsoft.com/en-us/projects/pex/) is a [white box test generation for .NET](http://research.microsoft.com/pubs/81193/fulltext.pdf) that came out of Microsoft Research and have been successfully integrated into Visual Studio 2010. It have been a result of collaborative work between Microsoft Research and the [Automated Software Engineering Research Group](https://sites.google.com/site/asergrp/) at [North Carolina State University](http://www.ncsu.edu/) led by  [Dr. Tao Xie](http://www.csc.ncsu.edu/faculty/xie/).

You can download and install Microsoft Pex for Visual Studio 2010 from [here](http://research.microsoft.com/en-us/projects/pex/downloads.aspx). We have talked in a previous [post](http://ebeid-soliman.blogspot.com/2013/04/unit-tests-vs-parameterized-unit-tests.html) about parameterized unit tests and the possibilities it brings. In this post and the following we will explore Microsoft Pex and how it can help you in understanding the input/output behavior of your code, finding inputs that cause the code-under-test to crash, and exploring parameterized unit tests to check whether your code implements the desired functionality for all inputs.

### Running Pex for the First Time

In Visual Studio click File > New > Project. In the left pane of the New Project dialog box, click Visual C#. In the center pane, click Console Application, pick a Name for it and click OK. Replace your class Program with the following class. It just the classic triangle classification program :

```
class Program  
    {  
        public static String\[\] triTypes = { "", // Ignore 0.  
                                               "scalene", "isoscelese", "equilateral", "not a valid triangle"};  
        public static String instructions = "This is the ancient TriType program.\\nEnter three integers that represent the lengths of the sides of a triangle.\\nThe triangle will be categorized as either scalene, isosceles, equilateral\\n or invalid.\\n";  
  
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
  
            Console.WriteLine("Result is: " + triTypes\[T\]);  
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
                    triOut = 4;  
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

```  

In the Build menu, click Build Solution.

  

To run Pex on your code, right-click in the body of the Triang method, and click Run Pex. If this is your first time running Pex, the Pex: Select a Test Framework dialog box appears. You could select your preferred test frame (Visual Studio Unit test, or NUnit)  and provide the installation path for its, then click OK. This dialog box will not appear again after you select the test framework. After a brief pause, Pex shows the results of its analysis in the Pex Exploration Results window. When you run Microsoft Pex on your .NET code, Pex generates test cases by analyzing the code-under-test. For every statement in the code, Pex will eventually try to create a test input that will reach that statement. Pex will do a case analysis for every conditional branch in the code—for example, if statements, assertions, and all operations that can throw exceptions. Each row in the table contains input/output values for the method under consideration(Traing). In the Pex Exploration Results window, click one row in the table on the left to see details in the right pane. You could select these rows and save them as unit tests. These details also displayed on the right in the Pex Explorer pane as test cases. [![ConsoleApplication2 - Microsoft Visual Studio_2013-04-23_16-45-40](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg1eeUwyVK7P7DAia2VmlhGdMqnnCXeG1KvFICFKEI1vNlsqt0YVw0pPz9vYNnJpe69v3wXUbjGUebjocNrLqB9t6ueWqZZlFmq_0wBF4FTv8vRusZo0s7DIjoiGqndjD5K3n8V61j1fA/?imgmax=800 "ConsoleApplication2 - Microsoft Visual Studio_2013-04-23_16-45-40")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjEG-FKRA6Gd93tYu4oWyZ-WIvatC-noUXe3oPzbcqWWBfQ2wLI6EHXH2wqrXiHjFhSEBp9Y2yKH00j4lRZn757-iYRLOaQJQv1ytgbARGiWMmJkCkNO8KgT_VidFtyUspKl2Sw6R5M_A/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-23_16-45-40%25255B6%25255D.jpg)

  

On the next post we will explain why Pex chose these values, and other Pex stuff :)