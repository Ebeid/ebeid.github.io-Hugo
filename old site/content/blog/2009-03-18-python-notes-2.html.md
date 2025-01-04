--- 
title: "Python Notes – 2 : Variables, Statements, Expressions, Operators, and Functions" 
date: '2009-03-18T15:25:00.001-05:00' 
tags: 
    - Python
modified_time: '2009-05-15T02:21:29.083-05:00' 
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-6249182555567542586
blogger_orig_url: http://ebeid-soliman.blogspot.com/2009/03/python-notes-2.html 
---

Welcome to our second note in our Python learning process. In this note
we will talk about variables, statements, expressions, operators,
comments, and functions. These are the very basic building blocks of you
programs whatever its final size

#### Variables

The assignment statement creates new variables and gives them values

> &gt;&gt;&gt; message = "What's up, Doc?"

> &gt;&gt;&gt; n = 17

> &gt;&gt;&gt; pi = 3.14159

Python is a dynamically typed language. Which means that variables'
types don't have to be defined before the variables use. The python
interpreter figure out what type a variable is when you first assign it
a value.

#### Variables naming

-   Variable name can contain letters, numbers, and underscore.
-   Variable name must begin with letter.
-   Variable names are case-sensitive ( x different than X ).
-   Variable names can't be one of the Python language reserved words,
    which are :

<table>
<tbody>
<tr class="odd">
<td>and</td>
<td>continue</td>
<td>else</td>
<td>for</td>
<td>import</td>
<td>not</td>
<td>raise</td>
</tr>
<tr class="even">
<td>assert</td>
<td>def</td>
<td>except</td>
<td>from</td>
<td>in</td>
<td>or</td>
<td>return</td>
</tr>
<tr class="odd">
<td>break</td>
<td>def</td>
<td>exec</td>
<td>global</td>
<td>is</td>
<td>pass</td>
<td>try</td>
</tr>
<tr class="even">
<td>class</td>
<td>elif</td>
<td>finally</td>
<td>if</td>
<td>lambda</td>
<td>print</td>
<td>while</td>
</tr>
</tbody>
</table>

#### Statements

A statement is an instruction that the Python interpreter can execute. A
Python script is a sequence of statements. The results appear one at a
time as the statements execute.

For example, the script

> &gt;&gt;&gt; print 1

> &gt;&gt;&gt; 1

> &gt;&gt;&gt; x = 2

> &gt;&gt;&gt; print x

