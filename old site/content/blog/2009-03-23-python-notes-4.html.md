--- 
title: "Python Notes – 4 : Lists" 
date: '2009-03-23T05:13:00.002-05:00'
modified_time: '2009-05-15T02:05:38.812-05:00' 
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-1084417766038192547
blogger_orig_url: http://ebeid-soliman.blogspot.com/2009/03/python-notes-4.html 
---

Welcome to our third note in our Python learning process. In this note
we will talk mainly about lists, its functions and how to use it.

#### Lists - Creation

A list is an ordered set of values, where each value is identified by an
index. The values that make up a list are called its elements. You could
create it like:

> <span style="color: #0000ff">&gt;&gt;&gt; X = \[12, 56, 87\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; print X</span>

> <span style="color: #0000ff">\[12, 56, 87\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; Y = \["one", "three",
> "five"\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; print Y</span>

> <span style="color: #0000ff">\["one", "three", "five"\]</span>

The list elements don't have to be the same type.

> <span style="color: #0000ff">\["hello", 2.0, 5, \[10, 20\]\]</span>

A list within another list is said to be nested.

Another way of creating special list of consecutive integers:

> <span style="color: #0000ff">&gt;&gt;&gt; range(1,5)</span>

> <span style="color: #0000ff">\[1, 2, 3, 4\]</span>

If there is no start of the range, it will create starting from the 0

> <span style="color: #0000ff">&gt;&gt;&gt; range(10)</span>

> <span style="color: #0000ff">\[0, 1, 2, 3, 4, 5, 6, 7, 8, 9\]</span>

If there is a third argument, it specifies the space between successive
values,

which is called the step size

> <span style="color: #0000ff">&gt;&gt;&gt; range(1, 10, 2)</span>

> <span style="color: #0000ff">\[1, 3, 5, 7, 9\]</span>

#### Lists - Accessing elements

You access list elements by index. Indices starts with zero. Indices
could be any integer expression.

> <span style="color: #0000ff">&gt;&gt;&gt; numbers = range(1,10)</span>

> <span style="color: #0000ff">&gt;&gt;&gt; print numbers\[0\]</span>

> <span style="color: #0000ff">1</span>

> <span style="color: #0000ff">&gt;&gt;&gt; print numbers\[5-3\]</span>

> <span style="color: #0000ff">3</span>

#### Lists - Length

You can get the list length using len() method. Syntax like that:

> <span style="color: #0000ff">&gt;&gt;&gt; len(numbers)</span>

> <span style="color: #0000ff">9</span>

Although a list can contain another list, the nested list still counts
as a single

element. The length of this list is four:

> <span style="color: #0000ff">\['spam!', 1, \['Brie', 'Roquefort', 'Pol
> le Veq'\], \[1, 2, 3\]\]</span>

#### Lists - operators

in is a boolean operator that tests membership in a sequence.

> <span style="color: #0000ff">&gt;&gt;&gt; horsemen = \['war',
> 'famine', 'pestilence', 'death'\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; 'pestilence' in
> horsemen</span>

> <span style="color: #0000ff">1</span>

> <span style="color: #0000ff">&gt;&gt;&gt; 'debauchery' in
> horsemen</span>

> <span style="color: #0000ff">0</span>

#### Lists - for loops

The syntax is like:

> <span style="color: #0000ff">for VARIABLE in LIST:</span>

> <span style="color: #0000ff">BODY</span>

> <span style="
> color: #0000ff"></span>
>
> <span style="color: #0000ff">for horseman in horsemen:</span>

> <span style="color: #0000ff">print horseman</span>

This is equivalent to:

> <span style="color: #0000ff">i = 0</span>

> <span style="color: #0000ff">while i &lt; len(LIST):</span>

> <span style="color: #0000ff">VARIABLE = LIST\[i\]</span>

> <span style="color: #0000ff">BODY</span>

> <span style="color: #0000ff">i = i + 1</span>

Any list expression can be used in a for loop:

> <span style="color: #0000ff">for number in range(20):</span>

> <span style="color: #0000ff">if number % 2 == 0:</span>

> <span style="color: #0000ff">print number</span>

#### List - operations

The + operator concatenates lists:

> <span style="color: #0000ff">&gt;&gt;&gt; a = \[1, 2, 3\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; b = \[4, 5, 6\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; c = a + b</span>

> <span style="color: #0000ff">&gt;&gt;&gt; print c</span>

> <span style="color: #0000ff">\[1, 2, 3, 4, 5, 6\]</span>

Similarly, the \* operator repeats a list a given number of times:

> <span style="color: #0000ff">&gt;&gt;&gt; \[0\] \* 4</span>

> <span style="color: #0000ff">\[0, 0, 0, 0\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; \[1, 2, 3\] \* 3</span>

> <span style="color: #0000ff">\[1, 2, 3, 1, 2, 3, 1, 2, 3\]</span>

The head function takes a list as a parameter and returns the first
element.

> <span style="color: #0000ff">&gt;&gt;&gt; a = \[1, 2, 3\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; head(a)</span>

> <span style="color: #0000ff">1</span>

#### List - slices

> <span style="color: #0000ff">&gt;&gt;&gt; list = \['a', 'b', 'c', 'd',
> 'e', 'f'\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; list\[1:3\]</span>

> <span style="color: #0000ff">\['b', 'c'\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; list\[:4\]</span>

> <span style="color: #0000ff">\['a', 'b', 'c', 'd'\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; list\[3:\]</span>

> <span style="color: #0000ff">\['d', 'e', 'f'\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; list\[:\]</span>

> <span style="color: #0000ff">\['a', 'b', 'c', 'd', 'e', 'f'\]</span>

#### List - deletion

del removes an element from a list:

> <span style="color: #0000ff">&gt;&gt;&gt; a = \['one', 'two',
> 'three'\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; del a\[1\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; a</span>

> <span style="color: #0000ff">\['one', 'three'\]</span>

You can use a slice as an index for del:

> <span style="color: #0000ff">&gt;&gt;&gt; list = \['a', 'b', 'c', 'd',
> 'e', 'f'\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; del list\[1:5\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; print list</span>

<span style="color: #0000ff">\['a', 'f'\]</span>

-   Strings are lists and can be treated the same way you treat lists.

#### Nested lists

A nested list is a list that appears as an element in another list. In
this list, the

three-eth element is a nested list:

> <span style="color: #0000ff">&gt;&gt;&gt; list = \["hello", 2.0, 5,
> \[10, 20\]\]</span>

To extract an element from the nested list, we can proceed in two steps:

> <span style="color: #0000ff">&gt;&gt;&gt; elt = list\[3\]</span>

> <span style="color: #0000ff">&gt;&gt;&gt; elt\[0\]</span>

> <span style="color: #0000ff">10</span>

Or we can combine them:

> <span style="color: #0000ff">&gt;&gt;&gt; list\[3\]\[1\]</span>

> <span style="color: #0000ff">20</span>

In this note we talked mainly lists which are very powerful feature in
Python. We will continue our learning in the upcoming notes.
