--- 
title: "Microsoft Dynamics CRM 2011 for Developers | Creating Custom Reports Using Microsoft SQL Server 2008 Reporting Services" 
date: '2012-03-13T17:47:00.001-05:00' 
tags: 
    - Microsoft Dynamics CRM 2011 
    - FetchXML - Business Intelligence Development Studio 
    - Business Intelligence Development Studio CRM Report Authoring Extension 
    - SQL Server Reporting Services 
modified_time: '2012-03-22T15:37:19.495-05:00' 
thumbnail: http://lh6.ggpht.com/-Y3DcxYmCUtY/T1\_OGFZOA4I/AAAAAAAAAVY/TRW6PnSCuSE/s72-c/xRM\_Demo2---Microsoft-Visual-Studio\_.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-7721924274916416097
blogger_orig_url: http://ebeid-soliman.blogspot.com/2012/03/microsoft-dynamics-crm-2011-for\_14.html
---

#### **Contents**

1.  Introduction
2.  Setup the Development Environment
3.  Report Development Process
4.  Create Custom Reports Using Business Intelligence Development Studio
    1.  Create a Custom SQL-Based Report
    2.  Create a Custom Fetch-Based Report
5.  Import Custom Reports into Dynamics CRM

**Introduction**

Microsoft Dynamics CRM provides many out-of-box reports for viewing
business data. You can view a list of reports you have access to by
navigating to Workplace &gt; My Work &gt; Reports. You can also see a
list of all reports available by navigating to Settings &gt;
Customization &gt; Customizations &gt; Customize the System &gt; Report
\[left navigation\]. In both lists, you can select a report and click
Run Report from the ribbon to preview the report in running mode.

You can create custom reports using one of the out-of-box reports as
templates, or create a custom report from scratch. There are two types
of reports in Microsoft Dynamics CRM:

-   **SQL-Based Reports** Use SQL queries to retrieve data from filtered
    views defined by the system. The default out-of-box reports are
    SQL-based reports. You can’t deploy SQL-based reports for Dynamics
    CRM online.
-   **Fetch-Based Reports** Use FetchXML queries to retrieve data. They
    are introduced in Dynamics CRM 2011 and can be deployed both on
    on-premise and online. All reports created using the Report Wizard
    in the web interface, are fetch-based reports.

**Setup the Development Environment**

To write custom reports for Microsoft Dynamics CRM you need the
following:

-   Microsoft SQL Server 2008 Reporting Services (or 2008 R2) in native
    mode installation.
-   Business Intelligence Development Studio. This is the report
    authoring environment in Visual Studio that hosts the Report
    Designer (available on the Microsoft SQL Server setup CD).
-   Microsoft Dynamics CRM Report Authoring Extension. You will need
    this when creating a custom fetch-based reports. You can install it
    from <http://www.microsoft.com/download/en/details.aspx?id=27823> or
    from the BIDSExtension folder in the Microsoft Dynamics CRM setup
    DVD.

**Report Development Process**

The following lists the steps for developing custom Microsoft Dynamics
CRM reports. You may have to repeat some steps while you develop a
report:

1.  Develop a report concept or specification based on what business
    information is to be displayed.
2.  Decide on the type of report you want to create: SQL-based or
    Fetch-based. Microsoft Dynamics CRM Online users can only create
    custom Fetch-based reports.
3.  Download an existing Microsoft Dynamics CRM report definition
    (.rdl), and modify it or create a new report by using Business
    Intelligence Development Studio.
4.  Create basic report parameters.
5.  Specify datasets and filtering criteria for retrieving data:
    -   For SQL-based reports, create datasets that contain Microsoft
        Dynamics CRM data obtained from the filtered views.
    -   Enable pre-filtering on the primary entities.
6.  Define the basic layout of the report, including headers and
    footers.
7.  Add report items as required based on the report specification.
8.  Preview the report in Microsoft Visual Studio, and resolve any
    errors.
9.  Deploy the report to the reporting server by using Microsoft
    Dynamics CRM.
10. Run the deployed report to verify.

**Create Custom Reports Using Business Intelligence Development Studio**

**Create a Custom SQL-Based Report**

To create a c ustom SQL-based report using Business Intelligence
Development Studio:

1- Open Business Intelligence Development Studio, and create a report
server project.

