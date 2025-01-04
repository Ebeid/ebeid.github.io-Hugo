---
title: 'Introduction to R – Functions'
date: 2013-01-13T14:42:00.000-06:00
draft: false
url: /2013/01/introduction-to-r-functions.html
tags: 
- R Programming Language
---

Functions
---------

Functions are just like what you remember from math class. Most functions are in the following form: _f(argument1, argument2, ...)_ Where f is the name of the function, and argument1, argument2, . . . are the arguments  
to the function. Here are a few examples of built-in functions:  
[![RGui (64-bit)_2013-01-08_16-25-25_thumb[1]](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhHizGchtEVRuwhDuZqfjidr5ONsOrQuuuT4LT3cdFH98BDCJ7-Vd4ytrJdtXQhOzt4okW0NTeemj62gkeKczpVVI89CGZ7XyezMVeT3gwT08qwa_uTFqNWp3pDNNeEpMZsjMtXSgSwMw/?imgmax=800 "RGui (64-bit)_2013-01-08_16-25-25_thumb[1]")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiKwb7Exx_8d3fHHDvcC6c2RTzEPL6p58nvQG7RekPJ5xp18C-XW210dChiRbilT4gmOh29GEyLFlbpa_t2oVtxu7eWxGN92zCjOF45eZdm61_oiyhgPbD91mh-0pwG7ADvFTEyABf9fA/s1600-h/RGui-64-bit_2013-01-08_16-25-25_thum%25255B2%25255D.jpg)  
Note in the last example that if you give the argument in the default order, you can omit the names. Some built-in functions have operator form like the following examples:  
[![RGui (64-bit)_2013-01-08_16-29-23_thumb[3]](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgEOEh2dWXvaiUZ64XcCw23XDWxAPx6-aUEPUvBrR_DeAHlBTYbikz_fiIJsZuVg3cqR3YNv4puPmiiiMeFugRJEda30yo-Iw_2yorjo5_R_Cb9_Ca97kYgdCOfxRup8zuuhwDb2MWZhQ/?imgmax=800 "RGui (64-bit)_2013-01-08_16-29-23_thumb[3]")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhLXUQrB4kYJ2Ckp6YI08Yyt_nikqVpO4g-zSKHBSc_agelcijVxHyw3nmgCRRsbUiv3x19qNJV8lb1xWoi8taq7vFCKXUEJEhWoL1VLYL__z4hgU0HeOBGTxYM8PjScGf56hBURARiXg/s1600-h/RGui-64-bit_2013-01-08_16-29-23_thum%25255B2%25255D.jpg)  
A function in R is just another object that is assigned to a symbol. You can define your own functions in R, assign them a name, and then call them just like the built-in functions. Writing your function code on the R Console is hard, so R provided a simple text editor for that. To write your code go to File >> New Script. This will open the R Editor, enter the following code  
[![RGui (64-bit)_2013-01-10_09-05-56](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj8Er4u5OhSwQxxXrJfv9lSz2LmNFMIPNXxnahaQzInHSwNuLCu0eHVwrHENmYKWEElOabCY03Q2ZkPnlr7Rk4cXdhNiggCxxaLqS8rEAzFTjlenCTz_-C2IDUQ7KvCh8bwjRMxDyiw5g/?imgmax=800 "RGui (64-bit)_2013-01-10_09-05-56")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhqauut5wwS90gOXj3uuRw7Xzmdyr4ejTy8SeT9q5uJfcXYd0R-IHSMmluJr6zHdQGsPWOe0Om0aj4kQmHI04AeT_0XVKsIcujRonKDeAiWVfQ-sgSKTmsO7u_wt5OXArzgyveXw1fhvw/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_09-05-56%25255B3%25255D.jpg)  
  
