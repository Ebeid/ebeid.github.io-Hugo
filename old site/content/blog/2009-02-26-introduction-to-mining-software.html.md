--- 
title: "Introduction to Mining Software Engineering Data" 
date: '2009-02-26T08:55:00.001-06:00' 
tags: 
modified_time: '2009-02-26T08:55:31.220-06:00' 
thumbnail: http://lh6.ggpht.com/\_R1exOFT\_lVs/SaatQQs-jXI/AAAAAAAAABg/JHGSaAM4IkA/s72-c/clip\_image001\_thumb.png?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-5499474282686390104
blogger_orig_url: http://ebeid-soliman.blogspot.com/2009/02/introduction-to-mining-software.html
---

 

Tao Xie | North Carolina State University | <xie@csc.ncsu.edu>

Ahmed E. Hassan | University of Victoria | ahmed@uvic.ca

Part I

Mining Software Engineering Data goals:

-   Transform static record-keeping SE data to active data.
-   Make SE data actionable by uncovering hidden patterns and trends.

Uses of mining SE data:

-   Gain empirically-based understanding of software development.
-   Predict, plan, and understand various aspects of a project.
-   Support future development and project management activities.

[<img src="http://lh6.ggpht.com/_R1exOFT_lVs/SaatQQs-jXI/AAAAAAAAABg/JHGSaAM4IkA/clip_image001_thumb.png?imgmax=800" title="clip_image001" width="244" height="161" alt="clip_image001" />](http://lh3.ggpht.com/_R1exOFT_lVs/SaatPqA-b_I/AAAAAAAAABc/e5Pi6diYAjA/s1600-h/clip_image001%5B3%5D.png)

Types of SE Data:

-   Historical data

Used primarily for record-keeping activities (checking the status of a
bug, retrieving old code)

-   Version or source control:
    -   cvs, subversion, perforce.
    -   Store changes to the data

<!-- -->

-   Bug systems:
    -   bugzilla, GNATS, JIRA.
    -   Follow the resolution of defects.

<!-- -->

-   Mailing lists:
    -   Mbox
    -   Record rationale for decisions throughout the life of a project.

<!-- -->

-   Multi-run and Multi-site data
    -   Execution traces
    -   Deployment logs

[<img src="http://lh4.ggpht.com/_R1exOFT_lVs/SaatRTSYRkI/AAAAAAAAABo/neK6mmAdnRY/clip_image002_thumb.png?imgmax=800" title="clip_image002" width="244" height="175" alt="clip_image002" />](http://lh6.ggpht.com/_R1exOFT_lVs/SaatQ6t8yYI/AAAAAAAAABk/HSWWUsDklPg/s1600-h/clip_image002%5B3%5D.png)

Software Maintenance Activities

-   Perfective: add new functionality
-   Corrective: fix faults
-   Adaptive: new file formats, refactoring

Source Control Repositories

A source control system tracks changes to ChangeUnits.

Examples of ChangeUnits:

-   File
-   Function
-   Dependency (e.g. Call )

For each ChangeUnit, it tracks the developer, time, change message,
co-changing Units.

[<img src="http://lh5.ggpht.com/_R1exOFT_lVs/SaatSa5VBsI/AAAAAAAAABw/J1P1h_tum1U/clip_image003_thumb.jpg?imgmax=800" title="clip_image003" width="244" height="177" alt="clip_image003" />](http://lh6.ggpht.com/_R1exOFT_lVs/SaatR5gwbXI/AAAAAAAAABs/ZZipjyMgw1U/s1600-h/clip_image003%5B3%5D.jpg)

Change Propagation

[<img src="http://lh3.ggpht.com/_R1exOFT_lVs/SaatTw41ryI/AAAAAAAAACA/P_EVKn0kCZk/clip_image004_thumb.png?imgmax=800" title="clip_image004" width="244" height="135" alt="clip_image004" />](http://lh5.ggpht.com/_R1exOFT_lVs/SaatS7YDNaI/AAAAAAAAAB0/MtuxFhn-pH0/s1600-h/clip_image004%5B3%5D.png)

Measuring Change Propagation

[<img src="http://lh5.ggpht.com/_R1exOFT_lVs/SaatU9NH75I/AAAAAAAAACI/cCYXBBOVRbY/clip_image005_thu%0Amb.png?imgmax=800" title="clip_image005" width="244" height="44" alt="clip_image005" />](http://lh5.ggpht.com/_R1exOFT_lVs/SaatUdOdvJI/AAAAAAAAACE/rdvmvb70_hI/s1600-h/clip_image005%5B3%5D.png)

[<img src="http://lh4.ggpht.com/_R1exOFT_lVs/SaatV2HCvKI/AAAAAAAAACQ/8zo0oLlScYM/clip_image006_thumb.png?imgmax=800" title="clip_image006" width="244" height="48" alt="clip_image006" />](http://lh3.ggpht.com/_R1exOFT_lVs/SaatVW27xHI/AAAAAAAAACM/EZemx9UBL8Y/s1600-h/clip_image006%5B3%5D.png)

We want:

-   High precision to avoid wasting time
-   High recall to avoid bugs

Guiding Change Propagation

Mine association rules from change history.

Use rules to help propagate changes:

-   Recall as high as 44%
-   Precision around 30%

High precision and recall reached in &lt; 1mth

Prediction accuracy improves prior to a release (i.e., during
maintenance phase)

Code Sticky Notes

Traditional dependency graphs and program understanding models usually
do not use historical information.

Static dependencies capture only a static view of a system - not enough
detail!

Development history can help understand the current structure
(architecture) of a software system.

Studying Conway's Law

"The structure of a software system is a direct reflection of the
structure of the development team"

[<img src="http://lh5.ggpht.com/_R1exOFT_lVs/SaatW98LVMI/AAAAAAAAACY/PV5hEjse4jw/clip_image007_thumb.png?imgmax=800" title="clip_image007" width="244" height="120" alt="clip_image007" />](http://lh4.ggpht.com/_R1exOFT_lVs/SaatWYncpBI/AAAAAAAAACU/8UuHXSipFdo/s1600-h/clip_image007%5B3%5D.png)

Predicting Bugs

Studies have shown that most complexity metrics correlate well with LOC
! (Lines of Code)

Noteworthy findings:

-   Previous bugs are good predictor of future bugs.
-   The more a file changes, the more likely it will have bugs in it.
-   Recent changes affect more the bug potential of a file over older
    changes (weighted time damp models)
-   Number of developers is of little help in predicting bugs.
-   Hard to generalize bug predictors across projects unless in similar
    domains.

Example 1 : using imports in Eclipse to predict bugs

-   71% of files that import compiler packages, had to be fixed later
    on.
-   14% of all files that import ui packages, had to be fixed later on.

Example 2 : don't program on fridays

Percentage of bug-introducing changes for eclipse, most high in Friday.

Classifying changes as Buggy or Clean

Given a change can we warn a developer that there is a bug in it ?

-   Recall/Precision in 50-60% range.

Project Communication - Mailing lists

Most open source projects communicate through mailing lists or IRC
channels.

Rich source of information about the inner workings of large projects.

Discussion cover topics such as future plans, design decision, project
policies, code or path reviews.

Social network analysis could be performed on discussion threads.

Social Network Analysis

Mail list activity

-   Strongly correlates with code change activity.
-   Moderately correlates with document change activity.

Social network measures (in-degree, out-degree, between's) indicate that
committers play much more significant roles in the mailing list
community that non-committers.

Immigration rate of developers

When will a developer be invited to join a project?

-   Expertise vs. interest

The patch review process

Two review styles

-   RTC : Review-then-Commit
-   CTR : Commit-then-Review

80% patches reviewed within 3.5 days and 50% reviewed in &lt; 19 hrs

Measure a team's morale around release time

Study the content of messages before and after release.

Use dimensions from a psychometric text analysis tool.

Program Source Code

Code Entities

[<img src="http://lh4.ggpht.com/_R1exOFT_lVs/SaatYtPX6HI/AAAAAAAAACg/RswNhS-DBsI/clip_image008_thumb.png?imgmax=800" title="clip_image008" width="244" height="127" alt="clip_image008" />](http://lh5.ggpht.com/_R1exOFT_lVs/SaatXRFxCtI/AAAAAAAAACc/b36b_fM0Xz4/s1600-h/clip_image008%5B3%5D.png)

Mining API Usage Patterns

How should an API be used correctly?

-   An API may serve multiple functionalities --&gt; Different styles of
    API usage

"I know what type of object I need, but I don't know how to write the
code to get the object"

-   Can we synthesize jungloid code fragments automatically?
-   Given a simple query describing the desired code in terms of input
    and output types, return a code segement.

"I know what method call I need, but I don't know how to write code
before and after this method call"

Relationships between Code Entities

-   Mine framework reuse patterns
    -   Membership relationships
        -   A class contains membership functions

    <!-- -->

    -   Reuse relationships
        -   Class inheritance / instantiation
        -   Function invocations / overriding

<!-- -->

-   Mine software plagiarism
    -   Program dependence graphs

Program Execution Traces

Method-Entry/Exit States

Goal: Mine specifications (pre/post conditions) or object behavior
(object transition diagrams)

State of an object: values of transitively reachable fields.

Method-entry state: Receiver-object state, method argument values.

Method-exit state: Receiver-object state, updated method argument
values, method return value.

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

Check the revisions (fixes to bugs), find the pairs of method calls
whose confidences have improved dramatically by frequent added fixes.

Those are the matching method call pairs that may often be violated by
programmers

Conflicting Patterns

999 out of 1000 times spin\_lock is followed by spin\_unlock

The single time that spin\_unlock does not follow may likely be an
error.

We can detect an error without knowing the correctness rules.

Detect Copy-Paste Code

Apply closed sequential pattern mining techniques.

Customizing the techniques:

-   A copy-paste segment typically does not have big gaps .
    -   Use a maximum gap threshold to control.

<!-- -->

-   Output the instances of patterns ( i.e., the copy-pasted code
    segments) instead of the patterns.
-   Use small copy-pasted segments to form larger ones.
-   Prune false positives: tiny segments, unmappable segments,
    overlapping segments, and segments with large gaps.

Find Bugs in Copy-Pasted Segments

For two copy-pasted segments, are the modifications consistent?

-   Identifier a in segment S1 is changed to b in segment S3 3 times,
    but remains unchanged once - likely a bug
-   The heuristics may not be correct all the time

The lower the unchanged rate of an identifier, the more likely there is
a bug.

Mining Rules in Traces

Mining association rules or sequential patterns S --&gt; F, where S is a
statement and F is the status of program failure.

The higher the confidence, the more likely S is faulty or related to a
fault.

Using only one statement at the left side of the rule can be misleading,
since a fault may led by a combination of statements.

Frequent patterns can be used to improve.

Mining Emerging Patterns in Traces

A method executed only in failing runs is likely to point to the defect.

Comparing the coverage of passing and failing program runs helps.

Mining patterns frequent in failing program runs but infrequent in
passing program runs.

Sequential patterns may be used.

Classification

Classification: A 2-step Process

Model construction: describe a set of predetermined classes

-   Training dataset: tuples for model construction
    -   Each tuples/sample belongs to a predefined class

<!-- -->

-   Classification rules, decision trees, or math formulae

Model application: classify unseen objects

-   Estimate accuracy of the model using an independent test set.
-   Acceptable accuracy --&gt; apply the model to classify tuples with
    known class labels.

Supervised learning (Classification)

-   Supervision: objects in the training data set have labels
-   New data is classified based on the training set

Unsupervised learning (Clustering)

-   The class labels of training data are unknown
-   Given a set of measurements, observations, etc. with the aim of
    establishing the existence of classes or clusters in the data.

GUI-Application Stabilizer

Given a program state S and an event e, predict whether e likely results
in a bug

-   Positive samples: past bugs
-   Negative samples: not bug reports

A K-NN based approach

-   Consider the k closest cases reported before
-   Compare sum 1/d for bug cases and not-bug cases, where d is the
    similarity between the current state and the reported states.
-   If the current state is more similar to bugs, predict a bug.

Clustering

What is clustering ==&gt; group data into clusters.

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

-   Use Latent Semantic Analysis (LSA) to find similarity between
    software systems.
-   Use identifiers (e.g., variable names, function names) as features
    -   "gtk\_window" represents some wi ndow
    -   The source code near "gtk\_window" contains some GUI operation
        on the window.

<!-- -->

-   Extracting categories using frequent identifiers
    -   "gtk\_window", "gtk\_main", and "gpointer" --&gt; GTK related
        software system
    -   Use LSA to find relationships between identifiers

Other Mining Techniques

Automation/grammar/regular expression learning

Searching/matching

Concept analysis

Template-based analysis

Abstraction-based analysis
