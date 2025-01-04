---
title: 'Microsoft Dynamics CRM 2011 for Developers | Accessing Microsoft Dynamics CRM 2011 using WCF'
date: 2012-03-02T16:28:00.001-06:00
draft: false
url: /2012/03/accessing-microsoft-dynamics-crm-2011.html
tags: 
- Microsoft Dynamics CRM 2011
- Early Binding
- Late Binding
- WCF
---

#### Contents

1.  Introduction
2.  Creating a client application
3.  Using the Discovery Service
4.  Using the Organization Service
5.  Working with CRM Data
    1.  Late Binding Approach
        1.  Using RetrieveMultiple method
        2.  Using Retrieve method
        3.  Using Update method
        4.  Using Delete method
        5.  Using Create method
    2.  Early binding Approach
        1.  generating Client Types
        2.  Enable ProxyTypeBehavior
        3.  Using RetrieveMultiple method
        4.  Using Retrieve method
        5.  Using Create method

### Introduction

**Microsoft Dynamics CRM** is a Customer Relationship Management software package developed to focus mainly on Sales, Marketing, and Service (help desk) sectors. The Microsoft Dynamics family of business applications includes other related products such as Microsoft Dynamics AX, Microsoft Dynamics GP, Microsoft Dynamics NAV, and Microsoft Dynamics SL.

Basically, Dynamics CRM is a client-server web application that supports extensive web services interfaces. Dynamics CRM 2011 introduces a new WCF interface for working with data, services and metadata.

