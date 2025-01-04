---
title: 'Introduction to R – Removing missing values'
date: 2013-01-11T13:53:00.000-06:00
draft: false
url: /2013/01/introduction-to-r-removing-missing.html
tags: 
- R Programming Language
- Statistics
---

A common task in preparing you data is to remove missing values(NAs). One way to do that is to retrieve a vector of the missing values in your data, and then filter them out from your structure.  
[![RGui (64-bit)_2013-01-09_13-17-45](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgEypioB8HojS51tn4ECVjQdae6zjvY9ep4s-0I80BfKyG2-cjFanL6dv3utFrLNM8FMvYTCplFQMJxrsDJA4nFp3eIjmikBAu4hZwWRvdiWLklnpUB-QOwK6sURsCeLXM9uV-WRSdsMA/?imgmax=800 "RGui (64-bit)_2013-01-09_13-17-45")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh-tkGjyOKy8IvODPxVXCgx5TNO-SuokAhiyMUDhT1gWCzv4YFvf83rZym01gRJj1zd-bAL9DwJz7l74hAFadtc9ikPxewadtfXq3cvgleRr2QvclqGf_8A0UkvuDnvhJ5vULCcHmh0aQ/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_13-17-45%25255B3%25255D.jpg)  
If you want to filter out the missing values from more than one vector , you can use complete.cases() to get the indices that contains good data in both vectors.  
[![RGui (64-bit)_2013-01-09_13-25-29](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgLMSVYPmKOAYae8F2aOcbMb_c9nTnlXVLFuaC03ux-2ZnSoST7bPs52En7I7JTSGoE1RHCzTEF4aWzZj4haroJvwQZUuZuUGE8zi5BFVkNiooMRwwrwrZi2o9A3yywWvTfJnXc94olYg/?imgmax=800 "RGui (64-bit)_2013-01-09_13-25-29")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh-zrVNajt1EerMK_tPQgXhVLZoNkl78-zYyYrtkyWIX0vb52BBbkipVM6vey8xrmDSR1PFX7UBdloX7a7OWXt9L7RkZRsA5DO3Mme-GVaRXZ3mcotoRNOFM0QE9Ldf9z0arAZ38i72Jg/s1600-h/RGui%252520%25252864-bit%252529_2013-01-09_13-25-29%25255B3%25255D.jpg)  
Here good will contain TRUE only for indices that hold good data in both vectors; FALSE otherwise. complete.cases() works with data frames also. In that case it removes any row that contains NA in any column.The returned data frame will not contain any NAs.  
Stay tuned for more R notes.