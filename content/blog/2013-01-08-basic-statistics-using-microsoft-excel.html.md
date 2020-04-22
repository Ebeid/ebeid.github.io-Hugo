--- 
title: "Basic statistics using Microsoft Excel" 
date: '2013-01-08T13:01:00.001-06:00' 
tags: 
    - Microsoft Excel 
    - Statistics
modified_time: '2013-01-08T13:13:44.209-06:00' 
thumbnail: http://lh6.ggpht.com/-B7Tey99JXUY/UOxsCLShlrI/AAAAAAAAAjo/Dme-zM64jW0/s72-c/clip\_image002\_thumb.gif?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-238100843033678581
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/01/basic-statistics-using-microsoft-excel.html
---

Microsoft Excel is a powerful software that have been used my end users
and professionals for many years for various purposes. In this post we
going to introduce basic statistical features of Excel. This post is
using Microsoft Excel 2013, but it is easy to map it to your Excel
version.

### **Basic Formulas**

Computations in Excel are carried out using formulas. A formula is a
mathematical expression that is used to calculate a value. In Excel, a
formula is entered into the active cell by typing an expression. In
certain situations, Excel will automatically insert a formula for you.

Excel formulas are *<span class="underline">always</span>* entered
beginning with an = sign and followed by the expression. Without an =
sign, the expression will be treated as text. The expression will
consist of cell references and/or numbers, and contain one or more
arithmetic operators such as +, -, \*, / or ^. The operator, ^,
represents exponentiation. If an expression contains more than one
arithmetic operator, the computations are performed in a certain
sequence called the *<span class="underline">order of
precedence</span>*. The rules in the order of precedence are as follows:

1.  Exponentiation (^)
2.  Multiplication (\*) or Division (/), whichever comes first working
    from left to right
3.  Addition (+) or subtraction (-), whichever comes first working from
    left to right

If there are any parentheses in the formula, Excel executes the inner
most parenthesis first and then works outwards. Within the parenthesis,
the order of precedence also holds. Assume you had the following formula
in an Excel cell:

=8+(2\*(6+5^2\*4))

When executed, this formula will enter a value of 220 in that cell. Here
is how this value is calculated. First, the inner most parenthesis
(6+5^2\*4) will be executed. Within this set of parenthesis, the
exponentiation will be computed first (5^2=25) to reduce the expression
in the inner parenthesis to (6+25\*4). Next, the multiplication
(25\*4=100) is done giving (6+100). This is followed by the addition
(6+100=106). This reduces the original formula to =8+(2\*106). Next,
Excel executes the parenthesis (2\*106) giving us 212. Finally, the
addition 8+212 is done for a total of 220. Note that if the expression
is =8+(2\*6+5^2\*4), that is without the inner set of parenthesis, the
value would be 120.

Ways to enter formulas (like A1+B1+C1 ) :

1.  Enter the whole formula in the cell that will store the result (
    =A1+B1+C1 ) and press Enter.
2.  Enter = and then click on cell A1 then enter the + sign using the
    keyboard then click on cell B1 then enter the + sign using the
    keyboard then click on cell C1 and press Enter.
3.  If the cells to be added are adjacent, you can identify these cells
    using a range that could be passed to functions. In our case enter
    =SUM(A1:C2)
