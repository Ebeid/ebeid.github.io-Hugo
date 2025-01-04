---
title: 'Microsoft Dynamics CRM 2011 for Developers | Web Resources Part 1'
date: 2012-03-11T06:10:00.001-05:00
draft: false
url: /2012/03/microsoft-dynamics-crm-2011-for.html
tags: 
- Microsoft Dynamics CRM Dashboards
- Microsoft Dynamics CRM Solution Configuration Page
- Microsoft Dynamics CRM Forms
- Web Resources
- Microsoft Dynamics CRM SiteMap
---

#### **Contents**

1.  Introduction
2.  Types of Web Resources
3.  Where can Web Resources be Used ?
4.  Web Resources Limitations
5.  Web Resources Management
6.  Using Web Resources on a Form
7.  Using Web Resources from the Form Navigation 
8.  Using Web Resources on a Dashboard
9.  Using Web Resources Direct from SiteMap  
10.  Using Web Resources as a Solution Configuration Page
11.  Referencing Other Web Resources

**Introduction**

Web resources are a new feature of Dynamics CRM 2011 that allows storing of client side content in the CRM server database in order to be used for extending the Dynamics CRM web application. That content is then available to be delivered to users as needed during their interaction with the user interface. These resources can be used by URL, which also allows relative path referencing.

Based on that and using the appropriate development tools, a fully functional web site can be created on a development server by using file types that are compatible with web resources. Then, if using a consistent naming convention and relative path references, the web site will function after uploading all the files into Microsoft Dynamics CRM. These web resources can then be exported in a solution and installed on any Microsoft Dynamics CRM deployment (both on-premises and on-line). It will also available to users of Microsoft Dynamics CRM for Microsoft Office Outlook with Offline Access when offline because they are synchronized with the user’s data.

**Types of Web Resources**

Microsoft Dynamics CRM allows ten types to create web resources which fall into seven type categories. We will explore them here:

*   **HTML Web Pages** You can upload \*.htm or \*.html files as web resources, or you can use the Text Editor in the CRM interface to create your HTML web resources. Web pages can’t contain any code that must be executed on the server (no ASP.NET support). Web pages can only accept one custom query string parameter called _data._
*   **Images** You can upload PNG, JPG, GIF, and ICO files. They can be used as icons for custom ribbon controls or Sitemape subareas, decoration for entity forms and web pages, background images.
*   **Script** Enables uploading JScripts for reuse of many parts in the CRM like web page, ribbon commands, or form and field-level events.
*   **Style Sheet** .css files linked to web page web resources to efficiently manage their appearance.
*   **Data** Enables you to upload some XML files to your system
*   **Style Sheet** enables you to upload \*.xsl and \*.xslt files to be used by Data and Web Page web resources, so you can apply the style on XML files.
*   Silverlight enables you to upload \*.xap files which is the output of Silverlight application build process. Silverlight applications can be used on forms to create a more rich and visual components for users.

**Where can Web Resources be Used ?**

All web resources (except XML, XSL, XSLT, CSS) can be used on forms, on dashboards, from SiteMap, or from the application ribbon. All web resources can be used in the context of Web Page web resources.

**Web Resources Management**

Web resources can be created in the context of any unmanaged solution inside a CRM organization.

If you will create the web resource in the default solution navigate to Settings > Customizations > Customize the System > click on Web Resources from the left navigation > New. Enter the Name, Display Name, and select the web resource type. If you will create the web resource in a default solution other than the default solution, Settings > Customizations > Solutions > and click your solution and complete in the same steps as above.

After uploading a new or updating web resource, you have to publish the web resource before you use it in the application.

You can remove an unmanaged Web Resource at any time as long as it is not currently being by any component. If you attempt to remove a web resource while it is in use by another component you will get an error message.

> Web Page web resources are the container that can host (or link to) all the other web resource types, so we will explain all the ways to incorporate Web Page web resources in Dynamics CRM. Then we will explain how to link and integrate other types of web resources.

In order to proceed, we will create a simple "Hello World" page and upload it as a web resource. Create a simple page.html file like the following:

[![page](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi7Ppmn0pZAQYYwHPaqGPRMGA42K2y71yHcsc2xVFOLVFpJGdqzvGpMX2Ixg4w8bR44FH1TvD9tmN75YwQZSFzehBgBiIxTmMlTotvNIu30Tyww2SVVmdgY4pPyE_WthTL3JukfaGu2Vw/?imgmax=800 "page")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi5ZkdhxqBVzfDq2ENyY2qtRcB6v2y_9uy6miRGurA3PWzDqaAponuXFZRA80g8Y8kIszOIEAMfouE2WN1xSO_IoE2q9bM5K2WVRNSucfnYSy-_kYCF-WvuUj-oJuDF94A0TNX3CimZUQ/s1600-h/page3.jpg)

