---
title: 'Python Notes – 7 : Files &amp; directories'
date: 2009-03-23T10:12:00.002-05:00
draft: false
url: /2009/03/python-notes-7.html
tags: 
- Python
---

Welcome to our seventh note in our Python learning process. This note will talk specifically about files, directories, and exceptions.

#### Files

Opening a file creates a file object. Syntax is like that:

> \>>> f = open("test.dat","w")

> \>>> print f

> <open file 'test.dat', mode 'w' at fe820>

The first parameter to open is the file name, the second parameter is the mode. Modes are: w for write, r for read.

To write data in the file we invoke the write method on the file object:

> \>>> f.write("Now is the time")

> \>>> f.write("to close the file")

After we done we can close the file like that:

> \>>> f.close()

The read method reads data from the file. With no arguments, it reads the entire contents of the file:

> \>>> text = f.read()

> \>>> print text

> Now is the time to close the file

read can also take an argument that indicates how many characters to read.

If not enough characters are left in the file, read returns the remaining characters. When we get to the end of the file, read returns the empty string:

> \>>> print f.read(5)

> Now i

> \>>> print f.read(1000006)

> s the timeto close the file

> \>>> print f.read()

> \>>>

The write method write data to the file. It takes strings only.

> \>>> x = 52

> \>>> f.write (str(x))

#### Directories

When you create a new file by opening it and writing, the new file goes in the current directory (wherever you were when you ran the program). Similarly, when you open a file for reading, Python looks for it in the current directory. If you want to open a file somewhere else, you have to specify the path to the file, which is the name of the directory (or folder) where the file is located:

> \>>> f = open("/usr/share/dict/words","r")

> \>>> print f.readline()

> Whatever exist

#### glob module

Returns filenames in a directory that match a pattern.

> import glob

> a = glob.glob("\*.html")

> b = glob.glob("image\[0-5\]\*.gif")

Pattern matching is performed using rules of Unix shell. Tilde (~) and variable expansion is not performed.

#### fnmatch module

Matches filenames according to rules of Unix shell.

> import fnmatch

> if fnmatch(filename,"\*.html"):

> ...

Case-sensitivity depends on the operating system.

#### Other File-Related Modules

*   ##### fcntl : Provides access to the fcntl() system call and file-locking operations
    

> import fcntl, FCNTL

> fcntl.flock(f.fileno(),FCNTL.LOCK\_EX) # Lock a file

*   ##### tempfile : Creates temporary files
    
*   ##### gzip : Creates file objects with compression/decompression. Compatible with the GNU gzip program.
    

> import gzip

> f = gzip.open("foo","wb")

> f.write(data)

#### Exceptions

Whenever a runtime error occurs, it creates an exception. Usually, the program stops and Python prints an error message.

> \>>> print 55/0

> ZeroDivisionError: integer division or modulo

We can handle the exception using the try and except statements.

> filename = raw\_input('Enter a file name: ')

> try:

> f = open (filename, "r")

> except:

> print 'There is no file named', filename

The try statement executes the statements in the first block. If no exceptions occur, it ignores the except statement. If any exception occurs, it executes the statements in the except branch and then continues.

If your program detects an error condition, you can make it raise an exception.

> def inputNumber () :

> x = input ('Pick a number: ')

> if x == 17 :

> raise 'BadNumberError', '17 is a bad number'

> return x

The raise statement takes two arguments: the exception type and specific

information about the error. And here how the previous example appears:

> \>>> inputNumber ()

> Pick a number: 17

> BadNumberError: 17 is a bad number

This note talked about files, directories, and exceptions. The next note will go into the object oriented features of Python.