--- 
title: "Microsoft Pex: Understanding Assumptions, Assertions, and Test-Case Failures" 
date: '2013-04-29T15:00:00.000-05:00' 
tags: 
    - Microsoft Pex 
modified_time: '2013-04-28T16:01:25.139-05:00' 
thumbnail: http://lh4.ggpht.com/-E1BV--ea4YU/UXmnznj8UkI/AAAAAAAABLE/\_L5VZaVypYs/s72-c/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio\_2013-04-24\_15-46-30\_thumb%25255B2%25255D.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-6691406490897728526
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/04/microsoft-pex-understanding-assumptions.html
---

In a previous post we started using Microsoft Pex and showed how it
helped exploring all possible code paths, and how that helped
discovering a defect in our program logic. In that example, even our
program logic is defective, all test cases succeeded. A test case fails
if there is an un-caught exception or a failed assertion.

To see an example of a failed test case and how Pex could help in fixing
it, let’s add the following basic function to our code:

    public void Add(ArrayList a, object o)
            {
                a.Add(o);
            }

  

when you run Pex for that simple method, you get the following results:

  

[<img src="http://lh4.ggpht.com/-E1BV--ea4YU/UXmnznj8UkI/AAAAAAAABLE/_L5VZaVypYs/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-24_15-46-30_thumb%25255B2%25255D.jpg?imgmax=800" title="ConsoleApplication2 - Microsoft Visual Studio_2013-04-24_15-46-30" width="727" height="134" alt="ConsoleApplication2 - Microsoft Visual Studio_2013-04-24_15-46-30" />](http://lh3.ggpht.com/-Thkc7tlIHdY/UXmnzD-F23I/AAAAAAAABK8/0xbEpUghC58/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-24_15-46-30%25255B4%25255D.jpg)

  

As you might expected, the ArrayList object might be NULL. In situations
similar to this one, when a higher-level component (the code that called
Add() method) passes malformed data to a lower-level component(that
Add() method), which the lower-level component rejects, then the
higher-level component should be prevented from doing so in the first
place.

  

One way to achieve this is to promote the failure condition of the
lower-level component to the abstraction level of the higher-level
component. This is what the <span class="underline">Add
Precondition</span> feature of Pex does: It expresses a low-level
failure condition at the abstraction level of the code under test. When
added to the code-under-test as argument validation code—also called a
precondition—then this effectively prevents the code under test from
causing a failure somewhere in its execution. In other words, the Add
Precondition feature doesn’t completely fix an error, but it promotes
the failure condition to a higher, more appropriate abstraction level.

  

To add a precondition to your code, click the failed test case row, then
on the details section (right) click <span class="underline">Add
Precondition</span>, as in picture below

  

[<img src="http://lh5.ggpht.com/-TOCaWmxTeQA/UXmn0PHPulI/AAAAAAAABLQ/7nxDventpME/002%252520-%252520200%252520-%252520Exploring%252520Code%252520with%252520Microsoft%252520Pex.docx%252520%25255BCompatibility%252520Mode%25255D%252520-%252520Word_2013-04-25_08-56-05_thumb%25255B2%25255D.jpg?imgmax=800" title="002 - 200 - Exploring Code with Microsoft Pex.docx [Compatibility Mode] - Word_2013-04-25_08-56-05" width="581" height="392" alt="002 - 200 - Exploring Code with Microsoft Pex.docx [Compatibility Mode] - Word_2013-04-25_08-56-05" />](http://lh5.ggpht.com/-EcW7YsvnRFA/UXmnz9bgwMI/AAAAAAAABLM/9I2Slcoh6iA/s1600-h/002%252520-%252520200%252520-%252520Exploring%252520Code%252520with%252520Microsoft%252520Pex.docx%252520%25255BCompatibility%252520Mode%25255D%252520-%252520Word_2013-04-25_08-56-05%25255B4%25255D.jpg)

  

Pex will open <span class="underline">Preview and Apply updates</span>
dialog box to show you the proposed code modifications that Pex will do.

  

[<img src="http://lh4.ggpht.com/-0ZJJTu76gyI/UXmn0ygH80I/AAAAAAAABLk/1s3XMMG4eU8/Preview%252520and%252520Apply%252520updates_2013-04-25_09-00-24_thumb%25255B1%25255D.jpg?imgmax=800" title="Preview and Apply updates_2013-04-25_09-00-24" width="480" height="311" alt="Preview and Apply updates_2013-04-25_09-00-24" />](http://lh4.ggpht.com/-4gCSpnuh2dw/UXmn0Trx99I/AAAAAAAABLc/ILN7OVMFba8/s1600-h/Preview%252520and%252520Apply%252520updates_2013-04-25_09-00-24%25255B3%25255D.jpg)

  

Review and Click <span class="underline">Apply</span>. The modified
method will look like:

            
    public void Add(ArrayList a, object o)
            {
                // 
                Debug.Assert(a != (ArrayList)null, "a");
                // 
                a.Add(o);
            }

  

When you run Pex for our method now, we will not find a failed test
case.

  

The concept of assertions is well known in unit test frameworks. Pex
understands the built-in Assert classes provided by each supported test
framework. However, most frameworks do not provide a corresponding
Assume class as Pex did.
**[PexAssume](http://research.microsoft.com/en-us/um/redmond/projects/pex/wiki/pexassume.html)**
is a class to express assumptions, i.e. a precondition. The methods of
this class can be used to filter out undesirable test inputs. If you do
not want to use an existing test framework, Pex also has the
[PexAssert](http://research.microsoft.com/en-us/um/redmond/projects/pex/wiki/PexAssert.html)
class. Some functionalities can be achieved using attributes instead of
PexAssume methods, like
**[PexAssumeNotNullAttribute](http://research.microsoft.com/en-us/um/redmond/projects/pex/wiki/PexAssumeNotNullAttribute.html)**
and
[**PexAssumeUnderTestAttribute**](http://research.microsoft.com/en-us/um/redmond/projects/pex/wiki/PexAssumeUnderTestAttribute.html).

     
    [PexMethod]
    public void Test1(object o)  //precondition: o should not be null
    {
     PexAssume.IsNotNull(o);
     ...
    }

    [PexMethod]
    public void Test2([PexAssumeNotNull]object o) //precondition: o should not be null
    { 
     ...
    }

  

When you write an assertion, Pex will not only passively detect
assertion violations, but Pex will in fact actively try to compute test
inputs that will cause the assertion to fail (just as an assertion might
throw a **PexAssertFailedException**). Pes uses these exceptions
internally to stop a test case when an assumption fails.

  

### Expected Exceptions

  

You can annotate the test—or the test class, or the test assembly—with
one of the following attributes to indicate which exception types can or
must be thrown by the test in order to be considered successful:  

-   **PexAllowedExceptionAttribute** indicates that a test method, or
    any other method that it calls directly or indirectly, can throw a
    particular type of exception for some test inputs.

        using System;
        using Microsoft.Pex.Framework;
        using Microsoft.Pex.Framework.Validation;

        namespace ConsoleApplication3
        {
            class Stack
            {
                int[] _elements;
                int _count;
                public Stack(int capacity)
                {
                    if (capacity < 0) throw new ArgumentOutOfRangeException();
                    _elements = new int[capacity];
                    _count = 0;
                }
            }

            [PexClass]
            public partial class StackTest
            {
                [PexMethod]
                [PexAllowedException(typeof(ArgumentOutOfRangeException))]
                public void CtorTest(int capacity) // will not fail
                {
                    Stack s = new Stack(capacity); // may throw Argume
        ntOutOfRangeException
                }
            }
        }

      

-   **PexAllowedExceptionFromTypeAttribute** indicates that any method
    of a specified type can throw a particular type of exception for
    some test inputs.

        using System;
        using System.Collections;
        using Microsoft.Pex.Framework;
        using Microsoft.Pex.Framework.Validation;

        namespace ConsoleApplication3
        {
            [PexClass]
            public partial class ArrayListTest
            {
                [PexMethod]
                [PexAllowedExceptionFromType(typeof(NullReferenceException), typeof(ArrayListTest))]
                public void Add1(ArrayList a, object o) //will not fail
                {
                    a.Add(o);
                }
            }
        }

      

-   **PexAllowedExceptionFromTypeUnderTestAttribute** indicates that any
    method of the designated type under test can throw a particular type
    of exception for some test inputs.  

-   **PexAllowedExceptionFromAssemblyAttribute** indicates that any
    method located in a specified assembly can throw a particular type
    of exception for some test inputs.

  

### <span id="_Toc255301736">When Does Pex Emit a Test Case?</span>

  

Pex supports different filters that decide when generated test inputs
will be emitted as a test case. You can configure these filters with the
**[TestEmissionFilter](http://research.microsoft.com/en-us/um/redmond/projects/pex/wiki/TestEmissionFilter.html)**
property that you can set for example in the **PexMethod** attribute.
Possible values are the following:

  

-   **All** Emit every generated test input as a test case, including
    those that cause assumption violations.  
-   **FailuresAndIncreasedBranchHits** (<span
    class="underline">default</span>) Emit tests for all unique
    failures, and whenever a test case increases coverage, as controlled
    by the TestEmissionBranchHits property (take values 1 or 2).  
-   **FailuresAndUniquePaths** Emit tests for all failures Pex finds,
    and also for each test input that causes a unique execution path.  
-   **Failures** Emit tests for failures only.

  

Regarding increased branch coverage, the TestEmissionBranchHits property
controls how a branch is covered. For example:  

-   **TestEmissionBranchHits=1**: Whether Pex should just consider
    whether a branch was covered at all. This gives a very small test
    suite that covers all branches Pex could reach. In particular, this
    test suite also covers all reached basic blocks and statements.  
-   **TestEmissionBranchHits=2**: Whether a test covered it either once
    or twice.

  

The default is TestEmissionBranchHits=2, which generates a more
expressive test suite that is also better suited to detect future
regression errors.

    using System;
    using Microsoft.Pex.Framework;
    using Microsoft.Pex.Framework.Settings;

    namespace ConsoleApplication3
    {
        [PexClass]
        partial class TestEmission
        {
            int max(int x, int y)
            {
                if (x > y)
                    return x;
                else
                    return y;
            }

            [PexMethod(TestEmissionFilter=Microsoft.Pex.Framework.Settings.PexTestEmissionFilter.All)]
            public void MaxTest1(int a, int b, int c, int d)    // 1 test case generated
            {
                int e = max(a, b);
                PexObserve.ValueForViewing("max", e);
            }

            [PexMethod(TestEmissionFilter = Microsoft.Pex.Framework.Settings.PexTestEmissionFilter.Failures)]
            public void MaxTest2(int a, int b, int c, int d)    // No test cases generated 
            {
                int e = max(a, b);
                PexObserve.ValueForViewing("max", e);
            }
        }
    }

  

### When Does Pex Stop ?

  

If the code under test does not contain loops or unbounded recursion,
Pex will typically stop quickly because there is only a (small) finite
number of execution paths to analyze. However, most interesting programs
contain loops and/or unbounded recursion. In such cases the number of
execution paths is (practically) infinite, and it is in general
undecidable whether a statement is reachable. In other words, Pex would
take forever to analyze all execution paths of the program.  

In order to make sure that Pex terminates after a reasonable amount of
time, there are several exploration bounds. All bounds have predefined
default values, which you can override to let Pex analyze more and
longer execution paths. The bounds are parameters of the PexMethod,
PexClass, and PexAssemblySettings attributes. There are different kinds
of bounds:  

-   **Constraint Solving Bounds:** apply to each attempt of Pex to
    determine whether an execution path is feasible or not. Pex might
    need several constraint solving attempts to compute the next test
    inputs.  
    -   **ConstraintSolverTimeOut** Seconds the constraint solver has to
        figure out inputs that will cause a different execution path to
        be taken.  
    -   **ConstraintSolverMemoryLimit** Megabytes the constraint solver
        can use to figure out inputs.

      
-   **Exploration Path Bounds:** apply to each execution path that Pex
    executes and monitors. These bounds make sure that the program does
    not get stuck in an infinite loop, or recursive method.  
    -   **MaxBranches** Maximum number of branches that can be taken
        along a single execution path.  
    -   **MaxCalls** Maximum number of calls that can be taken during a
        single execution path.  
    -   **MaxStack** Maximum size of the stack at any time during a
        single execution path, measured in number of active call
        frames.  
    -   **MaxConditions** Maximum number of conditions over the inputs
        that can be checked during a single execution path.

      
-   **Exploration Bounds** apply to the exploration of each
    parameterized unit test.  
    -   **MaxRuns** Maximum number of runs that will be tried during an
        exploration (each run uses different test inputs; not every run
        will result in the emission of a new test case).  
    -   **MaxRunsWithoutNewTests** Maximum number of consecutive runs
        without a new test being emitted.  
    -   **MaxRunsWithUniquePaths** Maximum number of runs with unique
        execution paths that will be tried during an exploration.  
    -   **MaxExceptions** Maximum number of exceptions that can be found
        over all discovered execution paths combined.  
    -   **MaxExecutionTreeNodes** Maximum number of conditions over the
        inputs that can be checked during all discovered execution paths
        combined.  
    -   **MaxWorkingSet** Maximum size of working set in megabytes.  
    -   **TimeOut** Seconds after which exploration stops.

  

The following example shows a parameterized test that involves a loop.
The loop bound depends on the test inputs, and the exception can only be
triggered if the loop is executed a certain number of times. Here, we
used an explicit bound of 10 runs *MaxRuns=10* to let Pex finish
quickly. However, with this bound, Pex will most likely not be able to
trigger the exception, as Pex will not unroll the loop sufficiently many
times:

     [PexMethod(MaxRuns = 10)]
            public void TestWithLoop(int n)
            {
                var sum = 0;
                for (int i = 0; i < n; i++)
                    sum++;
                if (sum > 20) throw new Exception();
            } 
     

  

In the Pex Exploration Results you may see the Exception statement
reached, but you will see on the Pex tool bar that there is 1 boundry
reached.
[<img src="http://lh4.ggpht.com/-RJa9gQF3pDc/UX2Lf5BPsjI/AAAAAAAABL8/JeGP2MuNJLs/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-01-11_thumb.jpg?imgmax=800" title="ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-01-11" width="180" height="86" alt="ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-01-11" />](http://lh5.ggpht.com/-0iqrQSiM5YA/UX2LfVAqpKI/AAAAAAAABL0/lRqob2u4m4E/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-01-11%25255B2%25255D.jpg)
If you click on it, you will see more details:  
[<img src="http://lh5.ggpht.com/-wzeFFSVgpvI/UX2LgvZFNiI/AAAAAAAABMM/pN9z39kW7ww/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-04-15_thumb%25255B1%25255D.jpg?imgmax=800" title="ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-04-15" width="601" height="238" alt="ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-04-15" />](http://lh5.ggpht.com/-DPXDqCCgi7Y/UX2LgUw2_nI/AAAAAAAABME/iioNUjn44bU/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-04-15%25255B3%25255D.jpg)  
on the right, you could click Set MaxRuns=20 to increase the MaxRuns
boundry. You could do the same from the Pex tool bar
[<img src="http://lh6.ggpht.com/-euiHnSSQO0E/UX2LhbrfH2I/AAAAAAAABMc/f8552av2JcU/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-15-32_thumb.jpg?imgmax=800" title="ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-15-32" width="220" height="91" alt="ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-15-32" />](http://lh6.ggpht.com/-MCZ8WSEiR3I/UX2Lg8fB4pI/AAAAAAAABMU/XktXEpPIS1Q/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-15-32%25255B2%25255D.jpg)
and also setting boundary to infinity. Both actions will open a dialog
to review and approve the code changes.  

The following example shows another parameterized test that involves a
loop, but this loop does not depend on the test inputs. Here, we used an
explicit bound of 10 branches *MaxBranches=10* to let Pex finish
quickly. However, with this bound, Pex cannot even once execute the code
from beginning to end, as executing the embedded loop will cause more
than 10 branches to be executed.

     [PexMethod(MaxBranches = 10)]
            public void TestWithFixedLoop(int j)
            {
                var sum = 0;
                for (int i = 0; i < 15; i++)
                    sum++;
                if (j == 10) throw new Exception();
            }
     

  

In those cases, where a particular run exceeded some path-specific
bounds, we get a special row in the results.
[<img src="http://lh4.ggpht.com/-PKx0DnVshnA/UX2LiqngnvI/AAAAAAAABMs/s9v5yC1gxQg/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-28-43_thumb.jpg?imgmax=800" title="ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-28-43" width="216" height="51" alt="ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-28-43" />](http://lh4.ggpht.com/-fwJAgIRmwSo/UX2LiGNixiI/AAAAAAAABMk/FyQjO98JQY8/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-28-43%25255B2%25255D.jpg)
The Set MaxBranches= button on the results tool can be used to increase
the
bounds.[<img src="http://lh6.ggpht.com/-NG-jK1X2X2c/UX2LjaTfhHI/AAAAAAAABM8/-LgjASHxojQ/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-31-57_thumb.jpg?imgmax=800" title="ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-31-57" width="229" height="94" alt="ConsoleApplication2 - Microsoft Visual Studio_2013-04-28_15-31-57" />](http://lh5.ggpht.com/-Bfkv7dGSqmY/UX2LjMa__eI/AAAAAAAABM0/grYBR-3zTTM/s1600-h/ConsoleApplication2%252520-%252520Microsoft%252520Visual%252520Studio_2013-04-28_15-31-57%25255B2%25255D.jpg)
If you increased the boundary to 20, you will get all you branched
executed and the exception statement reached.  

In this post we talked about how and when a test case fail, how to use
precondition and assumptions to differentiate between failures from your
unit code and failures from malformed input, how to allow specific
exception to be raised from your tests without causing it to fail, how
to control which test inputs should Pex use as a test case, and finally
how to control the Pex stop criteria whether through  bounding the
constraint solver, or bounding the exploration paths, or bounding the
exploration runs.