Now open your browser and navigate to your CRM organization, then navigate to Settings > Customizations > Customize the System > click on Web Resources from the left navigation > New. Enter a Name for our page, Display Name, and select Web Page (HTML) from the Type combo box. Click Save, then click Publish, then close the window.

[![Web Resource New](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgwqzjfZe75Thyphenhyphen1zKMtzjOT51SDZN_m1hTAdFlvBR_EZwdqPeXvdAvwKG2PbQXwYI9GNB6r16bXElP6AhqcmRXJ5JAyKfuxs3b2VzkWqVg4-w0bIalOxp8H93moF7WDcf9YIuNXHu6Lew/?imgmax=800 "Web Resource New")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjQBnYonKJzYvMGtJ7RJYnPNJ6EVH-Qd4e8MFDslKACQoo49adaqLk6uFFjfydQjq-LLOtVmxpFBcPkZfT3_3mrdEv660miquOMclDMY7xUCKkdoiXsjQ_aZZzb3feAVgUbjHM8AfEjYw/s1600-h/Web-Resource-New4.jpg)

Now we create a simple web page web resource and ready to explore the different ways to use it in our Dynamics CRM. We will explore just the basic usage scenarios, advanced features will be explained in a future post.

**Using Web Resources on a Form**

Now let's put use our test HTML page web resource on a Form, e.g. Account. Navigate to Settings > Customizations > Customize the System > from the left navigation expand Entities, then expand Account, then expand Forms, then click on the form named Information which have Main in the Form Type column. The form designer will open. Just to make things easier for you, collapse the regions on the form (called tabs in Dynamics CRM) by clicking the small blue rectangle on the left-top corner of each of them. Then Click on Insert in ribbon

 [![insert](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEisCFqWUAIA8Ci0P1FozNqYjwLG3LuJ6g-5mynSY-TV6c5PdbOjy3p-1pC4awVPqbHKR90xFO_U4Zl-E4Y93t7Lf_rT3Z3Gel9CsN2dzQOMK24KNnVcXp-_ZI3pIvrqkMjj-qq9J1d5pQ/?imgmax=800 "insert")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhRQl1sPdgTmghBHckL6TmcdqylLYHct8BL0FXkbs88TyRr0RiodjRPBCaqdV-iM_-TaeACkW98KB33OoHPxJVaMoajwondZj271epbJ_zNeVkNb1DenFRZKRpIoLqLtgEcxT9Is-1lAA/s1600-h/insert2.jpg)

Then click One Column on the ribbon.

[![one column tab](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiAsephr1BUqoYi6AOW62NRuEl_wVg9QCGDBUNzEMm_rZAWcEze4wt4kfRsLBuCeut1K3WSc3Ltw90LrSZnXdCANVGoDmqlQH9oBjRHtRFRSIE8q1iX7AgKNKLMouhKpXGQaR3nJXtnxA/?imgmax=800 "one column tab")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjQ-ySNfT1R2dHOhNYPJ1ZjrXmxQ2nClbz67z16ZOUc6MxWm-fXISaPCF7cTdYYsjiUQm1qq-_baXUJdGjfTJCkE_kpAgTAAZBsb7W7yeGStyvdc2HRLyldQQfxo6aegZvCNph3oG2h8Q/s1600-h/one-column-tab2.jpg)

This will insert a one column region (called Tabs in Dynamics CRM) below the currently selected region.

[![new tab](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjadh_2Faah9R3tzktSlWTkGSlAWsq4IkaCSRKprfnTl17iuP-b2513KyPaEfLO30jF8bNVL4C37-KiHz5CNz7MIjfQ-EUFk_iwcuR2qNo6N7qwRNXVmw5cevW2-gd3R9bFhr84UFnvVA/?imgmax=800 "new tab")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi5o9nkMQW2NASCZrJhP_SuzQ4siXOuagE1yS-JEsbnju-x_QhKUvv3jMkGIzDUQ63kXbNiNYt-aC35jz6RLDUsBc88tVvuBaRaZeUgxw8n7AKWVPSKSrOyDAGt-h5H1AvEPimG0gBjcw/s1600-h/new-tab2.jpg)

While your new region is selected, click Web Resource on the ribbon. [![new WR ribbon](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhsigbLbLGCJJzEXFlantq5emMLhlaujX5u89ivvb0calcPzfM9wyWwqVC43pa3L-eguwLXT6spOHDiiZd1a9Z2Cx3146NLtvLOhP9hhAVbv2iUyQFP2n74S7jFSz0SQ3ZYxhaXKakK9g/?imgmax=800 "new WR ribbon")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjcpFrh9PiA7jzEo77e79Km8vGE85_8FUrvmZalL46-N0cJpEd_yxf1gLp5wbTeVpydemtn-NExbATkAWnZwYjuajqLth6lmsB7dtLsYq34QjZEfke_Rq2bbKVDwh_d16Iel_Te9Oeaig/s1600-h/new-WR-ribbon2.jpg)

