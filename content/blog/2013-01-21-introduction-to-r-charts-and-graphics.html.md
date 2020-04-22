--- 
title: "Introduction to R – Charts and Graphics" 
date: '2013-01-21T09:40:00.001-06:00' 
tags: 
    - R Programming Language
modified_time: '2013-01-21T09:41:00.014-06:00' 
thumbnail: http://lh4.ggpht.com/-4\_BhS4vrurI/UP1hZda58-I/AAAAAAAAA\_Y/nIRmQjiEUnU/s72-c/RGui-64-bit\_2013-01-17\_14-02-00\_thum.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-4313821195834083375
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/01/introduction-to-r-charts-and-graphics.html
---

R includes several packages for visualizing data:

-   **graphics** contains plotting functions for the “base” graphing
    systems, including plot, hist, boxplot and many others.
-   **lattice** contains code for producing Trellis graphics, which are
    independent of the “base” graphics system; including functions like
    xyplot, bwplot, levelplot. It built on **grid** which implements a
    different graphing system independent of the “base” system.
-   **grDevices** contains all code implementing the various graphics
    devices, including X11, PDF, PostScript, PNG, etc.

before making you chart, you need to think in the following:

-   To what device will the chart be sent ? The default on windows is
    windows, on Mac OS X it is quartz, on Unix it is x11. You can find a
    list of devices available on your system in ?Devices
-   Is The chart for viewing temporarily on the screen, or will it
    eventually end up in a paper ? Are you using it in a presentation ?
    charts included in a paper/presentation need to use a file device
    rather than a screen device.
-   Is there a large amount of data going into the chart ? Or is it just
    a few points ?
-   Do you need to be able to resize the chart ?
-   What graphics system will you use: base or grid/lattice ?
-   Base graphics are usually constructed with each aspect of the chart
    handled separately through a series of function calls; this is often
    conceptually simpler and allows plotting to mirror the thought
    process.
-   Lattice/grid graphics are usually created in a single function call,
    so all of the graphics parameters have to be specified at once;
    specifying everything at once allows R to automatically calculate
    the necessary spacings and font sizes.

You can close the graphics device for your system with dev.off() or set
it by dev.set() or turn all the graphics devices with graphics.off().

The base graphics system has many parameters that can set and tweaked
for the whole session using par() function. Any of these parameters can
be overridden as arguments to specific plotting functions. Some
important parameters are:

-   pch the plotting symbol (default is open circle). For more options
    run example(points)
