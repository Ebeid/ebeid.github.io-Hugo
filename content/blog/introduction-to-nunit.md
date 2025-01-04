---
title: 'Introduction to NUnit'
date: 2011-10-21T12:17:00.001-05:00
draft: false
url: /2011/10/introduction-to-nunit.html
tags: 
- NUnit
- Unit testing
---

**What is unit testing?**

According to [Jeff Canna](http://www-128.ibm.com/developerworks/library/j-test.html), unit testing ensures that a particular method of a class successfully performs a set of specific tasks. Each test confirms that a method produces the expected output when given a known input.

**What is NUnit?** NUnit is an open source framework that facilitates unit testing for all .NET languages. It allows you to build your test cases directly into the code of the project.

**How do I get NUnit?** Download the appropriate file from [here](http://www.nunit.org/index.php?p=download) and install it. That’s it !!

**Write your code**

We will write our code now and let it drive our testing cases and exploration of NUnit. Make a new project, class library that similar to the code below. Below an implementation of a “largest” method that returns the largest number in a list. <br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }

```
 1: using System;
```  
  
```
 2: namespace ClassLibrary1
```  
  
```
 3: {
```  
  
```
 4:    public class Cmp
```  
  
```
 5:    {
```  
  
```
 6:        public static int Largest(int\[\] list)
```  
  
```
 7:        {            
```  
  
```
 8:            int max = Int32.MaxValue;
```  
  
```
 9:            for (int index = 0; index < list.Length - 1; index++)
```  
  
```
 10:            {
```  
  
```
 11:                if (list\[index\] > max)
```  
  
```
 12:                    max = list\[index\];
```  
  
```
 13:            }
```  
  
```
 14:            return max;
```  
  
```
 15:        }
```  
  
```
 16:    }
```  
  
```
 17: }
```  

  
  

**Test your code**

  
  

Now it comes to the testing step. Writing test cases is a big topic to be discussed here. We will try to make our first test as simple as possible because there is much to be tested the first time besides the code itself. First, add reference to NUnit and then write our test cases.

  
  

  
2.  Right click on the references in “Solution Explorer” and click add a reference.
  
  
5.  Click on tab “Browse”
  
  
8.  Navigate to your NUnit directory and go into the bin subdirectory. For me this directory is in “C:\\Program Files (x86)\\NUnit 2.5.10\\bin\\net-2.0\\framework”
  
  
11.  Select nunit.framework.dll and click OK.
  

  
  

Then add a new class library to the project and add the code below to it. This code uses the NUnit namespace, attributes, Assert, and Is. We will explain all of these in detail in further posts. For now, just build the project.<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }

  
  

  
```
 1: using System;
```  
  
```
 2: using NUnit.Framework;
```  
  
```
 3: namespace ClassLibrary1
```  
  
```
 4: {
```  
  
```
 5:    \[TestFixture\]
```  
  
```
 6:    public class CmpTest
```  
  
```
 7:    {
```  
  
```
 8:        \[Test\]
```  
  
```
 9:        public void LargestOf3()
```  
  
```
 10:        {
```  
  
```
 11:            int\[\] numbers = new int\[\] { 8, 9, 7 };
```  
  
```
 12:            Assert.That(Cmp.Largest(numbers), Is.EqualTo(9));
```  
  
```
 13:        }
```  
  
```
 14:    }
```  
  
```
 15: }
```  

  
  

**Run your tests**

  
  

Now we have got our code, and our test cases. The next step is to run that test cases to test our code and that is the role of _test runners._ A test runner knows to look for the \[TestFixture\] attribute of a class and for the \[Test\] methods within it. The runner will run the tests, accumulate some statistics on which tests passed and failed, and report the results to you. There are many test runners, you can use the NUnit GUI which is installed by default with NUnit (will be located in the programs menu of the start menu).

  
  

**Using NUnit GUI**

  
  

In the NUnit GUI, select File > Open or press Ctrl + O. This would show the Open Project dialog. Browse to the folder which contains the assembly containing your tests and open it.  
  
[![NUnit1](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgg66o4d0RFr6viEabUH1NuK34LC7VUAKaNhcimc_Y-4VCOGQ2lbzOanrIk_EcAwdv0sszwNdw7kJ6gn6pISgoNEHndxAyArDTjfbRaruBdkAibHbuUwsUp66_IyTkoWCjbropaSvdOFA/?imgmax=800 "NUnit1")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjanY0eNnKI-7Fa-OBvyYShfXYM0JzV5O8QzynSiudTuDaI_Aw3BVQKdvzeWqk6EfJXu0C89g6sPUZJCDiAvU653dtXAzZJFBzpCxkw4MCMdZG2vNC-7wttajZuHexk4VFdPnUPB2OUFQ/s1600-h/NUnit14.jpg)  
  
  
Now you can test your code by clicking the Run button.  
  
  
[![NUnit2](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgHPaqZn9Jyet4xhHHJXrRGGFf-XIfo4o7Jg-PqTGIvK9-ogCMgpHvf_hYkPRwn1VEOU6lZ98hP3_dm9ls2FY9i_2BkS4ilhYMRNwJnFZXXAj1jjdQ3Hr09XwINnV5d7Dvq8Hep4GWxgg/?imgmax=800 "NUnit2")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiSJ_7tipfnN0xaUYHm1fdBta_0-a0b7qs1r7-SQlxMp1dX4gzig1rkG5Bh2XQyUJ_5IcnG1cXB3vBx3LKi5cx2Y9NSqcHFH8FGcl8sme_lnnQB1DxPcQcrGehO_GIB1PSVvxXMaHA55A/s1600-h/NUnit24.jpg)  
  
  
When we run a selected test, the GUI will display a large, colored, status bar. If all the tests pass, the bar is bright green. If any test fails, the bar is red. If any test was skipped, the bar is yellow.

  
  

It is obvious that our test case here have been failed. Try to fix the code and run the test again until it succeed ![Smile](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg7VN65sISINXsXT031D0ZYRVJ344hVck8lAGEib8yxl-tqwLuoYhfdBsA9ohjp9dY2kGDA75L6kYY7CWOcj-IwXv16K4xP8QjT8lJ1A1e3mLKhIH2kWKIsKgwFbrmZdvM-nWVX__PJjg/?imgmax=800)