Microsoft Dynamics CRM supports two kinds of deployments: Online, on-premises. You can signup for 30 days free trial at [http://crm.dynamics.com/en-us/trial-overview](http://crm.dynamics.com/en-us/trial-overview "http://crm.dynamics.com/en-us/trial-overview"). This will provide you with 30 days full functioning online version of Dynamics CRM. We will you this version in this post and the upcoming posts.

There is a lot of situations where organizations want to gain more benefit of its Dynamics CRM deployment than what Dynamics CRM can offer through its built-in customization tools. Based on the situation, you as a developer may be required to develop applications that interact with Dynamics CRM through its web services interfaces or develop applications that run within Dynamics CRM itself.

In this post we will explore one of the techniques of interacting with Dynamics CRM through its web services interfaces. We will build a windows forms application that connects to the online version of Dynamics CRM 2011, retrieve data from it, and manipulate its data. To continue with this post you need to signup for an online trial version and to install Microsoft Dynamics CRM 2011 Software Development Kit (SDK) ( download from [http://www.microsoft.com/download/en/details.aspx?id=24004](http://www.microsoft.com/download/en/details.aspx?id=24004) )

**Step 1: Create a client application**

Simply create a new windows forms application. Right click your project in the solution explorer and select properties, locate the Target Framework drop down and change it from .Net Framework 4 Client Profile to .Net Framework 4. Add references to _System.Runtime.Serialization.dll_ and _System.ServiceModel.dll_ and _System.Security._ Add references to _Microsoft.Xrm.Sdk.dll_ and _Microsoft.Crm.Sdk.Proxy.dll_ (both files located in the Bin folder in your CRM SDK installation directory). Right click on the project in the solution explorer and click Add existing, browse to %CRMSDK%\\samplecode\\cs\\helpercode\\deviceidmanager.cs

The DeviceIdManager class is included in the Dynamics CRM SDK to register a computing device with Windows Live ID through the generation of a Device ID and password. Then it optionally stores that information in an encrypted format on the local disk for later use. This functionality is required when authenticating with Microsoft Dynamics CRM online. The device registration is stored in %USERPROFILE%\\LiveDeviceID\\LiveDevice.xml. It looks like:

```
<?xml version="1.0"?>  
 AQAAANCMnd8BFdERjHoAwE/Cl+sBAAAAooZFtct7dEyyPUNu1eZujgAAAAACAAAAAAADZgAAqAAAABAAAAD0860vIxbs57z9CgRRPAtTAAAAAASAAACgAAAAEAAAAFL9eqV3G5WLFhHYAkX1/z8gAAAAZjBYCltk8cNwuydeQK70t9/txdmoJhIGeN2StJbyx9EUAAAAY10YU7QprX0EO5Fq43A/S2Wer2I= 
```  
  

The CRM SDK team is separating the more CRM specific types from the xRM Application Framework related types.  The Microsoft.Xrm.Sdk assembly will provide all the low-level types necessary for basic operation against the xRM Application Framework. The Microsoft.Crm.Sdk.Proxy.dll  assembly will abstract away much of the complexity of dealing with the WCF services directly.

  
  

Now, try to make your application interface like the one in the image below.

  
  

[![app](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhN4MuoGtGVvTEpJ7thlxIRbgjpJKZcDk6EFMnIK0A5Sj22M-EULxcT3wUZtEoKZsK3UZiTRCFUAFLKb1euqr5TLpWCTVth9gT4nRsBzIWVeR4vJ5RKCZvoMtCHgErO3kvd5EyBHSEQ7Q/?imgmax=800 "app")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiQjYJcWQ73C9pKzv1Z1qWPOieAw1j1mtj_MyGtwyJK8GmJSHcd4Uz21-3o3SqFJKGV8OKdql53GBnNzFRXrnP8taL4zJh_lFxENzCiV9fxLcYBKuvjRFXgsJZ_Myo4OoWFYLR6Q5c77w/s1600-h/app3.jpg)

  
  

Now we created the application interface, added the required references, and ready for the real thing :)

  
  

**Step 2: Using the Discovery Service**

  
  

The discovery service allows you to explore and enumerate the organizations on a certain CRM server and the web services endpoint URL needed to access the Organization Services web service for each of these organizations (The CRM server can contain multiple organizations). We will use this information later to configure the organization web service proxy and call web service methods to access the organization’s data and metadata. The service respects security such that it will only return those organizations to which a user has access. The discovery service is accessed using methods on the **IDiscoveryService** interface. The **DiscoveryServiceProxy** class is a helper class to make it easier to get instances of **IDiscoveryService** without having to deal with all the WCF low-level details.

  
  

Now on the forms designer surface double click on the Discover button to add event handler and open the MainWindow.xaml.cs code behind file. In the code behind, add the following using statements:

  
  
```
using Microsoft.Xrm.Sdk;  
using Microsoft.Xrm.Sdk.Client;  
using Microsoft.Xrm.Sdk.Discovery;  
using System.ServiceModel.Description;  
using Microsoft.Crm.Services.Utility;  
using Microsoft.Xrm.Sdk.Query;  
using Microsoft.Xrm.Sdk.Messages;
```  
  

Inside the frmMain class, add the following private properties to hold references to the organization details (the Discovery service and the Organization service).

  
  
```
private OrganizationDetail CurrentOrganizationDetail { get; set; }  
private IDiscoveryService DiscoveryService { get; set; }  
private OrganizationServiceProxy OrgService { get; set; }  
private ClientCredentials \_ClientCreds { get; set; }  
private ClientCredentials \_DeviceCreds { get; set; }  
private bool IsLiveID { get; set; }
```  
  

Now, let's add to frmMain class a helper method to builds the full Uri of the discovery service.

  
  
```
        public Uri GetDiscoveryServiceUri(string serverName)  
        {  
            string discoSuffix = @"/XRMServices/2011/Discovery.svc";  
  
            return new Uri(string.Format("{0}{1}", serverName, discoSuffix));  
        }
```  
  

Next, In the event handler for the Discover button, add the following code to use the **ServiceConfigurationFactory** helper class to get an instance of the Discovery service configuration. This returned as an **IServiceConfiguration<IDiscoveryService>** type that hides and simplifies some of the lower level WCF configuration.

  
  
```
var discoUri = GetDiscoveryServiceUri(ServerURL.Text);  
IServiceConfiguration dinfo =               	ServiceConfigurationFactory.CreateConfiguration(discoUri);
```  
  

Different credentials are needed for CRM online vs. on premises. To differentiate between them we will add the following **GetServerType** helper method.

  
  
```
public AuthenticationProviderType GetServerType(Uri uri)  
{  
   return ServiceConfigurationFactory.CreateConfiguration(uri).AuthenticationType;  
}
```  
  

Now, we will return to the Discover button handler. The follwoing code will create a DiscoveryServiceProxy instance based on the server type we connecting to (on-line or on-premises). Note that DeviceIdManager class have been used only in the on-line scenario. Then we use this instance (DiscoveryServiceProxy) to connect to the server, authenticate, and execute our RetrieveOrganizationsRequest to get RetrieveOrganizationResponse. This response has a property OrganizationDetails that is an array of OrganizationDetail objects which we will use to fill the oragnizations combo box. Add the following code to the couple of lines that you are added to btnDiscover\_click handler.

  
  
```
\_ClientCreds = new ClientCredentials();  
DiscoveryServiceProxy dsp;  
  
if (GetServerType(discoUri) == AuthenticationProviderType.LiveId)  
{  
    \_ClientCreds.UserName.UserName = username.Text;  
    \_ClientCreds.UserName.Password = password.Text;  
  
    \_DeviceCreds = DeviceIdManager.LoadOrRegisterDevice();  
  
    dsp = new DiscoveryServiceProxy(discoUri, null, \_ClientCreds, \_DeviceCreds);  
    IsLiveID = true;  
}  
else  
{  
    \_ClientCreds.Windows.ClientCredential.UserName = username.Text;  
    \_ClientCreds.Windows.ClientCredential.Password = password.Text;  
    \_ClientCreds.Windows.ClientCredential.Domain = domain.Text;  
  
    dsp = new DiscoveryServiceProxy(dinfo, \_ClientCreds);  
    IsLiveID = false;  
}  
  
dsp.Authenticate();  
var orgRequest = new RetrieveOrganizationsRequest();  
var orgResponse = dsp.Execute(orgRequest) as RetrieveOrganizationsResponse;  
comboOrgs.ItemsSource = orgResponse.Details;
```  
  

You can now check your frmMain.cs aginst the below code. If everything is Ok, hit F5, enter the user name/password you used in your 30-days free trial signup (or your active directory credentials, if you test against your on-premises deployment), click Discover button. You will see the organizations combo box filled with the available organizations on this server that you have access to.

  
  
```
using System;  
using System.Collections.Generic;  
using System.ComponentModel;  
using System.Data;  
using System.Drawing;  
using System.Linq;  
using System.Text;  
using System.Windows.Forms;  
using System.Collections;  
  
using Microsoft.Xrm.Sdk;  
using Microsoft.Xrm.Sdk.Client;  
using Microsoft.Xrm.Sdk.Discovery;  
using System.ServiceModel.Description;  
using Microsoft.Crm.Services.Utility;  
  
using Microsoft.Xrm.Sdk.Query;  
using Microsoft.Xrm.Sdk.Messages;  
  
namespace xRM\_Demo01  
{  
    public partial class frmMain : Form  
    {  
        private OrganizationDetail CurrentOrganizationDetail { get; set; }  
        private IDiscoveryService DiscoveryService { get; set; }  
        private IOrganizationService OrgService { get; set; }  
        private ClientCredentials \_ClientCreds { get; set; }  
        private ClientCredentials \_DeviceCreds { get; set; }  
        private bool IsLiveID { get; set; }  
        public frmMain()  
        {  
            InitializeComponent();  
        }  
  
        private void btnDiscover\_Click(object sender, EventArgs e)  
        {  
            var discoUri = GetDiscoveryServiceUri(txtServer.Text);  
  
            IServiceConfiguration dinfo =  
                ServiceConfigurationFactory.CreateConfiguration(discoUri);  
            \_ClientCreds = new ClientCredentials();  
            DiscoveryServiceProxy dsp;  
  
            if (GetServerType(discoUri) == AuthenticationProviderType.LiveId)  
            {  
                \_ClientCreds.UserName.UserName = txtUserName.Text;  
                \_ClientCreds.UserName.Password = txtPassword.Text;  
  
                \_DeviceCreds = DeviceIdManager.LoadOrRegisterDevice();  
  
                dsp = new DiscoveryServiceProxy(discoUri, null, \_ClientCreds, \_DeviceCreds);  
                IsLiveID = true;  
            }  
            else  
            {  
                MessageBox.Show("This is not a valid Microsoft Dynamics CRM online URL");  
                return;  
            }  
  
            dsp.Authenticate();  
            var orgRequest = new RetrieveOrganizationsRequest();  
            var orgResponse = dsp.Execute(orgRequest) as RetrieveOrganizationsResponse;  
            comboOrgs.DataSource = orgResponse.Details;  
            comboOrgs.DisplayMember = "FriendlyName";  
            comboOrgs.ValueMember = "UrlName";  
        }  
        public Uri GetDiscoveryServiceUri(string serverName)  
        {  
            string discoSuffix = @"/XRMServices/2011/Discovery.svc";  
  
            return new Uri(string.Format("{0}{1}", serverName, discoSuffix));  
        }  
        public AuthenticationProviderType GetServerType(Uri uri)  
        {  
            return ServiceConfigurationFactory.CreateConfiguration(uri).AuthenticationType;  
        }
```  
  

**Step 3: Using the Organization Service**

  
  

The organization service is the endpoint that you will use to interact with an individual organization's data and metadata services. It accessed using the methods on the IOrganizationService interface. The **OrganizationServiceProxy** helper class is used to make it easier to get instance of IOrganizationService without dealing with the WCF low-level details. Double click on the Connect button to add an event handler for it and add the following code.

  
  
```
            if (comboOrgs.SelectedItem == null)  
            {  
                MessageBox.Show("You must select an organization before connecting");  
                return;  
            }  
            this.CurrentOrganizationDetail = comboOrgs.SelectedItem as OrganizationDetail;  
            Uri orgServiceUri = new Uri(CurrentOrganizationDetail.Endpoints\[EndpointType.OrganizationService\]);  
            if (IsLiveID)  
            {  
                OrgService = new OrganizationServiceProxy(orgServiceUri, null, \_ClientCreds, \_DeviceCreds);  
            }  
            else  
            {  
                IServiceConfiguration orgConfigInfo =  
                    ServiceConfigurationFactory.CreateConfiguration(orgServiceUri);  
                OrgService = new OrganizationServiceProxy(orgConfigInfo, \_ClientCreds);  
            }
```  
  

The added code checks that you selected an organization, get the select organization as an OrganizationDetail object, use the **EndPoints** of this object to get the Uri of the Organization Service. Then use this information and the client credentials and the device credentials to create an object of **OrganizationServiceProxy**.

  
  

Now we are ready to start interacting with the organization service through this proxy (which will be the next step). If you want to ensure that you did everything right, you can try send a simple request to the organization service and see the result. To do so, we can send the WhoAmI message to the service and receive the response (the ID of the logged in used). Add a using statement for _Microsoft.Crm.Sdk.Messages_. Add the following code to the end of btnConnect\_click to test your connectivity.

  
  
```
WhoAmIRequest req = new WhoAmIRequest();  
var response = OrgService.Execute(req) as WhoAmIResponse;  
MessageBox.Show("You are connected as userid " + response.UserId.ToString());
```  
  

Run, put your credentials an server, click Discover, choose your organization from the combo box and click connect. You will get something like the below image.

  
  

[![msg](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjt2lJVYL4MVKvCl0rg574-9ejmIZ-5AuO6396YoPvx5tqN8UDzsqZT5CbFavbaXKEx-F7qEsDtTQ34WqR0L5e_c_KAKMBvdSPBvVbtl-VQmqRihI8k6UuXm73frVBYTFcoihBVTP7c0A/?imgmax=800 "msg")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi9xZYOCJFC5DcQyFkLMyi6WoY0_MjLEDqkCGVhEig-bonKTegGGkKbSu36ir16eVRwVBRhxwcckdRm2xvKngxUpxnJNiC1vcpjnqPtqZvuj22BXLPzSfcRMgeiYCLQ8AzlsART9Pg1Pg/s1600-h/msg4.jpg)

  
  

**Step 4: Working with the CRM data**

  
  

_Early versus Late-Bounding_ In Microsoft Dynamics CRM 2011, you can choose from several programming styles to find the model that best fits your situation.

  
  

>   
> 
> In Early-Bound style, you create a class for each business entity in your CRM deployment. You will use these classes to access business data in your CRM deployment. There is a code generation tool included in the %CRMSDK%\\bin called crmsvcutil.exe that will generate early-bound entity classes for you. It works with on-premises and online deployments. Every time you make customizations to your entities, you have to run this tool to regenerate these classes again. The advantages of using early-bound entity classes is that all type references are checked at compile time. You will also enjoy the intellisense support.
> 
>   
>   
> 
> In Late-Bound style, you can work with the data in CRM without having classes representing each data entity in the organization. Most Probably, you will use this style when working with entities (or customizations) that you can’t anticipate at the development time.
> 
>   

  
  

In this step we will work with the CRM data using late-bound style to retrieve all accounts data in our CRM, update it, save it, and add new records also.

  
  

**Method** : **RetrieveMultiple**

  
  

To retrieve multiple records from Dynamics CRM, we use the **RetrieveMultiple** of the organization service and pass a **QueryExpression** object to it. QueryExpression holds all the information required to get the desired data from Dynamics CRM. To construct the Query expression you need:

  
  

  
*   **ColumnSet** object to specify the columns we need to retrieve.
  
  
*   **ConditionExpression** object to hold any conditions we will use to filter the returned rows.
  
  
*   **FilterExpression** object to hold all the ConditionExpression objects we use in our query. This enables us to make complex queries.
  
  
*   **EntityName** a string property used to specify the entity the query runs against.
  
  
*   You can also order the returned data through method **AddOrder(“columnName”, OrderType).** OrderType is an enumeration have the values Ascending and Descending.
  

  
  

For Simplicity we will retrieve columns name and accountid of all account type records in CRM. Because we using late-bound style, we get the results into EntityCollection collection. We enumerate through the returned collection, and put the entities into a list of custom objects of type Item. Then we bind our accounts combobox to this list.

  
  
```
            ColumnSet cs = new ColumnSet();  
            cs.AddColumns("name", "accountid");  
  
            QueryExpression qe = new QueryExpression();  
            qe.ColumnSet = cs;  
            qe.EntityName = "account";  
  
            EntityCollection accountList = OrgService.RetrieveMultiple(qe);  
            List accounts = new List();  
            comboAccounts.ValueMember = "Value";  
            comboAccounts.DisplayMember = "Name";  
            for (int i = 0; i < accountList.Entities.Count; i++ )  
            {  
                accounts.Add(new Item(accountList\[i\].Attributes\["name"\].ToString(),  
                    accountList\[i\].Attributes\["accountid"\].ToString()));  
            }  
            comboAccounts.DataSource = accounts;  
}
```  
  

Also add the following class into your solution namespace, which holds the acounts name and accountid to bind it to the combobox.

  
  
```
    class Item  
    {  
        private string \_name;  
        private string \_value;  
        public string Name  
        {  
            get { return \_name; }  
            set { \_name = value; }  
        }  
        public string Value  
        {  
            get { return \_value; }  
            set { \_value = value; }  
        }  
        public Item(string p\_name, string p\_value)  
        {  
            Name = p\_name;   
            Value = p\_value;  
        }  
    }
```  
  

Now you can run the application, connect to your organization, and check that the combobox is filled of your accounts data.

  
  

**Method :** **Retrieve**

  
  

Now we will use the accountid of the selected account in the combobox to get the rest of the account data. In this case we will use the **Retrieve** method of the organization service. This method retrieves just one record of the type specified in the first argument, designated by the key passed in the second argument. Double click on the accounts combobox to add an event handler for the SelectedIndexChanged event. Add the following code to this event handler to fill the form with the account data.

  
  
```
            ColumnSet cs2 = new ColumnSet(new string\[\] {"address1\_city","address1\_line1","address1\_stateorprovince",  
                "name","industrycode"});  
            try  
            {  
                var account = OrgService.Retrieve("account", new Guid(comboAccounts.SelectedValue.ToString()), cs2);  
                txtName.Text = account.Attributes\["name"\].ToString();  
                txtCity.Text = account.Attributes\["address1\_city"\].ToString();  
                txtAddress.Text = account.Attributes\["address1\_line1"\].ToString();  
                txtState.Text = account.Attributes\["address1\_stateorprovince"\].ToString();  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show("An error happened: " + ex.Message);  
            }
```  
  

**Method : Update**

  
  

Now we can go farther and modify the current displayed account data and try to save it. To save any entity data into CRM, create an Entity object and pass the entity type into the constructor (it will be "account" in our case). Then set the attribute values you want and pass the updated entity to the organization service **Update** method. Add the following code the save button click event handler to realize the update operation.

  
  
```
   
try  
            {  
                Entity account = new Entity("account");  
                account.Attributes\["accountid"\] = new Guid(comboAccounts.SelectedValue.ToString());  
                account.Attributes\["name"\] = txtName.Text;  
                account.Attributes\["address1\_line1"\] = txtAddress.Text;  
                account.Attributes\["address1\_city"\] = txtCity.Text;  
                account.Attributes\["address1\_stateorprovince"\] = txtState.Text;  
                OrgService.Update(account);  
                MessageBox.Show("Account updated successfully");  
                // TODO: reload the accounts combobox.  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show("An error occurred : " + ex.Message);  
            }         
```  
  

**Method : Delete**

  
  

To delete a record you use the **Delete** method of the organization service, pass the entity type name and its key like the following.

  
  
```
try  
            {  
                OrgService.Delete("account", new Guid(comboAccounts.SelectedValue.ToString()));  
                MessageBox.Show("Account deleted successfully");  
                // TODO: reload the accounts combobox  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show("An error occurred : " + ex.Message);  
            }
```  
  

Now let's add code to clear the form in the clear button click event handler.

  
  
```
            txtName.Text = "";  
            txtCity.Text = "";  
            txtAddress.Text = "";  
            txtState.Text = "";
```  
  

**Method : Create**

  
  

To insert a new record to CRM, we create an Entity object passing the entity name to its constructor, set its attributes, and pass it to the organization service **Create** method. Add the following code to the save new button click event handler.

  
  
```
try  
            {  
                Entity account = new Entity("account");  
                account.Attributes\["name"\] = txtName.Text;  
                account.Attributes\["address1\_line1"\] = txtAddress.Text;  
                account.Attributes\["address1\_city"\] = txtCity.Text;  
                account.Attributes\["address1\_stateorprovince"\] = txtState.Text;  
                OrgService.Create(account);  
                MessageBox.Show("Account created successfully");  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show("An error occurred : " + ex.Message);  
            }
```  
  

No we have examined almost all basic data operations on the CRM data using late-bounding style: RetrieveMultiple, Retrieve, Update, Delete, and Create new record.

  
  

**Generating Client Types for Early Binding**

  
  

Now we will use a different style than the one we used above. We will use the SDK tool **crmsvcutil.exe** to generate the typed classes for our CRM entities bsed on the metadata service of our CRM organization. These generated typed classes will inherit from the Entity class we worked with earlier in this post. Now follow the following steps to generate your typed classes:

  
  

  
2.  Open the project included in the SDK at %SDK%\\tools\\deviceregistration folder and build it.
  
  
5.  Open the command prompt cmd.exe and change directories to %SDK%\\tools\\deviceregistration\\bin\\Debug and run the command **DeviceRegistration.exe /operation:Register** This will generate a Device ID and Device Password for you (similar to the ones created by deviceidmanager.cs class).
  
  
8.  Copy the Deviceid and Device Password to a notepad. (if you are not familiar with cmd, right click the inside the window and click highlight, then highlight the desired text, then right click the cmd window title bar and click Edit>> copy.)
  
  
11.  In the command window, change the directories to %SDK%\\bin and create a command like the following:
  

  
  

crmsvcutil.exe /url:<CRM Online Organization service URL> /out:<Output file name> /servicecontextName:<Organization name> /username:<LiveID> /password:<LiveIDPassword>  
  
  
/deviceid:<Deviceid> /devicepassword:<DevicePassword> /namespace:<Namespace>

  
  

<CRM Online Organization service URL> will be like https://xrmdemo5.api.crm.dynamics.com/XRMServices/2011/Organization.svc? . You can find your URL by going to Settings >> Customizations >> Developer Resources, your URL will be there.

  
  

<Output file name> is the file name of the generated code (like GeneratedEntities.cs)

  
  

<Organization name> is your organization name.

  
  

<LiveID>, <LiveIDPassword> are your live credentials used for this organization.

  
  

<Deviceid>, <DevicePassword> are provided from step 3.

  
  

<Namespace> is the name space of the generated classes (may be YourCompanyname.YourOrganizationName)

  
  

the complete command may look like

  
  

crmsvcutil.exe /url:[https://xrmdemo5.api.crm.dynamics.com/XRMServices/2011/Organization.svc](https://xrmdemo5.api.crm.dynamics.com/XRMServices/2011/Organization.svc) /out:GeneratedEntities.cs /servicecontextName:xrmdemo5 /username:ebeid\_soliman@hotmail.com /password:mypassword  
  
/deviceid:11denl276oo3fgxbakccnnq2x4 /devicepassword:bH.iaG?c3rRi-\`L,nKC0S4^^ /namespace:xRMDemo.Entities

  
  

Now we created our early bound entity classes. Let’s modify our application to use the early-bound entity classes that we generated.

  
  

**Step 1: Add the generated types to the project**

  
  

Right click on the project in the solution explorer and click Add existing, browse to %CRMSDK%\\bin and add your generated file (its GeneratedEntities.cs in my above command).

  
  

**Step 2: Enable proxy types**

  
  

In order to use the generated types when dealing with the organization service, you have to add the _ProxyTypesBehavior_ to the endpoint _Behaviors_ collection. This instructs the OrganizationServiceProxy to look in the assembly for classes with certain attributes to use. The generated classes are already attributed with these attributes. Simply, this makes all interactions with the organization service to be done using the generated typed classes for each entity instead of the generic Entity class we used earlier.

  
  

Open the frmMain.cs, locate btnConnect\_Click event handler and add the following line of code after the last section line that creates the new instance of our OrganizationServiceProxy.

  
  
```
OrgService.ServiceConfiguration.CurrentServiceEndpoint.Behaviors.Add(new ProxyTypesBehavior());
```  
  

**Method** : **RetrieveMultiple**

  
  

It’s the same before. Now, let's modify the accounts combobox filling section to use the generated Account class instead of the Item class (you can get ride of it) that we created earlier. Modify the last section in btnConnect\_Click event handler to look like the following.

  
  
```
List accounts = new List();  
            comboAccounts.ValueMember = "accountid";  
            comboAccounts.DisplayMember = "name";  
            for (int i = 0; i < accountList.Entities.Count; i++)  
            {  
                accounts.Add((Account)accountList\[i\]);  
            }  
            comboAccounts.DataSource = accounts;
```  
  

**Method : Retrieve**

  
  

It almost the same, except we will use Account class and its properties instead of the Entity class and its attributes. Modify the comboAccounts\_SelectedIndexChanged event handler to look like:

  
  
```
ColumnSet cs2 = new ColumnSet(new string\[\] {"address1\_city","address1\_line1","address1\_stateorprovince",  
                "name","industrycode"});  
            try  
            {  
                Account account = (Account)OrgService.Retrieve("account", new Guid(comboAccounts.SelectedValue.ToString()), cs2);  
                txtName.Text = account.Name;  
                txtCity.Text = account.Address1\_City;  
                txtAddress.Text = account.Address1\_Line1;  
                txtState.Text = account.Address1\_StateOrProvince;  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show("An error happened: " + ex.Message);  
            }
```  
  

Delete method is solely done by the organization service, so it didn't change due the style we use.

  
  

**Method : Create**

  
  

It almost the same, except we will use Account class and its properties instead of the Entity class and its attributes. Modify the btnSaveNew\_Click event handler to look like:

  
  
```
try  
            {  
                Account account = new Account();  
                account.Name = txtName.Text;  
                account.Address1\_Line1 = txtAddress.Text;  
                account.Address1\_City = txtCity.Text;  
                account.Address1\_StateOrProvince = txtState.Text;  
                OrgService.Create(account);  
                MessageBox.Show("Account created successfully");  
            }  
            catch (Exception ex)  
            {  
                MessageBox.Show("An error occurred : " + ex.Message);  
            }
```  
  

This post is one of multiple posts to come under the same topic, Microsoft Dynamics CRM 2011 for Developers. Basicly we will deal with Dynamics CRM from the developer point of view. In this post we have tried to cover the basics of accessing Microsoft Dynamics CRM data using WCF. We tried the basic data operations: retrieve multiple records, retrieve one record, update, delete, and insert. We tried to cover both early-bounding and late-bounding approaches in our implementations.