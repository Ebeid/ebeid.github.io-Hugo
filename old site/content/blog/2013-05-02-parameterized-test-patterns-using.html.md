--- 
title: "Parameterized Test Patterns using Microsoft Pex" 
date: '2013-05-02T16:08:00.000-05:00' 
tags: 
    - Microsoft Pex 
    - Parameterized Unit Tests 
    - Unit Tests 
    - Unit testing 
modified_time: '2013-05-02T16:08:18.632-05:00' 
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-8505498433861402798
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/05/parameterized-test-patterns-using.html
---

We talked before about the difference between unit tests and
parameterized unit tests. In this post we will talk about common
patterns for writing good parameterized unit tests. Keep in mind that we
will use these tests with Microsoft Pex (as an automatic test input
generation tool) to get test inputs that trigger all the possible
scenarios of the code-under-test.

> Before anything, let’s clarify what are the questions we want to
> answer using the parameterized unit tests. There are  two core
> questions:
>
> -   What are good scenarios (sequences of method calls) to exercise
>     the code-under-test? (Coverage)
> -   What are good assertions that can be stated easily without
>     re-implementing the algorithm? (Verification)
>
> A parameterized unit test is only useful if it provides answers for
> both questions:
>
> -   Without sufficient coverage, i.e. if the scenario is too narrow to
>     reach all the code-under-test, the extent of the test is limited.
> -   Without sufficient verification of the computed results, i.e. if
>     the test does not contain enough assertions, the test does not
>     check that the code is doing the right thing. All it would check
>     for is that the code-under-test does not crash.

### Test Patterns

#### 1- Arrange, Act, Assert

The ’AAA’ (Triple-A) is a well-known pattern for writing unit tests. It
applies to parameterized unit tests as well. A parameterized unit test
using this patter is organized in three sections:

-   **Arrange**: set up the unit under test
-   **Act**: exercise the unit under test, capturing any resulting state
-   **Assert**: verify the behavior through assertions

An example of this pattern in a traditional unit test:

    [Test]
    pubic void AddItem()
    {
          // arrange
          var list = new ArrayList();
          var item = new object();
          // act
          list.Add(item);
          // assert
          Assert.IsTrue(list.Count == 1);
    }

  
  

An example of this pattern in a parameterized unit test:

  
  

    [PexMethod]
    pubic void AddItem(object item)
    {
          // arrange
          var list = new ArrayList();
          // act
          list.Add(item);
          // assert
          Assert.IsTrue(list.Count == 1);
    }

  
  

#### 2- Assume, Arrange, Act, Assert

  

This pattern is an extension of the first pattern where an Assumption
section is added at the beginning. An **assumption** restricts possible
test inputs, acting as a filter. A parameterized unit test using this
pattern is organized in four sections:

  

-   **Assume**: assume preconditions over the test inputs
-   **Arrange**: set up the unit under test
-   **Act**: exercise the unit under test, capturing any resulting state
-   **Assert**: verify the behavior through assertions

  

The following example tests that adding an element to any list
increments the Count property. We use an assumption to filter out the
case where list is a null reference.

  
  

    [PexMethod]
    void AssumeActAssert(ArrayList list, object item)
    {
         // assume
         PexAssume.IsNotNull(list);
         // arrange
         var count = list.Count;
         // act
         list.Add(item);
         // assert
         Assert.IsTrue(list.Count == count + 1);
    }

  
  

#### 3- Parameterized Stubs

  
  

