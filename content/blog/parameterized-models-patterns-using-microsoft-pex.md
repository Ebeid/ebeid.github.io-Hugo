---
title: 'Parameterized Models Patterns using Microsoft Pex'
date: 2013-05-02T16:45:00.001-05:00
draft: true
url: 
tags: 
- Microsoft Pex
- Parameterized Unit Tests
- Unit Tests
- Unit testing
---

Pex provides an infrastructure to implement parameterized models. We refer to parameterized models as they build on top of Pex infrastructure to generate new parameters on the fly, which we usually refer as **choices**. Parameterized models can be used to replace traditional mocked-based testing as a single model captures all possible behavior.  
For a modeled component, instead of defining a single input/output pair as with mock objects, a parameterized model can specify a general input/output relationship, and it can use test parameters to act in various ways. In unit testing, mock objects are used to simulate the behavior of external components in order to test each component in isolation.  
Although mock object frameworks have greatly improve the usability in recent years, mock-based testing is still a tedious task. Note that the term mock object is used for somewhat different concepts by developers practicing unit testing. The meaning ranges from very simple (empty) stubs to complex and precise behavior with expected inputs and correctly computed outputs.  
Martin Fowler discusses this in detail [here](http://www.martinfowler.com/articles/mocksArentStubs.html). In this sense, the first parameterized model patterns we present start out as simple stubs, but the patterns allow sophisticated models that assert expected inputs and restrict possible outputs.  
There are many frameworks that make it easy to write mock objects—for example, for .NET. Similar to how NUnit relates to Pex, these existing frameworks make it easy to manage mock objects—for example, by reducing the amount of code that must be written—but they do not help in exploring different behaviors. Note that Pex comes with a simple stubs framework. This framework was designed to be friendly with the kind of code analysis Pex does.