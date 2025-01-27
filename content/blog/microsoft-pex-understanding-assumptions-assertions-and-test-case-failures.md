---
title: 'Microsoft Pex: Understanding Assumptions, Assertions, and Test-Case Failures'
date: 2013-04-29T15:00:00.000-05:00
draft: false
url: /2013/04/microsoft-pex-understanding-assumptions.html
tags: 
- Microsoft Pex
---

In a previous post we started using Microsoft Pex and showed how it helped exploring all possible code paths, and how that helped discovering a defect in our program logic. In that example, even our program logic is defective, all test cases succeeded. A test case fails if there is an un-caught exception or a failed assertion.

To see an example of a failed test case and how Pex could help in fixing it, let’s add the following basic function to our code:

```
public void Add(ArrayList a, object o)  
        {  
            a.Add(o);  
        }  

```  

when you run Pex for that simple method, you get the following results:

  

[![ConsoleApplication2 - Microsoft Visual Studio_2013-04-24_15-46-30](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhE_JIr1jcWXKwavO2Lx5X9o1d7p_eUmCP8jnNJBDei3mk08fmzM13AHscR6tq1tU6-1jHSKyRYLq-oMXvbqjKOvqpv01YaPQJyRcgPIzXKbiLQke5nC0jxPBMPoALXMWfPxfQ8opK8gg/?imgmax=800 "ConsoleApplication2 - Microsoft Visual Studio_2013-04-24_15-46-30")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhmNopAnmrQoO81K3UwsmumD6CPNmeBQeHYF-FHafOxt2MTCHDtWChlaLweTELqe31zXap2gctbBBww0-RHjbVu7Ys1ok6lAYrNl_narsjSXVXKBXZAWsz9QxUnkHLzN04nMWQEAIHLQA/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-24_15-46-30%25255B4%25255D.jpg)

  

As you might expected, the ArrayList object might be NULL. In situations similar to this one, when a higher-level component (the code that called Add() method) passes malformed data to a lower-level component(that Add() method), which the lower-level component rejects, then the higher-level component should be prevented from doing so in the first place.

  

One way to achieve this is to promote the failure condition of the lower-level component to the abstraction level of the higher-level component. This is what the Add Precondition feature of Pex does: It expresses a low-level failure condition at the abstraction level of the code under test. When added to the code-under-test as argument validation code—also called a precondition—then this effectively prevents the code under test from causing a failure somewhere in its execution. In other words, the Add Precondition feature doesn’t completely fix an error, but it promotes the failure condition to a higher, more appropriate abstraction level.

  

To add a precondition to your code, click the failed test case row, then on the details section (right) click Add Precondition, as in picture below

  

[![002 - 200 - Exploring Code with Microsoft Pex.docx [Compatibility Mode] - Word_2013-04-25_08-56-05](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhneUfBNIRhvuAmQB7-ZA8OFtcAodVroDtW6TMTL-zRStUZFCj7QqIm8Zj9hcsjooTXHPBpCgsoCIg7qcQxDqBmL8hyphenhyphen-3z1DmGIJ2ONXLBLFnjOmjPhlFMZQxtDTYDtoprRj31XgOrC0Q/?imgmax=800 "002 - 200 - Exploring Code with Microsoft Pex.docx [Compatibility Mode] - Word_2013-04-25_08-56-05")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiIFJJshmEjPOEvsmzTLRvdPSUj_PZWAeGahVE0lQcp4EujKQN62XPzp8_RXYgJMGmT4wKq6dd944wy3VxPXYebf_ABdJGemvgKSqCYbsY0GwDQle15kUxSFCI4p2zp8x1JL-f1hz8IQw/s1600-h/002%252520-%252520200%252520-%252520Exploring%252520Code%252520with%252520Microsoft%252520Pex.docx%252520%25255BCompatibility%252520Mode%25255D%252520-%252520Word_2013-04-25_08-56-05%25255B4%25255D.jpg)

  

Pex will open Preview and Apply updates dialog box to show you the proposed code modifications that Pex will do.

  