If the code-under-test already contains many assertion statements that
verify its behavior, an effective parameterized unit test might be quite
simple in itself, because it can leverage the assertions in the code.

  
  

    [PexMethod] 
    public void Add( [PexAssumeUnderTest]Array
    List list, object item) 
    { 
     list.Add(item); 

  
  

The attribute PexAssumeUnderTest is a short-hand notation to make sure
that the parameter is not null, and has exactly the type indicated by
its declaration (not a subtype).

  
  
  
  

#### 4- Observed Values

At any point in the parameterized unit test, if you want to log the
value of any variable or parameter, just use  

    PexObserve.ValueForViewing("Variable Name", var_name);

  
  

#### 5- Allowed Exceptions

  

Traditional unit test frameworks support the concept of expected
exception, where a test case or API call is expected to throw an
exception. If the test does not throw the exception or throws an
exception that does not match the criteria, the execution fails. The
same concept applied to parameterized unit tests.

  
  

    [PexMethod][PexAllowedException(typeof(ArgumentNullException))] 
    void Constructor(string value) 
    { 
     // throws ArgumentNullException if value is null 
     var myClass = new MyClass(value); 
    }

  
  

#### 6- State Relation

  

This pattern applies when an API call causes an internal state change
that can be (partially) observed through other API calls. A classic
example of such a pattern is the combination of Insert and Contains
operation on any collection type:

  
  

    [PexMethod] 
    void InsertContains(stringvalue) 
    { 
     var list = new List(); 
     list.Add(value); 
     Assert.IsTrue(list.Contains(value)); 
    }

  
  

#### 7- Roundtrip

  

This pattern applies to an API that transforms its inputs in a
reversible way: When the API has a function *f* and an inverse function
*f\_1*, then it should hold that *f\_1(f(x))=x* for all *x*. A classic
example of such pattern is property setters and getters, where the test
fails when the setter rejects a particular argument value.

  
  

    [PexMethod] 
    void PropertyRoundtrip(string value) 
    { 
     // arrange 
     var target = new MyClass(); 
     
     // two-way roundtrip 
     target.Name = value;   // calls setter 
     var roundtripped = target.Name; // calls getter 

     // assert 
     Assert.AreEqual(value, roundtripped); 
    }

  
  

Another example is serialization and deserialization of values.

  

    [PexMethod] 
    void ToStringParseRoundtrip(int value) 
    { 
     // two-way roundtrip 
     string s = value.ToString(); 
     int parsed = int.Parse(s); 

     // assert Assert.AreEqual(value, parsed); 
    }

  
  

#### 8- Normalized Roundtrip

  

The Pattern Roundtrip showed how to test a method for which in inverse
operation exists. For example, **int.Parse** is the inverse of
**int.ToString**. This is not the case in the other direction:
**int.ToString** is not exactly the inverse of **int.Parse**, because
the parsing ignores whitespace (some kind of data normalization):

  
  

    int.Parse(" 5").ToString() == "5";

  
  

This pattern is applied when the API has a function **f** and an inverse
function **f\_1**, then it should hold that **f\_1(f(f\_1(x)))=f\_1(x)**
for all **x** where **f\_1(x)** is defined.

  
  

    [PexMethod] 
    void ThreeWayRoundtrip(string value) 
    { 
     // ’hello%20world’ <= ’hello world’ 
     var normalized = Uri.EscapeDataString(value); 
     
     // ’helloworld’ <= ’hello%20world’ 
     var intermediate = Uri.UnescapeDataString(normalized); 

     // ’hello%20world’ <= ’hello world’ 
     var roundtripped = Uri.EscapeDataString(intermediate); 

     // assert 
     Assert.AreEqual(normalized, roundtripped); 
    }
    <
    br />

  
  

#### 9- Reachability

  
  

If your test assumptions are so complicated and it is not clear whether
there is any test input that fulfills them. You could use
**PexAssert.ReachEventually("GoalName")** wherever in your test to make
sure that there is at least one input that reach this point in your
test. The goal name have to be passed to the
**PexAssertReachEventuallyAttribute** constructor. A parameterized unit
test fails when Pex does not find a way to reach a goal, indicated by
calling the **PexAssert.Reached** method in a parameterized unit test
annotated with the **PexAssertReachEventuallyAttribute**.

  
  

    [PexMethod] 
    [PexAssertReachEventually("passed", StopWhenAllReached = true)] 
    public void ParsingSuccesful(string input) 
    { 
     // complicated parsing code 
     DateTime date; 
     if (DateTime.TryParse(input, out date)) 
     { 
      // and we want to see at least one case where parsing is successful. 
      PexAssert.ReachEventually("passed"); 
     } 
    }

  
  

Multiple goals can be combined in a single parameterized unit test for
more advanced scenarios by passing a list of goal identifiers in the
constructor of the PexAssertReachEventuallyAttribute. Each goal
identifier must be reached and notified in order for the parameterized
unit test to succeed.

  
  

    [PexMethod] 
    [PexAssertReachEventually("parsed", "y2k", StopWhenAllReached = true)] 
    public void ParsingSuccesfulWithMoreGoals(string input) 
    { 
     // complicated parsing code 
     DateTime date;
     if (DateTime.TryParse(input, out date)) 
     { 
      // and we want to see at least one case where parsing is successful. 
      PexAssert.ReachEventually("parsed"); 
     } 
     if (date.Year == 2000) 
     {
      // we want to see at least one test with the year 2000 
      PexAssert.ReachEventually("y2k"); 
     }
    }

  
  

#### 10- Reachable Implication

  
  

Implications assert a property when a predicate (condition) is true. Use
**PexAssert.ImpliesEventually** to make an implication that should be
true and that should be executed at least once. The test have to be
annotated with the **PexAssertReachEventuallyAttribute**. A
parameterized unit test fails when Pex does not find a way to make the
predicate of **PexAssert.ImpliesEventually** evaluates true at least
once.

  
  

    [PexMethod] 
    [PexAssertReachEventually] 
    public void ParseImpliesParse(string input) 
    { 
     bool value; 
     // if TryParse succeeds, Parse should succeed too. Also make sure TryParse succeeds at least once 
     PexAssert.ImpliesEventually( bool.TryParse(input, out value), () => bool.Parse(input) );
    }

  
  

#### 11- Seed Values to Help Pex

  

A parameterized unit test needs concrete input data to be executed.
Pex's role is to automatically generate relevant input data via code
analysis. Sometimes it might be desirable or even necessary to provide
manually chosen seed values to Pex to guide the automated code
exploration. In effect, Pex will fuzz the provided values in ways that
cause alternative execution paths to be taken. The
**PexArgumentsAttribute** can be used to provide primitive data. Each
instance of this attribute gives a list of values that must match the
parameter types of the parameterized unit test (and in the same
parameters order).  

  
  

    [PexMethod]
    [PexArguments("var i = 0;", 0)]
    [PexArguments("class Foo {}", 12)]
    public void ParseTest(string text, int line)
    {
     var parser = new Parser();
     parser.SetLine(line);
     var node = parser.Parse(text);

    }

  

Before analyzing the branch conditions in the code, Pex will first
execute the parameterized unit test with the provided values. This way,
Pex acquires knowledge about the code reachable from a test, and during
the subsequence code exploration Pex will try to further increase code
coverage by slightly modifying the values to trigger different execution
paths. In effect, Pex will
[fuzz](http://en.wikipedia.org/wiki/Fuzz_testing) the provided values.

  
  

#### 12- Regression Tests

  
  

In these tests some we could persist a computed value in the generated
test so when the generated test is executed in the future, it verifies
that the (possible changed) code-under-test still computes the same
value. There are several ways how outputs can be logged. For a single
output value, one can use the return value of the parameterized unit
test:

  

    [PexMethod]
    public int Add(int a, int b)
    {
     return a + b;
    }

  

Pex will recursively traverse the observable properties and fields of
the value and add assertions in the generated test for each one of them:

  

    [Test]
    [PexGeneratedBy(typeof(Program))]
    public void Add866()
    {
        int i;
        i = this.Add(0, 0);
        PexAssert.AreEqual(0, i);
    }

  

For multiple values, use **out** parameters in the parameterized unit
tests

  

    [PexMethod]
    public void Add(int a, int b, out int result)
    {
     result = a + b;
    }

  

Which Pex will use to generate the following

  

    [Test]
    [PexGeneratedBy(typeof(Program))]
    public void Add13()
    {
        int i = 0;
        this.Add(0, 0, out i);
        PexAssert.AreEqual(0, i);
    }

  

If the number of values might be dynamic, you could log these values
using
**[PexObserve](http://research.microsoft.com/en-us/um/redmond/projects/pex/wiki/PexObserve.html).Value**
and observe it later using the
**[PexObserve](http://research.microsoft.com/en-us/um/redmond/projects/pex/wiki/PexObserve.html).ValueAtEndOfTest**
method:

  

    [PexMethod]
    void Add(int a, int b)
    {
     int result = a * b;
     PexObserve.Value("result", result);
    }
