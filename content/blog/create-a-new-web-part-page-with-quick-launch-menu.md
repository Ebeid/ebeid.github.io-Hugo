---
title: 'Create a new Web Part Page with Quick Launch menu'
date: 2013-07-17T10:20:00.001-05:00
draft: false
url: /2013/07/create-new-web-part-page-with-quick.html
tags: 
- SharePoint 2010
- SharePoint Designer 2010
---

This post is about a simple task we do daily in SharePoint 2010, creating a new Web Part page. Every time we need a new Web Part page, we go to _All Site Content_ > _Create_ > _Web Part Page_ \> _Create_. Now we have a Web Part page but no quick launch menu on the left.

To show the quick launch menu on the new created page:

*   Open the page for editing in SharePoint 2010.
*   Switch to the Code view.
*   Click on the Advanced Mode button on the ribbon.
*   Now look for the following code snippet and delete it.

> <SharePoint:UIVersionedContent ID="WebPartPageHideQLStyles" UIVersion="4"runat="server">  
> <ContentTemplate>  
> body # {s4-leftpanel  
> display: none;  
> }  
> . s4 {ca-  
> margin-left: 0px;  
> }  
> </ style>  
> </ ContentTemplate>  
> </ SharePoint: UIVersionedContent>

*   Now look for the following snippet and delete it.

> <asp:Content ContentPlaceHolderId="PlaceHolderLeftNavBar" runat="server">  
> </ asp: Content>

*   Save and Close

Now when you open the page, the quick launch navigation will be there.