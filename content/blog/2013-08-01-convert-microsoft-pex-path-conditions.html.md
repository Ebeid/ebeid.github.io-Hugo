--- 
title: "Convert Microsoft Pex path conditions from Z3 native format to SMT-LIB" 
date: '2013-08-01T16:24:00.001-05:00' 
tags: 
    - Microsoft Pex
    - Z3 
    - SMT-LIB 
modified_time: '2013-08-13T13:00:02.463-05:00'
thumbnail: http://lh4.ggpht.com/-Vz88wIo5p30/Ugp0ICflqEI/AAAAAAAAB1w/dL-ogc\_PgSo/s72-c/Z3ToSMTLIB%252520-%252520Microsoft%252520Visual%252520Studio\_2013-08-13\_12-58-55\_thumb%25255B2%25255D.png?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-1053702483261378276
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/08/convert-microsoft-pex-path-conditions.html
---

We talked before about [getting the code path conditions from Microsoft
Pex](http://ebeid-soliman.blogspot.com/2013/07/get-path-conditions-from-microsoft-pex.html "Get path conditions from Microsoft Pex")
as in
[Z3](http://research.microsoft.com/en-us/um/redmond/projects/z3/old/index.html "Z3 : An Efficient Theorem Prover")
native format(.z3 file).

Sometimes you may need to convert from Z3 native format to
[SMT-LIB](http://www.smt-lib.org/ "SMT-LIB The Satisfiability Modulo Theories Library")
standard. You can do that using the [Z3 C\#
APIs](http://ebeid-soliman.blogspot.com/2013/07/the-z3-constraint-solver-developer.html "The Z3 Constraint Solver, a developer perspective").
The only trick here is: you have to use the Microsoft.Z3.dll that come
with your current Microsoft Pex installation (C:\\Program
Files\\Microsoft Pex\\bin\\Microsoft.Z3.dll).

To show how it works, let’s create a new C\# console application. Add
refeerence to Microsoft.Z3.dll that come with your Pex installation.

Edit your code to look like:

    using System;
    using System.IO;
    using Microsoft.Z3;

    namespace Z3ToSMTLIB
    {
        class Program
        {
            static void Main(string[] args)
            {
                if(args.Length == 0)
                    Console.WriteLine("Please provide input file name.");
                if (!File.Exists(args[0]))
                    Console.WriteLine("The specified file doesn't exist.");
                using (Context ctx = new Context(new Config()))
                {
                    string SMTLIB= ctx.ParseZ3File(args[0]).ToString();
                    StreamWriter writer = new StreamWriter(args[0].TrimEnd("z3".ToCharArray()) + "SMTLIB");
                    writer.Write(SMTLIB);
                    writer.Close();
                }
            }
        }
    }

  

Right click your project in the solution explorer and select Add
&gt;&gt; New Item &gt;&gt; select Application Configuration File
&gt;&gt; click Add. Edit the newly created App.config file to look like:
[<img src="http://lh4.ggpht.com/-Vz88wIo5p30/Ugp0ICflqEI/AAAAAAAAB1w/dL-ogc_PgSo/Z3ToSMTLIB%252520-%252520Microsoft%252520Visual%252520Studio_2013-08-13_12-58-55_thumb%25255B2%25255D.png?imgmax=800" title="Z3ToSMTLIB - Microsoft Visual Studio_2013-08-13_12-58-55" width="562" height="127" alt="Z3ToSMTLIB - Microsoft Visual Studio_2013-08-13_12-58-55" />](http://lh5.ggpht.com/-FZnsrOJ7QM4/Ugp0HznPK6I/AAAAAAAAB1o/-vgKoRVAUAI/s1600-h/Z3ToSMTLIB%252520-%252520Microsoft%252520Visual%252520Studio_2013-08-13_12-58-55%25255B4%25255D.png)Now
you can run your code and pass a file in Z3 native format and get a file
in SMT-LIB format. This SMT-LIB format opens a lot of possibilities that
we will explore later.
