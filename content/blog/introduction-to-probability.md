---
title: 'Introduction to Probability'
date: 2013-02-01T16:55:00.000-06:00
draft: true
url: 
tags: 
- Propability
- Statistics
---

### 1 - What is probability ?

There is three different interpretations of probability :

1.  The Frequency Interpretation of Probability : The probability that some specific outcome of a process will be obtained can be interpreted to mean the **_relative frequency_** with which that outcome would be obtained if the process were repeated a large number of times under similar conditions. In this case probability is based on history.

1.  what exactly large number means ?
2.  what “under similar conditions” really means ?
3.  relative frequency is not precise ! 
4.  Applicable only when a large number of similar repetitions of a certain process is available.

3.  The Classical Interpretation of Probability : The probability is based on the concept of **_equally likely  
    outcomes_**. If the outcome of some process must be one of n different outcomes, and if these n outcomes are equally likely to occur, then the probability of each outcome is 1/n.  For example, when a coin is tossed, there are two possible outcomes: a head or a tail. If it may be assumed that these outcomes are equally likely to occur, then they must have the same probability. Since the sum of the probabilities must be 1, both the probability of a head and the probability of a tail must be 1/2. More generally.

1.  The concept of equally likely outcome is based on the concept of probability (which we are trying to define) ![Open-mouthed smile](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiyaDhyR1ONvxi4wzosG-8ZfUXBWtlf7gWG57gmDMJRTx6RS9F3WmvHPqZcpQIAKpHBLj6NsO2Xs_b0zjK9jv7U1IkGbVD0SYDvto47sC99ZxfnJJw5G5xRt0tAUP9Fq1Ki4Gk-GVcXKQ/?imgmax=800)
2.  No systematic method is given for assigning probabilities to outcomes that are not assumed  
    to be equally likely.

5.  The Subjective Interpretation of Probability : The probability that a person assigns to a possible outcome of some process represents his/her own judgment of the likelihood that the outcome will be obtained. This judgment will be based on each person’s beliefs and information about the process. Another person, who may have different beliefs or different information, may assign a different probability to the same outcome. For this reason, it is appropriate to speak of a certain person’s subjective probability of an outcome, rather than to speak of the _true_ probability of that outcome.

It’s good to know that the mathematical theory of probability does not depend on the above interpretations ![Smile with tongue out](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh4HRt20FnEXvXWnHXmKw_E823-p6Cw9H89Jk2qnAhEGB7yVD3FwMnDn4o55Le_5HCjsaM1CJ620OLav-jYw7fDEEFYmCmFllYkgwFd0QeME9_K2FS0QO7xFdjKU2bfv9kPpNTGrKc9EQ/?imgmax=800)

### 2 - Experiments and Events

The theory of probability pertains to the various possible outcomes that might be obtained and the possible events that might occur when an experiment is performed.

*   An **_experiment_** is any process, real or hypothetical, in which the possible outcomes can be identified ahead of time.
*   An **_event_** is a well-defined set of possible outcomes of the experiment.

A common type of hypothetical experiment is repeating a well-defined task infinitely often under similar conditions (dice, coin, inspecting products in a manufactory, measuring temperature,…)

### 3 - Set Theory

The formal mathematical model for events named the theory of sets.

*   The collection (set) of all possible outcomes of an experiment is called the _**sample space**_ of the experiment. Each outcome can be thought of as a _point_, or an _element_, in the sample space. Events can be thought of as _subsets_ of the sample space.

