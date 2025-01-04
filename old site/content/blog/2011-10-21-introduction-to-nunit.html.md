--- 
title: "Introduction to NUnit" 
date: '2011-10-21T12:17:00.001-05:00'
tags: 
    - NUnit 
    - Unit testing 
modified_time: '2011-11-04T14:51:57.532-05:00' 
thumbnail: http://lh5.ggpht.com/-ZpqTaDf8XsM/TqGpGCkzcaI/AAAAAAAAAJI/K7cQKbo6JwI/s72-c/NUnit1\_thumb2.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-8620442067718593403
blogger_orig_url: http://ebeid-soliman.blogspot.com/2011/10/introduction-to-nunit.html 
---

<span class="underline">**What is unit testing?**</span>

According to [Jeff
Canna](http://www-128.ibm.com/developerworks/library/j-test.html), unit
testing ensures that a particular method of a class successfully
performs a set of specific tasks. Each test confirms that a method
produces the expected output when given a known input.

**<span class="underline">What is NUnit?</span>** NUnit is an open
source framework that facilitates unit testing for all .NET languages.
It allows you to build your test cases directly into the code of the
project.

**<span class="underline">How do I get NUnit?</span>** Download the
appropriate file from [here](http://www.nunit.org/index.php?p=download)
and install it. That’s it !!

**<span class="underline">Write your code</span>**

We will write our code now and let it drive our testing cases and
exploration of NUnit. Make a new project, class library that similar to
the code below. Below an implementation of a “largest” method that
returns the largest number in a list.

       1:  using System;

  
  

       2:  namespace ClassLibrary1

  
  

       3:  {

  
  

       4:      public class Cmp

  
  

       5:      {

  
  

       6:          public static int Largest(int[] list)

  
  

       7:          {            

  
  

       8:              int max = Int32.MaxValue;

  
  

       9:              for (int index = 0; index < list.Length - 1; index++)

  
  

      10:              {

  
  

      11:                  if (list[index] > max)

  
  

      12:                      max = list[index];

  
  

      13:              }

  
  

      14:              return max;

  
  

      15:          }

  
  

      16:      }

  
  

      17:  }

  

  
  

**<span class="underline">Test your code</span>**

  
  

Now it comes to the testing step. Writing test cases is a big topic to
be discussed here. We will try to make our first t est as simple as
possible because there is much to be tested the first time besides the
code itself. First, add reference to NUnit and then write our test
cases.

  
  

1.  Right click on the references in “Solution Explorer” and click add a
    reference.
2.  Click on tab “Browse”
3.  Navigate to your NUnit directory and go into the bin subdirectory.
    For me this directory is in “C:\\Program Files (x86)\\NUnit
    2.5.10\\bin\\net-2.0\\framework”
4.  Select <span class="underline">nunit.framework.dll</span> and click
    OK.

  
  

Then add a new class library to the project and add the code below to
it. This code uses the NUnit namespace, attributes, Assert, and Is. We
will explain all of these in detail in further posts. For now, just
build the project.

  
  

  

       1:  using System;

  
  

       2:  using NUnit.Framework;

  
  

       3:  namespace ClassLibrary1

  
  

       4:  {

  
  

       5:      [TestFixture]

  
  

       6:      public class CmpTest

  
  

       7:      {

  
  

       8:          [Test]

  
  

       9:          public void LargestOf3()

  
  

      10:          {

  
  

      11:              int[] numbers = new int[] { 8, 9, 7 };

  
  

      12:              Assert.That(Cmp.Largest(numbers), Is.EqualTo(9));

  
  

      13:          }

  
  

      14:      }

  
  

      15:  }

  

  
  

**<span class="underline">Run your tests</span>**

  
  

Now we have got our code, and our test cases. The next step is to run
that test cases to test our code and that is the role of *test runners.*
A test runner knows to look for the \[TestFixture\] attribute of a class
and for the \[Test\] methods within it. The runner will run the tests,
accumulate some statistics on which tests passed and failed, and report
the results to you. There are many test runners, you can use the NUnit
GUI which is installed by default with NUnit (will be located in the
programs menu of the start menu).

  
  

**<span class="underline">Using NUnit GUI</span>**

  
  

In the NUnit GUI, select File &gt; Open or press Ctrl + O. This would
show the Open Project dialog. Browse to the folder which contains the
assembly containing your tests and open it.  
  
[<img src="http://lh5.ggpht.com/-ZpqTaDf8XsM/TqGpGCkzcaI/AAAAAAAAAJI/K7cQKbo6JwI/NUnit1_thumb2.jpg?imgmax=800" title="NUnit1" width="559" height="340" alt="NUnit1" />](http://lh5.ggpht.com/-ZzfW7Wivl68/TqGpFxFkxxI/AAAAAAAAAJA/MxxwI9pvD7Y/s1600-h/NUnit14.jpg)  
  
  
Now you can test your code by clicking the Run button.  
  
  
[<img src="http://lh4.ggpht.com/-T9Nd1jHgELU/TqGpGhO4YFI/AAAAAAAAAJY/ddP8YPT94tc/NUnit2_thumb2.jpg?imgmax=800" title="NUnit2" width="521" height="317" alt="NUnit2" />](http://lh4.ggpht.com/-pyKIWMEDcu4/TqGpGQw5GhI/AAAAAAAAAJQ/5aPwJG1wfmw/s1600-h/NUnit24.jpg)  
  
  
When we run a selected test, the GUI will display a large, colored,
status bar. If all the tests pass, the bar is bright green. If any test
fails, the bar is red. If any test was skipped, the bar is yellow.

  
  

It is obvious that our test case here have been failed. Try to fix the
code and run the test again until it succeed
<img src="http://lh4.ggpht.com/-tPXK8-ulKw8/TqGpGyLTHlI/AAAAAAAAAJg/fFvD3ixzxB8/wlEmoticon-smile2.png?imgmax=800" class="wlEmoticon wlEmoticon-smile" alt="Smile" />
