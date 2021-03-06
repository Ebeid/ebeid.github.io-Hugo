--- 
title: "Introduction to R – Removing missing values" 
date: '2013-01-11T13:53:00.000-06:00' 
tags: 
    - R Programming Language 
    - Statistics 
modified_time: '2013-03-28T09:46:09.613-05:00' 
thumbnail: http://lh6.ggpht.com/-zC51Rgf93Bw/UO3Kpf93nMI/AAAAAAAAAvw/eqBr3oH87dM/s72-c/RGui%252520%25252864-bit%252529\_2013-01-09\_13-17-45\_thumb%25255B1%25255D.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-4905056413028467134
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/01/introduction-to-r-removing-missing.html
--- 
A common task in preparing you data is to remove missing
values(NAs). One way to do that is to retrieve a vector of the missing
values in your data, and then filter them out from your structure.  
[<img src="http://lh6.ggpht.com/-zC51Rgf93Bw/UO3Kpf93nMI/AAAAAAAAAvw/eqBr3oH87dM/RGui%252520%25252864-bit%252529_2013-01-09_13-17-45_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_13-17-45" width="368" height="110" alt="RGui (64-bit)_2013-01-09_13-17-45" />](http://lh4.ggpht.com/-fqvd8zYqRaM/UO3Ko7OHciI/AAAAAAAAAvo/2LmL5CKpUyU/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_13-17-45%25255B3%25255D.jpg)  
If you want to filter out the missing values from more than one vector ,
you can use complete.cases() to get the indices that contains good data
in both vectors.  
[<img src="http://lh5.ggpht.com/-keVSlp4VWfQ/UO3KqsNRD9I/AAAAAAAAAwA/pdKN83-HCbA/RGui%252520%25252864-bit%252529_2013-01-09_13-25-29_thumb%25255B1%25255D.jpg?imgmax=800" title="RGui (64-bit)_2013-01-09_13-25-29" width="393" height="173" alt="RGui (64-bit)_2013-01-09_13-25-29" />](http://lh3.ggpht.com/-8MfkwQHNFGQ/UO3KqEfBS1I/AAAAAAAAAv4/2EMSYTGQsYg/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_13-25-29%25255B3%25255D.jpg)  
Here good will contain TRUE only for indices that hold good data in both
vectors; FALSE otherwise. complete.cases() works with data frames also.
In that case it removes any row that contains NA in any column.The
returned data frame will not contain any NAs.  
Stay tuned for more R notes.
