--- 
title: "The Z3 Constraint Solver, a developer perspective" 
date: '2013-07-30T06:30:00.000-05:00' 
tags: 
    - Z3 
    - Satiability Modulo Theories
modified_time: '2013-08-13T12:23:43.430-05:00' 
thumbnail: http://lh6.ggpht.com/-\_oulgO08Rjs/UfbC-\_W4NUI/AAAAAAAAB0g/oMAhsSkxYIY/s72-c/fileFProjectsZ3Demo1Z3Demo1binDebugZ3Demo1.EXE\_2013-07-29\_08-51-07\_thumb%25255B1%25255D.png?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-1325923284266296577
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/07/the-z3-constraint-solver-developer.html
---

[Z3](http://research.microsoft.com/en-us/um/redmond/projects/z3/old/ "Z3 : An Efficient Theorem Prover")
is a high-performance SMT solver developed at [Microsoft
Research](http://research.microsoft.com/en-us/ "Microsoft Research"). It
have been integrated with many many tools that came out from Microsoft
for program analysis, testing, and verification.

#### What SAT means ?

SAT refers to Boolean satisfiability problem where we want to determine
if there exists an interpretation that satisfies a given Boolean
formula. In other words, it establishes if the variables of a given
Boolean formula can be assigned in such a way as to make the formula
evaluate to true.

#### What SMT means ?

SMT stands for Satiability Modulo Theories. SMT instance is a formula in
first-order logic, where some functions and predicates have additional
interpretations. SMT problem is a decision problem of determining
whether such a formula is satisfiable or not.

An SMT instance is a generalization of a Boolean SAT instance in which
various sets of variables are replaced by predicates over a suitable set
of non-binary variables.

These predicates are classified according to the theory they belong to.
For instance, linear inequalities over real variables are evaluated
using the rules of the theory of linear real arithmetic.

#### What SMT solver means ?

The goal of an SMT solver is to determine whether an SMT instance can
evaluate to true or not. The same analog applies for SAT solvers.

#### SMT solvers

There is a lot of SMT solvers available but there is only one SMT solver
with C\# APIs, it is Z3. For a list of available SMT solvers, refer to
this
[page](http://en.wikipedia.org/wiki/Satisfiability_Modulo_Theories "Satisfiability Modulo Theories").

#### Download Z3

You can download Z3 from <http://z3.codeplex.com/> . I downloaded Z3
4.3.0 and extracted it to C:\\z3.

#### C\# Example

In the following example we going to let Z3 solve the following equation
system:

-   x &gt; 0
-   y = x + 1 
-   y &lt; 3

Solving the equations means finding values for x and y that make the
whole formula evaluates to true.

-   Let’s create a new console application project in Visual Studio.
-   Add reference to *Microsoft.Z3.dll* which is located in the bin
    directory of the Z3 installation directory.
-   Copy the file libz3.dll from the bin directory of the Z3
    installation directory to your project build directory.
-   Now edit your code to look like the following:

<!-- -->

    using System;
    using Microsoft.Z3;

    namespace Z3Demo1
    {
        class Program
        {
            static void Main(string[] args)
            {
                using (Context ctx = new Context())
                {
                    Expr x = ctx.MkConst("x", ctx.MkIntSort());
                    Expr y = ctx.MkConst("y", ctx.MkIntSort());
                    Expr zero = ctx.MkNumeral(0, ctx.MkIntSort());
                    Expr one = ctx.MkNumeral(1, ctx.MkIntSort());
                    Expr three = ctx.MkNumeral(3, ctx.MkIntSort());
                    
                    Solver s = ctx.MkSolver();
                    s.Assert(ctx.MkAnd(ctx.MkGt((ArithExpr)x, (ArithExpr)zero), ctx.MkEq((ArithExpr)y, 
                        ctx.MkAdd((ArithExpr)x, (ArithExpr)one)), ctx.MkLt((ArithExpr)y, (ArithExpr)three)));
                    Console.WriteLine(s.Check());

                    Model m = s.Model;
                    foreach (FuncDecl d in m.Decls)
                            Console.WriteLine(d.Name + " -> " + m.ConstInterp(d));
                        
                    Console.ReadLine();
                }
            }
        }
    }

  
  

Now let’s run the code above and see the output. The solver says the
equation system is satisfiable and then gives us the x and y values that
satisfy.

  
  

[<img src="http://lh6.ggpht.com/-_oulgO08Rjs/UfbC-_W4NUI/AAAAAAAAB0g/oMAhsSkxYIY/fileFProjectsZ3Demo1Z3Demo1binDebugZ3Demo1.EXE_2013-07-29_08-51-07_thumb%25255B1%25255D.png?imgmax=800" title="fileFProjectsZ3Demo1Z3Demo1binDebugZ3Demo1.EXE_2013-07-29_08-51-07" width="134" height="84" alt="fileFProjectsZ3Demo1Z3Demo1binDebugZ3Demo1.EXE_2013-07-29_08-51-07" />](http://lh5.ggpht.com/-9rk9PdkdmKw/UfbC-RmJw4I/AAAAAAAAB0Y/tKHMbwujGC8/s1600-h/fileFProjectsZ3Demo1Z3Demo1binDebugZ3Demo1.EXE_2013-07-29_08-51-07%25255B3%25255D.png)

  
  

#### How it works ?

  
  

To interact with Z3 through C\#, you need a
[Context](http://research.microsoft.com/en-us/um/redmond/projects/z3/class_microsoft_1_1_z3_1_1_context.html "Context Class Reference")
object. Variables and numerals in your equations are modeled as
[Expr](http://research.microsoft.com/en-us/um/redmond/projects/z3/class_microsoft_1_1_z3_1_1_expr.html "Expr Class Reference")
objects. You get these objects using member functions in the Context
object (MkConts(), MkNumeral(),….). You construct your operand using
member functions in the Context object (MkGt(), MkAdd(), MkLt(),…). To
solve all the equations together you need to hock them up using AND
operator, which is implemented using Context.MkAnd(). After hocking
everything in one AND, you pass that the solver through
[Solver](http://research.microsoft.com/en-us/um/redmond/projects/z3/class_microsoft_1_1_z3_1_1_solver.html "Solver Class Reference").Assert().
And as you may guessed, you obtain this Solver using Context.MkSolver().

  
  

Solver.Check() will tell you whether this equation system can be solved
or not. To get the variables’ assignments that the come up with, get a
Model object Solver.Model. Then use the Delcs collection to get all
symbols that have an interpretation in the model. Model.ConstInterp()
will get the symbol assigned value.

  
  

In this post we briefly introduced SAT, SMT, and their solvers. Then we
explored the only SMT solver that written in C\# and had a C\# API. Now
you can play with as many equations as you want and check them for
satisfiability and even got the solution values.
