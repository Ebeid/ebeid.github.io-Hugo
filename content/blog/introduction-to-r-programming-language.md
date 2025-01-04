---
title: 'Introduction to R Programming Language'
date: 2013-01-08T13:44:00.000-06:00
draft: true
url: 
tags: 
- R Programming Language
---

**R** is an open source programming language and software environment for statistical computing and graphics. The R language is widely used among statisticians for developing statistical software and data analysis. R was created by [Ross Ihaka](https://www.facebook.com/pages/w/103371346383347) and [Robert Gentleman](https://www.facebook.com/pages/w/126921034017343) at the [University of Auckland](https://www.facebook.com/pages/w/105560002810339), New Zealand, and now, R is developed by the _R Development Core Team_. To download R and install it on your computer, you can get it at the Comprehensive R Archive Network ([http://cran.r-project.org](http://cran.r-project.org/)). One option that you may want to explore is RStudio ([http://rstudio.org](http://rstudio.org/)) which is a very nice front-end to R and works on all platforms.  
The R System is divided into 2 conceptual parts:  

1.  The “base” R system that you download and install from CRAN. This part is required to run R, and it contains the most fundamental functions.
2.  Everything else as can be downloaded as a separate package from CRAN.

**Data Types**
--------------

*   R has five basic types of objects: character, numeric (real numbers), integer, complex, logical.
    *   Numbers in R are numeric by default. If you want an integer, you need to specify the L suffix.
        *   Ex: Entering 1 gives you a numeric object; entering 1L explicitly gives you an integer.
    *   Special number Inf represents infinity
    *   The value NaN represents an undefined value
*   A **vector** is a container that can contain objects of the same types only. Empty vectors can be created with the vector() function.
*   A **list** can contain objects of different types.

**Attributes**
--------------

R objects can have attributes: names or dimnames, dimensions (e.g. matrices, arrays), class, length, or any other user-defined attributes/metadata. attributes of an object can be access using the attributes() function.  

**First use of R prompt**
-------------------------

Go to Start > Programs > R > R . This will open the R prompt which we will use to test basic statements. The <- symbol is the assignment operator. When a complete expression is entered at the prompt, it is evaluated and the result of the evaluated expression is returned. The result may/not be auto-printed. The \[1\] indicates the index of the element in the vector. The # character indicates a comment and anything right to it is ignored.  
[![RGui (32-bit)_2012-09-25_16-24-35](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjumRfvZqw-oo-xdYzFXN17OIWtkiYrMgeSP9J59caILkpU7vnPCaidXCViCAYAGH3AdbTsizf9Y1h3NCdFD-74CvR9TR3igOMI2HhyphenhyphenrB6V001i_rZhBVEnYhOopUi0nWAGJ3tRCG5AtA/?imgmax=800 "RGui (32-bit)_2012-09-25_16-24-35")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjb3HXNn0v_d1A-IkdEqYR9pzOXr9ZTu6tNKKp1F2PaoqIuYhURZrYPyY-YYO15cPrixKPzyjsQ3Prn6ROXYTWhgnx9bRw_DmpK-c8Fl7nMZQgdvyEQ3i-geENLXXZkyOH55bl9Bhmfxw/s1600-h/RGui%252520%25252832-bit%252529_2012-09-25_16-24-35%25255B2%25255D.jpg)  
The **:** operator can be used to create integer sequence vector.  
[![RGui (32-bit)_2012-09-25_16-58-36](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiRKaB6EWbvsQz4-VSKoFT2JO_mm6ysyYCQPN2XLUyhgm77bhrJZKLQ-S4vxPTtF3puug0RbgSVnUZswZfhkeZg8jqMc8P_R2S6mFCnHp7c62-ts6w6RoQUaGQhu6QPpTwtwjOiyYsW1w/?imgmax=800 "RGui (32-bit)_2012-09-25_16-58-36")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEimLig0Vxbo61su5Va9W872EDqWGu7mPpjE1zSdf1I_MvTR5VlygB87OF2C5VppWJwTHlqROHnGH7twVBAqqTssaQPtOBdIsPPj7WyRpZoFGwWmanRiw3UPb9TGRuf43sOJ5AWrWOIfCg/s1600-h/RGui%252520%25252832-bit%252529_2012-09-25_16-58-36%25255B3%25255D.jpg)  
THe c() function can be used to create vectors of objects.  
[![RGui (32-bit)_2012-09-26_11-08-00](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhnci_kCsS24v1Y35ZbhL8tZnWxxXYc2_cU8Z255UD-isJ3AfAizvNFdsvt2EviHx3j3ygmuaSU_mJ7fwJO9H0xAL4EcSENVDUw9TH4FRbKyvAgyREgIBDUwuIitqInDoflfqfRPlrX4A/?imgmax=800 "RGui (32-bit)_2012-09-26_11-08-00")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgz0zVJQB5LUAbsx0UTRNrnxRR15R99xh41QLtyqJ6_ueb6HLc1kj_DL86Wv0q8_DV4RUtCPd0R-uQGcbpz-mxHz0eb7KxupjsStwAS69Z1yIL8gFkZSmbQ3zp6BtpW5tW2YTaJue48vQ/s1600-h/RGui%252520%25252832-bit%252529_2012-09-26_11-08-00%25255B3%25255D.jpg)  
You could use the vector() function to specify the vector type and length and it will create an empty vector for you.  
[![RGui (32-bit)_2012-09-26_11-44-12](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgqZOUB01BPobdHqEx7pFbjIPO5nLMyenuDp9CQ0nUQeiKjd349ix7J5O80Qjk1WXfU3ZSVWyf2ydW_K_Gs9SAr-bBFna_7KwQH7FhY6ZIHNX6GhIHNu8uKquvCR4if2LbcDk12g51yPw/?imgmax=800 "RGui (32-bit)_2012-09-26_11-44-12")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEguOF4EU2BheMVy_VtdeYETESpZ-xMmDaobXJHgToLRXgnhACR9At0BhzhsteUxZgxfaYozQWCjXXXCr8Mt0-k4j5tLilN2gJ5eFSVeq1g-7W6lDli_vj7bE8OEP-QwJazZJWvO3ULFHw/s1600-h/RGui%252520%25252832-bit%252529_2012-09-26_11-44-12%25255B3%25255D.jpg)  
What about mixing different objects in a vector, implicit casting occurs so that every element in the vector is of the same class (least common dominator).  

**Explicit casting**
--------------------

Objects can be explicitly casted from one class to another using the as.\* functions, if available. like :  
[![RGui (32-bit)_2012-09-26_12-17-35](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEghAkK_2vAQEHO-9Lxs8kdof-y8otSNj-M858v4xYoRP2MH16k_qlE1QSJDtXhbG_08v6SxPfKpO0sGwv3gNMjAmoby-O1T6Rz2fRF-LconunZ2Dyuikcc85atKTpcZv-rCSi9t-nLnAA/?imgmax=800 "RGui (32-bit)_2012-09-26_12-17-35")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgusTzfSzK50Upd28Sr_ptStKvNilXxiwIqymEMGb7tRg052A4LyHh-SGHlAho9G49GSVfuZXz3TachtMsEbQp-cwhewMprtbdWroc6NK7T41jG0BgXLgOsa1d0SaeH6PmJ83NgTHRL8Q/s1600-h/RGui%252520%25252832-bit%252529_2012-09-26_12-17-35%25255B4%25255D.jpg)  
Nonsensical casting results in NAs  
[![RGui (32-bit)_2012-09-26_12-33-20](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEibkN8uUgzpJZUu73hPg5tBSShA6yCxujWiXfX-SWrOAVl7VHTnTuaq966CnDhSwQwcUnfdIGbUPUSJGlVmFBfASbnhyyb2PGo2bTe4SzJNHfQotE6N89seREnwOx4XlT88DLWVvKGEQw/?imgmax=800 "RGui (32-bit)_2012-09-26_12-33-20")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi98B_DrP_T5k0NnNHDLJq7C2YMqJGQfF5AuR2TilBc5CAw6MhC7VO7aF7TkOlrdb3VoZxyaESQDzes0DTllQy9sWTXP-mYmLbpHl85ONstlY3lPN_Pqi6QQhQXUTjZdXvPg0R0SW2d2g/s1600-h/RGui%252520%25252832-bit%252529_2012-09-26_12-33-20%25255B3%25255D.jpg)  

**Matrices**
------------

Matrices are vectors with a dimension attribute. The dimension attribute itself is an integer vector of length 2 (nrow, ncol)  
[![RGui (32-bit)_2012-09-26_12-43-32](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhZWaIjy8QsFY3QvIPstcezLwkeENmaimdhnw58Mtw4YihyphenhyphenvtD68c-cZ5MbODPetgt70Wc65ojLMCjwB8o7hVH1gBcTkXLEcnQvVL_3Ju-l3kc4C2SeS2vM99pBMMS4bd-Ac6xovrjckg/?imgmax=800 "RGui (32-bit)_2012-09-26_12-43-32")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhiypwBAaY0NuVH6JAQeA86N30YNpRfKl4L196diFwX1GbzsekqQPahZDHtqQy_lHfgA4J_FW5xIS3PKXKS-W2KvaGbf3TWrojyZBOdn6rKLq6H-4Ij9ZfSuwBT8mO3qBnJPkCr0UjkUA/s1600-h/RGui%252520%25252832-bit%252529_2012-09-26_12-43-32%25255B3%25255D.jpg)  
Matrices are constructed column-wise, so entries can be thought of starting in the upper left corner and running down the columns.  
[![RGui (32-bit)_2012-09-26_13-36-35](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjiH_QMj0naYwQn3nK2w4JKYdjvGatk66OOSyk-2HwF_Hi0LsX4bz5gYR90jbOaObeNGdsNATCwm9N4U9Lgu6iO-0PiSH-g9W6anN9_Xd79T75yT9AL9TsUSgaSYID-DHJIQom4Kkxs3A/?imgmax=800 "RGui (32-bit)_2012-09-26_13-36-35")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiBYBOvx0MEtiZ7QjHRlAd8m_c0eX_Vo4whNdKb_eWsye3cYu-NoKZnF2UXCO1d_3si2XOQUA4xmAZ_hPpIATwZzM_B7kj7jpKS5BBz1nA6tBkvI_D23sYsFK71w0zvEM8SBnr52ZaZxA/s1600-h/RGui%252520%25252832-bit%252529_2012-09-26_13-36-35%25255B3%25255D.jpg)  
based on the above fact, matrices can be created directly from vectors by adding a dimension attribute to a vector  
[![RGui (32-bit)_2012-09-30_18-58-01](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjEAXvhaj7uAvw7mZXfE7WV_SWT66tPj8fegYTSWbeOLhOFaO1Oq-zcxdL3lu1N4t4EWGtCTO7NEOTQpFqTlxg1SbiTBe4vrL5xN1uTSEAxHbmAftEBPGVjK_mKPBk9YokF4RaX17_NjA/?imgmax=800 "RGui (32-bit)_2012-09-30_18-58-01")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh3EjK2CFwG8o1Vv7fdu720x7gEIszXyhRpZatiC-qqNRbgP98Edd5_V3qjIUUT9LAa0aoj4Wop8FN-THKaUcHEKyWEiThIaSQdbOePtWzTFhzIgCBTo81z-NZIGFrh6dZoK2PfmgStgg/s1600-h/RGui32bit_20120930_1858013.jpg)  
Matrices can be created by column-binding cbind() or row-binding rbind(). the example explains it all  
[![RGui (32-bit)_2012-09-30_19-02-57](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiHI1qO5jKOmZ1F_PcGYfgPHgIZjsBNEtF6Fgptxmwc0c3XPQ020vmh-lHSKLXZfd-MiUwmV-HkHlYE1IrLq5K-urSMbeV6LYifPpt-T0S4rN_YlCadx_WCYpM7c6OJfmx-eP6-rFrLLw/?imgmax=800 "RGui (32-bit)_2012-09-30_19-02-57")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjzfO9bb39-69pcKzR3_UZSRfrsiu2pHKvtMkmy1-Pf-vPqNWTCxKAsuhNfAy5_ijwj_ZkIKkBFEQoQssm30uYMCIj3_E25KedY0l1Z6oT7V8ZWnGZkcRlJ-MYVFg4oJTzpvgNfAEDElw/s1600-h/RGui32bit_20120930_1902573.jpg)  

**Lists**
---------

Lists are a special type of vector that can contain elements of different classes (notice that its printing is different)  
[![RGui (32-bit)_2012-10-01_07-05-02](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiSMwLedIwTx3kEq8IiELvl-dDoyNMgOG8C7gfqdqhf2KI3lYAFo5Z_cVV78XlchKYw9VIL84IkuhUjHXRzr6kWU3Yc1p1U-9O3L6tSp6b3QDyMaiW-Cw_dxSjHWBUcMGHWVNuiAHyG6A/?imgmax=800 "RGui (32-bit)_2012-10-01_07-05-02")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhQyCS78lIVknArFcZBfqLHNMmallL1VJcxELZkcVePS9u6woDgWQT13GbWlfGutuH-uw3XqgeJ7bUWFwIFkfc7zMw3NHnl7EnxvTqgNyjvWQPSQhK7ycp4v9JNN_MtRuKtXxuaYQ5fgw/s1600-h/RGui%252520%25252832-bit%252529_2012-10-01_07-05-02%25255B3%25255D.jpg)  

**Factors**
-----------

Factors are used to represent categorical data. Factors can be unordered or ordered. Its like an integer vector where each integer has a label, so you create a vector of any type that is treated internally by integers. The following example creates a factor from a vector of strings. When it prints, it prints the values and it has an attribute Levels that represents  
[![RGui (32-bit)_2012-10-01_07-24-52](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgAhFD1IarFmfruv0yFSdeiSVNqzo_sJ-7t8IwfYYHlHWlzaG5_5un_4mD6m1Mdq0MNUC6LYG_enKP-WqlT9vh8XKIjsDfNWaOFyvd4NZ1v3XeO6u7MH-inJfEYzNkoKMUtdWZ9XFeLOQ/?imgmax=800 "RGui (32-bit)_2012-10-01_07-24-52")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhiz0Anjzui_xceVqXzHMbyiZlTKDBZtvxg2bOEdSn8XUC8WBncHfJ5vjKPJQIKmDGwDuFt_QUirNEuihg8ilDtVynzZnfmYrarsWHnygxOB9H3nfYYhJ30RokCOofIGZsJ02sKsMVP9w/s1600-h/RGui%252520%25252832-bit%252529_2012-10-01_07-24-52%25255B3%25255D.jpg)