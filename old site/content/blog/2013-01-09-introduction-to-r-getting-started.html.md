--- 
title: "Introduction to R – Getting Started" 
date: '2013-01-09T10:19:00.001-06:00' 
tags: 
    - R Programming Language 
    - Statistics 
modified_time: '2013-01-21T15:48:45.516-06:00' 
thumbnail: http://lh5.ggpht.com/-G6GT4cGFMFk/UO2X79BYkLI/AAAAAAAAAoo/tb3VmXosBU8/s72-c/RGui%252520%25252864-bit%252529\_2013-01-08\_15-16-51\_thumb%25255B2%25255D.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-6279714534161383586
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/01/introduction-to-r-getting-started.html
--- 
<span style="font-family: Calibri;">**R** is an open source
programming language and software environment for statistical computing
and graphics. The R language is widely used among statisticians for
developing statistical software and data analysis. R was created by
</span>[<span style="font-family: Calibri;">Ross
Ihaka</span>](https://www.facebook.com/pages/w/103371346383347)<span
style="font-family: Calibri;"> and </span>[<span
style="font-family: Calibri;">Robert
Gentleman</span>](https://www.facebook.com/pages/w/126921034017343)<span
style="font-family: Calibri;"> at the </span>[<span
style="font-family: Calibri;">University of
Auckland</span>](https://www.facebook.com/pages/w/105560002810339)<span
style="font-family: Calibri;">, New Zealand, and now, R is developed by
the *R Development Core Team*. </span>  
<span style="font-family: Calibri;">To download R and install it on your
computer, you can get it at the Comprehensive R Archive Network
(</span>[<span
style="font-family: Calibri;">http://cran.r-project.org</span>](http://cran.r-project.org/)<span
style="font-family: Calibri;">). One option that you may want to explore
is RStudio (</span>[<span
style="font-family: Calibri;">http://rstudio.org</span>](http://rstudio.org/)<span
style="font-family: Calibri;">) which is a very nice front-end to R and
works on all platforms.  
The R System is divided into 2 conceptual parts: </span>  

1.  <span style="font-family: Calibri;">The “base” R system that you
    download and install from CRAN. This part is required to run R, and
    it contains the most fundamental functions. </span>
2.  <span style="font-family: Calibri;">Everything else as can be
    downloaded as a separate package from CRAN. </span>

**<span style="color: black; font-family: Calibri; font-size: small;">Data Types</span>**
-----------------------------------------------------------------------------------------

-   <span style="font-family: Calibri;">R has five basic types of
    objects: character, numeric (real numbers), integer, complex,
    logical. </span>
    -   <span style="font-family: Calibri;">Numbers in R are numeric by
        default. If you want an integer, you need to specify the L
        suffix. </span>
        -   <span style="font-family: Calibri;">Ex: Entering 1 gives you
            a numeric object; entering <span class="underline">1L</span>
            explicitly gives you an integer. </span>
    -   <span style="font-family: Calibri;">Special number <span
        class="underline">Inf</span> represents infinity; e.g. 1 / Inf
        is 0</span>
    -   <span style="font-family: Calibri;">The value <span
        class="underline">NaN</span> represents an undefined value; e.g.
        0 / 0 is NaN</span>
-   <span style="font-family: Calibri;">A **vector** is a container that
    can contain objects of the same types only. Empty vectors can be
    created with the vector() function. </span>
-   <span style="font-family: Calibri;">A **list** can contain objects
    of different types. </span>

**<span style="color: black; font-family: Calibri; font-size: small;">Attributes</span>**
-----------------------------------------------------------------------------------------

<span style="font-family: Calibri;">R objects can have attributes: names
or dimnames, dimensions (e.g. matrices, arrays), class, length, or any
other user-defined attributes/metadata. attributes of an object can be
access using the <span class="underline">attributes()</span>
function.</span>  

**<span style="color: black; font-family: Calibri; font-size: small;">Getting Started with R prompt</span>**
------------------------------------------------------------------------------------------------------------

<span style="font-family: Calibri;">Go to Start &gt; Programs &gt; R
&gt; R . This will open the R prompt which we will use to test basic
statements. When you enter an expression into the R prompt and press
Enter, R will evaluate that expression and display the results (if there
are any).</span>  
<span
style="font-family: Calibri;">[<img src="http://lh5.ggpht.com/-G6GT4cGFMFk/UO2X79BYkLI/AAAAAAAAAoo/tb3VmXosBU8/RGui%252520%25252864-bit%252529_201%0A3-01-08_15-16-51_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-08_15-16-51" width="126" height="105" alt="RGui (64-bit)_2013-01-08_15-16-51" />](http://lh4.ggpht.com/-H13MEhasVx0/UO2X7Z6ZThI/AAAAAAAAAog/0OrGgFaYos0/s1600-h/RGui%252520%25252864-bit%252529_2013-01-08_15-16-51%25255B4%25255D.jpg)</span>  
<span style="font-family: Calibri;">as you can see the rules of
precedence are applied here.  Notice the weird “\[1\]” that accompanies
each returned value. In R, any number that you enter in the console is
interpreted as a vector. A vector is an ordered collection of numbers.
The “\[1\]” means that the index of the first item displayed in the row
is 1. In each of these cases, there is also only one element in the
vector.</span>  
<span style="font-family: Calibri;">The &lt;- symbol is the assignment
operator. When a complete expression is entered at the prompt, it is
evaluated and the result of the evaluated expression is returned. The
result may/not be auto-printed. The \[1\] indicates the index of the
element in the vector. The \# character indicates a comment and anything
right to it is ignored.</span>[<span
style="font-family: Calibri;"><img src="http://lh5.ggpht.com/-Hw-XuJUPDII/UGIpqfjVCtI/AAAAAAAAAgA/4LdXC1vzj2U/RGui%252520%25252832-bit%252529_2012-09-25_16-24-35_thumb.jpg?imgmax=800" title="RGui (32-bit)_2012-09-25_16-24-35" width="105" height="108" alt="RGui (32-bit)_2012-09-25_16-24-35" /></span>](http://lh5.ggpht.com/--WNQst6LZG4/UGIpp3GTkFI/AAAAAAAAAf4/YV4FCXW6EXs/s1600-h/RGui%252520%25252832-bit%252529_2012-09-25_16-24-35%25255B2%25255D.jpg)<span
style="font-family: Calibri;"> </span>  
<span style="font-family: Calibri;">you can also assign an object on the
left to a variable on the right</span>  
<span
style="font-family: Calibri;">[<img src="http://lh4.ggpht.com/-11QRLvqNh3E/UO2X9I6qmpI/AAAAAAAAAo4/sbmxab3WQCE/RGui%252520%25252864-bit%252529_2013-01-09_08-29-06_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_08-29-06" width="121" height="56" alt="RGui (64-bit)_2013-01-09_08-29-06" />](http://lh3.ggpht.com/-ShN9JG1fIYk/UO2X8g5T-cI/AAAAAAAAAow/_q0t04rPHZk/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_08-29-06%25255B3%25255D.jpg)</span>  
<span style="font-family: Calibri;">= means assign the value of the
right hand side to the variable on the left hand side. == tests
variables for equality</span>  
<span
style="font-family: Calibri;">[<img src="http://lh5.ggpht.com/-n1BJFiK_nNw/UO2X-DbDNJI/AAAAAAAAApI/GsaWDAD9X2k/RGui%252520%25252864-bit%252529_2013-01-09_08-30-37_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_08-30-37" width="128" height="198" alt="RGui (64-bit)_2013-01-09_08-30-37" />](http://lh5.ggpht.com/-edmktKvBJCo/UO2X9lM1KZI/AAAAAAAAApA/i4sDIGcIXug/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_08-30-37%25255B3%25255D.jpg)  
The **:**</span><span style="font-family: Calibri;"> operator can be
used to create <span class="underline">integer sequence vector</span>.
</span>[<span
style="font-family: Calibri;"><img src="http://lh3.ggpht.com/-9clXQN79DPQ/UGIprX_jmAI/AAAAAAAAAgQ/6927e2fNFPg/RGui%252520%25252832-bit%252529_2012-09-25_16-58-36_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (32-bit)_2012-09-25_16-58-36" width="528" height="50" alt="RGui (32-bit)_2012-09-25_16-58-36" /></span>](http://lh3.ggpht.com/-RiylLrc0sUY/UGIpqrlutpI/AAAAAAAAAgI/UzUGikvNYQs/s1600-h/RGui%252520%25252832-bit%252529_2012-09-25_16-58-36%25255B3%25255D.jpg)<span
style="font-family: Calibri;"> </span>  
<span
style="font-family: Calibri;">[<img src="http://lh6.ggpht.com/-di1B7XAXbcU/UO2X_4ylNsI/AAAAAAAAApU/tuhJebO9Yn8/RGui%252520%25252864-bit%252529_2013-01-08_15-33-30_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-08_15-33-30" width="604" height="54" alt="RGui (64-bit)_2013-01-08_15-33-30" />](http://lh5.ggpht.com/-y7qSmrYJct8/UO2X-2zg1VI/AAAAAAAAApQ/d3CH8owcEVs/s1600-h/RGui%252520%25252864-bit%252529_2013-01-08_15-33-30%25255B3%25255D.jpg)</span>  
<span style="font-family: Calibri;">The numbers in the brackets on the
left-hand side of the results indicate the index of the first element
shown in each row.  
THe <span class="underline">c()</span> function can be used to create
<span class="underline">vectors of objects</span>.</span>[<span
style="font-family: Calibri;"><img src="http://lh3.ggpht.com/-hO_1IhuUNF8/UGNN_-cY3DI/AAAAAAAAAgs/y_wDs5I3G2o/RGui%252520%25252832-bit%252529_2012-09-26_11-08-00_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (32-bit)_2012-09-26_11-08-00" width="528" height="277" alt="RGui (32-bit)_2012-09-26_11-08-00" /></span>](http://lh5.ggpht.com/-2-PypxtB9FY/UGNN_bTMWAI/AAAAAAAAAgk/1EgJnLr3GSs/s1600-h/RGui%252520%25252832-bit%252529_2012-09-26_11-08-00%25255B3%25255D.jpg)<span
style="font-family: Calibri;">  
You could use the <span class="underline">vector()</span> function to
specify the vector type and length and it will create an empty vector
for you.</span>[<span
style="font-family: Calibri;"><img src="http://lh3.ggpht.com/-XjYANPYqttw/UGNOAiT5q1I/AAAAAAAAAg8/_WEIHe1Y0zI/RGui%252520%25252832-bit%252529_2012-09-26_11-44-12_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (32-bit)_2012-09-26_11-44-12" width="314" height="71" alt="RGui (32-bit)_2012-09-26_11-44-12" /></span>](http://lh5.ggpht.com/-2yj6udK6wCU/UGNOAMgdshI/AAAAAAAAAg0/ktuacj6ZB3s/s1600-h/RGui%252520%25252832-bit%252529_2012-09-26_11-44-12%25255B3%25255D.jpg)<span
style="font-family: Calibri;"> </span>  
<span style="font-family: Calibri;">Variables can be used in creating
vectors, their values will replace their names</span>  
<span
style="font-family: Calibri;">[<img src="http://lh6.ggpht.com/-nwRG2ykQYCw/UO2YAiMGzLI/AAAAAAAAApk/Qp0SUMsbees/RGui%252520%25252864-bit%252529_2013-01-09_08-10-21_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_08-10-21" width="172" height="108" alt="RGui (64-bit)_2013-01-09_08-10-21" />](http://lh5.ggpht.com/-PU0ije-xt10/UO2YALnLirI/AAAAAAAAApc/vg_QmqfXuTo/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_08-10-21%25255B3%25255D.jpg)  
What about mixing different objects in a vector, implicit casting occurs
so that every element in the vector is of the same class (least common
dominator).</span>  
<span style="font-family: Calibri;">You can refer to specific member
using its location, </span>  
<span
style="font-family: Calibri;">[<img src="http://lh4.ggpht.com/-h2nBZTqJVO8/UO2YCJDeamI/AAAAAAAAAp4/yUmEDAYve3U/RGui%252520%25252864-bit%252529_2013-01-09_%0A08-16-19_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_08-16-19" width="407" height="101" alt="RGui (64-bit)_2013-01-09_08-16-19" />](http://lh5.ggpht.com/-eAyPwbr-kbo/UO2YBcpmDAI/AAAAAAAAApw/kD_5VcQQqVk/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_08-16-19%25255B3%25255D.jpg)</span>  

> <span style="font-family: Calibri; font-size: x-small;">*For you
> reference: \[ \] always returns an object of the same class as the
> original; can be used to select more than one element (retrieving
> matrix elements is exception to this rule, it returns a
> vector)*</span>

<span style="font-family: Calibri;">or members using location or
expression.</span>  
<span
style="font-family: Calibri;">[<img src="http://lh6.ggpht.com/-r6KdOO1__DI/UO2YEntu1kI/AAAAAAAAAqI/0I752isyU1o/RGui%252520%25252864-bit%252529_2013-01-09_08-18-25_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_08-18-25" width="712" height="75" alt="RGui (64-bit)_2013-01-09_08-18-25" />](http://lh3.ggpht.com/-VFDJm8h69Lg/UO2YC3-GPhI/AAAAAAAAAqA/lFpA_ZS9Ycc/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_08-18-25%25255B3%25255D.jpg)</span>  
<span style="font-family: Calibri;">or specific members using their
indices as integer vector (they will be retrieved in the order of
reference, not by their order in the original vector)</span>  
<span
style="font-family: Calibri;">[<img src="http://lh3.ggpht.com/-29ZYTTEzjiQ/UO2YF8Xya2I/AAAAAAAAAqY/QjvmrNTRDxs/RGui%252520%25252864-bit%252529_2013-01-09_08-20-40_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_08-20-40" width="192" height="54" alt="RGui (64-bit)_2013-01-09_08-20-40" />](http://lh3.ggpht.com/-2SlTGcDPRKo/UO2YFGQ5JnI/AAAAAAAAAqQ/Wx79s4vHSNw/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_08-20-40%25255B3%25255D.jpg)</span>  
<span style="font-family: Calibri;">When you perform an operation on two
vectors, R will match the elements of the two vectors pairwise and
return a vector. This is called vectorized operation.</span>  
[<img src="http://lh5.ggpht.com/-1gv900FX67g/UO2YG61csQI/AAAAAAAAAqk/ArigoLIb7fw/RGui%252520%25252864-bit%252529_2013-01-08_15-38-53_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-08_15-38-53" width="387" height="130" alt="RGui (64-bit)_2013-01-08_15-38-53" />](http://lh5.ggpht.com/-qGiHHWPPKKQ/UO2YGTqG3KI/AAAAAAAAAqg/99PqNDrZWX8/s1600-h/RGui%252520%25252864-bit%252529_2013-01-08_15-38-53%25255B3%25255D.jpg)  
<span style="font-family: Calibri;">If the two vectors aren’t the same
size, R will repeat the smaller sequence multiple times:</span>  
<span style="font-family: Calibri;"></span>  
<span
style="font-family: Calibri;">[<img src="http://lh3.ggpht.com/-tHx-vNxoyPE/UO2YIOpJawI/AAAAAAAAAq4/RxSZmjfcJuU/RGui%252520%25252864-bit%252529_2013-01-08_15-43-10_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-08_15-43-10" width="603" height="201" alt="RGui (64-bit)_2013-01-08_15-43-10" />](http://lh4.ggpht.com/-SIjWStSqD78/UO2YHU0lGsI/AAAAAAAAAqw/eetp9FyiEcc/s1600-h/RGui%252520%25252864-bit%252529_2013-01-08_15-43-10%25255B4%25255D.jpg)</span>  
<span style="
font-family: Calibri;">Note the warning if the second sequence isn’t a
multiple of the first.</span>  

<span style="color: black;"><span style="font-family: Calibri; font-size: small; font-weight: bold;">Explicit casting</span></span>
-----------------------------------------------------------------------------------------------------------------------------------

<span style="font-family: Calibri;">Objects can be explicitly casted
from one class to another using the as.\* functions, if available. like
:</span>[<span
style="font-family: Calibri;"><img src="http://lh3.ggpht.com/-Q54TpaiCvYU/UGNOBV3mxvI/AAAAAAAAAhM/OZSVMZDwnAM/RGui%252520%25252832-bit%252529_2012-09-26_12-17-35_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (32-bit)_2012-09-26_12-17-35" width="436" height="206" alt="RGui (32-bit)_2012-09-26_12-17-35" /></span>](http://lh4.ggpht.com/-it-WP1ejMGI/UGNOAx1VR1I/AAAAAAAAAhE/RzG9ql8DoMY/s1600-h/RGui%252520%25252832-bit%252529_2012-09-26_12-17-35%25255B4%25255D.jpg)<span
style="font-family: Calibri;">  
Nonsensical casting results in NAs</span>[<span
style="font-family: Calibri;"><img src="http://lh4.ggpht.com/-9UIK-YYKC3s/UGNOCTPvBaI/AAAAAAAAAhc/joibUao1CGU/RGui%252520%25252832-bit%252529_2012-09-26_12-33-20_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (32-bit)_2012-09-26_12-33-20" width="266" height="137" alt="RGui (32-bit)_2012-09-26_12-33-20" /></span>](http://lh6.ggpht.com/-PdZHHaTQUgw/UGNOBxDX9BI/AAAAAAAAAhU/UA7GyUQQ66Q/s1600-h/RGui%252520%25252832-bit%252529_2012-09-26_12-33-20%25255B3%25255D.jpg)<span
style="font-family: Calibri;"> </span>  

<span style="color: black; font-family: Calibri; font-size: small;"><span style="font-weight: bold;">Arrays</span></span>
-------------------------------------------------------------------------------------------------------------------------

<span style="font-family: Calibri;">An array is a multidimensional
vector. Vectors and arrays are stored the same way internally, but an
array may be displayed differently and accessed differently. An array
object is just a vector that’s associated with a dimension attribute.
The dimension attribute itself is an integer vector of length 2 (nrow,
ncol). Items can be referenced by its indices. </span>  
<span
style="font-family: Calibri;">[<img src="http://lh5.ggpht.com/-2Ii8FmNIgl0/UO2YJfOe47I/AAAAAAAAArI/P93DO0AFYmI/RGui%252520%25252864-bit%252529_2013-01-09_09-06-18_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_09-06-18" width="521" height="150" alt="RGui (64-bit)_2013-01-09_09-06-18" />](http://lh3.ggpht.com/-0psuAEyTliQ/UO2YIm2zdII/AAAAAAAAArA/XqhnnRuSYZ4/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_09-06-18%25255B4%25255D.jpg)</span>  
<span style="font-family: Calibri;">you can refer to part of the array
by specifying separate indices for each dimension, separated by
commas:</span>  
<span
style="font-family: Calibri;">[<img src="http://lh3.ggpht.com/-6kW67M2I9U4/UO2YLj_3iJI/AAAAAAAAArY/YdaZ0IR3NqA/RGui%252520%25252864-bit%252529_2013-01-09_09-17-58_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_09-17-58" width="193" height="105" alt="RGui (64-bit)_2013-01-09_09-17-58" />](http://lh5.ggpht.com/-Ge1WXzTRv1g/UO2YKA4Lt7I/AAAAAAAAArQ/wpjZd53txiA/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_09-17-58%25255B3%25255D.jpg)</span>  
<span style="font-family: Calibri;">to get all values in one dimension,
simply omit the indices for that dimension:</span>  
<span
style="font-family: Calibri;">[<img src="http://lh5.ggpht.com/-kl0ZReBDhNk/UO2YNFPDGZI/AAAAAAAAAro/4Je3URSgh2w/RGui%252520%25252864-bit%252529_2013-01-09_09-23-57_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_09-23-57" width="370" height="306" alt="RGui (64-bit)_2013-01-09_09-23-57" />](http://lh5.ggpht.com/-9A5oZNiFkGg/UO2YMEeTbsI/%0AAAAAAAAAArg/z-b7l-HL_OI/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_09-23-57%25255B3%25255D.jpg)</span>  
<span style="font-family: Calibri;">three dimensional arrays
</span><span
style="color: black; font-family: Calibri; font-size: small; font-weight: bold;">[<img src="http://lh4.ggpht.com/-9e5cxJzvBTo/UO2YOFZiZBI/AAAAAAAAAr4/P2hl99IF384/RGui%252520%25252864-bit%252529_2013-01-09_09-12-36_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_09-12-36" width="313" height="435" alt="RGui (64-bit)_2013-01-09_09-12-36" />](http://lh3.ggpht.com/-3puV9R4vC88/UO2YN10ecEI/AAAAAAAAArw/PdE75ua8bvY/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_09-12-36%25255B3%25255D.jpg)</span>  

<span style="color: black; font-family: Calibri; font-size: small;"><span style="font-weight: bold;">Matrices</span></span>
---------------------------------------------------------------------------------------------------------------------------

<span style="font-family: Calibri;">A Matrix is just a two-dimensional
array.</span>[<span
style="font-family: Calibri;"><img src="http://lh5.ggpht.com/-XKWo-A8GOOo/UGNODYYMfNI/AAAAAAAAAhs/sVLSqlPauoA/RGui%252520%25252832-bit%252529_2012-09-26_12-43-32_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (32-bit)_2012-09-26_12-43-32" width="279" height="199" alt="RGui (32-bit)_2012-09-26_12-43-32" /></span>](http://lh4.ggpht.com/-tBk7Y9YBq9Q/UGNOCzH5dPI/AAAAAAAAAhk/5OEPcE2o54A/s1600-h/RGui%252520%25252832-bit%252529_2012-09-26_12-43-32%25255B3%25255D.jpg)<span
style="font-family: Calibri;">  
Matrices are constructed column-wise, so entries can be thought of
starting in the upper left corner and running down the
columns.</span>[<span
style="font-family: Calibri;"><img src="http://lh3.ggpht.com/-TdJXEvgZiKQ/UGNOD614f6I/AAAAAAAAAh8/k-xfK9t9ZNI/RGui%252520%25252832-bit%252529_2012-09-26_13-36-35_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (32-bit)_2012-09-26_13-36-35" width="313" height="85" alt="RGui (32-bit)_2012-09-26_13-36-35" /></span>](http://lh4.ggpht.com/-KHEJ7f3u0pE/UGNODieKVjI/AAAAAAAAAh0/z-JSYr1CYcs/s1600-h/RGui%252520%25252832-bit%252529_2012-09-26_13-36-35%25255B3%25255D.jpg)<span
style="font-family: Calibri;">  
based on the above fact, matrices can be created directly from vectors
by adding a dimension attribute to a vector</span>[<span
style="font-family: Calibri;"><img src="http://lh4.ggpht.com/-7A0YcswR7X0/UGmSW2xX4qI/AAAAAAAAAiY/qInB6TayNpk/RGui32bit_20120930_185801_thumb1.jpg?imgmax=800" title="RGui (32-bit)_2012-09-30_18-58-01" width="327" height="149" alt="RGui (32-bit)_2012-09-30_18-58-01" /></span>](http://lh6.ggpht.com/-mAlHlcoTGjQ/UGmSWuZia1I/AAAAAAAAAiQ/6Ex5Vgna_YE/s1600-h/RGui32bit_20120930_1858013.jpg)<span
style="font-family: Calibri;">  
Matrices can be created by column-binding <span
class="underline">cbind()</span> or row-binding <span
class="underline">rbind()</span>. the example explains it all  
<span
class="underline">[<img src="http://lh5.ggpht.com/-DJM6zy9T-Rg/UGmSX10cQaI/AAAAAAAAAio/UykESY-TtZg/RGui32bit_20120930_190257_thumb1.jpg?imgmax=800" title="RGui (32-bit)_2012-09-30_19-02-57" width="175" height="208" alt="RGui (32-bit)_2012-09-30_19- 02-57" />](http://lh5.ggpht.com/-bp04OxkCerA/UGmSXSwuXTI/AAAAAAAAAig/DEOMKXW6ud4/s1600-h/RGui32bit_20120930_1902573.jpg)</span></span>  

**<span style="color: black; font-family: Calibri; font-size: small;">Lists</span>**
------------------------------------------------------------------------------------

<span style="font-family: Calibri;">Lists are a special type of vector
that can contain elements of different data types (notice that its
printing is different)</span>[<span
style="font-family: Calibri;"><img src="http://lh4.ggpht.com/-iprFyjWMMcM/UGmSYxB3PhI/AAAAAAAAAi4/UHPjJjanvq8/RGui%252520%25252832-bit%252529_2012-10-01_07-05-02_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (32-bit)_2012-10-01_07-05-02" width="341" height="265" alt="RGui (32-bit)_2012-10-01_07-05-02" /></span>](http://lh4.ggpht.com/-E3EKnlwrVKI/UGmSYFMGiLI/AAAAAAAAAiw/y7ggZHWzBSs/s1600-h/RGui%252520%25252832-bit%252529_2012-10-01_07-05-02%25255B3%25255D.jpg)<span
style="font-family: Calibri;"> </span>  

> <span style="font-family: Calibri; font-size: x-small;">*For your
> reference: \[\[ \]\] is used to extract elements of a list or a data
> frame; it can only be used to extract a single element and the type of
> the returned object doesn’t have to be a list or data frame. Doesn’t
> support partial name matching, passed name have to be exact.*</span>

<span style="font-family: Calibri;">You can name each element in a list.
Items in a list may be referred by either location or name. $ is used to
retrieve elements by name. It also supports partial name matching
(passing part of the name, not all of it)  
[<img src="http://lh6.ggpht.com/-1TuCW5EuE8U/UO2YPWG3zII/AAAAAAAAAsI/SeCXM7tOziE/RGui%252520%25252864-bit%252529_2013-01-09_09-31-33_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_09-31-33" width="368" height="321" alt="RGui (64-bit)_2013-01-09_09-31-33" />](http://lh3.ggpht.com/-_KaLnplzaY0/UO2YOzwWZZI/AAAAAAAAAsA/ccYXVI9hQYw/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_09-31-33%25255B3%25255D.jpg)</span>  
<span style="font-family: Calibri;">A list can even contain other lists
(we will refer to previous list e):</span>  
<span
style="font-family: Calibri;">[<img src="http://lh3.ggpht.com/-fgaRzfHGJLs/UO2YQh3flsI/AAAAAAAAAsY/HO3W96pdEp8/RGui%252520%25252864-bit%252529_2013-01-09_09-34-18_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_09-34-18" width="463" height="201" alt="RGui (64-bit)_2013-01-09_09-34-18" />](http://lh3.ggpht.com/-wEI2c9WdVZI/UO2YP3faOlI/AAAAAAAAAsQ/wELT3VlGYv0/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_09-34-18%25255B3%25255D.jpg)</span>  

**<span style="color: black; font-family: Calibri; font-size: small;">Factors</span>**
--------------------------------------------------------------------------------------

<span style="font-family: Calibri;">Factors are used to represent
categorical data. Factors can be unordered or ordered. Its like an
integer vector where each integer has a label, so you create a vector of
any type that is treated internally by integers. The following example
creates a factor from a vector of strings. When it prints, it prints the
values and it has an attribute <span class="underline">Levels</span>
that represents data categories of the factor elements. </span>[<span
style="font-family: Calibri;"><img src="http://lh6.ggpht.com/-Rh8wc15WkLc/UGmSZW1r7qI/AAAAAAAAAjI/A29kxnmb5B8/RGui%252520%25252832-bit%252529_2012-10-01_07-24-52_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (32-bit)_2012-10-01_07-24-52" width="468" height="79" alt="RGui (32-bit)_2012-10-01_07-24-52" /></span>](http://lh4.ggpht.com/-ytEP4zZX3R4/UGmSZHSSv9I/AAAAAAAAAjA/xuEeyE91Fg8/s1600-h/RGui%252520%25252832-bit%252529_20%0A12-10-01_07-24-52%25255B3%25255D.jpg)  
<span style="font-family: Calibri;">Factors are treated specially by
modeling functions like lm() and glm() which we will discuss later.
Using factors with labels is better than using integers because factors
are self-describing; having a variable that has values “Male” and
“Female” is better than a variable that has values 1 and 2.</span>  
<span style="font-family: Calibri;">We can call table() function on
factor c and it will give us the frequency table of each level
(category)</span>  
[<img src="http://lh5.ggpht.com/-ujLvOb_N-Hc/UO2YRgwZFLI/AAAAAAAAAsk/jOGyh12h6zU/RGui%252520%25252864-bit%252529_2013-01-08_16-42-10_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-08_16-42-10" width="108" height="75" alt="RGui (64-bit)_2013-01-08_16-42-10" />](http://lh6.ggpht.com/-dD9Zd6i_GH4/UO2YRN7wYTI/AAAAAAAAAsg/Z4x1GKX1Cw0/s1600-h/RGui%252520%25252864-bit%252529_2013-01-08_16-42-10%25255B3%25255D.jpg)  
<span style="font-family: Calibri;">We can also call unclass() function
on the factor to strip out the factor categories and show us how it is
stored underneath.</span>  
[<span
style="font-family: Calibri;"><img src="http://lh6.ggpht.com/-MSestVGZgYs/UO2YStS-NGI/AAAAAAAAAs0/PBI38XI4HQU/RGui%252520%25252864-bit%252529_2013-01-08_16-46-55_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-08_16-46-55" width="158" height="82" alt="RGui (64-bit)_2013-01-08_16-46-55" /></span>](http://lh3.ggpht.com/-B9138wXdPS4/UO2YSKCxTaI/AAAAAAAAAss/gTtSu_eM-sg/s1600-h/RGui%252520%25252864-bit%252529_2013-01-08_16-46-55%25255B3%25255D.jpg)  
<span style="font-family: Calibri;">The order of the level can be set
using the levels argument to factor(). This can be important in linear
modeling because the first level is used as the baseline level (the
first level in the factor). If you didn’t assign levels explicitly, it
will be assigned alphabetically (that’s why “no” came before “yes” in
the previous example).  </span>  
[<img src="http://lh3.ggpht.com/-YvO7epAZsAw/UO2YUShc2SI/AAAAAAAAAtI/e5IYwRL_jQQ/RGui%252520%25252864-bit%252529_2013-01-08_16-50-59_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-08_16-50-59" width="678" height="69" alt="RGui (64-bit)_2013-01-08_16-50-59" />](http://lh5.ggpht.com/-CV3vllJ_KbU/UO2YT3NYWtI/AAAAAAAAAs8/W_cDrwtVhS0/s1600-h/RGui%252520%25252864-bit%252529_2013-01-08_16-50-59%25255B3%25255D.jpg)  

<span style="color: black; font-family: Calibri; font-size: small; font-weight: bold;">Missing Values</span>
------------------------------------------------------------------------------------------------------------

Missing values are denoted by NA or NaN for undefined mathematical
operations. <span class="underline">is.na()</span> and <span
class="underline">is.nan()</span> are used to test objects if they are
NA or NaN, respectively. NA values have a class also, so there are
integer NA, character NA, etc. A NaN value is also NA but the converse
is not true.  
[<img src="http://lh4.ggpht.com/-PwGMEfUuYVA/UO2YVq44jXI/AAAAAAAAAtY/rot2HjAZBeQ/RGui%252520%25252864-bit%252529_2013-01-08_17-03-02_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-08_17-03-02" width="334" height="192" alt="RGui (64-bit)_2013-01-08_17-03-02" />](http://lh6.ggpht.com/-bT_XjQpEeAM/UO2YUzqx6TI%0A/AAAAAAAAAtQ/OOhXDZWPl7c/s1600-h/RGui%252520%25252864-bit%252529_2013-01-08_17-03-02%25255B4%25255D.jpg)  

<span style="color: black; font-family: Calibri; font-size: small;"><span style="font-weight: bold;">Data Frames</span></span>
------------------------------------------------------------------------------------------------------------------------------

<span style="font-family: Calibri;">A data frame is a list that contains
multiple named vectors that are the same length. A data frame is a lot
like a spreadsheet or a database table. Each vector represents a column
in the table. Unlike matrices, and much like database tables, data
frames can store different types of objects in each column. Data frames
have a special attribute called row.names which represents rows’ names,
which could be useful for annotating data. Data frames are usually
created by calling read.table() or read.csv() (which we will discuss
later when we come to reading data) or data.frame(). </span>  
[<img src="http://lh3.ggpht.com/-DcCjd5y_ZJk/UO2YXBSlCmI/AAAAAAAAAto/7VM8hHK3btk/RGui%252520%25252864-bit%252529_2013-01-09_10-01-42_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_10-01-42" width="551" height="207" alt="RGui (64-bit)_2013-01-09_10-01-42" />](http://lh4.ggpht.com/-eRnj8Su7-Xc/UO2YWbehlyI/AAAAAAAAAtg/NkfTbAzAKfs/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_10-01-42%25255B4%25255D.jpg)  
<span style="font-family: Calibri;">Here we create a data frame of two
columns foo and bar, foo is an integer sequence, bar is a vector of
TRUEs and FALSEs. nrow() returns the number of rows, ncol() returns the
number of columns. Since we didn’t specified row names, we got 1,2,3,4
automatically (they printed on the left of each row).</span>  
<span style="font-family: Calibri;">You can refer to columns by
name</span>  
[<img src="http://lh6.ggpht.com/-8LmWTGuNbCc/UO2YYLDs1fI/AAAAAAAAAt0/_V-Sle_ZIio/RGui%252520%25252864-bit%252529_2013-01-09_10-05-10_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_10-05-10" width="284" height="51" alt="RGui (64-bit)_2013-01-09_10-05-10" />](http://lh5.ggpht.com/-H4fqXIFVClE/UO2YXgv1gUI/AAAAAAAAAts/7waYovXzX3k/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_10-05-10%25255B3%25255D.jpg)  
<span style="font-family: Calibri;">You can retrieve a specific cell in
the data frame by specifying the column name and expression to filter
rows in this column. If you want to get the blood pressure of patient
Mike:</span>  
[<img src="http://lh5.ggpht.com/-QyTL9ugOZ2g/UO2YZMLfbQI/AAAAAAAAAuI/EChZrQ0eqr0/RGui%252520%25252864-bit%252529_2013-01-09_10-07-39_thumb%25255B3%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_10-07-39" width="521" height="47" alt="RGui (64-bit)_2013-01-09_10-07-39" />](http://lh5.ggpht.com/--jS01EuLAEU/UO2YYvAFyAI/AAAAAAAAAuA/-0ug6cNRElY/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_10-07-39%25255B5%25255D.jpg)  
<span style="font-family: Calibri;">Data frames can be converted to a
matrix by calling data.matrix() which will cast data to make it of the
same type, below it casted TRUEs and FALSEs to 1s and 0s.</span>  
[<img src="http://lh3.ggpht.com/-yuVcM9JQUYc/UO2YZxKuprI/AAAAAAAAAuU/bwdcT7JBWTw/RGui%252520%25252864-bit%252529_2013-01-08_17-23-28_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-08_17-23-28" width="240" height="169" alt="RGui (64-bit)_2013-01-08_17-23-28" />](http://lh3.ggpht.com/-tBCdNhe5EQA/UO2YZhVXe9I/AAAAAAAAAuM/hcVXc14wGyM/s1600-h/RGui%252520%25252864-bit%252529_2013-01-08_17-23-28%25255B3%25255D.jpg)  

<span style="color: black; font-family: Calibri; font-size: small; font-weight: bold;">Names</span>
---------------------------------------------------------------------------------------------------

<span style="font-family: Calibri;">R objects can have names, which is a
very useful for writing readable code and self-describing
objects.</span>  
[<span
style="font-family: Calibri;"><img src="http://lh6.ggpht.com/-zukgXB7Dcnc/UO2YbPbw2dI/AAAAAAAAAuo/31HY0bQzhZk/RGui%252520%25252864-bit%252529_2013-01-08_17-28-55_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-08_17-28-55" width="387" height="183" alt="RGui (64-bit)_2013-01-08_17-28-55" /></span>](http://lh4.ggpht.com/-2UN0BQdwkX4/UO2Yaa7NlcI/AAAAAAAAAuc/nogMR4VvE9w/s1600-h/RGui%252520%25252864-bit%252529_2013-01-08_17-28-55%25255B4%25255D.jpg)  
<span style="font-family: Calibri;">Lists can also have names.</span>  
[<span
style="font-family: Calibri;"><img src="http://lh6.ggpht.com/-A--fN3bW4Gk/UO2YcC0c1II/AAAAAAAAAu0/1F-UuJJqTF0/RGui%252520%25252864-bit%252529_2013-01-08_17-33-38_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-08_17-33-38" width="377" height="229" alt="RGui (64-bit)_2013-01-08_17-33-38" /></span>](http://lh3.ggpht.com/-qJDFO2xkAx8/UO2YbtW36DI/AAAAAAAAAus/UG-4yjVEmCA/s1600-h/RGui%252520%25252864-bit%252529_2013-01-08_17-33-38%25255B3%25255D.jpg)  
<span style="font-family: Calibri;">also matrices can have
names</span>  
[<img src="http://lh4.ggpht.com/-q1dUu-xsIkk/UO2YdRGJbhI/AAAAAAAAAvI/Av70r0wuiMo/RGui%252520%25252864-bit%252529_2013-01-08_17-36-06_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-08_17-36-06" width="431" height="111" alt="RGui (64-bit)_2013-01-08_17-36-06" />](http://lh5.ggpht.com/-DDQfmi9SOGc/UO2Ycv9dkjI/AAAAAAAAAu8/bmoyIGrBJkQ/s1600-h/RGui%252520%25252864-bit%252529_2013-01-08_17-36-06%25255B3%25255D.jpg)  
<span style="font-family: Calibri;"></span>  
<span style="font-family: Calibri;"></span>  
  
<span style="font-family: Century;">In this post we introduced R and its
data types and data structures. In future posts we will get more deep
into R. </span>
