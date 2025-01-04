--- 
title: "Asserts in NUnit" 
date: '2011-10-21T12:19:00.003-05:00'
tags: 
    - NUnit 
    - Unit testing 
modified_time: '2011-11-04T14:53:39.699-05:00' 
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-438810458685811864
blogger_orig_url: http://ebeid-soliman.blogspot.com/2011/10/asserts-in-nunit.html 
---

Assertions (or asserts for short) are helper methods that can assist us
in determining whether a method under test is performing correctly or
not. They let us assert conditions, data, and so on. All assertion
methods will report failures (that’s when the assertion is false) or
errors (that’s when we get an unexpected exception) and report these
through the NUnit test runner. when a failure or error occurs, execution
of the current test method is aborted. Other Test within the same test
fixture will still be run.

**<span class="underline">Classic Asserts</span>**

-   Assert.AreEqual (*expected*, *actual*, string *message*)
    -   For floating-point numbers we need to specify the tolerance of
        the equality.
    -   Assert.AreEqual(3.33, 10.0/3.0, 0.01)  // Checks the result but
        looks only for the first two decimal places.
-   Assert.Less(x, y)     // asserts that x &lt; y
-   Assert.Greater(x, y)      // asserts that x &gt; y
-   Assert.LessOrEqual(x, y)    // asserts that x &lt;= y
-   Assert.GreaterOrEqual(x, y)    // asserts that x &gt;= y
-   Assert.IsNull(object, string *message*)
-   Assert.IsNotNull(object, string *message*)
-   Assert.AreSame(expected, actual, string *message*)
-   Assert.IsTrue(bool condition, string *message)*
-   Assert.IsFalse(bool condition, string *message)*
-   Assert.Fail(string *message)*
    -   Fails the test immediately, can be used to mark sections of code
        that should not be reached.

\**message* in all previous statements is optional.

**<span class="underline">Constrain-Based Asserts</span>**

These are new assertion style introduced in NUnit 2.4. That new style
enable many expectations to be evaluated together in a single assertion:

Assert.That(4, Is.LessThan(5) & Is.GreatThan(0));

-   Assert.That(actual, **Is.EqualTo**(expected))
-   Assert.That(actual, **Is.Not.EqualTo**(expected));
-   Assert.That(actual, **Is.AtMost**(expected));        //equivalent to
    Assert.LessOrEqual()
-   Assert.That(actual, **Is.Atleast**(expected));        //equivalent
    to Assert.GreaterOrEqual()
-   Assert.That(expected, **Is.Null**);
-   Assert.That(expected, **Is.Not.Null**);                 //equivalent
    to Assert.That(expected, !Is.Null);
-   Assert.That(expected, **Is.Empty**);                   //for
    collections and strings
-   Assert.That(actual, **Is.InstanceOfType**(expected));
-   Assert.That(actual, **Has.Length**(expected));
-   Assert.That(actualCollection, **List.Contains**(expectedValue));
    -   Assert.That({5, 3, 2}, List.contains(2))   //will pass
-   Assert.That(actualCollection, **Is.SubsetOf**(expectedCollection));
    -   Assert.That({5, 3, 2}, Is.SubsetOf({5, 4, 3, 2, 1})
-   Assert.That(*actual*, **Text.StartsWith**(*expected*)); //asserts
    that the *expected* string is at the beginning of *actual*
-   Assert.That(*actual*, **Text.Matches**(*expected*));    //asserts
    that the *expected* regular expression string matches *actual*
-   FileAssert.AreEqual(FileInfo expected, FileInfo actual);
    -   FileAssert.AreEqual(String pathToExpected, String PathTo
        Actual);

**<span class="underline">NUnit and Exceptions</span>**

Part of your code behavior may be throwing a specific exception in
certain cases. If you want to assert that your code throws the
exceptions that it designed to throw, you need to tag your test method
with attribute: **\[ExpectedException(typeof(*ExpectedException*))\]**.

       1:  [TestFixture]

  
  

       2:  public class ImportListTest

  
  

       3:  {

  
  

       4:      [Test]

  
  

       5:      [ExpectedException(typeof(ArgumentNullException))]

  
  

       6:      public void NullList()

  
  

       7:      {

  
  

       8:          Class1.ImportList(null);

  
  

       9:      }

  
  

      10:  }

  

  
  

This test method in now expected to throw an exception \[from the call
to ImportList(null)\]. If it doesn’t, the test will fail. If a different
exception is thrown (even a superclass of the one specified), the test
fails. The test passes only if the exact exception specified is thrown.

  
  

**<span class="underline">Temporarily ignoring tests</span>**

  
  

If you wrote the test code first and will start writing code
incrementally (something like TDD), you may temporarily ignore tests
that you still implementing the code required to pass them. You could
just tag these tests with attribute **\[Ignore(“Optional Message”)\] .**
NUnit will report that these tests were skipped and show a yellow bar in
the GUI, so you won’t forget about it later.
