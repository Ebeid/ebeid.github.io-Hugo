--- 
title: "Microsoft Dynamics CRM 2011 for Developers | Plug-ins" 
date: '2012-03-23T15:49:00.001-05:00' 
tags: 
    - Dynamics CRM Plug-in Registration Tool 
    - Microsoft Dynamics CRM 2011 
    - Plug-ins 
    - WCF
modified_time: '2012-03-23T15:49:42.537-05:00' 
thumbnail: http://lh5.ggpht.com/-6-oxUTh5oQ8/T2zht7bBxhI/AAAAAAAAAcs/zFkQoT-Nqys/s72-c/xRM\_Demo03%252520-%252520Microsoft%252520Visual%252520Studio%252520%252528Administrator%252529\_2012-03-19\_12-33-32\_thumb.png?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-523580624632940019
blogger_orig_url: http://ebeid-soliman.blogspot.com/2012/03/microsoft-dynamics-crm-2011-for\_23.html
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

A plug-in is .Net assembly that can be used to intercept events
generated from the CRM system. Plug-ins subscribe to a set of events and
run when the events occur regardless of how the event raised (or the
method that is used to perform the activity that raised the event).

Any number of plug-ins can be associated with a given entity and event.
When multiple plug-ins are registered for the same event on the same
entity, they are called in a sequence based on the order specified on
the step registration. This value is specified as the Rank and it is
supplied when the plug-in is registered. This allows developer control
over the sequence.

**Common Uses of Plug-ins**

Plug-ins have many uses like:

-   Performing complex business logic data validation
-   Performing complex update routines on CRM entities and/or attributes
    when it is impractical to use JavaScript.
-   Grabbing data from another system and updating CRM when an entity
    instance is being created or updated.
-   Updating another system programmatically from CRM

**Plug-ins Basics**

**Event Framework** Event framework is the term that is used to describe
the technology and mechanisms available in Microsoft Dynamics CRM to
enable you to extend or customize functionality with custom code. Your
custom code will run on top of Dynamics CRM either synchronously as part
of the main Microsoft Dynamics CRM execution path, or asynchronously
from a managed queue.

**Event Execution Pipeline** Event framework executes plug-ins based on
a message pipeline execution model. A user action in the Microsoft
Dynamics CRM Web application or an SDK method call by a plug-in or other
application results in a message being sent to the organization Web
service. The message contains business entity information and core
operation information. The message is passed through the event execution
pipeline where it can be read or modified by the platform core operation
and any registered plug-ins.

The event execution pipeline processes events either synchronously or
asynchronously. The platform core operation and any plug-ins registered
for synchronous execution are executed immediately. Synchronous plug-ins
that are registered for the event are executed in a well-defined order.
Plug-ins registered for asynchronous execution are queued by the
Asynchronous Queue Agent and executed at a later time by the
asynchronous service.

**Pipeline Stages** The event execution pipeline is divided into
multiple stages, four of them are available to register custom developed
plug-ins. Multiple plug-ins that are registered in each stage can be
further be ordered (ranked) within that stage during plug-in
registration.

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p><strong>Event</strong></p></td>
<td><p><strong>Stage name</strong></p></td>
<td><p><strong>Stage number</strong></p></td>
<td><p><strong>Description</strong></p></td>
</tr>
<tr class="even">
<td>Pre-Event</td>
<td>Pre-validation</td>
<td>10</td>
<td><ul>
<li><div data-align="left">
For plug-ins that execute before the main system operation.
</div></li>
<li><div data-align="left">
Plug-ins may execute outside the database transaction.
</div></li>
<li><div data-align="left">
For plug-ins run prior to making security checks on the calling user.  <br />