> &gt;&gt;&gt; 2
>
> #### Expressions
>
> An expression is a combination of values, variables, and operators. If
> you type an expression on the command line, the interpreter evaluates
> it and displays the result:
>
> > &gt;&gt;&gt; 1 + 1
>
> > 2
>
> #### Boolean Expressions
>
> A boolean expression is an expression that is either true or false.
> Boolean expressions are expressions that uses logical operators. There
> are three logical operators: and, or, not. The operands of logical
> operands should be boolean expressions. In Python there is no boolean
> data type instead 0, '', \[\], (), {}, and None are false in a boolean
> context; everything else is true. The absence of boolean data types
> results in the following behavior of logical operators:
>
> -   All the behaviors depends on the order of expressions evaluation,
>     which is from left to right.
> -   and : returns the first false value, if all values are true,
>     returns the last value.
>
> > &gt;&gt;&gt; 'a' and 'b'
>
> > 'b'
>
> > &gt;&gt;&gt; ' ' and 'b'
>
> > ' '
>
> > &gt;&gt;&gt; 'a' and 'b' and 'c'
>
> > 'c'
>
> -   or : returns the first true value, if all values are false,
>     returns the last value
>
> > &gt;&gt;&gt; 'a' or 'b'
>
> > 'a'
>
> > &gt;&gt;&gt; ' ' or 'b'
>
> > 'b'
>
> > &gt;&gt;&gt; ' ' or \[\] or {}
>
> > {}
>
> -   not : evaluates the boolean expression that follows it and inverts
>     it whole value.
>
> > &gt;&gt;&gt; not (1 and 0)
>
> > True
>
> > &gt;&gt;&gt; not (1 or 0)
>
> > False
>
> #### Operators and operands
>
> Operators are special symbols that represent computations like
> addition and multiplication. The values the operator uses are called
> operands.
>
> The symbols +, -, and /, and the use of parenthesis for grouping, mean
> in
>
> Python what they mean in mathematics. The asterisk (\*) is the symbol
> for multiplication, and \*\* is the symbol for exponentiation.
>
> #### Order of operations
>
> When more than one operator appears in an expression, the order of
> evaluation depends on the rules of precedence. The following is
> operators from highest precedence to lower precedence:
>
> -   Parentheses
> -   Exponentiation
> -   Multiplication / Division
> -   Addition / Subtraction
>
> Operators with the same precedence are evaluated from left to right.
>
> #### Comments
>
> Comments start with \#.
>
> #### Built-in Functions
>
> Here are some of the built-in functions available in Python:
>
> -   Type conversion functions which converts values from one type to
>     another. Like:
>     -   int() :
>
> > &gt;&gt;&gt; int("32")
>
> > 32
>
> > &gt;&gt;&gt; int("Hello")
>
> > ValueError: invalid literal for int(): Hello
>
> <span class="underline"></span>
>
> -   float():
>
> > &gt;&gt;&gt; float(32)
>
> > 32.0
>
> > &gt;&gt;&gt; float("3.14159")
>
> > 3.14159
>
> -   str():
>
> > &gt;&gt;&gt; str(32)
>
> > '32'
>
> > &gt;&gt;&gt; str(3.14149)
>
> > '3.14149'
>
> -   Math functions which provides most of the familiar mathematical
>     functions. These functions are implemented in a module called
>     math, we will talk about modules soon. But for now, if you want to
>     use these functions, you have to import the math module. This is
>     very straight foreword, using following statement
>     -   &gt;&gt;&gt; import math
>     -   After the import statement, you can simply call the math
>         functions.
>
> > &gt;&gt;&gt; decibel = math.log10 (17.0)
>
> > &gt;&gt;&gt; angle = 1.5
>
> > &gt;&gt;&gt; height = math.sin(angle)
>
> > &gt;&gt;&gt; degrees = 45
>
> > &gt;&gt;&gt; angle = degrees \* 2 \* math.pi / 360.0
>
> > &gt;&gt;&gt; math.sin(angle)
>
> > 0.707106781187
>
> > &gt;&gt;&gt; math.sqrt(2) / 2.0
>
> > 0.707106781187
>
> There are many other built-in functions, we mentioned these two types
> just as examples.
>
> #### Creating your own functions
>
> A function is a named sequence of statements that performs a desired
> operation. This operation is specified in a function definition.
>
> The syntax for a function definition is:
>
> def FUNCTION\_NAME( LIST OF PARAMETERS ):
>
> > STATEMENTS
>
> -   def is a keyword.
> -   FUNCTION\_NAME could be anything except Python keywords.
> -   LIST OF PARAMETERS are the ordered list parameters the function
>     needs to operate. The empty parentheses indicate no parameters
>     needed.
> -   The function body doesn't have starting or ending characters (like
>     "{" and "}" in C like languages ). Indentation is the only scope
>     identifier for statements in Python. The first statement that
>     doesn't follow the indentation, will be considered out of the
>     function and will mark the function termination.
>
> > \# just to show the function scope and structure
>
> > def sample\_func():
>
> >     Print "we are in the function body scope"
>
> >     Print "we still in the function scope"
>
> > Print "we are out of the function scope"
>
> > \# another function with parameters
> >
> > def sum(x, y):
>
> > &lt; font color="\#0000ff"&gt;    print x + y
>
> -   To call a function just use the function name followed by the list
>     of parameters between parentheses
>
> > &gt;&gt;&gt; sample\_func()
>
> > &gt;&gt;&gt; sum(1,2)
>
> > 3
>
> -   Functions can call other functions in their body.
> -   Functions can return values to its caller
>
> > def sum(x,y):
>
> > return x +y
>
> > def print\_sum(x,y):
>
> > print sum(x,y)
>
> > print\_sum(2,3)
>
> > 5
>
> -   When you create a local variable inside a function, it only exists
>     inside the function, and you cannot use it outside. The following
>     will generate a run-time error when trying to access Z variable.
>
> > def sum(x,y):
>
> > Z = x +y
>
> > print Z \# will generate a runtime error
>
> #### Returning multiple values
>
> > def divide(a,b):
>
> > q = a/b
>
> > r = a - q\*b
>
> > return q,r
>
> > &gt;&gt;&gt; x,y = divide(42,5) \# x = 8, y = 2
>
> > &gt;&gt;&gt; x
>
> > 8
>
> > &gt;&gt;&gt; y
>
> > 2
>
> In this note we talked about variables, statements, expressions,
> operators, comments, and functions. These are the very basic building
> blocks of you programs whatever its final size. We will continue our
> learning in the upcoming notes.
