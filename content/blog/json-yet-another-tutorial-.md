---
title: 'JSON–yet another tutorial :)'
date: 2011-12-01T17:43:00.002-06:00
draft: false
url: /2011/12/jsonyet-another-tutorial.html
tags: 
- JSON
---

#### What is JSON?

**[JSON](http://json.org/)** (or **J**ava**S**cript **O**bject **N**otation) is a highly portable data interchange format. While its structure is recognized natively by Javascript (as it _is_ Javascript), its formatting conventions are easily recognized by other C-like languages.

JSON is built on two structures:

*   A collection of name/value pairs. In various languages, this is realized as an object, record, struct, dictionary, hash table, keyed list, or associative array. Example:

```
var jason = {  
 "age" : "28",  
 "hometown" : "Cairo, Egypt",  
 "gender" : "male"  
 };
```

> The object created in the example could be accessed like any other object.

*   An ordered list of values. In most languages, this is realized as an array, vector, list, or sequence. Example,

```
var family = \[{  
 "name" : "Jason",  
 "age" : "24",  
 "gender" : "male"  
 },  
 {  
 "name" : "Kyle",  
 "age" : "21",  
 "gender" : "male"  
 }\];
```

> This array could be accessed like any array of objects.

Since JSON and XML are both used for data exchange, you may find yourself in the middle of deciding which format to use.

##### Reasons to choose JSON over XML

1.  JSON is easier to read than XML (especially of large amounts of data)
2.  JSON requires less tags than XML – XML items must be wrapped in open and close tags whereas JSON you just name the tag once
3.  Because JSON is transportation-independent, you can just bypass the XMLHttpRequest object for getting your data.
4.  JavaScript is not just data – you can also put methods and all sorts of goodies in JSON format.
5.  JSON is better at helping procedural decisions in your JavaScript based on objects and their values (or methods).
6.  You can get JSON data from anywhere, not just your own domain.

##### Reasons to choose XML over JSON

1.  Easy to take XML and apply XSLT to make XHTML.
2.  XML is supported by many more desktop applications than JSON.
3.  XML can put JSON in it on the way back to the client.
4.  AJAX includes XML in it and not JSON.

#### .Net Support for JSON

#### .Net framework provides System.Web.Script.Serialization.JavaScriptSerializer to serialize and deserialize objects. Here is a simple example:

```
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Web;  
using System.Web.UI;  
using System.Web.UI.WebControls;  
namespace JSON\_Demo1  
{  
  public partial class Page1 : System.Web.UI.Page  
  {  
      protected void Page\_Load(object sender, EventArgs e)  
      {  
          Employee oEmployee1 = new Employee { Name = "Emp1", ID = "11", Age = "30" };  
          Employee oEmployee2 = new Employee { Name = "Emp2", ID = "22", Age = "31" };  
          Employee oEmployee3 = new Employee { Name = "Emp3", ID = "33", Age = "20" };  
          List oList = new List() { oEmployee1, oEmployee2, oEmployee3 };  
          System.Web.Script.Serialization.JavaScriptSerializer oSerializer = new System.Web.Script.Serialization.JavaScriptSerializer();  
          string sJSON = oSerializer.Serialize(oList);  
          Response.Write(sJSON);  
      }  
  }  
  public class Employee  
  {  
      public string Name { get; set; }  
      public string Age { get; set; }  
      public string ID { get; set; }  
  }  
}
```

When you run the above application, you will see the JSON array on the response like so:

[![JSON_Demo11](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgCSyn02MusBDg9Cq77GiAwNod_maxDKv9-MFCm7Zzc6BX5y2Papi8NoXL8m-GOsl_CHoVSD11RxKDXOwApvq2ZZtFl2qQJ5Y60QNM8PhsVs16isGoyIcghMAN0_bU4Gu5H0bPvj-WCdQ/?imgmax=800 "JSON_Demo11")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgh00G-5bQa7QUQvBbWx6BYspBgiFy_GDa6tEkx_6grfuhHTWOLDl4qSXa199SXJwvOZtWcij1BXB5Lmmi7pF7pt1JVA8uT-ebDy6cT_WeskibeSB_vxEH5_E_aJLxDSrZfG-OLTx3f2g/s1600-h/JSON_Demo11%25255B3%25255D.jpg)

Now let’s change this example a little bit so we can make Ajax call to get the JSON data and parse it using javaScript. Change the code-behind to look like:

```
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Web;  
using System.Web.UI;  
using System.Web.UI.WebControls;  
using System.Web.Services;  
  
namespace JSON\_Demo1  
{  
  public partial class Page1 : System.Web.UI.Page  
  {  
      protected void Page\_Load(object sender, EventArgs e)  
      {  
          Response.Write(GetJSONData());  
      }  
  
      \[WebMethod()\]  
      public static string GetJSONData()  
      {  
          Employee oEmployee1 = new Employee { Name = "Emp1", ID = "11", Age = "30" };  
          Employee oEmployee2 = new Employee { Name = "Emp2", ID = "22", Age = "31" };  
          Employee oEmployee3 = new Employee { Name = "Emp3", ID = "33", Age = "20" };  
          List oList = new List() { oEmployee1, oEmployee2, oEmployee3 };  
          System.Web.Script.Serialization.JavaScriptSerializer oSerializer = new System.Web.Script.Serialization.JavaScriptSerializer();  
          return oSerializer.Serialize(oList);  
      }  
  }  
  public class Employee  
  {  
      public string Name { get; set; }  
      public string Age { get; set; }  
      public string ID { get; set; }  
  }  
  
}
```

now change the .aspx page to look like:

```
<%@ Page Language="C#" AutoEventWireup="true" CodeBehind="Page1.aspx.cs" Inherits="JSON\_Demo1.Page1" %>  
  
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">  
<html xmlns\="http://www.w3.org/1999/xhtml"\>  
<head runat\="server"\>  
  <title\></title\>  
  <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js" type="text/javascript"\></script\>  
  <script type="text/javascript"\>  
      $(document).ready(function () {  
          $.ajax({  
              type: "POST",  
              url: "Page1.aspx/GetJSONData",  
              contentType: "application/json; charset=utf-8",  
              dataType: "json",  
              success: function (msg) {  
                  BuildTable(msg.d);  
                  }  
          });  
      });  
      
      function BuildTable(msg) {  
          var table \= '<table> <thead> <tr> <th>Name</th> <th>ID</th> <th>Age</th> </thead> <tbody>';  
          var myJSONObject \= eval( msg );  
          for (var i \= 0; i < 3; i++) {                
              var row \= '<tr>';  
              row += '<td>' + myJSONObject\[i\].Name + '</td>';  
              row += '<td>' + myJSONObject\[i\].ID + '</td>';  
              row += '<td>' + myJSONObject\[i\].Age + '</td>';  
              row += '</tr>';  
              table += row;  
          }  
          table += '</tbody></table>';  
          $('#Container').html(table);  
      }  
      </script\>  
</head\>  
<body\>  
  <div  id\="Container"\>  
  </div\>  
</body\>  
</html\>
```  
  

Now let’s run the application and see the output:

  
  

[![JSON_Demo12](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj45wOIhXi1Jf7RtFqht4pZgR17hAYPz_9sCxc-6HC6pHPkvmTYJv2QfTqZUEIdG-TALp86m-xWGWXBM298u6Z2eKkgGRiBBDL1hurDl_qWc6yhH3afrWgTrtYgofiPB14EM0JWANOkHw/?imgmax=800 "JSON_Demo12")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEioEyEdUkiEzD_SfM0fV8uODvDCmrNnkhCdKVTIuiV5bKKDCICCJxpuHoRlABhi-YKQkHKV0wD4ZQexo82eRj4X91HpOVv7iPYuFEvBzz1TN80c1gPXn53nXk4XuiKb_T7UHaAYgFHx9A/s1600-h/JSON_Demo12%25255B4%25255D.jpg)

In the previous example, we created a WebMethod, then call it from jQuery and pass the output of it to JavaScript method **BuildTable(msg)**. This method convert the string msg into a JSON array of objects and then loop on that array to build the shown simple data table. We also rendered the JSON data to the browser directly from server-side code, just to show the original data and how it transformed using JSON.

In this post we gave a brief background about JSON, when use it and when use XML to send data, how .Net provides native serializer for JSON, and how to deserialize it using JavaScript. We may look into more advanced topics regarding JSON in future posts.

Good Luck