-   lty the line type (default is solid line). More information
    [here](http://students.washington.edu/mclarkso/documents/line%20styles%20Ver2.pdf)
-   lwd the line width, specified as an integer.
-   col the plotting color, specified as a number, string, or hex code;
    the colors function gives you a vector of colors by name.
-   las the orientation of the axis labels on the plot. More information
    [here](http://www.statmethods.net/advgraphs/axes.html)
-   bg the background color
-   mar the margin size
-   oma the output margin size

you can get the default value of a parameter by par(“param\_name”)

Plotting function
-----------------

-   **plot** make a scatterplot, or other type of plot depending on the
    class of the object being plotted.
-   **lines** add lines to a plot, given a vector x values and a
    corresponding vector of y values (or a 2-column matrix); this
    function just connects the dots
-   **points** add point to a plot
-   **text** add text lebels to a plot using specified x, y coordinates
-   **title** add annotations to x, y axis labels, title, subtitle, out
    margin
-   **mtext** add arbitrary text to the margins (inner or outer) of the
    plot
-   **axis** adding axis ticks/labels

[<img src="http://lh4.ggpht.com/-4_BhS4vrurI/UP1hZda58-I/AAAAAAAAA_Y/nIRmQjiEUnU/RGui-64-bit_2013-01-17_14-02-00_thum.jpg?imgmax=800" title="RGui (64-bit)_2013-01-17_14-02-00" width="575" height="593" alt="RGui (64-bit)_2013-01-17_14-02-00" />](http://lh6.ggpht.com/-wYyXWF0pVX0/UP1hYgQWtNI/AAAAAAAAA_Q/-4T5HXQ3Dlk/s1600-h/RGui-64-bit_2013-01-17_14-02-006.jpg)

now try to add some red points to it (this can be used make different
types of points on the same scatterplot)

[<img src="http://lh5.ggpht.com/-xWkzvHI3_8c/UP1hbCeXCQI/AAAAAAAAA_o/ZsfdcyDoLIU/RGui-64-bit_2013-01-17_14-04-56_thum.jpg?imgmax=800" title="RGui (64-bit)_2013-01-17_14-04-56" width="576" height="565" alt="RGui (64-bit)_2013-01-17_14-04-56" />](http://lh4.ggpht.com/-bhgFYtjQPP4/UP1hacst3dI/AAAAAAAAA_g/JvjludK07Q0/s1600-h/RGui-64-bit_2013-01-17_14-04-564.jpg)

Now lets create a plot in a PDF file.

[<img src="http://lh6.ggpht.com/-UABrCHWmyZ0/UP1hcBVImDI/AAAAAAAAA_0/cBpfKSqnXzw/RGui-64-bit_2013-01-17_14-24-59_thum.jpg?imgmax=800" title="RGui (64-bit)_2013-01-17_14-24-59" width="254" height="124" alt="RGui (64-bit)_2013-01-17_14-24-59" />](http://lh5.ggpht.com/-DVwGp63Mzsg/UP1hbyLsvfI/AAAAAAAAA_w/DRArAPXSU50/s1600-h/RGui-64-bit_2013-01-17_14-24-593.jpg)

nothing will appear on the screen but a file names “testPlot.pdf” will
be created in your working directory and contains the histogram. Notice
that you have to call dev.off() to close the PDF device.

Copying plots
-------------

You can copy your plot to another device. This is useful because some
plots require a lot of code and it can be a pain to type all that in
again for a different device.

-   **dev.copy** copy a plot from one device to another
-   **dev.copy2pdf** copy a plot to a PDF file
-   **dev.list** show a list of open graphics devices
-   **dev.next** switch control to the next graphics device on the
    device list
-   **dev.set** set control to a specific graphics device
-   **dev.off** close the current graphics device

 
-

Plotting with lattice graphics
------------------------------

Major lattice functions

-   **xyplot** the main function for creating scatterplots
-   **bwplot** for box-and-whiskers plots
-   **histogram** for histograms
-   **stripplot** like box-and-whiskers but with actual points
-   **dotplot** for dots on violin strings
-   **splom** scatterplot matrix
-   **levelplot** contoutplot for plotting image data

Lattice functions generally take a formula for their first argument,
usually of the form y ~ x | f \* g where x, y are the x, y variables,
after | are the conditioning variables (optional). The second argument
is the data frame or list from which the variables in the formula should
be obtained. If no data frame or list is passed, then the parent frame
is used. If no other arguments are passed, there are defaults that can
be used. To see some example in action before getting all the details,
run the following:

&gt; library(lattice)  
&gt; library(nlme)  
&gt; xyplot(distance ~ age | Subject, data = Orthodont)  
&gt; xyplot(distance ~ age | Subject, data = Orthodont, type = "b")

Lattice functions behave differen tly from base graphics functions. Base
graphics functions plot data directly on graphics device. Lattice
graphics functions return an object of class *trellis* which can be
stored. On the command line, trellis objects are auto printed; otherwise
you have to print the trellis object.

Lattice functions have a *panel* function that controls what happens
inside each panel of the entire plot. Lets create two sets of random
values that are linearly related; and create a factor level that will be
used as condition between them :

&gt; x &lt;- rnorm(100)  
&gt; y &lt;- x + rnorm(100, sd = 0.5)  
&gt; f &lt;- gl(2, 50, labels = c("Group 1", "Group 2"))  
&gt; xyplot(y ~ x | f)  
[<img src="http://lh6.ggpht.com/-wmJPV_j6B00/UP1hdQNLQFI/AAAAAAAABAE/fOaMFzG1muA/RGui-64-bit_2013-01-17_15-51-04_thum.jpg?imgmax=800" title="RGui (64-bit)_2013-01-17_15-51-04" width="429" height="426" alt="RGui (64-bit)_2013-01-17_15-51-04" />](http://lh4.ggpht.com/-ygwkZZtejVw/UP1hc8bDO3I/AAAAAAAAA_8/oRfKzM-UHPg/s1600-h/RGui-64-bit_2013-01-17_15-51-044.jpg)

In the previous example we used the default panel function to draw each
panel but we can write our own function to draw panels. In below example
we just added a line representing the median of y.

&gt; xyplot(y ~ x | f,  
+ panel = function(x, y, ...) {  
+ panel.xyplot(x, y, ...)  
+ panel.abline(h = median(y), lty = 2) }  
+ )

[<img src="http://lh6.ggpht.com/-0NxdAPDR20I/UP1hepSmvcI/AAAAAAAABAY/Nf_VZB6kRKc/RGui-64-bit_2013-01-17_15-56-46_thum.jpg?imgmax=800" title="RGui (64-bit)_2013-01-17_15-56-46" width="439" height="435" alt="RGui (64-bit)_2013-01-17_15-56-46" />](http://lh6.ggpht.com/-956izKU3avU/UP1heBzo3hI/AAAAAAAABAQ/Ina-iaK4JAQ/s1600-h/RGui-64-bit_2013-01-17_15-56-463.jpg)

mathematical annotation
-----------------------

R can produce [LaTeX](http://en.wikipedia.org/wiki/LaTeX)-like symbols
on a plot for mathematical annotation. Math symbols in R are expressions
that need to be wrapped in expression() function and passed to plotting
functions (that accepts text like text, mtext, axis, legend). The output
will be formatted according to LaTeX-like rules. ?plotmath gives you a
list of allowed symbols. The following shows LaTex-like chart, x-axis,
and y-axis titles:

&gt; plot(x, y, main=expression(theta==0),
ylab=expression(hat(gamma)==0),
xlab=expression(sum(x\[i\]\*y\[i\],i==1,n)))

[<img src="http://lh3.ggpht.com/-gWb1HfUBYd8/UP1hf922CaI/AAAAAAAABAo/3-3Eq0zEXIs/RGui%252520%25252864-bit%252529_2013-01-21_09-17-21_thumb%25255B3%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-21_09-17-21" width="740" height="454" alt="RGui (64-bit)_2013-01-21_09-17-21" />](http://lh4.ggpht.com/-GsRz2xcTof4/UP1hfH227uI/AAAAAAAABAg/hvkuYXjmQ3g/s1600-h/RGui%252520%25252864-bit%252529_2013-01-21_09-17-21%25255B5%25255D.jpg)

You can concatenate strings with LaTex symbols using \*. like :

[<img src="http://lh4.ggpht.com/-N-79gFczZ4Q/UP1hhPyeNqI/AAAAAAAABA0/XnSi7Hqw2HA/RGui%252520%25252864-bit%252529_2013-01-21_09-24-29_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-21_09-24-29" width="637" height="149" alt="RGui (64-bit)_2013-01-21_09-24-29" />](http://lh5.ggpht.com/-RSMWUxW1Y54/UP1hggDpWKI/AAAAAAAABAs/_sQU-2IB3VE/s1600-h/RGui%252520%25252864-bit%252529_2013-01-21_09-%0A24-29%25255B3%25255D.jpg)

If you want to use a computed value in the annotation, use substitute() 
to substitute the right hand side variable with your computed value
(provided in list()).

[<img src="http://lh6.ggpht.com/-_QmvOzfwrFs/UP1hiYYLoQI/AAAAAAAABBI/ZN_XBhpRR5c/RGui%252520%25252864-bit%252529_2013-01-21_09-31-46_thumb%25255B3%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-21_09-31-46" width="677" height="593" alt="RGui (64-bit)_2013-01-21_09-31-46" />](http://lh4.ggpht.com/-yO34GUh-LGI/UP1hhuSgP8I/AAAAAAAABA8/Bdsyf1q-B5E/s1600-h/RGui%252520%25252864-bit%252529_2013-01-21_09-31-46%25255B5%25255D.jpg)

Important help pages for plotting
---------------------------------

-   ?par set or get graphical parameters
-   ?plot generic xy charts (base)
-   ?xyplot generic xy charts (lattice)
-   ?plotmath for mathematical annotation
-   ?axis for modifying axes

In this post we explored the basic charting capabilities in R using both
base package and lattice package. Stay tuned for more R notes.
