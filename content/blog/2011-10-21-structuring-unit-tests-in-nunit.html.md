--- 
title: "Structuring unit tests in NUnit" 
date: '2011-10-21T12:19:00.001-05:00' 
tags: 
       - NUnit 
       - Unit testing
modified_time: '2011-11-04T14:54:02.356-05:00' 
thumbnail: http://lh3.ggpht.com/-AWxRoAtM0NQ/TqGpg8H6mJI/AAAAAAAAAJw/ImDIFUJg3sI/s72-c/NUnit3\_thumb3.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-9169556324814322059
blogger_orig_url: http://ebeid-soliman.blogspot.com/2011/10/structuring-unit-tests-in-nunit.html
---

Our goal in the previous post Introduction to NUnit, was just to
introduce the unit testing using NUnit as simple as possible. Now it is
the time to elaborate more on NUnit framework, structuring and
organizing your test cases. If you examined the test code again:

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

  

  
  

The code is pretty straightforward. The using statement on line 2 brings
in the necessary NUnit classes.

  
  

Next, we have the class definition on line 6: each class that contains
tests must be annotated with a \[TestFixture\] attribute. The class have
to be public, so the test runners can run it. The class must have a
public, no-parameter constructor.

  
  

Finally, the test class contains individual methods annotated with
\[Test\] attributes. Any public, parameterless method specified with a
\[Test\] attribute will be run automatically by NUnit.

  
  

**<span class="underline">Structuring Unit Tests</span>**

  
  

As a good object-oriented design concept, a class should be focused on
one responsibility and only one. This applies to test fixtures as well.
Test fixtures should be focused on verifying behavior in a specific
scenario. Its name should reflect this scenario. Tests inside that
fixture should test different behaviors within this scenario. Tests
should be organized around *behaviors*, not necessarily individual
methods. To keep things readable and clear in the test runner output,
favor putting fixture classes under a namespace that includes the name
of the class that the fixture are testing.

  
  

  

       1:  namespace solutionName.Test.ShoppingCartTest

  
  

       2:  {

  
  

       3:      [TestFixture]

  
  

       4:      public class EmptyCartFixture

  
  

       5:      {

  
  

       6:          [Test]

  
  

       7:          public void OverallRateIsZero() { }

  
  

       8:      }

  
  

       9:  }

  

  
  

**<span class="underline">Categories</span>**

  
  

NUnit provides an easy way to mark and run individual test and fixtures
by using categories. A category is just a name that we define. We can
associate different test methods with one or more categories, that
enable us to select which categories we want to exclude (or include)
when running the tests. A category is specified as an attribute.

  
  

  

       1:  using System;

  
  

       2:  using NUnit.Framework;

  
  

       3:  namespace ClassLibrary1

  
  

       4:  {

  
  

       5:      [TestFixture]

  
  

       6:      public class CmpTest

  
  

       7:      {

  
  

       8:          [Test]

  
  

       9:          [Category("Short")]

  
  

      10:          public void LargestOf3()

  
  

      11:          {

  
  

      12:              int[] numbers = new int[] { 8, 9, 7 };

  
  

      13:              Assert.That(Cmp.Largest(numbers), Is.EqualTo(9));

  
  

      14:          }

  
  

      15:   

  
  

      16:          [Test]

  
  

      17:          [Category("Long")]

  
  

      18:          [Category("Fred")]

  
  

      19:          public void LargestOf3Alt()

  
  

      20:          {

  
  

      21:              int[] numbers = new int[3];

  
  

      22:              numbers[0] = 1;

  
  

      23:              numbers[1] = 1;

  
  

      24:              numbers[2] = 1;

  
  

      25:              Assert.That(Cmp.Largest(numbers), Is.EqualTo(1));

  
  

      26:          }

  
  

      27:   

  
  

      28:          [SetUp]

  
  

      29:          public void LargestOf3Alt2()

  
  

      30:          {

  
  

      31:              int[] numbers = new int[1];

  
  

      32:              numbers[0] = 0;

  
  

      33:              Assert.That(Cmp.Largest(numbers), Is.EqualTo(0));

  
  

      34:          }

  
  

      35:      }

  
  

      36:  }

  

  
  

