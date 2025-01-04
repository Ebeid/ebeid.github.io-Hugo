---
title: 'Bring “Sign in as Different User” back to SharePoint 2013'
date: 2013-07-23T17:36:00.001-05:00
draft: false
url: /2013/07/bring-sign-in-as-different-user-back-to.html
tags: 
- SharePoint 2013
---

If you new to SharePoint 2013 like me and get confused looking for “Sign in as a Different User” menu command, don’t worry it is not there by design but we can easily bring it back.

Do the following steps to get the link back:

*   Locate the file \\15\\TEMPLATE\\CONTROLTEMPLATES\\Welcome.ascx and open it for editing.
*   Add the following snippet before the existing element that have id of “ID\_RequestAccess”.

```
  
 Text="<%$Resources:wss,personalactions\_loginasdifferentuser%>"  
 Description="<%$Resources:wss,personalactions\_loginasdifferentuserdescription%>"  
 MenuGroupId="100"  
 Sequence="100"  
 UseShortId="true"  
 />
```  

Save and close the file. Now you should get the link “Sign in as Different User” back.