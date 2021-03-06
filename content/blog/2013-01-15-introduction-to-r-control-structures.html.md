--- 
title: "Introduction to R – Control Structures" 
date: '2013-01-15T16:43:00.001-06:00' 
tags: 
    - R Programming Language
modified_time: '2013-01-16T15:14:53.703-06:00' 
thumbnail: http://lh5.ggpht.com/-fdfAj4LBhPM/UPXbbqQp55I/AAAAAAAAA24/RN9iNcDl3Ks/s72-c/RGui%252520%25252864-bit%252529\_2013-01-15\_15-43-49\_thumb%25255B3%25255D.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-5089175416861366139
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/01/introduction-to-r-control-structures.html
---

Like every other programing language, R have control structures that
allow you control the flow of your code execution.

**If, else** for testing a condition. else section is optional.

[<img src="http://lh5.ggpht.com/-fdfAj4LBhPM/UPXbbqQp55I/AAAAAAAAA24/RN9iNcDl3Ks/RGui%252520%25252864-bit%252529_2013-01-15_15-43-49_thumb%25255B3%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-15_15-43-49" width="742" height="62" alt="RGui (64-bit)_2013-01-15_15-43-49" />](http://lh6.ggpht.com/-gYJ4GV0bDS8/UPXbbL8gR-I/AAAAAAAAA2w/eMueMr7ukjA/s1600-h/RGui%252520%25252864-bit%252529_2013-01-15_15-43-49%25255B5%25255D.jpg)

if it’s all about assigning a value to a variable, you can do like this

[<img src="http://lh4.ggpht.com/-OKbUX7D_9vs/UPXbdIQmEVI/AAAAAAAAA3I/HW3vYEQ59T8/RGui%252520%25252864-bit%252529_2013-01-15_15-46-22_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-15_15-46-22" width="739" height="56" alt="RGui (64-bit)_2013-01-15_15-46-22" />](http://lh6.ggpht.com/-iYk2p5vu19s/UPXbcmvSsiI/AAAAAAAAA3A/VUgTCt98Uas/s1600-h/RGui%252520%25252864-bit%252529_2013-01-15_15-46-22%25255B4%25255D.jpg)

**for** for executing a loop for a fixed number of times. It takes a
variable and assign it successive values from a sequence or vector.

[<img src="http://lh4.ggpht.com/-oqRBWSaXfEk/UPXbeYZJBsI/AAAAAAAAA3Y/PnmmfRkrPmw/RGui%252520%25252864-bit%252529_2013-01-15_15-59-06_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-15_15-59-06" width="310" height="356" alt="RGui (64-bit)_2013-01-15_15-59-06" />](http://lh6.ggpht.com/-YJkO5zxWoz8/UPXbeDnAPnI/AAAAAAAAA3Q/1QjCGy97i7A/s1600-h/RGui%252520%25252864-bit%252529_2013-01-15_15-59-06%25255B4%25255D.jpg)

**while** for executing a loop while a condition is true. It begins by
testing that condition, if it is true, the loop body will execute, if
not, R will skip the loop.

[<img src="http://lh6.ggpht.com/-Z17A4aa5i0A/UPXbf5FdDSI/AAAAAAAAA3k/ZIE-Xu8Blm0/RGui%252520%25252864-bit%252529_2013-01-15_16-08-36_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-15_16-08-36" width="222" height="287" alt="RGui (64-bit)_2013-01-15_16-08-36" />](http://lh5.ggpht.com/-6nXAmd51H7w/UPXbfbYOK8I/AAAAAAAAA3g/HvZ8SmKrbo8/s1600-h/RGui%252520%25252864-bit%252529_2013-01-15_16-08-36%25255B3%25255D.jpg)

**repeat** for executing an infinite loop; the only way to exit the loop
is to call break

[<img src="http://lh3.ggpht.com/-ttr49u4HAEk/UPXbiKttCfI/AAAAAAAAA34/8d8iMLxYrT0/RGui%252520%25252864-bit%252529_2013-01-15_16-12-57_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-15_16-12-57" width="215" height="354" alt="RGui (64-bit)_2013-01-15_16-12-57" />](http://lh3.ggpht.com/-KsJQCVWGWkU/UPXbgis3aKI/AAAAAAAAA3w/R3FsdYSGfac/s1600-h/RGui%252520%25252864-bit%252529_2013-01-15_16-12-57%25255B4%25255D.jpg)

**break** for breaking the e xecution of a loop and continue from the
next line of code after the loop (just like in the previous example)

**next** is used to skip an iteration of a loop

[<img src="http://lh6.ggpht.com/-i97OGM-Un3Q/UPXblJ5gQQI/AAAAAAAAA4I/3OfVZGGZwXM/RGui%252520%25252864-bit%252529_2013-01-15_16-35-49_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-15_16-35-49" width="162" height="132" alt="RGui (64-bit)_2013-01-15_16-35-49" />](http://lh4.ggpht.com/-qOBH7jfJcf4/UPXbj_X7WJI/AAAAAAAAA4A/udDZVv0kt9c/s1600-h/RGui%252520%25252864-bit%252529_2013-01-15_16-35-49%25255B3%25255D.jpg)

Writing multiple lines of code on the command-line interactive
environment is hard. I have used the script editor to write the code in
this post and then copied it to R console.

Loop functions
--------------

Loop functions is so similar to loops. It just more compact and easy to
use on command line.

**lapply** loop over a list and evaluate a function on each element. If
the first argument wasn’t a list, it will be coerced to a list (using
as.list). lapply always returns a list. Any arguments passed to lapply
beyonf the FUN parameter, will be assigned to the ellipsis and then
passed as parameters to FUN. FUN can be an anonymous function.

[<img src="http://lh6.ggpht.com/-F41GRpZ39PM/UPcYOVrd5UI/AAAAAAAAA60/7-OCkUY3TKg/RGui%252520%25252864-bit%252529_2013-01-16_12-46-03_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-16_12-46-03" width="367" height="323" alt="RGui (64-bit)_2013-01-16_12-46-03" />](http://lh4.ggpht.com/-goBil_EXhw8/UPcYNtbm4XI/AAAAAAAAA6s/5JGsOz_3_JU/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_12-46-03%25255B3%25255D.jpg)

**sapply** will try to simplify the result of lapply if possible. If the
result is a list where every element is length 1, then it returns a
vector. If the result is a list where every element is a vector of the
same length (&gt;1), it returns a matrix. If it can’t figure things out,
it returns a list.

[<img src="http://lh3.ggpht.com/-MVw0bOGuSSI/UPcYPwy4TmI/AAAAAAAAA7A/YKsLAlbOt2w/RGui%252520%25252864-bit%252529_2013-01-16_12-59-27_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-16_12-59-27" width="389" height="91" alt="RGui (64-bit)_2013-01-16_12-59-27" />](http://lh4.ggpht.com/-gIO1qG5mtz8/UPcYPF5gIyI/AAAAAAAAA68/lNvAVcd_Z24/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_12-59-27%25255B3%25255D.jpg)

**apply** apply a function over the margins of an array. Often used to
apply a function to rows and columns of a matrix. It takes as parameters
the array; margin which indicates which dimension will be used as
parameter to the function applied; and the function to be applied. In
the example below, when passing 2 for the margin it means apply the
function to columns, so we got a result of vector with length 10
containing the sum of each column. When we passed 1 for the margin, it
means apply the function to rows, so we got a result of vector with
length 20 containing the sum of each row.

[<img src="http://lh5.ggpht.com/-B-b41FL0Vck/UPcYRfiEEhI/AAAAAAAAA7U/fj-nGue_Rys/RGui%252520%25252864-bit%252529_2013-01-16_13-15-23_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-16_13-15-23" width="519" height="433" alt="RGui (64-bit)_2013-01-16_13-15-23" />](http://lh5.ggpht.com/-4hQWB3hV4s0/UPcYQUL4FoI/AAAAAAAAA7M/mrg0KPKtn4s/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_13-15-23%25255B4%25255D.jpg)

for sums and means of matrix dimensions, we have some shortcuts:

-   rowSums = apply(x, 1, sum)
-   rowMeans = apply(x, 1, mean)
-   colSums = apply(x, 2, sum)
-   colMeans = apply(x, 2, mean)

**tapply** apply a function over subsets of a vector. It is equal to
using split and lapply together. **split** take a vector or other
objects and splits it into groups determined by a factor or list of
factors.

**mapply** is a multivariate version of lapply. Each element will in 1:4
repeated by the corresponding number in 4:1.

[<img src="http://lh4.ggpht.com/-_oRdnWA-Qu4/UPcYSzitK-I/AAAAAAAAA7k/oXZldYm_ZRc/RGui%252520%25252864-bit%252529_2013-01-16_14-14-26_thumb%25255B2%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-16_14-14-26" width="398" height="424" alt="RGui (64-bit)_2013-01-16_14-14-26" />](http://lh5.ggpht.com/-sMx4ASwbzxU/UPcYSJlZaZI/AAAAAAAAA7Y/2kgm0ModWm4/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_14-14-26%25255B4%25255D.jpg)

In this post we introduced the basic control structured in R. Its almost
the same in any c-like programming language.

Stay tuned for more R notes.
