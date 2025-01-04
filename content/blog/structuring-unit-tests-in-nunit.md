---
title: 'Structuring unit tests in NUnit'
date: 2011-10-21T12:19:00.001-05:00
draft: false
url: /2011/10/structuring-unit-tests-in-nunit.html
tags: 
- NUnit
- Unit testing
---

Our goal in the previous post Introduction to NUnit, was just to introduce the unit testing using NUnit as simple as possible. Now it is the time to elaborate more on NUnit framework, structuring and organizing your test cases. If you examined the test code again:<br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }

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

  
  

The code is pretty straightforward. The using statement on line 2 brings in the necessary NUnit classes.

  
  

Next, we have the class definition on line 6: each class that contains tests must be annotated with a \[TestFixture\] attribute. The class have to be public, so the test runners can run it. The class must have a public, no-parameter constructor.

  
  

Finally, the test class contains individual methods annotated with \[Test\] attributes. Any public, parameterless method specified with a \[Test\] attribute will be run automatically by NUnit.

  
  

**Structuring Unit Tests**

  
  

As a good object-oriented design concept, a class should be focused on one responsibility and only one. This applies to test fixtures as well. Test fixtures should be focused on verifying behavior in a specific scenario. Its name should reflect this scenario. Tests inside that fixture should test different behaviors within this scenario. Tests should be organized around _behaviors_, not necessarily individual methods. To keep things readable and clear in the test runner output, favor putting fixture classes under a namespace that includes the name of the class that the fixture are testing. <br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }

  
  

  
```
 1: namespace solutionName.Test.ShoppingCartTest
```  
  
```
 2: {
```  
  
```
 3:    \[TestFixture\]
```  
  
```
 4:    public class EmptyCartFixture
```  
  
```
 5:    {
```  
  
```
 6:        \[Test\]
```  
  
```
 7:        public void OverallRateIsZero() { }
```  
  
```
 8:    }
```  
  
```
 9: }
```  

  
  

**Categories**

  
  

NUnit provides an easy way to mark and run individual test and fixtures by using categories. A category is just a name that we define. We can associate different test methods with one or more categories, that enable us to select which categories we want to exclude (or include) when running the tests. A category is specified as an attribute. <br /><br /><br /><br /><br /><br /><br /><br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }

  
  

  
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
 9:        \[Category("Short")\]
```  
  
```
 10:        public void LargestOf3()
```  
  
```
 11:        {
```  
  
```
 12:            int\[\] numbers = new int\[\] { 8, 9, 7 };
```  
  
```
 13:            Assert.That(Cmp.Largest(numbers), Is.EqualTo(9));
```  
  
```
 14:        }
```  
  
```
 15:  
```  
  
```
 16:        \[Test\]
```  
  
```
 17:        \[Category("Long")\]
```  
  
```
 18:        \[Category("Fred")\]
```  
  
```
 19:        public void LargestOf3Alt()
```  
  
```
 20:        {
```  
  
```
 21:            int\[\] numbers = new int\[3\];
```  
  
```
 22:            numbers\[0\] = 1;
```  
  
```
 23:            numbers\[1\] = 1;
```  
  
```
 24:            numbers\[2\] = 1;
```  
  
```
 25:            Assert.That(Cmp.Largest(numbers), Is.EqualTo(1));
```  
  
```
 26:        }
```  
  
```
 27:  
```  
  
```
 28:        \[SetUp\]
```  
  
```
 29:        public void LargestOf3Alt2()
```  
  
```
 30:        {
```  
  
```
 31:            int\[\] numbers = new int\[1\];
```  
  
```
 32:            numbers\[0\] = 0;
```  
  
```
 33:            Assert.That(Cmp.Largest(numbers), Is.EqualTo(0));
```  
  
```
 34:        }
```  
  
```
 35:    }
```  
  
```
 36: }