*   For an experiment of rolling a six-sided dice, the sample space **S** = {1,2,3,4,5,6}
*   Each possible outcome **s** of the experiment is a member of the sample space s [![Probability_and_Statistics - 4th.pdf - Adobe Reader_2013-02-06_15-11-05](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhCUsfR5gIjkzw9Ij9ypppH_LTvcJKbSU89i6qMcymQoSU7qfP7O-9lpFLATJrJD6gThlTXLkVXUvSEK_TVse5AGvwGS6RzS-mrgA9VwcIuNqbBRw4L-T9UrPDvJcKouwpIwxe6IiCm_g/?imgmax=800 "Probability_and_Statistics - 4th.pdf - Adobe Reader_2013-02-06_15-11-05")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhw1tiHIZodJvyc2HJF1jUOfQxR1XjZXJm345RRgzBCqe7uCVssfrfSKy-utt37TRT1qozG8zo4slt0TB574Qm22KCTZw3g1tAPN5rHEF5Gqm6IKFWlLE-QxAPZmBoHLCTOmy-UtgOMEQ/s1600-h/Probability_and_Statistics%252520-%2525204th.pdf%252520-%252520Adobe%252520Reader_2013-02-06_15-11-05%25255B3%25255D.jpg)S
*   One event A could be that an even number is obtained, it can be represented as the subset A = {2,4,6}

*   It is said that a set A is _**contained**_ in another set B if every element of the set A also belongs to the set B. This relation between two events is expressed symbolically by the expression A [![Probability_and_Statistics - 4th.pdf - Adobe Reader_2013-02-06_15-20-39](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjlBAxqDgox9RdhvU79nShtHMfl4kPB2ZAYZ9AE4iFEdn7BRk5Bih7FrILrBgGftPTcrf-PhgUzURTrPv1HG0QmKgexEODAIo84xFSiIueEnqoQSTYvK9Wv2iJa6oemy5O7ACwtz17OZg/?imgmax=800 "Probability_and_Statistics - 4th.pdf - Adobe Reader_2013-02-06_15-20-39")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiAEpWd0_q_vcg8zd3X3EmY_eMyrYY2vh9UBBlwCjwNkHfuR595YxNGgeUU9XVZcvtypUyJJDHeu8fhGPLuOseZdX_rSFMl5VFue5S-a6k_UHEG-MP8iKBynVQqzG6E4RptD5QIDcBekw/s1600-h/Probability_and_Statistics%252520-%2525204th.pdf%252520-%252520Adobe%252520Reader_2013-02-06_15-20-39%25255B2%25255D.jpg) B. All events are subsets of **S**. \[If A is subset of B, B subset of C, then A is subset of C\]
*   Some events are impossible (getting a negative number from a dice); which defined as **_Empty set_** [![Probability_and_Statistics - 4th.pdf - Adobe Reader_2013-02-06_15-24-09](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhr-qsvpoXtqS09cDGO9tMr7YFoVd2FHGTSJuEs8rb0tdEZdEf4LthW-UCkGrxr3QYqRq8bnWsq7FuG7czSpW6QtS1bbXloPA_1g__4N-4DfeOPJznPGdmsRzRekSmF1TwLZ6qaT1wCCA/?imgmax=800 "Probability_and_Statistics - 4th.pdf - Adobe Reader_2013-02-06_15-24-09")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjLpGz35sIXNiBYjhVGsJ53hKipZIlXKi67zcL8k9FFsZufh9990ZaR5oZayGiSD-TtJ6lCWeWzsnGoWmmrbAS54Q6F7VWn7R6nvR45Qq9N8kv_yjaCS617dV8b9N5q-zlCKF8lFNTF-w/s1600-h/Probability_and_Statistics%252520-%2525204th.pdf%252520-%252520Adobe%252520Reader_2013-02-06_15-24-09%25255B2%25255D.jpg).  \[Empty subset is subset of any event\]
*   There is finite sets and infinite sets.
*   Set operations :

*   **Complement**. The complement of a set A is defined to be the set that contains all  
    elements of the sample space S that do not belong to A.

