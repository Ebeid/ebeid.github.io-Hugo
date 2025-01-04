---
title: 'Python Notes – 2 : Variables, Statements, Expressions, Operators, and Functions'
date: 2009-03-18T15:25:00.001-05:00
draft: false
url: /2009/03/python-notes-2.html
tags: 
- Python
---

Welcome to our second note in our Python learning process. In this note we will talk about variables, statements, expressions, operators, comments, and functions. These are the very basic building blocks of you programs whatever its final size

#### Variables

The assignment statement creates new variables and gives them values

> \>>> message = "What's up, Doc?"

> \>>> n = 17

> \>>> pi = 3.14159

Python is a dynamically typed language. Which means that variables' types don't have to be defined before the variables use. The python interpreter figure out what type a variable is when you first assign it a value.

#### Variables naming

*   Variable name can contain letters, numbers, and underscore.
*   Variable name must begin with letter.
*   Variable names are case-sensitive ( x different than X ).
*   Variable names can't be one of the Python language reserved words, which are :

and

continue

else

for

import

not

raise

assert

def

except

from

in

or

return

break

def

exec

global

is

pass

try

class

elif

finally

if

lambda

print

while

#### Statements

A statement is an instruction that the Python interpreter can execute. A Python script is a sequence of statements. The results appear one at a time as the statements execute.

For example, the script

> \>>> print 1

> \>>> 1

> \>>> x = 2

> \>>> print x

> \>>> 2

#### Expressions

An expression is a combination of values, variables, and operators. If you type an expression on the command line, the interpreter evaluates it and displays the result:

> \>>> 1 + 1

> 2

#### Boolean Expressions

A boolean expression is an expression that is either true or false. Boolean expressions are expressions that uses logical operators. There are three logical operators: and, or, not. The operands of logical operands should be boolean expressions. In Python there is no boolean data type instead 0, '', \[\], (), {}, and None are false in a boolean context; everything else is true. The absence of boolean data types results in the following behavior of logical operators:

*   All the behaviors depends on the order of expressions evaluation, which is from left to right.
*   and : returns the first false value, if all values are true, returns the last value.

> \>>> 'a' and 'b'

> 'b'

> \>>> ' ' and 'b'

> ' '

> \>>> 'a' and 'b' and 'c'

> 'c'

*   or : returns the first true value, if all values are false, returns the last value

> \>>> 'a' or 'b'

> 'a'

> \>>> ' ' or 'b'

> 'b'

> \>>> ' ' or \[\] or {}

> {}

*   not : evaluates the boolean expression that follows it and inverts it whole value.

> \>>> not (1 and 0)

> True

> \>>> not (1 or 0)

> False

#### Operators and operands

Operators are special symbols that represent computations like addition and multiplication. The values the operator uses are called operands.

The symbols +, -, and /, and the use of parenthesis for grouping, mean in

Python what they mean in mathematics. The asterisk (\*) is the symbol for multiplication, and \*\* is the symbol for exponentiation.

#### Order of operations

When more than one operator appears in an expression, the order of evaluation depends on the rules of precedence. The following is operators from highest precedence to lower precedence:

*   Parentheses
*   Exponentiation
*   Multiplication / Division
*   Addition / Subtraction

Operators with the same precedence are evaluated from left to right.

#### Comments

Comments start with #.

#### Built-in Functions

Here are some of the built-in functions available in Python:

*   Type conversion functions which converts values from one type to another. Like:
    *   int() :

> \>>> int("32")

> 32

> \>>> int("Hello")

> ValueError: invalid literal for int(): Hello

*   float():

> \>>> float(32)

> 32.0

> \>>> float("3.14159")

> 3.14159

*   str():

> \>>> str(32)

> '32'

> \>>> str(3.14149)

> '3.14149'

*   Math functions which provides most of the familiar mathematical functions. These functions are implemented in a module called math, we will talk about modules soon. But for now, if you want to use these functions, you have to import the math module. This is very straight foreword, using following statement
    *   \>>> import math
    *   After the import statement, you can simply call the math functions.

> \>>> decibel = math.log10 (17.0)

> \>>> angle = 1.5

> \>>> height = math.sin(angle)

> \>>> degrees = 45

> \>>> angle = degrees \* 2 \* math.pi / 360.0

> \>>> math.sin(angle)

> 0.707106781187

> \>>> math.sqrt(2) / 2.0

> 0.707106781187

There are many other built-in functions, we mentioned these two types just as examples.

#### Creating your own functions

A function is a named sequence of statements that performs a desired operation. This operation is specified in a function definition.

The syntax for a function definition is:

def FUNCTION\_NAME( LIST OF PARAMETERS ):

> STATEMENTS

*   def is a keyword.
*   FUNCTION\_NAME could be anything except Python keywords.
*   LIST OF PARAMETERS are the ordered list parameters the function needs to operate. The empty parentheses indicate no parameters needed.
*   The function body doesn't have starting or ending characters (like "{" and "}" in C like languages ). Indentation is the only scope identifier for statements in Python. The first statement that doesn't follow the indentation, will be considered out of the function and will mark the function termination.

> \# just to show the function scope and structure

> def sample\_func():

>     Print "we are in the function body scope"

>     Print "we still in the function scope"

> Print "we are out of the function scope"

> \# another function with parameters
> 
> def sum(x, y):

>     print x + y

*   To call a function just use the function name followed by the list of parameters between parentheses

> \>>> sample\_func()

> \>>> sum(1,2)

> 3

*   Functions can call other functions in their body.
*   Functions can return values to its caller

> def sum(x,y):

> return x +y

> def print\_sum(x,y):

> print sum(x,y)

> print\_sum(2,3)

> 5

*   When you create a local variable inside a function, it only exists inside the function, and you cannot use it outside. The following will generate a run-time error when trying to access Z variable.

> def sum(x,y):

> Z = x +y

> print Z # will generate a runtime error

#### Returning multiple values

> def divide(a,b):

> q = a/b

> r = a - q\*b

> return q,r

> \>>> x,y = divide(42,5) # x = 8, y = 2

> \>>> x

> 8

> \>>> y

> 2

In this note we talked about variables, statements, expressions, operators, comments, and functions. These are the very basic building blocks of you programs whatever its final size. We will continue our learning in the upcoming notes.