```  

  
  

In the GUI, if you excluded “Short” methods from run, only LargestOf3() will be selected and executed.

  
  

[![NUnit3](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj-1fA6DhLNv9vP_pAZ0DNSSDodlYvkC6I1lb_7nGd0jhXzso4BSZM_KwnMN0-1CAZBmGHQqQTielgfiCPFG1UJSJu65UexQAH4Kr4GYut1-jjcikdKDwEX-rbvY3jKNwd2aY8BsIqmOg/?imgmax=800 "NUnit3")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgIvhqVBoYMfJYP5GnI1KN8fo4L2BuZdezxUXHiaGcgmNrJh25Iqxf45F1y5sOafLfiFpNV-5uwIG4ozVV9-Cwd36_wjsNwQUdfmcJxPsRuIYkKA66kH7V_iYjgBba76_MUmP4-R_HRBw/s1600-h/NUnit35.jpg)

  
  

When categories are used, only the tests in the selected categories will be run. Those tests in categories that are not selected are not reported at all. If no category selected in the GUI, then all methods will be executed unless it is tagged with Explicit attribute. The Explicit attribute causes a test or test fixture to be ignored unless it is explicitly selected for running.

  
  

**Per-Method Setup and Teardown** We should write our test in order that each test can run independently of other tests; this allows us to run any test at any time in any order. In order to accomplish that we may need to reset things between tests or clean up after a test has run. \[Setup\] and \[TearDown\] attributes are used for these tasks.

  
  

**Per-Fixture Setup and Teardown** If we need to set something up or clean up after the entire test class has run, use \[TestFixtureSetup\] and \[TestFixtureTearDown\] for that.

  
  

Although setup and teardown methods generally come in pair, they don’t have to do so.

  
  

Suppose we need some sort of database connection for each test. Rather than duplicating code in each test method that connects to and disconnects from the database, we could use SetUp and TearDown methods. Since creating the initial connection to the database can be slow, we may want to do that only once before all the tests run by using TestFixtureSetUp. <br /><br /><br /><br />.csharpcode, .csharpcode pre<br />{<br /> font-size: small;<br /> color: black;<br /> font-family: consolas, "Courier New", courier, monospace;<br /> background-color: #ffffff;<br /> /\*white-space: pre;\*/<br />}<br /><br />.csharpcode pre { margin: 0em; }<br /><br />.csharpcode .rem { color: #008000; }<br /><br />.csharpcode .kwrd { color: #0000ff; }<br /><br />.csharpcode .str { color: #006080; }<br /><br />.csharpcode .op { color: #0000c0; }<br /><br />.csharpcode .preproc { color: #cc6633; }<br /><br />.csharpcode .asp { background-color: #ffff00; }<br /><br />.csharpcode .html { color: #800000; }<br /><br />.csharpcode .attr { color: #ff0000; }<br /><br />.csharpcode .alt <br />{<br /> background-color: #f4f4f4;<br /> width: 100%;<br /> margin: 0em;<br />}<br /><br />.csharpcode .lnum { color: #606060; }

  
  

  
```
 1: \[TestFixture\]
```  
  
```
 2: public class DBTest
```  
  
```
 3: {
```  
  
```
 4:    private SqlConnection dbConn;
```  
  
```
 5:            
```  
  
```
 6:    \[TestFixtureSetUp\]
```  
  
```
 7:    public void PerFixtureSetup()
```  
  
```
 8:    {
```  
  
```
 9:        dbConn = new SqlConnection("ConnectionString");
```  
  
```
 10:        dbConn.Open();
```  
  
```
 11:    }
```  
  
```
 12:  
```  
  
```
 13:    \[SetUp\]
```  
  
```
 14:    public void PerTestSetup()
```  
  
```
 15:    {
```  
  
```
 16:        //populate database with test data
```  
  
```
 17:    }
```  
  
```
 18:  
```  
  
```
 19:    \[TearDown\]
```  
  
```
 20:    public void PerTestTearDown()
```  
  
```
 21:    {
```  
  
```
 22:        // clean up database
```  
  
```
 23:    }
```  
  
```
 24:  
```  
  
```
 25:    \[TestFixtureTearDown\]
```  
  
```
 26:    public void PerFixtureTearDown()
```  
  
```
 27:    {
```  
  
```
 28:        dbConn.Close();
```  
  
```
 29:        dbConn.Dispose();
```  
  
```
 30:    }
```  
  
```
 31:  
```  
  
```
 32:    \[Test\]
```  
  
```
 33:    public void AccountAccess()
```  
  
```
 34:    {
```  
  
```
 35:        // Uses dbConn
```  
  
```
 36:    }
```  
  
```
 37:  
```  
  
```
 38:    \[Test\]
```  
  
```
 39:    public void EmployeeAccess()
```  
  
```
 40:    {
```  
  
```
 41:        // Uses dbConn
```  
  
```
 42:    }
```  
  
```
 43: }
```  

  
  

In this example, here is the methods run sequence: PerFixtureSetup >> PerTestSetup >> AccountAccess >> PerTestTearDown >> PerFixtureTearDown >> PerFixtureSetup >> PerTestSetup >> EmployeeAccess >> PertestTearDown >> PerFixtureTearDown.

  
  

In this post we tried to elaborate more on the NUnit framework and how we structure and organize test cases in NUnit.