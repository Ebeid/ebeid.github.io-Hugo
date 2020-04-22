--- 
title: "Python Notes – 1 : Setup" 
date: '2009-03-18T08:55:00.000-05:00' 
tags: 
    - Python
modified_time: '2009-05-15T02:35:18.606-05:00' 
thumbnail: http://lh3.ggpht.com/\_R1exOFT\_lVs/ScD9Vw9T7-I/AAAAAAAAAC4/\_fRqstfZRyA/s72-c/clip\_image001\_thumb.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-781831074844537891
blogger_orig_url: http://ebeid-soliman.blogspot.com/2009/03/python-notes-1.html 
---

I write this notes about Python during my learning process of it. I'm
not an expert in Python. I'm just writing this notes while I learn
Python aiming to help others who are learning it too. Never hesitate to
comment on anything you want.

#### Origins of Python

-   Developed by Guido van Rossum.
-   Derived from ABC, a teaching language that was developed in 1980s.

#### Why Pyhton ?

-   Python code is pretty simple, compact and easy to learn.
-   Code simplicity let you focus on the core program functionality.
-   Suitable for programming languages introductory courses.
-   Provides a balance between the practical and the conceptual. You
    start writing after the first tutorial; and if you want to go
    further in advanced topics you will find a large library of modules
    that can be used to do all sorts of tasks ranging from
    web-programming to graphics.
-   Python borrows features from both functional programming languages
    and object-oriented programming languages, which enables it to serve
    as an excellent foundation for introducing important computer
    science concepts.
-   Python allow you to see higher level of success and a lower level of
    frustration :)

#### How to setup Python ?

