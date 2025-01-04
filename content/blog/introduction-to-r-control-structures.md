---
title: 'Introduction to R – Control Structures'
date: 2013-01-15T16:43:00.001-06:00
draft: false
url: /2013/01/introduction-to-r-control-structures.html
tags: 
- R Programming Language
---

Like every other programing language, R have control structures that allow you control the flow of your code execution.

**If, else** for testing a condition. else section is optional.

[![RGui (64-bit)_2013-01-15_15-43-49](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiosiARflsNiG8yMUC8DVopcx9BCeYxchc1KkCj4yMvlkI3h-bbyxvsEPY_gDbHLj1VcI2ACehUyj72Ru56Qf964Iq9E28qMDqbK_CGDH7XU8jmLY_8rAvFAPelcIFN6PEF6jfbz5J8ow/?imgmax=800 "RGui (64-bit)_2013-01-15_15-43-49")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhnyx3LdN10pybDo3WkOmkO4xy9iGHJGxyktALLRPKtOqBMJYGvnRMkQpkDYBeAHqLdrBQOhAT20cE9Yjgx1XL64bxEQRQhSXiyn8VgPVFIWC9c2U3r9HDgLuCb03btauejZPIo7HFocQ/s1600-h/RGui%252520%25252864-bit%252529_2013-01-15_15-43-49%25255B5%25255D.jpg)

if it’s all about assigning a value to a variable, you can do like this

[![RGui (64-bit)_2013-01-15_15-46-22](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg_EbyBaJIRXKrFpknPI3BE8t-m4ILiD39jOcOdPYi6u5ZIafeO1zh7mUjKBOI9AieO08vg5OTyCbyqTlt5JRDQtA2H6QfXLgkaclniB1zGz4WB3RZuMzz7uTOL_ipQcMghdWe2SwdofA/?imgmax=800 "RGui (64-bit)_2013-01-15_15-46-22")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh_LGjEXwwie9QITS4OAJ49BFhAUfj2_GiMa7rJ06bhIhM2DCRBnfsqKMBQWtRDLrRKGkqbjCLTI7LguKw7GTfDVWeJtQEiK6Q-UUvQdvxajeI6ldxxYvVMaJ7tYkc_BhHeijZXtWkHuQ/s1600-h/RGui%252520%25252864-bit%252529_2013-01-15_15-46-22%25255B4%25255D.jpg)

**for** for executing a loop for a fixed number of times. It takes a variable and assign it successive values from a sequence or vector.

[![RGui (64-bit)_2013-01-15_15-59-06](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiD35pzRTOGmMfh1je2MnF_DxtiJXXmMC1vfLKtuMhbyUvtUjXojkEGjbNg-wAg7zBcY7jWNcbmeKWTEzxGvtMYUWTgbBHEFfYkXI9sbWDmsvA9kxDIFUVxnvAJq_qkAsey2hdLLAoGsQ/?imgmax=800 "RGui (64-bit)_2013-01-15_15-59-06")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiTkUKqJ7S215kUYkRoORSrPvwM6_s5805YCU6u42js4fJMudGYF2tAdn_3hxTJeCda9PXFNpoIWIJ7Qx6rjkutvfzEjsgoz7HAwRrdFQsahDzzA7kK-VGRE12TcL41Yu8t3LKiChEA3g/s1600-h/RGui%252520%25252864-bit%252529_2013-01-15_15-59-06%25255B4%25255D.jpg)

**while** for executing a loop while a condition is true. It begins by testing that condition, if it is true, the loop body will execute, if not, R will skip the loop.