[![18_05_lec1.pdf - Adobe Reader_2013-02-06_15-28-54](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiG1CfwSZY3EFGLR2J_2ayAZ5OuvNb3JaAFInX1rp6V2MpO6LtxALpSSSZ92sbG2pMqbjspuc5se_h5Y6WxZS3xvYf1qJCFpbiv4j0xWnX6SczPVlSE3lBWvSPysFz-cf4dnlgYuxZ7gg/?imgmax=800 "18_05_lec1.pdf - Adobe Reader_2013-02-06_15-28-54")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhs25wtJ8SR_eGXq9ioOLABnlnR1P4LbacYQuSEuzn41cuq_eRfUUZUvcj7KW8FThndo7AdAX9oCk6xKikFSW5i6I19sjEpwj80FT1TMo3GGmqwSGUsYvdOaCrZXxio21E8XkHDY7T2AQ/s1600-h/18_05_lec1.pdf%252520-%252520Adobe%252520Reader_2013-02-06_15-28-54%25255B3%25255D.jpg)

*   **Union of Two Sets**. If A and B are any two sets, the union of A and B is defined to be the set containing all outcomes that belong to A alone, to B alone, or to both A and  
    B. The concept of union extends to more than two sets.

[![18_05_lec1.pdf - Adobe Reader_2013-02-06_15-31-50](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhbfw15iGrsd01RWXDqnSp_nBkQzrq-8MYwtpZgVAoSYRV5ddMbsmrBpyVvZfR8HXnwRsxY2QNpxDNGhY7wAL2hVgEnLis2cgFwriKRgNvhHMYZUvXhTT_c5hyBD8xuO4L1Po3paEnagw/?imgmax=800 "18_05_lec1.pdf - Adobe Reader_2013-02-06_15-31-50")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg8H0F536a8eW4usyXXyHCWE_nz_ErfIBJK6nXCXFmA9pCn9ksxf42Byij3RfQgoiF45bvkCfuVX0Czn8-jOqYy7BH1YyjAiCv9HPyFhl11MEg45_5lJCeWnoP-Ug9CktkLxrPyQjtbkA/s1600-h/18_05_lec1.pdf%252520-%252520Adobe%252520Reader_2013-02-06_15-31-50%25255B3%25255D.jpg)

*   **Intersection of Two Sets**. If A and B are any two sets, the intersection of A and B is defined to be the set that contains all outcomes that belong both to A and to B. Sets are disjoint or mutually exclusive if they don’t have any outcomes in common.

[![18_05_lec1.pdf - Adobe Reader_2013-02-06_15-34-59](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhSv8YuZsbQ7IrT_9HWVHoCR2L4CXYI4bFmaEw39pXHm_t_GcRg32_way-Bh3YtUOjgZGXJMEwRgU_MHj65xZtc5LLGPRlINfZwLIL78uZi8okNz0fQwJbpTm77f9Fz8AaHwJVYGfZkKQ/?imgmax=800 "18_05_lec1.pdf - Adobe Reader_2013-02-06_15-34-59")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjCWcXavcvWz05ObScW6BjFuKLDshtU4m949RYyEjfK-23vm_5UYfCTaWbW9lHbAfgETGi6qcRNH4S6I3RRVVpmp3v6l0ehwuBlFjecv3GjciEoMzbYQJOOsbCVATwpibWHBhROJlI0ww/s1600-h/18_05_lec1.pdf%252520-%252520Adobe%252520Reader_2013-02-06_15-34-59%25255B3%25255D.jpg)

*   **Difference**. If A and B are any two sets, A difference B is defined to be the set that contains all outcomes that belong to A but not to B.

