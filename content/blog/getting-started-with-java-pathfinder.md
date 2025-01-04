---
title: 'Getting Started with Java PathFinder'
date: 2013-03-30T19:06:00.001-05:00
draft: false
url: /2013/03/getting-started-with-java-pathfinder.html
tags: 
- JPF
- Model Checking
---

Java™ Pathfinder, or **_"JPF"_** as we call it from here, is a highly customizable execution environment for verification of Java™ bytecode programs. **[JPF](http://babelfish.arc.nasa.gov/trac/jpf/)** was developed at the [NASA Ames Research Center](http://www.arc.nasa.gov), open sourced in 2005, and is freely available [here](http://babelfish.arc.nasa.gov/trac/jpf/) under the [NOSA 1.3](http://javapathfinder.sourceforge.net/NOSA-1.3-JPF.txt) license. **JPF** started as a software model checker but it integrates model checking, program analysis and testing.

In this post  we will go in a step by step process to setup the  environment where Java Path Finder can be used within Eclipse IDE environment. We will show a simple example of using JPF.

*   Step 1. Install Eclipse
    *   Step 1.1 : Download and install the latest JDK fro your platform from [here](http://www.oracle.com/technetwork/java/javase/downloads/index.html).
    *   Step 1.2 : Download the latest Eclipse from [here](http://www.eclipse.org/downloads/). Once you have unzipped the previously downloaded file, you will see a folder named eclipse.  In that folder you will find the eclipse application.  We recommend you create a shortcut on the desktop to simplify the launching of eclipse.  Notice that unlike Java, Eclipse does not have an installation process. Once you have unzipped the file you are done.
*   Step 2. Download JPF

*   Step 2.1 : Download Mercurial plug-in for Eclipse
    *   Launch Eclipse. Go to Help >> Install New Software
    *   [![2013-03-28 13_54_12-Java - jpf_junit_demo_src_TestGenerator.java - Eclipse SDK](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjjQSIAnZR8AkQMeAc6m-iiEIHZF3HKTHOSdoLExxHVhTuhHda7WeinRESqFFQKQhckJpB5TxuIUKQZzQGMieOjmiPVKZXiJOdhDEsqawzqsfFq_DBanQK1oUIWfA65Si-92cNYHR7wyQ/?imgmax=800 "2013-03-28 13_54_12-Java - jpf_junit_demo_src_TestGenerator.java - Eclipse SDK")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh27GAQtRHt2zWifcgT1ikpMxwN18KQ6nZHFCXqkl2HX3-uYOq3dk5rvy30xpLYukYaDSjkKd-TarJQPOqHczV9Vg5u52xKYRYB5nORZk8vwZtyjNWvITp9oOe6CGvIhy95Up26F-Jd3Q/s1600-h/2013-03-28%25252013_54_12-Java%252520-%252520jpf_junit_demo_src_TestGenerator.java%252520-%252520Eclipse%252520SDK%25255B3%25255D.png)
    *   Click Add
    *   [![2013-03-28 14_01_12-Install](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgH8apSvB38az2Wy4qOe_P_vpZf6km_Uc29Xa_tbACWSS0CqKm94RILZXaDUrCIR9RLF9k5zWM1kh4s31Vx0z9lb30EOgg4gpsoxHXXoDc89DLwW7SzPuAxgDWp2bI1xZ8nFikE3gCIEA/?imgmax=800 "2013-03-28 14_01_12-Install")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh0td3JfZwfZy0GNebO7-vZixMhh1kxV7Zf4TcrX_GNL1CnE44YT-sH_9S3ILZPLryPZKGatnUkN9MRaThLcU37EeRpy8XsErw9A_PKLaZor479pSJ4bceoFVG07Ji3QjuazUFdr35oyA/s1600-h/2013-03-28%25252014_01_12-Install%25255B2%25255D.png)
    *   Insert “Mercurial” in the Name box. Insert “[http://mercurialeclipse.eclipselabs.org.codespot.com/hg.wiki/update\_site/stable/](http://mercurialeclipse.eclipselabs.org.codespot.com/hg.wiki/update_site/stable/ "http://mercurialeclipse.eclipselabs.org.codespot.com/hg.wiki/update_site/stable/")” in the Address box. Click Ok.
    *   In the install dialog select the newly added site from Work with drop down box. The list below it will show the available software at this site, select the item named MercurialEclipse and click Next, then finish..
    *   [![2013-03-28 14_05_37-Install](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEil2okeEXs4sGyo-K_J1OzoEuPlz__82SAk-xZhyIetQQB4DpgMiWU4pixvrxgWYgD2ZSb1v_f-tsKjEgm8a37PV3P6Iv4gJL-YY1YVav6bTok089UHtvQ-spAMJ5pCMpLg1RKgSghpeA/?imgmax=800 "2013-03-28 14_05_37-Install")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiyeaiKmC2Qgo7-heaDvCMtRKnWFY0OjX039dYOTckPeX2uhJeWhbrTpt6MVxwnbiNCdQOYUw7TfYPTdHaWXUD17ybhF866msl1A9r7E7hNxRb0ofY0o2C7o9WR18a0kgzgKFSvGg3gLg/s1600-h/2013-03-28%25252014_05_37-Install%25255B2%25255D.png)
*   Step 2.2 : Download the JPF source code
    *   In Eclipse menu : File >> Import >> Mercurial >> Clone Existing Mercurial Repository >> Next.
    *   [![2013-03-28 14_42_31-Mercurial clone repository wizard](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjifgSSmYXOYxeryVu4dHSyeB4rAfsH74K0tio7-Uz-cIb-CAiY3N-iWc2Yqu6WnBgIn2g5esuIuJA9DBAmdzMm2RzVI0q-U1op62ej6aG4e1D8nucQYehDMILd_Z13yT-BXZWHnU2kpA/?imgmax=800 "2013-03-28 14_42_31-Mercurial clone repository wizard")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEggtVegeqquEKSl_JVpzIa1YJ7eTA6I6tylWlSWBg19KIIDusBU_4L-XJpk0b8OQI-SRVde4_Yu3xo6HpNm5Si70jqgQdaj3n-tiymFolJsNSVD3GniSgcl8sOMfSk-izWx1nhPF5vGRg/s1600-h/2013-03-28%25252014_42_31-Mercurial%252520clone%252520repository%252520wizard%25255B2%25255D.png)
    *   In the repository location URL, insert “[http://babelfish.arc.nasa.gov/hg/jpf/jpf-core](http://babelfish.arc.nasa.gov/hg/jpf/jpf-core "http://babelfish.arc.nasa.gov/hg/jpf/jpf-core")”. Click Next, then Finish. The JPF project files will be downloaded to your local computer.
*   Step 2.3 : Build the JPF

*   In the package explorer, select the build.xml, right click on it, select “run as” >> “Run as Ant build “.
*   Eclipse will build JPF and a new folder named “build” will appear in the package explorer (it may not appear even the build was successful, double check the windows explorer for it.)

*   If the build failed due to error missing JDK:

*   On Eclipse menu : Project >> Properties. Select Builders from the lift hand side list
*   [![2013-03-30 19_52_18-Java - jpf_junit_demo_test_CalculatorTest.java - Eclipse SDK](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhXkSmgi8KQ6CEH51SQSrTvtiyU2tyUnuuryU3uTO1iLE83iqjSzWuj68X5Ev7COClRojBXBbT-9ANT5C1hUGBI26pl1AkF2rKER2Iegd56EXPjQEKCcMn2kAK6J0VpS0-Y_3EBB68oqw/?imgmax=800 "2013-03-30 19_52_18-Java - jpf_junit_demo_test_CalculatorTest.java - Eclipse SDK")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEilE28D-G1VtKtYPWdzErJJ6Of07Eoe0ZGwfeEm-5T6j0upnzHE9NpPv70SEDKsOp_FCo0ddYci8s4q8MhxHUjWSDnM29QCxrAUuPsRcfAZTe3MG8Cm01R8NYCrZKY9qbTUbEVY4Y5a2A/s1600-h/2013-03-30%25252019_52_18-Java%252520-%252520jpf_junit_demo_test_CalculatorTest.java%252520-%252520Eclipse%252520SDK%25255B2%25255D.png)
*   Select Ant Builder and click New.
*   Select Ant Builder and click New.
*   In the Edit Configuration dialog, select the “JRE” tab, then select “Separate JRE” from the “Runtime JRE section”. In the drop down list, select JDK:
*   [![2013-03-30 20_01_41-Edit Configuration](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjyYmXvATLdMmzjBlaiuwQmdaFMomlsYJ57iSV_3iICUtTq00Mnbjj_DOPV8mFOXFknX98-epPxp41uUTRfm_vcJGvcle50OKfaaFFFQt0F_2Rt7ez_nHp_MS6EZalaekdm3Bn0Zbv18w/?imgmax=800 "2013-03-30 20_01_41-Edit Configuration")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhWzCRjbsia3V39OfMvs289XUWWkhfypUl4wKggQl2pctZJHzEcjXnhahSj2H7yLjkGx9EVP5wf-0Ray8eW2m5vbqjF52IBncKe_onf2TPa6uNIL1BS9yOmlBmMkv9zm_LzI9zb-lP_ag/s1600-h/2013-03-30%25252020_01_41-Edit%252520Configuration%25255B2%25255D.png)
*   If you couldn’t find the JDK in the drop down list, click “Installed JRE …”
*   [![2013-03-30 20_05_18-Preferences (Filtered)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjBK1ViO7cJu5-LKUkZm9f36cFR1iftTYaqf-QkatYAcZlwyHprSByM3udI5SFl5xqZsOvoGGgF0HPMGQ_TcYvWQgfxqKM2bWLjw3jV5WxpMNTOz30MjbgbbJxmqce022ZDu3LBdPH-gw/?imgmax=800 "2013-03-30 20_05_18-Preferences (Filtered)")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg4kLXyPDgEbY23NT5U03M5zgJP8lEetxJ07-RFAV23ej45sXWwbHj4DGRrCL9LFj6ynge20p6qV-ga3lGJb80_VazSxjUCh2gOnhMZ71-jnCNWLXimJxHAcnJ6LP6Joxeaddv_0-b4jA/s1600-h/2013-03-30%25252020_05_18-Preferences%252520%252528Filtered%252529%25255B2%25255D.png)
*   In the “Preferences” dialog, click “Add”
*   [![2013-03-30 20_07_40-Preferences (Filtered)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgzRffkz9B8Y33SaG7IgseiBT63mDuOoZOyRc-CRVjpvqIHXgJwnl7Wd4_Uuatm5sXGDHwm_NBrm-YWAt_z5kCthRaLKfsRfSXkBR1rKz7QXocA_tSaxT7tVwAUYKM-G_TDTdfLoHDbPA/?imgmax=800 "2013-03-30 20_07_40-Preferences (Filtered)")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhfETFF4rPbpIRbP-_W2k8Q6uD8L28fHLUbic-tPec_nEFAueEEIYwLL8nMhQTnIAXxlxZJqhKrJaIKX2EkuUyDk71AlxT4x8y48Nn8EnkIq7ecKgPRn7zyMW5tpvlx_6sm_6nCCCOPzQ/s1600-h/2013-03-30%25252020_07_40-Preferences%252520%252528Filtered%252529%25255B2%25255D.png)
*   Select “Standard VM” and click “Next”
*   [![2013-03-30 20_10_06-Edit Configuration](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiS2mJcchkyW5dDq7nlLaFbMR-5p_k1s2apnyByZaFDA5GjsE7czs070YjGP7zHI3ekFUBtJsDHzKSW5o0mcbcbIciyqSu2ufDEmiVi6WK8zglDyX4KlsfNqksxsXANYHmtuS9KVPLE2w/?imgmax=800 "2013-03-30 20_10_06-Edit Configuration")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjL3kEyu6v8HjHL62hYmQxDhKecq5B2qPiZ1sFEAVsW8o99K7q4Y9csgh-9T6Gnsk6q8puv0iKHtWJcJq9_wzeiypWNCTGDpOz5id1vLoZReC_l_nWTajIpbPjXplDQVumoGu8KlZCYuw/s1600-h/2013-03-30%25252020_10_06-Edit%252520Configuration%25255B2%25255D.png)
*   Click “Directory” and navigate to your JDK installation directory. Then click “Finish” to return to the previous dialog.
*   [![2013-03-30 20_11_56-Preferences (Filtered)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg1Iy3SHntyTBLyyEkWH2j3_qDqFh8o6aHQCHVVgIhNYleR2tus4aN0KqKQHALEEJ0hVwcKnxTomAKHeSSQFI63OJ6FiE0vXh4zck64s_1TeWxzYSLCBiMzYnORQYrfEW7FBhH7fX_sqw/?imgmax=800 "2013-03-30 20_11_56-Preferences (Filtered)")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg6sRJ2nAC3yg7rngp0WW_3wxfdpShOmHmqpPVLKgEha-dqMXGFfLY-TTrNBrR9dJVE2NH-FfkIgOZ3luQuQst3TS-RxZinn0IjY4s-nH6VkGjxCsfeK8osclXoB7CHWVpW1B6l4-XPIQ/s1600-h/2013-03-30%25252020_11_56-Preferences%252520%252528Filtered%252529%25255B2%25255D.png)  
*   Select the JDK and click Ok.
*   Select JDK in the drop down box and click OK
*   [![2013-03-30 20_13_43-Edit Configuration](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiKZSqz5xDWCdT-4ORSKJ3Xlw-5JEG2nt-F7wl4oj6uKNkP2z8KhGVJlJpibuiZmmUuOpPmub4YI_XbPZQoNLC1po90lGin8kxvs0rdJPD3ugyT2qTGF30GAFTVxLO4Yc-EeO4GFJBSvw/?imgmax=800 "2013-03-30 20_13_43-Edit Configuration")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjB3hGDDRbZNrJH175ku0Re0VqB6jEGo97LDSaV7rFftzHCHUr-gdano4OOo3aCFkmmQcswn-KOz7O_n8xvFbgR5pHOnrtZFEI_bgY6fA6MBmt_iSOw01JhnkaCVZczxIiKmwGxkt8FBA/s1600-h/2013-03-30%25252020_13_43-Edit%252520Configuration%25255B2%25255D.png)

*   Step 3 : Install and configure JPF
    *   Step 3.1 : Install JPF files : Copy the whole jpf-core project folder into <user.home>/projects/jpf
    *   Step 3.2 : Create site.properties
        *   Create site.properties under <user.home>/.jpf folder.
        *   To create the folder on windows, use the following command on the command window after navigating to the user home: mkdir .jpf .
        *   Paste the following content into the site.properties file.```
            \# JPF site configuration
            
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
            
            ```
    *   Step 3.3 : Install Eclipse plug-in
        *   The JPF Eclipse plug-in allows you to invoke JPF directly from Eclipse.
        *   In Eclipse go to Help >> Install New Software.
        *   In the new window click Add. In the name insert JPF. In the location insert “[http://babelfish.arc.nasa.gov/trac/jpf/raw-attachment/wiki/install/eclipse-plugin/update/](http://babelfish.arc.nasa.gov/trac/jpf/raw-attachment/wiki/install/eclipse-plugin/update/)” then click Ok.
        *   From the “Work with:” drop down menu select the newly added site.
        *   In the list, check “Eclipse-JPF”, click Next, then Finish.
*   Step 4 : Start the demo project
    *   Step 4.1 : Create and configure project
        *   In Eclipse menu : File >> New >> Java project : project name = jpf\_junit\_demo
        *   In the package explorer, right click on the project name. Choose “Build Path” >> “Add libraries”
        *   [![2013-03-28 15_41_55-Add Library](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg5GLQ9dSxu-3TgpKfFl6jCv0eCAEh8CiqMyFNkTYlBWR_ruFBT-owakpWLPxJY52ZjQffZlJzMR6tlwHuBfUs8q5eL4pm8bi11vTAEcsOdWr2mEZJjfuJymPM_hPo7vUtE0GilwCxNiw/?imgmax=800 "2013-03-28 15_41_55-Add Library")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg52OxEXoSGBF1R4wkDur-6mODnwHC_HBwgTufH3kbXiSEUnw4StYfXFIt6X9r6zgdg1x5pdJsc4GyqXrlxFLqWZ_dlg1wQgnSbTJU3pl1apD01uZAsyatVOxptYrZ6dbyQRei3rCY0gQ/s1600-h/2013-03-28%25252015_41_55-Add%252520Library%25255B2%25255D.png) 
        *   Select User Library and click Next.
        *   Click User libraries. Then New. You will see a window for creating a library. Put “jpf” as the library name and click Ok to return to the previous dialog.
        *   Select the newly added jpf library and click “Add External JARs …”.
        *   Select all the jar files under <user.home>/jpf/jpf-core/build and click “Open” to add them under library jpf
        *   Click New to create a new user library. Name it “jpf-support”.
        *   Select the newly added jpf-support library and click “Add External JARs …”.
        *   Select all the jar files under <user.home>/jpf/jpf-core/lib and click “Open” to add them under library jpf-support
        *   Now the User Libraries should look like the following:
        *   [![2013-03-28 15_54_32-Preferences (Filtered)](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiH_OByU4p5Y29D4wykvsSM0IW_nLlcz1ApDUBAuHx9f0y52aotcVy62ihA1_-DkCzCUVdy47wJ4zem5PynDYENLkcIjRW1peP2Wi195QGzSs7xRHAg3uSImw7vSbuhlb-Yu8yQZUtaDA/?imgmax=800 "2013-03-28 15_54_32-Preferences (Filtered)")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjLPHE9xY02c7C54DmlTEn556Mmzr-6jjkQYAPz-xTm2ANUqQ2Wfu79G5DA3c5sEnt0x6VWJqzCe7UEuPfIiToygbs7EKflDUXmpIaQqbdG9CRGLipfgVTKTRVfzPBF-wrPGzQi5mgeqA/s1600-h/2013-03-28%25252015_54_32-Preferences%252520%252528Filtered%252529%25255B2%25255D.png) 
        *   Right click on the project name and select : New >> Folder, name the folder as test. Right click on the newly created test folder and select : Build Path >> Use as Source Folder. This folder will be used in the future to hold the JUnit test classes.
        *   Now the project folder should look like the following:
        *   [![2013-03-28 16_00_38-Java - jpf_junit_demo_src_TestGenerator.java - Eclipse SDK](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjygA-xpgfsEUHoIv3Y8UGLfhs5NO7BSyF84Un-AcTRSHQcuMtGo7z-Gyp3-T1czKiI_tEJPYZVuZd8d_xtM7wOazgidxD4A7iWHhKBdimrnZfpkqDf2j8CIoBHZakCYqSQmh_vav1-tA/?imgmax=800 "2013-03-28 16_00_38-Java - jpf_junit_demo_src_TestGenerator.java - Eclipse SDK")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh8w2VBn9RYnUR8Z6NRwBWrtJF3YnLFTsYHuKnGkJ4Cu1DacO1HABwsp_XpvlTqS0V-p73xUHop894UTWyrcsGfxlfCv86ONtMQhLA__rciiFBwH4-jaSkymUncQ6FVJ8iGXhnWHQ_81Q/s1600-h/2013-03-28%25252016_00_38-Java%252520-%252520jpf_junit_demo_src_TestGenerator.java%252520-%252520Eclipse%252520SDK%25255B2%25255D.png)
    *   Step 4.2 : Create a class (program under test)
        
        *   Right click on the “src” folder and choose: New >> Class. Name it Calculator and click Finish.
        *   This is the content of the very simple Calculator.java which prints the sum of two integers. The Verify statements are the only JPF statements, the rest is pure java. We will explain the JPF statements through its results in the next step.
            
            ```
            import gov.nasa.jpf.jvm.Verify;
            
            public class Calculator {
                int add (int a, int b)
                {
                    return a+b;
                }
                public static void main(String\[\] args)
                {
                    int a = Verify.getInt(1,3);
                    int b = Verify.getInt(5,8);
                    Calculator cal = new Calculator();
                    System.out.println(a + "+" + b + "=" + cal.add(a, b));
                }
            }
            
            ```
        
        *   Step 4.3 : Run JPF from Eclipse
            *   Right click on the project name and select: New >> File. Name the file “jpf\_junit\_demo.jpf”.
            *   This is the content of the newly added file
                
                +classpath=${config\_path}/bin  
                target=TestGenerator
                
            *   In the package explorer, right click on the “jpf\_junit\_demo.jpf” and select “Verify …”.
            *   If you couldn’t see the “Verify…” option, this means that you didn’t installed the JPF plug-in properly.  See step 3.3.
            *   JPF will get started and you will see its output in the console pane. It will be like the following:
        
        ```
        Executing command: java -jar C:\\Users\\Ebeid\\projects\\jpf\\jpf-core\\build\\RunJPF.jar +shell.port=4242 C:\\Users\\Ebeid\\projects\\jpf\_junit\_demo\\jpf\_junit.demo.jpf
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
        
        ```
        
        According to our program code and the JPF results, you may already guessed what the verify statements are doing in the following lines of code:
        
        int a = Verify.getInt(1,3);  
        int b = Verify.getInt(5,8);
        
        *   Simply, Verify.getInt(x, y) get a new integer within the range \[x,y\].
        *   That is it ?
        *   Partially yes.
        *   But how JPF get 12 print outputs ?
        *   Ok Actually JPF starts a new clone of the program for each value resulted from a Verify.getInt() statement.
        *   This means that JPF will create 3 versions of the program, each one of these versions runs with a different value of a (1, 2, 3).
        *   Each version of these three versions will be used as a base to create another 4 versions of the program for variable b, each one of these versions runs with a different value of b (5, 6, 7, 8).
        
        So, the total versions of the program running by JPF is 3 \* 4 = 12. Its like a tree where the leafs are the print statements :
        
        *   a = 1
            *   a = 1, b = 5    |    System.out.println(a + "+" + b + "=" + cal.add(a, b));    |    1+5=6
            *   a = 1, b = 6    |    System.out.println(a + "+" + b + "=" + cal.add(a, b));    |    1+6=7
            *   a = 1, b = 7    |    System.out.println(a + "+" + b + "=" + cal.add(a, b));    |    1+7=8
            *   a = 1, b = 8    |    System.out.println(a + "+" + b + "=" + cal.add(a, b));    |    1+8=9
        *   a = 2
            *   a = 1, b = 5    |    System.out.println(a + "+" + b + "=" + cal.add(a, b));    |    2+5=7
            *   a = 1, b = 6    |    System.out.println(a + "+" + b + "=" + cal.add(a, b));    |    2+6=8
            *   a = 1, b = 7    |    System.out.println(a + "+" + b + "=" + cal.add(a, b));    |    2+7=9
            *   a = 1, b = 8    |    System.out.println(a + "+" + b + "=" + cal.add(a, b));    |    2+8=10
        *   a = 3
            *   a = 1, b = 5    |    System.out.println(a + "+" + b + "=" + cal.add(a, b));    |    3+5=8
            *   a = 1, b = 6    |    System.out.println(a + "+" + b + "=" + cal.add(a, b));    |    3+6=9
            *   a = 1, b = 7    |    System.out.println(a + "+" + b + "=" + cal.add(a, b));    |    3+7=10
            *   a = 1, b = 8    |    System.out.println(a + "+" + b + "=" + cal.add(a, b));    |    3+8=11
        
        you can use JPF for your JUnit tests to generate explore your code states as we did; just keep in mind that a small increase in the number of states of variables could result in huge number of total program states.
        
        I hope you enjoyed it, and see you later in more posts about JPF.