---
title: 'Microsoft Dynamics CRM 2011 for Developers | Creating Custom Reports Using Microsoft SQL Server 2008 Reporting Services'
date: 2012-03-13T17:47:00.001-05:00
draft: false
url: /2012/03/microsoft-dynamics-crm-2011-for_14.html
tags: 
- Microsoft Dynamics CRM 2011
- FetchXML
- Business Intelligence Development Studio
- Business Intelligence Development Studio CRM Report Authoring Extension
- SQL Server Reporting Services
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

Microsoft Dynamics CRM provides many out-of-box reports for viewing business data. You can view a list of reports you have access to by navigating to Workplace > My Work > Reports. You can also see a list of all reports available by navigating to Settings > Customization > Customizations > Customize the System > Report \[left navigation\]. In both lists, you can select a report and click Run Report from the ribbon to preview the report in running mode.

You can create custom reports using one of the out-of-box reports as templates, or create a custom report from scratch. There are two types of reports in Microsoft Dynamics CRM:

*   **SQL-Based Reports** Use SQL queries to retrieve data from filtered views defined by the system. The default out-of-box reports are SQL-based reports. You can’t deploy SQL-based reports for Dynamics CRM online.
*   **Fetch-Based Reports** Use FetchXML queries to retrieve data. They are introduced in Dynamics CRM 2011 and can be deployed both on on-premise and online. All reports created using the Report Wizard in the web interface, are fetch-based reports.

**Setup the Development Environment**

To write custom reports for Microsoft Dynamics CRM you need the following:

