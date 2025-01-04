--- 
title: "Create a new Web Part Page with Quick Launch menu" 
date: '2013-07-17T10:20:00.001-05:00' 
tags: 
    - SharePoint 2010 
    - SharePoint Designer 2010 
modified_time: '2013-07-17T10:20:55.849-05:00'
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-3147025565333079798
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/07/create-new-web-part-page-with-quick.html
---

This post is about a simple task we do daily in SharePoint 2010,
creating a new Web Part page. Every time we need a new Web Part page, we
go to *All Site Content* &gt; *Create* &gt; *Web Part Page* &gt;
*Create*. Now we have a Web Part page but no quick launch menu on the
left.

To show the quick launch menu on the new created page:

-   Open the page for editing in SharePoint 2010.
-   Switch to the Code view.
-   Click on the Advanced Mode button on the ribbon.
-   Now look for the following code snippet and delete it.

> &lt;SharePoint:UIVersionedContent ID="WebPartPageHideQLStyles"
> UIVersion="4"runat="server"&gt;  
> &lt;ContentTemplate&gt;  
> body \# {s4-leftpanel  
> display: none;  
> }  
> . s4 {ca-  
> margin-left: 0px;  
> }  
> &lt;/ style&gt;  
> &lt;/ ContentTemplate&gt;  
> &lt;/ SharePoint: UIVersionedContent&gt;

-   Now look for the following snippet and delete it.

> &lt;asp:Content ContentPlaceHolderId="PlaceHolderLeftNavBar"
> runat="server"&gt;  
> &lt;/ asp: Content&gt;

-   Save and Close

Now when you open the page, the quick launch navigation will be there.