This will open the Add Web Resource dialog. In the Web Resource textbox click the look-up icon on the right and select our Web Page web resource from the list (you can also search for it by name). Fill the required Name and Label fields, and click Ok.

[![Add Web Resource - filled](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiwJmfkaBQFTtP45TlPJg8vm2g3sgXQjms3vzMrQ_Tf0NyhaHW88fejm7K9eiHbulXYmdkxKSWQQZyx9nsyoDsZwRNNw8loESr7qXh1xY_tz8TlcZ_6UHQN3J32qNDo5v6q9VDfREIQVw/?imgmax=800 "Add Web Resource - filled")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh-CnLwW8a-x7C7jl8DbMs8q5Z49FZCJaQdmB_MyIbBS-oslHSf0XXbAM1mRxK2y2T3JOwMFAUpmrHDeo1kq61Rw1kWTDPOJhwzlh_YURBExYRbYAhZzKZmD6UO6Wl4dHVZkKu9vbt82A/s1600-h/Add-Web-Resource---filled4.jpg)

This will place our web page web resource on the new region we added previously to the form

[![Tab filled](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgA4yHfKV3EhrNH32Bio95SLs5TLwy3NSOfWol988ev5KLhT4hV84EEFcknMFAIGJ7IgpApfgHcO7n3opyLPnWhjxv94P8cV1Wxyy9cHnICOysZcIyBSUOx39Nvq3OT1PQIAmg-a5AZRw/?imgmax=800 "Tab filled")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi0zfe7HdNOv_aAPtLreght0qQNxXB6OqLd3RuFn54uCQNSiEdMLclgAyUb1YbJw9UBwtf59ma4AyRWdjs34vJau0eECf2xDbF5B2HPLkzPIiBkBXgVv5S1XMTmeMgfKXgcSGFqbMYudw/s1600-h/Tab-filled2.jpg)

Now click Save on the form designer then click Publish to publish your for customizations, then click Save and Close to close the window. Click Publish All to ensure that everything is published fine, then close the solution window. Refresh your browser and navigate to the form you have customized, it will be Account in our case and open any record to check that our HTML page web resource is published on the form correctly.

[![Account Blue Company - Microsoft Dynamics CRM - Windows Internet Explorer_2012-03-09_04-17-58](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgI1I0HoO7nHHj3sOwPkosrtPsovoLOXrNBL_u2v-f23TixyxPNNO6D_N6FgQ-vmsdw39YmzVDMXGSiHTKrjYmBTNYX5eOs3ooHwpijDIt9EUtk8J74UdPZrqYBp1LdkNAQL8gzD6ja7A/?imgmax=800 "Account Blue Company - Microsoft Dynamics CRM - Windows Internet Explorer_2012-03-09_04-17-58")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjPzvl-O9mSGUNyvxHeofeJRE9SlcwqrHeSLYpVzXNcK9L_KLkJFOmv7UZqtGtpta33b-tsrY56pYdDTTphX_yDZG5wgCuX1ip2ITQNCGCOA7Xhc6dfszHn2hRJXK3hV-t1LLJr2Zl1wg/s1600-h/Account-Blue-Company---Microsoft-Dyn%25255B2%25255D.jpg)

**Using Web Resources from the Form Navigation**

Using our web page web resource from the left navigation of a form is much more easier than using it on the form. There are two ways to do accomplish this task; one using the CRM web client interface and the other one is through editing the Entity Navigation via the **FormXML** directly. Now we will use the web interface and will talk about FormXML in a future post.

Use the same steps we did in the previous example to open the form designer of the entity you want to customize, for example Account. Click on Navigation in the ribbon

[![nav](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjmQCj_WudUoxHSSRlR89N3RRC06drs7SRrHLzDTisFrw9saWgKd83azf48sVwMVxv7H7mNZVm0eilzuWVuE1xj-FX9myNUisyUqCGagGO6zZYoTqSNIw3Edm3GWytMI9OELZaEgkFMcg/?imgmax=800 "nav")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh_NpNxkffyXyd-PRRizOamRw8_G04mEMzJnIbZBrA1skSbnMgpExwZRNv7Xcv3hh5UIWLi0cSdxqYuQRRywV0rZ0mWxnLJuwC4ivBUxLVOdyWYSNG2VKxDa5Sqjzg6wjZANZutPB2O5Q/s1600-h/nav2.jpg)

This will disable the form controls except the left navigation area. Click on Insert tab on the ribbon. Then click Navigation Link

