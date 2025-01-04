---
title: 'Introduction to Mining Software Engineering Data'
date: 2009-02-26T08:55:00.001-06:00
draft: false
url: /2009/02/introduction-to-mining-software.html
---

Tao Xie | North Carolina State University | [xie@csc.ncsu.edu](mailto:xie@csc.ncsu.edu)

Ahmed E. Hassan | University of Victoria | ahmed@uvic.ca

Part I

Mining Software Engineering Data goals:

*   Transform static record-keeping SE data to active data.
*   Make SE data actionable by uncovering hidden patterns and trends.

Uses of mining SE data:

*   Gain empirically-based understanding of software development.
*   Predict, plan, and understand various aspects of a project.
*   Support future development and project management activities.

[![clip_image001](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEik-EUy9r3DJNkZgi6tq6-2RqUad8xyqvpwfZCU37X2AGf875An8I0GAVfGL4aub6hZsQp-4iSVetzkWeIvIj1m6whznkObHf2b7sT8TzYYtdRJfgGlTHSNuDkbOEv1WAbnhhbhGLvxpA/?imgmax=800 "clip_image001")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh7tOTCwU6a4VU-lhWN_7Rzpd5OkHYDQ44XjkmKyzIp1dygl2bzS3kWRQU2gLUA-Ypzkhjai8UW29cQFF2vOMLLBmQJNSdXEWg35eO0awWOdLFns4gC9iTrBRJAz2IirUPZg-8VafV72w/s1600-h/clip_image001%5B3%5D.png)

Types of SE Data:

*   Historical data

Used primarily for record-keeping activities (checking the status of a bug, retrieving old code)

*   Version or source control:
    *   cvs, subversion, perforce.
    *   Store changes to the data

*   Bug systems:
    *   bugzilla, GNATS, JIRA.
    *   Follow the resolution of defects.

*   Mailing lists:
    *   Mbox
    *   Record rationale for decisions throughout the life of a project.

*   Multi-run and Multi-site data
    *   Execution traces
    *   Deployment logs

[![clip_image002](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi607lLm41gHivHyBRd6DAtDkXF60c52kNYx_sZH3V8CZWKqRHi6DCgnbBOItCTWWFzrkvudLv9G26Vlw057-8wf_vhP0ci5c0xqy0MDhVrbqjpTip19LP9aD061GNg_i3H622UPMpQ1Q/?imgmax=800 "clip_image002")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg5vSshUC0nseonS_jyfojFlhiMEBfyG-jH-Z0hNqNXAtpNTORdC1-w0Np6X3nLvdSjaK5IEWq1o6olJD_GoBSfceKU6HavQNwJSm_5_-yNOhXG7FHYCkE9zRlL88mhRP956ljw3dH4Hw/s1600-h/clip_image002%5B3%5D.png)

Software Maintenance Activities

*   Perfective: add new functionality
*   Corrective: fix faults
*   Adaptive: new file formats, refactoring

Source Control Repositories

A source control system tracks changes to ChangeUnits.

Examples of ChangeUnits:

*   File
*   Function
*   Dependency (e.g. Call )

For each ChangeUnit, it tracks the developer, time, change message, co-changing Units.

[![clip_image003](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjVGQXH_yCHD-uXP6UQk3J4UkvfWzEISq1CrJCrY0gqXQsIWxx0BhkI6Hq16QuhPyBDP1QlUBBXvUegSRVUzgIyEN9CUbyYqkFVADJUm1p9TaDqbP0qysjXeu_NeSpnf2IoZgK-arp3Ew/?imgmax=800 "clip_image003")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjQ_OOntLwQno12UkiYQMhcCNxaJhUhPn3v-CijdJYEb2h86GOTZ4Gwxqx5hQkx_jv-DUSpBmgKZ_wYct8hUGejEZxBJtTr3EN373CVTXb8E_XRBP_BjsdejI2lyuAwN6u8pN7X1YZXdA/s1600-h/clip_image003%5B3%5D.jpg)