[![RGui (64-bit)_2013-01-15_16-08-36](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhMpJEw7VFnIWr-rp1QEEUnX_KYSZy_6ZfkI5Zhrga1quzF4JDVMog9KgPoonrXQ7-eok7E_UMGc942djCmtHx1ZYpjrGOXtH3Ioh8JkJRTIoScFqKfhpoeH9bYcKIVL4v7HcYZzCqPhg/?imgmax=800 "RGui (64-bit)_2013-01-15_16-08-36")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjX6VNewOgf5duySA6VVx9VisBGoGxeggtXx9f5APWNcU87SMf1PcPkznrKQdPgo73E5lrWbxqopxiFWmks6pXFYAEs_EEBnB1HFl20c3_kJLUPmT85mONlQaA27qa9X8ex7xRDNRJRHg/s1600-h/RGui%252520%25252864-bit%252529_2013-01-15_16-08-36%25255B3%25255D.jpg)

**repeat** for executing an infinite loop; the only way to exit the loop is to call break

[![RGui (64-bit)_2013-01-15_16-12-57](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiAyuUMCs5BMsQt7YCNOk-xcc9JbqQLLzNwPKqLqkvSujCFf4apkbZUXuAYcKp9_4drYZl5Pl2yX3ZSU8T56Gs_EYNMcJQ0xo4tpeRcgII2led5-W25YMTdIUD-pbqzTTKr4LwQ9WJPTQ/?imgmax=800 "RGui (64-bit)_2013-01-15_16-12-57")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhNCcmA8I2Ht6pe3zxAgX5HHqjVerL_fDTm4A3Jkj9LaRafxu0bh1z7_7XdnWVZaL1DFGw_cs7dQrqrIRIaoISKdYojVYIht6QzdWJAG8UxesNMOHjPC6ZEGxq18sJz-_ZwHjBBOzYu2Q/s1600-h/RGui%252520%25252864-bit%252529_2013-01-15_16-12-57%25255B4%25255D.jpg)

**break** for breaking the execution of a loop and continue from the next line of code after the loop (just like in the previous example)

**next** is used to skip an iteration of a loop

[![RGui (64-bit)_2013-01-15_16-35-49](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgrK2ojgE8dX_BcnfxU1v9zIT-XZiqghwqPEuYFuPlpDQFZG8BFIVOfzknUJ5gbfbwYT8L-96TScZO12G6V1S4oSZR0HRJI9ptM8G_INjY7iIG0azoW_4h9qTWDwPsYz1DImCXpInZpEw/?imgmax=800 "RGui (64-bit)_2013-01-15_16-35-49")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhbxJuUHfAdxNUVSAg8rLCyOYDI0xDTsIWpOMG2czTWkEUEStvpOIPyLeCmh7_saQD_uomaJ6HD97j3fMaauWkjQzciR4ZRFk3WBz9OwOyo1X9SlRDla4ZVUKHMAdahwlhWyAAshqJEZg/s1600-h/RGui%252520%25252864-bit%252529_2013-01-15_16-35-49%25255B3%25255D.jpg)

Writing multiple lines of code on the command-line interactive environment is hard. I have used the script editor to write the code in this post and then copied it to R console.

Loop functions
--------------

Loop functions is so similar to loops. It just more compact and easy to use on command line.

**lapply** loop over a list and evaluate a function on each element. If the first argument wasn’t a list, it will be coerced to a list (using as.list). lapply always returns a list. Any arguments passed to lapply beyonf the FUN parameter, will be assigned to the ellipsis and then passed as parameters to FUN. FUN can be an anonymous function.

[![RGui (64-bit)_2013-01-16_12-46-03](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjfM77BrbiGmFKBcsteAxSNtwN8i1w0C6lbzwqhrvC7TZAYpH3bsvYAQ0-26LtqNp2b77Sp2pR2y51K-WfevSYdvfsjEbQSfcCk00sDO47sWDfz5-14kqS3ruyW0wmcrr0T-o190oS9qQ/?imgmax=800 "RGui (64-bit)_2013-01-16_12-46-03")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgE5j8un9zw7kVniKHQWcoBjrQmCd6oeIH41-UiOG00xrOYWK4WAdeQQj5W5kaMytqKaLLgO6fuVhdPdcjd1g52_WkwpGpchBtl8TLL6qgATG4H94QkoUNu9RgPQrDudbf0soBDLPrCfA/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_12-46-03%25255B3%25255D.jpg)