[![nav link](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgdfbyXoj6geQ3O6HZv9bho5YzUtsVGYp9KcMLkAFnAreKPHAvonjb_Fz0DpKmvpYkN6bVjWWueKMNsKqGq3oVWR06T8bytu28uSjgmGsGcJc907wSVEgx7phOpUBMGHoS24lykl3-BQA/?imgmax=800 "nav link")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjpfMjMQQHKNwCrKhqPQdwuhOXJPBpDcRg1VPwvXskSSql_JtkafgXM4SqVg4rlT5Wbz_nYbxlLsOYHRX5y0U_rTqYFVwYLJ2OHf503JPDpHEWeGqLvG-t12QeJAmRhfhWLXjxVe-BscA/s1600-h/nav-link2.jpg)

This will open the Navigation Link Properties dialog. Enter Name of the link which will be the text that will appear on the left navigation, then select our web page web resource from the Web Resource textbox (you can link to external URL which will be rendered inside the form at runtime).

[![nav lnk](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg3-RVmG0PVlbm3-aVeXaHigdPcpzJ5x-FfWq8Im6sv9noX9GlKwHMcc5CCTJZ3-0wOdMdEyneCcD3PVJusIUzvoXLaSUb1tLTcdsE3DMN9INR5nes4oddto6Gz__SyeJ-UPZIBcA7BAQ/?imgmax=800 "nav lnk")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjWLUiEzsap4-Nd5qLj7LCiHpW2ODhtJLIRfa85OJwZfiX5YWE_wDsw3_93QLYFfpLfhqCfbQyM-VHtjPJoWVOx5e34KpV7XerZJ_r3auZI9iBRezGCB-BVeuU7iXrh-qGvkEOkjPBivg/s1600-h/nav-lnk3.jpg)

Now If you open any account record, you will see our link added on the left, if you click it our web page web resource will be rendered on the right.

[![acc](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjKey_GtyOiilLojozxUi0skiSxh7kAWpkg7Io_0o-xVCmD8lRsQQYrvB5Z9TcVq4FJSyobj0zjCzcnAYF_Mtn1CWB44Nx-3qrmKc4NonGro12aomJclpyCb_Ns2lNTHmydRvlBDMQTAw/?imgmax=800 "acc")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhwwuUzxU81E7b3wIp_kJJAqM_lUwz3NvFuWFbEX1Sq2F9gTYXoEQFXxnnCydc4RDL4hlipZIKxAeS6UDgFkrEhoZ-YKBUAIn5O70QBp9MLiEwrgNNwAEpeDX4dgvKRZN5yiF2jOxFHDA/s1600-h/acc3.jpg)

**Using Web Resources on a Dashboard**

Using Web Page web resource on a CRM dashboard is pretty similar to using it on a form. The first step is to create a new dashboard by navigating to My Work > Dashboards > click New on the ribbon. This will open Select Dashboard Layout dialog, select the layout you want (for example, 3-Column Focused Dashboard), and click Create.

[![Dashboard Layouts](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhKBKDnYrM5vPW3W-iJ53aLLnMsmlrIlTRehj8j5PdJ_LnsIYne-idUO2Y5N5xl9t-iy2vQ9yFF91OFCRbYbqWkXFUoZehTnD-UplstbYOcuRrrrv4ohTTlZugEAFu7fVIKeYofdAPJfA/?imgmax=800 "Dashboard Layouts")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjZr2yCQ5bxmQ6RhRiaw8k2QqNBk_NFNQxBcKA4kKP14xJq6MijMk3Gn_QbthtPg9m5ltalEdenEIUyQTr_5ZeKfckcAbZTuOVJS0vSAOzxbZbfxMJCkSxYwHAWWT7dAcYKw0WBFc77OA/s1600-h/Dashboard-Layouts3.jpg)

The dashboard designer window opens. Click on the Insert Web Resource icon on any region on the dashboard (indicated by arrows in the image)

[![New Dashboard Designer](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhg4iqWpCrYRaNkGvaLf1B3HAyS275-CblZvBwZtBTjvq1VbHsQhr4MU3GhpYaNvqVGTKVa4TDLLhovDODAC1N0JBodqfZmjdg6U-U8qUulMRYkJS0OGLVH_7SQGMWzjCxr8F1RapTxzw/?imgmax=800 "New Dashboard Designer")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjkDT3ISit06GYk-9T_pzUpz9zsAmKXqgMO9kRC8NXL0Zi7J1EonXz5A5e1adiqbfQMPUhpU13OEEBvvPgIgYCmMzXm7MRpXB75wKLUpExa32XLAWfTc5f2KCbpdoJPbuNORvCB36ySag/s1600-h/New-Dashboard-Designer3.jpg)

This will open the same Add Web Resource dialog we worked with before. Do the same steps to add the web page, then gave a name to your dashboard and click Save and Close. This will close the close the designer window and open the new dashboard in your CRM main window. For example, I added the web page web resource to the left region on the dashboard and named it Test Dashboard, and below what I got.

