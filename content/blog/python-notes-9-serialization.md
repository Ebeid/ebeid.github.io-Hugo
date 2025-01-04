---
title: 'Python Notes – 9 : Serialization'
date: 2009-03-27T01:53:00.001-05:00
draft: false
url: /2009/03/python-notes-9.html
tags: 
- Python
---

Welcome to our ninth note in our Python learning process. We talked previously about files and how to handle it but we talked about writing and reading only the primitive data types as integers and strings. We also talked about objects and classes. Now, what if we want to write a compound data type or a complex object to a file. This note will talk about writing objects to files, which is called object serialization.

#### pickle

The pickle module is a Python built-in module that object serialization and de-serialization. To store a data structure, use the dump method and then close the file in the usual way:

> \>>> pickle.dump(12.3, f)

> \>>> pickle.dump(\[1,2,3\], f)

> \>>> f.close()

Then we can open the file for reading and load the data structures we dumped:

> \>>> f = open("test.pck","r")

> \>>> x = pickle.load(f)

> \>>> x

> 12.3

> \>>> type(x)

> <type 'float'>

> \>>> y = pickle.load(f)

> \>>> y

> \[1, 2, 3\]

> \>>> type(y)

> <type 'list'>

Each time we invoke load, we get a single value from the file, complete with its original type.

#### What can be serialized and de-serialized

The following types can be serialized and de-serialized using pickle:

*   None, True, and False
*   integers, long integers, floating point numbers, complex numbers
*   normal and Unicode strings
*   tuples, lists, sets, and dictionaries containing only picklable objects
*   functions defined at the top level of a module
*   built-in functions defined at the top level of a module
*   classes that are defined at the top level of a module
*   instances of such classes whose\_\_dict\_\_ or \_\_setstate\_\_() is picklable

#### Things to consider when using pickle

*   Attempts to pickle unpicklable objects will raise the picklingError exception; when this happens, an unspecified number of bytes may have already been written to the underlying file.
*   Trying to pickle a highly recursive data structure may exceed the maximum recursion depth, a RuntimeError will be raised in this case. You can carefully raise this limit with sys.setrecursionlimit().

#### cPickle

The cPickle is an optimized version of pickle written in C, so it can be up to 1000 faster than pickle.

#### marshal

The marshal module can also be used for serialization. Marshal is similar to pickle, but is intended only for simple objects. Can’t handle recursion or class instances. On the plus side, it’s pretty fast if you just want to save simple objects to a file. Data is stored in a binary architecture independent format.To serialize:

> import marshal

> marshal.dump(obj,file)                  # Write obj to file

To unserialize:

> obj = marshal.load(file)

#### shelve

The shelve module provides a persistent dictionary. It is works like a dictionary, but data is stored on disk.

Keys must be strings. Data can be any object serializable with pickle.

> import shelve

> d = shelve.open("data") # Open a ’shelf’

> d\[’foo’\] = 42 # Save data

> x = d\[’bar’\] # Retrieve data

#### Shelf operations

> d\[key\] = obj              # Store an object

> obj = d\[key\]              # Retrieve an object

> del d\[key\]                 # Delete an object

> d.has\_key(key)          # Test for existence of key

> d.keys()                   # Return a list of all keys

> d.close()                  # Close the shelf

In this note will talked about writing objects to files, which is called object serialization. Object serialization is very useful in persisting your application logic to resume its execution later, transfer of execution to remote machine, and many other applications scenarios.