Change Propagation

[![clip_image004](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhKgAiNbxOG6pvnykObtIm1BNGi2aB3sXy_OjbSN3CRUIDk7DTbgYt-lEM7zh2-z_mVdOhV5IWxU6fnHdVgH2-42fSNDcix0TTxAmjlKJkjO4HfbcCvY7g-uU5qEG8fOAoCYJZ4aKG8LA/?imgmax=800 "clip_image004")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiyrblXKJHdp2GY0Bd7hi6qMscWXBB1Yd-C8wHa5qSJ8Wljv72C1S7APnrpjozX0kbDHnK8GQTz-cXdWso0btOFiIELBLA9iGCL-QtDVqluE-qAcXpTUgbuoDYHVmo_9-8ZDMrWEjpyyg/s1600-h/clip_image004%5B3%5D.png)

Measuring Change Propagation

[![clip_image005](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjS5MGs0AurKHFxjwGzy35ThiZQqpKrYuCNYbwwrzoGF8WCasGvoi7ZCt5ItWPHmma83rczxfeIgxK8SgH3FWFxKqCG2_e3unCYT2TUBuJK06qVb35-j4Z7MJ2zowdu2fG6-OeXjKqPgA/?imgmax=800 "clip_image005")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjsLaurKsV7OjHFdJ8TB8sVOUzKCFqrx2s8RsbyCtD4gIBw1cbHuhi7SnRZyPAbWXeALu5_CLuEF_rkPELzHZT1p2ckY_sYjYTzuyX2pa3RJ8gBPdCz1SkERkalN4sbMd3O7NnEF2mwsg/s1600-h/clip_image005%5B3%5D.png)

[![clip_image006](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgkzHGxONVXTl6ISjDxlv47WvdEik8vI21BcE6o9-liALKREUoC4wxmjNK6guVEkhBhzs8QaW-A_gpNAGvHNROGvjWxm34vLBm0GGTSDvniDBgAEwX-gRBdd8Llumt6q-25bNHEm6T7Yw/?imgmax=800 "clip_image006")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhSHZNdVcFf_bJ87mXudMn0ekDQTp-43y4Xo4nv5fbFyTyJ890rgqbQiVaWFiqahqp2TZ-o1ajziNeKvPBA6P74mm8W1Ge09pVuWmiewMDKi0EcwutTnIGENydJqQOIvE2i18L6B9qc4A/s1600-h/clip_image006%5B3%5D.png)

We want:

*   High precision to avoid wasting time
*   High recall to avoid bugs

Guiding Change Propagation

Mine association rules from change history.

Use rules to help propagate changes:

*   Recall as high as 44%
*   Precision around 30%

High precision and recall reached in < 1mth

Prediction accuracy improves prior to a release (i.e., during maintenance phase)

Code Sticky Notes

Traditional dependency graphs and program understanding models usually do not use historical information.

Static dependencies capture only a static view of a system - not enough detail!

Development history can help understand the current structure (architecture) of a software system.

Studying Conway's Law

"The structure of a software system is a direct reflection of the structure of the development team"

[![clip_image007](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiHvuaLHfKzZCz-E50RPuCGLno7lc4HYCL3Ubp7Bj7ase02olPPCIr1Y8rXLXlp0qg6yohx8rqUYNI7DTR158GUYKHm4tcryTOKYrM2jDsUAD6yMilHkhyphenhyphenPRoSwE2D_sAKGfwN7Kd0J6w/?imgmax=800 "clip_image007")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgj9sUgyNzyuWzqAoOTqk0-12yU_JGqKPAeSl33VYrfxmOhyphenhyphenOiOG32dU_YNe-hmccnnz7LeOgszpO5CAbhDm4z7n1ruUTehkWlp4RI0Q2NCDMa0x5oAD6wMV39jo9cyQMsubNibEYRXgA/s1600-h/clip_image007%5B3%5D.png)