[![new DB](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhf2Cz1YkReXL1jOjItfXFsi4yzSju89LNUzhyphenhyphenFtz3ewDcxASU3-EN0rD2HXXnYM-Ebyviu-mFD_x2eUVL3ftgotGK8lxN2K9yOdjBGwZBILQ7LARN-jgMPleMpJ5FqyA65RDxOb-FNgw/?imgmax=800 "new DB")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEge5FOi7RuZVYIHV2ndIm-Eehoy6H-E-lxG5sDpg3GqPn4gs6tqXO0mypKb6rJV65cAEVWnZFq9svdZBOO2xmSwsAwvMVVlRuRRAOS7DNHhMCAPymSRsCpn_8ywTiLRr_GhLeiyVfH0hQ/s1600-h/new-DB4.jpg)

**Using Web Resources Direct From SiteMap**

In order to make our web resource accessible directly from Sitemap, we have to edit the SiteMap. Unfortunately there is now way to edit the SiteMap from the Dynamics CRM web interface, you have to export the SiteMap in a temporary unmanaged solution, edit the SiteMap XML, then import the solution back again.

To create a new solution, navigate to Settings > Customizations > Solutions >  New

[![s](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjthowq1h74gObe6AuzJzmocPEp_z-zd_FF8WCKNrxjQ9TtIPe-gpzFjySNvTJn3jkVHVc1U-vqUY1h1LguwEsGWfAFBTcedmzOkodDxx5UoTK_KllrJYEX6Qu0UqJrJ5KkWRTb3ItprQ/?imgmax=800 "s")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj1J4RlaU_jiJlW6iB-S6piED_fKcGw8zCF6WOQkp-sgSbFvagWDQ0zY9VaqLXaRmz4QoALpXXreQAf0QMVeUQd4tNCB205NFTtE5XoIf1IAaH30HZBFKJxpiWh9gKergXBcp5ojrb-FQ/s1600-h/s2.jpg)

This will open the New Solution window, enter a Display Name, Name, Version, select a Publisher, and click Save

[![new s](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjLnnNXSO-PUBH2uB3DB208N4i6NaZkYnzb-YmgnXKuPd8_SIE9opFuHIuKT525OjTaPWiC_GIUqaCv1Bn6Cr94kjvzrIZHBo-xTD4A43J66qF_UHbZjReneOFJK6ynn1MufihWiN0wPg/?imgmax=800 "new s")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjSeUEKjhU-aYDnwsPDIGWNoM4lJjU-Ms6Qf92CloIzOo8NU91xuy7-DO1eJvQ2Lv3Xm7SqAP8Dlq1f2R7ebpPMy0MI_G008NY20KrKnh75stXyuBrNfJQh63qkqGuBI5LWkzSWWWmX3Q/s1600-h/new-s4.jpg)

After you click Save, the window will change to allow you adding your solution components. Click Add Existing > SiteMap

[![n s m](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjTBQ5aKjm49NhteWsz1SAH-_lIMmMscVzA-u7ivhQN-iu1kGLFX4c59SKfKlFj2mlAC70oVR6K4NAkT1BBmxB1bTV4outm_QefpQW6Sdag1oiSPu-SWsghR-ihd4_40hRtj-uhbsa3BQ/?imgmax=800 "n s m")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj86dP9LFbzZS-QK_iql331ehLf1mveWo1bCFRtQhBQSJk-kD476FrJui7nkvL0agnYB9PmXj2WGOyQ6RIM8AmqP0OhdcJCK-9iWH19QVbfZ6qoV2mRAlO2iKwZuIq6iAIrpHkIVCensg/s1600-h/n-s-m2.jpg)

Click on Export Solution icon

[![export](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhFK7Gl-UakxP5ywzQLvDMcIXiuMQmswqA0lNoN_miiPFtFNKAtyn0QOspDM5BTPsgycGUPOnFlGFZb-eS8kDHpLIbtAEtfE5vtJX4-fZ7IxUCHyWpj_xCIE4OmooqSnt_W0qonHq4CcQ/?imgmax=800 "export")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhfdjgv8la9E4YR4LbETUNfIDkHWEHYIDI58bPAblSe6V54I_L3o3MPIPX00985VSHRVyNohk8-l5Cdjbp2znf70XIXQ_HlEN46EIsM64kE-p6S8Qiv0MkIJPhL-iRyANAFemInb65hVA/s1600-h/export3.jpg)

In the solution export dialog click Next > Next > ensure that the package type is Unmanaged then click Export. The Dynamics CRM server will package the solution files for you in a zip file and deliver it for you. You will see a file download message from your browser to download the zip file.