[![18_05_lec1.pdf - Adobe Reader_2013-02-06_15-41-31](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhT4j_8yT2FMwU-BGRBqnG3h_wrTKUViso-Nzz5wyl5mYLmJnTesdhpami4z7zkvA-DfFclw2mSRt78YVLMf-xdJnSGfeWrn7AhXQNqFcNlTWb4gwOrRFsRMKJi0BUzUY_bQvaNnzTnVg/?imgmax=800 "18_05_lec1.pdf - Adobe Reader_2013-02-06_15-41-31")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiXtgdMC7B5oRNA7G9Q5JqxvUoWgQ2ycpSi4DHxYj1FcSv-KjIHyttjJwrARFa3SecdcYDpNy9bwbG7aokRW4VvDbGHC0NKHcGttGbEufPzPDmHPmmpKUQqAV1v3p4LC2tR2O1Ii2c_KA/s1600-h/18_05_lec1.pdf%252520-%252520Adobe%252520Reader_2013-02-06_15-41-31%25255B4%25255D.jpg)

*   **Symmetric Difference**. If A and B are any two sets, the symmetric difference is defined to be the set that contains all outcomes that belong to A or B but not both of them.

[![18_05_lec1.pdf - Adobe Reader_2013-02-06_15-44-59](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiq8rWhwleCAEjvcXI8gWhT5qdPEn616zYzDLtqJsmOY8306gqOLoLbiLqaRj2PRWX99gjaYOAFkp9yAdj0Oc6epGmWyenvSMUVY0eDv0nbf2SiA_wYtOOAo5ApDqEkVjNTfJCGp6l9bQ/?imgmax=800 "18_05_lec1.pdf - Adobe Reader_2013-02-06_15-44-59")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiqT7_VdyoOQuoh2fofTOfrbqdgLJeVA9wtfqQO6wTfWGtGBAXaqyccvzy5zWAYP8AaTJmwtcYYH87EftGyeD56p7g2geAE2-xxCGpXSoFgerbl2863yBCDZ_2AGztyg2374btniig7MQ/s1600-h/18_05_lec1.pdf%252520-%252520Adobe%252520Reader_2013-02-06_15-44-59%25255B4%25255D.jpg)

*   **Properties of Set Operations** :

[![18_05_lec1.pdf - Adobe Reader_2013-02-06_16-21-10](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi5ijmJa612T0QMmPlz6x_26ZmVJXKTGURaaqmu9R7KuqRxkjtdwt6RN6eefErM_6R4-ASpocqki3IBkM0H_xHVqSjXJMS2Or2NLIKELIziW5OMu7K7d-J99daWJM03aLym-r_bvH2nfg/?imgmax=800 "18_05_lec1.pdf - Adobe Reader_2013-02-06_16-21-10")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjL3P2yl1Qe2XUlcd6t-P1AAZaZ8aOmtq-_OFckAiKaicobgTPjKb0h-E6_TRXLAoAIk0CnFC_9q8F5DCNJ7PuskFoxgfjwfq-37IdQPeGUuQQsV-OwtcIHZQ1o-uvOdqqdwc2lsD5e4Q/s1600-h/18_05_lec1.pdf%252520-%252520Adobe%252520Reader_2013-02-06_16-21-10%25255B10%25255D.jpg)

### 4 - The Definition of Probability

Axioms and basic theorems:

*   The probability of every event must be nonnegative. For every event A, 1 ≥ Pr(A) ≥ 0.
*   If an event is certain to occur, then the probability of that event is 1 Pr(S) = 1.
*   For disjoint (mutually exclusive) events A, B : P(A or B) = P(A) + P(B). This can be written for any number of events.

*   [![Probability_and_Statistics - 4th.pdf - Adobe Reader_2013-02-06_17-10-08](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgOyMp_vA4ifpmiA69M6dNtoouU2g9ZVRXKoAdZP4G60CcNC8ymp604peWz5yyxga9nypm6X1cmEb0aQRS4c9z7c9pzse4dBMK9H6fvAD-5QpcRmfSLEz9qhc63vqu_L737Z8YmAn4KOA/?imgmax=800 "Probability_and_Statistics - 4th.pdf - Adobe Reader_2013-02-06_17-10-08")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi3Zcx9lirGDIjID_y-8m2xBw9iVgCF-gFFSX7xa37vQrOF8BmHoTUQu6ojcvKl0RK_SGcMW1UTU10MSr0RXbwb5C8tTfWaWtez4Egwc6cjIG-TLMyMQkTTs8F6UJSR5xAxhFoaPJbujQ/s1600-h/Probability_and_Statistics%252520-%2525204th.pdf%252520-%252520Adobe%252520Reader_2013-02-06_17-10-08%25255B3%25255D.jpg)