Predicting Bugs

Studies have shown that most complexity metrics correlate well with LOC ! (Lines of Code)

Noteworthy findings:

*   Previous bugs are good predictor of future bugs.
*   The more a file changes, the more likely it will have bugs in it.
*   Recent changes affect more the bug potential of a file over older changes (weighted time damp models)
*   Number of developers is of little help in predicting bugs.
*   Hard to generalize bug predictors across projects unless in similar domains.

Example 1 : using imports in Eclipse to predict bugs

*   71% of files that import compiler packages, had to be fixed later on.
*   14% of all files that import ui packages, had to be fixed later on.

Example 2 : don't program on fridays

Percentage of bug-introducing changes for eclipse, most high in Friday.

Classifying changes as Buggy or Clean

Given a change can we warn a developer that there is a bug in it ?

*   Recall/Precision in 50-60% range.

Project Communication - Mailing lists

Most open source projects communicate through mailing lists or IRC channels.

Rich source of information about the inner workings of large projects.

Discussion cover topics such as future plans, design decision, project policies, code or path reviews.

Social network analysis could be performed on discussion threads.

Social Network Analysis

Mail list activity

*   Strongly correlates with code change activity.
*   Moderately correlates with document change activity.

Social network measures (in-degree, out-degree, between's) indicate that committers play much more significant roles in the mailing list community that non-committers.

Immigration rate of developers

When will a developer be invited to join a project?

*   Expertise vs. interest

The patch review process

Two review styles

*   RTC : Review-then-Commit
*   CTR : Commit-then-Review

80% patches reviewed within 3.5 days and 50% reviewed in < 19 hrs

Measure a team's morale around release time

Study the content of messages before and after release.

Use dimensions from a psychometric text analysis tool.

Program Source Code

Code Entities

[![clip_image008](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhLCC2jGfGh8rwQCs7JR3ygpDYFQUJ64PCSzrIwhy9uWoRokS-JeR1A2v8ZMebBKIfi2xoT_d4lswgHfNIiEYRiP5p0yy9IvPP3v1teNsZlqVb3JrrE6kF01DLwXHG3lV1SxguXi7DDAQ/?imgmax=800 "clip_image008")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgYdFsrYmcPMsWx96jtQeBcsgWoyJu4AcyfH4MGhLA35-oNLPpiMgA0kBUWrPwcFDT6-CeygR4cOgCe2CDUiRwtVpPjes-i4bN0IclTKlMetAyB41kHyN1oLvvY_AdwcXPtMxO7IfEAEA/s1600-h/clip_image008%5B3%5D.png)

Mining API Usage Patterns

How should an API be used correctly?

*   An API may serve multiple functionalities --> Different styles of API usage

"I know what type of object I need, but I don't know how to write the code to get the object"

*   Can we synthesize jungloid code fragments automatically?
*   Given a simple query describing the desired code in terms of input and output types, return a code segement.

"I know what method call I need, but I don't know how to write code before and after this method call"

Relationships between Code Entities

*   Mine framework reuse patterns
    
    *   Membership relationships
        *   A class contains membership functions
    
    *   Reuse relationships
        *   Class inheritance / instantiation
        *   Function invocations / overriding

*   Mine software plagiarism
    *   Program dependence graphs

Program Execution Traces

Method-Entry/Exit States

Goal: Mine specifications (pre/post conditions) or object behavior (object transition diagrams)

State of an object: values of transitively reachable fields.

Method-entry state: Receiver-object state, method argument values.

Method-exit state: Receiver-object state, updated method argument values, method return value.

Other Profiled program states

Goal: detect or locate bugs.

Values of variables at certain code locations

Object/static field read/write

Method-call arguments

Method returns

Sampled predictions on values of variables

Executed Structural Entities

Goal: Locate bugs.

Executed branches/paths, def-use pairs.

Executed function/method calls.

Group methods invoked on the same object

Profiling options

Execution hit vs. count

Execution order (sequences)

Part II

How can you mine Software Engineering data?

Overview of data mining techniques

Association rules and frequent patterns

Classification

Clustering

Misc.

Association Rules

Example:

Finding highly correlated method call pairs.

Check the revisions (fixes to bugs), find the pairs of method calls whose confidences have improved dramatically by frequent added fixes.

Those are the matching method call pairs that may often be violated by programmers

Conflicting Patterns

999 out of 1000 times spin\_lock is followed by spin\_unlock

The single time that spin\_unlock does not follow may likely be an error.

We can detect an error without knowing the correctness rules.

Detect Copy-Paste Code

Apply closed sequential pattern mining techniques.

Customizing the techniques:

*   A copy-paste segment typically does not have big gaps.
    *   Use a maximum gap threshold to control.

*   Output the instances of patterns ( i.e., the copy-pasted code segments) instead of the patterns.
*   Use small copy-pasted segments to form larger ones.
*   Prune false positives: tiny segments, unmappable segments, overlapping segments, and segments with large gaps.

Find Bugs in Copy-Pasted Segments

For two copy-pasted segments, are the modifications consistent?

*   Identifier a in segment S1 is changed to b in segment S3 3 times, but remains unchanged once - likely a bug
*   The heuristics may not be correct all the time

The lower the unchanged rate of an identifier, the more likely there is a bug.

Mining Rules in Traces

Mining association rules or sequential patterns S --> F, where S is a statement and F is the status of program failure.

The higher the confidence, the more likely S is faulty or related to a fault.

Using only one statement at the left side of the rule can be misleading, since a fault may led by a combination of statements.

Frequent patterns can be used to improve.

Mining Emerging Patterns in Traces

A method executed only in failing runs is likely to point to the defect.

Comparing the coverage of passing and failing program runs helps.

Mining patterns frequent in failing program runs but infrequent in passing program runs.

Sequential patterns may be used.

Classification

Classification: A 2-step Process

Model construction: describe a set of predetermined classes

*   Training dataset: tuples for model construction
    *   Each tuples/sample belongs to a predefined class

*   Classification rules, decision trees, or math formulae

Model application: classify unseen objects

*   Estimate accuracy of the model using an independent test set.
*   Acceptable accuracy --> apply the model to classify tuples with known class labels.

Supervised learning (Classification)

*   Supervision: objects in the training data set have labels
*   New data is classified based on the training set

Unsupervised learning (Clustering)

*   The class labels of training data are unknown
*   Given a set of measurements, observations, etc. with the aim of establishing the existence of classes or clusters in the data.

GUI-Application Stabilizer

Given a program state S and an event e, predict whether e likely results in a bug

*   Positive samples: past bugs
*   Negative samples: not bug reports

A K-NN based approach

*   Consider the k closest cases reported before
*   Compare sum 1/d for bug cases and not-bug cases, where d is the similarity between the current state and the reported states.
*   If the current state is more similar to bugs, predict a bug.

Clustering

What is clustering ==> group data into clusters.

Similar to one another within the same cluster.

Dissimilar to the objects in other clusters.

Unsupervised learning: no predefined classes.

Clustering and Categorization

Software categorization

Partitioning software systems into categories

Categories predefined - a classification problem

Categories discovered automatically - a clustering problem

Software Categorization - MUDABlue

Understanding source code

*   Use Latent Semantic Analysis (LSA) to find similarity between software systems.
*   Use identifiers (e.g., variable names, function names) as features
    *   "gtk\_window" represents some window
    *   The source code near "gtk\_window" contains some GUI operation on the window.

*   Extracting categories using frequent identifiers
    *   "gtk\_window", "gtk\_main", and "gpointer" --> GTK related software system
    *   Use LSA to find relationships between identifiers

Other Mining Techniques

Automation/grammar/regular expression learning

Searching/matching

Concept analysis

Template-based analysis

Abstraction-based analysis