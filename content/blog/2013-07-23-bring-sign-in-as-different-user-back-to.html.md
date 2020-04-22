--- 
title: "Bring “Sign in as Different User” back to SharePoint 2013"
date: '2013-07-23T17:36:00.001-05:00' 
tags: 
    - SharePoint 2013
modified_time: '2013-07-23T17:40:45.250-05:00' 
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-3596697447652063456
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/07/bring-sign-in-as-different-user-back-to.html
---

If you new to SharePoint 2013 like me and get confused looking for “Sign
in as a Different User” menu command, don’t worry it is not there by
design but we can easily bring it back.

Do the following steps to get the link back:

-   Locate the file \\15\\TEMPLATE\\CONTROLTEMPLATES\\Welcome.ascx and
    open it for editing.
-   Add the following snippet before the existing element that have id
    of “ID\_RequestAccess”.

<!-- -->

     Text="<%$Resources:wss,personalactions_loginasdifferentuser%>"
     Description="<%$Resources:wss,personalactions_loginasdifferentuserdescription%>"
     MenuGroupId="100"
     Sequence="100"
     UseShortId="true"
     />

  

Save and close the file. Now you should get the link “Sign in as
Different User” back.