[![dn n s](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiyZY91cb93eEZNNIBQQtJBAUlBVVvFtsJjGuW13JxHa5tgN4eB2sWO5yZ8IE5HXBTf8vzRxp59Ig1n3yW3pvP6u_y0-CZPt1KaqSTof_gNqM95gFfuzZR4JbWzHjBTQ0UvcL3tTvvjrw/?imgmax=800 "dn n s")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhctdkTfk975Mixkcm574eH9ee6icV46xWeKYGKgDNqiQfrumotxP1ACvcznpjopGizQlHUZx_FElDnhigpRRxVchAloaSQ4KX86VWq3NpxXqX8Z3dhUpMDxZLUySEVjvgUpCZBbTEWhg/s1600-h/dn-n-s3.jpg)

Save the zip file, extract its contents, open the customizations.xml file in Visual Studio (or your favorite XML editor). If you collapsed all the nodes in the XML Editor, you will see that the SiteMap parent node have many Area nodes. Each node represents the major parts of CRM web client navigation, which are available on the left bottom part of the window.

[![sm](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhVEjSMvFORPIjTLGsb-wXUuRV6DMwhxuJ_99Lxa4vn-Ss88j-hIyXHg31YC72bFUcatMMBNptk8vYl07_83DnC462fK3TepXd0Fvi-QdwK77aLSd7TC1WasxTLD2U9S-wP7pBEL7p6-A/?imgmax=800 "sm")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjyFh2AWlIqFaHe9OMmx1sDEGKGCDI_iQimPzwd3Y7_-NKpRwA_rzipZu3-0jGw7LMQGhuub57o-dzEMa6dW4PobgAHvHUhBmPiniporX23bXrpCWEVY1MXQjnnLJuI-H5yGVF8YXx9KA/s1600-h/sm2.jpg) [![Areas](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhbw6zc-jZ91HrwTC6QgBCXMo4mNHj-3cmay_F4IlcME460VRl9R6M6flkXvMJktY23XSCOD5Ri1b8aUzq_Q-If5z9hsWgRkYsLezMtOr5ipZv1Mrq1Izf_3SC8dPb1FXpjy8uD3JHjVA/?imgmax=800 "Areas")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgaj_YOpSZg4tGlRuoDsh1WXogyM-TPUUu2djNzhVOQ8R1EbLoFla6bGGVAQint14RHK5SYCaGmh5WJ-u_aBKsEHK1bW8OGX-SqUem9hNAIMUqOolvib6K1zig4aKTpymNCqqKpN2k4pA/s1600-h/Areas2.jpg)

Now expand the the area node with Id=”Workplace”, which represents the Workplace in the web client. You will see Group nodes for each sub-section of Workplace area

[![sm area](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEirkELBpFqg4wiBqLRqmfpNEiupfj91TzjFAARmlUNPImF1yf_YDuZ1gy7KHEYOWVCxYeb00xIXoWF-aNtTymvqO5OyrUeSPJEMrYFdacq2OeouB48Bxy_G1y4RB7qz9fvx6RvL8bHkYg/?imgmax=800 "sm area")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiqe70N09fmtRzyFXvX98okQOuw2WeKIvSAWoSIynqoOj1Km5gXIS4jHxnNZdEEGFvDmVDUXvsQz4IecnhX96YGjQHt-ChLJLbNmBD8ZDRPpkXdClDo0IpjX1ktiBTWcsAB568mK48HwA/s1600-h/sm-area2.jpg) [![wp](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjtCUSjytT8BnQYW4y-SYC8glnCNiPH6gD3aXCewsMO9jwvVxnC4MyQLoqlsU4u3VLLCVCo0Hq78lPtdZREBZIxShivS2ahr448tkMQV52N223slQlXi_8tXAyghrYTm2F4wZJCW1dgEA/?imgmax=800 "wp")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgHvbBFkMlU2l2CEnhC9Eb8CVXv2Os-1axlVf81TJRvteSPoqGnXbyq6xhRrSyQo5ptQttRJssPjh9wSOiGpLF9YIHjdzY3ayUG-rBWHaVGmv2yWOqH85IC7-Rf5P-2fG0hkC7Gx0RMJQ/s1600-h/wp2.jpg)

Now expand the group node with Id=”MyWork”, which represents MyWork in the web client. You will see SubArea nodes for each sub-section of the MyWork area.