You could select the code, copy and paste it in R console. Now you can call the function to get its result (note that entering the function name and hitting enter retrieves the function code. This is a useful trick to view function code before using it).  
[![RGui (64-bit)_2013-01-10_10-29-47](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgNbvgq6RRhotMe8Ez1tRjxPlWhNr2Gj8R3G-9Rx_frampI27ZzmeLrvtY1wMRCQsn8-jKOgwyB5-5stKrW4x98Ggfhe0SFQ8AbWBT9ro3dvF3Ur0hEebUSB0zZJQvPlkX49vDXQ0wjbg/?imgmax=800 "RGui (64-bit)_2013-01-10_10-29-47")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgMcQK1qs193sjcwf7beMNcGWjqQEIwhjRc3ER_h8hXb7S_zy0nP1QqdSVSFZgkSs6yhSh5oEQ19HOKf9hmfUdO12IiKqAEtDdSjWjND0NljVMJljivIrtPgJ-wuvnkaXqFIut5z1VSAg/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_10-29-47%25255B3%25255D.jpg)  
Now lets go back to the editor and save the code in our working directory in MyCode.R (.R is the extension for R code files). To load the code in any R code file inside the console for use, use source() and pass the file name for it. Then you can use the code inside that file in the console. Each time you edit that code file, you have to call source() again to load the latest code.  
[![RGui (64-bit)_2013-01-10_10-40-49](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiL17HWTTXC8WiazMUgPkEHdpGK_HobNj2GpZAQZ2LgtgnI17WjktINjRzn814KjiCIstlMSNfArmCIrOY7YTA9VxvaRg3AOInJhW60z3-ShMyKErybFXyWCf0Pv-kA4rlQrjRajMVYyQ/?imgmax=800 "RGui (64-bit)_2013-01-10_10-40-49")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh-xaQGI32FcB9tEwIwEdIx-u-HwNfkV057fNT14cCE3Ei0QmcSHMZOV6qPxddysRMqQUTQgb3U0XOlDEgltDv_wFui2k9lp_9J9FMgm7JKLQgqxN4VVKTzVv0tzkmOGqaSWbf8Zlrf5Q/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_10-40-49%25255B4%25255D.jpg)  

Arguments
---------

A function definition in R includes the arguments’ names (in the previous example we didn’t use any arguments).  
[![RGui (64-bit)_2013-01-10_11-08-31](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiJChIQRZUNBD3Lhx6AjNY41QVJ0lo2Qen_qM4ftrpmeBjv_dSh1T7NaokbmSX-DC2PnYAHa13Cb6-4z8eaaEF9hHEK9VopjmDBaNRsM-9u7gAgVmAJZhpsD8p0-G89VooyFKfWHAGFZQ/?imgmax=800 "RGui (64-bit)_2013-01-10_11-08-31")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjn6MGzU3U07XE0YRV7RknVAPqKkVpXRFFNm2f-wrroBWvZcbN6o9PZD72XPRMlv7GFVSwFAfgivv-6NlvMPbEd10EAjYBqCESXnpamHUyNKgEQLOiZZL0VCx7pd5ARYAWvOjyUzoKLFw/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_11-08-31%25255B3%25255D.jpg)  
Optionally, you can include **default values for arguments**. If you specify a default value for an argument, it will be considered optional (can be omitted from the function call). If you provided a value for an argument with default value, your value will override the default one. Non-optional parameters have to be provided in the function call.  
[![RGui (64-bit)_2013-01-10_11-26-13](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhty9lWmdZzoDm7E16tvvkY1DyDi1f8v_GAK2yx9rlfRWpsC0JupKmbBLr3GHGriqLYb0_2vQe6Xl3su0eV-awfhgjavA1YRDuUCtDilrTZEy8UCbTzfmdvcNr6r6J21tHQ_AxG5VjCXg/?imgmax=800 "RGui (64-bit)_2013-01-10_11-26-13")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjrbmfCcSDTRqbqU-sbhhmVDjNanOVdVR6GGyELplKdqusPe47Fe3FOEd93AMHXKX1V0Xbtp4pkX8AgKQhYfCRI-LCabZ1xsmFLQXuRvhZiVnOKWwTuHBS7sktw_rzKNCif_Cp12uP-ZQ/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_11-26-13%25255B3%25255D.jpg)  
  
