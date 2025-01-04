---
title: 'Introduction to R – Importing/Exporting Data to External Files'
date: 2013-01-09T17:56:00.001-06:00
draft: false
url: /2013/01/introduction-to-r-importingexporting.html
tags: 
- R Programming Language
---

There are many functions that read/write data in R and export it files

read.table, read.csv for reading tabular data and return it in data frames from delimited files. read.csv is identical to read.table except that default separator is coma. There are so many arguments for these functions, the most commonly used arguments are:

*   file : string –> file name or URL
*   header : logical –> TRUE if the file first line is a header line, FALSE if first line is data.
*   sep : string –> represents the data separator
*   quote “ string –> if character values are enclosed in quotes, this argument should specify the type of quotes.
*   colClasses : string vector –> represent the data tyoe of each column in file.
*   nrows : integer –> the number of rows in file (optional)
*   comment.char : string –> the comment indicator string
*   skip : integer –> number of lines to skip from the file beginning
*   stringsAsFactors : logical –> should character variables be coded as factors?

save the following file into your default user directory

[![ReadingWriting Data Part 1 (1255) - Google Chrome_2013-01-09_16-40-34](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjYfTDPKhqy1nFmpYkvkm2AEHSyGxRKnEhMkb2QPzLQrHwo_q5LdDkLxQiwZZZ49YU9d-AK63xo5TNYytGSvPjykonJeYwFu5CuxpNrtWmTh5cURtb7QZFJZElUSQoX70Ta2JCPFUituA/?imgmax=800 "ReadingWriting Data Part 1 (1255) - Google Chrome_2013-01-09_16-40-34")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgPWLOl22WZ2X5PEh3m4Hsl5Kf9peRe2Ay6khiYx-Kr_RlDoognvhC0WhUYDskF6aZhYcmX2EC88DLWAi092EHnjkQzeqxwjcXNiCzCc_0gneaYJ_AXL7UnxVAgFJsQtH-5h_bMyI-MJA/s1600-h/ReadingWriting%252520Data%252520Part%2525201%252520%2525281255%252529%252520-%252520Google%252520Chrome_2013-01-09_16-40-34%25255B4%25255D.jpg)

now you can load it into R

[![RGui (64-bit)_2013-01-09_16-39-34](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiEh-AiVdl1kAPgT888Ha4p2yzRiEphIL1gC7-oG8YVkYv_kkdHM-bsuyYNF4yq-ocWPteO_1oSk7MeVR0Nu9IV2ItKMqy-r6WZs1P9WLWOHhwHIktnviIhgtMakX3b_L9UEiCsrZXxDg/?imgmax=800 "RGui (64-bit)_2013-01-09_16-39-34")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgI5TaRj1vJVt8kzdc6tL1wnNGkBpq5AZO7YA3RoT5kPp7EFDPlBiM5c8GB9guluomIEQZgLfNeQC6IzsivXYmCE1DYcPlDYK_cwam_2RKat4LEjtd_DWvQk6U38OmTrEiBUkPCbq9NJw/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_16-39-34%25255B5%25255D.jpg)

You may process this data and want to save it again in another file. To save data as text file, use write.table which have many parameters similar to read.table. There are many wrapper functions that call write.table with different defaults like write.csv()

[![RGui (64-bit)_2013-01-09_17-50-00](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiQdVZprLOd5BqQupEl-9p661V5ZEqzrpzg8KMgi2vBwuDb62iShuyPsSaarxRmtXx3K9tFl5sntjPjfH13AgH5Z9FZrmL7gyS4XUgrC5R1_k42Pk24Mt9-BcU-QSC5N2K3c3WMF3SI5Q/?imgmax=800 "RGui (64-bit)_2013-01-09_17-50-00")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhECNyw1R7LfSExuphhsrnec-9A2jTo0fGNsyJ_wqV8P9TM0J_4kxaMQbGnsdsQE9zGI6eJsat4t94MyOCyvILS8QX8wum95xwrcpOq-yR3kIjipIXx46p-4hOGsw2UWpu_RaBd05sOsA/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_17-50-00%25255B3%25255D.jpg)

readLines and writeLines can be used to read/write certain number of lines of a text file.

There are more read/write functions that are available in R but we introduced here only the most commonly used ones.

**Get/Set your working directory**

You may be wondering how R knows the path to data.csv file ? R look for files in the user working directory for files and this working directory by default is your documents folder (that’s why we save the file in “My Documents” in the first place"). To know you working directory, use getwd()

[![RGui (64-bit)_2013-01-10_08-50-40](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjXZyuDQE140vp-MpLr0suL46dN-6UTjHV-ZVITwV7z_q4u4rGqFYSpS9gd0Q_4n9Dm2x7GPq7qVr0Y_gY5cUIrvscdRnjq_6i1kd48YzQWhLFUHmjS-7YSqfg-fd7sI_4wh75tYGMC-g/?imgmax=800 "RGui (64-bit)_2013-01-10_08-50-40")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiWVqtNOiRgvlrSD1A4IPkjoQJSF_TFqqa3OJQfnaSNoq5OClTVtDjyxe5aNPDa-Fncdeg9kCP1VyGwhpDlxs40c2kfnhyphenhyphenRM1d4geYgUbwDIBOneevkokrNKPpixErq_WviWSS7_V826A/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_08-50-40%25255B3%25255D.jpg)

to change your working directory, go to File >> Change dir and select your new working directory and click Ok.

You can use dir() to list all files in your working directory.

Stay tuned for more R notes.