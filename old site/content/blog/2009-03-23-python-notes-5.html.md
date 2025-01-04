--- 
title: "Python Notes – 5 : Objects & Values" 
date: '2009-03-23T07:49:00.002-05:00' 
tags: 
    - Python 
modified_time: '2009-05-15T02:00:50.437-05:00' 
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-3164749506609126737
blogger_orig_url: http://ebeid-soliman.blogspot.com/2009/03/python-notes-5.html 
---

Welcome to our fifth note in our Python learning process. In this note
we will talk about one of the core concepts of the Python language
semantics .

Objects and Values

An object is something a variable can refer to. Every object has a
unique identifier, which we can obtain with the id function.

> <span style="color: #0000ff">&gt;&gt;&gt; a = "banana"</span>

> <span style="color: #0000ff">&gt;&gt;&gt; b = "banana"</span>

> <span style="color: #0000ff">&gt;&gt;&gt; id(a)</span>

> <span style="color: #0000ff">135044008</span>

> <span style="color: #0000ff">&gt;&gt;&gt; id(b)</span>

> <span style="color: #0000ff">135044008</span>

Interestingly, lists behave differently. When we create two lists, we
get two

objects:

> <span style="color: #0000ff">&gt;&gt;&gt; a = \[1, 2, 3\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; b = \[1, 2, 3\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; id(a)</span>

> <span style="color: #0000ff">135045528</span>

> <span style="color: #0000ff">&gt;&gt;&gt; id(b)</span>

> <span style="color: #0000ff">135041704</span>

Since both a and b refer to the same object, changes made to the object
through one of them appear when you access the object through the other.
This is called aliasing.

> <span style="color: #0000ff">&gt;&gt;&gt; a = \[1, 2, 3\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; b = \[1, 2, 3\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; b\[0\] = 5</span>

> <span style="color: #0000ff">&gt;&gt;&gt; print a</span>

> <span style="color: #0000ff">\[5, 2, 3\]</span>

This brief note is just to differentiate between values and objects.
Objects not only the instances we create of classes, some language types
treated as objects and others treated as values.

We will discuss object oriented in a separate note within days.