If you want to specify a **variable-length argument list**, specify (…) in the arguments to the function. Everything other than the named arguments, will be stored in the ellipsis … .To can then convert the ellipsis to a list to work with it.  
[![RGui (64-bit)_2013-01-10_12-31-13](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi3N4X7s2VW1mjvSSmYeGEkeAwN-zhyphenhyphenVK3EjvON-WVYrzOjVubvRVudlCfZVA3a3OTDJisT3cggQEkpeoArL2gZNdLzf6Zt_HTQAa2nsWq0N7iWzYB7ek3_2ob72MRxaHoonUNmCXT_7g/?imgmax=800 "RGui (64-bit)_2013-01-10_12-31-13")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEguhTq1IvgtNb9b5TQkihLyWgYwpZn2SKLXinr_u83-D8xXGIrEj16v67fcyDrWGCUkT28F_zXOTV09bxL2nzxXNWNrI3QVHTWYowuwUYR3PQQCw6vC7kSAJbM8DsiZIkh5P14ZM4Dxdw/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_12-31-13%25255B3%25255D.jpg)  
You can also refer directly to items within the ellipsis using the variables ..1 for the first item, ..2 for second and so on to ..9. Any argument that appear after the ellipsis in the function call, have to be named explicitly.  
You can get the set of arguments accepted by a function, use the args function. NULL represents the function body.  
[![RGui (64-bit)_2013-01-10_14-30-46](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjWE77LZMo0y5qnh4KKyUIFz4SPUdON_n_npfxFsHQ4Wk55tlOjrf489RfWdCrgDQFXcF-wrRK-OkpucGAUb7QBtoKEkofb2DYos8npX8QJHaUM1uISMmWLqwTn3mQknuvJNvEhf64zdw/?imgmax=800 "RGui (64-bit)_2013-01-10_14-30-46")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjvLz14O8vEdMNul_DTXlN1Qj1GIqjd8ZTaFHzr6yfS-JqAFOwDxL0ay9GfbfoSkKNXs8FdCQStY-sYyqCcKUwYwnsTRhliTom8f4nF5pNHqQEKIg8xU8ZUQ5OKzc79OS-u-d5mHdPt8g/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_14-30-46%25255B5%25255D.jpg)  
You can pass named arguments any ware in the function call by their name. Unnamed arguments have to match the order that they are listed in the function definition. The following lm() function calls are equivalent :  
lm(data = mydata, y ~ x, model = FALSE, 1:100)  
lm(y ~ x, mydata, 1:100, model = FALSE)  
Named argument are helpful if you have a long argument list which you remember it by arguments’ names, not the order.  

Lazy Evaluation
---------------

Arguments to functions are evaluated _lazily,_ so they are evaluated only as needed. The function below never uses the argument b, so calling f(2) will not produce an error because the 2 gets positionally matched to a (the only variable needed).  
[![RGui (64-bit)_2013-01-15_17-07-50](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhLJk8K3vEqMEqpxcHyqw2Rdho8ZCiYl2V9dK39eIvhjQgo_6DJcNdOLPgJ3P2y2vea1xMes_R8BprR0Ij6tLNqD6WCgeG8PJQUxH4cyoDIhxP4UC3Zh3o6RQmbuSgIrD37O7rQrbbNVg/?imgmax=800 "RGui (64-bit)_2013-01-15_17-07-50")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi34QWyfq-NJI-vmXtORRyPTUTw-2XjCpSTcZJyLRJJf8v09Ej4DeYbIo1kZGoNDLSfCJVebU2jW6U0ZfkyZZ2DfpFAIivfc2jUYtzRhyphenhyphenHZxQQbbep4szHy0P1Xxk8YppxO8wURsKvQOA/s1600-h/RGui-64-bit_2013-01-15_17-07-503.jpg)  
even if you will use a missing argument, R will not give an error until the first use of this missing argument. Everything before that will execute normally.  
[![RGui (64-bit)_2013-01-16_07-49-45](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjHWNfkrnpfnzx1YHk1mN_NyE8EYz1IRsYbOJxzazl9AQCrsLS534ksq7ZIUX5FOB0nM_gaVvloJdnXBSH-JIssbZ369ZxKR9ghbF5NvsTAYeSBPtsJSEuLBYKfdR35ofkAb-XBqXOmHQ/?imgmax=800 "RGui (64-bit)_2013-01-16_07-49-45")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgYg6pCsuFha-71UYpegbRlrzxPLgaps0ZtVsFsRfRMckHruPNTVL3g7LVlC7cQw1XRCBV0TBDU5GdvrBFF0SbuSXnLgA_jTQm8I_B9XjXMZNdLptIw2Ic9DNd1_vco0BIO-Ah1ZbJdPQ/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_07-49-45%25255B3%25255D.jpg)  

