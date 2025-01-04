--- 
title: "Introduction to R – Importing/Exporting Data to External Files" 
date: '2013-01-09T17:56:00.001-06:00' 
tags: 
    - R Programming Language 
modified_time: '2013-01-10T14:47:42.431-06:00' 
thumbnail: http://lh5.ggpht.com/-mB-tzxUQWOw/UO4DsaENhyI/AAAAAAAAAxI/KEershDVoys/s72-c/ReadingWriting%252520Data%252520Part%2525201%252520%2525281255%252529%252520-%252520Google%252520Chrome\_2013-01-09\_16-40-34\_thumb%25255B2%25255D.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-6282924967467589279
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/01/introduction-to-r-importingexporting.html
---

There are many functions that read/write data in R and export it files

read.table, read.csv for reading tabular data and return it in data
frames from delimited files. read.csv is identical to read.table except
that default separator is coma. There are so many arguments for these
functions, the most commonly used arguments are:

-   file : string –&gt; file name or URL
-   header : logical –&gt; TRUE if the file first line is a header line,
    FALSE if first line is data.
-   sep : string –&gt; represents the data separator
-   quote “ string –&gt; if character values are enclosed in quotes,
    this argument should specify the type of quotes.
-   colClasses : string vector –&gt; represent the data tyoe of each
    column in file.
-   nrows : integer –&gt; the number of rows in file (optional)
-   comment.char : string –&gt; the comment indicator string
-   skip : integer –&gt; number of lines to skip from the file beginning
-   stringsAsFactors : logical –&gt; should character variables be coded
    as factors?

save the following file into your default user directory

[<img src="http://lh5.ggpht.com/-mB-tzxUQWOw/UO4DsaENhyI/AAAAAAAAAxI/KEershDVoys/ReadingWriting%252520Data%252520Part%2525201%252520%2525281255%252529%252520-%252520Google%252520Chrome_2013-01-09_16-40-34_thumb%25255B2%25255D.jpg?imgmax=800" title="ReadingWriting Data Part 1 (1255) - Google Chrome_2013-01-09_16-40-34" width="436" height="215" alt="ReadingWriting Data Part 1 (1255) - Google Chrome_2013-01-09_16-40-34" />](http://lh4.ggpht.com/-XFXKQZoMle8/UO4DsM-tzxI/AAAAAAAAAxA/eBqs0b2HXg0/s1600-h/ReadingWriting%252520Data%252520Part%2525201%252520%2525281255%252529%252520-%252520Google%252520Chrome_2013-01-09_16-40-34%25255B4%25255D.jpg)

now you can load it into R

[<img src="http://lh3.ggpht.com/-rQ4ErZj6IYs/UO4DtefzghI/AAAAAAAAAxY/Y0Yq1tZfBEM/RGui%252520%25252864-bit%252529_2013-01-09_16-39-34_thumb%25255B3%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_16-39-34" width="650" height="151" alt="RGui (64-bit)_2013-01-09_16-39-34" />](http://lh4.ggpht.com/-_--ZXYp7KsU/UO4Ds2jONWI/AAAAAAAAAxQ/0w7OjOfsHJo/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_16-39-34%25255B5%25255D.jpg)

You may process this data and want to save it again in another file. To
save data as text file, use write.table which have many parameters
similar to read.table. There are many wrapper functions that call
write.table with different defaults like write.csv()

[<img src="http://lh4.ggpht.com/-mOi7BRCykfE/UO4DuDC9mBI/AAAAAAAAAxo/R1w-oaNhlHo/RGui%252520%25252864-bit%252529_2013-01-09_17-50-00_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_17-50-00" width="348" height="26" alt="RGui (64-bit)_2013-01-09_17-50-00" />](http://lh5.ggpht.com/-JLb5CQd1RS0/UO4DtjIsMNI/AAAAAAAAAxg/uVfx-j2VKwQ/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_17-50-00%25255B3%25255D.jpg)

readLines and writeLines can be used to read/write certain number of
lines of a text file.

There are more read/write functions that are available in R but we
introduced here only the most commonly used ones.

**Get/Set your working directory**

You may be wondering how R knows the path to data.csv file ? R look for
files in the user working directory for files and this working directory
by default is your documents folder (t hat’s why we save the file in “My
Documents” in the first place"). To know you working directory, use
getwd()

[<img src="http://lh5.ggpht.com/-h7jztPjoE2M/UO8o7Oop5jI/AAAAAAAAA10/trTcytVvkZ8/RGui%252520%25252864-bit%252529_2013-01-10_08-50-40_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-10_08-50-40" width="506" height="35" alt="RGui (64-bit)_2013-01-10_08-50-40" />](http://lh6.ggpht.com/-yB0OfsVt_c4/UO8o6eyZMJI/AAAAAAAAA1s/eAGq8Jn9mSE/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_08-50-40%25255B3%25255D.jpg)

to change your working directory, go to File &gt;&gt; Change dir and
select your new working directory and click Ok.

You can use dir() to list all files in your working directory.

Stay tuned for more R notes.
