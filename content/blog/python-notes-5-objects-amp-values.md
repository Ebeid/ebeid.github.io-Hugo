---
title: 'Python Notes – 5 : Objects &amp; Values'
date: 2009-03-23T07:49:00.002-05:00
draft: false
url: /2009/03/python-notes-5.html
tags: 
- Python
---

Welcome to our fifth note in our Python learning process. In this note we will talk about one of the core concepts of the Python language semantics .

Objects and Values

An object is something a variable can refer to. Every object has a unique identifier, which we can obtain with the id function.

> \>>> a = "banana"

> \>>> b = "banana"

> \>>> id(a)

> 135044008

> \>>> id(b)

> 135044008

Interestingly, lists behave differently. When we create two lists, we get two

objects:

> \>>> a = \[1, 2, 3\]

> \>>> b = \[1, 2, 3\]

> \>>> id(a)

> 135045528

> \>>> id(b)

> 135041704

Since both a and b refer to the same object, changes made to the object through one of them appear when you access the object through the other. This is called aliasing.

> \>>> a = \[1, 2, 3\]

> \>>> b = \[1, 2, 3\]

> \>>> b\[0\] = 5

> \>>> print a

> \[5, 2, 3\]

This brief note is just to differentiate between values and objects. Objects not only the instances we create of classes, some language types treated as objects and others treated as values.

We will discuss object oriented in a separate note within days.