Return Values
-------------

You can use the return function to specify the value to be returned by the function. Also R will return the last evaluated expression as the result of the function if no return() is found.  
[![RGui (64-bit)_2013-01-10_12-52-41](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjqsb-NsE-ej7UyT4vAbNryj91SeDiHZsurEsuQEhWFOT_AmqtUpK3q0HnbHXBRhxr8-9chNoiRozSx-ikvf_mD91DpAheo_cYmGrmMCjESVgReGY7ClxbKIqlfIyMEX68B-wq-75dbWg/?imgmax=800 "RGui (64-bit)_2013-01-10_12-52-41")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhwy-mMlaAh0Cw0zfeqo7tsTOn6lyBDKUp5zfrLki5ZH6MFkDpNaccbm-eBNTEXcb1_dRJGP3m3IkTjXsNddtz_xQkJHYDmaZqTErf9GjwW5ws76-OSIQWr4xtbgCTK_SagLop2Fbicyg/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_12-52-41%25255B3%25255D.jpg)  

Functions as Arguments
----------------------

Many functions in R can take other functions as arguments. An example of these functions, the sapply function iterates through each element in a vector, applying another function to each element in the vector and returning the results.  
[![RGui (64-bit)_2013-01-10_13-07-51](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiBwQUVVr9ThBLpiQcNIKcGi4FpcjT8DK5i0cKZhLGAwZ0YNHDlbcZ8ToCHM9Y8A4opqKmwQtrv-BAcgUsMiP1luiZtd-RBiiLOnpY0FG6D3h5eUnIxO5wNOV5pbBEMCmTWyfagzUKAOA/?imgmax=800 "RGui (64-bit)_2013-01-10_13-07-51")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj-oxIKW6lRG06Z9mIplolJq2tow3uc2-0kL4D-VgVzkNOG4I5GJg8LP9mINBZk6OnpaYSR0GlKpmPZDoFnU8dNBaYmlFGPIk8ayDyOqctppOh81afaLpWgw13bcjoBCY6lJlwvjuORgw/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_13-07-51%25255B5%25255D.jpg)  

Anonymous Functions
-------------------

