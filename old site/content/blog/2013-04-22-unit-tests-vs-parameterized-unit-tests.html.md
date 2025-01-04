--- 
title: "Unit Tests vs Parametrized Unit Tests" 
date: '2013-04-22T17:17:00.001-05:00' 
tags: 
    - Microsoft Pex 
    - Parameterized Unit Tests 
    - Unit Tests 
modified_time: '2013-04-25T05:52:01.166-05:00'
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-1187183382641437833
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/04/unit-tests-vs-parameterized-unit-tests.html
---

### Unit Tests

Using the conventions of NUnit unit tests as test methods contained in
test classes. A parameterless method decorated with a custom attribute
like \[TestMethod\] is a test method. Usually, each unit test explores a
particular aspect of the behavior of the class-under-test.

Here is a unit test written in C\# that adds an element to a .NET
ArrayList instance. The test first creates a new array list, where the
parameter to the constructor is the initial capacity, then adds a new
object to the array list, and finally checks that the addition was
correctly performed by verifying that a subsequent index lookup
operation returns the new object.

    [TestMethod] 
    void TestAdd() 
    { 
     ArrayList a = new ArrayList(0); 
     object o = new object(); 
     a.Add(o); 
     Assert.IsTrue(a[0] == o); 
    }

It is important to note that unit tests include a test oracle that
compares observed behavior with expected results. By convention, the
test oracle of a unit test is encoded using assertions. The test fails
if any assertion fails or an exception is thrown. Unit test frame- works
can also deal with expected exceptions. For a quick introduction about
NUnit refer previous
[posts](http://ebeid-soliman.blogspot.com/search/label/NUnit).  

A test suite produced by unit testing with high code coverage gives
confidence in the correctness of the tested code. However, writing unit
tests to achieve high coverage can be time-consuming and tedious given
that test execution frameworks only automate the test executions. You
still have to write your test cases !  

To address this problem, several automatic unit test generation tools
such as Parasoft JTest or jCUTE can automatically generate conventional
unit tests. These tools, nevertheless, cannot guarantee high code
coverage, unless testers manually write some tests.  

###  

  

### Parametrized Unit Tests

  

The unit test above specifies the behavior of the array list by example.
Strictly speaking, this unit test only says that by adding a new object
to an empty array list, this object becomes the first element of the
list. What about other array lists and other objects?

    [TestAxiom]
    void TestAdd(ArrayList a, object o) 
    {
     Assume.IsTrue(a!=null);
     int i = a.Count;
     a.Add(o);
     Assert.IsTrue(a[i] == o);
    }

By adding parameters we can turn a closed unit test into a universally
quantified conditional axiom that must hold for all inputs under
specified assumptions.  

Adding parameters to a unit test improves its expressiveness as a
specification of intended behavior, but we lose concrete test cases. We
can no longer execute this test axiom by itself. We need actual
parameters. But which values must be provided to ensure sufficient and
comprehensive testing? Which values can be chosen at all?  

In the ArrayList example, if we study the internal structure of the .NET
Framework implementation, we observe that there are two cases of
interest. One occurs when adding an element to an array list that
already has enough room for the new element (i.e. the array list’s
capacity is greater than the current number of elements in the array
list). The other occurs when the internal capacity of the array list
must be increased before adding the element.  

If we assume that library methods invoked by the ArrayList
implementation are themselves correctly implemented, we can deduce that
running exactly two test cases is sufficient to guarantee that the
parametrized TestAdd(...) succeeds for all array lists and all objects.

    [TestMethod]
    void TestAddNoOverflow() 
    {
     TestAdd(new ArrayList(1), new object());
    }

    [TestMethod]
    void TestAddWithOverflow() 
    {
     TestAdd(new ArrayList(0), new object());
    }

Splitting axioms and test cases in this way is a separa tion of
concerns:  

-   First, we describe expected behavior as parametrized unit tests.  
-   Then we study the case distinctions made by the code paths of the
    program under test to determine which inputs make sense for testing.

  

So, parametrized unit tests are more general specifications than
conventional unit tests because it specifies the behavior for the whole
input classes other than for a single concrete value of the input. But
it needs concrete parameter values to be executed.

  

The good news is, Given a parametrized unit test, a test-generation
tool, such as Microsoft Pex, can automatically generate tests with
concrete inputs for the parameters to achieve high coverage. Pex
explores the behaviors of a parametrized unit test using a technique
called dynamic [symbolic
execution](http://en.wikipedia.org/wiki/Symbolic_execution). Dynamic
Symbolic Execution (DSE) is a variation of symbolic execution, which
systematically explores feasible paths of the program under test by
running the program with different test inputs to achieve high
structural coverage. It collects the symbolic constraints on inputs
obtained from predicates (condition statements like if else, switch,…)
in branch statements along the execution and relies on a [constraint
solver](http://en.wikipedia.org/wiki/Constraint_satisfaction_problem)
\[like
[Zap](http://research.microsoft.com/apps/pubs/default.aspx?id=70224) or
[Simplify](http://www.hpl.hp.com/techreports/2003/HPL-2003-148.html)\]
to solve the constraints and generate new test input for exploring new
path. For each set of concrete test input that leads to a new path that
achieves new coverage, Pex generates a corresponding conventional unit
test. So, all what you have to do is write your parametrized unit test.

  

In this post we gave a brief overview about parametrized unit tests and
its related research areas. It’s a very important concept to understand
before start learning Microsoft Pex, which we will start . In later
posts, we will explore Microsoft Pex in detail.
