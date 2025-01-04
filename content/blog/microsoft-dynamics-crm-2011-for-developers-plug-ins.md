---
title: 'Microsoft Dynamics CRM 2011 for Developers | Plug-ins'
date: 2012-03-23T15:49:00.001-05:00
draft: false
url: /2012/03/microsoft-dynamics-crm-2011-for_23.html
tags: 
- Dynamics CRM Plug-in Registration Tool
- Microsoft Dynamics CRM 2011
- Plug-ins
- WCF
---

#### **Contents**

1.  Introduction
2.  Common Uses of Plug-ins
3.  Plug-ins Basics
    1.  Event Framework
    2.  Event Execution Pipeline
    3.  Pipeline Stages
    4.  Message Processing
    5.  Inclusion in Database Transactions 
    6.  Plug-in Isolation
    7.  Trusts
4.  Develop Plug-ins
5.  Register Plug-ins

**Introduction**

A plug-in is .Net assembly that can be used to intercept events generated from the CRM system. Plug-ins subscribe to a set of events and run when the events occur regardless of how the event raised (or the method that is used to perform the activity that raised the event).

Any number of plug-ins can be associated with a given entity and event. When multiple plug-ins are registered for the same event on the same entity, they are called in a sequence based on the order specified on the step registration. This value is specified as the Rank and it is supplied when the plug-in is registered. This allows developer control over the sequence.

**Common Uses of Plug-ins**

Plug-ins have many uses like:

*   Performing complex business logic data validation
*   Performing complex update routines on CRM entities and/or attributes when it is impractical to use JavaScript.
*   Grabbing data from another system and updating CRM when an entity instance is being created or updated.
*   Updating another system programmatically from CRM

**Plug-ins Basics**

**Event Framework** Event framework is the term that is used to describe the technology and mechanisms available in Microsoft Dynamics CRM to enable you to extend or customize functionality with custom code. Your custom code will run on top of Dynamics CRM either synchronously as part of the main Microsoft Dynamics CRM execution path, or asynchronously from a managed queue.

**Event Execution Pipeline** Event framework executes plug-ins based on a message pipeline execution model. A user action in the Microsoft Dynamics CRM Web application or an SDK method call by a plug-in or other application results in a message being sent to the organization Web service. The message contains business entity information and core operation information. The message is passed through the event execution pipeline where it can be read or modified by the platform core operation and any registered plug-ins.

The event execution pipeline processes events either synchronously or asynchronously. The platform core operation and any plug-ins registered for synchronous execution are executed immediately. Synchronous plug-ins that are registered for the event are executed in a well-defined order. Plug-ins registered for asynchronous execution are queued by the Asynchronous Queue Agent and executed at a later time by the asynchronous service.

**Pipeline Stages** The event execution pipeline is divided into multiple stages, four of them are available to register custom developed plug-ins. Multiple plug-ins that are registered in each stage can be further be ordered (ranked) within that stage during plug-in registration.

**Event**

**Stage name**

**Stage number**

**Description**

Pre-Event

Pre-validation

10

*   For plug-ins that execute before the main system operation.
    
*   Plug-ins may execute outside the database transaction.
    
*   For plug-ins run prior to making security checks on the calling user.    
    

Pre-Event

Pre-operation

20

*   For plug-ins that execute before the main system operation.
    
*   Plug-ins execute within the database transaction.
    

Platform Core Operation

MainOperation

30

*   Dedicated to main system operations.
*   For internal use only, no custom plug-ins can register in this stage.

Post-Event

Post-operation

40

*   For plug-ins that execute after the main operation.
*   Plug-ins execute within the database transaction.

Post-Event

Post-operation  
(Deprecated)

50

*   For Dynamics CRM 4.0 based plug-ins ONLY.

