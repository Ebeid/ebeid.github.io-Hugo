---
title: 'Introduction to R – Charts and Graphics'
date: 2013-01-21T09:40:00.001-06:00
draft: false
url: /2013/01/introduction-to-r-charts-and-graphics.html
tags: 
- R Programming Language
---

R includes several packages for visualizing data:

*   **graphics** contains plotting functions for the “base” graphing systems, including plot, hist, boxplot and many others.
*   **lattice** contains code for producing Trellis graphics, which are independent of the “base” graphics system; including functions like xyplot, bwplot, levelplot. It built on **grid** which implements a different graphing system independent of the “base” system.
*   **grDevices** contains all code implementing the various graphics devices, including X11, PDF, PostScript, PNG, etc.

before making you chart, you need to think in the following:

*   To what device will the chart be sent ? The default on windows is windows, on Mac OS X it is quartz, on Unix it is x11. You can find a list of devices available on your system in ?Devices
*   Is The chart for viewing temporarily on the screen, or will it eventually end up in a paper ? Are you using it in a presentation ? charts included in a paper/presentation need to use a file device rather than a screen device.
*   Is there a large amount of data going into the chart ? Or is it just a few points ?
*   Do you need to be able to resize the chart ?
*   What graphics system will you use: base or grid/lattice ?
*   Base graphics are usually constructed with each aspect of the chart handled separately through a series of function calls; this is often conceptually simpler and allows plotting to mirror the thought process.
*   Lattice/grid graphics are usually created in a single function call, so all of the graphics parameters have to be specified at once; specifying everything at once allows R to automatically calculate the necessary spacings and font sizes.

You can close the graphics device for your system with dev.off() or set it by dev.set() or turn all the graphics devices with graphics.off().

The base graphics system has many parameters that can set and tweaked for the whole session using par() function. Any of these parameters can be overridden as arguments to specific plotting functions. Some important parameters are:

