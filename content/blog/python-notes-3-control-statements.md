---
title: 'Python Notes – 3 : Control Statements'
date: 2009-03-19T08:59:00.002-05:00
draft: false
url: /2009/03/python-notes-3.html
tags: 
- Python
---

Welcome to our third note in our Python learning process. In this note we will talk about conditional statements, iteration and keyboard input.

#### Conditional Statements

The normal flow of statements execution is sequential where the interpreter executes the statements in the same sequence that it appears in the script. If your program logic requires a different flow than the that, you should use conditional statements. The syntax looks like:

> if x%2 == 0:

> print x, "is even"

> else:

> print x, "is odd"

The statement indentation is the only statement scope identifier.

Conditional statements can be chained to whatever level you want. The syntax looks like:

> if x < y:

> print x, "is less than", y

> elif x > y:

> print x, "is greater than", y

> else:

> print x, "and", y, "are equal"

elif is an abbreviation of "else if."

Conditional statements can be nested to whatever level you want. Take care of indentation. The syntax looks like:

> if x == y:

> print x, "and", y, "are equal"

> else:

> if x < y:

> print x, "is less than", y

> else:

> print x, "is greater than", y

#### Iteration

Iteration is the way to execute some statements multiple times. The syntax is like that:

> While CONDITION:

> STATEMENTS IN SCOPE

> STATEMENTS IN SCOPE

> STATEMENTS OUT OF WHILE SCOPE

The while will execute the in scope statements until the CONDITION evaluates to false. Example:

> X = 10

> While X != 0:

> Print X

> X = X - 1

> print "Finish"

This will print numbers from 10 to 1 then "Finish".

#### Keyboard input

Python provides built-in functions that get input from the keyboard. The simplest is called raw input. When this function is called, the program stops and waits for the user to type something. When the user presses Return or the Enter key, the program resumes and raw input returns what the user typed as

a string:

> \>>> input = raw\_input ()

> What are you waiting for?

> \>>> print input

> What are you waiting for?

In this note we talked about conditional statements, iteration and keyboard input. These are another way of organizing your program logic to satisfy accomplish your program goal. We will continue our learning in the upcoming notes.