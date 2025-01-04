---
title: "Microsoft Dynamics CRM 2011 for Developers | Web Resources Part 1"
date: '2012-03-11T06:10:00.001-05:00'
tags:
    - Microsoft Dynamics CRM Dashboards
    - Microsoft Dynamics CRM Solution Configuration Page
    - Microsoft Dynamics CRM Forms
    - Web Resources
    - Microsoft Dynamics CRM SiteMap
modified_time: '2012-03-22T15:35:30.009-05:00'
thumbnail: http://lh4.ggpht.com/-x3FFcP8Ch00/T1yH2XK-GgI/AAAAAAAAAME/XB-nmGYka4M/s72-c/page_thumb1.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-2053507440203242420
blogger_orig_url: http://ebeid-soliman.blogspot.com/2012/03/microsoft-dynamics-crm-2011-for.html
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
10. Using Web Resources as a Solution Configuration Page
11. Referencing Other Web Resources

**Introduction**

Web resources are a new feature of Dynamics CRM 2011 that allows storing
of client side content in the CRM server database in order to be used
for extending the Dynamics CRM web application. That content is then
available to be delivered to users as needed during their interaction
with the user interface. These resources can be used by URL, which also
allows relative path referencing.

Based on that and using the appropriate development tools, a fully
functional web site can be created on a development server by using file
types that are compatible with web resources. Then, if using a
consistent naming convention and relative path references, the web site
will function after uploading all the files into Microsoft Dynamics CRM.
These web resources can then be exported in a solution and installed on
any Microsoft Dynamics CRM deployment (both on-premises and on-line). It
will also available to users of Microsoft Dynamics CRM for Microsoft
Office Outlook with Offline Access when offline because they are
synchronized with the user’s data.

**Types of Web Resources**

Microsoft Dynamics CRM allows ten types to create web resources which
fall into seven type categories. We will explore them here:

-   **HTML Web Pages** You can upload \*.htm or \*.html files as web
    resources, or you can use the Text Editor in the CRM interface to
    create your HTML web resources. Web pages can’t contain any code
    that must be executed on the server (no ASP.NET support). Web pages
    can only accept one custom query string parameter called *data.*
-   **Images** You can upload PNG, JPG, GIF, and ICO files. They can be
    used as icons for custom ribbon controls or Sitemape subareas,
    decoration for entity forms and web pages, background images.
-   **Script** Enables uploading JScripts for reuse of many parts in the
    CRM like web page, ribbon commands, or form and field-level events.
-   **Style Sheet** .css files linked to web page web resources to
    efficiently manage their appearance.
-   **Data** Enables you to upload some XML files to your system
-   **Style Sheet** enables you to upload \*.xsl and \*.xslt files to be
    used by Data and Web Page web resources, so you can apply the style
    on XML files.
-   Silverlight enables you to upload \*.xap files which is the output
    of Silverlight application build process. Silverlight applications
    can be used on forms to create a more rich and visual components for
    users.

**Where can Web Resources be Used ?**

All web resources (except XML, XSL, XSLT, CSS) can be used on forms, on
dashboards, from SiteMap, or from the application ribbon. All web
resources can be used in the context of Web Page web resources.

**Web Resources Management**

Web resources can be created in the context of any unmanaged solution
inside a CRM organization.

If you will create the web resource in the default solution navigate to
<span class="underline">Settings</span> &gt; <span
class="underline">Customizations</span> &gt; <span
class="underline">Customize the System</span> &gt; click on <span
class="underline">Web Resources</span> from the left navigation &gt;
<span class="underline">New</span>. Enter the Name, Display Name, and
select the web resource type. If you will create the web resource in a
default solution other than the default solution, <span
class="underline">Settings</span> &gt; <span
class="underline">Customizations</span> &gt; <span
class="underline">Solutions</span> &gt; and click your solution and
complete in the same steps as above.

After uploading a new or updating web resource, you have to publish the
web resource before you use it in the application.

You can remove an unmanaged Web Resource at any time as long as it is
not currently being by any component. If you attempt to remove a web
resource while it is in use by another component you will get an error
message.

> Web Page web resources are the container that can host (or link to)
> all the other web resource types, so we will explain all the ways to
> incorporate Web Page web resources in Dynamics CRM. Then we will
> explain how to link and integrate other types of web resources.

In order to proceed, we will create a simple "Hello World" page and
upload it as a web resource. Create a simple page.html file like the
following:

[<img src="http://lh4.ggpht.com/-x3FFcP8Ch00/T1yH2XK-GgI/AAAAAAAAAME/XB-nmGYka4M/page_thumb1.jpg?imgmax=800" title="page" width="519" height="219" alt="page" />](http://lh5.ggpht.com/-EIxrx_YyIeQ/T1yH2HnEXBI/AAAAAAAAAMA/P3HboZa2yR4/s1600-h/page3.jpg)

Now open your browser and navigate to your CRM organization, then
navigate to <span class="underline">Settings</span> &gt; <span
class="underline">Customizations</span> &gt; <span
class="underline">Customize the System</span> &gt; click on <span
class="underline">Web Resources</span> from the left navigation &gt;
<span class="underline">New</span>. Enter a Name for our page, Display
Name, and select Web Page (HTML) from the Type combo box. Click <span
class="underline">Save</span>, then click <span
class="underline">Publish</span>, then close the window.

[<img src="http://lh5.ggpht.com/-5XQaHpADKTY/T1yH3ICog3I/AAAAAAAAAMY/rY9zoXSdlZs/Web-Resource-New_thumb2.jpg?imgmax=800" title="Web Resource New" width="387" height="490" alt="Web Resource New" />](http://lh3.ggpht.com/--BZwF_e0JB8/T1yH2_9vUXI/AAAAAAAAAMQ/r3XqttV4fCQ/s1600-h/Web-Resource-New4.jpg)

Now we create a simple web page web resource and ready to explore the
different ways to use it in our Dynamics CRM. We will explore just the
basic usage scenarios, advanced features will be explained in a future
post.

**Using Web Resources on a Form**

Now let's put use our test HTML page web resource on a Form, e.g.
Account. Navigate to <span class="underline">Settings</span> &gt; <span
class="underline">Customizations</span> &gt; <span
class="underline">Customize the System</span> &gt; from the left
navigation expand <span class="underline">Entities</span>, then expand
<span class="underline">Account</span>, then expand <span
class="underline">Forms</span>, then click on the form named <span
class="underline">Information</span> which have Main in the Form Type
column. The form designer will open. Just to make things easier for you,
collapse the regions on the form (called tabs in Dynamics CRM) by
clicking the small blue rectangle on the left-top corner of each of
them. Then Click on <span class="underline">Insert</span> in ribbon

 [<img src="http://lh5.ggpht.com/-SLP2LRPc-KY/T1yH3zSVSBI/AAAAAAAAAMo/uduC_AniHUg/insert_thumb.jpg?imgmax=800" title="insert" width="207" height="150" alt="insert" />](http://lh3.ggpht.com/-zY-UAuh9p00/T1yH3bJ5iGI/AAAAAAAAAMg/70ojh2Aka-A/s1600-h/insert2.jpg)

Then click <span class="underline">One Column</span> on the ribbon.

[<img src="http://lh6.ggpht.com/-lYxjIIL62f0/T1yH4ft4l0I/AAAAAAAAAM4/-RDWRv5GvNY/one-column-tab_thumb.jpg?imgmax=800" title="one column tab" width="244" height="108" alt="one column tab" />](http://lh6.ggpht.com/-j9inEp1XVFs/T1yH4IqJaDI/AAAAAAAAAMw/A2oeFGIGOv4/s1600-h/one-column-tab2.jpg)

This will insert a one column region (called Tabs in Dynamics CRM) below
the currently selected region.

[<img src="http://lh3.ggpht.com/-jpE_Dvy8JVE/T1yH5eJxXTI/AAAAAAAAANE/JYQsPG9hkDs/new-tab_thumb.jpg?imgmax=800" title="new tab" width="244" height="104" alt="new tab" />](http://lh3.ggpht.com/-SLF1KcvDS0w/T1yH5CPuXFI/AAAAAAAAANA/vylvOXshuoo/s1600-h/new-tab2.jpg)

While your new region is selected, click <span class="underline">Web
Resource</span> on the ribbon.
[<img src="http://lh6.ggpht.com/-ZEYLiEuiMO4/T1yH5xyiDWI/AAAAAAAAANQ/xQCgBnej3kc/new-WR-ribbon_thumb.jpg?imgmax=800" title="new WR ribbon" width="244" height="111" alt="new WR ribbon" />](http://lh3.ggpht.com/-ENNceawAwY0/T1yH5ge41RI/AAAAAAAAANM/eh9ljd9dIBg/s1600-h/new-WR-ribbon2.jpg)

This will open the Add Web Resource dialog. In the Web Resource textbox
click the look-up icon on the right and select our Web Page web resource
from the list (you can also search for it by name). Fill the required
<span class="underline">Name</span> and <span
class="underline">Label</span> fields, and click Ok.

[<img src="http://lh4.ggpht.com/-fBVS5Jddi5Y/T1yH6-EEq9I/AAAAAAAAANk/hK5xQ06sIyA/Add-Web-Resource---filled_thumb2.jpg?imgmax=800" title="Add Web Resource - filled" width="319" height="413" alt="Add Web Resource - filled" />](http://lh6.ggpht.com/-n2RniwSjp9A/T1yH6TNgNmI/AAAAAAAAANc/85sgpiUNTgI/s1600-h/Add-Web-Resource---filled4.jpg)

This will place our web page web resource on the new region we added
previously to the form

[<img src="http://lh3.ggpht.com/-LRVM2H6pO8k/T1yH7c_dt_I/AAAAAAAAAN4/8PzWwArsZaM/Tab-filled_thumb.jpg?imgmax=800" title="Tab filled" width="244" height="145" alt="Tab filled" />](http://lh4.ggpht.com/-Pp9BhDBNIyg/T1yH7CU_J3I/AAAAAAAAANs/mGuztuop4UM/s1600-h/Tab-filled2.jpg)

Now click <span class="underline">Save</span> on the form designer then
click <span class="underline">Publish</span> to publish your for
customizations, then click <span class="underline">Save and Close</span>
to close the window. Click <span class="underline">Publish All</span> to
ensure that everything is published fine, then close the solution
window. Refresh your browser and navigate to the form you have
customized, it will be Account in our case and open any record to check
that our HTML page web resource is published on the form correctly.

[<img src="http://lh4.ggpht.com/-ExZVXe-UXgU/T1yH8KHv8nI/AAAAAAAAAOE/C7itRZhu2pY/Account-Blue-Company---Microsoft-Dyn%25255B1%25255D.jpg?imgmax=800" title="Account Blue Company - Microsoft Dynamics CRM - Windows Internet Explorer_2012-03-09_04-17-58" width="462" alt="Account Blue Company - Microsoft Dynamics CRM - Windows Internet Explorer_2012-03-09_04-17-58" />](http://lh6.ggpht.com/-VVLKV3myPC0/T1yH77fqBkI/AAAAAAAAAOA/urCAn0ijQy0/s1600-h/Account-Blue-Company---Microsoft-Dyn%25255B2%25255D.jpg)

**Using Web Resources from the Form Navigation**

Using our web page web resource from the left navigation of a form is
much more easier than using it on the form. There are two ways to do
accomplish this task; one using the CRM web client interface and the
other one is through editing the Entity Navigation via the **FormXML**
directly. Now we will use the web interface and will talk about FormXML
in a future post.

Use the same steps we did in the previous example to open the form
designer of the entity you want to customize, for example Account. Click
on <span class="underline">Navigation</span> in the ribbon

[<img src="http://lh4.ggpht.com/-h3U28XG2mnE/T1yH86gsKoI/AAAAAAAAAOY/-zh_CJ6-ays/nav_thumb.jpg?imgmax=800" title="nav" width="244" height="97" alt="nav" />](http://lh3.ggpht.com/-ndmPH2Lac60/T1yH8WIR6eI/AAAAAAAAAOQ/chzuVXWRJGI/s1600-h/nav2.jpg)

This will disable the form controls except the left navigation area.
Click on <span class="underline">Insert</span> tab on the ribbon. Then
click <span class="underline">Navigation Link</span>

[<img src="http://lh5.ggpht.com/-x6DtGvYlP3A/T1yH9mICqNI/AAAAAAAAAOk/46DQJrelvCE/nav-link_thumb.jpg?imgmax=800" title="nav link" width="109" height="119" alt="nav link" />](http://lh4.ggpht.com/-JBCcxsdOfmo/T1yH9YMGJjI/AAAAAAAAAOg/GNsjPkZFzYI/s1600-h/nav-link2.jpg)

This will open the <span class="underline">Navigation Link
Properties</span> dialog. Enter Name of the link which will be the text
that will appear on the left navigation, then select our web page web
resource from the Web Resource textbox (you can link to external URL
which will be rendered inside the form at runtime).

[<img src="http://lh6.ggpht.com/-rQeJkyaDN2A/T1yH-YbgqeI/AAAAAAAAAO4/Z0MLlTdMfq4/nav-lnk_thumb1.jpg?imgmax=800" title="nav lnk" width="408" height="299" alt="nav lnk" />](http://lh4.ggpht.com/-hbtyOgJyqDI/T1yH9-q8fSI/AAAAAAAAAOw/RHlFUqsSLVk/s1600-h/nav-lnk3.jpg)

Now If you open any account record, you will see our link added on the
left, if you click it our web page web resource will be rendered on the
right.

[<img src="http://lh6.ggpht.com/-ZaWZ-59MWnE/T1yH_NNNkyI/AAAAAAAAAPE/NJXk2gSFWI4/acc_thumb1.jpg?imgmax=800" title="acc" width="510" height="419" alt="acc" />](http://lh3.ggpht.com/-uN8DSMHop7g/T1yH-vNU6TI/AAAAAAAAAPA/eIl33-8VXQM/s1600-h/acc3.jpg)

**Using Web Resources on a Dashboard**

Using Web Page web resource on a CRM dashboard is pretty similar to
using it on a form. The first step is to create a new dashboard by
navigating to <span class="underline">My Work</span> &gt; <span
class="underline">Dashboards</span> &gt; click <span
class="underline">New</span> on the ribbon. This will open <span
class="underline">Select Dashboard Layout</span> dialog, select the
layout you want (for example, 3-Column Focused Dashboard), and click
<span class="underline">Create</span>.

[<img src="http://lh3.ggpht.com/-CNFCEg%0Ac_77I/T1yH_5u75EI/AAAAAAAAAPU/w8-MfqnuGRQ/Dashboard-Layouts_thumb1.jpg?imgmax=800" title="Dashboard Layouts" width="412" height="302" alt="Dashboard Layouts" />](http://lh6.ggpht.com/-ShIxp8fxLqw/T1yH_RnoQCI/AAAAAAAAAPQ/0iWT-pbWY1s/s1600-h/Dashboard-Layouts3.jpg)

The dashboard designer window opens. Click on the Insert Web Resource
icon on any region on the dashboard (indicated by arrows in the image)

[<img src="http://lh6.ggpht.com/-ozqkUAawsMg/T1yIAn-T70I/AAAAAAAAAPk/3g_uej7d4fQ/New-Dashboard-Designer_thumb1.jpg?imgmax=800" title="New Dashboard Designer" width="384" height="344" alt="New Dashboard Designer" />](http://lh6.ggpht.com/-ZAzIQsN09dw/T1yIAVeM6UI/AAAAAAAAAPg/Y078EJRYNe4/s1600-h/New-Dashboard-Designer3.jpg)

This will open the same <span class="underline">Add Web Resource</span>
dialog we worked with before. Do the same steps to add the web page,
then gave a name to your dashboard and click <span
class="underline">Save and Close</span>. This will close the close the
designer window and open the new dashboard in your CRM main window. For
example, I added the web page web resource to the left region on the
dashboard and named it Test Dashboard, and below what I got.

[<img src="http://lh6.ggpht.com/-ybg96IJYFaM/T1yIBahYHkI/AAAAAAAAAP0/IRZ5H9Pl_LM/new-DB_thumb2.jpg?imgmax=800" title="new DB" width="413" height="345" alt="new DB" />](http://lh5.ggpht.com/-cucfXDnOFsI/T1yIAx5NqQI/AAAAAAAAAPw/5fW6FG4obOw/s1600-h/new-DB4.jpg)

**Using Web Resources Direct From SiteMap**

In order to make our web resource accessible directly from Sitemap, we
have to edit the SiteMap. Unfortunately there is now way to edit the
SiteMap from the Dynamics CRM web interface, you have to export the
SiteMap in a temporary unmanaged solution, edit the SiteMap XML, then
import the solution back again.

To create a new solution, navigate to Settings &gt; Customizations &gt;
Solutions &gt;  New

[<img src="http://lh4.ggpht.com/-hHwxFxNuNgM/T1yIB3NkpnI/AAAAAAAAAQE/ex6EvTvJJNg/s_thumb.jpg?imgmax=800" title="s" width="242" height="190" alt="s" />](http://lh5.ggpht.com/-zbZC5s9xFgw/T1yIBbgb7lI/AAAAAAAAAP8/tsxOSJWo9A4/s1600-h/s2.jpg)

This will open the New Solution window, enter a <span
class="underline">Display Name</span>, <span
class="underline">Name</span>, <span class="underline">Version</span>,
select a <span class="underline">Publisher</span>, and click <span
class="underline">Save</span>

[<img src="http://lh5.ggpht.com/-3-wvqUBNaOo/T1yICShjRII/AAAAAAAAAQU/Re5A6O66KoI/new-s_thumb2.jpg?imgmax=800" title="new s" width="427" height="422" alt="new s" />](http://lh4.ggpht.com/-klCwvFC5mRQ/T1yICCpDaVI/AAAAAAAAAQM/ZP1ngdFft_M/s1600-h/new-s4.jpg)

After you click Save, the window will change to allow you adding your
solution components. Click Add Existing &gt; SiteMap

[<img src="http://lh4.ggpht.com/-gA0b8Mzf2_I/T1yIDrjRHII/AAAAAAAAAQo/zcPFQaPiM_Y/n-s-m_thumb.jpg?imgmax=800" title="n s m" width="244" height="165" alt="n s m" />](http://lh4.ggpht.com/-zWzAL32YO28/T1yICx5MAxI/AAAAAAAAAQg/zqFetF1DFj4/s1600-h/n-s-m2.jpg)

Click on Export Solution icon

[<img src="http://lh3.ggpht.com/-NYMLelvf7hU/T1yIErJUjrI/AAAAAAAAAQ0/0qZs3-y_Veo/export_thumb1.jpg?imgmax=800" title="export" width="260" height="88" alt="export" />](http://lh5.ggpht.com/-yixtk6z3MWU/T1yIED8k_QI/AAAAAAAAAQw/KDHsM3avlL4/s1600-h/expo%0Art3.jpg)

In the solution export dialog click Next &gt; Next &gt; ensure that the
package type is Unmanaged then click Export. The Dynamics CRM server
will package the solution files for you in a zip file and deliver it for
you. You will see a file download message from your browser to download
the zip file.

[<img src="http://lh5.ggpht.com/-jfIaR6ZYeTs/T1yIFUS3XyI/AAAAAAAAARI/K8EtLyzV-vo/dn-n-s_thumb1.jpg?imgmax=800" title="dn n s" width="503" height="83" alt="dn n s" />](http://lh4.ggpht.com/-AF-eM-a6msc/T1yIE36MmgI/AAAAAAAAAQ4/xYNTR1Ry6pg/s1600-h/dn-n-s3.jpg)

Save the zip file, extract its contents, open the customizations.xml
file in Visual Studio (or your favorite XML editor). If you collapsed
all the nodes in the XML Editor, you will see that the SiteMap parent
node have many <span class="underline">Area</span> nodes. Each node
represents the major parts of CRM web client navigation, which are
available on the left bottom part of the window.

[<img src="http://lh3.ggpht.com/-Mz_JX5gpCCQ/T1yIGKriYHI/AAAAAAAAARY/rH2YrvunDas/sm_thumb.jpg?imgmax=800" title="sm" width="235" height="244" alt="sm" />](http://lh6.ggpht.com/-eZmW2alBgfQ/T1yIF3xqwgI/AAAAAAAAARQ/Xa9-LiL-PTU/s1600-h/sm2.jpg) [<img src="http://lh4.ggpht.com/-ZFD7HZ0-2mg/T1yIG0P84WI/AAAAAAAAARo/ND1U_WP0qmc/Areas_thumb.jpg?imgmax=800" title="Areas" width="188" height="192" alt="Areas" />](http://lh6.ggpht.com/-K5kwiVbIbQs/T1yIGXmsjgI/AAAAAAAAARg/j2BMfR1E5AU/s1600-h/Areas2.jpg)

Now expand the the area node with Id=”Workplace”, which represents the
Workplace in the web client. You will see Group nodes for each
sub-section of Workplace area

[<img src="http://lh5.ggpht.com/-rLCggse3v5E/T1yIHkoOTkI/AAAAAAAAAR4/6t3mVoT8QNc/sm-area_thumb.jpg?imgmax=800" title="sm area" width="187" height="134" alt="sm area" />](http://lh4.ggpht.com/-CDVsgEPEceA/T1yIHClnJ8I/AAAAAAAAARw/qyl9Mxc5aSg/s1600-h/sm-area2.jpg) [<img src="http://lh3.ggpht.com/-dkb922S3EgI/T1yIINRKA1I/AAAAAAAAASE/pK5IueTcTeA/wp_thumb.jpg?imgmax=800" title="wp" width="182" height="103" alt="wp" />](http://lh5.ggpht.com/-6qgMnhLs8WQ/T1yIIPtwvdI/AAAAAAAAAR8/LQiI-B56RuE/s1600-h/wp2.jpg)

Now expand the group node with Id=”MyWork”, which represents <span
class="underline">MyWork</span> in the web client. You will see SubArea
nodes for each sub-section of the MyWork area.

[<img src="http://lh5.ggpht.com/-_SBNW2Sk9a8/T1yIIw5JetI/AAAAAAAAASU/NpONpNbFV2I/sm-group_thumb.jpg?imgmax=800" title="sm group" width="244" height="232" alt="sm group" />](http://lh3.ggpht.com/-7DmY5H5zTKw/T1yIIuoQ75I/AAAAAAAAASQ/qL4spZOIgIc/s1600-h/sm-group2.jpg) [<img src="http://lh5.ggpht.com/-BsDxRKaLnL0/T1yIJxX9FPI/AAAAAAAAASs/3-ql4E5g22I/mw_thumb.jpg?imgmax=800" title="mw" width="164" height="214" alt="mw" />](http://lh3.ggpht.com/-0PFASe1lC40/T1yIJaONA5I/AAAAAAAAASg/8X-vYMXRorU/s1600-h/mw2.jpg)

Now let’s say we want to add the link to our web page web resource just
next to Dashboards under MyWork. Locate the SubArea with
Id="nav\_dashboards" and insert the following XML after it to make our
link

              
              

  
  

This xml adds two links on the SiteMap, both of them links to our web
page web resource. The first one uses the web resource direct URL which
can be used to access the web resource even from external systems (vice
versa, you can link other URLs directly to your CRM). To get the web
resource URL, navigate to <span class="underline">Settings</span> &gt;
<span class="underline">Customizations</span> &gt; <span
class="underline">Customize the System</span> &gt; click <span
class="underline">Web Resources</span> from left navigat &gt; double
click the desired web resource to open its properties dialog, you will
find the URL in the bottom of the form

  
  

[<img src="http://lh5.ggpht.com/-fnsqsRKhQGo/T1yIKpouR8I/AAAAAAAAAS4/dX1P5iHjCTc/WR%252520url_thumb%25255B1%25255D.jpg?imgmax=800" title="WR url" width="316" height="370" alt="WR url" />](http://lh3.ggpht.com/-G2Gab9LuQc4/T1yIKTHtB4I/AAAAAAAAASw/Fcfwf9oAU4Q/s1600-h/WR%252520url%25255B3%25255D.jpg)

  
  

The second link uses the keyword **$webresource** to reference the web
resource by name. We will talk about $webresource keyword in the
“Referencing Other Web Resources” section of this post.

  
  

Now its time to get these SiteMap modifications into CRM. Save
customizations.xml, Select all the exported solution files and add them
to a .Zip file, navigate to <span class="underline">Settings</span> &gt;
<span class="underline">Customization</span> &gt; <span
class="underline">Solutions</span> &gt; and click <span
class="underline">Import</span>. In the solution import dialog upload
your .Zip file, and click <span class="underline">Publish All
Customizations</span> at the end. If you navigate to your CRM home page
and refreshed the page you will see the links on the left

  
  

[<img src="http://lh4.ggpht.com/-rA8sUztaQMo/T1yILcjmN7I/AAAAAAAAATI/GC7ulFx3OXo/VER_thumb%25255B1%25255D.jpg?imgmax=800" title="VER" width="344" height="324" alt="VER" />](http://lh3.ggpht.com/-l7mqVDP18lc/T1yIK4d3nqI/AAAAAAAAATA/fRzkFs_G-C4/s1600-h/VER%25255B3%25255D.jpg)

  
  

**Using Web Resources as a Solution Configuration Page**

  
  

Solutions are containers that track customizations and allow it to be
moved around from server to server. When building a custom solution you
may want to add a page where you provide details about your solution and
its features. Configuration pages for solutions can fulfill your
requirement for such a page. Let’s see how we can use our web page web
resource as a solution configuration page. Navigate to Settings &gt;
Custo mization &gt; Solutions &gt; click your solution &gt; on the
Solution dialog click on the Information from the left navigation

  
  

[<img src="http://lh5.ggpht.com/-BuGt4wqUfUE/T1yIL03JvyI/AAAAAAAAATY/4hNLmC81kAU/sol%252520info_thumb.jpg?imgmax=800" title="sol info" width="201" height="171" alt="sol info" />](http://lh6.ggpht.com/-O2fzEaxPTDg/T1yILuTHZBI/AAAAAAAAATU/g4JnEFvNozQ/s1600-h/sol%252520info%25255B2%25255D.jpg)

  
  

Then choose our web page web resource in the Configuration Page textbox

  
  

[<img src="http://lh4.ggpht.com/-RdRNebmCbiw/T1yIMenWYuI/AAAAAAAAATs/6hSV3NRx77k/sol%252520info%2525202_thumb%25255B1%25255D.jpg?imgmax=800" title="sol info 2" width="408" height="351" alt="sol info 2" />](http://lh3.ggpht.com/-51GfeXGxesI/T1yIMCJ2XkI/AAAAAAAAATg/FL7-4obmRRQ/s1600-h/sol%252520info%2525202%25255B3%25255D.jpg)

  
  

Then Click <span class="underline">Save</span> and then Click <span
class="underline">Publish</span>. Now you will see a new link added on
the left navigation after the <span class="underline">Information</span>
link, it will be called <span class="underline">Configuration</span>

  
  

[<img src="http://lh5.ggpht.com/-QRzN3_wVvXI/T1yINVl3LEI/AAAAAAAAAT8/BY3H7_pLwQA/col%252520cnfg_thumb.jpg?imgmax=800" title="col cnfg" width="206" height="188" alt="col cnfg" />](http://lh6.ggpht.com/-W9TncUJ-q_o/T1yIMwsGCkI/AAAAAAAAAT0/1ZtYwWcaHp4/s1600-h/col%252520cnfg%25255B2%25255D.jpg)

  
  

if you click it, you will see our web page web resource on the right.

  
  

[<img src="http://lh5.ggpht.com/-dk55bK2LSDE/T1yIOGUk2mI/AAAAAAAAAUM/xhTfIqLng70/col%252520cnfg%2525202_thumb%25255B1%25255D.jpg?imgmax=800" title="col cnfg 2" width="403" height="365" alt="col cnfg 2" />](http://lh3.ggpht.com/-H46QUAoOR6k/T1yINivAqvI/AAAAAAAAAUE/srO-RAO8wt0/s1600-h/col%252520cnfg%2525202%25255B3%25255D.jpg)

  
  

**Referencing Other Web Resources**

  
  

While some web resources can be added directly to a form or a dashboard,
others can only be referenced through their relative path. There are
many ways you can use to reference Web Resources:

  
  

**$webresource Directive** You should use it when referencing a web
resource from XML like from a ribbon control, or a SiteMap sub area
(like what we did before). When using the $webresource directive,
Microsoft Dynamics CRM will create or update solution dependencies.

  
  

**Relative URL** You can use relative URL when referencing from HTML or
other areas that doesn’t support using $webresource. To make this works,
it is recommend that you use a consistent naming convention for the web
resources that reflect a virtual file structure. The solution
publisher’s customization prefix will always be included as a prefix to
the name of the web resource. This can represent a virtual ”root” folder
for all web resources added by that publisher. You can then use the
forward slash character (/) to simulate a folder structure that will be
honored by the web server.

  
  

From another web resource, you should always use relative URLs to
reference each other. For example, for the webpage web resource
`new_/content/c ontentpage.htm` to reference the CSS web
resource`new_/Styles/styles.css`, create the link as follows:

  
  

  
  

For the webpage web resource new\_/content/contentpage.htm to open the
webpage web resource isv\_/foldername/dialogpage.htm, create the link as
follows:

  
  

    Dialog Page

  
  

Full URL As web resources are URL accessible, you can open the
information dialog of any web resource and copy the URL in the bottom of
the window and use it anywhere you can use a URL (as we did before).

  
  

In this post we introduced the web resources feature in Microsoft
Dynamics CRM 2011. We started with exploring the different types of Web
Resources, where can Web Resources be Used in our customization
scenarios, and what is the limitations we have on using web resources.
Because web Page web resources are the containers that can host (or link
to) all the other web resource types, we explained all the ways to
incorporate Web Page web resources in Dynamics CRM. Then we explained
how to link to other types of web resources.
