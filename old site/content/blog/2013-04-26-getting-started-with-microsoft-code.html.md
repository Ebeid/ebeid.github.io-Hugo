--- 
title: "Getting started with Microsoft Code Digger" 
date: '2013-04-26T03:00:00.000-05:00' 
tags: 
    - Microsoft Pex 
modified_time: '2013-04-26T03:00:08.510-05:00' 
thumbnail: http://lh3.ggpht.com/-Rpzh3T\_bfro/UXgyBO\_u12I/AAAAAAAABKU/RVwBHgrB5Yo/s72-c/PortableClassLibrary1%252520-%252520Microsoft%252520Visual%252520Studio\_2013-04-24\_14-17-51\_thumb%25255B2%25255D.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-1812192897765606868
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/04/getting-started-with-microsoft-code.html
---

Microsoft Code Digger is Visual Studio 2012 extension that have been
released few days ago by RiSE team at Microsoft Research (the same team
who developed Pex). You can download the it from the Visual Studio
Gallery
[here](http://visualstudiogallery.msdn.microsoft.com/fb5badda-4ea3-4314-a723-a1975cbdabb4).

Microsoft Code Digger uses the same engine that Pex uses, and the same
techniques under the hood (dynamic symbolic execution and constraint
solvers). The only constrain that Code Digger have is that it only works
on public .NET code in Portable Class Libraries.

### Let’s try it

After installing the Code Digger extension for Visual Studio 2012,
create a Portable Class Library. Let’s use the Triang() method we used
in previous posts as an example here. Your code should look like:

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

  

Right click inside Triang() method and wait for few seconds. You will
see the below Inputs / Outputs pane.

  

[<img src="http://lh3.ggpht.com/-Rpzh3T_bfro/UXgyBO_u12I/AAAAAAAABKU/RVwBHgrB5Yo/PortableClassLibrary1%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-24_14-17-51_thumb%25255B2%25255D.jpg?imgmax=800" title="PortableClassLibrary1 - Microsoft Visual Studio_2013-04-24_14-17-51" width="455" height="221" alt="PortableClassLibrary1 - Microsoft Visual Studio_2013-04-24_14-17-51" />](http://lh6.ggpht.com/-k2dprYyaE8U/UXgyA4-6wAI/AAAAAAAABKM/-gDylz5tgW8/s1600-h/PortableClassLibrary1%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-24_14-17-51%25255B4%25255D.jpg) 

  

It’s the same set we got before from Pex and for the same reasons. No
surprises, both tools use the same engine under hood.
