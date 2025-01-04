--- 
title: "Introduction to R – Random Variables Generation & Probability Distribution Functions" 
date: '2013-01-17T17:07:00.001-06:00' 
tags: 
    - R Programming Language
modified_time: '2013-01-17T17:07:36.796-06:00' 
thumbnail: http://lh4.ggpht.com/-cbaFb2LsPbU/UPiEHJX\_F5I/AAAAAAAAA9Q/Gz9IbY0uFg4/s72-c/RGui-64-bit\_2013-01-17\_10-01-50\_thum.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-406573201145262576
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/01/introduction-to-r-random-variables.html
---

Simulation is important topic for statistical applications and
scientific purposes in general.

Generating Random Numbers
-------------------------

The first step in simulation is to generate random values based on your
variables distribution. R has a large number of functions that generate
the standard random variables.

for <span class="underline">Normal random variable generation</span>

**rnorm()** simulate a simple random normal variable with a given mean
and standard deviation and generate as many random values as requested.

[<img src="http://lh4.ggpht.com/-cbaFb2LsPbU/UPiEHJX_F5I/AAAAAAAAA9Q/Gz9IbY0uFg4/RGui-64-bit_2013-01-17_10-01-50_thum.jpg?imgmax=800" title="RGui (64-bit)_2013-01-17_10-01-50" width="436" height="74" alt="RGui (64-bit)_2013-01-17_10-01-50" />](http://lh3.ggpht.com/-L1OgbWvZGQg/UPiEGXhhdOI/AAAAAAAAA9M/HIgesG3k6rM/s1600-h/RGui-64-bit_2013-01-17_10-01-509.jpg)

When generating any random variable setting the random number seed with
set.seed ensures reproducibility. In the following example, notice that
the first and the third sets are identical (both called set.seed with 1
before generating the numbers), and the second is different (because we
didn’t set the seed)

[<img src="http://lh3.ggpht.com/-vbOl-SfUUO0/UPiEIQIBPeI/AAAAAAAAA9k/TvYQMwfUt7M/RGui-64-bit_2013-01-17_10-32-05_thum.jpg?imgmax=800" title="RGui (64-bit)_2013-01-17_10-32-05" width="495" height="137" alt="RGui (64-bit)_2013-01-17_10-32-05" />](http://lh6.ggpht.com/-KeCPVNBsq9U/UPiEHqE70OI/AAAAAAAAA9Y/r8zJWZWmMRM/s1600-h/RGui-64-bit_2013-01-17_10-32-056.jpg)

for <span class="underline">Poisson random variable generation</span>

**rpois()** simulate a Poisson random variable with a given rate
(lambda) and generate as many random values as requested.

[<img src="http://lh3.ggpht.com/-bqiG3w4likM/UPiEJ23n2mI/AAAAAAAAA90/3XjgwSuO1K4/RGui-64-bit_2013-01-17_10-39-53_thum.jpg?imgmax=800" title="RGui (64-bit)_2013-01-17_10-39-53" width="229" height="71" alt="RGui (64-bit)_2013-01-17_10-39-53" />](http://lh6.ggpht.com/-e-VGmx4XFak/UPiEJOH1QjI/AAAAAAAAA9s/IdlDTyGvWy8/s1600-h/RGui-64-bit_2013-01-17_10-39-537.jpg)

Radom sampling
--------------

The sample function draws randomly from a specified set of (scalar)
objects allowing you to sample from arbitrary distributions (sample
space).

[<img src="http://lh6.ggpht.com/-fb5oRnpzapo/UPiEKx3aoiI/AAAAAAAAA-A/fig_NlXZ_W4/RGui-64-bit_2013-01-17_11-31-03_thum.jpg?imgmax=800" title="RGui (64-bit)_2013-01-17_11-31-03" width="245" height="141" alt="RGui (64-bit)_2013-01-17_11-31-03" />](http://lh3.ggpht.com/-_hfkS6ikEZU/UPiEKSKdK1I/AAAAAAAAA94/9lbqtAwPVJw/s1600-h/RGui-64-bit_2013-01-17_11-31-033.jpg)

if you didn’t specified the number of values you want, sample will give
you random permutation of the sequence.

[<img src="http://lh6.ggpht.com/-Tm2puXYwuXo/UPiEMvs73MI/AAAAAAAAA-Q/2qV_C-hrIQw/RGui-64-bit_2013-01-17_11-32-51_thum.jpg?imgmax=800" title="RGui (64-bit)_2013-01-17_11-32-51" width="297" height="104" alt="RGui (64-bit)_2013-01-17_11-32-51" />](http://lh3.ggpht.com/-_HItEjFiA40/UPiELhIcaFI/AAAAAAAAA-M/V_KAoEGyuRU/s1600-h/RGui-64-bit_2013-01-17_11-32-513.jpg)

as you noticed, by default sample will not repeat values, set parameter
replace= TRUE to make it repeat .

[<img src="http://lh4.ggpht.com/-CW93xuQaF58/UPiENmY1bJI/AAAAAAAAA-g/aFRdS40-BxU/RGui-64-bit_2013-01-17_11-36-09_thum.jpg?imgmax=800" title="RGui (64-bit)_2013-01-17_11-36-09" width="287" height="37" alt="RGui (64-bit)_2013-01-17_11-36-09" />](http://lh6.ggpht.com/-ZULOobh0XA0/UPiENGjFKpI/AAAAAAAAA-Y/Qt02UFLlf_4/s1600-h/RGui-64-bit_2013-01-17_11-36-093.jpg)

Probability distribution functions
----------------------------------

Probability distributions usually have four functions associated with
them. The functions are prefixed with:

-   **r** for random number generation
-   **d** for density
-   **p** for cumulative distribution
-   **q** for quantile function

some useful distributions are:

<table>
<tbody>
<tr class="odd">
<td>Nickname</td>
<td>Distribution</td>
<td>For more information</td>
</tr>
<tr class="even">
<td>norm</td>
<td>normal distribution</td>
<td>?Normal</td>
</tr>
<tr class="odd">
<td>pois</td>
<td>poisson distribution</td>
<td>?Possion</td>
</tr>
<tr class="even">
<td>binom</td>
<td>binomial distribution</td>
<td>?Binomial</td>
</tr>
<tr class="odd">
<td>geom</td>
<td>geometric distribution</td>
<td>?Geometric</td>
</tr>
<tr class="even">
<td>t</td>
<td>students t distribution</td>
<td>?TDist</td>
</tr>
<tr class="odd">
<td>f</td>
<td>F distribution</td>
<td>?FDist</td>
</tr>
<tr class="even">
<td>chisq</td>
<td>Chi-Squared distribution</td>
<td>?Chisquare</td>
</tr>
</tbody>
</table>

function names are : prefix + distribution nickname. rnorm, rpois,
rbinom,….. –&gt; for random number generation, and so on.

In this note we introduced the basic functions for random number
generation based on variable distribution type, arbitrary random
sampling, and the associated probability distributions functions. Later
will present each of them in detail.

Stay tuned for more R notes.