Python is free downloadable from many source, and it have also many IDEs
and editors. Aiming to start coding quickly without wasting time in IDE
exploration, setup, configuration problems; we will use just the
[ActivePython.](http://downloads.activestate.com/ActivePython/windows/2.6/ActivePython-2.6.1.1-win32-x86.msi)
Let's see how to do that:

1.  Download
    [ActivePython](http://downloads.activestate.com/ActivePython/windows/2.6/ActivePython-2.6.1.1-win32-x86.msi),
    it is free.
2.  After you install ActivePython you will got that the following
    change in your start menu. We will not use Python Intercative Shell
    nor PythonWin Editor in our first steps, we will use them in
    upcoming notes.

>      
> [<img src="http://lh3.ggpht.com/_R1exOFT_lVs/ScD9Vw9T7-I/AAAAAAAAAC4/_fRqstfZRyA/clip_image001_thumb.jpg?imgmax=800" title="clip_image001" width="175" height="244" alt="clip_image001" />](http://lh6.ggpht.com/_R1exOFT_lVs/ScD9VAXJfaI/AAAAAAAAAC0/929cCy3b8-I/s1600-h/clip_image001%5B3%5D.jpg)

1.  In our first note we will use Python from the Windows Command
    window. To do that we need to add the Python installation path to
    the Environment Variables of the operating system.
2.  If you are using Windows XP or Windows 2000 do the following (if you
    are using Windows Vista go for step 5):
    1.  Right-click My Computer and select Properties from the displayed
        context menu. You will got the System Properties dialog

>      
> [<img src="http://lh5.ggpht.com/_R1exOFT_lVs/ScD9XH6gEOI/AAAAAAAAADA/zkTM51JbpGw/clip_image002_thumb.jpg?imgmax=800" title="clip_image002" width="211" height="244" alt="clip_image002" />](http://lh5.ggpht.com/_R1exOFT_lVs/ScD9WV9DArI/AAAAAAAAAC8/Sm-__aoNTLw/s1600-h/clip_image002%5B3%5D.jpg)

1.  Then click the Advanced Tab

>      
> [<img src="http://lh5.ggpht.com/_R1exOFT_lVs/ScD9YTCrM0I/AAAAAAAAADI/IYpr1-MScgI/clip_image003_thumb.jpg?imgmax=800" title="clip_image003" width="211" height="244" alt="clip_image003" />](http://lh6.ggpht.com/_R1exOFT_lVs/ScD9Xt2nsFI/AAAAAAAAADE/XlkStz3LP_A/s1600-h/clip_image003%5B3%5D.jpg)

1.  Then click the Environment Variables button near the left bottom.
    You will got the Environment variables dialog

>      
> [<img src="http://lh3.ggpht.com/_R1exOFT_lVs/ScD9ZrXEv_I/AAAAAAAAADQ/wBpuEuAai-8/clip_image004_thumb.png?imgmax=800" title="clip_image004" width="222" height="244" alt="clip_image004" />](http://lh3.ggpht.com/_R1exOFT_lVs/ScD9Y6cv3nI/AAAAAAAAADM/gW15fqj4BqQ/s1600-h/clip_image004%5B3%5D.png)

1.  Select the variable path from the second list called System
    Variables. Then click Edit button, you will got the Edit System
    Variable dialog box

>      
> [<img src="http://lh6.ggpht.com/_R1exOFT_lVs/ScD9asMnM6I/AAAAAAAAADY/VWdFfMxV29w/clip_image005_thumb.png?imgmax=800" title="clip_image005" width="244" height="105" alt="clip_image005" />](http://lh3.ggpht.com/_R1exOFT_lVs/ScD9aCyiYkI/AAAAAAAAADU/zR-KpQCMkYM/s1600-h/clip_image005%5B4%5D.png)

1.  Append the Python installation path to the string in Variable value
    textbox. The default installation path for ActivePython in our case
    is C:\\Python25\\; the semicolon ';' is not part of the path but is
    mandatory to be added at the end. This semicolon acts as the
    delimiter that enables the operating system to differentiate between
    this list of paths.

<!-- -->

1.  If you using Windows Vista, do the following (very similar steps):
    1.  Right-click My Computer and select Properties from the displayed
        context menu. You will got the System Properties dialog

>      
> [<img src="http://lh5.ggpht.com/_R1exOFT_lVs/ScD9cOyccCI/AAAAAAAAADg/oOIaeK8YNH8/clip_image006_thumb.png?imgmax=800" title="clip_image006" width="244" height="184" alt="clip_image006" />](http://lh6.ggpht.com/_R1exOFT_lVs/ScD9bZpQofI/AAAAAAAAADc/GvOlMrvArm8/s1600-h/clip_image006%5B3%5D.png)

1.  Then the link Advanced system settings on the left menu, you will
    got the System Properties dialog box

>      
> [<img src="http://lh3.ggpht.com/_R1exOFT_lVs/ScD9dIM-SkI/AAAAAAAAADo/iCJQkGmQ0MQ/clip_image007_thumb.png?imgmax=800" title="clip_image007" width="219" height="244" alt="clip_image007" />](http://lh6.ggpht.com/_R1exOFT_lVs/ScD9cg9LAAI/AAAAAAAAADk/hcaAdOrZZ7Q/s1600-h/clip_image007%5B3%5D.png)

1.  Then click the Advanced tab

>      
> [<img src="http://lh6.ggpht.com/_R1exOFT_lVs/ScD9eVu0akI/AAAAAAAAADw/yZzpnBC26f0/clip_image008_thumb.png?imgmax=800" title="clip_image008" width="219" height="244" alt="clip_image008" />](http://lh6.ggpht.com/_R1exOFT_lVs/ScD9d-tmasI/AAAAAAAAADs/kIs5CuEPbWo/s1600-h/clip_image008%5B3%5D.png)

1.  Click the Environment Variables button near the right bottom, you
    will got Environment Variables dialog box

>      
> [<img src="http://lh6.ggpht.com/_R1exOFT_lVs/ScD9fcv4cEI/AAAAAAAAAD4/U_2xmhPmKVY/clip_image009_thumb.png?imgmax=800" title="clip_image009" width="223" height="244" alt="clip_image009" />](http://lh3.ggpht.com/_R1exOFT_lVs/ScD9e4nnr5I/AAAAAAAAAD0/lEWSXc508ck/s1600-h/clip_image009%5B3%5D.png)

1.  Select the variable path from the second list called System
    Variables. Then click Edit button, you will got the Edit System
    Variable dialog box

>      
> [<img src="http://lh6.ggpht.com/_R1exOFT_lVs/ScD9hK6lhVI/AAAAAAAAAEA/KwnGheXVQHE/clip_image005%5B1%5D_thumb.png?imgmax=800" title="clip_image005[1]" width="244" height="105" alt="clip_image005[1]" />](http://lh4.ggpht.com/_R1exOFT_lVs/ScD9f_xMybI/AAAAAAAAAD8/DnmAl8msbjM/s1600-h/clip_image005%5B1%5D%5B2%5D.png)

1.  Append the Python installation path to the string in Variable value
    textbox. The default installation path for ActivePython in our case
    is C:\\Python25\\; the semicolon ';' is not part of the path but is
    mandatory to be added at the end. This semicolon acts as the
    delimiter that enables the operating system to differentiate between
    this list of paths.

Now, we have Python installed and configured on our machines.

Let's begin in Python

Python is a high-level programming language. It is interpreted language,
which means that its programs are executed by an interpreter rather than
a compiler. There are two ways to use the interpreter:

-   Command-line mode where you type your python programs at the
    command-line and the interpreter prints the result.
    -   Open the windows command window and type python, to invoke the
        python interpreter.
    -   Type print "Hello world !" and press enter. Guess what, you have
        wrote your first program in Python :)

>       
> [<img src="http://lh4.ggpht.com/_R1exOFT_lVs/ScD9iJiDOYI/AAAAAAAAAEI/l7uGTaqDCIY/clip_image010_thumb.png?imgmax=800" title="clip_image010" width="244" height="125" alt="clip_image010" />](http://lh3.ggpht.com/_R1exOFT_lVs/ScD9hh-sYeI/AAAAAAAAAEE/Ccp8n-KzCFc/s1600-h/clip_image010%5B3%5D.png)

-   Script mode where you write your program in a file and use the
    interpreter to execute the contents of the file. Such a file called
    script. By convention python files have extension .py.
    -   To try that mode, create a file script1.py in your Python
        installation folder ( default is : C:\\Python25 ).
    -   In this file write print "Hello world !" , save and close.
    -   Open the windows command window and type python, to invoke the
        python interpreter.
    -   Type import script1 and press enter. You just ran your first
        Python program.

>       
> [<img src="http://lh3.ggpht.com/_R1exOFT_lVs/ScD9jarJnrI/AAAAAAAAAEQ/4liyici08rE/clip_image011_thumb.png?imgmax=800" title="clip_image011" width="244" height="201" alt="clip_image011" />](http://lh6.ggpht.com/_R1exOFT_lVs/ScD9i4P-T8I/AAAAAAAAAEM/hCUBH-W6_4M/s1600-h/clip_image011%5B3%5D.png)
>
> We will use the script mode in most of our notes.

This is just the beginning of our notes about Python. Now we have Python
installed and configured on our machines. We will continue our learning
in the upcoming notes.