**sapply** will try to simplify the result of lapply if possible. If the result is a list where every element is length 1, then it returns a vector. If the result is a list where every element is a vector of the same length (>1), it returns a matrix. If it can’t figure things out, it returns a list.

[![RGui (64-bit)_2013-01-16_12-59-27](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi4wiZXgatq6ywMO8qm6Kq6mr3S1LiGPalVSxEJ5V_CPVgNOQ6i47JdM1kE2tL5QSK7AV3_HBDcvF5Qz_d_i2co3HOjUKJ1XAAQ5uItH-4Ki0TL5iTUWJly53L9JtsM_wVi62-sxEC26g/?imgmax=800 "RGui (64-bit)_2013-01-16_12-59-27")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjRhu_qTZ2Hs0-YvXAH5x4o3R9a2beF5-vK2tyi9xMqEQ3dOgmBzg8aWkMD-deIyiBPSGUGYSlCWPIgK6c0aPV9AmJ8aUCIDos9uBFDpVY-2x0fhCxulPYt9Gpt_uf_JZmR1wONV34Isw/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_12-59-27%25255B3%25255D.jpg)

**apply** apply a function over the margins of an array. Often used to apply a function to rows and columns of a matrix. It takes as parameters the array; margin which indicates which dimension will be used as parameter to the function applied; and the function to be applied. In the example below, when passing 2 for the margin it means apply the function to columns, so we got a result of vector with length 10 containing the sum of each column. When we passed 1 for the margin, it means apply the function to rows, so we got a result of vector with length 20 containing the sum of each row.

[![RGui (64-bit)_2013-01-16_13-15-23](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjHOg1ZHmpYqZ0oFFKuuoqDETSXs2gesfvz1Xjq7II-626kpwvUq9eIOAz2TqwETTbCnRQB7-Rv0lMkuvU-SCA7eMIHo11O3J2GrcGxGOr6zNnMP4Jcm_Tkxm_bnMWPRrLD8oXWB2Swag/?imgmax=800 "RGui (64-bit)_2013-01-16_13-15-23")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh5aMGmcl7lXkHqa6THW088UhlXTKIWvYgIOy_KHGivKWm9AnHOkGvdriCLqQHA-AHtBT42O38ZPOXRb-t1n9AJFVbHQGQXEwdsemyab6v3pblIsRDkwmQoEsODx3FcdjF7unwBw6qI_Q/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_13-15-23%25255B4%25255D.jpg)

for sums and means of matrix dimensions, we have some shortcuts:

*   rowSums = apply(x, 1, sum)
*   rowMeans = apply(x, 1, mean)
*   colSums = apply(x, 2, sum)
*   colMeans = apply(x, 2, mean)

**tapply** apply a function over subsets of a vector. It is equal to using split and lapply together. **split** take a vector or other objects and splits it into groups determined by a factor or list of factors.

**mapply** is a multivariate version of lapply. Each element will in 1:4 repeated by the corresponding number in 4:1.

[![RGui (64-bit)_2013-01-16_14-14-26](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg5ClneyC4OkXdfJuhxe0xpaGAmvyQsXVomqU9sL4XhMRa72Vtei1fzPfxShP_VsZfuiHJBPicP_5lf7kBvHMaWapq9a3jrbAVqhooil1VA_jEuhnfWrdTUGoHUnhRcjqKoTXCdspCRRw/?imgmax=800 "RGui (64-bit)_2013-01-16_14-14-26")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjvBzEMX4K0dkSPSdZJ3jnqNdyeQtE_Yz3EJj2pFH0xIvKHnpSnQWToeZzj3AjGVVtzF_kVHAcZYGGVJUs-yVzYXZOGSYQJ3nMNVMsCUMDSmw1glBoEQbuVe3RW9aJ_Hi1umMzoB1DRJg/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_14-14-26%25255B4%25255D.jpg)

In this post we introduced the basic control structured in R. Its almost the same in any c-like programming language.

Stay tuned for more R notes.