[![Preview and Apply updates_2013-04-25_09-00-24](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhwWpYaW3xwr-N42tC3H2hbto3h9mUORDPvZcx1pQTc-9lID_w3AI2I-PnqWw3jipzGxvDkiznsl_URwX17blm_buNwzoxMW9KFgZczhsYQnIOPnf2L1-pJlVj-Ktcit0VTPXncGo4mEA/?imgmax=800 "Preview and Apply updates_2013-04-25_09-00-24")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgcPwX7lK571_JPD08DZCP3IfP74Fnw7psJ9k617fS3Xg3JON4qu6xVyTbyokbby83Pp1xy0L_h3Jbj5IVZbLZvKPJcTCTTWYMAZKVOYaVjzq5pZFfkFylrgDF3dcAdIBPMl5YmtVoa-Q/s1600-h/Preview%252520and%252520Apply%252520updates_2013-04-25_09-00-24%25255B3%25255D.jpg)

  

Review and Click Apply. The modified method will look like:

```
          
public void Add(ArrayList a, object o)  
        {  
            // Debug.Assert(a != (ArrayList)null, "a");  
            //   
            a.Add(o);  
        }  

```  

When you run Pex for our method now, we will not find a failed test case.

  

The concept of assertions is well known in unit test frameworks. Pex understands the built-in Assert classes provided by each supported test framework. However, most frameworks do not provide a corresponding Assume class as Pex did. **[PexAssume](http://research.microsoft.com/en-us/um/redmond/projects/pex/wiki/pexassume.html)** is a class to express assumptions, i.e. a precondition. The methods of this class can be used to filter out undesirable test inputs. If you do not want to use an existing test framework, Pex also has the [PexAssert](http://research.microsoft.com/en-us/um/redmond/projects/pex/wiki/PexAssert.html) class. Some functionalities can be achieved using attributes instead of PexAssume methods, like **[PexAssumeNotNullAttribute](http://research.microsoft.com/en-us/um/redmond/projects/pex/wiki/PexAssumeNotNullAttribute.html)** and [**PexAssumeUnderTestAttribute**](http://research.microsoft.com/en-us/um/redmond/projects/pex/wiki/PexAssumeUnderTestAttribute.html).

```
   
\[PexMethod\]  
public void Test1(object o)  //precondition: o should not be null  
{  
 PexAssume.IsNotNull(o);  
 ...  
}  
  
\[PexMethod\]  
public void Test2(\[PexAssumeNotNull\]object o) //precondition: o should not be null  
{   
 ...  
}  

```  

When you write an assertion, Pex will not only passively detect assertion violations, but Pex will in fact actively try to compute test inputs that will cause the assertion to fail (just as an assertion might throw a **PexAssertFailedException**). Pes uses these exceptions internally to stop a test case when an assumption fails.

  

### Expected Exceptions

  

You can annotate the test—or the test class, or the test assembly—with one of the following attributes to indicate which exception types can or must be thrown by the test in order to be considered successful:  

  
*   **PexAllowedExceptionAttribute** indicates that a test method, or any other method that it calls directly or indirectly, can throw a particular type of exception for some test inputs.```
    using System;  
    using Microsoft.Pex.Framework;  
    using Microsoft.Pex.Framework.Validation;  
      
    namespace ConsoleApplication3  
    {  
        class Stack  
        {  
            int\[\] \_elements;  
            int \_count;  
            public Stack(int capacity)  
            {  
                if (capacity < 0) throw new ArgumentOutOfRangeException();  
                \_elements = new int\[capacity\];  
                \_count = 0;  
            }  
        }  
      
        \[PexClass\]  
        public partial class StackTest  
        {  
            \[PexMethod\]  
            \[PexAllowedException(typeof(ArgumentOutOfRangeException))\]  
            public void CtorTest(int capacity) // will not fail  
            {  
                Stack s = new Stack(capacity); // may throw ArgumentOutOfRangeException  
            }  
        }  
    }  
    
    ```  
    
*   **PexAllowedExceptionFromTypeAttribute** indicates that any method of a specified type can throw a particular type of exception for some test inputs.```
    using System;  
    using System.Collections;  
    using Microsoft.Pex.Framework;  
    using Microsoft.Pex.Framework.Validation;  
      
    namespace ConsoleApplication3  
    {  
        \[PexClass\]  
        public partial class ArrayListTest  
        {  
            \[PexMethod\]  
            \[PexAllowedExceptionFromType(typeof(NullReferenceException), typeof(ArrayListTest))\]  
            public void Add1(ArrayList a, object o) //will not fail  
            {  
                a.Add(o);  
            }  
        }  
    }  
    
    ```  
    
*   **PexAllowedExceptionFromTypeUnderTestAttribute** indicates that any method of the designated type under test can throw a particular type of exception for some test inputs.  
    
*   **PexAllowedExceptionFromAssemblyAttribute** indicates that any method located in a specified assembly can throw a particular type of exception for some test inputs.

  

### When Does Pex Emit a Test Case?

  

Pex supports different filters that decide when generated test inputs will be emitted as a test case. You can configure these filters with the **[TestEmissionFilter](http://research.microsoft.com/en-us/um/redmond/projects/pex/wiki/TestEmissionFilter.html)** property that you can set for example in the **PexMethod** attribute. Possible values are the following:

  

  
*   **All** Emit every generated test input as a test case, including those that cause assumption violations.  
    
*   **FailuresAndIncreasedBranchHits** (default) Emit tests for all unique failures, and whenever a test case increases coverage, as controlled by the TestEmissionBranchHits property (take values 1 or 2).  
    
*   **FailuresAndUniquePaths** Emit tests for all failures Pex finds, and also for each test input that causes a unique execution path.  
    
*   **Failures** Emit tests for failures only.

  

Regarding increased branch coverage, the TestEmissionBranchHits property controls how a branch is covered. For example:  

  
*   **TestEmissionBranchHits=1**: Whether Pex should just consider whether a branch was covered at all. This gives a very small test suite that covers all branches Pex could reach. In particular, this test suite also covers all reached basic blocks and statements.  
    
*   **TestEmissionBranchHits=2**: Whether a test covered it either once or twice.

  

The default is TestEmissionBranchHits=2, which generates a more expressive test suite that is also better suited to detect future regression errors.

```
using System;  
using Microsoft.Pex.Framework;  
using Microsoft.Pex.Framework.Settings;  
  
namespace ConsoleApplication3  
{  
    \[PexClass\]  
    partial class TestEmission  
    {  
        int max(int x, int y)  
        {  
            if (x > y)  
                return x;  
            else  
                return y;  
        }  
  
        \[PexMethod(TestEmissionFilter=Microsoft.Pex.Framework.Settings.PexTestEmissionFilter.All)\]  
        public void MaxTest1(int a, int b, int c, int d)    // 1 test case generated  
        {  
            int e = max(a, b);  
            PexObserve.ValueForViewing("max", e);  
        }  
  
        \[PexMethod(TestEmissionFilter = Microsoft.Pex.Framework.Settings.PexTestEmissionFilter.Failures)\]  
        public void MaxTest2(int a, int b, int c, int d)    // No test cases generated   
        {  
            int e = max(a, b);  
            PexObserve.ValueForViewing("max", e);  
        }  
    }  
}  

```  

### When Does Pex Stop ?

  

If the code under test does not contain loops or unbounded recursion, Pex will typically stop quickly because there is only a (small) finite number of execution paths to analyze. However, most interesting programs contain loops and/or unbounded recursion. In such cases the number of execution paths is (practically) infinite, and it is in general undecidable whether a statement is reachable. In other words, Pex would take forever to analyze all execution paths of the program.  

In order to make sure that Pex terminates after a reasonable amount of time, there are several exploration bounds. All bounds have predefined default values, which you can override to let Pex analyze more and longer execution paths. The bounds are parameters of the PexMethod, PexClass, and PexAssemblySettings attributes. There are different kinds of bounds:  

  
*   **Constraint Solving Bounds:** apply to each attempt of Pex to determine whether an execution path is feasible or not. Pex might need several constraint solving attempts to compute the next test inputs.  
    
      
    *   **ConstraintSolverTimeOut** Seconds the constraint solver has to figure out inputs that will cause a different execution path to be taken.  
        
    *   **ConstraintSolverMemoryLimit** Megabytes the constraint solver can use to figure out inputs.
    
      
    
*   **Exploration Path Bounds:** apply to each execution path that Pex executes and monitors. These bounds make sure that the program does not get stuck in an infinite loop, or recursive method.  
    
      
    *   **MaxBranches** Maximum number of branches that can be taken along a single execution path.  
        
    *   **MaxCalls** Maximum number of calls that can be taken during a single execution path.  
        
    *   **MaxStack** Maximum size of the stack at any time during a single execution path, measured in number of active call frames.  
        
    *   **MaxConditions** Maximum number of conditions over the inputs that can be checked during a single execution path.
    
      
    
*   **Exploration Bounds** apply to the exploration of each parameterized unit test.  
      
    *   **MaxRuns** Maximum number of runs that will be tried during an exploration (each run uses different test inputs; not every run will result in the emission of a new test case).  
        
    *   **MaxRunsWithoutNewTests** Maximum number of consecutive runs without a new test being emitted.  
        
    *   **MaxRunsWithUniquePaths** Maximum number of runs with unique execution paths that will be tried during an exploration.  
        
    *   **MaxExceptions** Maximum number of exceptions that can be found over all discovered execution paths combined.  
        
    *   **MaxExecutionTreeNodes** Maximum number of conditions over the inputs that can be checked during all discovered execution paths combined.  
        
    *   **MaxWorkingSet** Maximum size of working set in megabytes.  
        
    *   **TimeOut** Seconds after which exploration stops.

  

The following example shows a parameterized test that involves a loop. The loop bound depends on the test inputs, and the exception can only be triggered if the loop is executed a certain number of times. Here, we used an explicit bound of 10 runs _MaxRuns=10_ to let Pex finish quickly. However, with this bound, Pex will most likely not be able to trigger the exception, as Pex will not unroll the loop sufficiently many times:

```
 \[PexMethod(MaxRuns = 10)\]  
        public void TestWithLoop(int n)  
        {  
            var sum = 0;  
            for (int i = 0; i < n; i++)  
                sum++;  
            if (sum > 20) throw new Exception();  
        }   
 
```  

In the Pex Exploration Results you may see the Exception statement reached, but you will see on the Pex tool bar that there is 1 boundry reached. [![ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-01-11](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi7jQU-dWLUkJqKHlbGdQp25bIGXn_vvWDBlxD1oLRbPPOXDGWxQ_7kEusjbxOtdOO3YPSFjlyl0qBNvKJimZcNFX43L0uQXeeZhMoMZkTm6CUgG4shjSJM71CNAnWS52xvAmVLfF4WLw/?imgmax=800 "ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-01-11")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiYblGnaDT0dJuzLTDM43MnDVQNMlclKzedQBopf6Fx-9eBxiW0KLcq1TlyACw5uEd0wR1PLBk31HQ3Buk5c1NnEozaQ3t0ZTXPgqm5dkgAFxHE5FoVjd5NmvzOdyqKTiaGxD2WFD_1_g/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-01-11%25255B2%25255D.jpg) If you click on it, you will see more details:  
[![ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-04-15](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgbsa9oHbfvhUp2EoAzr05LBy8Rmfv5GJzMMzn4t1VzLSw2w4796WgsA4AlgEoSYzCn1XA9B2tBgJb4Nv8FM_rzgATEyOEelNvdMjlDlwdSm5G1dqtSt_0NLHH2rjqUPu19sphft_g-gQ/?imgmax=800 "ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-04-15")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiStRYiTTXzCuwRTVN4Gcmx6-yb5YOhPh8kEXQJz2HpU0JpB8W_3a6gBuSVqvoI8CnJox7ubLbltC9J-wjL8JXrR9gSuQVzKh5lxeW8R5zkBnw2JdLgxROA9UZUNmYQqjPltGDOYsYYwg/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-04-15%25255B3%25255D.jpg)  
on the right, you could click Set MaxRuns=20 to increase the MaxRuns boundry. You could do the same from the Pex tool bar [![ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-15-32](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEid5InQjKrXs5H1h4QRU0AbM6eSytz9Vd2hUTHoj3wDOgmc0J9OBgAn08V7Risf_lBrMzhstIsIE6rCh1laa7AD48Y3az52SpPqYFKttuHeCH0xGkmexP-OljBR8anAs62lMKvQrZ7Y-g/?imgmax=800 "ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-15-32")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgito0hAgSLNloC9olgBYXKwWS8gw8q_G9jJoc2_tSPbjzRDsbhgt8_rBr1L0Bj8S7g224VyJADmooYmTg5iO8VJ5tCBS8bWjvqk4kTP8LPycH1wk-AOCYcDuT2u9gMngy3TD-y28zfkA/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-15-32%25255B2%25255D.jpg) and also setting boundary to infinity. Both actions will open a dialog to review and approve the code changes.  

The following example shows another parameterized test that involves a loop, but this loop does not depend on the test inputs. Here, we used an explicit bound of 10 branches _MaxBranches=10_ to let Pex finish quickly. However, with this bound, Pex cannot even once execute the code from beginning to end, as executing the embedded loop will cause more than 10 branches to be executed.

```
 \[PexMethod(MaxBranches = 10)\]  
        public void TestWithFixedLoop(int j)  
        {  
            var sum = 0;  
            for (int i = 0; i < 15; i++)  
                sum++;  
            if (j == 10) throw new Exception();  
        }  
 
```  

In those cases, where a particular run exceeded some path-specific bounds, we get a special row in the results. [![ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-28-43](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj8-rQMbYnYaLaaWcJ8eAiv6alg-FccKSxZXSJvmJgjSLE7e-bgLhqaD9m2sCxePJZbQ20nZpPaOZpWARySPMVwaCnd9nxhHTE2INfqom8gUmAuJrL5Ryq0UeZRG22rMQzjn1cAXk4JTQ/?imgmax=800 "ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-28-43")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjP-NuzHNVdmDan6j9dy6VigwdhnmA8K8WLklU49W2eHdDjMhoDI65G8kbO81RHalwIaGke0fKJppxBzdy-ImhRbr6YABXIoW-sSrgWkLdrVKwRO0Q9pymE-V8L2AyQhTp5AkHEQdZHkg/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-28-43%25255B2%25255D.jpg) The Set MaxBranches= button on the results tool can be used to increase the bounds.[![ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-31-57](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi9hiEZUP5vAZuD1_G2cj_-VWn7rddeTTmD9T5tOboaoG9X9CwtOhaW-Y6V5Y4JDEGk8casYbaoO-4-vr8dweRnXZPy5ItOSfAS1dn7LCUTHrocnbuGOYi3oTbE3GTrvWinzhctcyYxjA/?imgmax=800 "ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-31-57")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhldaoiKtMug5Vrhnc5dK3zBgpeKueJN9bW1HVBjdpadW077319DudG_8KkFR_s_K-9lzTGMJKGkAinXQSK0lcDJMTOnUJ5kXR_wB8qrQQ7kE2oraffB5T5UScafyxSLJfUVmHhmS8yeQ/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-31-57%25255B2%25255D.jpg) If you increased the boundary to 20, you will get all you branched executed and the exception statement reached.  

In this post we talked about how and when a test case fail, how to use precondition and assumptions to differentiate between failures from your unit code and failures from malformed input, how to allow specific exception to be raised from your tests without causing it to fail, how to control which test inputs should Pex use as a test case, and finally how to control the Pex stop criteria whether through  bounding the constraint solver, or bounding the exploration paths, or bounding the exploration runs.