You create functions that do not have names. These are called anonymous functions. Anonymous functions are usually passed as arguments to other functions.  
[![RGui (64-bit)_2013-01-10_13-32-56](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhDm9cPqwtz-Xx02olEg6HiA_SMtJfvUTWhm1Pfdh0MZd46rBtXcjXvDfYUsLx5OSwoBy_kbxwnjd7QKZf2VajTGqqqy0ZMZ_q8TznyT1LWuk4R4-Xe-WSIPot8eS7rMIf3xCbhit_mZw/?imgmax=800 "RGui (64-bit)_2013-01-10_13-32-56")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiDsr5oOybyw7RoUYbMi_MZ7TyK_vV-28ogdjofNg_Blh81jnAZACtq7WpxXBo6uwmNIzgT7NTzKSugJJaZeXK7O-ERclZdxTBvC33JrGMjJbocGjPa50TSL-3j94u3GCz-9oiHTJaWkQ/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_13-32-56%25255B4%25255D.jpg)  
the R interpreter assigns the anonymous function _functions(x) {x \* 7}_ to the argument _f_ of function _apply.to.three_ then assigns 3 to the argument x of the anonymous function. So, it will ends up by evaluating 3 \* 7 and returns the result.  
anonymous functions can also be used with sapply()  
[![RGui (64-bit)_2013-01-10_13-43-09](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEigKEFVXSRtXFAlNK_oM5Oat97K8ALDFwqdTaWPe7K3OB4r23EDfRqweytjIyN9TIX4klh0KMBC5kkaN4D9V6RzBqwIg5zXzFdSKeUcAz3FgPzG_k5U-Pbi4OiAEMjW4VJo5pbeL_eepA/?imgmax=800 "RGui (64-bit)_2013-01-10_13-43-09")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh0Es2p5pwbMypxQFDQfiw6XIEJVWnPyK6nt26t_SqLoKj1aVX8Gxwjdgpbna2LJjEEP51FP13Wiq7CTjFiN0n8zJ_RpSxcYxmy4ZQCWMnDZY4yd3H0C5szDIuhPSyrz9flzOw7B3Qjgg/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_13-43-09%25255B3%25255D.jpg)  
it is possible also to define an anonymous function and apply it directly to an argument.  
[![RGui (64-bit)_2013-01-10_13-45-53](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhKXv1J1osikpy9PNujxsIHvKxuS3WtHKl1upvEfNVvOJM2-j2edWX4znOGPqjIXkjeP-yLTBDCgT-EH31ciWSKOnS9Wagxas-kqnSILGv02HyQf26oa-OWyG64p9TAan9X93SPM7ABlA/?imgmax=800 "RGui (64-bit)_2013-01-10_13-45-53")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgcNpgYIIEmX9FEW_caTs6vByWBJaQVwEMXZuFfK_4aXhthQTuCVVwKuTm6Ou08NKMYNjYCRSIAVplytbpQF1rDXqAkchnyHIFhRgvL2CQb2Ott-8kkCuWI7ODzavJ9C7HTmBIocdPTzw/s1600-h/RGui%252520%25252864-bit%252529_2013-01-10_13-45-53%25255B3%25255D.jpg)  

Scoping rules
-------------

