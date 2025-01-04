---
title: 'Introduction to R – Random Variables Generation &amp; Probability Distribution Functions'
date: 2013-01-17T17:07:00.001-06:00
draft: false
url: /2013/01/introduction-to-r-random-variables.html
tags: 
- R Programming Language
---

Simulation is important topic for statistical applications and scientific purposes in general.

Generating Random Numbers
-------------------------

The first step in simulation is to generate random values based on your variables distribution. R has a large number of functions that generate the standard random variables.

for Normal random variable generation

**rnorm()** simulate a simple random normal variable with a given mean and standard deviation and generate as many random values as requested.

[![RGui (64-bit)_2013-01-17_10-01-50](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgZN8ktvP33H7_4rpfSAn06edtHCcPOs5zxJ9KxNfABeMDaDwHpG5XTi9TWKQB6HtOrlAlUggroOLDF1Gg_Su8STtHvG-EwnS8HPKPPLOz1Ke9Zd4v2ei8g7KkBFtPBldX87iICSijwwA/?imgmax=800 "RGui (64-bit)_2013-01-17_10-01-50")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEifoMps3s4n4Udjv8qXyOgh_V8-hpDnkOcfQ66_OXMiyG4yhR2s7DQQ5a4UYR7N23WMS7PJmaEJdMB3HaKIm1n2u-RZH8c7bEymAV1iuizLkzsr8sGDSIobbH3OnQumEYhOJ9aT6I_ACg/s1600-h/RGui-64-bit_2013-01-17_10-01-509.jpg)

When generating any random variable setting the random number seed with set.seed ensures reproducibility. In the following example, notice that the first and the third sets are identical (both called set.seed with 1 before generating the numbers), and the second is different (because we didn’t set the seed)

[![RGui (64-bit)_2013-01-17_10-32-05](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhEj22sjS-O4mtkgANNng0IfuvRyUVIyOXzVIHyVsyLr3VKGus8UxTh4_fHHecaN9a_QJDytTPSTU23zkMkE7qB5vvAUyHfISzg98e-5hbEsPrBxjibEwfL1Hdz39ZTE5mgKnf4tnQ6tQ/?imgmax=800 "RGui (64-bit)_2013-01-17_10-32-05")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiZfVxenpftNOcaXhkCZNWgJZi2s5z0Xp0siQC8irZ7O-gU674OcGihpm1N1wOqkb21bP2V_JoPyK1nlQxhs9MuHyf9PM610bSd5KDgwoTsENdf5UEXul3XR-lELfdcORfTrHWTbEcaAw/s1600-h/RGui-64-bit_2013-01-17_10-32-056.jpg)

for Poisson random variable generation

**rpois()** simulate a Poisson random variable with a given rate (lambda) and generate as many random values as requested.

[![RGui (64-bit)_2013-01-17_10-39-53](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi-yhQqa0fJ0IxLSw-nWL_bRYzH7FYsayRkg-D35wX4-11GkiTcKiWg_f1LFy8Zxgmn6LDNzAn63F0awIEj53xEHkVBf4i-Q_v9p4Bw7WEgHL-9Bv_KeMSf3VnAAcF7k_KSw_V-i_T8gA/?imgmax=800 "RGui (64-bit)_2013-01-17_10-39-53")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhpDNoI2PIJB9oAWsxQtQny5-2BbPkFDQB_cHTbp46lka6DTKcUHeILrzETCVdZAnR3APriOfaZ3_V2m927lgDKleXbtsi_ef3WAuZvJV31h5DM7isIoEBMJHSMg4uU5Srd7L2NtvhE8A/s1600-h/RGui-64-bit_2013-01-17_10-39-537.jpg)

Radom sampling
--------------

The sample function draws randomly from a specified set of (scalar) objects allowing you to sample from arbitrary distributions (sample space).

[![RGui (64-bit)_2013-01-17_11-31-03](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjs_EYpEDzOnlSzlaX5oL2Yl4JTQZy577m47pvtOcLPXxc-tbylZj9OZ6ZvGlxkFZ5ufyQgJZAbjwRuso-aCl1h2Id9VAUAtvCcsZqNB_1WY9uHzL7YegeyBPA3gUIghoPJrWopGJNkjQ/?imgmax=800 "RGui (64-bit)_2013-01-17_11-31-03")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEipQqSoPkIMxeyRCte5Tzu8TQk3P0f2br5LNUK6F_DjG6mwiWlp7CVK0_wiMbls9kohwv-yAzGxgd8S2fbj1FE2F2hHwBNbVHrHwY-RhVyH4uzlu1a2LmWYluRC8Dhz8i3dM3ob3ZJJbw/s1600-h/RGui-64-bit_2013-01-17_11-31-033.jpg)

if you didn’t specified the number of values you want, sample will give you random permutation of the sequence.

[![RGui (64-bit)_2013-01-17_11-32-51](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhG2IEWf7cYWp6bmJ5Dec_y11i7YVrR-e1kuLpXa9Ib1ziiwfqoWwtRiHvVpRKi9VV-xMHiX63V1W8G0CiUu6yLsAkBZ-d5QlHP_75ysdaGrlsOBGmPQC9yX-0fE4wQ2ls-nRcnaS2-fA/?imgmax=800 "RGui (64-bit)_2013-01-17_11-32-51")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh9ecf37rBnoAbmspXammUpG-Lu5m977-dHlf_cfIPPcqUytHECxoHwLhVl0-JXbIFKvZFFQMUJ_TJfpt5CPgB58MRs81KDDTTNDSNgBFspIUGAU9CQaz81LaUMf_wU2DC4gmTk7ocvaQ/s1600-h/RGui-64-bit_2013-01-17_11-32-513.jpg)

as you noticed, by default sample will not repeat values, set parameter replace= TRUE to make it repeat .

[![RGui (64-bit)_2013-01-17_11-36-09](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjFQwirtOdMb5F1RerG97fsY_3PD4BwbYnX46FkLWutCiG55p6oIc1dU3dA29CLr-wjNEPzYHYOjrwFhzEAVeSh1uHf1Oe0cdy1N4uFJ7JVyT8yBEwFhWbGBseEUAaeacBaF21VYEg7xg/?imgmax=800 "RGui (64-bit)_2013-01-17_11-36-09")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh5lbT8-iry0kqve-8XHIeP-xjvWJyvNFU0y9u1OULarUzEbz1WxN00MxVuvbbpTu5yd_y-0jUQW519-vgzQnorY2ZBMMErIuXEKzjc4oDxWgzOCRiRv3YVSB_VaJc-arL4tMVAXgq6CA/s1600-h/RGui-64-bit_2013-01-17_11-36-093.jpg)

Probability distribution functions
----------------------------------

Probability distributions usually have four functions associated with them. The functions are prefixed with:

*   **r** for random number generation
*   **d** for density
*   **p** for cumulative distribution
*   **q** for quantile function

some useful distributions are:

Nickname

Distribution

For more information

norm

normal distribution

?Normal

pois

poisson distribution

?Possion

binom

binomial distribution

?Binomial

geom

geometric distribution

?Geometric

t

students t distribution

?TDist

f

F distribution

?FDist

chisq

Chi-Squared distribution

?Chisquare

function names are : prefix + distribution nickname. rnorm, rpois, rbinom,….. –> for random number generation, and so on.

In this note we introduced the basic functions for random number generation based on variable distribution type, arbitrary random sampling, and the associated probability distributions functions. Later will present each of them in detail.

Stay tuned for more R notes.