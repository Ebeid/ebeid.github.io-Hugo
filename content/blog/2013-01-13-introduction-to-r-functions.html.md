--- 
title: "Introduction to R – Functions" 
date: '2013-01-13T14:42:00.000-06:00' 
tags: 
    - R Programming Language
modified_time: '2013-03-28T09:48:04.269-05:00' 
thumbnail: http://lh4.ggpht.com/-y4l9LPyjLp0/UO8nfiQOW4I/AAAAAAAAAyQ/d1M9vOj6IBA/s72-c/RGui-64-bit\_2013-01-08\_16-25-25\_thum.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-995205592543094906
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/01/introduction-to-r-functions.html
---

<span style="color: black; font-size: x-small; font-weight: bold;">Functions</span>
-----------------------------------------------------------------------------------

<span style="font-size: x-small;">Functions are just like what you
remember from math class. Most functions are in the following form:
*f(argument1, argument2, ...)* Where f is the name of the function, and
argument1, argument2, . . . are the arguments  
to the function. Here are a few examples of built-in functions:</span>  
[<span
style="font-size: x-small;"><img src="http://lh4.ggpht.com/-y4l9LPyjLp0/UO8nfiQOW4I/AAAAAAAAAyQ/d1M9vOj6IBA/RGui-64-bit_2013-01-08_16-25-25_thum.jpg?imgmax=800" title="RGui (64-bit)_2013-01-08_16-25-25_thumb[1]" width="215" height="205" alt="RGui (64-bit)_2013-01-08_16-25-25_thumb[1]" /></span>](http://lh5.ggpht.com/-RJ4ylIVjALY/UO8nenj7uLI/AAAAAAAAAyI/EPSaz5GvCkQ/s1600-h/RGui-64-bit_2013-01-08_16-25-25_thum%25255B2%25255D.jpg)  
<span style="font-size: x-small;">Note in the last example that if you
give the argument in the default order, you can omit the names. Some
built-in functions have operator form like the following examples:
</span>  
[<span
style="font-size: x-small;"><img src="http://lh6.ggpht.com/-7GUpY7ExpGk/UO8nhAIaz5I/AAAAAAAAAyg/_KBedfokC0k/RGui-64-bit_2013-01-08_16-29-23_thum%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-08_16-29-23_thumb[3]" width="97" height="127" alt="RGui (64-bit)_2013-01-08_16-29-23_thumb[3]" /></span>](http://lh6.ggpht.com/-YYkQD8uVMjM/UO8ngRXxMcI/AAAAAAAAAyY/IQoravsvJQ8/s1600-h/RGui-64-bit_2013-01-08_16-29-23_thum%25255B2%25255D.jpg)  
<span style="font-size: x-small;">A function in R is just another object
that is assigned to a symbol. You can define your own functions in R,
assign them a name, and then call them just like the built-in functions.
Writing your function code on the R Console is hard, so R provided a
simple text editor for that. To write your code go to File &gt;&gt; New
Script. This will open the R Editor, enter the following code</span>  
[<span
style="font-size: x-small;"><img src="http://lh3.ggpht.com/-SAKhoZTlmCk/UO8nicHCq4I/AAAAAAAAAyw/T_ldhmiKWRI/RGui%252520%25252864-bit%252529_2013-01-10_09-05-56_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-10_09-05-56" width="329" height="110" alt="RGui (64-bit)_2013-01-10_09-05-56" /></span>](http://lh5.ggpht.com/-iRli5V_53xg/UO8nh3vi_MI/AAAAAAAAAyk/Nwkq3RuOD28/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_09-05-56%25255B3%25255D.jpg)  
<span style="font-size: x-small;"></span>  
<span style="font-size: x-small;">You could select the code, copy and
paste it in R console. Now you can call the function to get its result
(note that entering the function name and hitting enter retrieves the
function code. This is a useful trick to view function code before using
it).</span>  
[<span
style="font-size: x-small;"><img src="http://lh4.ggpht.com/-6InyWEZHzzA/UO8njy0NggI/AAAAAAAAAy8/G7gJkHNkZRY/RGui%252520%25252864-bit%252529_2013-01-10_10-29-47_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-10_10-29-47" width="309" height="235" alt="RGui (64-bit)_2013-01-10_10-29-47" /></span>](http://lh5.ggpht.com/-RLsFaxc0Dbs/UO8nja4EAKI/AAAAAAAAAy0/VZRZ-y__3rM/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_10-29-47%25255B3%25255D.jpg)  
<span style="font-size: x-small;">Now lets go back to the editor and
save the code in our working directory in MyCode.R (.R is the extension
for R code files). To load the code in any R code file inside the
console for use, use source() and pass the file name for it. Then you
can use the code inside that file in the console. Each time you edit
that code file, you have to call source() again to load the latest
code.</span>  
[<span
style="font-size: x-small;"><img src="http://lh5.ggpht.com/-Yk1qhRDoSpE/UO8nlGZN_cI/AAAAAAAAAzQ/vGkPznjVQ0A/RGui%252520%25252864-bit%252529_2013-01-10_10-40-49_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-10_10-40-49" width="233" height="68" alt="RGui (64-bit)_2013-01-10_10-40-49" /></span>](http://lh3.ggpht.com/-0na61sPgPTA/UO8nkYuSVbI/AAAAAAAAAzE/LkeEJHPqtUM/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_10-40-49%25255B4%25255D.jpg)  

<span style="color: black; font-size: x-small; font-weight: bold;">Arguments</span>
-----------------------------------------------------------------------------------

<span style="font-size: x-small;">A function definition in R includes
the arguments’ names (in the previous example we didn’t use any
arguments).</span>  
[<span
style="font-size: x-small;"><img src="http://lh5.ggpht.com/-kcGGO-zjc-4/UO8nmZKIVHI/AAAAAAAAAzg/F9gSSDrE_Wg/RGui%252520%25252864-bit%252529_2013-01-10_11-08-31_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-10_11-08-31" width="259" height="63" alt="RGui (64-bit)_2013-01-10_11-08-31" /></span>](http://lh3.ggpht.com/-60VMdZrd5kw/UO8nlv4F3wI/AAAAAAAAAzY/t_DHVMvLQls/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_11-08-31%25255B3%25255D.jpg)  
<span style="font-size: x-small;">Optionally, you can include **default
values for arguments**. If you specify a default value for an argument,
it will be considered optional (can be omitted from the function call).
If you provided a value for an argument with default value, your value
will override the default one. Non-optional parameters have to be
provided in the function call.</span>  
[<span
style="font-size: x-small;"><img src="http://lh4.ggpht.com/-ZkeCfWujUJI/UO8nni_WHKI/AAAAAAAAAzs/bOBcISEMOWw/RGui%252520%25252864-bit%252529_2013-01-10_11-26-13_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-10_11-26-13" width="278" height="91" alt="RGui (64-bit)_2013-01-10_11-26-13" /></span>](http://lh3.ggpht.com/-MHn_6h0dZgQ/UO8nnAarg6I/AAAAAAAAAzk/ErLFJGdL_is/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_11-26-13%25255B3%25255D.jpg)  
<span style="font-size: x-small;"></span>  
<span style="font-size: x-small;">If you want to specify a
**variable-length argument list**, specify (…) in the arguments to the
function. Everything other than the named arguments, will be stored in
the ellipsis … .To can then convert the ellipsis to a list to work with
it.</span>  
[<span
style="font-size: x-small;"><img src="http://lh5.ggpht.com/-1FzxTlVLMSY/UO8noUM8-VI/AAAAAAAAA0A/jf4auP7EGvg/RGui%252520%25252864-bit%252529_2013-01-10_12-31-13_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-10_12-31-13" width="380" height="203" alt="RGui (64-bit)_2013-01-10_12-31-13" /></span>](http://lh4.ggpht.com/-z11PJxH1swA/UO8noM8YEmI/AAAAAAAAAz0/RS5jK6fNelo/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_12-31-13%25255B3%25255D.jpg)  
<span style="font-size: x-small;">You can also refer directly to items
within the ellipsis using the variables ..1 for the first item, ..2 for
second and so on to ..9. Any argument that appear after the ellipsis in
the function call, have to be named explicitly. </span>  
<span style="font-size: x-small;">You can get the set of arguments
accepted by a function, use the args function. NULL represents the
function body.</span>  
[<img src="http://lh4.ggpht.com/-Yd1LuyevOHA/UO8npsHamdI/AAAAAAAAA0Q/Ei1Vz3EDSjQ/RGui%252520%25252864-bit%252529_2013-01-10_14-30-46_thumb%25255B3%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-10_14-30-46" width="579" height="80" alt="RGui (64-bit)_2013-01-10_14-30-46" />](http://lh5.ggpht.com/-c45-HARKbaQ/UO8npLfFnxI/AAAAAAAAA0I/mnnEmQES-Hw/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_14-30-46%25255B5%25255D.jpg)  
<span style="font-size: x-small;">You can pass named arguments any ware
in the function call by their name. Unnamed arguments have to match the
order that they are listed in the function definition. The following
lm() function calls are equivalent :</span>  
<span style="font-size: x-small;">lm(data = mydata, y ~ x, model =
FALSE, 1:100)</span>  
<span style="font-size: x-small;">lm(y ~ x, mydata, 1:100, model =
FALSE)</span>  
<span style="font-size: x-small;">Named argument are helpful if you have
a long argument list which you remember it by arguments’ names, not the
order.</span>  

<span style="font-size: x-small;"><span style="color: black; font-weight: bold;">Lazy Evaluation</span></span>
--------------------------------------------------------------------------------------------------------------

Arguments to functions are evaluated *lazily,* so they are evaluated
only as needed. The function below never uses the argument b, so calling
f(2) will not produce an error because the 2 gets positionally matched
to a (the only variable needed).  
[<img src="http://lh4.ggpht.com/-W6fJtaoNGIc/UPbev-7aTxI/AAAAAAAAA40/uGSmPAsSZLA/RGui-64-bit_2013-01-15_17-07-50_thum.jpg?imgmax=800" title="RGui (64-bit)_2013-01-15_17-07-50" width="271" height="61" alt="RGui (64-bit)_2013-01-15_17-07-50" />](http://lh5.ggpht.com/-OaJNnmJrj2k/UPbevJneacI/AAAAAAAAA4s/QMhSO8PZ02g/s1600-h/RGui-64-bit_2013-01-15_17-07-503.jpg)  
even if you will use a missing argument, R will not give an error until
the first use of this missing argument. Everything before that will
execute normally.  
[<img src="http://lh3.ggpht.com/-BxXvuGrtXkc/UPbew8fh3BI/AAAAAAAAA5E/5trf2xjwJLg/RGui%252520%25252864-bit%252529_2013-01-16_07-49-45_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-16_07-49-45" width="503" height="118" alt="RGui (64-bit)_2013-01-16_07-49-45" />](http://lh3.ggpht.com/-kghNTF3oDPw/UPbewri2AYI/AAAAAAAAA48/3T6Npejnx1Q/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_07-49-45%25255B3%25255D.jpg)  

<span style="font-size: x-small;"><span style="color: black; font-weight: bold;">Return Values </span></span>
-------------------------------------------------------------------------------------------------------------

You can use the return function to specify the value to be returned by
the function. Also R will return the last evaluated expression as the
result of the function if no return() is found.  
[<img src="http://lh4.ggpht.com/-t-oz19IQwH0/UO8nq8BRvyI/AAAAAAAAA0c/0kisBJPKFDc/RGui%252520%25252864-bit%252529_2013-01-10_12-52-41_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-10_12-52-41" width="348" height="113" alt="RGui (64-bit)_2013-01-10_12-52-41" />](http://lh3.ggpht.com/-2E3VsuC%0ADvW8/UO8nqJp36jI/AAAAAAAAA0Y/gHBUo6WY-TA/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_12-52-41%25255B3%25255D.jpg)  

<span style="color: black; font-size: x-small;"><span style="font-weight: bold;">Functions as Arguments</span></span>
---------------------------------------------------------------------------------------------------------------------

Many functions in R can take other functions as arguments. An example of
these functions, the sapply function iterates through each element in a
vector, applying another function to each element in the vector and
returning the results.  
[<img src="http://lh3.ggpht.com/-DxuiiGUzCv4/UO8nrxGQeeI/AAAAAAAAA0s/kcaxeGnx0j8/RGui%252520%25252864-bit%252529_2013-01-10_13-07-51_thumb%25255B3%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-10_13-07-51" width="581" height="54" alt="RGui (64-bit)_2013-01-10_13-07-51" />](http://lh4.ggpht.com/-hx8geuw0Imo/UO8nrZpfrKI/AAAAAAAAA0k/7QNIP15UTiM/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_13-07-51%25255B5%25255D.jpg)  

<span style="color: black; font-size: x-small;"><span style="font-weight: bold;">Anonymous Functions</span></span>
------------------------------------------------------------------------------------------------------------------

You create functions that do not have names. These are called anonymous
functions. Anonymous functions are usually passed as arguments to other
functions.  
[<img src="http://lh6.ggpht.com/-ZpIhE_rJxQ4/UO8ns3BfPjI/AAAAAAAAA1A/as78fmXCxRM/RGui%252520%25252864-bit%252529_2013-01-10_13-32-56_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-10_13-32-56" width="387" height="61" alt="RGui (64-bit)_2013-01-10_13-32-56" />](http://lh5.ggpht.com/-DTxF9mAqz_c/UO8nsYXMbBI/AAAAAAAAA00/6-9wwwpgpxY/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_13-32-56%25255B4%25255D.jpg)  
the R interpreter assigns the anonymous function *functions(x) {x \* 7}*
to the argument *f* of function *apply.to.three* then assigns 3 to the
argument x of the anonymous function. So, it will ends up by evaluating
3 \* 7 and returns the result.  
anonymous functions can also be used with sapply()  
[<img src="http://lh6.ggpht.com/-7X-o3-gzaS0/UO8nuAEWntI/AAAAAAAAA1Q/CGbWMnNu5bw/RGui%252520%25252864-bit%252529_2013-01-10_13-43-09_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-10_13-43-09" width="382" height="72" alt="RGui (64-bit)_2013-01-10_13-43-09" />](http://lh6.ggpht.com/-6wjJKug7ZQg/UO8ntrvQsoI/AAAAAAAAA1I/fgW4bO8QI8M/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_13-43-09%25255B3%25255D.jpg)  
it is possible also to define an anonymous function and apply it
directly to an argument.  
[<img src="http://lh4.ggpht.com/-7uxuUoySb2o/UO8nvMBAXlI/AAAAAAAAA1g/S40anTDgyus/RGui%252520%25252864-bit%252529_2013-01-10_13-45-53_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-10_13-45-53" width="311" height="54" alt="RGui (64-bit)_2013-01-10_13-45-53" />](http://lh6.ggpht.com/-nRKv_f-jvuE/UO8nuiSI-aI/AAAAAAAAA1Y/UHH1hixpFj4/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_13-45-53%25255B3%25255D.jpg)  

<span style="color: black;"><span style="font-size: x-small; font-weight: bold;">Scoping rules</span></span>
------------------------------------------------------------------------------------------------------------

How does R know which value to assign to which symbol ? How does R know
what value to assign to the symbol lm ? Why doesn’t it give it the value
of lm that is in the stats package ?  
[<img src="http://lh5.ggpht.com/-mmHQNHAh8HQ/UPbeyB2WKtI/AAAAAAAAA5U/-Seiu7mmV6g/RGui%252520%25252864-bit%252529_2013-01-16_09-13-32_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-16_09-13-32" width="311" height="69" alt="RGui (64-bit)_2013-01-16_09-13-32" />](http://lh4.ggpht.com/-zbDk7sUXkZE/UPbexSKAn3I/AAAAAAAAA5M/aVuoJe0EVlw/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_09-13-32%25255B3%25255D.jpg)  
When R tries to bind a value to a symbol, it searches through a series
of environments (sets of symbols, objects,…) to find the appropriate
value. When you are working on the command line and need to retrieve the
value of an R object, the search begins with the global environment you
working in it and look for a symbol name matching the one requested. If
not found, R starts searching the namespaces of each of the packages on
the search list. You can get the search list using search() function.
.*GlobalEnv* represents your current working environment on the R
command line, and its always the first element of the search list. The
*base* package is always the last one. The order on the list matters  
[<img src="http://lh4.ggpht.com/-UjPMBFk62so/UPbezWYAfuI/AAAAAAAAA5k/aoOBdZOThoY/RGui%252520%25252864-bit%252529_2013-01-16_09-25-18_thumb%25255B3%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-16_09-25-18" width="531" height="70" alt="RGui (64-bit)_2013-01-16_09-25-18" />](http://lh3.ggpht.com/-27gudoBehk0/UPbeyqTCrKI/AAAAAAAAA5Y/lDvKRbZT54U/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_09-25-18%25255B5%25255D.jpg)  
If you loaded a package with library the namespace of that package will
be in the 2nd position of the search list, and everything else will be
shifted down the list.  
[<img src="http://lh4.ggpht.com/-1vAA-eWkF1k/UPbe0Sns-9I/AAAAAAAAA50/HNTqe-tOiNA/RGui%252520%25252864-bit%252529_2013-01-16_09-34-34_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-16_09-34-34" width="522" height="114" alt="RGui (64-bit)_2013-01-16_09-34-34" />](http://lh3.ggpht.com/-eWjqT7iiJd0/UPbezgqmpWI/AAAAAAAAA5s/z_HeEKUhmnU/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_09-34-34%25255B4%25255D.jpg)  
You can also load package on the command line window by going to
Packages &gt;&gt; Load package &gt;&gt; then select the desired package
and click Ok.  
You can configure which packages to be loaded automatically on startup
to be available for you. To do that open C:\\Program
Files\\R\\&lt;Your-R-Version&gt;\\etc\\Rprofile.site using Notepad and
append the following to the bottom of the file. You can append whatever
package you want to the vestor c and it will be loaded for your on
startup.  
*<span style="color: #c0504d; font-size: x-small;">local({  
old &lt;- getOption("defaultPackages")  
options(defaultPackages = c(old, "car", "RODBC", "foreign", "DA AG",
"MASS", </span>*  
*<span style="color: #c0504d; font-size: x-small;">"lattice ",
"latticedl", "sciplot", "tree", "lme4"))  
})</span>*  
**Lexical Scoping Rules (or Static Scoping Rules)**  determines how a
value is associated with a free variable in a function. <span
class="underline">The values of *<span style="color: #9b00d3;">free
variables</span>* are searched for in the *<span
style="color: #9b00d3;">environments</span>* in which the function was
defined</span>.  
So what is a a free variable ? a free variable is not a formal argument
(arguments declared in function signature) nor a local variable that is
declared and assigned in the function body. In the following example, x
and y are formal arguments. z is a free variable. <span
style="color: #c0504d;">f &lt;- function(x, y) { x^2 + y / z }</span>  
So what is an environment ? an environment is a collection of (symbol,
value) pairs. Every environment has a parent environment, and it is
possible for an environment to have multiple children. A function + an
environment = a closure or function closure.  
So, searching for the value for a free variable starts in the
environment in which the function was defined, if not found, the search
continued to the parent environment. The search continues until we hit
the top-level environment ( workspace or the namespace of the package).
After that the search continues down the search list until we hit the
empty environment. If not found, an error is thrown.  
You can get the environment of a function using environment() (for
functions coded on the command line, that will be the global
environment). You can get the parent of an environment using
parent.env() (for functions coded on command line, it will be send item
in the search list).  
[<img src="http://lh6.ggpht.com/-BImkaKBmntU/UPbe1RgCJRI/AAAAAAAAA6E/gNcftAi9mqY/RGui%252520%25252864-bit%252529_2013-01-16_10-37-17_thumb%25255B3%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-16_10-37-17" width="656" height="208" alt="RGui (64-bit)_2013-01-16_10-37-17" />](http://lh4.ggpht.com/-8JjPCBw1zDI/UPbe05sWvBI/AAAAAAAAA58/pcws4QV15TE/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_10-37-17%25255B5%25255D.jpg)  
**Why does knowing lexical scoping rules matters ?** Typically, a
function is defined in the global environment, so that the values of
free variables will be found in the user’s workspace (which is the right
approach). However, in R you can define functions inside other
functions, in this case the environment in which a function is defined
is the body of another function.  
In this post we talked about functions and using it weather from the
console or from external files, functions as parameters, anonymous
functions, and many other low level stuff.  
Stay tuned for more R notes.
