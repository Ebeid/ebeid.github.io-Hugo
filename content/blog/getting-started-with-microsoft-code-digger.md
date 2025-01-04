---
title: 'Getting started with Microsoft Code Digger'
date: 2013-04-26T03:00:00.000-05:00
draft: false
url: /2013/04/getting-started-with-microsoft-code.html
tags: 
- Microsoft Pex
---

Microsoft Code Digger is Visual Studio 2012 extension that have been released few days ago by RiSE team at Microsoft Research (the same team who developed Pex). You can download the it from the Visual Studio Gallery [here](http://visualstudiogallery.msdn.microsoft.com/fb5badda-4ea3-4314-a723-a1975cbdabb4).

Microsoft Code Digger uses the same engine that Pex uses, and the same techniques under the hood (dynamic symbolic execution and constraint solvers). The only constrain that Code Digger have is that it only works on public .NET code in Portable Class Libraries.

### Let’s try it

After installing the Code Digger extension for Visual Studio 2012, create a Portable Class Library. Let’s use the Triang() method we used in previous posts as an example here. Your code should look like:

```
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
  
namespace PortableClassLibrary1  
{  
    public class Class1  
    {  
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
    }  
}  

```  

Right click inside Triang() method and wait for few seconds. You will see the below Inputs / Outputs pane.

  

[![PortableClassLibrary1 - Microsoft Visual Studio_2013-04-24_14-17-51](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjUU3ne3xMp-kQSGfJXgsQ1sX8mTeah_AsFGmOjt1xH-F759a9JlLS3jfpoYn_p8D7jPNHWR0HQ5Cdta6sVNinqKpPUJMocNUT6Ngi_N05AATicFHxG4tXWpuJ7rO5mQK4pg0K5W9qcaQ/?imgmax=800 "PortableClassLibrary1 - Microsoft Visual Studio_2013-04-24_14-17-51")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgNEcipgiWFyGCJ3opXnfLqNOsy91dwy7e2JYzxIBPKDE6nrk8c2gN_FeRxFqa_9KmSCwak8HPTewT1Zhdl1fGZCUQ8sB6chnVw9PeVE9OZBOtaP5rf7swtKktEtT9wR497JbdXZmhpwA/s1600-h/PortableClassLibrary1%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-24_14-17-51%25255B4%25255D.jpg) 

  

It’s the same set we got before from Pex and for the same reasons. No surprises, both tools use the same engine under hood.