**Message Processing** as we saw in a previous [post](http://ebeid-soliman.blogspot.com/2012/03/accessing-microsoft-dynamics-crm-2011.html), any web service method call is done through OrganizationRequest message. This call raises an event. Information in this message is passed to first plug-in registered for that event. Plug-in receives the message information in the form of context that is passed to its Execute method, where it can be read or modify its contents before passing it to the next registered plug-in for that event and so on. The message then passed to the platform core operation. After the core platform operation has completed, the message is then known as the OrganizationResponse. This response is passed to the registered post-event plug-ins which may modify it before a copy of the response is passed to any registered asynchronous plug-ins. Finally, the response is returned to the application or workflow that initiated the original Web service method call.

Because a single Microsoft Dynamics CRM server can host more than one organization, the execution pipeline is organization specific. Plug-ins registered with the pipeline can only process business data for a single organization.

**Inclusion in Database Transactions** Plug-ins can execute or not execute within the database transaction of the Dynamics CRM platform. Within the plug-in, you can detect that through the IsInTransaction property in IPluginExecutionContext that is passed to the plug-in. Any registered plug-in that executes during the database transaction and that passes an exception back to the platform cancels the core operation. This results in a rollback of the core operation. In addition, any pre-event or post event registered plug-ins that have not yet executed and any workflow that is triggered by the same event that the plug-in was registered for will not execute.

**Plug-in Isolation** The execution of plug-ins can be in an isolated environment, known as a _sandbox_, where a plug-in can access and use the organization Web service only. Plug-ins can’t access system resources but can access to external endpoints (only through HTTP and HTTPS). CRM platform collects run-time statistics and monitors plug-ins that execute in the sandbox, if it exceeded certain thresholds or became unresponsive, it kills the sandbox worker process (this makes all currently executing plug-ins in the current organization fail).

**Trusts**

*   Full trust Plug-ins run outside the sandbox, available in on-premises and internet facing deployments.
*   Partial trust Plug-ins run inside the sandbox, available in all deployments.

**Develop Plug-ins**

Simply plug-ins are classes that implement the IPlugin interface. You can write a plug-in in any .NET Framework 4 CLR-compliant language.

Now let’s consider a simple case that plug-ins may be its appropriate solution. Let say that your company wants leads to be numbered automatically when they are created. In order to achieve our goal, we will add a custom field to the Lead entity and add it to the form. We will disable this field on the form. We will create a plug-in and register it for the Pre-event for the Create message on the Lead entity. When a lead is created, it will look for the next available number in the system and assign it to the newly created Lead.

**Step 1: Create Customizations**

Now we will quickly customize the Lead entity and form to accommodate our solution. Navigate to Settings > Customizations > Customize the System. In the left navigation pane, expand Entities, expand Lead, select Fields, and click New.    
In the New for Lead form, set the Display Name to Auto Number, the Type to Whole Number, and then click Save and Close. In the left navigation Pane, select Forms. Click the Main Information form > Drag the field, new\_autonumber, to the Name section of the General section. Select the field, click Change Properties, mark the Field is read-only check box, and then click OK. Click Save and Close, and then Publish.

**Step 2: Create the Plug-in**

1- Open Visual Studio and Create a new project of type Class Library.

2- Add references to Microsoft.Xrm.Client.dll, Microsoft.Xrm.Sdk.dll, and Microsoft.crm.sdk.proxy.dll \[located at %SDK%\\bin folder\].

3- Add references to System.Data.Services, System.Data.Services.Client, System.Runtime.Serialization, and System.ServiceModel.

4- Add reference to Microsoft.IdentityModel.dll from "C:\\Program Files\\Reference Assemblies\\Microsoft\\Windows Identity Foundation\\v3.5\\”. Then go to reference properties and set Copy Local to True for the DLL. The DLL will be included in the package. If you don’t have the dll you need to install [Windows Identity Foundation](http://www.microsoft.com/download/en/details.aspx?id=17331).

5- Make your class implement the IPlugin interface, and implement its member method Execute method. This identifies your class as a plugin to the CRM platform when registering your assembly later. Plug-in code will be placed in the Execute method which takes a parameter of type IServiceProvider. This parameter is a container of many objects that will be utilized by our code.

First get the IPluginExecutionContext. This context object gives you access to all the property values associated with the entity and event context where the method is being executed.

```
IPluginExecutionContext context = (IPluginExecutionContext) serviceProvider.GetService(typeof(IPluginExecutionContext));
```  
  

InputParameters property of the context is a collection of the request parameters associated with the event. We use it to check the entity of which the event is fired.

  
  
```
if (context.InputParameters.Contains("Target") && context.InputParameters\["Target"\] is Entity)  
            {  
                Entity entity = (Entity)context.InputParameters\["Target"\];  
                if (entity.LogicalName != "lead")  
                    return;
```  
  

Then we get the OrganizationServiceFactory to use it to create an OrganizationService. We also get the TracingService. Then we edited our auto number field with the next maximum number in the organization. GetMaxLeadNumber is a typical method that passes a QueryExpression to the OrganizationService to get the next max lead number.

  
  
```
IOrganizationServiceFactory orgServiceFactory = (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));  
                ITracingService tracingService = (ITracingService)serviceProvider.GetService(typeof(ITracingService));  
                IOrganizationService orgService = orgServiceFactory.CreateOrganizationService(context.UserId);  
  
                try  
                {                                    
                    entity.Attributes\["new\_autonumber"\] = GetMaxLeadNumber(orgService);              
                }  
                catch (Exception ex)  
                {  
                    tracingService.Trace("xRM\_Demo03 | {0}", ex.ToString());  
                    throw;   
                }                  
            }  
        }
```  
  

Now your class should look like:

  
  
```
using System;  
using System.ComponentModel;  
using System.Diagnostics;  
using System.Security;  
using System.ServiceModel.Description;  
using Microsoft.Xrm.Sdk;  
using Microsoft.Xrm.Sdk.Client;  
using Microsoft.Xrm.Sdk.Query;  
using System.Collections;  
  
namespace xRM\_Demo03  
{  
    public class Plugin:IPlugin   
    {  
        public void Execute(IServiceProvider serviceProvider)  
        {  
            IPluginExecutionContext context =   
                (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));  
  
            if (context.InputParameters.Contains("Target") && context.InputParameters\["Target"\] is Entity)  
            {  
                Entity entity = (Entity)context.InputParameters\["Target"\];  
                if (entity.LogicalName != "lead")  
                    return;  
  
                IOrganizationServiceFactory orgServiceFactory = (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));  
                IOrganizationService orgService = orgServiceFactory.CreateOrganizationService(context.UserId);  
                ITracingService tracingService = (ITracingService)serviceProvider.GetService(typeof(ITracingService));  
  
                try  
                {                      
                    Random rand = new Random();                      
                    entity.Attributes\["new\_autonumber"\] = GetMaxLeadNumber(orgService);              
                }  
                catch (Exception ex)  
                {  
                    tracingService.Trace("xRM\_Demo03 | {0}", ex.ToString());  
                    throw;   
                }                  
            }  
        }  
  
        private int GetMaxLeadNumber(IOrganizationService orgService)  
        {      
            QueryExpression qe = new QueryExpression("lead");  
            qe.ColumnSet.AddColumn("new\_autonumber");           
            qe.AddOrder("new\_autonumber", OrderType.Descending);  
            qe.PageInfo.Count = 1;  
            qe.PageInfo.PageNumber = 1;  
  
            Entity entity = (Entity)orgService.RetrieveMultiple(qe)\[0\];  
            if (entity.Attributes\["new\_autonumber"\].ToString()!= string.Empty)  
                return int.Parse(entity.Attributes\["new\_autonumber"\].ToString()) + 1;  
            else  
                return 1;  
        }  
    }  
}
```  
  

Now the last step is to sign your assembly. Double click Properties under your plugin project.

  
  

[![xRM_Demo03 - Microsoft Visual Studio (Administrator)_2012-03-19_12-33-32](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh5IcIsHDtKryjygYNEdfp_OBQSUreCpyCWh7-s0vzFfmVJdMHH9L_qttMWHi09zp-HixU1T7DgWoPhVieUieRPzCSPaxpU5_9ubYoioBXNcpBwLSQyEtjkXyGA5q5RJeJwE_Nv87xrHg/?imgmax=800 "xRM_Demo03 - Microsoft Visual Studio (Administrator)_2012-03-19_12-33-32")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjD3NW_8dBuu7QA4TWjzDgW4_px5e0Hz_Ja7RnyuhjHQjSunSh6HaloeZkxNNwl_H8wdBqJHdP3qF1SA6GG892yXzRPhB63nQPgqOwTgrWQbYV3p9NP8rCfvqo1wZ7FCklloA6ar_kD2g/s1600-h/xRM_Demo03%252520-%252520Microsoft%252520Visual%252520Studio%252520%252528Administrator%252529_2012-03-19_12-33-32%25255B2%25255D.png)

  
  

then click Signing from the left tabs

  
  

[![xRM_Demo03 - Microsoft Visual Studio (Administrator)_2012-03-19_12-34-21](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj5DGPCc0HX9K5-d5ICLyrv5-SpsD7zr2uGJ3uAF14eu74Q_UiHhzAcXLcNj91j_14dn9zBP3VPNQxoGFdweQaEKcXKS8N9tZTd2DF_uqr7aExNxammbbOXXVGlKllSplIFNgO5vH4AMg/?imgmax=800 "xRM_Demo03 - Microsoft Visual Studio (Administrator)_2012-03-19_12-34-21")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiW88etRy_20gzojqhxXLHln64GLzwUR1Ofgl8CzseZk9SoD99RJoPSYHShLqb-8dLcM_Dtz6sdNBg_PWO6sfLF_439Llpz2uvBhvOoQW9iAhnNQFUAs934RkAYMvs1Gg2aeqYIGzK6Eg/s1600-h/xRM_Demo03%252520-%252520Microsoft%252520Visual%252520Studio%252520%252528Administrator%252529_2012-03-19_12-34-21%25255B3%25255D.png)

  
  

select Sign the assembly checkbox, choose New from the dropbox or choose an existing key. Build the project. Now we are ready to register our plugin into Dynamics CRM.

  
  

**Step 3: Register the Plug-in**

  
  
  
  
  
  

The Dynamics CRM SDK have a tool to register plugins located as a source code at %CRMSDK%\\tools\\pluginregistration. Open the solution, build it, and run it.

  
  

1- Click the Create New Connection on the toolbar. Enter a name for the connection, organization URL, and the email you used for creating this organization.[![Plugin Registration Tool_2012-03-19_12-20-45](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhlpV62x67nGJN0u_wEBK9_56twyaJW70ROER2Hm5pS0eWfTyfa452Tki6mWRH227BMZfOxZDzD3qZZ3Rc-ebSwwZLpb2csZIMXz2N5FxcG147jX8QL1JSo6Pcbb8yOgmC9KRgOxsDCUQ/?imgmax=800 "Plugin Registration Tool_2012-03-19_12-20-45")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhCd9t5de_19LvXJ08ruK_6EjRjj-9t9T9j31JJpUPurIUvlF87HjSdK4IEC_CEhxiFNUvjer6dmrU8IHZBefOTnd4ya7v2aXIjazAltPalrDsWpojXRb_qBNSGxi2J_4qjqQ5lYQRMgw/s1600-h/Plugin%252520Registration%252520Tool_2012-03-19_12-20-45%25255B3%25255D.png)

  
  

Click Connect, it will ask you for the password.

  
  

[![Connect to CRM Web Service_2012-03-19_12-21-24](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi0AM2wZrGIefqeSHpqFXlkjEA66aLABGVLDPKVcX5etCIJpoiClyLnJbQRGs7s1_rQFeQn_kLSBXyNImcUVLPTvBFRgUH5P0ONMKNewlqAjSZQGZ5pvcFUtzpzC0qRhMvlSjN5vZ1gJg/?imgmax=800 "Connect to CRM Web Service_2012-03-19_12-21-24")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjdCUfuRtXHWjlaPWPyImTrwYPBw00ghzNzuupxONzOIETqNi4TSkic_7xMllqiKUX296CpDu891WFxGYXvQogXynXfqEzp953xBfD0m3coxBIS7dRePdSlImMJg6RQiZ5leY0zb4qI-w/s1600-h/Connect%252520to%252520CRM%252520Web%252520Service_2012-03-19_12-21-24%25255B2%25255D.png)

  
  

Enter your password and click Ok to connect to the CRM organization web service.

  
  

After getting connected click Register > Register New Assembly

  
  

[![Plugin Registration Tool_2012-03-19_12-27-20](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjaU4pmpxu8ZAarNMk1zsoAzm7_GGWwawuhr0p_FZODig_Y13Y8HRDBHhfl5ngfTyOM-wJ8mlziWA_c6B3n7qJIyqtonZ0kFh6f739HTZtKLwPNqDqBrYb_1OY3Ows6v1aNowTUT0s03Q/?imgmax=800 "Plugin Registration Tool_2012-03-19_12-27-20")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhwTrO8-VSLZfgJsZs1-QQlU9dBP2C3n5o6NF0rsqZVcDOxwh78nGPFLfGxOkse1cSkbHCzyqWZK4v9-vzsShst89HxVK1BukJhV0b8UIL_DEJvcIIDRbSxWXVzj6FnpRPEiWAcqsvaTA/s1600-h/Plugin%252520Registration%252520Tool_2012-03-19_12-27-20%25255B2%25255D.png)

  
  

This will open Register New Plugin dialog.

  
  

[![Register New Plugin_2012-03-19_12-27-57](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgv71WOMCKc5moawXw4k58ncAvzkxG-ftSN-t1DGIuUQLefgnDp2EyrVbrbBZs048MnRdDBlJyBVdLI4jAvToodbE6cA6OP6NYw0_pCZURJjbn_Iou3tUdQsra7apnvpqj7ylFf2VaUTQ/?imgmax=800 "Register New Plugin_2012-03-19_12-27-57")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjU4B4ofVWVLhOvguc954rBE-2XgIgm-iz9cE2ZQAYHbfmCgIWIQ2-6-eFBJu9VvqvQbapMFZWfhyphenhyphenkG-GeK0cNfOYLS8eReABaIYSYLCH0DTQ9gEzyXxJsLn9yDAJ5MhPERWYafdunKqQ/s1600-h/Register%252520New%252520Plugin_2012-03-19_12-27-57%25255B5%25255D.png)

  
  

Click the three dots button in the top right of the dialog, browse to your plugin dll. Ensure that your plugin is listed and checked. Also ensure that you selected Sandbox as isolation mode, and to store your assembly in the Database as shown below.

  
  

[![Register New Plugin_2012-03-19_12-29-50](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjI15E-bxhelD2ptmn-DaiOt3WIRu5UWkBkhnFdNZGVxXBaZhVZdUwcZmUNYVbEy_jD680YPvDqR4ZdX9_lfhLjbS1N5bNNnkV3ji2iN6JtEgCGFUyhwI8aWAzvRtQqb-bKElz0vXe8gw/?imgmax=800 "Register New Plugin_2012-03-19_12-29-50")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg_3Eqgw9XAtnIKHujJ2yIaL62fLFioGZLC1aWa15Q1oVX_PGziwvnFT9HhbI99Zbk7SmfXLSC9EvO85DFGYMSK7bE5C2XXpKQL9zo7iAJKKs_bd-nYXY5bwji03Nh9kRzsR3bPddogJA/s1600-h/Register%252520New%252520Plugin_2012-03-19_12-29-50%25255B5%25255D.png)

  
  

Click Register Selected Plugins. You will see in the log the steps done by the tool and when it is done it will show message box showing how many assemblies and plugins have been registered (you could have multiple plugins in one assembly). Click Ok.

  
  

[![xRM_Demo03 - Microsoft Visual Studio (Administrator)_2012-03-19_12-36-58](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiYfOhsX02AwWx0b5UnTekQcuJ4Nf9crJEF59KBOLJuPsM5HVuav8mfEg3s73jr9_F66a-U10po3FfbkB-DULZpAhc2ad_96zeEXYvt5Rr6qdjgzPkQjE2uzqWdtmDyYQoXwT5dceSFdA/?imgmax=800 "xRM_Demo03 - Microsoft Visual Studio (Administrator)_2012-03-19_12-36-58")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg_5GmWsMnhpnWQJTbHhiGv1aUxVZjNTwmoAdC2gvwsa5uQ_MRaLi8DLyMd30KGXBaJVIUs6FsLc_oIktkfYtKFV6G8UjOImIrkC2B4kPjU2HOgI9lExqjyStQj9urKq_LJRGH8PAeQsA/s1600-h/xRM_Demo03%252520-%252520Microsoft%252520Visual%252520Studio%252520%252528Administrator%252529_2012-03-19_12-36-58%25255B4%25255D.png)

  
  

Now select your assembly from the list

  
  

[![Plugin Registration Tool_2012-03-19_12-39-46](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEieLFy8e8oNGZ3dwvUnJPD7emkveuD7BCxZKO1m81GV4VyXJ5qs5fb9MN5yBbI9dtimKEH_S5AwS45IMWEP6lPzCkCkLiXZ0fKC-txl3nC0VIHuB3R5f9kuRaZonzNpvk9ormzvA1l-cQ/?imgmax=800 "Plugin Registration Tool_2012-03-19_12-39-46")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjRENTwnD8YvykvP82rGo2UkhKBPjezKnkcC-tdqPdJs7Y4HgF0n33KZamY0wPLuMTvWeq7niFyEmvquxvGTm8lzXyonsw1JNGD_pmWenOIjCBqwzi8C6GIh8ievXMhDi0lDoa5JbgR9w/s1600-h/Plugin%252520Registration%252520Tool_2012-03-19_12-39-46%25255B4%25255D.png)

  
  

and click Register > Register New Step. This will open Register New Step dialog. This dialog used to define mainly the message, the entity, and the stage that your plugin will execute within. We will register for Message _Create_, Entity _lead_, _Pre-operaton_ stage. Click Register New Step.

  
  

[![Register New Step_2012-03-19_12-42-08](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgCCNvhJFJtFimW1cNAI_w1lUALdyLx1At8wDyImmleaAiDzc8GIkuuaFD5J-6OFaGK_YmvcCTkfImr8DdquHcefSKF60uSS9M2XUnrUCV-L4SFW3r6_462iy0cIfhIradSU_rn2ti8kw/?imgmax=800 "Register New Step_2012-03-19_12-42-08")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgciZzhzKjhR44-RoRjXAlpk6D35jAOCAW7Vom5nk5aMvuj7_igeb78TD1-UUhgO_XewhwZDKMhebQIwtGtjdX8-x6lpfeRuQAx8aF_dXcSIgAEw8idq_j31T7Oq_5UPpk8LNrCQHLD4A/s1600-h/Register%252520New%252520Step_2012-03-19_12-42-08%25255B3%25255D.png)

  
  

You will see child step added under your assembly.

  
  

[![Plugin Registration Tool_2012-03-19_12-43-20](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjUazQ8raE5uZRElLosJ5paYvz4Q077H6S6xI6Rk-mCqJeBJgBF_fssk_yS2aqIguSKmDDoHwUY4942p3G_8yvcLXmh7dWDPs4jxnfOm6khXP_owLTukkDq91phi0jes4EXewnnQ0N30A/?imgmax=800 "Plugin Registration Tool_2012-03-19_12-43-20")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiKIFokjGJ5JjN6TBsBqhcT801D-0K5jfpkTywBGSrtFUfmprn6TP2BdXP7DKJtxomqNdUMuziha9GaF670K3QrV0OW_P7lY8r_uWTYITC5oPwGnowSQRi1g-9AjoyUhX_7Sq7x1S2y5g/s1600-h/Plugin%252520Registration%252520Tool_2012-03-19_12-43-20%25255B5%25255D.png)

  
  
  
  

Now our assembly is registered and our plugin will run for create messages on the lead entity. Go to the CRM web interface and create a new lead, save it, open it again and see the Auto Number populated.

  
  

In this post we explored the plug-in basics, and developed a simple plug-in. To complete the picture, you also explored how to register our plug-in into Dynamics CRM and see it in action.