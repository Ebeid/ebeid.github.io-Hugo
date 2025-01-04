--- 
title: "Python Notes – 7 : Files & directories" 
date: '2009-03-23T10:12:00.002-05:00' 
tags: 
    - Python 
modified_time: '2009-05-15T01:57:36.571-05:00' 
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-8598980118992725030
blogger_orig_url: http://ebeid-soliman.blogspot.com/2009/03/python-notes-7.html 
---

Welcome to our seventh note in our Python learning process. This note
will talk specifically about files, directories, and exceptions.

#### Files

Opening a file creates a file object. Syntax is like that:

> <span style="color: #0000ff">&gt;&gt;&gt; f =
> open("test.dat","w")</span>

> <span style="color: #0000ff">&gt;&gt;&gt; print f</span>

> <span style="color: #0000ff">&lt;open file 'test.dat', mode 'w' at
> fe820&gt;</span>

The first parameter to open is the file name, the second parameter is
the mode. Modes are: w for write, r for read.

To write data in the file we invoke the write method on the file object:

> <span style="color: #0000ff">&gt;&gt;&gt; f.write("Now is the
> time")</span>

> <span style="color: #0000ff">&gt;&gt;&gt; f.write("to close the
> file")</span>

After we done we can close the file like that:

> <span style="color: #0000ff">&gt;&gt;&gt; f.close()</span>

The read method reads data from the file. With no arguments, it reads
the entire contents of the file:

> <span style="color: #0000ff">&gt;&gt;&gt; text = f.read()</span>

> <span style="color: #0000ff">&gt;&gt;&gt; print text</span>

> <span style="color: #0000ff">Now is the time to close the file</span>

read can also take an argument that indicates how many characters to
read.

If not enough characters are left in the file, read returns the
remaining characters. When we get to the end of the file, read returns
the empty string:

> <span style="color: #0000ff">&gt;&gt;&gt; print f.read(5)</span>

> <span style="color: #0000ff">Now i</span>

> <span style="color: #0000ff">&gt;&gt;&gt; print f.read(1000006)</span>

> <span style="color: #0000ff">s the timeto close the file</span>

> <span style="color: #0000ff">&gt;&gt;&gt; print f.read()</span>

> <span style="color: #0000ff">&gt;&gt;&gt;</span>

The write method write data to the file. It takes strings only.

> <span style="color: #0000ff">&gt;&gt;&gt; x = 52</span>

> <span style="color: #0000ff">&gt;&gt;&gt; f.write (str(x))</span>

#### Directories

When you create a new file by opening it and writing, the new file goes
in the current directory (wherever you were when you ran the program).
Similarly, when you open a file for reading, Python looks for it in the
current directory. If you want to open a file somewhere else, you have
to specify the path to the file, which is the name of the directory (or
folder) where the file is located:

> <span style="color: #0000ff">&gt;&gt;&gt; f =
> open("/usr/share/dict/words","r")</span>

> <span style="color: #0000ff">&gt;&gt;&gt; print f.readline()</span>

> <span style="color: #0000ff">Whatever exist</span>

#### glob module

Returns filenames in a directory that match a pattern.

> <span style="color: #0000ff">import glob</span>

> <span style="color: #0000ff">a = glob.glob("\*.html")</span>

> <span style="color: #0000ff">b =
> glob.glob("image\[0-5\]\*.gif")</span>

Pattern matching is performed using rules of Unix shell. Tilde (~) and
variable expansion is not performed.

#### fnmatch module

Matches filenames according to rules of Unix shell.

> <span style="color: #0000ff"> import fnmatch</span>

> <span style="color: #0000ff">if fnmatch(filename,"\*.html"):</span>

> <span style="color: #0000ff">...</span>

Case-sensitivity depends on the operating system.

#### Other File-Related Modules

-   ##### fcntl : Provides access to the fcntl() system call and file-locking operations

> <span style="color: #0000ff">import fcntl, FCNTL</span>

> <span style="color: #0000ff">fcntl.flock(f.fileno(),FCNTL.LOCK\_EX) \#
> Lock a file</span>

-   ##### tempfile : Creates temporary files

-   ##### gzip : Creates file objects with compression/decompression. Compatible with the GNU gzip program.

> <span style="color: #0000ff">import gzip</span>

> <span style="color: #0000ff">f = gzip.open("foo","wb")</span>

> <span style="color: #0000ff">f.write(data)</span>

#### Exceptions

Whenever a runtime error occurs, it creates an exception. Usually, the
program stops and Python prints an error message.

> <span style="color: #0000ff">&gt;&gt;&gt; print 55/0</span>

> <span style="color: #0000ff">ZeroDivisionError: integer division or
> modulo</span>

We can handle the exception using the try and except statements.

> <span style="color: #0000ff">filename = raw\_input('Enter a file name:
> ')</span>

> <span style="color: #0000ff">try:</span>

> <span style="color: #0000ff">f = open (filename, "r")</span>

> <span style="color: #0000ff">except:</span>

> <span style="color: #0000ff">print 'There is no file named',
> filename</span>

The try statement executes the statements in the first block. If no
exceptions occur, it ignores the except statement. If any exception
occurs, it executes the statements in the except branch and then
continues.

If your program detects an error condition, you can make it raise an
exception.

> <span style="color: #0000ff">def inputNumber () :</span>

> <span style="color: #0000ff">x = input ('Pick a number: ')</span>

> <span style="color: #0000ff">if x == 17 :</span>

> <span style="color: #0000ff">raise 'BadNumberError', '17 is a bad
> number'</span>

> <span style="color: #0000ff">return x</span>

The raise statement takes two arguments: the exception type and specific

information about the error. And here how the previous example appears:

> <span style="color: #0000ff">&gt;&gt;&gt; inputNumber ()</span>

> <span style="color: #0000ff">Pick a number: 17</span>

> <span style="color: #0000ff">BadNumberError: 17 is a bad number</span>

This note talked about files, directories, and exceptions. The next note
will go into the object oriented features of Python.
