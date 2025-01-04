---
title: 'Using Python Scripts with IIS 7'
date: 2009-08-15T00:31:00.001-05:00
draft: false
url: /2009/08/using-python-scripts-with-iis-7.html
tags: 
- Python
---

Here are the steps you should make if you want to use python scripts on IIS 7:

*   Please make sure Python is installed properly or refer to [Python Notes – 1 : Setup](http://ebeid-soliman.blogspot.com/2009/03/python-notes-1.html) for installation steps.
*   Make sure CGI module is installed in IIS 7.

**Control Panel** -> **Programs** -> **Program and Features** -> **Turn Windows features on and off** -> **Internet Information Services** -> **World Wide Web Services** -> **Application Development Features** -> **CGI module** (Ensure that it is selected).

> [![Screenshot Studio capture #1](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi3JxRV9aVOUWwU1omfWRRb1Wo3MWbN2H4JdKVWcBHtkVTJ-_8_QeexlgIlOf2PFy19b7eEcp7dfbz8JCS5MDybqhotYScRdiomde5Kc-BnXw9jHqDVo5Q3RHeoVfRKdqNygRdl38F4_A/?imgmax=800 "Screenshot Studio capture #1")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEijr1f2eyY2xyM5nk6LEWYQlT7mWtAjpE0AYhZxSBjHlms8lZ-vLhc1cGr45_MM0oO4zpQ_X9j6MQfLh9KSepusCWC2-fM1gB5TKDl6Updr3X45SGw9VgSqv-qSH4FjngVEAFu36m1k9A/s1600-h/Screenshot%20Studio%20capture%20%231%5B5%5D.jpg)

*   Add web application for Python, In IIS Manager, right click **Sites** –> **Add Web Site..**

> [![Screenshot Studio capture #2](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjG_CtwrPE7Q5UBxXqcMbMndDzU77mDVwbV-9US28dDFenCe7ZwA3OYddrYElEyavva_KwcCJ7BOnnW7jCliAGZ46h0wk5FmQTAMYkWmtZYWOURV7z0mlwr0UqxBLM6xaoEPN0_U5lfYA/?imgmax=800 "Screenshot Studio capture #2")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEifDMwjT_WQZnbmr5Vmhevv06Xl-16ewTLgdf3DUJ9s3DIGragEKbkwQts8vntBAdV9Cny2Reii_YM3BpaL8MQ16vileHHtWTi4Iy2yNmyv-LDmrNzUwlIvEndHe_bBqsAntV9VWGO4eA/s1600-h/Screenshot%20Studio%20capture%20%232%5B3%5D.jpg)

*   In the **Add Web Site** dialog box, set **Site name** e.g.: PythonTest, and make it pointing to some folder like C:\\PythonTest, then click **OK**

> [![Screenshot Studio capture #4](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhPgJvTqPYn7v28Zuo5ux2las2CdVKIvbqKtoOeAcU1y0KOOMryU2G-JShgsfoBsLrNeRXkK93IYNn9hLhRe08NOYLL96FFn2hKVAr5QoS6NdNW_SB0SrdwKhGTHaVpPyqRE4EUd-ThxQ/?imgmax=800 "Screenshot Studio capture #4")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiCiSFMhwuGa0V3AE_RYCKO4a-VB20l3CYznh5IAUeQNFrV9yzWKcbOa2_v6lzehsu1ffxebmvqVkQrUhWEaLjM3LfcuKD2jjoeoCyRfcctNHTP96Q7ijBACwACesiQHrpcZl9beogqEA/s1600-h/Screenshot%20Studio%20capture%20%234%5B4%5D.jpg)

*   In **Features View**, open **Handler Mappings**

> [![Screenshot Studio capture #5](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiYzYpwwR6rnlj6a0isXK4_hW5FswzyEAwzAujCKB_44CXXZj6QqrPzXZBCQqcXQdrlDp3DabGThYtv8OxkaO6EUCkuLr1yvq_e5MOyhZuPWnIEhsYK2AwlkYAEQRUwyHs9hiJ3qSy2tA/?imgmax=800 "Screenshot Studio capture #5")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiLcTAKs2RKcwPtBvmKhHFO8ymWlisPz2egTfp3EZUTlEWQDvAWi1_0uFXeG0ARdejnMIRTMde3XIsJeh3yqDAyb2HrZ37K04GD6W5GCfjrJInlq-HY49pq2JI1_tyYZyVvX4LY5zD1fw/s1600-h/Screenshot%20Studio%20capture%20%235%5B6%5D.jpg)

*   On the left pane click **Add Script Map ...**

> [![Screenshot Studio capture #7](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhgDlwHsByh4GpBiTaSlKoU3WzwQGhXDP2NxblliT66rRnqDL0MkIlQwvllO3jhnux0FEpQqfzDAdbhPkttjLp-ZqNFwQ95CGieF2E4UdcEtkctebgMJrjJTWMUIUZ6S3P5uCvL5x1QTA/?imgmax=800 "Screenshot Studio capture #7")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgFnPrmP4Z3RQmJ0UsfE85rcmO1H4_kOE_Ww2iFhGmScsC_bA-vXdPN7n-4MdnOWQAc-JgNwYlp7SV5C26k_HKqWQObxkcaWtjfMpV7yO6KJguWMTVMRGwjeZ7iPfftBF9KQ7woHGvmrQ/s1600-h/Screenshot%20Studio%20capture%20%237%5B4%5D.jpg)

*   In **Request** path, put "\*.py" as the script files extension, In **Executable** select "C:\\Python25\\Python.exe %s %s", or change it according to your Python installation path. (The two "%s" after the executable are required for console-based script interpreters but would not be required for an Internet Server API \[ISAPI\]-based script interpreter). Then give the script mapping an appropriate Name, like Python. Click **OK**.

> [![Screenshot Studio capture #8](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhZJF8ZQwqzQF0IZ_b1yLPsvFQ8KG_xs_pZpA-uBwq4G8BHQtGuGpHGaSAUYFTNKfPw-kNvcOr7K1bnjaguxwotVa2YDUtSX2yIVy_jZTuSRzEyZrfgOZxfZnBFDxiCx-6Rz_N7q_zavw/?imgmax=800 "Screenshot Studio capture #8")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEikFiEymMep1x8hg2AYkulHtiOhNlT8BhK5T0e5hm_OmVkzg0tR_jnbNwydwLGM3xprrIBlfcn0-f6efCA21CUtZ73_ivw7ibL8fqJlrUqjAl9ln4UpUIqzpL11nuzb-4OT8ZvaURM_1g/s1600-h/Screenshot%20Studio%20capture%20%238%5B3%5D.jpg)

*   Create a test.py into the virtual directory (C:\\PythonTest), and copy the following script into it.

> print
> 
> print 'Status: 200 OK'
> 
> print 'Content-type: text/html'
> 
> print
> 
> print '<HTML><HEAD><TITLE>Python Sample CGI</TITLE></HEAD>' print '<BODY>'
> 
> print '<H1>This is a header</H1>'
> 
> print '<p>' #this is a comment
> 
> print 'See this is just like most other HTML'
> 
> print '<br>'
> 
> print '</BODY>'

*   Then type [http://localhost/pythontest/test.py](http://localhost/pythontest/test.py "http://localhost/pythontest/test.py") into your IE URL bar to verify it is working.