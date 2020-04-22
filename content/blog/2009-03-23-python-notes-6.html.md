--- 
title: "Python Notes – 6 : Tuples & Dictionaries" 
date: '2009-03-23T09:06:00.001-05:00' 
tags: 
    - Python 
modified_time: '2009-05-15T01:58:53.222-05:00' 
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-6064389959870668619
blogger_orig_url: http://ebeid-soliman.blogspot.com/2009/03/python-notes-6.html 
---

Welcome to our sixth note in our Python learning process. In this note
we will talk about tuples and dictionaries.

#### Tuples

Tuples are similar to lists but its elements can't be modified.
Syntactically, a tuple is a comma-separated list of values:

> &gt;&gt;&gt; tuple = 'a', 'b', 'c', 'd', 'e'

Although it is not necessary, it is conventional to enclose tuples in
parentheses:

> &gt;&gt;&gt; tuple = ('a', 'b', 'c', 'd', 'e')

To create a tuple with a single element, we have to include the ¯nal
comma:

> &gt;&gt;&gt; t1 = ('a',)

> &gt;&gt;&gt; type(t1)

> &lt;type 'tuple'&gt;

Without the comma, Python treats ('a') as a string in parentheses:

> &gt;&gt;&gt; t2 = ('a')

> &gt;&gt;&gt; type(t2)

> &lt;type 'string'&gt;

#### Tuple assignment

Tuples assignment could be used to perform multiple assignments in one
statement. For example, to swap a and b we can make it like that:

> &gt;&gt;&gt; a, b = b, a

The left side is a tuple of variables; the right side is a tuple of
values. Each value is assigned to its respective variable.

#### Dictionaries

Dictionaries are like lists and tuples in that all of them are compound
types.

Dictionaries are different than lists and tuples in that it can use any
immutable type as an index not only integers like tuples and lists.
Dictionaries are not ordered.

To create an empty dictionary and then add elements to it:

> &gt;&gt;&gt; eng2sp = {}

> &gt;&gt;&gt; eng2sp\['one'\] = 'uno'

> &gt;&gt;&gt; eng2sp\['two'\] = 'dos'

> &gt;&gt;&gt; print eng2sp

> {'one': 'uno', 'two': 'dos'}

You can also create the dictionary by providing a list of key-value
pairs:

> &gt;&gt;&gt; eng2sp = {'one': 'uno', 'two': 'dos', 'three': 'tres'}

> &gt;&gt;&gt; print eng2sp

> {'one': 'uno', 'three': 'tres', 'two': 'dos'}

#### Dictionary Operations

del statement removes a key-value pair from a dictionary.

> &gt;&gt;&gt; inventory = {'apples': 430, 'bananas': 312, 'oranges':
> 525, 'pears': 217}

> &gt;&gt;&gt; print inventory

> {'oranges': 525, 'apples': 430, 'pears': 217, 'bananas': 312}

> &gt;&gt;&gt; del inventory\['pears'\]

> &gt;&gt;&gt; print inventory

> {'oranges': 525, 'apples': 430, 'bananas': 312}

The len function also works on dictionaries; it returns the number of
key-value pairs:

> &gt;&gt;&gt; len(inventory)

> 4

#### Dictionary methods

The keys method takes a dictionary and returns a list of the keys.

> &lt; p&gt;&gt;&gt;&gt; eng2sp.keys()

> \['one', 'three', 'two'\]

The values method is similar; it returns a list of the values in the
dictionary:

> &gt;&gt;&gt; eng2sp.values()

> \['uno', 'tres', 'dos'\]

The items method returns both, in the form of a list of tuples|one for
each key-value pair:

> &gt;&gt;&gt; eng2sp.items()

> \[('one','uno'), ('three', 'tres'), ('two', 'dos')\]

The method has\_key takes a key and returns true (1) if the key appears
in the dictionary:

> &gt;&gt;&gt; eng2sp.has\_key('one')

> 1

> &gt;&gt;&gt; eng2sp.has\_key('deux')

> 0

#### Aliasing and copying

Dictionaries are objects that can be aliased like that:

> &gt;&gt;&gt; opposites = {'up': 'down', 'right': 'wrong', 'true':
> 'false'}

> &gt;&gt;&gt; alias = opposites

Or copied to a new fresh copy like that:

> &gt;&gt;&gt; copy = opposites.copy()

This note completed the compound data types talk we started before with
lists. Lists, tuples, and dictionaries are the compound data types that
Python provides. You can use them as is or you can use them to build a
more complex data types and containers.