[![sm group](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhb93jDgHxuX1_hKXk5HmStCTj6ZwlHXFIrw-942QJw9EpB5rz8k71ZNVTbhyTam8n_RMJ0l4UTraygirIKUSRH6GXziSc4dxkZEwwwX4Db9tgBYRHqvIa1Xc4esTGHnDAqAXJpX8JxzQ/?imgmax=800 "sm group")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjweQNyzGlDoS_vI0EnBCi-N-T-wZ6WNBdzvJwmHdtS8AVl-iVqKH9MLF5rUjdMmbvDK3YPH1GRyjkofrMdhZvTaLgEXGvI4WifpTeS6br5oLbu4vCZLbgzCHUMXdPrcwmkOqnb9IvTaw/s1600-h/sm-group2.jpg) [![mw](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgNM9noUohpZGmF0rvwUQE-Dd_xOjHvLKaD-yNKCMRsIkJ2Q61NrxzZSHhidCDdeVXMyzV0p2W2KzMeG25kVmXDy3zue3pnCB0IQX0FwwGHO2Y_G2oFlJ6_nXKpVouCQAJd_gSJ0XUOtg/?imgmax=800 "mw")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiBApPvYhGFrZ6MsIbFq__yyrx5jGhRRrN2YdEi0thz9HlYmHuZ_HnuEn_JWZQKxgqIxmPhNoTZ9Mor-nEZkfZrXWWLTGVvyHpHz5k46jmnDqdmKxUxP6Sa7K_GxwG2fvedHexvYn7_Kw/s1600-h/mw2.jpg)

Now let’s say we want to add the link to our web page web resource just next to Dashboards under MyWork. Locate the SubArea with Id="nav\_dashboards" and insert the following XML after it to make our link

```
           
```  
  

This xml adds two links on the SiteMap, both of them links to our web page web resource. The first one uses the web resource direct URL which can be used to access the web resource even from external systems (vice versa, you can link other URLs directly to your CRM). To get the web resource URL, navigate to Settings > Customizations > Customize the System > click Web Resources from left navigat > double click the desired web resource to open its properties dialog, you will find the URL in the bottom of the form

  
  

[![WR url](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjQ022OizdZfTdnISvGDvTTGvwC_7veHlOzkveS3WB8AkXmkXF7yIIvuDVSDf_uiH9DM7pfrJXFb2-qfkhHcIBmJ35gGxsrp_VIrIQrS7atKUqTwc8iXublH8DALXdr-S9pOHwY_E_MLw/?imgmax=800 "WR url")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgSMrBB8thjXtHJWVY12m6q1P98tUfyMcFSpvpo7ThdMjsBRzHV2CahpS75k1xYa06HEXk7V7XkvYQiTiK799GDI-o7C-F8JFQMzAXiksEdIWXWiPuaIOvkJtI7qXaT3vqPtlVv4zrm4w/s1600-h/WR%252520url%25255B3%25255D.jpg)

  
  

The second link uses the keyword **$webresource** to reference the web resource by name. We will talk about $webresource keyword in the “Referencing Other Web Resources” section of this post.

  
  

Now its time to get these SiteMap modifications into CRM. Save customizations.xml, Select all the exported solution files and add them to a .Zip file, navigate to Settings > Customization > Solutions > and click Import. In the solution import dialog upload your .Zip file, and click Publish All Customizations at the end. If you navigate to your CRM home page and refreshed the page you will see the links on the left

  
  

[![VER](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjOZWAboKXbEwQ_IUnh6NFGJL6fQkwyE2-JE4bpUbkVxv5ENne5mwtsdRRnF7Q5iANpStRyWDrrFc8zORQDnWRgzQadGqugRjLJCGx1wrEuX9R47Jn4UltlBX7B6f2O1Fc1VFjKrGvs8g/?imgmax=800 "VER")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjt0fFRajn9XfNi2DiVc1J7mq8RKolh0uZpdVh65882kW2adctUKC9hYoI9e0thn38GlbdHe5NQuDTi5Eu2Nm6wibfZYP4RNw4LIV59apS7dr1ZMadYsJ6312hTQCvg5VHk7-L-Etf47Q/s1600-h/VER%25255B3%25255D.jpg)

  
  

**Using Web Resources as a Solution Configuration Page**

  
  

Solutions are containers that track customizations and allow it to be moved around from server to server. When building a custom solution you may want to add a page where you provide details about your solution and its features. Configuration pages for solutions can fulfill your requirement for such a page. Let’s see how we can use our web page web resource as a solution configuration page. Navigate to Settings > Customization > Solutions > click your solution > on the Solution dialog click on the Information from the left navigation

  
  

[![sol info](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhizafBX_0sV5oRQuIaMZOK4967QoKeHME5x8eH4k5xbEC_cCa9J18V0jdSfm67PlHN7kBNKaNaHtLq-QrEx-OS67TDUBCeUaME0Jn-k5shtSQfKjbMFMvBfxzoN3UdWRS03x6cruSr9A/?imgmax=800 "sol info")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjefR9AGA7KFo-6PgQYmrp8R94-OzqFQ3fv1yRGcQVXmDGMfXl-oYG8BNtg0SIurNgZnKu9Es76HyG6gsioR1h1reLMBDRqS9U24hR-5rEhSPpkPE4nGn6IwFP_tYl7qEs_PgmCLOEBKQ/s1600-h/sol%252520info%25255B2%25255D.jpg)

  
  

