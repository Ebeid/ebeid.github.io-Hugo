--- 
title: "Python Notes – 3 : Control Statements" 
date: '2009-03-19T08:59:00.002-05:00' 
tags: 
    - Python 
modified_time: '2009-05-15T02:16:40.511-05:00' 
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-8075616602984890109
blogger_orig_url: http://ebeid-soliman.blogspot.com/2009/03/python-notes-3.html 
---

Welcome to our third note in our Python learning process. In this note
we will talk about conditional statements, iteration and keyboard input.

#### Conditional Statements

The normal flow of statements execution is sequential where the
interpreter executes the statements in the same sequence that it appears
in the script. If your program logic requires a different flow than the
that, you should use conditional statements. The syntax looks like:

> <span style="color: #0000ff">if x%2 == 0:</span>

> <span style="color: #0000ff">print x, "is even"</span>

> <span style="color: #0000ff">else:</span>

> <span style="color: #0000ff">print x, "is odd"</span>

The statement indentation is the only statement scope identifier.

Conditional statements can be chained to whatever level you want. The
syntax looks like:

> <span style="color: #0000ff">if x &lt; y:</span>

> <span style="color: #0000ff">print x, "is less than", y</span>

> <span style="color: #0000ff">elif x &gt; y:</span>

> <span style="color: #0000ff">print x, "is greater than", y</span>

> <span style="color: #0000ff">else:</span>

> <span style="color: #0000ff">print x, "and", y, "are equal"</span>

elif is an abbreviation of "else if."

Conditional statements can be nested to whatever level you want. Take
care of indentation. The syntax looks like:

> <span style="color: #0000ff">if x == y:</span>

> <span style="color: #0000ff">print x, "and", y, "are equal"</span>

> <span style="color: #0000ff">else:</span>

> <span style="color: #0000ff">if x &lt; y:</span>

> <span style="color: #0000ff">print x, "is less than", y</span>

> <span style="color: #0000ff">else:</span>

> <span style="color: #0000ff">print x, "is greater than", y</span>

#### Iteration

Iteration is the way to execute some statements multiple times. The
syntax is like that:

> <span style="color: #0000ff">While CONDITION:</span>

> <span style="color: #0000ff">STATEMENTS IN SCOPE</span>

> <span style="color: #0000ff">STATEMENTS IN SCOPE</span>

> <span style="color: #0000ff">STATEMENTS OUT OF WHILE SCOPE</span>

The while will execute the in scope statements until the CONDITION
evaluates to false. Example:

> <span style="color: #0000ff">X = 10</span>

> <span style="color: #0000ff">While X != 0:</span>

> <span style="color: #0000ff">Print X</span>

> <span style="color: #0000ff">X = X - 1</span>

> <span style="color: #0000ff">print "Finish"</span>

This will print numbers from 10 to 1 then "Finish".

#### Keyboard input

Python provides built-in functions that get input from the keyboard. The
simplest is called raw input. When this function is called, the program
stops and waits for the user to type something. When the user presses
Return or the Enter key, the program resumes and raw input returns what
the user typed as

a string:

> <span style="color: #0000ff">&gt;&gt;&gt; input = raw\_input ()</span>

> <span style="color: #0000ff">What are you waiting fo r?</span>

> <span style="color: #0000ff">&gt;&gt;&gt; print input</span>

> <span style="color: #0000ff">What are you waiting for?</span>

In this note we talked about conditional statements, iteration and
keyboard input. These are another way of organizing your program logic
to satisfy accomplish your program goal. We will continue our learning
in the upcoming notes.