</div></li>
</ul></td>
</tr>
<tr class="odd">
<td>Pre-Event</td>
<td>Pre-operation</td>
<td>20</td>
<td><ul>
<li><div data-align="left">
For plug-ins that execute before the main system operation.
</div></li>
<li><div data-align="left">
Plug-ins execute within the database transaction.
</div></li>
</ul></td>
</tr>
<tr class="even">
<td>Platform Core Operation</td>
<td>MainOperation</td>
<td>30</td>
<td><ul>
<li>Dedicated to main system operations.</li>
<li>For internal use only, no custom plug-ins can register in this stage.</li>
</ul></td>
</tr>
<tr class="odd">
<td>Post-Event</td>
<td>Post-operation</td>
<td>40</td>
<td><ul>
<li>For plug-ins that execute after the main operation.</li>
<li>Plug-ins execute within the database transaction.</li>
</ul></td>
</tr>
<tr class="even">
<td>Post-Event</td>
<td>Post-operation<br />
(Deprecated)</td>
<td>50</td>
<td><ul>
<li>For Dynamics CRM 4.0 based plug-ins ONLY.</li>
</ul></td>
</tr>
</tbody>
</table>

**Message Processing** as we saw in a previous
[post](http://ebeid-soliman.blogspot.com/2012/03/accessing-microsoft-dynamics-crm-2011.html),
any web service method call is done through <span
class="underline">OrganizationRequest</span> message. This call raises
an event. Information in this message is passed to first plug-in
registered for that event. Plug-in receives the message information in
the form of context that is passed to its <span
class="underline">Execute</span> method, where it can be read or modify
its contents before passing it to the next registered plug-in for that
event and so on. The message then passed to the platform core operation.
After the core platform operation has completed, the message is then
known as the <span class="underline">OrganizationResponse</span>. This
response is passed to the registered post-event plug-ins which may
modify it before a copy of the response is passed to any registered
asynchronous plug-ins. Finally, the response is returned to the
application or workflow that initiated the original Web service method
call.

Because a single Microsoft Dynamics CRM server can host more than one
organization, the execution pipeline is organization specific. Plug-ins
registered with the pipeline can only process business data for a single
organization.

**Inclusion in Database Transactions** Plug-ins can execute or not
execute within the database transaction of the Dynamics CRM platform.
Within the plug-in, you can detect that through the <span
class="underline">IsInTransaction</span> property in <span
class="underline">IPluginExecutionContext</span> that is passed to the
plug-in. Any registered plug-in that executes during the database
transaction and that passes an exception back to the platform cancels
the core operation. This results in a rollback of the core operation. In
addition, any pre-event or post event registered plug-ins that have not
yet executed and any workflow that is triggered by the same event that
the plug-in was registered for will not execute.

**Plug-in Isolation** The execution of plug-ins can be in an isolated
environment, known as a *sandbox*, where a plug-in can access and use
the organization Web service only. Plug-ins can’t access system
resources but can access to external endpoints (only through HTTP and
HTTPS). CRM platform collects run-time statistics and monitors plug-ins
that execute in the sandbox, if it exceeded certain thresholds or became
unresponsive, it kills the sandbox worker process (this makes all
currently executing plug-ins in the current organization fail).

**Trusts**

-   <span class="underline">Full trust</span> Plug-ins run outside the
    sandbox, available in on-premises and internet facing deployments.
-   <span class="underline">Partial trust</span> Plug-ins run inside the
    sandbox, available in all deployments.

**Develop Plug-ins**

Simply plug-ins are classes that implement the IPlugin interface. You
can write a plug-in in any .NET Framework 4 CLR-compliant language.

Now let’s consider a simple case that plug-ins may be its appropriate
solution. Let say that your company wants leads to be numbered
automatically when they are created. In order to achieve our goal, we
will add a custom field to the Lead entity and add it to the form. We
will disable this field on the form. We will create a plug-in and
register it for the Pre-event for the Create message on the Lead entity.
When a lead is created, it will look for the next available number in
the system and assign it to the newly created Lead.

**Step 1: Create Customizations**

Now we will quickly customize the Lead entity and form to accommodate
our solution. Navigate to <span class="underline">Settings</span> &gt;
<span class="underline">Customizations</span> &gt; <span
class="underline">Customize the System</span>. In the left navigation
pane, expand <span class="underline">Entities</span>, expand <span
class="underline">Lead</span>, select <span
class="underline">Fields</span>, and click New.    
In the New for Lead form, set the Display Name to Auto Number, the Type
to Whole Number, and then click <span class="underline">Save and
Close</span>. In the left navigation Pane, select <span
class="underline">Forms</span>. Click the Main Information form &gt;
Drag the field, new\_autonumber, to the Name section of the <span
class="underline">General</span> section. Select the field, click <span
class="underline">Change Properties</span>, mark the <span
class="underline">Field is read-only</span> check box, and then click
<span class="underline">OK</span>. Click <span class="underline">Save
and Close</span>, and then <span class="underline">Publish</span>.

**Step 2: Create the Plug-in**

1- Open Visual Studio and Create a new project of type Class Library.

2- Add references to Microsoft.Xrm.Client.dll, Microsoft.Xrm.Sdk.dll,
and Microsoft.crm.sdk.proxy.dll \[located at %SDK%\\bin folder\].

3- Add references to System.Data.Services, System.Data.Services.Client,
System.Runtime.Serialization, and System.ServiceModel.

4- Add reference to Microsoft.IdentityModel.dll from "C:\\Program
Files\\Reference Assemblies\\Microsoft\\Windows Identity
Foundation\\v3.5\\”. Then go to reference properties and set Copy Local
to True for the DLL. The DLL will be included in the package. If you
don’t have the dll you need to install [Windows Identity
Foundation](http://www.microsoft.com/download/en/details.aspx?id=17331).

5- Make your class implement the IPlugin interface, and implement its
member method Execute method. This identifies your class as a plugin to
the CRM platform when registering your assembly later. Plug-in code will
be placed in the <span class="underline">Execute</span> method which
takes a parameter of type <span
class="underline">IServiceProvider</span>. This parameter is a container
of many objects that will be utilized by our code.

First get the IPluginExecutionContext. This context object gives you
access to all the property values associated with the entity and event
context where the method is being executed.

    IPluginExecutionContext context = (IPluginExecutionContext) serviceProvider.GetService(typeof(IPluginExecutionContext));

  
  

InputParameters property of the context is a collection of the request
parameters associated with the event. We use it to check the entity of
which the event is fired.

  
  

    if (context.InputParameters.Contains("Target") && context.InputParameters["Target"] is Entity)
                {
                    Entity entity = (Entity)context.InputParameters["Target"];
                    if (entity.LogicalName != "lead")
                        return;

  
  

Then we get the OrganizationServiceFactory to use it to create an
OrganizationService. We also get the TracingService. Then we edited our
auto number field with the next maximum number in the organization.
GetMaxLeadNumber is a typical method that passes a QueryExpression to
the OrganizationService to get the next max lead number.

  
  

    IOrganizationServiceFactory orgServiceFactory = (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
                    ITracingService tracingService = (ITracingService)serviceProvider.GetService(typeof(ITracingService));
                    IOrganizationService orgService = orgServiceFactory.CreateOrganizationService(context.UserId);

                    try
                    {                                  
                        entity.Attributes["new_autonumber"] = GetMaxLeadNumber(orgService);            
                    }
                    catch (Exception ex)
                    {
                        tracingService.Trace("xRM_Demo03 | {0}", ex.ToString());
                        throw; 
                    }                
                }
            }

  
  

Now your class should look like:

  
  

    using System;
    using System.ComponentModel;
    using System.Diagnostics;
    using System.Security;
    using System.ServiceModel.Description;
    using Microsoft.Xrm.Sdk;
    using Microsoft.Xrm.Sdk.Client;
    using Microsoft.Xrm.Sdk.Query;
    using System.Collections;

    namespace xRM_Demo03
    {
        public class Plugin:IPlugin 
        {
            public void Execute(IServiceProvider serviceProvider)
            {
                IPluginExecutionContext context = 
                    (IPluginExecutionContext)serviceProvider.GetService(typeof(IPluginExecutionContext));

                if (context.InputParameters.Contains("Target") && context.InputParameters["Target"] is Entity)
                {
                    Entity entity = (Entity)context.InputParameters["Target"];
                    if (entity.LogicalName != "lead")
                        return;

                    IOrganizationServiceFactory orgServiceFactory = (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
                    IOrganizationService orgService = orgServiceFactory.CreateOrganizationService(context.UserId);
                    ITracingService tracingService = (ITracingService)serviceProvider.GetService(typeof(ITracingService));

                    try
                    {                    
                        Random rand = new Random();                    
                        entity.Attributes["new_autonumber"] = GetMaxLeadNumber(orgService);            
                    }
                    catch (Exception ex)
                    {
                        tracingService.Trace("xRM_Demo03 | {0}", ex.ToString());
                        throw; 
                    }                
                }
            }

            private int GetMaxLeadNumber(IOrganizationService orgService)
            {    
                QueryExpression qe = new QueryExpression("lead");
                qe.ColumnSet.AddColumn("new_autonumber");         

             qe.AddOrder("new_autonumber", OrderType.Descending);
                qe.PageInfo.Count = 1;
                qe.PageInfo.PageNumber = 1;

                Entity entity = (Entity)orgService.RetrieveMultiple(qe)[0];
                if (entity.Attributes["new_autonumber"].ToString()!= string.Empty)
                    return int.Parse(entity.Attributes["new_autonumber"].ToString()) + 1;
                else
                    return 1;
            }
        }
    }

  
  

Now the last step is to sign your assembly. Double click Properties
under your plugin project.

  
  

[<img src="http://lh5.ggpht.com/-6-oxUTh5oQ8/T2zht7bBxhI/AAAAAAAAAcs/zFkQoT-Nqys/xRM_Demo03%252520-%252520Microsoft%252520Visual%252520Studio%252520%252528Administrator%252529_2012-03-19_12-33-32_thumb.png?imgmax=800" title="xRM_Demo03 - Microsoft Visual Studio (Administrator)_2012-03-19_12-33-32" width="240" height="183" alt="xRM_Demo03 - Microsoft Visual Studio (Administrator)_2012-03-19_12-33-32" />](http://lh3.ggpht.com/-IfxDR5X1NDo/T2zhtdfVywI/AAAAAAAAAck/M_NB9igKWZU/s1600-h/xRM_Demo03%252520-%252520Microsoft%252520Visual%252520Studio%252520%252528Administrator%252529_2012-03-19_12-33-32%25255B2%25255D.png)

  
  

then click Signing from the left tabs

  
  

[<img src="http://lh6.ggpht.com/-a2ruRgXRBI8/T2zhv_kywZI/AAAAAAAAAc8/hv5c-r1GKAY/xRM_Demo03%252520-%252520Microsoft%252520Visual%252520Studio%252520%252528Administrator%252529_2012-03-19_12-34-21_thumb%25255B1%25255D.png?imgmax=800" title="xRM_Demo03 - Microsoft Visual Studio (Administrator)_2012-03-19_12-34-21" width="467" height="398" alt="xRM_Demo03 - Microsoft Visual Studio (Administrator)_2012-03-19_12-34-21" />](http://lh3.ggpht.com/-e5ZX4Tzeb7s/T2zhuUwluEI/AAAAAAAAAc0/srC4wTbiOd8/s1600-h/xRM_Demo03%252520-%252520Microsoft%252520Visual%252520Studio%252520%252528Administrator%252529_2012-03-19_12-34-21%25255B3%25255D.png)

  
  

select Sign the assembly checkbox, choose New from the dropbox or choose
an existing key. Build the project. Now we are ready to register our
plugin into Dynamics CRM.

  
  

**Step 3: Register the Plug-in**

  
  
  
  
  
  

The Dynamics CRM SDK have a tool to register plugins located as a source
code at %CRMSDK%\\tools\\pluginregistration. Open the solution, build
it, and run it.

  
  

1- Click the <span class="underline">Create New Connection</span> on the
toolbar. Enter a name for the connection, organization URL, and the
email you used for creating this
organization.[<img src="http://lh6.ggpht.com/-OYNYNwngpEE/T2zhxBRRhJI/AAAAAAAAAdM/P76G_TQGVxQ/Plugin%252520Registration%252520Tool_2012-03-19_12-20-45_thumb%25255B1%25255D.png?imgmax=800" title="Plugin Registration Tool_2012-03-19_12-20-45" width="395" height="327" alt="Plugin Registration Tool_2012-03-19_12-20-45" />](http://lh4.ggpht.com/-O-dFTKlbZG4/T2zhwVVSUDI/AAAAAAAAAdE/0R7GPtzg6Vg/s1600-h/Plugin%252520Registration%252520Tool_2012-03-19_12-20-45%25255B3%25255D.png)

  
  

Click <span class="underline">Connect</span>, it will ask you for the
password.

  
  

[<img src="http://lh6.ggpht.com/-UIQ8Gnu0e24/T2zhxzd-ZDI/AAAAAAAAAdc/ypOCI9R7Id4/Connect%252520to%252520CRM%252520Web%252520Service_2012-03-19_12-21-24_thumb.png?imgmax=800" title="Connect to CRM Web Service_2012-03-19_12-21-24" width="244" height="212" alt="Connect to CRM Web Service_2012-03-19_12-21-24" />](http://lh4.ggpht.com/-LThsQayYv78/T2zhxSbyKjI/AAAAAAAAAdU/VLvoRl1Aacg/s1600-h/Connect%252520to%252520CRM%252520Web%252520Service_2012-03-19_12-21-24%25255B2%25255D.png)

  
  

Enter your password and click Ok to connect to the CRM organization web
service.

  
  

After getting connected click <span class="underline">Register</span>
&gt; <span class="underline">Register New Assembly</span>

  
  

[<img src="http://lh5.ggpht.com/-LUfbZQic9QI/T2zhyntykJI/AAAAAAAAAds/DqA5bbv8py0/Plugin%252520Registration%252520Tool_2012-03-19_12-27-20_thumb.png?imgmax=800" title="Plugin Registration Tool_2012-03-19_12-27-20" width="244" height="126" alt="Plugin Registration Tool_2012-03-19_12-27-20" />](http://lh5.ggpht.com/-eSEzdotUCaI/T2zhyBsIBCI/AAAAAAAAAdk/WfTBDO_nugM/s1600-h/Plugin%252520Registration%252520Tool_2012-03-19_12-27-20%25255B2%25255D.png)

  
  

This will open Register New Plugin dialog.

  
  

[<img src="http://lh3.ggpht.com/-eSqBRvBgF44/T2zhzsgsDDI/AAAAAAAAAd8/5G4_OpdjnBI/Register%252520New%252520Plugin_2012-03-19_12-27-57_thumb%25255B3%25255D.png?imgmax=800" title="Register New Plugin_2012-03-19_12-27-57" width="471" height="517" alt="Register New Plugin_2012-03-19_12-27-57" />](http://lh3.ggpht.com/-KLxe9EnZNe4/T2zhy04bgUI/AAAAAAAAAd0/KggJbnZIFpQ/s1600-h/Register%252520New%252520Plugin_2012-03-19_12-27-57%25255B5%25255D.png)

  
  

Click the three dots button in the top right of the dialog, browse to
your plugin dll. Ensure that your plugin is listed and checked. Also
ensure that you selected Sandbox as isolation mode, and to store your
assembly in the Database as shown below.

  
  

[<img src="http://lh4.ggpht.com/-Y12kxSSZiYs/T2zh0jJdA3I/AAAAAAAAAeM/N_DQTD6V_vk/Register%252520New%252520Plugin_2012-03-19_12-29-50_thumb%25255B3%25255D.png?imgmax=800" title="Register New Plugin_2012-03-19_12-29-50" width="476" height="522" alt="Register New Plugin_2012-03-19_12-29-50" />](http://lh6.ggpht.com/-2ZbzQXxWZvk/T2zh0JHlQOI/AAAAAAAAAeE/2NbmCx1L-n0/s1600-h/Register%252520New%252520Plugin_2012-03-19_12-29-50%25255B5%25255D.png)

  
  

Click <span class="underline">Register Selected Plugins</span>. You will
see in the log the steps done by the tool and when it is done it will
show message box showing how many assemblies and plugins have been
registered (you could have multiple plugins in one assembly). Click Ok.

  
  

[<img src="http://lh6.ggpht.com/-jDQwmD5GvmM/T2zh1uJr6pI/AAAAAAAAAec/PrW1tHbf1-A/xRM_Demo03%252520-%252520Microsoft%252520Visual%252520Studio%252520%252528Administrator%252529_2012-03-19_12-36-58_thumb%25255B2%25255D.png?imgmax=800" title="xRM_Demo03 - Microsoft Visual Studio (Administrator)_2012-03-19_12-36-58" width="477" height="518" alt="xRM_Demo03 - Microsoft Visual Studio (Administrator)_2012-03-19_12-36-58" />](http://lh4.ggpht.com/-dcoQAsZmjYQ/T2zh0_2kEUI/AAAAAAAAAeU/7YMVXjnTKRo/s1600-h/xRM_Demo03%252520-%252520Microsoft%252520Visual%252520Studio%252520%252528Administrator%252529_2012-03-19_12-36-58%25255B4%25255D.png)

  
  

Now select your assembly from the list

  
  

[<img src="http://lh3.ggpht.com/-p55bYm8q1QQ/T2zh35L3kzI/AAAAAAAAAes/SPuCiM7BFRc/Plugin%252520Registration%252520Tool_2012-03-19_12-39-46_thumb%25255B2%25255D.png?imgmax=800" title="Plugin Registration Tool_2012-03-19_12-39-46" width="479" height="401" alt="Plugin Registration Tool_2012-03-19_12-39-46" />](http%0A://lh4.ggpht.com/-MFmwz2UmKzo/T2zh2Wpa7fI/AAAAAAAAAek/Izxl2LmBYp0/s1600-h/Plugin%252520Registration%252520Tool_2012-03-19_12-39-46%25255B4%25255D.png)

  
  

and click Register &gt; <span class="underline">Register New
Step</span>. This will open Register New Step dialog. This dialog used
to define mainly the message, the entity, and the stage that your plugin
will execute within. We will register for Message *Create*, Entity
*lead*, *Pre-operaton* stage. Click <span class="underline">Register New
Step</span>.

  
  

[<img src="http://lh4.ggpht.com/-W5TGJREt2hg/T2zh4mRpw9I/AAAAAAAAAe8/awk2cOcLa6E/Register%252520New%252520Step_2012-03-19_12-42-08_thumb%25255B1%25255D.png?imgmax=800" title="Register New Step_2012-03-19_12-42-08" width="453" height="243" alt="Register New Step_2012-03-19_12-42-08" />](http://lh6.ggpht.com/-qNi8MGQGk1E/T2zh4YYEhjI/AAAAAAAAAe0/HuPsTNBJKZY/s1600-h/Register%252520New%252520Step_2012-03-19_12-42-08%25255B3%25255D.png)

  
  

You will see child step added under your assembly.

  
  

[<img src="http://lh4.ggpht.com/-XLKKj5bArqo/T2zh5Un6LII/AAAAAAAAAfM/SBsXDSw2_RA/Plugin%252520Registration%252520Tool_2012-03-19_12-43-20_thumb%25255B1%25255D.png?imgmax=800" title="Plugin Registration Tool_2012-03-19_12-43-20" width="244" height="65" alt="Plugin Registration Tool_2012-03-19_12-43-20" />](http://lh5.ggpht.com/-mA7XuBdhmDI/T2zh5C4sjJI/AAAAAAAAAfE/LLKPxkgJqVg/s1600-h/Plugin%252520Registration%252520Tool_2012-03-19_12-43-20%25255B5%25255D.png)

  
  
  
  

Now our assembly is registered and our plugin will run for create
messages on the lead entity. Go to the CRM web interface and create a
new lead, save it, open it again and see the Auto Number populated.

  
  

In this post we explored the plug-in basics, and developed a simple
plug-in. To complete the picture, you also explored how to register our
plug-in into Dynamics CRM and see it in action.
