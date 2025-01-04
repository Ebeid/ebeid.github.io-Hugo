---
title: 'Python Notes – 6 : Tuples &amp; Dictionaries'
date: 2009-03-23T09:06:00.001-05:00
draft: false
url: /2009/03/python-notes-6.html
tags: 
- Python
---

Welcome to our sixth note in our Python learning process. In this note we will talk about tuples and dictionaries.

#### Tuples

Tuples are similar to lists but its elements can't be modified. Syntactically, a tuple is a comma-separated list of values:

> \>>> tuple = 'a', 'b', 'c', 'd', 'e'

Although it is not necessary, it is conventional to enclose tuples in parentheses:

> \>>> tuple = ('a', 'b', 'c', 'd', 'e')

To create a tuple with a single element, we have to include the ¯nal comma:

> \>>> t1 = ('a',)

> \>>> type(t1)

> <type 'tuple'>

Without the comma, Python treats ('a') as a string in parentheses:

> \>>> t2 = ('a')

> \>>> type(t2)

> <type 'string'>

#### Tuple assignment

Tuples assignment could be used to perform multiple assignments in one statement. For example, to swap a and b we can make it like that:

> \>>> a, b = b, a

The left side is a tuple of variables; the right side is a tuple of values. Each value is assigned to its respective variable.

#### Dictionaries

Dictionaries are like lists and tuples in that all of them are compound types.

Dictionaries are different than lists and tuples in that it can use any immutable type as an index not only integers like tuples and lists. Dictionaries are not ordered.

To create an empty dictionary and then add elements to it:

> \>>> eng2sp = {}

> \>>> eng2sp\['one'\] = 'uno'

> \>>> eng2sp\['two'\] = 'dos'

> \>>> print eng2sp

> {'one': 'uno', 'two': 'dos'}

You can also create the dictionary by providing a list of key-value pairs:

> \>>> eng2sp = {'one': 'uno', 'two': 'dos', 'three': 'tres'}

> \>>> print eng2sp

> {'one': 'uno', 'three': 'tres', 'two': 'dos'}

#### Dictionary Operations

del statement removes a key-value pair from a dictionary.

> \>>> inventory = {'apples': 430, 'bananas': 312, 'oranges': 525, 'pears': 217}

> \>>> print inventory

> {'oranges': 525, 'apples': 430, 'pears': 217, 'bananas': 312}

> \>>> del inventory\['pears'\]

> \>>> print inventory

> {'oranges': 525, 'apples': 430, 'bananas': 312}

The len function also works on dictionaries; it returns the number of key-value pairs:

> \>>> len(inventory)

> 4

#### Dictionary methods

The keys method takes a dictionary and returns a list of the keys.

> \>>> eng2sp.keys()

> \['one', 'three', 'two'\]

The values method is similar; it returns a list of the values in the dictionary:

> \>>> eng2sp.values()

> \['uno', 'tres', 'dos'\]

The items method returns both, in the form of a list of tuples|one for each key-value pair:

> \>>> eng2sp.items()

> \[('one','uno'), ('three', 'tres'), ('two', 'dos')\]

The method has\_key takes a key and returns true (1) if the key appears in the dictionary:

> \>>> eng2sp.has\_key('one')

> 1

> \>>> eng2sp.has\_key('deux')

> 0

#### Aliasing and copying

Dictionaries are objects that can be aliased like that:

> \>>> opposites = {'up': 'down', 'right': 'wrong', 'true': 'false'}

> \>>> alias = opposites

Or copied to a new fresh copy like that:

> \>>> copy = opposites.copy()

This note completed the compound data types talk we started before with lists. Lists, tuples, and dictionaries are the compound data types that Python provides. You can use them as is or you can use them to build a more complex data types and containers.