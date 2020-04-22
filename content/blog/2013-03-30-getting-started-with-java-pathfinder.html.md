--- 
title: "Getting Started with Java PathFinder" 
date: '2013-03-30T19:06:00.001-05:00' 
tags: 
    - JPF 
    - Model Checking
modified_time: '2013-04-25T14:48:20.497-05:00' 
thumbnail: http://lh3.ggpht.com/-J7bjx6wUSgg/UVd9qcW-UkI/AAAAAAAABF0/zvG9Ui8fjMQ/s72-c/2013-03-28%25252013\_54\_12-Java%252520-%252520jpf\_junit\_demo\_src\_TestGenerator.java%252520-%252520Eclipse%252520SDK\_thumb%25255B1%25255D.png?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-7346921535986352379
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/03/getting-started-with-java-pathfinder.html
---

Java™ Pathfinder, or ***"JPF"*** as we call it from here, is a highly
customizable execution environment for verification of Java™ bytecode
programs. **[JPF](http://babelfish.arc.nasa.gov/trac/jpf/)** was
developed at the [NASA Ames Research Center](http://www.arc.nasa.gov),
open sourced in 2005, and is freely available
[here](http://babelfish.arc.nasa.gov/trac/jpf/) under the [NOSA
1.3](http://javapathfinder.sourceforge.net/NOSA-1.3-JPF.txt) license.
**JPF** started as a software model checker but it integrates model
checking, program analysis and testing.

In this post  we will go in a step by step process to setup the 
environment where Java Path Finder can be used within Eclipse IDE
environment. We will show a simple example of using JPF.

Step 1. Install Eclipse

-   Step 1.1 : Download and install the latest JDK fro your platform
    from
    [here](http://www.oracle.com/technetwork/java/javase/downloads/index.html).
-   Step 1.2 : Download the latest Eclipse from
    [here](http://www.eclipse.org/downloads/). Once you have unzipped
    the previously downloaded file, you will see a folder named
    eclipse.  In that folder you will find the eclipse application.  We
    recommend you create a shortcut on the desktop to simplify the
    launching of eclipse.  Notice that unlike Java, Eclipse does not
    have an installation process. Once you have unzipped the file you
    are done.

Step 2. Download JPF

Step 2.1 : Download Mercurial plug-in for Eclipse

-   Launch Eclipse. Go to Help &gt;&gt; Install New Software
-   [<img src="http://lh3.ggpht.com/-J7bjx6wUSgg/UVd9qcW-UkI/AAAAAAAABF0/zvG9Ui8fjMQ/2013-03-28%25252013_54_12-Java%252520-%252520jpf_junit_demo_src_TestGenerator.java%252520-%252520Eclipse%252520SDK_thumb%25255B1%25255D.png?imgmax=800" title="2013-03-28 13_54_12-Java - jpf_junit_demo_src_TestGenerator.java - Eclipse SDK" width="274" height="211" alt="2013-03-28 13_54_12-Java - jpf_junit_demo_src_TestGenerator.java - Eclipse SDK" />](http://lh5.ggpht.com/-HYIUlscDsVA/UVd9pd6k2SI/AAAAAAAABFs/BbvO6YeOdTU/s1600-h/2013-03-28%25252013_54_12-Java%252520-%252520jpf_junit_demo_src_TestGenerator.java%252520-%252520Eclipse%252520SDK%25255B3%25255D.png)
-   Click Add
-   [<img src="http://lh6.ggpht.com/-FLwL5xh438M/UVd9r7QHCkI/AAAAAAAABGE/EDVdhLXUPYQ/2013-03-28%25252014_01_12-Install_thumb.png?imgmax=800" title="2013-03-28 14_01_12-Install" width="244" height="97" alt="2013-03-28 14_01_12-Install" />](http://lh5.ggpht.com/-Wv_H6c2jpCI/UVd9qxOm5tI/AAAAAAAABF8/DHOM1VPKIwk/s1600-h/2013-03-28%25252014_01_12-Install%25255B2%25255D.png)
-   Insert “Mercurial” in the Name box. Insert
    “<http://mercurialeclipse.eclipselabs.org.codespot.com/hg.wiki/update_site/stable/>”
    in the Address box. Click Ok.
-   In the install dialog select the newly added site from Work with
    drop down box. The list below it will show the available software at
    this site, select the item named MercurialEclipse and click Next,
    then finish..
-   [<img src="http://lh5.ggpht.com/-8RAdwDzkaZM/UVd9v2G-AWI/AAAAAAAABGU/kevrmv9Qy%0AeE/2013-03-28%25252014_05_37-Install_thumb.png?imgmax=800" title="2013-03-28 14_05_37-Install" width="244" height="193" alt="2013-03-28 14_05_37-Install" />](http://lh3.ggpht.com/-ALvEbOTkbrc/UVd9trTFDhI/AAAAAAAABGM/PqYSeIqeDYc/s1600-h/2013-03-28%25252014_05_37-Install%25255B2%25255D.png)

Step 2.2 : Download the JPF source code

-   In Eclipse menu : File &gt;&gt; Import &gt;&gt; Mercurial &gt;&gt;
    Clone Existing Mercurial Repository &gt;&gt; Next.
-   [<img src="http://lh4.ggpht.com/-fBQDzRT9eXc/UVd9y1Odn4I/AAAAAAAABGk/ZD5O0AyVMxY/2013-03-28%25252014_42_31-Mercurial%252520clone%252520repository%252520wizard_thumb.png?imgmax=800" title="2013-03-28 14_42_31-Mercurial clone repository wizard" width="244" height="172" alt="2013-03-28 14_42_31-Mercurial clone repository wizard" />](http://lh6.ggpht.com/-qYEeVNtyWVc/UVd9yFOK_MI/AAAAAAAABGc/_V3bbdgi2M4/s1600-h/2013-03-28%25252014_42_31-Mercurial%252520clone%252520repository%252520wizard%25255B2%25255D.png)
-   In the repository location URL, insert
    “<http://babelfish.arc.nasa.gov/hg/jpf/jpf-core>”. Click Next, then
    Finish. The JPF project files will be downloaded to your local
    computer.

Step 2.3 : Build the JPF

In the package explorer, select the build.xml, right click on it, select
“run as” &gt;&gt; “Run as Ant build “.

Eclipse will build JPF and a new folder named “build” will appear in the
package explorer (it may not appear even the build was successful,
double check the windows explorer for it.)

If the build failed due to error missing JDK:

-   On Eclipse menu : Project &gt;&gt; Properties. Select Builders from
    the lift hand side list
-   [<img src="http://lh5.ggpht.com/-B0jDpn4Rxxg/UVeOHFyh4uI/AAAAAAAABHs/O5poj1T8fhI/2013-03-30%25252019_52_18-Java%252520-%252520jpf_junit_demo_test_CalculatorTest.java%252520-%252520Eclipse%252520SDK_thumb.png?imgmax=800" title="2013-03-30 19_52_18-Java - jpf_junit_demo_test_CalculatorTest.java - Eclipse SDK" width="244" height="171" alt="2013-03-30 19_52_18-Java - jpf_junit_demo_test_CalculatorTest.java - Eclipse SDK" />](http://lh3.ggpht.com/-O6sm0jEDP2U/UVeOGdW2oWI/AAAAAAAABHk/Fs1Err8h38M/s1600-h/2013-03-30%25252019_52_18-Java%252520-%252520jpf_junit_demo_test_CalculatorTest.java%252520-%252520Eclipse%252520SDK%25255B2%25255D.png)
-   Select Ant Builder and click New.
-   Select Ant Builder and click New.
-   In the Edit Configuration dialog, select the “JRE” tab, then select
    “Separate JRE” from the “Runtime JRE section”. In the drop down
    list, select JDK:
-   [<img src="http://lh5.ggpht.com/-J5KIv88dIgk/UVeOIOxlGsI/AAAAAAAABH8/xGErREWzrRg/2013-03-30%25252020_01_41-Edit%252520Configuration_thumb.png?imgmax=800" title="2013-03-30 20_01_41-Edit Configuration" width="244" height="76" alt="2013-03-30 20_01_41-Edit Configuration" />](http://lh6.ggpht.com/-swJUlkWwjYg/UVeOHl2Er2I/AAAAAAAABH0/k0F3r4Kz7NA/s1600-h/2013-03-30%25252020_01_41-Edit%252520Configuration%25255B2%25255D.png)
-   If you couldn’t find the JDK in the drop down list, click “Installed
    JRE …”
-   [<img src="http://lh3.ggpht.com/-vqeiwaXKtwI/UVeOLFnPXtI/AAAAAAAABIM/UtcRtTPW1e0/2013-03-30%25252020_05_18-Preferences%252520%252528Filtered%252529_thumb.png?imgmax=800" title="2013-03-30 20_05_18-Preferences (Filtered)" width="244" height="191" alt="2013-03-30 20_05_18-Preferences (Filtered)" />](http://lh4.ggpht.com/-LiaktXhtNMw/UVeOKP4cKII/AAAAAAAABIE/P5qm-GezC6s/s1600-h/2013-03-30%25252020_05_18-Preferences%252520%252528Filtered%252529%25255B2%25255D.png)
-   In the “Preferences” dialog, click “Add”
-   [<img src="http://lh6.ggpht.com/-t37JsQuqask/UVeOOG0WiRI/AAAAAAAABIc/J-ulKLfN5lw/2013-03-30%25252020_07_40-Preferences%252520%252528Filtered%252529_thumb.png?imgmax=800" title="2013-03-30 20_07_40-Preferences (Filtered)" width="237" height="244" alt="2013-03-30 20_07_40-Preferences (Filtered)" />](http://lh5.ggpht.com/-eKXWQowTn8M/UVeOMPK%0AtwkI/AAAAAAAABIU/GiU5g3wEH5A/s1600-h/2013-03-30%25252020_07_40-Preferences%252520%252528Filtered%252529%25255B2%25255D.png)
-   Select “Standard VM” and click “Next”
-   [<img src="http://lh6.ggpht.com/-3wrjN9OT--Q/UVeOQWPN3WI/AAAAAAAABIs/g6vh1nnOOUk/2013-03-30%25252020_10_06-Edit%252520Configuration_thumb.png?imgmax=800" title="2013-03-30 20_10_06-Edit Configuration" width="244" height="239" alt="2013-03-30 20_10_06-Edit Configuration" />](http://lh5.ggpht.com/-J09x3j81-wM/UVeOPc4Y77I/AAAAAAAABIk/eCZYDu5b4GM/s1600-h/2013-03-30%25252020_10_06-Edit%252520Configuration%25255B2%25255D.png)
-   Click “Directory” and navigate to your JDK installation directory.
    Then click “Finish” to return to the previous dialog.
-   [<img src="http://lh3.ggpht.com/-K3pu2R8R4eg/UVeOR_4A0bI/AAAAAAAABI8/OoJLw5sd7ZM/2013-03-30%25252020_11_56-Preferences%252520%252528Filtered%252529_thumb.png?imgmax=800" title="2013-03-30 20_11_56-Preferences (Filtered)" width="244" height="73" alt="2013-03-30 20_11_56-Preferences (Filtered)" />](http://lh3.ggpht.com/-vejQMAEEj30/UVeOQ_D4UOI/AAAAAAAABI0/b_94P5tqtbs/s1600-h/2013-03-30%25252020_11_56-Preferences%252520%252528Filtered%252529%25255B2%25255D.png)  
-   Select the JDK and click Ok.
-   Select JDK in the drop down box and click OK
-   [<img src="http://lh5.ggpht.com/-t4iCBE3DsxA/UVeOTBsNKaI/AAAAAAAABJM/HYcTpyEPss0/2013-03-30%25252020_13_43-Edit%252520Configuration_thumb.png?imgmax=800" title="2013-03-30 20_13_43-Edit Configuration" width="244" height="23" alt="2013-03-30 20_13_43-Edit Configuration" />](http://lh3.ggpht.com/-sSwQsWzybOc/UVeOSSOKmiI/AAAAAAAABJE/bKkeyZsxJCE/s1600-h/2013-03-30%25252020_13_43-Edit%252520Configuration%25255B2%25255D.png)

Step 3 : Install and configure JPF

-   Step 3.1 : Install JPF files : Copy the whole jpf-core project
    folder into &lt;user.home&gt;/projects/jpf
-   Step 3.2 : Create site.properties
    -   Create site.properties under &lt;user.home&gt;/.jpf folder.

    -   To create the folder on windows, use the following command on
        the command window after navigating to the user home: <span
        class="underline">mkdir .jpf</span> .

    -   Paste the following content into the site.properties file.

            # JPF site configuration

            jpf.home = ${user.home}/projects/jpf

            # can only expand system properties
            jpf-core = ${user.home}/projects/jpf/jpf-core

            # annotation properties extension
            jpf-aprop = ${jpf.home}/jpf-aprop
            extensions+=,${jpf-aprop}
            # numeric extension
            jpf-numeric = ${jpf.home}/jpf-numeric
            extensions+=,${jpf-numeric}
            # concurrent extension
            #jpf-concurrent = ${jpf.home}/jpf-concurrent
            #extensions+=,${jpf-concurrent}
            jpf-shell = ${jpf.home}/jpf-shell
            extensions+=,${jpf-shell}
            jpf-awt = ${jpf.home}/jpf-awt
            extensions+=,${jpf-awt}

            jpf-awt-shell = ${jpf.home}/jpf-awt-shell
            extensions+=,${jpf-awt-shell}
-   Step 3.3 : Install Eclipse plug-in
    -   The JPF Eclipse plug-in allows you to invoke JPF directly from
        Eclipse.
    -   In Eclipse go to Help &gt;&gt; Install New Software.
    -   In the new window click Add. In the name insert JPF. In the
        location insert
        “[http://babelfish.arc.nasa.gov/trac/jpf/raw-attachment/wiki/install/eclipse-plugin/update/](http://babelfish.arc.nasa.gov/trac/jpf/raw-attachme%0Ant/wiki/install/eclipse-plugin/update/)”
        then click Ok.
    -   From the “Work with:” drop down menu select the newly added
        site.
    -   In the list, check “Eclipse-JPF”, click Next, then Finish.

Step 4 : Start the demo project

Step 4.1 : Create and configure project

-   In Eclipse menu : File &gt;&gt; New &gt;&gt; Java project : project
    name = jpf\_junit\_demo
-   In the package explorer, right click on the project name. Choose
    “Build Path” &gt;&gt; “Add libraries”
-   [<img src="http://lh5.ggpht.com/-v4wKdLyftlA/UVd91FwFt6I/AAAAAAAABG0/sBCAmrZASCk/2013-03-28%25252015_41_55-Add%252520Library_thumb.png?imgmax=800" title="2013-03-28 15_41_55-Add Library" width="244" height="167" alt="2013-03-28 15_41_55-Add Library" />](http://lh5.ggpht.com/-CSdE3fDs--E/UVd9z0SedPI/AAAAAAAABGs/4NFtDrpspG4/s1600-h/2013-03-28%25252015_41_55-Add%252520Library%25255B2%25255D.png) 
-   Select User Library and click Next.
-   Click User libraries. Then New. You will see a window for creating a
    library. Put “jpf” as the library name and click Ok to return to the
    previous dialog.
-   Select the newly added jpf library and click “Add External JARs …”.
-   Select all the jar files under &lt;user.home&gt;/jpf/jpf-core/build
    and click “Open” to add them under library jpf
-   Click New to create a new user library. Name it “jpf-support”.
-   Select the newly added jpf-support library and click “Add External
    JARs …”.
-   Select all the jar files under &lt;user.home&gt;/jpf/jpf-core/lib
    and click “Open” to add them under library jpf-support
-   Now the User Libraries should look like the following:
-   [<img src="http://lh5.ggpht.com/-ghAxZL9OYnM/UVd93kD3yYI/AAAAAAAABHE/In8cVDIgnpk/2013-03-28%25252015_54_32-Preferences%252520%252528Filtered%252529_thumb.png?imgmax=800" title="2013-03-28 15_54_32-Preferences (Filtered)" width="244" height="160" alt="2013-03-28 15_54_32-Preferences (Filtered)" />](http://lh6.ggpht.com/-zm0xQa0YzKI/UVd92I5WpiI/AAAAAAAABG8/uNSizUroHEY/s1600-h/2013-03-28%25252015_54_32-Preferences%252520%252528Filtered%252529%25255B2%25255D.png) 
-   Right click on the project name and select : New &gt;&gt; Folder,
    name the folder as test. Right click on the newly created test
    folder and select : Build Path &gt;&gt; Use as Source Folder. This
    folder will be used in the future to hold the JUnit test classes.
-   Now the project folder should look like the following:
-   [<img src="http://lh4.ggpht.com/-waVWgZ05CRE/UVd96U-nfAI/AAAAAAAABHU/_oYgiZlbOnc/2013-03-28%25252016_00_38-Java%252520-%252520jpf_junit_demo_src_TestGenerator.java%252520-%252520Eclipse%252520SDK_thumb.png?imgmax=800" title="2013-03-28 16_00_38-Java - jpf_junit_demo_src_TestGenerator.java - Eclipse SDK" width="240" height="244" alt="2013-03-28 16_00_38-Java - jpf_junit_demo_src_TestGenerator.java - Eclipse SDK" />](http://lh6.ggpht.com/-MH-Gau2Bbl4/UVd942dbyGI/AAAAAAAABHM/0eD7quCXC5c/s1600-h/2013-03-28%25252016_00_38-Java%252520-%252520jpf_junit_demo_src_TestGenerator.java%252520-%252520Eclipse%252520SDK%25255B2%25255D.png)

Step 4.2 : Create a class (program under test)

-   Right click on the “src” folder and choose: New &gt;&gt; Class. Name
    it Calculator and click Finish.

-   This is the content of the very simple Calculator.java which prints
    the sum of two integers. The Verify statements are the only JPF
    statements, the rest is pure java. We will explain the JPF
    statements through its results in the next step.

        import gov.nasa.jpf.jvm.Verify;

        public class Calculator {
            int add (int a, int b)
            {
                return a+b;
            }
            public static void main(String[] args)
            {
                int a = Verify.getInt(1,3);
                int b = Verify.getInt(5,8);
                Calculator cal = new Calculator();
                System.out.println(a + "+" + b + "=" + cal.add(a, b));
            }
        }

<!-- -->

-   Step 4.3 : Run JPF from Eclipse
    -   Right click on the project name and select: New &gt;&gt; File.
        Name the file “jpf\_junit\_demo.jpf”.

    -   This is the content of the newly added file

        +classpath=${config\_path}/bin  
        target=TestGenerator

    -   In the package explorer, right click on the
        “jpf\_junit\_demo.jpf” and select “Verify …”.

    -   If you couldn’t see the “Verify…” option, this means that you
        didn’t installed the JPF plug-in properly.  See step 3.3.

    -   JPF will get started and you will see its output in the console
        pane. It will be like the following:

<!-- -->

    Executing command: java -jar C:\Users\Ebeid\projects\jpf\jpf-core\build\RunJPF.jar +shell.port=4242 C:\Users\Ebeid\projects\jpf_junit_demo\jpf_junit.demo.jpf
    JavaPathfinder v6.0 (rev 960+) - (C) RIACS/NASA Ames Research Center

    ====================================================== system under test
    application: Calculator.java

    ====================================================== search started: 3/28/13 4:41 PM
    1+5=6
    1+6=7
    1+7=8
    1+8=9
    2+5=7
    2+6=8
    2+7=9
    2+8=10
    3+5=8
    3+6=9
    3+7=10
    3+8=11

    ====================================================== results
    no errors detected

    ====================================================== statistics
    elapsed time:       00:00:02
    states:             new=5, visited=11, backtracked=16, end=12
    search:             maxDepth=3, constraints hit=0
    choice generators:  thread=1 (signal=0, lock=1, shared ref=0), data=4
    heap:               new=545, released=197, max live=353, gc-cycles=13
    instructions:       5098
    max memory:         55MB
    loaded code:        classes=82, methods=1362

    ====================================================== search finished: 3/28/13 4:41 PM

According to our program code and the JPF results, you may already
guessed what the verify statements are doing in the following lines of
code:

int a = Verify.getInt(1,3);  
int b = Verify.getInt(5,8);

-   Simply, Verify.getInt(x, y) get a new integer within the range
    \[x,y\].
-   That is it ?
-   Partially yes.
-   But how JPF get 12 print outputs ?
-   Ok Actually JPF starts a new clone of the program for each value
    resulted from a Verify.getInt() statement.
-   This means that JPF will create 3 versions of the program, each one
    of these versions runs with a different value of a (1, 2, 3).
-   Each version of these three versions will be used as a base to
    create another 4 versions of the program for variable b, each one of
    these versions runs with a different value of b (5, 6, 7, 8).

So, the total versions of the program running by JPF is 3 \* 4 = 12. Its
like a tree where the leafs are the print statements :

-   a = 1
    -   a = 1, b = 5    |    System.out.println(a + "+" + b + "=" +
        cal.add(a, b));    |    1+5=6
    -   a = 1, b = 6    |    System.out.println(a + "+" + b + "=" +
        cal.add(a, b));    |    1+6=7
    -   a = 1, b = 7    |    System.out.println(a + "+" + b + "=" +
        cal.add(a, b));    |    1+7=8
    -   a = 1, b = 8    |    System.out.println(a + "+" + b + "=" +
        cal.add(a, b));    |    1+8=9
-   a = 2
    -   a = 1, b = 5    |    System.out.println(a + "+" + b + "=" +
        cal.add(a, b));    |    2+5=7
    -   a = 1, b = 6    |    System.out.println(a + "+" + b + "=" +
        cal.add(a, b));    |    2+6=8
    -   a = 1, b = 7    |    System.out.println(a + "+" + b + "=" +
        cal.add(a, b));    |    2+7=9
    -   a = 1, b = 8    |    System.out.println(a + "+" + b + "=" +
        cal.add(a, b));    |    2+8=10
-   a = 3
    -   a = 1, b = 5    |    System.out.println(a + "+" + b + "=" +
        cal.add(a, b));    |    3+5=8
    -   a = 1, b = 6    |    System.out.println(a + "+" + b + "=" +
        cal.add(a, b));    |    3+6=9
    -   a = 1, b = 7    |    System.out.println(a + "+" + b + "=" +
        cal.add(a, b));    |    3+7=10
    -   a = 1, b = 8    |    System.out.println(a + "+" + b + "=" +
        cal.add(a, b));    |    3+8=11

you can use JPF for your JUnit tests to generate explore your code
states as we did; just keep in mind that a small increase in the number
of states of variables could result in huge number of total program
states.

I hope you enjoyed it, and see you later in more posts about JPF.