In the GUI, if you excluded “Short” methods from run, only LargestOf3()
will be selected and executed.

  
  

[<img src="http://lh3.ggpht.com/-AWxRoAtM0NQ/TqGpg8H6mJI/AAAAAAAAAJw/ImDIFUJg3sI/NUnit3_thumb3.jpg?imgmax=800" title="NUnit3" width="801" height="492" alt="NUnit3" />](http://lh3.ggpht.com/-nXyJ5v9aObs/TqGpgt33HLI/AAAAAAAAAJo/zjY9Qasyy7A/s1600-h/NUnit35.jpg)

  
  

When categories are used, only the tests in the selected categories will
be run. Those tests in categories that are not selected are not reported
at all. If no category selected in the GUI, then all methods will be
executed unless it is tagged with Explicit attribute. The Explicit
attribute causes a test or test fixture to be ignored unless it is
explicitly selected for running.

  
  

**<span class="underline">Per-Method Setup and Teardown</span> ** We
should write our test in order that each test can run independently of
other tests; this allows us to run any test at any time in any order. In
order to accomplish that we may need to reset things between tests or
clean up after a test has run. \[Setup\] and \[TearDown\] attributes are
used for these tasks.

  
  

**<span class="underline">Per-Fixture Setup and Teardown</span> ** If we
need to set something up or clean up after the entire test class has
run, use \[TestFixtureSetup\] and \[TestFixtureTearDown\] for that.

  
  

Although setup and teardown methods generally come in pair, they don’t
have to do so.

  
  

Suppose we need some sort of database connection for each test. Rather
than duplicating code in each test method that connects to and
disconnects from the database, we could use SetUp and TearDown methods.
Since creating the initial connection to the database can be slow, we
may want to do that only once before all the tests run by using
TestFixtureSetUp.

  
  

  

       1:  [TestFixture]

  
  

       2:  public class DBTest

  
  

       3:  {

  
  

       4:      private SqlConnection dbConn;

  
  

       5:              

  
  

       6:      [TestFixtureSetUp]

  
  

       7:      public void PerFixtureSetup()

  
  

       8:      {

  
  

       9:          dbConn = new SqlConnection("ConnectionString");

  
  

      10:          dbConn.Open();

  
  

      11:      }

  
  

      12:   

  
  

      13:      [SetUp]

  
  

      14:      public void PerTestSetup()

  
  

      15:      {

  
  

      16:          //populate database with test data

  
  

      17:      }

  
  

      18:   

  
  

      19:      [TearDown]

  
  

      20:      public void PerTestTearDown()

  
  

      21:      {

  
  

      22
    :          // clean up database

  
  

      23:      }

  
  

      24:   

  
  

      25:      [TestFixtureTearDown]

  
  

      26:      public void PerFixtureTearDown()

  
  

      27:      {

  
  

      28:          dbConn.Close();

  
  

      29:          dbConn.Dispose();

  
  

      30:      }

  
  

      31:   

  
  

      32:      [Test]

  
  

      33:      public void AccountAccess()

  
  

      34:      {

  
  

      35:          // Uses dbConn

  
  

      36:      }

  
  

      37:   

  
  

      38:      [Test]

  
  

      39:      public void EmployeeAccess()

  
  

      40:      {

  
  

      41:          // Uses dbConn

  
  

      42:      }

  
  

      43:  }

  

  
  

In this example, here is the methods run sequence: PerFixtureSetup
&gt;&gt; PerTestSetup &gt;&gt; AccountAccess &gt;&gt; PerTestTearDown
&gt;&gt; PerFixtureTearDown &gt;&gt; PerFixtureSetup &gt;&gt;
PerTestSetup &gt;&gt; EmployeeAccess &gt;&gt; PertestTearDown &gt;&gt;
PerFixtureTearDown.

  
  

In this post we tried to elaborate more on the NUnit framework and how
we structure and organize test cases in NUnit.
