---
title: 'Python Notes – 1 : Setup'
date: 2009-03-18T08:55:00.000-05:00
draft: false
url: /2009/03/python-notes-1.html
tags: 
- Python
---

I write this notes about Python during my learning process of it. I'm not an expert in Python. I'm just writing this notes while I learn Python aiming to help others who are learning it too. Never hesitate to comment on anything you want.

#### Origins of Python

*   Developed by Guido van Rossum.
*   Derived from ABC, a teaching language that was developed in 1980s.

#### Why Pyhton ?

*   Python code is pretty simple, compact and easy to learn.
*   Code simplicity let you focus on the core program functionality.
*   Suitable for programming languages introductory courses.
*   Provides a balance between the practical and the conceptual. You start writing after the first tutorial; and if you want to go further in advanced topics you will find a large library of modules that can be used to do all sorts of tasks ranging from web-programming to graphics.
*   Python borrows features from both functional programming languages and object-oriented programming languages, which enables it to serve as an excellent foundation for introducing important computer science concepts.
*   Python allow you to see higher level of success and a lower level of frustration :)

#### How to setup Python ?

Python is free downloadable from many source, and it have also many IDEs and editors. Aiming to start coding quickly without wasting time in IDE exploration, setup, configuration problems; we will use just the [ActivePython.](http://downloads.activestate.com/ActivePython/windows/2.6/ActivePython-2.6.1.1-win32-x86.msi) Let's see how to do that:

1.  Download [ActivePython](http://downloads.activestate.com/ActivePython/windows/2.6/ActivePython-2.6.1.1-win32-x86.msi), it is free.
2.  After you install ActivePython you will got that the following change in your start menu. We will not use Python Intercative Shell nor PythonWin Editor in our first steps, we will use them in upcoming notes.

>       [![clip_image001](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgNkbS_-8qfuqJBpm0DZZ9_aYzjwkhxDXMqwGhJlBHKEV8MRdrPc2hVj5GwB7QKlq5ScVe5y4SrATgC186oPzQA29xxfc9FHJLiFZnK9iHOVVshK-1YAtmX-Jp3KFlbBvcVOOQQxEgF2A/?imgmax=800 "clip_image001")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgamaZCVDHO6BeSNEVpTgHMXerF44kHlrn_tt4O2D3QKgxN7Hr673hyphenhyphenCogzgGMxAPn0veX8wTQNMZbtstQpzwDB4oQMnx1aPWdiB5a2g1WHr9M6csuWWVaYt1XOt9Y7gSS_OStJbObP3w/s1600-h/clip_image001%5B3%5D.jpg)

1.  In our first note we will use Python from the Windows Command window. To do that we need to add the Python installation path to the Environment Variables of the operating system.
2.  If you are using Windows XP or Windows 2000 do the following (if you are using Windows Vista go for step 5):
    1.  Right-click My Computer and select Properties from the displayed context menu. You will got the System Properties dialog

>       [![clip_image002](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi04D_Jwf25wZ6tvbS2XOHw4w7KkmMySqiSUq4qhXVsdc9oknFTp5PXXJdUF1RLPEVddco0CrBob2Et-J5K8Ah9SZf8dPrQBde6ztjEfeKOn6Do6rID8VYcrt3gvNe9hM85OBYQT6MhQA/?imgmax=800 "clip_image002")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiKN681mpUlCbOaie1zCs7ESJCyuR-ieobuAzNBanhgoZZz8ewPFPF9Z0jnXheCJNU7iV66lgwyQJLxPo8uI1W8pBIB-5VV49pigNC7AmDg53Qip1FQiNRSr5wmSCKuHV-9lndH-kXbXw/s1600-h/clip_image002%5B3%5D.jpg)

1.  Then click the Advanced Tab

>       [![clip_image003](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEic6dmgayo08_BWCKdPN20zDupZ5zTQ9gJVxN2n1Gf-Ul2UdTB4U21e16FQTJ5rGXjS4k91BCwLu0u6WDMLjVZp4nr4fPfRX_Z2mYfOpPyTeq3zajocrh6t3rSWSCN8NvZaWK6qKktR7Q/?imgmax=800 "clip_image003")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgy8Ue4w4N76Khlc7-IZGaPccAWPZY6OL7ULdcSoo3lTXgyDX8jleTfW3jHEbAC90zKdOjqQgK39KwYKO8dME6rgIZeJ7hizZJca0-naNSxgFYYE8FvWkMJz-grZzCAkhYvyY12D1Vrng/s1600-h/clip_image003%5B3%5D.jpg)

1.  Then click the Environment Variables button near the left bottom. You will got the Environment variables dialog

>       [![clip_image004](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiKvf1nARd_kG-QU_ZX4Nprv2QIZTLfjmTsX0tHhpvPgKbpKJpbhRMqNMs7iwt9LY-w59qoBUpEQ2FeoW1UqstWrYZQl_70k0uLvuvkY_LEv5WvOs68MJGuCgDzLBs5Cq0W1gqkGMBgcg/?imgmax=800 "clip_image004")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhaPVdVgadXupYWniSYnFkLyWU7rhmQvSQ1juLXbS4gk6oGG3KAl_C0hodUnt8LqCZsqECTTtaqkHNZ1POutQzvYTeHKOrJ6BhcXvIWBlhdwitSdfJIZfg0_H4TcuKC1GpcgxgWxmgBHQ/s1600-h/clip_image004%5B3%5D.png)

1.  Select the variable path from the second list called System Variables. Then click Edit button, you will got the Edit System Variable dialog box

>       [![clip_image005](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgMdzZhAnX7c8gepbGuDByattsk2GUq33L1qYa3syKgFQ4zrlJRANHALNnLbtKaKjIy5QqJnIJ-ok6mouXL7RjCNZvCHsMPPltbWJUhgIYs86jjxcA1GiS3p0xcrCHhpnvRIeia_SDuBQ/?imgmax=800 "clip_image005")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhF9bZH8bN2oLHUfgfz_ctv-shLCUghqELZ1rEiavKcNN_87R0J3ekxGe51U6EkaSSUvx8dwuFo4Pu3V-3WpOXx6Y4xWahO-M3-1ju2DbcRkim22I0v-Gfgu-OwM7bq7UMU1PuUp842mA/s1600-h/clip_image005%5B4%5D.png)

1.  Append the Python installation path to the string in Variable value textbox. The default installation path for ActivePython in our case is C:\\Python25\\; the semicolon ';' is not part of the path but is mandatory to be added at the end. This semicolon acts as the delimiter that enables the operating system to differentiate between this list of paths.

1.  If you using Windows Vista, do the following (very similar steps):
    1.  Right-click My Computer and select Properties from the displayed context menu. You will got the System Properties dialog

>       [![clip_image006](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgnfBO-ZHLUs0lERTZ0U2RXObqSTSWJWTQsc-KR0mYtJexbTlbruUL_d6Q9ZGkkCMSybguThrveq_-ngSSBZHtVFQifKVWdnjziVepWToBoFhK0SJMeC0VUOiuBuRus5ScAr2DYzYkkBg/?imgmax=800 "clip_image006")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjdYHceihG9rfk9yUsr8up4bvbrKLIEHPLRYiGpC6981bwzlcZ5EPE7FDANNR2kfnaJmpb9ZUmCWvCbOlsEcJjYdxa6NcdGmxe6tTLWB2dUHMZgS-NOdThViKrB6nB6rw1ImUM7kgmwEg/s1600-h/clip_image006%5B3%5D.png)

1.  Then the link Advanced system settings on the left menu, you will got the System Properties dialog box

>       [![clip_image007](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhaOX8DKTWjBmGLTOyHeRUWV_5QBmWdzZnCxpcysshhT714Roo1WitxEjZy0ZSQ3V7xzYx84lvSFo-ub5-ctW_yrrkGlQtvRHuJIGE5VB68j8twRPfIC9w0KEYUUdDLi-76iti4XQwHYg/?imgmax=800 "clip_image007")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiEW1VR-E94hxluwzIQ7uiXQA1AMG3MoTm_c1OmFK4AEe203W3LpO6Yf0QTAcr4wKq1s4redKKU5bGGJEn62lcgU6FDNYx9M7PvXTqcJzzy_odIRpK2Gn8sCFyZUEPce4Ag_7RKBwfX-Q/s1600-h/clip_image007%5B3%5D.png)

1.  Then click the Advanced tab

>       [![clip_image008](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhaa_BHBnAEP6TBa4W3hc5dgej6CtxGI5x8i_mHxGoiy4nh3rZRrtoJxiNC5wWsHNiVkZj4Ty8gZkkcgTAGoAIcQZUAxNXYFaWQbN20DQdtQgyVEqscGEyHXrKGjY6bM9jiiKFcbNcphQ/?imgmax=800 "clip_image008")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhDlvmoeEZCUDaWF8Uu1wodDb26oBKr1NuujkmIlfEcbLtMBNItaf3yYJXFtn4d5xhuAoAayldOim9GAmPnpS5X6AyobEk54z8mthMjXkY5t3bAvN8TExM_fJkiqjIx1TZgXtkjM-ZtCA/s1600-h/clip_image008%5B3%5D.png)

1.  Click the Environment Variables button near the right bottom, you will got Environment Variables dialog box

>       [![clip_image009](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEigKXCPh9N9jgeeeBECh70xJhNoXKpOhS34gFE59TsNEh_mquu1YruIouHjjPJD9nANflMSn58X0sqegIp05SR4VZ9kzxLRs8Cp7f3o-PF6tmhWWl8k-hX0Rg241MfTOJ9DirpCg4GirA/?imgmax=800 "clip_image009")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhAULTz9V6v-mR6Ja0SHU1ziSVDnBPZbXujgUN94EGHD1QAm7vbDpK8SqJ-zDQmrskZa70pO0C6KJYg7D08jmiTa7ef1WFaw2kw88PR7gCtaxfJxsz0GxFYwe9USKmj42Sgv59lgz4iMQ/s1600-h/clip_image009%5B3%5D.png)

1.  Select the variable path from the second list called System Variables. Then click Edit button, you will got the Edit System Variable dialog box

>       [![clip_image005[1]](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjRa4L5wd1N-nT7NDKOD8m3pah2FP6bfnYdkZNCjwIVBqI-5n8A8DX4ewe3UNRrF3FWomZDXjMBDOBS-N7RqTys5jUMV_aRWLQADfHd-EdjDTtKx_qtXHJCTUjzJqm0FHdAVksW9aJ1jQ/?imgmax=800 "clip_image005[1]")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgvtjmn2B8fkPw-SbtvevAAhhABwyYggGGzkV4Fn2Uk_Qv6NAwObZEYNpI3nmDAntLRWgfy9KCXWyc3-b2piIdcx_CKl3haEFxd-fZEqmq5ZY9jbZTGI5WN3o-wL-ybO9kD4A_cy5Y1fQ/s1600-h/clip_image005%5B1%5D%5B2%5D.png)

1.  Append the Python installation path to the string in Variable value textbox. The default installation path for ActivePython in our case is C:\\Python25\\; the semicolon ';' is not part of the path but is mandatory to be added at the end. This semicolon acts as the delimiter that enables the operating system to differentiate between this list of paths.

Now, we have Python installed and configured on our machines.

Let's begin in Python

Python is a high-level programming language. It is interpreted language, which means that its programs are executed by an interpreter rather than a compiler. There are two ways to use the interpreter:

*   Command-line mode where you type your python programs at the command-line and the interpreter prints the result.
    *   Open the windows command window and type python, to invoke the python interpreter.
    *   Type print "Hello world !" and press enter. Guess what, you have wrote your first program in Python :)

>        [![clip_image010](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgO4MJ98FH-pNh_4fNwaqHzmAgEhsqzlp54l68YC2_l-zU-SDWROx6FQ9GmVgl5w71SdVdAdWHjt8s7hosShTnVvO2VkzEKH7jBa1VU3i8da-el-pbanLQzhTrhndFA_FQragKR7_6_4w/?imgmax=800 "clip_image010")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiUManLeLsqVOAGWO-pnFliJmvBp7sOF8aYWyO3u3vrqH03XC0h5RE0B6ZhAoek96dJFLFyZ5qmQ03JNhfpeKbqmUKrAHQhsRlLXpUaiLE9V2bV1d3lToBFRC_Zpk0xZqsDoci1Xznpdg/s1600-h/clip_image010%5B3%5D.png)

*   Script mode where you write your program in a file and use the interpreter to execute the contents of the file. Such a file called script. By convention python files have extension .py.
    *   To try that mode, create a file script1.py in your Python installation folder ( default is : C:\\Python25 ).
    *   In this file write print "Hello world !" , save and close.
    *   Open the windows command window and type python, to invoke the python interpreter.
    *   Type import script1 and press enter. You just ran your first Python program.

>        [![clip_image011](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg_exuB10-ZpYiJ8EEPUZSqCBVESoK5swBcUEGt_t004-W8ZWybN_Xzo15DXmeqWANKZWde0N8BKR5QQl84GXQBBIO29YELVC6k2D_wzG_yjqRoymxvMDAbT-dtF6SSn_Au1C7sOuVlKg/?imgmax=800 "clip_image011")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhELopx2Q0HvzjvZ4nlln-1O7kGwqSL6KYeRo7LPmTtkuYOVoRb-EFOSgc2t0-Xa_dDmg03EvRUsneWJDh-ue_ZUqJD7SKu4iv_meqUXN3A4sc2T9Haa46rZwz14Oth5R7eKEsoJ2SW7Q/s1600-h/clip_image011%5B3%5D.png)
> 
> We will use the script mode in most of our notes.

This is just the beginning of our notes about Python. Now we have Python installed and configured on our machines. We will continue our learning in the upcoming notes.