*   Microsoft SQL Server 2008 Reporting Services (or 2008 R2) in native mode installation.
*   Business Intelligence Development Studio. This is the report authoring environment in Visual Studio that hosts the Report Designer (available on the Microsoft SQL Server setup CD).
*   Microsoft Dynamics CRM Report Authoring Extension. You will need this when creating a custom fetch-based reports. You can install it from [http://www.microsoft.com/download/en/details.aspx?id=27823](http://www.microsoft.com/download/en/details.aspx?id=27823 "http://www.microsoft.com/download/en/details.aspx?id=27823") or from the BIDSExtension folder in the Microsoft Dynamics CRM setup DVD.

**Report Development Process**

The following lists the steps for developing custom Microsoft Dynamics CRM reports. You may have to repeat some steps while you develop a report:

1.  Develop a report concept or specification based on what business information is to be displayed.
2.  Decide on the type of report you want to create: SQL-based or Fetch-based. Microsoft Dynamics CRM Online users can only create custom Fetch-based reports.
3.  Download an existing Microsoft Dynamics CRM report definition (.rdl), and modify it or create a new report by using Business Intelligence Development Studio.
4.  Create basic report parameters.
5.  Specify datasets and filtering criteria for retrieving data:
    *   For SQL-based reports, create datasets that contain Microsoft Dynamics CRM data obtained from the filtered views.
    *   Enable pre-filtering on the primary entities.
6.  Define the basic layout of the report, including headers and footers.
7.  Add report items as required based on the report specification.
8.  Preview the report in Microsoft Visual Studio, and resolve any errors.
9.  Deploy the report to the reporting server by using Microsoft Dynamics CRM.
10.  Run the deployed report to verify.

**Create Custom Reports Using Business Intelligence Development Studio**

**Create a Custom SQL-Based Report**

To create a custom SQL-based report using Business Intelligence Development Studio:

1- Open Business Intelligence Development Studio, and create a report server project.

[![xRM_Demo2 - Microsoft Visual Studio_2012-03-12_17-50-44](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgHrBDQZP7aSR7xQNrxlHfUdL_RJOHkVCbWg6eiv3o85ndACBXovhkGJBx85eEv9Bo4Za0FVMv2ctAT78Fx0YeiaI7JV77zUfV-pZxi8BIEp4Baiv8MgTJ2nAMv_rxt68_1-aWMKbmmOQ/?imgmax=800 "xRM_Demo2 - Microsoft Visual Studio_2012-03-12_17-50-44")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhTHMGezdBAiSyI0zCF6hvVq4Th4vT8ZmqsQ6XV86MgObJbbCaRp35cy1bU8nkBjMHK9J0b1dlDm2Y3zfp5GDpdQzDrVhsBBTm0Uet_ptbohnxu_nAak7bujyA4ogSPfP3MvXDzsy1pag/s1600-h/xRM_Demo2---Microsoft-Visual-Studio_%25255B9%25255D.jpg)

2- In Solution Explorer, right-click the **Reports** folder, and then click **Add New Report**.

[![xRM_Demo2 - Microsoft Visual Studio_2012-03-12_17-51-26](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgnWkHr5ST19WEzL63yFMJoeDCU67FVGUJBi4m-kKRxd-F2HV6ed_GsvhBSh-BUUMUgOTnj-j_f6BKqu8v3zUaeF7uQaPcUsn4cgrsYCh4nWr5zDlsNU0X5ILvSnBTadBmpKc2erIsMMw/?imgmax=800 "xRM_Demo2 - Microsoft Visual Studio_2012-03-12_17-51-26")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjP6s0ZXJJrmdHBkUqyCRmT7G6NTpU-dbrAeZQlof-KE4xAEZDQ4nSc8TNzD9nJQEkfimcvdFMsFuR6_lTzD1ts4sca7c9lLajNQH5NhFeZTk0l-trA_UOlG-s1USq9CJ6DyNFBj5r-2g/s1600-h/xRM_Demo2---Microsoft-Visual-Studio_%25255B11%25255D.jpg)

3- Click **Next** on the Report Wizard welcome screen.

4- On the Select the Data Source page, click **New Data Source**, and specify the following details:

*   **Name**: Type a name for the data source.
*   **Type**: Select **Microsoft SQL Server**.

[![Report Wizard_2012-03-12_17-53-25](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjEaSOkoqeVALzK8txJ2og2fK4YOst-fykrXMezDY8cXlMQVnvn43eowvbGxVAijyyiimqu47xPKGe-i4BST8Cm0NG8N4xZnK6XircDh8eoGWin00O5qAFUYK4OUs8G5X2m348pStbDEQ/?imgmax=800 "Report Wizard_2012-03-12_17-53-25")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhEwecuQp3ohBvtUAgARruNL7JyL6zZZLXY1WOM518UZca-kbVjqi4QoxzXcXaki24DKv6dcBLNHZuyLHjiG9yeGBmkJvEZjEZXLJeZ3LQMaA4vxU5atnPFLOMUxM0wRpWkgLquqtX3NA/s1600-h/Report-Wizard_2012-03-12_17-53-253.jpg)

*   **Connection String**: Specify the connection string to connect to the instance of the Microsoft SQL Server database. To build the connection string, click **Edit**. To supply credentials, click **Credentials**. Click **Next**.

> [![Connection Properties_2012-03-12_17-54-53](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiLeBfyodAk5IU5UysZglMwc5rrgAG4GsLAmHVZI3uu0ctHV-1XQauqlm6grZX-idwCf5SLtR7hrKouDn8nNTyy8cDOHMTRUATOi-83pvMeSASUwKkIIrY-6DIVpMPS54d20FjU_7MlBQ/?imgmax=800 "Connection Properties_2012-03-12_17-54-53")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi1eHOkqn4ragwHViekyMuY5Qkd9NzRRlSLMM5-69dfqqFhZjS5Vlr1uR09HBDMdiek1EzLib-bXUx_-GJmh5VkJTMnoRA4UIBoYbjFSYzxKmfGXedmJmVgMjHD0zcE2RRtolIHABDcfQ/s1600-h/Connection-Properties_2012-03-12_17-%25255B1%25255D.jpg)

3- On the Design the Query page, type the SQL query to use in the report. You could also click Query Builder button to open the Query Builder window. Right click in the empty area at the top of the dialog and choose Add Table

[![xRM_Demo2 - Microsoft Visual Studio_2012-03-12_17-58-43](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjTIt-BwZMMeh1wgq65TxpBu5fsca05kVw71I98RFTc_DwcNsI74yepvvlFDiZDdsW3ZPZixDBLKttJg2C-cqfRoP9HXeItbbJplHeEOlWvutDXzjJBNZCUGOkRa12fPrEDnrG0jCbIFQ/?imgmax=800 "xRM_Demo2 - Microsoft Visual Studio_2012-03-12_17-58-43")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgVVkE92FefdKNN4WKLZu-sr-yP8ofw4wDJWnIQfatPTZ_2qjA_Xg86gtlbigp9n0uSta-yptRldbw4sh1MteQkRFplZQbv2jaJqwErsUV7oLXtH-AlLPq2kuFHVxnyyKTtYm3pxFQL_A/s1600-h/xRM_Demo2---Microsoft-Visual-Studio_%25255B8%25255D.jpg)

then click on the Views tab, hold the CTRL key and and select the views that you will use in your report and click Add

[![Add Table_2012-03-12_17-59-13](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEifLSSgMiqqRiprPwMLCA8mxLrrBcP2GEC-HXJoNknf9Px31fuLT1GEvP74FbMHyyWhruJRSzUvD6OuAvr3cqydl2O7yvzCX1jbgOxrnCGzoe7b8rruaFukv9ghVp8XTCEnUrh-jr_mbg/?imgmax=800 "Add Table_2012-03-12_17-59-13")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgM6Jh91hYG4TgnwYSFiS_MgcfL-z9Br76-GaVFEHLw6YBfm4Cwz3FfMKN45e7hcY1u_NHV7uNmsOeTEN7Gasj6Rrh0YXtZM6m9ic5S-HhldXiligx76rkVevuhY9UblJ5c7GFC-Z4xuA/s1600-h/Add-Table_2012-03-12_17-59-134.jpg)

select the columns you want, test your query results \[We just retrieved the account name, city, country\]

[![Query Designer_2012-03-12_18-02-20](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh93pcxWcLHSjv-AoQ4kGlkvfRIxmHgOvCejMmE6SKCJT6bhJQ6n0DIHWOCTH4sj4ZSrBiVpWZ4TibwM2t-9C_BgAUsADVAyF3F4YaheEZWzNME0nrh-Pru9MJZiRU5BuDwHYg5HxgpyQ/?imgmax=800 "Query Designer_2012-03-12_18-02-20")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjuv-4khIxK3l5ZABn87pDfOK29NdZ0iJ3Uylso_YGGmd6gvI7A-PAQ59xuvn_AQYfR-aj5PWxKMP7DQmvlo8xedyOO7u-jWpjqCi1NCvh1SeblrImZv5a1D2SFVw_CIjAvVfeDr47W3A/s1600-h/Query-Designer_2012-03-12_18-02-203.jpg)

when you satisfied with your query results, click Ok to use the query in the report

[![Report Wizard_2012-03-12_18-03-19](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhNpacAlPfcndmHoAataqZ1H5ciqKa_QxfFOB7VX7T_MCNk36Uu-8U3TAtwhwTcqifpsoG39upqrgcvUPDQ4TbiGd1Az3zYftqXAD6kHj3QEyKF7o8qfbyQW5A7BYlmfWA0ftuFmGP1Tw/?imgmax=800 "Report Wizard_2012-03-12_18-03-19")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgQAxX0s2_CchCWiiG1YPIb8DiJgrWjCNjxcRawzQdSaqblTt6wZEE_g8ySZ9fkfZRFes7xtjZG4jktP9IYmv3Yn7SNN-A2BwM4QeJMSx8qt42tLA_hxXCRE5xpP3LzrkFjfJRXdwi_tA/s1600-h/Report-Wizard_2012-03-12_18-03-193.jpg)

click **Next**.

4- On the Select the Report Type page, select a **Tabular** report or a **Matrix** report, and click **Next**. \[we used Tabular, which is the most common report format\]

[![Report Wizard_2012-03-12_18-03-24](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiVejM0JigoO5pgGF3b2OwOh-Qc9XOVNIEEDed0qhyphenhyphenDh9Hl5JxUa95tYrVf_HGx_wU3xX2yrDiNhNqMBxSFxA69cKnrNR6bhFc_oJhE8kqVkIEZLB6KesoCPQZcgqykoI34y9zHdbQYRQ/?imgmax=800 "Report Wizard_2012-03-12_18-03-24")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhTuR6vxdn0jV4rfg5rCFXbV8od06NuwnHFBiyO4fk1Um91rph3Cfou-IixNsB99O2KVGcPBoPR8RqsTIEl2GpOnYC98fQa4W5oXXIR8LbJSQSRifzvap5FJN1bbva8EyH5D3DotvDHrQ/s1600-h/Report-Wizard_2012-03-12_18-03-243.jpg)

5- Specify the fields that will be included in the report. You can add fields in three different sections \[Page, Group, Details\]. Page can be used for granular grouping like Country in our case, it will displayed on the page header only. Group can be used to more specific grouping within the page, like City in our case. Details is the place where individual records will be rendered, like our accounts names. Select each column name from the list on the left and click the designated section button to add the column to it.

[![Report Wizard_2012-03-12_18-04-41](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEheahch93LfCH0dZW4wm9N85QO9CuPMA3Wl5phushzMhXKeQuhJWSJCuOorAqjlmKoz83UUfvceQ28GG52XEAzw3cPdvb2v_z_OwXSXcmjwkzE3mYZb-9JnNWXDqKC8IB1vAaUak1MQ-A/?imgmax=800 "Report Wizard_2012-03-12_18-04-41")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEizuNE120JT1GKNM5DlfcQt8t-Uvo4ZIUxjYTF_RVpjO9F7CNvIWqyCBX7PBDUtYjIU1JRTcfBJUaNdRLREXTVkizlADCjYA4ybxUQ_KTDl9w8pK_gM7LjbRCVtgDKDXzy1psCk9lJ9OQ/s1600-h/Report-Wizard_2012-03-12_18-04-413.jpg)

Then click **Next**.

6- Select a stepped layout and click **Next**.

[![Report Wizard_2012-03-12_18-05-16](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiuTKCwX_Nutjbhx4U871Tjtws5g21-jLz8Q9nacam4HeyX7ERPbJfDm50jBu7kZOPmCmpYfUn2WOgxxuT1X92QYW7GTf14bnIctO5tNIsHLCbm7Fg_6-k1_7amW_OtdaHxq0PLnEc1qg/?imgmax=800 "Report Wizard_2012-03-12_18-05-16")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgbNQzvw__02PK9snKFxjmZ8lD45N0337yde7P_RXkra6HcbMiQuyWwbiAFW4RWwhnH0C8WvOx0NP_yZPvvcbWVXpM_LyF3HAtLFtGY6iGcG7J2H5z2y7e7iWmqFcGmRI9uIkEDkDUu7w/s1600-h/Report-Wizard_2012-03-12_18-05-163.jpg)

7- Select a style to apply to the report, and then click **Next**.

[![Report Wizard_2012-03-12_18-05-22](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi2kJ0ntL8oS5UM5PguCNTwm5cnWo7U5bCEqEzDl7cyJUYSpTJRRxQIifsWNBtzMd_qowHWRVJSaZ-v8BG3y1nfueIg67vxHyxwGU3lJ7lko8c7-UbpBJ-HyEEkahKuP5zN8YLDSphYKw/?imgmax=800 "Report Wizard_2012-03-12_18-05-22")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi-dcpemEKyfmTc401MxloIK4ulv9Qpu2uCAoioTJBWCFhUydm6OdBEZPqwQs6DZaIb98y-hQemd2Ig7ocrk40Wi13vvi6n640hdzX8cOZzSF-ZsNGp7MXFEvGRk4Jvu1QAJQlZn2Ix_Q/s1600-h/Report-Wizard_2012-03-12_18-05-223.jpg)

8- Verify the fields that will be included in the report, and name the report. Click **Finish**.

[![Report Wizard_2012-03-12_18-05-28](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjrYjK_bsj_kZ0TsEQMY_bC6IgApYwxoe8eXvHxbYScyTvRbuYSvyLm9kOgAw_SlxFC9ZWdaDD3G2TT9jHErmC-qS49xM53PGaDsJTT7DG0X51pAOdOZhDyzjEiaZW-J7ipxNc-s3rsrg/?imgmax=800 "Report Wizard_2012-03-12_18-05-28")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgVxZuUTKu_Ab7s5vj5UwnViuOovaPdvD3UQ_tGcJJMniWs5nt004YFKXMF3ekQYXul_dHf_4Pz9QldU1btv5Va5yjkqmpIwIqPLh1OufEr5H1gkemOJqe6c_xreSaxc1_eCQ2qb3cn4w/s1600-h/Report-Wizard_2012-03-12_18-05-283.jpg)

This will generate an .rdl file with the specified report name. You can use the .rdl file to publish your custom report in Microsoft Dynamics CRM.

[![xRM_Demo2 - Microsoft Visual Studio_2012-03-12_18-07-31](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj5-e61klgw2D3qPAYb7JZtLPfC1oh4MufyZQC5H22I9jlGi2KqKNREY7_f46SS8G8yynsbKIKKUm4_3YDx4KfIVUGE3Rf2Q_6tvsPiTTv6USSkIRjFa0HY1R8L1Cgr_1rG5-fEgQgyHQ/?imgmax=800 "xRM_Demo2 - Microsoft Visual Studio_2012-03-12_18-07-31")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjW1hsJmdqUfiw4UCVwn6lsVs9UPH-i2F7dJ21bYPPfa8XvPDAhnWqA_jtm8LK96sREcUD4AWt05cCLXQb47VwD3UlG0pp1catYpJjHcS11PfDN4MmRSzA5VYRuUIHfPqwn4Oi_s91eHQ/s1600-h/xRM_Demo2---Microsoft-Visual-Studio_%25255B5%25255D.jpg)

**Create a Custom Fetch-Based Report**

Creating a custom Fetch-based report is similar to creating a custom SQL-based report except for the data source name and the report query specified while creating the report definition.

Since you have the capability to create SQL-based reports for on-premise, most people will not use Fetch-based reports for on-premise. Let’s learn how to get the data source name for our CRM On-Line organization. It consists of:

*   Organization URL something like [https://xrmdemo5.crm.dynamics.com](https://xrmdemo5.crm.dynamics.com "https://xrmdemo5.crm.dynamics.com")
*   Organization unique name you can get it by navigating to Settings > Customization > Customizations > Developer Resources > it will be on this page

[![Developer res](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgVF_GZYUdyOEljaI570kdPos8f-Fn8Xtl0fksXB1iZZMb7mwJwXrhy-zG2Rt43XrEpsV1QBkw0AKSNqQVE7zir73S5OCHrpNLsM4GEAeeeX8fTUxtignb6KrqaMmp6if8r1xxirXZYmg/?imgmax=800 "Developer res")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgbrIuzVFsiNCAAiV1j1IpS57ftTDb1AOmDTn2xN7V94vlVCpc6rk3j85dsV9A0qNvg6cmpHUbLPF8vhZVSzBFv7MN4m1CzqtIW0e2XVn_IWgeE8UFa9uRjNfJTmqHj8qJ-Tr8ntMf13A/s1600-h/Developer%252520res%25255B3%25255D.jpg)

Put the two parts separated by semi-colon will form your connection string, like [](https://xrmdemo5.crm.dynamics.com "https://xrmdemo5.crm.dynamics.com")[https://xrmdemo5.crm.dynamics.com](https://xrmdemo5.crm.dynamics.com;4c69b8c565264033b4707c804cba7aa2);4c69b8c565264033b4707c804cba7aa2 put that connection string in a text file for later use.

Now, lets learn how to create a query for our Fetch-based report. There are two ways to do that:

1.  Manually type the FetchXML query (which I don’t personally prefer)
2.  Obtain the FetchXML queries from the CRM web client and then modify it.

To obtain FetchXML queries you can navigate to any entity listing in CRM web client, like Accounts. Then click Advanced Find on the ribbon

[![adv fnd](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiF-VDYOISLlj1DCjCX_FtTHlo2fYImBEKDX9SQCVu2JPy3ActPh21Wo5PQmXIPAai91V34RvKfFL_nfPbHApQWYGyBMtjFOBcIswPWtOnTHKZBPCkE3LqfEdLkxhVS10PWuMh_j4rD_w/?imgmax=800 "adv fnd")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg7QdV14PZ3VAKHauPlSbl9ioiyLFCHqBwhBcJDY5nYrqzF-2AAQEzJgXNNUpepX8-VffeVxV7Tz40e2TjLYg84gdXDXUqO2DMfots2uyWXGAlNigQWEB676luLc8gdZUhp6hYoZ2DvCw/s1600-h/adv%252520fnd%25255B3%25255D.png)

This will open the Advanced Find dialog

[![adv fnd 2](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgf0V14djiLH8HfV3fIBXKAKKUQVBXekzjjErTlaXhIieQkgveHu3_ZN0XiIu38CimJ5Tv7jHDcz17RvU9c5Xc27TLB6pVV17oeDiIryic-uuWciMnpryCjU8cQKf6V7zUgZlny5erzsA/?imgmax=800 "adv fnd 2")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiHtvEB0ZSaCNAOcKPGlnLoLISNY4ZrMnVFBFuDSpSSehJB2kWsjlOVHhlg-DJnZgPG4a2dmMvzUC5-lW6ChjNtwhL8G6ffiJ5kt94kxbLqnOVXWAvYOgUV4HRMHNql6l-gKbxcb_gk3w/s1600-h/adv%252520fnd%2525202%25255B3%25255D.jpg)

Then click New to start creating a new query.

1- You can select the Entity (Table) from the Look For combo-box.

2- You can create your query where conditions. Click Select link to select the desired column

[![adv fnd 3](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhSHwl2QIniMp4fitOYvTVmBl8hsT-oWE0hvVsUBYtcStGGFL1T4RYdObDezg-eBMgzHugMWeyaKdKKsld3gjweDgFlGmasCpYS6-gdgR2MkmS4Eb-AqlbUZcNkhKDrcTjzcvVT-Cd-2w/?imgmax=800 "adv fnd 3")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhjtb7dGH4qU_0khG8UGE_ppkV3vQ95-z1BLAh9w5ZhDHQujf03XO8b3pZcL3PXj6k4gJ7xP-YjkjXdADwJBYKcTg85C8ELYexllmyHs4otvrQwvqGKDUYZA8ilPFf0E1ihI21EoC4-Cw/s1600-h/adv%252520fnd%2525203%25255B4%25255D.jpg)

You can then click Equals link to specify the operator used in the where condition. You can then click Enter Text link to specify the value used in the condition

[![adv fnd 4](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiWqrN0tB53mjfHy4ldY22WzzM-r3d-ohJYpTGyF26ULLWHgaHYKjZQwUIuSvU3tDhTEKYEV9Quu6ik_cfem4y_U5GFu58Vwbg7dobLTAaSR3ey9jyBvQ3lwmPwyT5eSYhWsbDORbHEKg/?imgmax=800 "adv fnd 4")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiiLOodUen-62akzFDnKz0f449haV-7Pbccoz-QU2bWUmjWlVO6xoTe0iPP6tlDUc5Slfp838ktZelYcWQyPzj2jkHGCZRCteBQdvjwxAlQ0HSuphEFNwP5fJcY_-6gRKFlHdAJ0M9Uew/s1600-h/adv%252520fnd%2525204%25255B6%25255D.jpg)[![adv fnd 5](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjtJdp4MqCY8jUV_pA_UzI7WbbIp6ji9GpEY5r1k2EG4g7hNlNRutVkFFbt5YMl_TnvFneip9YUCTyck3H7tby7Ar8hynq4R9rp_uQUwp9ymsEplY-ZPSPfwGQz34WoDgBtQLxC3b-psA/?imgmax=800 "adv fnd 5")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhECK1SOcVcHHKXMJS8z6R0RHQS6WvwnJeVE5CyydPMzpV123yOVceAEkIcya0RikJIiWcyKMAR-te9eChBBIDctanEkvIPLY-q7wIKiDJrmGaDAHotKMXpRqAVeK0NSjDiHzK6l6v4Nw/s1600-h/adv%252520fnd%2525205%25255B4%25255D.jpg)

when you have multiple conditions, you can select them and use the Group AND and Group OR on the ribbon to build your query logic.

3- You can specify the columns you want retrieve. Click Edit Columns in the ribbon, this will open the Edit Columns dialog

[![Edit Columns -- Webpage Dialog_2012-03-13_13-07-57](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjjMB_m-foRmSflufgSk3vBdW83lVoKrAQQ_PnZLwksmxqmfFuZ5hutTSZoWxNFYpgS1c2ChDRFGEANjGwHmpi35R8OR8tjcV5dEcgu1RARYzPKZQ1Kjxg7NxSiEDzIj4ik2KESHiL6uQ/?imgmax=800 "Edit Columns -- Webpage Dialog_2012-03-13_13-07-57")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhXOq2S3h09EowhAy9hFY937_l8Pe0dVvxpXSwy1tHgxfvMjeoEjaVfI52qt8r9KFAVPuRTTUhX6iyqYRx1r6eseo0lR1Yi6MAaAZis-dAeI2O1gufoUxDekqaInMf5y2jX6pKHN_tpUQ/s1600-h/Edit%252520Columns%252520--%252520Webpage%252520Dialog_2012-03-13_13-07-57%25255B3%25255D.jpg)

The area on the left shows the query columns and the sequence they appear. You can click Add Columns from the left to add more columns from this entity or any of entities related to it.

[![Add Columns -- Webpage Dialog_2012-03-13_13-10-04](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgP1B57tlYbkE8gG3CrAhn5Bk09wZIzDpL-y7Yagy97PSeEG-tK8kTyRvLsHAKu4ru3CZZ58XdkSdXnZa99jmnJ7S4Jn8wyVaUbHJRlCvtPoteWOByiLGNGeIBXVWcWMFRIizyFaPIGhg/?imgmax=800 "Add Columns -- Webpage Dialog_2012-03-13_13-10-04")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgZSaxYFqS15Y-Nm66lJ1dNU_K0D-hn7XBzXHW4Y753YMCD-X_oHsABoesD6zq4UHJt_Yi6TLj0nkaFXjlLmYxcu3Msht3lRyZVEuRjrFDaDsGbjjqdIfOON0K_pWWI2FtjJJAxXn6ZgA/s1600-h/Add%252520Columns%252520--%252520Webpage%252520Dialog_2012-03-13_13-10-04%25255B3%25255D.jpg)

Select Address 1: City and Address 1: Country and click Ok.

4- You can specify the query sorting. Click Configure Sorting on the left to open the Configure Sort Order dialog

[![Configure Sort Order](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj8R6hWO4V2i-eqrHfRgBtZlJEa6S743M9CdXQQySU3qJDr3pZ47MEHzqiLgCV3AQ9tSzabYBf290XAxr-zm9Kb1kPFYw_dbBum3eUw1fP6bwoaZUlMhtj6iB1zkPsvJZAwgZdtxyw2hA/?imgmax=800 "Configure Sort Order")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiANAjuv38TUV2Y9DUsjJAY1b7oqc1ECtE1wNSCXuiTqeMxfMwRAPF-x5jBkInmiaPCthJemCXv-rVhP41LSuw9vIKmB-sjV_aFl4cgYgt-vorIzpANCqk_UtKx_DVNWiTRGuXO2B36Xw/s1600-h/Configure%252520Sort%252520Order%25255B3%25255D.jpg)

You can specify two columns only for the sorting criteria.

5- You can remove any column by click its name on the right and click Remove from the left.

When you done with editing the query columns click OK to return to the Advanced Find window. Now, click Download Fetch XML on the ribbon to download the Fetch query in a .xml file format to use inside SQL Business Intelligence Development Studio.

Now to add a custom Fetch-based report to our Report project, Right click **Reports** folder and click **Add New Report**. Click Next on the Report Wizard welcome screen.

1- On the Select the Data Source page, click **New Data Source**, and specify the following details:

*   **Name**: Type a name for the data source.
*   **Type**: Select **Microsoft Dynamics CRM Fetch**.
*   **Connection String**: copy the connection string we prepared earlier and past it here.
*   Click on Credentials and enter your live account and password you used in CRM Online and click Ok. Then click Next

[![Data Source Credentials_2012-03-13_15-07-56](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjsqudw0Anuzyi18f-0_UEA2qjrhb4DW1MESdEJw3yGpoMryhr6D-8rx6HnpEWSnCyPNWhjuYwD7ATeC64mRT1g5T3VE6urCWEMXdmqF-I04x7V6iRHx-0HUcBnXUZaqBo9kx-3h_0Vqg/?imgmax=800 "Data Source Credentials_2012-03-13_15-07-56")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhcehIwxJgCvoiQsOWa74a8cnO9KDXMdi1B4OhROLc_sUMrtjtzF_WOTfS3ztRuoL3Ds85iVstUTfM5W0iLziasxDvrcrM92XKQkPrFoL-XqNUX6zgXEuvfPhx5-FTW2FeaY2-dR65fJw/s1600-h/Data%252520Source%252520Credentials_2012-03-13_15-07-56%25255B3%25255D.jpg)

2- On the Design the Query page, click on Query Builder. On the Query Designer dialog, click Import and browse to the xml file you downloaded earlier.

[![Query Designer_2012-03-13_15-24-04](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgnWyTcDUzk5CPOpjn76RooMLMjhyJw7Y1ARS3C_5aV3SEGoYpHQLzPlRJ20G8D-R6bJnZlw_KGEF8behHV9pHZNwWSHnOFxq98TS9fiOJedilETjtan2_tcsYWXu5I1IkzaqwjAxcINA/?imgmax=800 "Query Designer_2012-03-13_15-24-04")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjnq82fJCHmD1YuMX10sYgornXINMnrC_acE83eiaNUaVwydTrkPXXSChC60WdY_OhwDlaliYh5j7FpUU7vvQQAklLVRKefSAXZtGN7WOV9m2nViWIv2cu42WKYOyR-I24-1Dpqwvs4gA/s1600-h/Query%252520Designer_2012-03-13_15-24-04%25255B4%25255D.jpg) 

You can click on Run to test the query. Click Ok to close the Query Designer dialog, and Click Next.

Complete the Wizard steps just like the SQL-based report, it is the same.

As you can create queries using Business Intelligence Development Studio, you can also use it to modify complex queries.

**Import Custom Reports into Dynamics CRM**

To complete the cycle and let the report used by your organization, you need to import it into CRM. Follow the following steps to import our report:

1- Navigate to My Work > Reports > click New on the ribbon. The New Report window will open.

[![Report New - Windows Internet Explorer_2012-03-13_17-07-32](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhBuqI_XrwoVTYM3S5oC79lNwdEtyoDig1M1lxYozqYEuL_Cy6xV_U8-EkhVrCwN3pFzAq4CYYQGMxSBuMwx49zWaXLnWOgzr9B_3MQmEbvlJQiZzE4f0crMPmZiomk99AitQsfpKaQ3w/?imgmax=800 "Report New - Windows Internet Explorer_2012-03-13_17-07-32")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEifWjr4dcI2cd4qNjOipUSpBJj6fUIuYs-BhzV_hmoYwW-Mv_g_3YdrTcjfAkWACDxZFQdfJoaah63MWSvmdguQKE8mcQQCjXAIiFh6g3leTIzwdtjvjiO3UpC1q6trZposB-cIt0QTGQ/s1600-h/Report%252520New%252520-%252520Windows%252520Internet%252520Explorer_2012-03-13_17-07-32%25255B4%25255D.jpg)

Click Browse and select your .rdl report file. Enter the report name. Near the bottom of the window there is a Display In field which decides areas where your reports will be displayed. By default new reports will be displayed in Reports area,  You can click the eclipse button if you want to make it displayed in forms or lists of the related entities, then select desired values and move them to Selected Values list.

[![Select Values -- Webpage Dialog_2012-03-13_17-20-21](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgEnWy5Na2Uz3P_z-xeBiFahozLYPeC6GT34Qgrk_rOVRKI9UYnXy7Y1iKcwaUoo5R8MjwDFxhIqq_U_9KmTsEwXnqZOaDUQLb71xOSJ_5Qjx9H1UbAtqRydZO1zPwTQ4syr9HYAIr-Uw/?imgmax=800 "Select Values -- Webpage Dialog_2012-03-13_17-20-21")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjTD-7443QH1c_1SqtBrJnBUGeZk_LzgEuP4jdz4iuV9jbIGRiCrxJTlfxNFHfpSEFbzniIGE0-1QY_cL3G-6OIXm-nct2K1Oj0l-BNvltNL0i7nc7DI936mL0SMYs-IMW32QBg0jLrAQ/s1600-h/Select%252520Values%252520--%252520Webpage%252520Dialog_2012-03-13_17-20-21%25255B3%25255D.jpg)

In the New Report window, if you want to make the report accessible by the whole organization click the Administration tab and change the Viewable By field from Individual to Organization.

[![Report New - Windows Internet Explorer_2012-03-13_17-14-18](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhnTlU8NtBOrLAeOpiErvIFXZB-PEoHitqM_YHr5dalO2RhbZwNk55yLN17VNIt8t3Fa9E99r3GatTD0JnnCNOPeLh_H552U0o9TzqiVLDWOfe_Kr96frzLxkJob8YVOKeUj1Owj50rXg/?imgmax=800 "Report New - Windows Internet Explorer_2012-03-13_17-14-18")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhPjXAS-v1D72v9Wq_ZhbcYiOIhqU5iaYtG3dkhOfcOUYmQlyafWxo50oyR71AQhiHp7U_ShQgbaP__f3XILYg5r0PFI6TEolR4eht4XOLkNtTUreuKlbYwKnWIhO8i2r4ZMxk08uGGOg/s1600-h/Report%252520New%252520-%252520Windows%252520Internet%252520Explorer_2012-03-13_17-14-18%25255B5%25255D.jpg)

Click Save and Close. Now our report will be available in the Reports area of configured accessibility level \[Organization or Individual\].

> To copy a report between organizations or deployments, include the report and any custom entities the report uses in a solution. This ensures that the entity types are mapped automatically by the system

In this post we used the Business Intelligence Development Studio to create both SQL-based and Fetch-based custom reports for on-premise and on-line CRM deployments. We also learned how to upload our reports to Dynamics CRM and make them accessible to the whole organization and through many access points.