4.  Many formulas have shortcut command on the Excel ribbon. In our case
    AutoSum command (represented by the
    button,[<img src="http://lh6.ggpht.com/-B7Tey99JXUY/UOxsCLShlrI/AAAAAAAAAjo/Dme-zM64jW0/clip_image002_thumb.gif?imgmax=800" title="clip_image002" width="17" height="20" alt="clip_image002" />](http://lh6.ggpht.com/-E3hmY9eZhsQ/UOxsBj-v0AI/AAAAAAAAAjk/Cqx4VGydwqA/s1600-h/clip_image0023.gif),
    in the Editing group on the Home ribbon tab) is used to sum adjacent
    horizontal or vertical cells.

In many cases you need to repeat the equation for many cells (e.g. to
sum all the rows the in the sheet below)

[<img src="http://lh5.ggpht.com/-A1Are8P9Ss8/UOxsDfAPkCI/AAAAAAAAAj8/p2YV4bnemqY/_2013-01-07_15-48-33_thumb2.jpg?imgmax=800" title="_2013-01-07_15-48-33" width="731" height="400" alt="_2013-01-07_15-48-33" />](http://lh3.ggpht.com/-7KhRA2euyhg/UOxsCn8cE8I/AAAAAAAAAjw/xvfQKCJIXZ0/s1600-h/_2013-01-07_15-48-334.jpg)

To repeat the equation for for the rest of D column, you could:

1.  Select D1, Copy, select D2, Past, and repeat the operation for the
    D3, D4, D5, D6
2.  Hover the mouse over the left bottom corner of D1 till the curser
    became small black square (called Fill Handle), then click and drag
    it to the desired range (D2:D6). Once you release the mouse button,
    Excel will execute the formula for your range.

You wondering that the equation we copied was for A1+B1+C1, how it
worked for the second row and the next rows ? The answer is that Excel
automatically adjusted the locations of the cells when the equation was
copied from cell D1 to cell D2 since the cells in the expression were
all relative reference cells. A **relative reference** is a cell
reference that changes or shifts when the cell is copied to another
location. In contrast, an **absolute reference** is a cell reference
that does not change when you copy that cell to another location. There
is also a **mixed reference** for cells. A mixed reference only changes
either the row reference or the column reference, depending on how the
mixed reference is set up.

All cell references are relative reference cells unless designated
otherwise. That is, a cell has to be designated an absolute reference or
a mixed reference cell. <span class="underline">To create an absolute
reference, you have to preface the cell row and column designations with
a dollar sign ($)</span>. For example, to make Cell A1 an absolute
reference cell, it would have to referred as $A$1. Without these dollar
prefixes, a cell is *<span class="underline">always</span>* considered a
relative location cell. The relative reference works as follows: When
you enter the formula, =A1+B1+C1, into Cell D1, the relative location of
Cell A1 to Cell D1 is three cells to the left. Similarly, Cell B1 is two
cells to the left of Cell D2, and Cell C1 is one cell left. When the
equation is copied down to Cell D2, the first cell in this equation will
still be the cell three cells to the left. However, the cell three cells
to the left of D2 is now Cell A2. Similarly, the cell two cells to the
left of D2 is Cell B2, and so on. That is why when the equation is
copied down one cell, it makes the automatic adjustment for the new
relative locations. Similarly, if the equation is copied down to Cell
D3, the equation in Cell D3 would be copied as =A3+B3+C3. If there was
an absolute reference cell in this equation, its reference would not
change when the equation is copied to another location. The same
processing happens when using the Fill Handle.

### Basic Functions

Excel have many functions like MIN, MAX, AVERAGE which work on ranges.

[<img src="http://lh6.ggpht.com/-Rfojz1md2Xw/UOxsEwP6CoI/AAAAAAAAAkM/ePptX6RKeoc/Book1---Excel_2013-01-07_%0A17-36-37_th.jpg?imgmax=800" title="Book1 - Excel_2013-01-07_17-36-37" width="690" height="381" alt="Book1 - Excel_2013-01-07_17-36-37" />](http://lh6.ggpht.com/-2rZ2NIVe2oo/UOxsD8DS7-I/AAAAAAAAAkE/_8ueYHrgMYk/s1600-h/Book1---Excel_2013-01-07_17-36-374.jpg)

### Logical Functions

Logic is handled within Excel by logical functions. A logical function
is a “logical” statement that determines whether a condition is true or
false. Excel has several logical functions. The most commonly used of
these is the **IF** function. The general form of the IF function is:
=IF (*logical-test, value-if-true, value-if-false*)

Example  =IF (A2&gt;=5, “Greater Than 5”, “Less Than 5”)

This function works as follows: *logical-test* is an expression that is
either true or false. If the expression is true, then the expression
*value-if-true* is executed. If the expression is false, then the
expression *value-if-false* is executed. The *logical-test* is
constructed using **comparison operators**. A comparison operator
compares two expressions according to the comparison operator. There are
six comparison operators. They are:

-   Greater than &gt;
-   Less than &lt;
-   Equal to =
-   Greater than or equal to &gt;=
-   Less than or equal to &lt;=
-   Not equal to &lt;&gt;

### The AND Function

The IF function example above only used one logical test. It can be
easily extended to include multiple logical tests. When there are
multiple conditions involved, the AND function is used within the IF
function as follows: =IF (AND(*logical-test 1, logical-test 2,* …..),
*value-if-true, value-if-false*)

Each *logical-test* is an expression that can true or false. If both
logical-test *1* and *logical-test 2* are true, the AND function returns
the value true. Otherwise, it returns the value false. If the AND
function returns the value true, the *value-if-true* expression is
executed. If the AND function returns the value false, the
*value-if-false* expression is executed.

Example =IF(AND(A2&gt;=5,B2&gt;=5), “Both A and B Greater than 5”,
“Either A or B Less than 5”)

### The OR Function

The OR function is also a multiple logical test. When there are multiple
conditions involved, the OR function is used within the IF function as
follows: =IF (OR (*logical-test 1, logical-test 2,* …..),
*value-if-true, value-if-false*)

Just like the AND function, each *logical-test* is an expression that
can be true or false. However, with the OR function, if **<span
class="underline">either</span>** *logical-test 1* **<span
class="underline">or</span>** *logical-test 2* is true, the OR function
returns the value true. If both tests are false, it returns the value
false. If the OR function returns the value true, the *value-if-true*
expression is executed. If the OR function returns the value false, the
*value-if-false* expression is executed.

Example =IF(OR(A2&gt;=5,B2&gt;=5), “Either A or B Greater than 5”, “Both
A and B Less than 5”)

### Lookup

Suppose you want to categorize your data or assign certain classes to
your data (like assign class grades based on the total percentage).
Excel provides VLOOKUP function. A VLOOKUP function is simply a table
with the ranges built in. Excel then matches a data value against these
ranges to determine a category or class (grade in our example). To use
the VLOOKUP table, you have to first create the VLOOKUP table and then
access this VLOOKUP tab le by using the VLOOKUP function within an Excel
statement. The VLOOKUP table can be created anywhere in your sheet. like
the one below

[<img src="http://lh4.ggpht.com/-EHk21h2tpIY/UOxsGU4ixbI/AAAAAAAAAkY/NSA0bY9Xxj0/Book1---Excel_2013-01-07_18-22-50_th.jpg?imgmax=800" title="Book1 - Excel_2013-01-07_18-22-50" width="474" height="522" alt="Book1 - Excel_2013-01-07_18-22-50" />](http://lh5.ggpht.com/-7pKolpKhDTs/UOxsFuKOGGI/AAAAAAAAAkQ/Dfu8HtE7B_E/s1600-h/Book1---Excel_2013-01-07_18-22-504.jpg)

Now we need to use the VLOOKUP function to access the VLOOKUP table to
assign grades to column B cells. The general form for VLOOKUP is 
=VLOOKUP(*lookup-value, table-array range, col-index-number, \[range
lookup\]*)

where:

-   ***lookup-value*** is the cell reference of the cell that contains
    the value to be looked up. In this case, the value will be the final
    percentage scores from the course. That is, the percentage scores in
    Column O.
-   ***table-array range*** is the range of the VLOOKUP table. Note that
    the headers are not included in this range. Also, the range of the
    table is *<span class="underline">always</span>* entered using
    *<span class="underline">absolute references</span>*.
-   ***col-index-number*** is the column number of the value of interest
    in the VLOOKUP table. For example, in this table, the value of
    interest is the grade which is in Column 2. Therefore, the
    col-index-number is 2. If the value of interest is the grade point,
    then the col-index-number will be 3.
-   ***\[range lookup\]*** is an optional argument with a value of true
    or false. A true value means that look-up value is being evaluated
    against ranges in the table-array. A false value means that the
    look-up value must exactly match the value in the table-array. Since
    this argument is optional, the default value is true.

With the total percentage for the first record in cell A2, the VLOOKUP
statement in cell B2 is entered as =VLOOKUP(A2, $E$2:$F$11,2,TRUE)

This statement works as follows: The score in Cell A2 is checked against
the first range. Excel forms the first range using the values in Rows 1
and 2 from Column 1 of the VLOOKUP table. These values are 0% and 70%.
Therefore, Excel sets the range as 0-70%. Logically, the range is set up
as &gt;=0% and &lt;70%. Thus, a score of exactly 70% is not part of this
range. If the score from Cell A2 is in this range, a grade of F is
returned and recorded in Cell B2. If it is not in this range, Excel
forms the second range using the values in Rows 2 and 3 from Column 1.
That is, 70% and 72%. As before, this range is set up as &gt;=70% and
&lt;72%. If the score is in this range, a grade of C- is returned and
recorded in Cell B2. If it is not in this range, Excel forms the third
range using the values in Rows 3 and 4 of Column 1 of the VLOOKUP table.
That is, 72% and 77%. This range is interpreted as &gt;=72% and &lt;77%.
If the score is in this range, a grade of C is returned and recorded in
Cell B2. If it is not in this range, Excel continues by forming the
fourth range using the values in Rows 4 and 5 of Column 1, and then the
fifth range and so on until it finds a range for the score in Cell A2.
The last range formed in this table will be 92% to 97% using the values
in Rows 9 and 10 of Column 1. If the score is not in this range, then it
assigns a grade of A+, the last grade, by default.

To calculate the rest of the grades using this grade criterion, the
VLOOKUP function in Cell B2 is copied down to Cell B24.

**Basics Of Probability**

**Probability** : a number between 0 and 1 that indicates how likely it
is that some event, or set of events, will occur. A probability of 0
indicates it will never occur. A probability of 1 indicates it will
always occur. P(event) = 0.2

**Experiment :** any situation capable of being replicated under
essentially stable conditions. The replications may be feasible, such as
flipping a coin over and over. Or, the experiment may only replicated in
theory, such as investing $1,000 in a friend’s promising invention. In
this case you could imagine repeating such an investment over and over
many times, even though you intend to do it only once. When an
experiment is defined it is important to carefully specify all possible
***sample outcomes*.** These are all the possible results of the
experiment. For example, if a coin is tossed once, then the sample
outcomes are {Head, Tail}. If the experiment is defined as tossing a
coin <span class="underline">twice</span>, then one way of specifying
the sample outcomes would be: {Head, Head}, {Head, Tail}, {Tail, Head},
and {Tail, Tail}. The outcomes of an experiment must be **mutually
exclusive**. Mutually exclusive means there is no overlap between the
outcomes. The outcomes of an experiment must also **exhaustive**. This
means one of the defined sample outcomes must occur. There are two basic
properties necessary for defining the probability of an outcome:

-   0 ≤ P(Outcome) ≤ 1
-    [<img src="http://lh3.ggpht.com/-aWK9ufgM0kM/UOxsHrCs-jI/AAAAAAAAAks/y--NPCZ4BZg/clip_image002_thumb%25255B1%25255D.gif?imgmax=800" title="clip_image002" width="17" height="20" alt="clip_image002" />](http://lh5.ggpht.com/-XAk183bMwpE/UOxsHNt0E4I/AAAAAAAAAkk/p5iupyDMjXQ/s1600-h/clip_image002%25255B3%25255D.gif)P(Outcomes)
    = 1

Probability Rules:

-   Rule for Complements:
    P([<img src="http://lh3.ggpht.com/-JMRRqM6dwLc/UOxsJVX1vGI/AAAAAAAAAk8/fO_t1OndmqY/clip_image002%25255B4%25255D_thumb.gif?imgmax=800" title="clip_image002[4]" width="16" height="21" alt="clip_image002[4]" />](http://lh3.ggpht.com/-DR6-wQOTPpc/UOxsIdqtfYI/AAAAAAAAAkw/Auyz38Ll09U/s1600-h/clip_image002%25255B4%25255D%25255B2%25255D.gif))
    = 1 – P(A).
    [<img src="http://lh5.ggpht.com/-L8DQ2CzmixI/UOxsK8ExTHI/AAAAAAAAAlM/BXtqm-9yxoY/clip_image002%25255B4%25255D_thumb%25255B1%25255D.gif?imgmax=800" title="clip_image002[4]" width="16" height="21" alt="clip_image002[4]" />](http://lh4.ggpht.com/-HnC4LDcQlHQ/UOxsJxggB-I/AAAAAAAAAlE/AHm7RE9s0cw/s1600-h/clip_image002%25255B4%25255D%25255B4%25255D.gif)represents
    all sample outcomes except A
-   Additive Rule for Mutually Exclusive Events: P(A *or* B) = P(A) +
    P(B)
-   Joint Probability for Two Independent Events**:** P(A *and* B) =
    P(A)\*P(B). Independent means that the occurrence of A have ne
    influence on the occurrence of B.

**Random Variables** : The outcomes of an experiment are said to take
place **random ly**, since they cannot, by definition, occur in any
particular order or pattern. Such outcomes, called **random variables.**
Once an experiment and its outcomes have been clearly stated, and the
random variable of interest has been defined, then the probability of
each value for the random variable can be specified. This specification
is called a ***probability mass function***. A probability mass function
(p.m.f.) gives the probability for each outcome of a random variable.

**Example** : Let take a statistics course, receive a grade, letting
random variable Y = grade point equivalent.

<table>
<tbody>
<tr class="odd">
<td><p>Outcome</p></td>
<td><p>Y</p></td>
<td><p><strong><span class="underline">Probability P(Y)</span></strong></p></td>
</tr>
<tr class="even">
<td><p>F grade</p></td>
<td><p>0</p></td>
<td><p>P(Y=0)=0.05</p></td>
</tr>
<tr class="odd">
<td><p>D grade</p></td>
<td><p>1</p></td>
<td><p>P(Y=1)=0.10</p></td>
</tr>
<tr class="even">
<td><p>C grade</p></td>
<td><p>2</p></td>
<td><p>P(Y=2)=0.35</p></td>
</tr>
<tr class="odd">
<td><p>B grade</p></td>
<td><p>3</p></td>
<td><p>P(Y=3)=0.30</p></td>
</tr>
<tr class="even">
<td><p>A grade</p></td>
<td><p>4</p></td>
<td><p>P(Y=4)=0.20</p></td>
</tr>
</tbody>
</table>

[<img src="http://lh3.ggpht.com/-98rY5N8xt2w/UOxsLwI7hcI/AAAAAAAAAlc/7zjllOV7hU4/Untitled_thumb%25255B1%25255D.jpg?imgmax=800" title="Untitled" width="240" height="112" alt="Untitled" />](http://lh6.ggpht.com/-AJCuf1ynGIU/UOxsLY5YX_I/AAAAAAAAAlU/i2D9g0yIi_c/s1600-h/Untitled%25255B3%25255D.jpg)

[**Expected Value
:**](http://lh3.ggpht.com/-l-RKtMOQDHg/UOxs4eUpJQI/AAAAAAAAAls/irro1m_jaxQ/s1600-h/clip_image002%25255B3%25255D.jpg)
An expected value is the average or mean of a random variable. The
expected value of the random variable X is denoted by the symbol E\[X\],
where E\[X\] =
[<img src="http://lh6.ggpht.com/-WiH5igjLoIU/UOxs5RJgLQI/AAAAAAAAAl8/9le75KWSFR4/clip_image002_thumb%25255B2%25255D.gif?imgmax=800" title="clip_image002" width="17" height="20" alt="clip_image002" />](http://lh5.ggpht.com/-h_F4l1ayRT0/UOxs448Nh3I/AAAAAAAAAl0/jpQDehrBLBc/s1600-h/clip_image002%25255B9%25255D.gif)XP(X)

[<img src="http://lh6.ggpht.com/-0MrtLXXwhKA/UOxs6v4v9hI/AAAAAAAAAmM/iw9ZwjcQ8pk/image_thumb%25255B1%25255D.png?imgmax=800" title="image" width="382" height="146" alt="image" />](http://lh5.ggpht.com/-nbshogKNet4/UOxs51N1TmI/AAAAAAAAAmE/yRmYP3QwP40/s1600-h/image%25255B3%25255D.pn%0Ag)

**Standard Deviation** : The **standard deviation** of a random variable
X measures the average amount by which the values of the random variable
X deviate from their expected value. This standard deviation is denoted
by σ<sub>X</sub>, where σ is the Greek letter sigma.

**Discrete random variable**: a variable whose values can be separated
from one another and counted then the probability of each value for the
random variable can be specified. This specification is called a
***probability mass function.***

**Continuous random variable**: a variable whose values cannot be
separated from one another, and are measured rather than counted.
Continuous probability distributions are often called **probability
density functions** because it defined over a range of X values (X
represents the random variable). The probability that any specific value
within this range is so small that it is assumed to be equal zero.
Probability P(a &lt; X &lt; b) is the Shaded Area

[<img src="http://lh4.ggpht.com/-AKth0uJiVsw/UOxs7w1YQGI/AAAAAAAAAmc/BNvLI0yHJ6c/clip_image002%25255B5%25255D_thumb%25255B1%25255D.jpg?imgmax=800" title="clip_image002[5]" width="382" height="124" alt="clip_image002[5]" />](http://lh4.ggpht.com/-Ykaie6o8MoA/UOxs7NavgnI/AAAAAAAAAmU/AhXLabh-MxU/s1600-h/clip_image002%25255B5%25255D%25255B3%25255D.jpg)

**Determining Normal Probabilities** : For data that follow normal
distribution this cumulative probability for a normal random variable X
P(X&lt;k) is calculated using the following Excel command: =NORM.DIST(k,
mean-of-X , Standard-Deviation-of-X,1)

**Example**: Suppose that the average person’s IQ in US is 100 and the
standard deviations for past IQs is 15, then the probability a randomly
selected person in the U.S. will have an IQ between 110 and 120 is P(110
&lt; X &lt; 120) = NORMDIST(120,100,15,1)- NORMDIST(110,100,15,1) =
0.9088 - 0.7475 = 0.1613

[<img src="http://lh4.ggpht.com/-M_yRzOGTSIU/UOxs8krp4DI/AAAAAAAAAms/12Aq9wPQJXA/image_thumb%25255B3%25255D.png?imgmax=800" title="image" width="608" height="168" alt="image" />](http://lh6.ggpht.com/-jqll3kM-fG8/UOxs8WXICnI/AAAAAAAAAmg/sp-Xnt6bbHU/s1600-h/image%25255B7%25255D.png)

**Normal Inverse** : If we want to reverse the previous process, get the
X value giving its probability. This is done using the Excel command :
=NORM.INV(Probability,mean-of-X , Standard-Deviation-of-X)

### Histograms

Histograms allow you to summarize large amounts of data graphically by
determining the frequencies over set ranges of specified size (called
classes). The width of a class in Excel is called a bin width. The
ranges of the classes are called class intervals. The graph of a
frequency distribution is called a histogram and is the same as a column
chart. To construct a histogram in Excel, we first have to determine the
bin width. If you want equal bin widths like the ones below, enter the
first and second values (4.20, 4.40), then select both cells and use the
fill handle to fill more cells using the same incremental value used in
the first two cells  (0.20). In order to create histograms, we need to
initialize the analysis toolpak addin that comes with Excel.

[<img src="http://lh6.ggpht.com/-0fSuJZYarrY/UOxs-BbJmoI/AAAAAAAAAm4/xottZ1B-LPw/Book1.xlsx%252520-%252520Excel_2013-01-08_12-22-06_thumb%25255B2%25255D.jpg?imgmax=800" title="Book1.xlsx - Excel_2013-01-08_12-22-06" width="184" height="427" alt="Book1.xlsx - Excel_2013-01-08_12-22-06" />](http://lh3.ggpht.com/-qxOHnuh-LB8/UOxs9kPIwXI/AAAAAAAAAm0/kn-R8WvA74s/s1600-h/Book1.xlsx%252520-%252520Excel_2013-01-08_12-22-06%25255B4%25255D.jpg)

**Initialize the Analysis Toolpak**: Click on the Office button
**&gt;&gt;** Excel Options in the lower right hand corner **&gt;&gt;**
choose the Add-ins section on the left hand side &gt;&gt; click the Go
button next to the Manage Excel Add-ins drop down box &gt;&gt; check the
box next to Analysis Toolpak and Analysis Toolpak VBA &gt;&gt; press OK.

To create your histogram, go to the Data ribbon tab and click on the
Data Analysis button in the Analysis group. In the dialog box that
appears, choose Histogram and click Ok. In the resulting dialog table,
enter the Input Range (A4:A26), the Bin Range (C2:C15), the worksheet
name (histogram1), check the Chart Output option and click on OK. These
steps will give a “basic” histogram (like the one below) which can be
formatted later.

[<img src="http://lh4.ggpht.com/-02_LHcX5kCE/UOxs_Vg-5mI/AAAAAAAAAnM/EQ8nudeSB9E/Book1.xlsx%252520-%252520Excel_2013-01-08_12-41-46_thumb%25255B2%25255D.jpg?imgmax=800" title="Book1.xlsx - Excel_2013-01-08_12-41-46" width="606" height="342" alt="Book1.xlsx - Excel_2013-01-08_12-41-46" />](http://lh4.ggpht.com/-h2t15o3wSnc/UOxs-k_tCJI/AAAAAAAAAnE/AyqX5l8jVyA/s1600-h/Book1.xlsx%252520-%252520Excel_2013-01-08_12-41-46%25255B4%25255D.jpg)

A common addition to histogram representation, is to convert the
frequencies into percentages. For histogram1, calculate the total number
of data items by entering a sum function in cell B17. In cell B17, type
the formula: =SUM(B2:B16)

Then in cell C2, type the following formula and copy it down to cell
C16: = B2/$B$17

Lastly, format C2:C16 to be percentage with one decimal place. From
ribbon Home tab, Number group

[<img src="http://lh5.ggpht.com/-Zygu5zkIHtY/UOxtAgDqTaI/AAAAAAAAAnc/jweGnoyX2yM/Book1.xlsx%252520-%252520Excel_2013-01-08_12-52-16_thumb%25255B1%25255D.jpg?imgmax=800" title="Book1.xlsx - Excel_2013-01-08_12-52-16" width="141" height="159" alt="Book1.xlsx - Excel_2013-01-08_12-52-16" />](http://lh4.ggpht.com/-Hhc6nTzw_6Q/UOxtAJqjiVI/AAAAAAAAAnY/kj7whvAH7No/s1600-h/Book1.xlsx%252520-%252520Excel_2013-01-08_12-52-16%25255B3%25255D.jpg)

In this post we introduced basic statistics operation that can be done
easily in Excel. To explain these operations we reviewed some statistics
background and general Excel knowledge. In the upcoming posts we will
dig deeper using Excel and other specialized software like SAS and R
language.