[<img src="http://lh6.ggpht.com/-Y3DcxYmCUtY/T1_OGFZOA4I/AAAAAAAAAVY/TRW6PnSCuSE/xRM_Demo2---Microsoft-Visual-Studio_.jpg?imgmax=800" title="xRM_Demo2 - Microsoft Visual Studio_2012-03-12_17-50-44" width="425" height="336" alt="xRM_Demo2 - Microsoft Visual Studio_2012-03-12_17-50-44" />](http://lh6.ggpht.com/-dpQXMjSJORM/T1_OFc1tU5I/AAAAAAAAAVQ/LrYaco45lgo/s1600-h/xRM_Demo2---Microsoft-Visual-Studio_%25255B9%25255D.jpg)

2- In Solution Explorer, right-click the **Reports** folder, and then
click **Add New Report**.

[<img src="http://lh5.ggpht.com/-H6CmuImhX9Q/T1_OHNdBeCI/AAAAAAAAAVo/3ERMLfAzNCE/xRM_Demo2---Microsoft-Visual-Studio_%25255B6%25255D.jpg?imgmax=800" title="xRM_Demo2 - Microsoft Visual Studio_2012-03-12_17-51-26" width="244" height="196" alt="xRM_Demo2 - Microsoft Visual Studio_2012-03-12_17-51-26" />](http://lh5.ggpht.com/-HuqXDtblv-M/T1_OGiUnurI/AAAAAAAAAVg/mu5unb1ioTM/s1600-h/xRM_Demo2---Microsoft-Visual-Studio_%25255B11%25255D.jpg)

3- Click **Next** on the Report Wizard welcome screen.

4- On the Select the Data Source page, click **New Data Source**, and
specify the following details:

-   **Name**: Type a name for the data source.
-   **Type**: Select **Microsoft SQL Server**.

[<img src="http://lh4.ggpht.com/-cwE2c2LUgIQ/T1_OICi0F4I/AAAAAAAAAV4/XPkIUT09lQY/Report-Wizard_2012-03-12_17-53-25_th.jpg?imgmax=800" title="Report Wizard_2012-03-12_17-53-25" width="418" height="396" alt="Report Wizard_2012-03-12_17-53-25" />](http://lh4.ggpht.com/-GRyw77MrdHg/T1_OHp9KsKI/AAAAAAAAAVw/LRssllCzblU/s1600-h/Report-Wizard_2012-03-12_17-53-253.jpg)

-   **Connection String**: Specify the connection string to connect to
    the instance of the Microsoft SQL Server database. To build the
    connection string, click **Edit**. To supply credentials, click
    **Credentials**. Click **Next**.

> [<img src="http://lh4.ggpht.com/-8NdXpHqC6x4/T1_OJO1cwhI/AAAAAAAAAWI/QCqFQJkEdq0/Connection-Properties_2012-03-12_17-%25255B2%25255D.jpg?imgmax=800" title="Connection Properties_2012-03-12_17-54-53" width="306" height="423" alt="Connection Properties_2012-03-12_17-54-53" />](http://lh4.ggpht.com/-1GYV0Eewvp0/T1_OIw9RrQI/AAAAAAAAAWA/5v3Zzg13CUQ/s1600-h/Connection-Properties_2012-03-12_17-%25255B1%25255D.jpg)

3- On the Design the Query page, type the SQL query to use in the
report. You could also click Query Builder button to open the Query
Builder window. Right click in the empty area at the top of the dialog
and choose Add Table

[<img src="http://lh4.ggpht.com/-CPgcop5iBOU/T1_OKKdASxI/AAAAAAAAAWY/dpp2wtSTqyM/xRM_Demo2---Microsoft-Visual-Studio_%25255B4%25255D.jpg?imgmax=800" title="xRM_Demo2 - Microsoft Visual Studio_2012-03-12_17-58-43" width="327" height="248" alt="xRM_Demo2 - Microsoft Visual Studio_2012-03-12_17-58-43" />](http://lh3.ggpht.com/-42i9hc-FEd8/T1_OJePyrsI/AAAAAAAAAWQ/sfIXXeOKwLY/s1600-h/xRM_Demo2---Microsoft-Visual-Studio_%25255B8%25255D.jpg)

then click on the Views tab, hold the CTRL key and and select the views
that you will use in your report and click Add

[<img src="http://lh4.ggpht.com/-34I9mJJmHaE/T1_OKjvSE4I/AAAAAAAAAWo/wdwjAUS4Rjk/Add-Table_2012-03-12_17-59-13_thumb2.jpg?imgmax=800" title="Add Table_2012-03-12_17-59-13" width="313" height="256" alt="Add Table_2012-03-12_17-59-13" />](http://lh4.ggpht.com/-u-BC28YWmrM/T1_OKS3P33I/AAAAAAAAAWg/cNGBQyQtJsM/s1600-h/Add-Table_2012-03-12_17-59-134.jpg)

select the columns you want, test your query results \[We just retrieved
the account name, city, country\]

[<img src="http://lh6.ggpht.com/-dJMzL2DTtbg/T1_OLQzxRPI/AAAAAAAAAW4/HXYeiYeVVOo/Query-Designer_2012-03-12_18-02-20_t.jpg?imgmax=800" title="Query Designer_2012-03-12_18-02-20" width="325" height="253" alt="Query Designer_2012-03-12_18-02-20" />](http://lh6.ggpht.com/-q69G8B1Z3LI/T1_OK_6jW2I/AAAAAAAAAWw/IMHVnCPdlqQ/s1600-h/Query-Designer_2012-03-12_18-02-203.jpg)

when you satisfied with your query results, click Ok to use the query in
the report

[<img src="http://lh5.ggpht.com/-dvLZehKl9Zo/T1_OL0zSKtI/AAAAAAAAAXI/hAwrUU0kNkA/Report-Wizard_2012-03-12_18-03-19_th.jpg?imgmax=800" title="Report Wizard_2012-03-12_18-03-19" width="394" height="373" alt="Report Wizard_2012-03-12_18-03-19" />](http://lh3.ggpht.com/-38xP0A3cYtg/T1_OLix99tI/AAAAAAAAAXA/ryQClGMbgZc/s1600-h/Report-Wizard_2012-03-12_18-03-193.jpg)

click **Next**.

4- On the Select the Report Type page, select a **Tabular** report or a
**Matrix** report, and click **Next**. \[we used Tabular, which is the
most common report format\]

[<img src="http://lh3.ggpht.com/-Kdft8hCzlbQ/T1_OMtBBSXI/AAAAAAAAAXY/twXUbKZeslI/Report-Wizard_2012-03-12_18-03-24_th.jpg?imgmax=800" title="Report Wizard_2012-03-12_18-03-24" width="360" height="341" alt="Report Wizard_2012-03-12_18-03-24" />](http://lh4.ggpht.com/-wutKFJhRhKw/T1_OMV7v2cI/AAAAAAAAAXQ/5fsNV61SNxc/s1600-h/Report-Wizard_2012-03-12_18-03-243.jpg)

5- Specify the fields that will be included in the report. You can add
fields in three different sections \[Page, Group, Details\]. Page can be
used for granular grouping like Country in our case, it will displayed
on the page header only. Group can be used to more specific grouping
within the page, like City in our case. Details is the place where
individual records will be rendered, like our accounts names. Select
each column name from the list on the left and click the designated
section button to add the column to it.

[<img src="http://lh4.ggpht.com/-NInQF22cCTY/T1_ONviq_9I/AAAAAAAAAXo/LOQ1EnZeqRw/Report-Wizard_2012-03-12_18-04-41_th.jpg?imgmax=800" title="Report Wizard_2012-03-12_18-04-41" width="393" height="372" alt="Report Wizard_2012-03-12_18-04-41" />](http://lh4.ggpht.com/-BxjJIuildAU/T1_ONBmIaQI/AAAAAAAAAXg/V68o0DFOYaU/s1600-h/Report-Wizard_2012-03-12_18-04-413.jpg)

Then click **Next**.

6- Select a stepped layout and click **Next**.

[<img src="http://lh5.ggpht.com/-cSGKTbr0LVU/T1_OORjAa1I/AAAAAAAAAX4/tYqLzC6gFzA/Report-Wizard_2012-03-12_18-05-16_th.jpg?imgmax=800" title="Report Wizard_2012-03-12_18-05-16" width="402" height="380" alt="Report Wizard_2012-03-12_18-05-16" />](http://lh3.ggpht.com/-ehUcLZUoDqc/T1_OOCCb6yI/AAAAAAAAAXw/dK_BXtWM4OM/s1600-h/Report-Wizard_2012-03-12_18-05-163.jpg)

7- Select a style to apply to the report, and then click **Next**.

[<img src="http://lh6.ggpht.com/-Fx1LCowXTow/T1_OPPde5lI/AAAAAAAAAYI/uovII7alBgo/Report-Wizard_2012-03-12_18-05-22_th.jpg?imgmax=800" title="Report Wizard_2012-03-12_18-05-22" width="411" height="389" alt="Report Wizard_2012-03-12_18-05-22" />](http://lh5.ggpht.com/-rNKs_52bvZ4/T1_OO_UKuOI/AAAAAAAAAYA/vBLwv4xrNzI/s1600-h/Report-Wizard_2012-03-12_18-05-223.jpg)

8- Verify the fields that will be included in the report, and name the
report. Click **Finish**.

[<img src="http://lh4.ggpht.com/-aqJAQ5lEjqI/T1_OPzj1dlI/AAAAAAAAAYc/Dv0CryRlA7o/Report-Wizard_2012-03-12_18-05-28_th.jpg?imgmax=800" title="Report Wizard_2012-03-12_18-05-28" width="418" height="396" alt="Report Wizard_2012-03-12_18-05-28" />](http://lh4.ggpht.com/-N4_zRUgIibI/T1_OPRoL-YI/AAAAAAAAAYQ/ZAx5mUETiKc/s1600-h/Report-Wizard_2012-03-12_18-05-283.jpg)

This will generate an .rdl file with the specified report name. You can
use the .rdl file to publish your custom report in Microsoft Dynamics
CRM.

[<img src="http://lh6.ggpht.com/-NiKkjlZGpZY/T1_OQxwrzvI/AAAAAAAAAYs/iabF3iYieqk/xRM_Demo2---Microsoft-Visual-Studio_%25255B1%25255D.jpg?imgmax=800" title="xRM_Demo2 - Microsoft Visual Studio_2012-03-12_18-07-31" width="459" height="367" alt="xRM_Demo2 - Microsoft Visual Studio_2012-03-12_18-07-31" />](http://lh4.ggpht.com/-Rvqzd4CmHe8/T1_OQcbHT1I/AAAAAAAAAYk/hbJifDq7UQk/s1600-h/xRM_Demo2---Microsoft-Visual-Studio_%25255B5%25255D.jpg)

**Create a Custom Fetch-Based Report**

Creating a custom Fetch-based report is similar to creating a custom
SQL-based report except for the data source name and the report query
specified while creating the report definition.

Since you have the capability to create SQL-based reports for
on-premise, most people will not use Fetch-based reports for on-premise.
Let’s learn how to get the data source name for our CRM On-Line
organization. It consists of:

-   <span class="underline">Organization URL</span> something like
    <https://xrmdemo5.crm.dynamics.com>
-   <span class="underline">Organization unique name</span> you can get
    it by navigating to <span class="underline">Settings</span> &gt;
    <span class="underline">Customization</span> &gt; <span
    class="underline">Customizations</span> &gt; <span
    class="underline">Developer Resources</span> &gt; it will be on this
    page

[<img src="http://lh5.ggpht.com/-e3_Ay73_fO0/T1_ORuKnrPI/AAAAAAAAAY8/qtLZf5qqG9I/Developer%252520res_thumb%25255B1%25255D.jpg?imgmax=800" title="Developer res" width="410" height="398" alt="Developer res" />](http://lh4.ggpht.com/-t8Ik73WXzeY/T1_ORW2bumI/AAAAAAAAAY0/wI7veidjHGM/s1600-h/Developer%252520res%25255B3%25255D.jpg)

Put the two parts separated by semi-colon will form your connection
string, like
[](https://xrmdemo5.crm.dynamics.com "https://xrmdemo5.crm.dynamics.com")[https://xrmdemo5.crm.dynamics.com](https://xrmdemo5.crm.dynamics.com;4c69b8c565264033b4707c804cba7aa2);4c69b8c565264033b4707c804cba7aa2
put that connection string in a text file for later use.

Now, lets learn how to create a query for our Fetch-based report. There
are two ways to do that:

1.  Manually type the FetchXML query (which I don’t personally prefer)
2.  Obtain the FetchXML queries from the CRM web client and then modify
    it.

To obtain FetchXML queries you can navigate to any entity listing in CRM
web client, like Accounts. Then click Advanced Find on the ribbon

[<img src="http://lh6.ggpht.com/-sGJJEM86OYE/T1_OSVXZXrI/AAAAAAAAAZM/S1Vo1Qp_eiE/adv%252520fnd_thumb%25255B1%25255D.png?imgmax=800" title="adv fnd" width="251" height="113" alt="adv fnd" />](http://lh4.ggpht.com/-cGFULnOxXAU/T1_OR2Lp0HI/AAAAAAAAAZE/y19B3ipN-R4/s1600-h/adv%252520fnd%25255B3%25255D.png)

This will open the Advanced Find dialog

[<img src="http://lh3.ggpht.com/-XzCCoxYngRI/T1_OTcxScqI/AAAAAAAAAZc/eH_P0gUM6dw/adv%252520fnd%2525202_thumb%25255B1%25255D.jpg?imgmax=800" title="adv fnd 2" width="436" height="260" alt="adv fnd 2" />](http://lh4.ggpht.com/-_0B4c0N_rC4/T1_OS8U9iNI/AAAAAAAAAZU/J4C6sWsjDc4/s1600-h/adv%252520fnd%2525202%25255B3%25255D.jpg)

Then click New to start creating a new query.

1- You can select the Entity (Table) from the <span
class="underline">Look For</span> combo-box.

2- You can create your query where conditions. Click <span
class="underline">Select</span> link to select the desired column

[<img src="http://lh3.ggpht.com/-tbwWbtpCyEg/T1_OUD2XgHI/AAAAAAAAAZs/Y_MjUsGFOXQ/adv%252520fnd%2525203_thumb%25255B2%25255D.jpg?imgmax=800" title="adv fnd 3" width="384" height="390" alt="adv fnd 3" />](http://lh6.ggpht.com/-LKJpI_VuIyE/T1_OTxtDkeI/AAAAAAAAAZk/fLGbvPwg_Pc/s1600-h/adv%252520fnd%2525203%25255B4%25255D.jpg)

You can then click <span class="underline">Equals</span> link to specify
the operator used in the where condition. You can then click <span
class="underline">Enter Text</span> link to specify the value used in
the condition

[<img src="http://lh3.ggpht.com/-yj21oCGB1qQ/T1_OVOofT%0AaI/AAAAAAAAAZ8/hK5jD0w8oiM/adv%252520fnd%2525204_thumb%25255B4%25255D.jpg?imgmax=800" title="adv fnd 4" width="378" height="240" alt="adv fnd 4" />](http://lh4.ggpht.com/-3-kYmbBMvOw/T1_OUo6e1OI/AAAAAAAAAZ0/D3fap7E_6-4/s1600-h/adv%252520fnd%2525204%25255B6%25255D.jpg)[<img src="http://lh5.ggpht.com/-dLoYf_r0YuQ/T1_OVj3raUI/AAAAAAAAAaM/la9i_91CK2o/adv%252520fnd%2525205_thumb%25255B2%25255D.jpg?imgmax=800" title="adv fnd 5" width="380" height="233" alt="adv fnd 5" />](http://lh4.ggpht.com/-g52z0YfZIYA/T1_OVetvodI/AAAAAAAAAaE/UiUt7ydKlL0/s1600-h/adv%252520fnd%2525205%25255B4%25255D.jpg)

when you have multiple conditions, you can select them and use the <span
class="underline">Group AND</span> and <span class="underline">Group
OR</span> on the ribbon to build your query logic.

3- You can specify the columns you want retrieve. Click Edit Columns in
the ribbon, this will open the Edit Columns dialog

[<img src="http://lh4.ggpht.com/-E90-9rz0vWw/T1_OWabb3lI/AAAAAAAAAac/iUpd74konwU/Edit%252520Columns%252520--%252520Webpage%252520Dialog_2012-03-13_13-07-57_thumb%25255B1%25255D.jpg?imgmax=800" title="Edit Columns -- Webpage Dialog_2012-03-13_13-07-57" width="368" height="222" alt="Edit Columns -- Webpage Dialog_2012-03-13_13-07-57" />](http://lh4.ggpht.com/-mR3GFdPsQp4/T1_OV4JVPoI/AAAAAAAAAaU/fNILclJTDVA/s1600-h/Edit%252520Columns%252520--%252520Webpage%252520Dialog_2012-03-13_13-07-57%25255B3%25255D.jpg)

The area on the left shows the query columns and the sequence they
appear. You can click <span class="underline">Add Columns</span> from
the left to add more columns from this entity or any of entities related
to it.

[<img src="http://lh4.ggpht.com/-wHFl3AqUN6Y/T1_OXJbEBOI/AAAAAAAAAas/yyTqiOED5Yo/Add%252520Columns%252520--%252520Webpage%252520Dialog_2012-03-13_13-10-04_thumb%25255B1%25255D.jpg?imgmax=800" title="Add Columns -- Webpage Dialog_2012-03-13_13-10-04" width="345" height="317" alt="Add Columns -- Webpage Dialog_2012-03-13_13-10-04" />](http://lh3.ggpht.com/-vyXgT5-xjmo/T1_OW4R4jMI/AAAAAAAAAak/S6DipAJxsPo/s1600-h/Add%252520Columns%252520--%252520Webpage%252520Dialog_2012-03-13_13-10-04%25255B3%25255D.jpg)

Select Address 1: City and Address 1: Country and click Ok.

4- You can specify the query sorting. Click Configure Sorting on the
left to open the Configure Sort Order dialog

[<img src="http://lh6.ggpht.com/-cXNQ5fZespE/T1_OX1RXyiI/AAAAAAAAAa8/6jqBLeXFmbg/Configure%252520Sort%252520Order_thumb%25255B1%25255D.jpg?imgmax=800" title="Configure Sort Order" width="326" height="307" alt="Configure Sort Order" />](http://lh3.ggpht.com/-A11tUiNzM5Q/T1_OXmLNd7I/AAAAAAAAAa0/mflhQcJZu0k/s1600-h/Configure%252520Sort%252520Order%25255B3%25255D.jpg)

You can specify two columns only for the sorting criteria.

5- You can remove any column by click its name on the right and click
<span class="underline">Remove</span> from the left.

When you done with editing the query columns click <span
class="underline">OK</span> to return to the <span
class="underline">Advanced Find</span> window. Now, click Download Fetch
XML on the ribbon to download the Fetch query in a .xml file format to
use inside SQL Business Intelligence Development Studio.

Now to add a custom Fetch-based report to our Report project, Right
click **Reports** folder and click **Add New Report**. Click Next on the
Report Wizard welcome screen.

1- On the Sele ct the Data Source page, click **New Data Source**, and
specify the following details:

-   **Name**: Type a name for the data source.
-   **Type**: Select **Microsoft Dynamics CRM Fetch**.
-   **Connection String**: copy the connection string we prepared
    earlier and past it here.
-   Click on <span class="underline">Credentials</span> and enter your
    live account and password you used in CRM Online and click Ok. Then
    click <span class="underline">Next</span>

[<img src="http://lh3.ggpht.com/-CazEx_VuOnY/T1_OYyWMzDI/AAAAAAAAAbM/h1XU8f6aHmU/Data%252520Source%252520Credentials_2012-03-13_15-07-56_thumb%25255B1%25255D.jpg?imgmax=800" title="Data Source Credentials_2012-03-13_15-07-56" width="383" height="351" alt="Data Source Credentials_2012-03-13_15-07-56" />](http://lh5.ggpht.com/-qI1zanzK3Cs/T1_OYYvU2iI/AAAAAAAAAbE/oevV7XyVsvA/s1600-h/Data%252520Source%252520Credentials_2012-03-13_15-07-56%25255B3%25255D.jpg)

2- On the Design the Query page, click on <span class="underline">Query
Builder</span>. On the Query Designer dialog, click <span
class="underline">Import</span> and browse to the xml file you
downloaded earlier.

[<img src="http://lh6.ggpht.com/-wp60SxS01EU/T1_OZuewrSI/AAAAAAAAAbc/FCFDwfMHPEM/Query%252520Designer_2012-03-13_15-24-04_thumb%25255B2%25255D.jpg?imgmax=800" title="Query Designer_2012-03-13_15-24-04" width="494" height="338" alt="Query Designer_2012-03-13_15-24-04" />](http://lh6.ggpht.com/-p37QAViwHSM/T1_OZPDm-1I/AAAAAAAAAbU/6ccY9T7Zro0/s1600-h/Query%252520Designer_2012-03-13_15-24-04%25255B4%25255D.jpg) 

You can click on Run to test the query. Click Ok to close the Query
Designer dialog, and Click Next.

Complete the Wizard steps just like the SQL-based report, it is the
same.

As you can create queries using Business Intelligence Development
Studio, you can also use it to modify complex queries.

**Import Custom Reports into Dynamics CRM**

To complete the cycle and let the report used by your organization, you
need to import it into CRM. Follow the following steps to import our
report:

1- Navigate to <span class="underline">My Work</span> &gt; <span
class="underline">Reports</span> &gt; click <span
class="underline">New</span> on the ribbon. The <span
class="underline">New Report</span> window will open.

[<img src="http://lh6.ggpht.com/--baZR7XNpVU/T1_OavTUzyI/AAAAAAAAAbs/0cr62JVNWOA/Report%252520New%252520-%252520Windows%252520Internet%252520Explorer_2012-03-13_17-07-32_thumb%25255B2%25255D.jpg?imgmax=800" title="Report New - Windows Internet Explorer_2012-03-13_17-07-32" width="423" height="435" alt="Report New - Windows Internet Explorer_2012-03-13_17-07-32" />](http://lh5.ggpht.com/-anZBNpdszCo/T1_OaDa9xzI/AAAAAAAAAbk/mHxTnCZRGcg/s1600-h/Report%252520New%252520-%252520Windows%252520Internet%252520Explorer_2012-03-13_17-07-32%25255B4%25255D.jpg)

Click <span class="underline">Browse</span> and select your .rdl report
file. Enter the report name. Near the bottom of the window there is a
Display In field which decides areas where your reports will be
displayed. By default new reports will be displayed in Reports area, 
You can click the eclipse button if you want to make it displayed in
forms or lists of the related entities, then select desired values and
move them to <span class="underline">Selected Values</span> list.

[<img src="http://lh3.ggpht.com/-By9HkNWChN8/T1_Obf-qgWI/AAAAAAAAAb8/cV8cGrcA2J0/Select%252520Values%252520--%252520Webpage%252520Dialog_2012-03-13_17-20-21_thumb%25255B1%25255D.jpg?imgmax=800" title="Select Values -- Webpage Dialog_2012-03-13_17-20-21" width="315" height="242" alt="Select Values -- Webpage Dialog_2012-03-13_17-20-21" />](http://lh4.ggpht.com/-vyGO7lQCLtM/T1_Oa7-pYsI/AAAAAAAAAb0/WZhBBqgxsKs/s1600-h/Select%252520Values%252520--%252520Webpage%252%0A520Dialog_2012-03-13_17-20-21%25255B3%25255D.jpg)

In the New Report window, if you want to make the report accessible by
the whole organization click the Administration tab and change the <span
class="underline">Viewable By</span> field from Individual to
Organization.

[<img src="http://lh5.ggpht.com/-F3ujXmMMBtQ/T1_OcCH9MLI/AAAAAAAAAcM/9EY7jbczHZA/Report%252520New%252520-%252520Windows%252520Internet%252520Explorer_2012-03-13_17-14-18_thumb%25255B3%25255D.jpg?imgmax=800" title="Report New - Windows Internet Explorer_2012-03-13_17-14-18" width="423" height="439" alt="Report New - Windows Internet Explorer_2012-03-13_17-14-18" />](http://lh3.ggpht.com/-hbRCYFBZ-M4/T1_ObrMdi3I/AAAAAAAAAcE/BRluTrS-xqY/s1600-h/Report%252520New%252520-%252520Windows%252520Internet%252520Explorer_2012-03-13_17-14-18%25255B5%25255D.jpg)

Click <span class="underline">Save and Close</span>. Now our report will
be available in the Reports area of configured accessibility level
\[Organization or Individual\].

> To copy a report between organizations or deployments, include the
> report and any custom entities the report uses in a solution. This
> ensures that the entity types are mapped automatically by the system

In this post we used the Business Intelligence Development Studio to
create both SQL-based and Fetch-based custom reports for on-premise and
on-line CRM deployments. We also learned how to upload our reports to
Dynamics CRM and make them accessible to the whole organization and
through many access points.