*   Pr([![Probability_and_Statistics - 4th.pdf - Adobe Reader_2013-02-06_15-24-09](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEimA05s0XuHfVfUZDN2kRNhahIPpPaT4Jwf26SeJAdAjWMu37hL3t2hYZV74bYS6p3h9sVfQDGaPyUXiUvyWcXSwhOh_ZAMFL7fgguC-sXMivYZp8V4wiSV4CS9p3Nry_EkXojPRLeQLA/?imgmax=800 "Probability_and_Statistics - 4th.pdf - Adobe Reader_2013-02-06_15-24-09")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgIW6qLybynnpgVHf99ppiV_iw8MeKi88CECMPNQdo9aatEKAMPcI2U7fI46QEuOidFN38TgQoYQzdrERt2zMYp7ZQgwi3tHxrTxMSxr5Rj_XlB0G0qYkCwiiqBBqJ03p1b-wO9TNCetg/s1600-h/Probability_and_Statistics%252520-%2525204th.pdf%252520-%252520Adobe%252520Reader_2013-02-06_15-24-09%25255B5%25255D.jpg)) = 0
*   Some properties of probability

[![Probability_and_Statistics - 4th.pdf - Adobe Reader_2013-02-06_17-17-11](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjFJo-W9UgR1dOVHMTUlPOCJ6YxDn0Rk_wW9sx_nxJU49NbJpXqdKMda3GorR-DWMyWdJVgDVL5qlGkcD8gcSBnThBosp4_C6SWCfBbwWJUJi60y4_ZJvBNQpmcUMQeZR790Cc2DFZQeg/?imgmax=800 "Probability_and_Statistics - 4th.pdf - Adobe Reader_2013-02-06_17-17-11")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhYIx88NdEnBVsaRfjSdOG1BhphuB368DrS3ZOLSdh2iC4Ya4hJrewS2lmXO9bkqGP8E7_Trq6j6KpPjNXM4mBo_hZVJUMhXleUMNdyhrpPIPrQd3rGZf_lZX0vVLnwx3Gi5obyVOwhIA/s1600-h/Probability_and_Statistics%252520-%2525204th.pdf%252520-%252520Adobe%252520Reader_2013-02-06_17-17-11%25255B3%25255D.jpg)

### 5 - Simple Sample Spaces

A sample space S containing n outcomes s1, . . . , sn is called a simple sample space if the probability assigned to each of the outcomes s1, . . . , sn is 1/n. If an event A in this simple sample space contains exactly m outcomes, then Pr(A) = m / n

### 6 - Counting Methods

In simple sample spaces, one way to calculate the probability of an event involves counting the number of outcomes in the event and the number of outcomes in the sample space. In this section we will try to get a method to determine the total number of outcomes in the space S and in various events in S without compiling a list of all its outcomes.

**Multiplication Rule**. Suppose that an experiment has k parts (k ≥ 2), that the ith  
part of the experiment can have ni possible outcomes (i = 1, . . . , k), and that all  
of the outcomes in each part can occur regardless of which specific outcomes have  
occurred in the other parts. Then the sample space S of the experiment will contain  
all vectors of the form (u1, . . . , uk), where ui is one of the ni possible outcomes of part  
i (i = 1, . . . , k). The total number of these vectors in S will be equal to the product  
n1n2 . . . nk.

8 - Combinatorial Methods

9 - Multinomial Coefficients

10 - The Probability of a Union of Events

11 - Statistical Swindles