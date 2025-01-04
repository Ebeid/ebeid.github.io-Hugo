---
title: 'Python Notes – 4 : Lists'
date: 2009-03-23T05:13:00.002-05:00
draft: false
url: /2009/03/python-notes-4.html
tags: 
- Python
---

Welcome to our third note in our Python learning process. In this note we will talk mainly about lists, its functions and how to use it.

#### Lists - Creation

A list is an ordered set of values, where each value is identified by an index. The values that make up a list are called its elements. You could create it like:

> \>>> X = \[12, 56, 87\]

> \>>> print X

> \[12, 56, 87\]

> \>>> Y = \["one", "three", "five"\]

> \>>> print Y

> \["one", "three", "five"\]

The list elements don't have to be the same type.

> \["hello", 2.0, 5, \[10, 20\]\]

A list within another list is said to be nested.

Another way of creating special list of consecutive integers:

> \>>> range(1,5)

> \[1, 2, 3, 4\]

If there is no start of the range, it will create starting from the 0

> \>>> range(10)

> \[0, 1, 2, 3, 4, 5, 6, 7, 8, 9\]

If there is a third argument, it specifies the space between successive values,

which is called the step size

> \>>> range(1, 10, 2)

> \[1, 3, 5, 7, 9\]

#### Lists - Accessing elements

You access list elements by index. Indices starts with zero. Indices could be any integer expression.

> \>>> numbers = range(1,10)

> \>>> print numbers\[0\]

> 1

> \>>> print numbers\[5-3\]

> 3

#### Lists - Length

You can get the list length using len() method. Syntax like that:

> \>>> len(numbers)

> 9

Although a list can contain another list, the nested list still counts as a single

element. The length of this list is four:

> \['spam!', 1, \['Brie', 'Roquefort', 'Pol le Veq'\], \[1, 2, 3\]\]

#### Lists - operators

in is a boolean operator that tests membership in a sequence.

> \>>> horsemen = \['war', 'famine', 'pestilence', 'death'\]

> \>>> 'pestilence' in horsemen

> 1

> \>>> 'debauchery' in horsemen

> 0

#### Lists - for loops

The syntax is like:

> for VARIABLE in LIST:

> BODY

> for horseman in horsemen:

> print horseman

This is equivalent to:

> i = 0

> while i < len(LIST):

> VARIABLE = LIST\[i\]

> BODY

> i = i + 1

Any list expression can be used in a for loop:

> for number in range(20):

> if number % 2 == 0:

> print number

#### List - operations

The + operator concatenates lists:

> \>>> a = \[1, 2, 3\]

> \>>> b = \[4, 5, 6\]

> \>>> c = a + b

> \>>> print c

> \[1, 2, 3, 4, 5, 6\]

Similarly, the \* operator repeats a list a given number of times:

> \>>> \[0\] \* 4

> \[0, 0, 0, 0\]

> \>>> \[1, 2, 3\] \* 3

> \[1, 2, 3, 1, 2, 3, 1, 2, 3\]

The head function takes a list as a parameter and returns the first element.

> \>>> a = \[1, 2, 3\]

> \>>> head(a)

> 1

#### List - slices

> \>>> list = \['a', 'b', 'c', 'd', 'e', 'f'\]

> \>>> list\[1:3\]

> \['b', 'c'\]

> \>>> list\[:4\]

> \['a', 'b', 'c', 'd'\]

> \>>> list\[3:\]

> \['d', 'e', 'f'\]

> \>>> list\[:\]

> \['a', 'b', 'c', 'd', 'e', 'f'\]

#### List - deletion

del removes an element from a list:

> \>>> a = \['one', 'two', 'three'\]

> \>>> del a\[1\]

> \>>> a

> \['one', 'three'\]

You can use a slice as an index for del:

> \>>> list = \['a', 'b', 'c', 'd', 'e', 'f'\]

> \>>> del list\[1:5\]

> \>>> print list

> \['a', 'f'\]

*   Strings are lists and can be treated the same way you treat lists.

#### Nested lists

A nested list is a list that appears as an element in another list. In this list, the

three-eth element is a nested list:

> \>>> list = \["hello", 2.0, 5, \[10, 20\]\]

To extract an element from the nested list, we can proceed in two steps:

> \>>> elt = list\[3\]

> \>>> elt\[0\]

> 10

Or we can combine them:

> \>>> list\[3\]\[1\]

> 20

In this note we talked mainly lists which are very powerful feature in Python. We will continue our learning in the upcoming notes.