How does R know which value to assign to which symbol ? How does R know what value to assign to the symbol lm ? Why doesn’t it give it the value of lm that is in the stats package ?  
[![RGui (64-bit)_2013-01-16_09-13-32](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhDCzG1qd7AYMP0UdxQLuI51TEskzVsNObP4gfMDNRZUdQqPPGcVkzutCuDBh-A3k1Iw8LeE61aqFoOJr3mtLVdHrkHu-NhrkoI5jeqPkuZeQP85c7DHTba3KeaaL7_HFaTwIZLDFQHmw/?imgmax=800 "RGui (64-bit)_2013-01-16_09-13-32")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjcA2V17KRASmkaZ6etd1NXkZhPh79j_EXOPBa_o48p6DHPXZ_ZKvB-0yvXPhdZkc290ngkPVoTXUVE0JODEt5f6qllNtVXq-8BYzWq-4xiU2Zp9Ex-1JNMjnaEOqKlS5cxqYe4l6aQQg/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_09-13-32%25255B3%25255D.jpg)  
When R tries to bind a value to a symbol, it searches through a series of environments (sets of symbols, objects,…) to find the appropriate value. When you are working on the command line and need to retrieve the value of an R object, the search begins with the global environment you working in it and look for a symbol name matching the one requested. If not found, R starts searching the namespaces of each of the packages on the search list. You can get the search list using search() function. ._GlobalEnv_ represents your current working environment on the R command line, and its always the first element of the search list. The _base_ package is always the last one. The order on the list matters  
[![RGui (64-bit)_2013-01-16_09-25-18](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiY93lRX2NPuITsDcW9hOwPQQdPA16-HQKVQCEZtxlI0qqbZtMRamhFx7M6wJ51IIDyWe6CBqb8_Cfkd2zJRj1pue7bv1oF09YPcbAOoKY6BuTpTL2UInJM0fbttfBdaLBMYsBHMr3sAA/?imgmax=800 "RGui (64-bit)_2013-01-16_09-25-18")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgZz80H1h3SctbHtopGvszYzLeyU4YAqUV0x29Zgz8sm3xviMPk8Zw-i_GQOsq7Bal8hJH3FbRkkRnPq-qxEp9qMK5_XG1jmPOu-LaxGJDtBSXBMVPlPGweIutlwYX3YlDciS_C8weuKA/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_09-25-18%25255B5%25255D.jpg)  
If you loaded a package with library the namespace of that package will be in the 2nd position of the search list, and everything else will be shifted down the list.  
[![RGui (64-bit)_2013-01-16_09-34-34](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjM-odcK5v458oREovXxqDLTXWaN1zjI_ttW52mUeZXAkVfafgWsyGLbT6Tue_qv0dih1HXYj4KzFVrMWOrzRUxEEvW0VXxJylwY1mA76JK5OvInY5wttZSu6Vgbl4HawLKpETzOQlq_w/?imgmax=800 "RGui (64-bit)_2013-01-16_09-34-34")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj-ByeHDf37oDIkLxvKJHnzS7Lwi5B5msUsuC2H15n-mnnz982fKWL7Tg2H5Oazn3oNZVgGrRvLeg5cN12H1uOAgdQ1NtHmyrkVkS28bMyDxR-G0ZAGqTU7EHZwdTg33R7zCZBisHdu3g/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_09-34-34%25255B4%25255D.jpg)  
You can also load package on the command line window by going to Packages >> Load package >> then select the desired package and click Ok.  
You can configure which packages to be loaded automatically on startup to be available for you. To do that open C:\\Program Files\\R\\<Your-R-Version>\\etc\\Rprofile.site using Notepad and append the following to the bottom of the file. You can append whatever package you want to the vestor c and it will be loaded for your on startup.  
_local({  
old <- getOption("defaultPackages")  
options(defaultPackages = c(old, "car", "RODBC", "foreign", "DAAG", "MASS",_  
_"lattice ", "latticedl", "sciplot", "tree", "lme4"))  
})_  
**Lexical Scoping Rules (or Static Scoping Rules)**  determines how a value is associated with a free variable in a function. The values of _free variables_ are searched for in the _environments_ in which the function was defined.  
So what is a a free variable ? a free variable is not a formal argument (arguments declared in function signature) nor a local variable that is declared and assigned in the function body. In the following example, x and y are formal arguments. z is a free variable. f <- function(x, y) { x^2 + y / z }  
So what is an environment ? an environment is a collection of (symbol, value) pairs. Every environment has a parent environment, and it is possible for an environment to have multiple children. A function + an environment = a closure or function closure.  
So, searching for the value for a free variable starts in the environment in which the function was defined, if not found, the search continued to the parent environment. The search continues until we hit the top-level environment ( workspace or the namespace of the package). After that the search continues down the search list until we hit the empty environment. If not found, an error is thrown.  
You can get the environment of a function using environment() (for functions coded on the command line, that will be the global environment). You can get the parent of an environment using parent.env() (for functions coded on command line, it will be send item in the search list).  
[![RGui (64-bit)_2013-01-16_10-37-17](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhBHdZeKLv7PfkNGXcR7WKm0xoXmaAdbN1vnxaxtmk4CIpn2yUg5nuboZwSlKDF_2qWYk_6jdf9QvD20oN06eIovNUliGMT8dSdwjXJp8YBMC-pNkmYQhQOrxegF6OxiVSQokrGQIxRIg/?imgmax=800 "RGui (64-bit)_2013-01-16_10-37-17")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiD1JRDVWB_9CwZmpELEAiDvIKm70VgGnr8VlpOoapiOFeH6AOM191zKttD7DxrASPy-gUKhVwBFRog_VKuBCr_9QJ6qGUL1KzrRJF68YVi5B_q6QQtFVBU04IlwN7xNDYU53SF-Ne4ew/s1600-h/RGui%252520%25252864-bit%252529_2013-01-16_10-37-17%25255B5%25255D.jpg)  
**Why does knowing lexical scoping rules matters ?** Typically, a function is defined in the global environment, so that the values of free variables will be found in the user’s workspace (which is the right approach). However, in R you can define functions inside other functions, in this case the environment in which a function is defined is the body of another function.  
In this post we talked about functions and using it weather from the console or from external files, functions as parameters, anonymous functions, and many other low level stuff.  
Stay tuned for more R notes.