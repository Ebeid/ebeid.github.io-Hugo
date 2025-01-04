--- 
title: "Using Python Scripts with IIS 7" 
date: '2009-08-15T00:31:00.001-05:00' 
tags: 
    - Python 
modified_time: '2009-08-15T00:34:50.715-05:00' 
thumbnail: http://lh4.ggpht.com/\_R1exOFT\_lVs/SoZHuXw03LI/AAAAAAAAAFk/K1DABd0FU6M/s72-c/Screenshot%20Studio%20capture%20%231\_thumb%5B3%5D.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-2403505418848381278
blogger_orig_url: http://ebeid-soliman.blogspot.com/2009/08/using-python-scripts-with-iis-7.html
---

Here are the steps you should make if you want to use python scripts on
IIS 7:

-   Please make sure Python is installed properly or refer to [Python
    Notes – 1 :
    Setup](http://ebeid-soliman.blogspot.com/2009/03/python-notes-1.html)
    for installation steps.
-   Make sure CGI module is installed in IIS 7.

**Control Panel** -&gt; **Programs** -&gt; **Program and Features**
-&gt; **Turn Windows features on and off** -&gt; **Internet Information
Services** -&gt; **World Wide Web Services** -&gt; **Application
Development Features** -&gt; **CGI module** (Ensure that it is
selected).

> [<img src="http://lh4.ggpht.com/_R1exOFT_lVs/SoZHuXw03LI/AAAAAAAAAFk/K1DABd0FU6M/Screenshot%20Studio%20capture%20%231_thumb%5B3%5D.jpg?imgmax=800" title="Screenshot Studio capture #1" width="362" height="425" alt="Screenshot Studio capture #1" />](http://lh5.ggpht.com/_R1exOFT_lVs/SoZHsToFdQI/AAAAAAAAAFg/lNjCD_Z3qnI/s1600-h/Screenshot%20Studio%20capture%20%231%5B5%5D.jpg)

-   Add web application for Python, In IIS Manager, right click
    **Sites** –&gt; **Add Web Site..**

> [<img src="http://lh4.ggpht.com/_R1exOFT_lVs/SoZH1C71TqI/AAAAAAAAAE8/pBjhfzy6APw/Screenshot%20Studio%20capture%20%232_thumb%5B1%5D.jpg?imgmax=800" title="Screenshot Studio capture #2" width="242" height="240" alt="Screenshot Studio capture #2" />](http://lh5.ggpht.com/_R1exOFT_lVs/SoZHzBoygmI/AAAAAAAAAE4/Rw7jkbRy-kM/s1600-h/Screenshot%20Studio%20capture%20%232%5B3%5D.jpg)

-   In the **Add Web Site** dialog box, set **Site name** e.g.:
    PythonTest, and make it pointing to some folder like C:\\PythonTest,
    then click **OK**

> [<img src="http://lh6.ggpht.com/_R1exOFT_lVs/SoZH54qE0pI/AAAAAAAAAF4/ms6ART8wQGM/Screenshot%20Studio%20capture%20%234_thumb%5B2%5D.jpg?imgmax=800" title="Screenshot Studio capture #4" width="461" height="446" alt="Screenshot Studio capture #4" />](http://lh6.ggpht.com/_R1exOFT_lVs/SoZH3Cw_GFI/AAAAAAAAAFw/1t7xc7r9ktA/s1600-h/Screenshot%20Studio%20capture%20%234%5B4%5D.jpg)

-   In **Features View**, open **Handler Mappings**

> [<img src="http://lh6.ggpht.com/_R1exOFT_lVs/SoZH-VDW9TI/AAAAAAAAAGI/aRzXPDOXwS8/Screenshot%20Studio%20capture%20%235_thumb%5B4%5D.jpg?imgmax=800" title="Screenshot Studio capture #5" width="563" height="381" alt="Screenshot Studio capture #5" />](http://lh6.ggpht.com/_R1exOFT_lVs/SoZH7iHBHQI/AAAAAAAAAGA/cbowuq2B8bg/s1600-h/Screenshot%20Studio%20capture%20%235%5B6%5D.jpg)

-   On the left pane click **Add Script Map ...**

> [<img src="http://lh4.ggpht.com/_R1exOFT_lVs/SoZIC_AiACI/AAAAAAAAAGU/CPKVDH-QLRs/Screenshot%20Studio%20capture%20%237_thumb%5B2%5D.jpg?imgmax=800" title="Screenshot Studio capture #7" width="295" height="237" alt="Screenshot Studio capture #7" />](http://lh5.ggpht.com/_R1exOFT_lVs/SoZIArQsLjI/AAAAAAAAAGQ/E5u9nOTSKqA/s1600-h/Screenshot%20Studio%20capture%20%237%5B4%5D.jpg)

-   In **Request** path, put "\*.py" as the script files extension, In
    **Executable** select &qu ot;C:\\Python25\\Python.exe %s %s", or
    change it according to your Python installation path. (The two "%s"
    after the executable are required for console-based script
    interpreters but would not be required for an Internet Server API
    \[ISAPI\]-based script interpreter). Then give the script mapping an
    appropriate Name, like Python. Click **OK**.

> [<img src="http://lh3.ggpht.com/_R1exOFT_lVs/SoZIFyPZSVI/AAAAAAAAAFc/qzJr3U5nlJY/Screenshot%20Studio%20capture%20%238_thumb%5B1%5D.jpg?imgmax=800" title="Screenshot Studio capture #8" width="452" height="369" alt="Screenshot Studio capture #8" />](http://lh5.ggpht.com/_R1exOFT_lVs/SoZIEUnp4NI/AAAAAAAAAFY/Ua1obD_qe24/s1600-h/Screenshot%20Studio%20capture%20%238%5B3%5D.jpg)

-   Create a test.py into the virtual directory (C:\\PythonTest), and
    copy the following script into it.

> print
>
> print 'Status: 200 OK'
>
> print 'Content-type: text/html'
>
> print
>
> print '&lt;HTML&gt;&lt;HEAD&gt;&lt;TITLE&gt;Python Sample
> CGI&lt;/TITLE&gt;&lt;/HEAD&gt;' print '&lt;BODY&gt;'
>
> print '&lt;H1&gt;This is a header&lt;/H1&gt;'
>
> print '&lt;p&gt;' \#this is a comment
>
> print 'See this is just like most other HTML'
>
> print '&lt;br&gt;'
>
> print '&lt;/BODY&gt;'

-   Then type <http://localhost/pythontest/test.py> into your IE URL bar
    to verify it is working.