*   pch the plotting symbol (default is open circle). For more options run example(points)
*   lty the line type (default is solid line). More information [here](http://students.washington.edu/mclarkso/documents/line%20styles%20Ver2.pdf)
*   lwd the line width, specified as an integer.
*   col the plotting color, specified as a number, string, or hex code; the colors function gives you a vector of colors by name.
*   las the orientation of the axis labels on the plot. More information [here](http://www.statmethods.net/advgraphs/axes.html)
*   bg the background color
*   mar the margin size
*   oma the output margin size

you can get the default value of a parameter by par(“param\_name”)

Plotting function
-----------------

*   **plot** make a scatterplot, or other type of plot depending on the class of the object being plotted.
*   **lines** add lines to a plot, given a vector x values and a corresponding vector of y values (or a 2-column matrix); this function just connects the dots
*   **points** add point to a plot
*   **text** add text lebels to a plot using specified x, y coordinates
*   **title** add annotations to x, y axis labels, title, subtitle, out margin
*   **mtext** add arbitrary text to the margins (inner or outer) of the plot
*   **axis** adding axis ticks/labels

[![RGui (64-bit)_2013-01-17_14-02-00](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgZtS4ERhEYssW3_rnoDcs3DR1ZveUPRr54f1V_VtQTl65ONxp4YdfM7yQPYp36QHJ6kOYfn1Cc_L5lk0v1wyR6hwGWB_eE_F1Be0j8vZRt3qbg6vA_OOaS-vW_AnlYzqcN9ZbXnPKicw/?imgmax=800 "RGui (64-bit)_2013-01-17_14-02-00")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhFRwAbGc8a9mIVnEPljTnZpYt_zA4d81RFEBMI00G9pxnbd9bYBIocpu2VCqbMyhQgoe6Ppz6WGkvHyx_ZrEfUPAIsWVRwjIaRYXzT36yQV-QZLrsnwJD_T6SjqhaQcPla-nm95834RQ/s1600-h/RGui-64-bit_2013-01-17_14-02-006.jpg)

now try to add some red points to it (this can be used make different types of points on the same scatterplot)

[![RGui (64-bit)_2013-01-17_14-04-56](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiB3_27UyfmKv8LzQOOUkStDnZ-7vPq559yNl3xSLmpnhbdr222olGhQXGPUjAZFOqxMD7eM-tiJBUggdtUlt5eGGau43i2DZgLO3uhPLfPsDRf5YlBBYH-_m6TAJtQajdvVdILmsPkXQ/?imgmax=800 "RGui (64-bit)_2013-01-17_14-04-56")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiRPIycTWsv1W3H-_vRnGyPdYhjW0D7ir34r7zzCtqarMvZM1CBqS-PemD8Vo2LKCDObwZVZwqSvNb7LpVCjrz8cqIY6Nw18oxBXZpi133C8kiZveDg8Cv-Hf2cCBlN6F-uCu22Ev41MA/s1600-h/RGui-64-bit_2013-01-17_14-04-564.jpg)

Now lets create a plot in a PDF file.

[![RGui (64-bit)_2013-01-17_14-24-59](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg1NWxOiLkkcMH5_gCkMSJfUJtm83log2PWkTNOJHHxvN3tAbXYUIYq2stZF24gkYXRkWp1Lt4Gdahvwbbvv3Kspz9Eimcli6xFaOabG5Fcv4jnJHxzvZKyXhbGRg6zu6KqDvuz_NrEOQ/?imgmax=800 "RGui (64-bit)_2013-01-17_14-24-59")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjo6eCCzjtUqVdBDLXRho8IDDZ9ZqstyN45L2w7jOHYT3E9mFzATMNS2X7cNQS0RVCxYMx7hnRGdasR8lQ_38j13UpJpPWtG5cETr_qnmwnn9HScVwb9KreGwaVw0X3GZYuNaJODBsQdw/s1600-h/RGui-64-bit_2013-01-17_14-24-593.jpg)

nothing will appear on the screen but a file names “testPlot.pdf” will be created in your working directory and contains the histogram. Notice that you have to call dev.off() to close the PDF device.

Copying plots
-------------

You can copy your plot to another device. This is useful because some plots require a lot of code and it can be a pain to type all that in again for a different device.

*   **dev.copy** copy a plot from one device to another
*   **dev.copy2pdf** copy a plot to a PDF file
*   **dev.list** show a list of open graphics devices
*   **dev.next** switch control to the next graphics device on the device list
*   **dev.set** set control to a specific graphics device
*   **dev.off** close the current graphics device

Plotting with lattice graphics
------------------------------

Major lattice functions

*   **xyplot** the main function for creating scatterplots
*   **bwplot** for box-and-whiskers plots
*   **histogram** for histograms
*   **stripplot** like box-and-whiskers but with actual points
*   **dotplot** for dots on violin strings
*   **splom** scatterplot matrix
*   **levelplot** contoutplot for plotting image data

Lattice functions generally take a formula for their first argument, usually of the form y ~ x | f \* g where x, y are the x, y variables, after | are the conditioning variables (optional). The second argument is the data frame or list from which the variables in the formula should be obtained. If no data frame or list is passed, then the parent frame is used. If no other arguments are passed, there are defaults that can be used. To see some example in action before getting all the details, run the following:

\> library(lattice)  
\> library(nlme)  
\> xyplot(distance ~ age | Subject, data = Orthodont)  
\> xyplot(distance ~ age | Subject, data = Orthodont, type = "b")

Lattice functions behave differently from base graphics functions. Base graphics functions plot data directly on graphics device. Lattice graphics functions return an object of class _trellis_ which can be stored. On the command line, trellis objects are auto printed; otherwise you have to print the trellis object.

Lattice functions have a _panel_ function that controls what happens inside each panel of the entire plot. Lets create two sets of random values that are linearly related; and create a factor level that will be used as condition between them :

\> x <- rnorm(100)  
\> y <- x + rnorm(100, sd = 0.5)  
\> f <- gl(2, 50, labels = c("Group 1", "Group 2"))  
\> xyplot(y ~ x | f)  
[![RGui (64-bit)_2013-01-17_15-51-04](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhaaoDoCRhy8yDZwZ4VtsBtqANHvXL4iRYk565eMqVxkRJZhgipv9ZhI99cETkcKwEKSfoc3ywcCRGIT00pQRpXuUVRDtYgysTGRD0q_E6M9SUcJ017Rxmm2edt0b-yV1K3x5UMCDwy9A/?imgmax=800 "RGui (64-bit)_2013-01-17_15-51-04")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhbyvSJ5AP6IDKHSt1xRRNJ1XjPYf60dFeaQdXqf-EjUTeODTa61KsHi2NhgXvOc9vBPMu0_PDO3kjpD_ea7HyI-X0Jd-pX1SvwFVtVUZqWTzJDIOFvIUqZoe9wn1kfkz6uxLPSXEorhQ/s1600-h/RGui-64-bit_2013-01-17_15-51-044.jpg)

In the previous example we used the default panel function to draw each panel but we can write our own function to draw panels. In below example we just added a line representing the median of y.

\> xyplot(y ~ x | f,  
\+ panel = function(x, y, ...) {  
\+ panel.xyplot(x, y, ...)  
\+ panel.abline(h = median(y), lty = 2) }  
\+ )

[![RGui (64-bit)_2013-01-17_15-56-46](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiVuvuDZSex7RRrRB1v31MdEL_XebPF0RCFjZi86luQrYWJWmUIggj46oQb3FxYYMweITv2UCDGyegYTD0_qoMYQ-ZOnpSmx4vPIzjJIJQRJTXbCb7hnLtfNN3TxEkzgc3oFI8iVAb0wg/?imgmax=800 "RGui (64-bit)_2013-01-17_15-56-46")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhH7CwB9rEnaqIjhp9VIdooNKdH_jbPfw0lrqH64kcMZuFWwFrWfjfTscwt1DvT6622wu5HQRxT36MFMULCN6PlQP3cJbItwwoe5FfGiJqfB04O0q5_Js4teXTOSkH_UAV4Gmak2mgp5w/s1600-h/RGui-64-bit_2013-01-17_15-56-463.jpg)

mathematical annotation
-----------------------

R can produce [LaTeX](http://en.wikipedia.org/wiki/LaTeX)\-like symbols on a plot for mathematical annotation. Math symbols in R are expressions that need to be wrapped in expression() function and passed to plotting functions (that accepts text like text, mtext, axis, legend). The output will be formatted according to LaTeX-like rules. ?plotmath gives you a list of allowed symbols. The following shows LaTex-like chart, x-axis, and y-axis titles:

\> plot(x, y, main=expression(theta==0), ylab=expression(hat(gamma)==0), xlab=expression(sum(x\[i\]\*y\[i\],i==1,n)))

[![RGui (64-bit)_2013-01-21_09-17-21](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhwbutulWqIbXrjStHIzQoUKS-YU78YK98a1a3bygVdRmDVaqfbIL_w7h_Y35TgHnF0M6ahykKMV5HzmXYXdgkoLjaAMeaulype6L3IjhilDEA8tyU4RTKYctTO2t663bEupKL8JHlMRA/?imgmax=800 "RGui (64-bit)_2013-01-21_09-17-21")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiY02UBeo9iE4aFDAJMEsDszG3ujYpjb31OXhwBDrQFTI22kRK-MXFlxCuHLoq13QUk-tg50T1CO3dcUisAV-V88jJguk9f4SC9iORDXDDIU2ehRfal3h7vUAdUbgV7yNvAXDKjFy0GmA/s1600-h/RGui%252520%25252864-bit%252529_2013-01-21_09-17-21%25255B5%25255D.jpg)

You can concatenate strings with LaTex symbols using \*. like :

[![RGui (64-bit)_2013-01-21_09-24-29](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgiNxFfdun72O8eySwZTtDrn_cQtEyXpHop8d0nTX9O2X4ocDsa1o_x0tyF9VvdJSwS9z4LtZ22unjiokRxZM-y-JvEI3z0_neS9lAsX6xcolQY6PWqzPFYwGPEUZmXx6J5G4zdVVPUBw/?imgmax=800 "RGui (64-bit)_2013-01-21_09-24-29")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhqzLh-C8bNhElhdVo18VwjG6HG4rzQWn1d3wouRD8RqZr-p2bSfl6eQzBWctfh-FV33czU7DJ0m8x99hvYQG56PThaKaDcEpl2fMukMHjRtQoVejAK-O-Odul6j_JkKaalTrdySgJrCA/s1600-h/RGui%252520%25252864-bit%252529_2013-01-21_09-24-29%25255B3%25255D.jpg)

If you want to use a computed value in the annotation, use substitute()  to substitute the right hand side variable with your computed value (provided in list()).

[![RGui (64-bit)_2013-01-21_09-31-46](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhs-XAeiCChMWDLi9syYxaun89UhLWK7ut0B9HOCgxjFvm5wgRWYTVYoEoYV9H927MpUeQEUXzBE3vaR3xuUTHtp0DTKlFh7gAg0cEOTlu99DgSHvPsUVu1P0xUo5BOQTthamsDUhcZZw/?imgmax=800 "RGui (64-bit)_2013-01-21_09-31-46")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiBjOwMgzgiwX9P7bKZa9qVavzOfQPb_FLmUyAd1E9xjsGJkBsmukaBs9nWTzz63sIN3Z7tSdv6N9yYYvICG7DFxKihAI_IcXa1YmVEa2gV0_9Vyh843SEFkUMxLvFUf1Yr1EgQAM6thg/s1600-h/RGui%252520%25252864-bit%252529_2013-01-21_09-31-46%25255B5%25255D.jpg)

Important help pages for plotting
---------------------------------

*   ?par set or get graphical parameters
*   ?plot generic xy charts (base)
*   ?xyplot generic xy charts (lattice)
*   ?plotmath for mathematical annotation
*   ?axis for modifying axes

In this post we explored the basic charting capabilities in R using both base package and lattice package. Stay tuned for more R notes.