Then choose our web page web resource in the Configuration Page textbox

  
  

[![sol info 2](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjJ8c9u5LuGykAimqNtuW4PJppWy6nLAHXMhNuQHtJ7anat6FxsPbULUY5yQfIXgGerD5gVsmamWVef6Bj_zUMVdga1shyphenhyphenpYToVIUfqZ0nZ-nogmSRgCl2o2O2VyoHRFhJMQO136x_Bbw/?imgmax=800 "sol info 2")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiIZ4fWpOyja0b_XE-PFmGZjFzpf95MeUlt_Cyw-V2hPnVKUVzX4aAvFmaW2totXNxVk4BGH53fersbx15C5SykLByVbTEnoKcohlq7AMLlQZXuuNDnC27MxcZMwwCLONKcdAFjouz36Q/s1600-h/sol%252520info%2525202%25255B3%25255D.jpg)

  
  

Then Click Save and then Click Publish. Now you will see a new link added on the left navigation after the Information link, it will be called Configuration

  
  

[![col cnfg](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhiS8PXnynEwawkyra5smXfWclS41E1E50rn6n-o1wkvncA3JQYMeMJU_ot2I-fr8m_CZ3fmr-lCA1lrNQJkHftjyrJOHVwNu58Tt3qBxSGdTXN2QNok1K7-KDSjQp2hzJv_zBswh0y_g/?imgmax=800 "col cnfg")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg0GUvs8fjZF64UG5De7Ok0XivMfcp8DmyrttgpBIFzjkP95in2knJQBC-K901cK_-7gMuvOwlmERL77eJOjpbYCFNfIuEK_v7W_uhIzRFcPka7kAOO2P77aRLMyCdWyYnjEeqYdG9JIA/s1600-h/col%252520cnfg%25255B2%25255D.jpg)

  
  

if you click it, you will see our web page web resource on the right.

  
  

[![col cnfg 2](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEis7F93cSNdn_0n_XS5EmNq-7r0dDzBPJxKHGDQgS1guVc-aOPIsYlwRjT9WQgeLoy2la1UGmlY3o9UahzSUgE8eP3bBtp7JieEYrdcaaVMmWZuNTwAxCHHVe3KzMFnYveogQRorh2nTw/?imgmax=800 "col cnfg 2")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiQVApTeD9Bvh0wM3oU_ayoNDYEvVMS543s7orlj3ngaU0Ama8mDq6L9XLc9rZQfvnBbMzt_cCN4DKR5GaTg6UPNzA8CMAkrTdnMNWQeFslbT3AyU-uMBJHhBXcQ6LatlWtcHedX0SRmg/s1600-h/col%252520cnfg%2525202%25255B3%25255D.jpg)

  
  

**Referencing Other Web Resources**

  
  

While some web resources can be added directly to a form or a dashboard, others can only be referenced through their relative path. There are many ways you can use to reference Web Resources:

  
  

**$webresource Directive** You should use it when referencing a web resource from XML like from a ribbon control, or a SiteMap sub area (like what we did before). When using the $webresource directive, Microsoft Dynamics CRM will create or update solution dependencies.

  
  

**Relative URL** You can use relative URL when referencing from HTML or other areas that doesn’t support using $webresource. To make this works, it is recommend that you use a consistent naming convention for the web resources that reflect a virtual file structure. The solution publisher’s customization prefix will always be included as a prefix to the name of the web resource. This can represent a virtual ”root” folder for all web resources added by that publisher. You can then use the forward slash character (/) to simulate a folder structure that will be honored by the web server.

  
  

From another web resource, you should always use relative URLs to reference each other. For example, for the webpage web resource `new_/content/contentpage.htm` to reference the CSS web resource`new_/Styles/styles.css`, create the link as follows:

  
  
```

```  
  

For the webpage web resource new\_/content/contentpage.htm to open the webpage web resource isv\_/foldername/dialogpage.htm, create the link as follows:

  
  
```
[Dialog Page](../../isv_/foldername/dialogpage.htm)
```  
  

Full URL As web resources are URL accessible, you can open the information dialog of any web resource and copy the URL in the bottom of the window and use it anywhere you can use a URL (as we did before).

  
  

In this post we introduced the web resources feature in Microsoft Dynamics CRM 2011. We started with exploring the different types of Web Resources, where can Web Resources be Used in our customization scenarios, and what is the limitations we have on using web resources. Because web Page web resources are the containers that can host (or link to) all the other web resource types, we explained all the ways to incorporate Web Page web resources in Dynamics CRM. Then we explained how to link to other types of web resources.