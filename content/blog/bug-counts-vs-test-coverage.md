---
title: 'Bug Counts vs. Test Coverage'
date: 2009-02-05T05:31:00.003-06:00
draft: false
url: /2009/02/bug-counts-vs-test-coverage.html
---

**What to Do When Bug Counts Don’t Speak for Themselves?**

Bug counts on a project speak volumes about the quality of testing for a particular product and how vigorous the test team is working to "assure quality." Bug counts are invariably a primary area of test metrics that are reported to management. What is the rationale behind drawing so much attention to the number of bugs being found through the course of a project?  
I have heard it said that QE’s job is to find bugs. If this is the assumption of management, bug counts will be an important indicator to them that QE is doing its job. They expect to see bug counts rise dramatically in the early stages of testing, and they expect to see the find rate decrease as the project comes to an end. These are management’s statistical expectations when they believe bug counts are a metric to assess quality of testing.  
If high bug counts, then, are an indicator that quality is going up, low bug counts can be seen as an indicator that something just isn’t right with the testing process. Management might imagine different problems that are preventing bugs from being found:  
  

*   Test coverage isn’t complete; maybe major areas of functionality aren’t being tested.
*   Testing is only scratching the surface of all functionality, not digging in to the real complexities of the code.
*   Our testers just aren’t that good.

Management might see red flags when bug counts are low, but a number of causes may contribute to low bug counts. On the second or third iteration of a product, the bulk of the defects may have been found on an earlier cycle. Or especially good development practices may have been implemented: strong unit testing, code reviews, good documentation, and not working developers to death. These are supposed to result in lower bug counts.  
Ultimately, however, QE will justify low bug counts when it can justify its test coverage. If the product under test is being tested with thorough coverage, the bug count should be treated only as a supporting statistic, not the primary one. After all, **we all know that a quality product hasn’t been reached when a certain bug count is reached. Quality is achieved when test coverage is maximized and bug finds decrease to a minimum.**  
There are several things you can do when bug counts are low and management is questioning the quality of testing:  

1.  **Take stock**. Call a meeting with your test team, go through the areas of test, possibly even some test cases themselves, and get a general feel for how much test coverage you really have. Maybe you’ll discover that an area of test really is being missed. Perhaps there is some misunderstanding of who should be testing what and some functionality fell between the cracks. Brainstorm more testing methods and techniques, and generate ideas of how your team can broaden the testing efforts. Before going to other groups or departments, get a solid understanding of where your team is in the process.
2.  **Talk to development**. Go over your current test coverage with development, and see if they have any input on areas you might also investigate. Ask them what the trouble spots are, if they can suggest lower-level tests that may ferret out more bugs, and possibly even conduct a test case review with them. On my last project, we sent out the test cases of a certain functionality to the appropriate developer for review. Though many times developers can be reluctant to help testers, demonstrate to them that it is in their best interest that we thoroughly test their code—if it’s solid, they have nothing to worry about.
3.  **Communicate with management**. When bug counts are low, use test coverage to justify them. This doesn’t mean dismissing the fact that the bug count is low. It means using the bug count as an indicator to do some analysis into the testing practices you are doing, and verifying that high test coverage is being achieved. If it is, explain to management your findings. Demonstrate by solid metrics that you are performing thorough testing, that you can’t force bug counts to go up, and that maybe—just maybe—a low bug count means you’ve got a quality product on your hands!

One thing to bear in mind: while you can use the above methods during testing cycles to understand and cope with a low bug count, the ideas are still applicable before testing even begins, while test cases are being written for a project, and while development is still in full swing. Good test coverage is something to be planned ahead of time, and having gone through the effort of mapping coverage and functional test cases early in the project, you will prevent yourself from spending valuable testing cycles repeating tasks.  
While low bug counts can cause people in both development and management to question the effectiveness of the testing, do not be defensive about it. Use it as a trigger to prove what you should already know—your testing efforts are appropriate, effective, and your coverage is maximized. Don’t let your bug counts do the talking—your test coverage should say it all.