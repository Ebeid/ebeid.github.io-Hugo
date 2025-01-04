--- 
title: "JSON–yet another tutorial :)"
date: '2011-12-01T17:43:00.002-06:00' 
tags: 
    - JSON 
modified_time: '2011-12-01T17:49:31.559-06:00' 
thumbnail: http://lh4.ggpht.com/-3m9QJruQuvA/TtgREUxCsDI/AAAAAAAAALI/5WZl5t\_qBmA/s72-c/JSON\_Demo11\_thumb%25255B1%25255D.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-251974912800519055
blogger_orig_url: http://ebeid-soliman.blogspot.com/2011/12/jsonyet-another-tutorial.html
---

#### What is JSON?

**[JSON](http://json.org/)** (or **J**ava**S**cript **O**bject
**N**otation) is a highly portable data interchange format. While its
structure is recognized natively by Javascript (as it *is* Javascript),
its formatting conventions are easily recognized by other C-like
languages.

JSON is built on two structures:

-   A collection of name/value pairs. In various languages, this is
    realized as an object, record, struct, dictionary, hash table, keyed
    list, or associative array. Example:

<!-- -->

    var jason = {
     "age" : "28",
     "hometown" : "Cairo, Egypt",
     "gender" : "male"
     };

> The object created in the example could be accessed like any other
> object.

-   An ordered list of values. In most languages, this is realized as an
    array, vector, list, or sequence. Example,

<!-- -->

    var family = [{
     "name" : "Jason",
     "age" : "24",
     "gender" : "male"
     },
     {
     "name" : "Kyle",
     "age" : "21",
     "gender" : "male"
     }];

> This array could be accessed like any array of objects.

Since JSON and XML are both used for data exchange, you may find
yourself in the middle of deciding which format to use.

##### Reasons to choose JSON over XML

1.  JSON is easier to read than XML (especially of large amounts of
    data)
2.  JSON requires less tags than XML – XML items must be wrapped in open
    and close tags whereas JSON you just name the tag once
3.  Because JSON is transportation-independent, you can just bypass the
    XMLHttpRequest object for getting your data.
4.  JavaScript is not just data – you can also put methods and all sorts
    of goodies in JSON format.
5.  JSON is better at helping procedural decisions in your JavaScript
    based on objects and their values (or methods).
6.  You can get JSON data from anywhere, not just your own domain.

##### Reasons to choose XML over JSON

1.  Easy to take XML and apply XSLT to make XHTML.
2.  XML is supported by many more desktop applications than JSON.
3.  XML can put JSON in it on the way back to the client.
4.  AJAX includes XML in it and not JSON.

#### .Net Support for JSON

#### <span class="Apple-style-span" style="font-weight: normal; ">.Net framework provides System.Web.Script.Serialization.JavaScriptSerializer to serialize and deserialize objects. Here is a simple example:</span>

    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Web;
    using System.Web.UI;
    using System.Web.UI.WebControls;
    namespace JSON_Demo1
    {
      public partial class Page1 : System.Web.UI.Page
      {
          protected void Page_Load(object sender, EventArgs e)
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

When you run the above application, you will see the JSON array on the
response like so:

[<img src="http://lh4.ggpht.com/-3m9QJruQuvA/TtgREUxCsDI/AAAAAAAAALI/5WZl5t_qBmA/JSON_Demo11_thumb%25255B1%25255D.jpg?imgmax=800" title="JSON_Demo11" width="496" height="371" alt="JSON_Demo11" />](http://lh3.ggpht.com/-YyboQaEuXN0/TtgREFLqnwI/AAAAAAAAALA/UZBtgfZSlP0/s1600-h/JSON_Demo11%25255B3%%0A25255D.jpg)

Now let’s change this example a little bit so we can make Ajax call to
get the JSON data and parse it using javaScript. Change the code-behind
to look like:

    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Web;
    using System.Web.UI;
    using System.Web.UI.WebControls;
    using System.Web.Services;

    namespace JSON_Demo1
    {
      public partial class Page1 : System.Web.UI.Page
      {
          protected void Page_Load(object sender, EventArgs e)
          {
              Response.Write(GetJSONData());
          }

          [WebMethod()]
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

now change the .aspx page to look like:

    <%@ Page Language="C#" AutoEventWireup="true" CodeBehind="Page1.aspx.cs" Inherits="JSON_Demo1.Page1" %>

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml">
    <head runat="server">
      <title></title>
      <script src="http://ajax.googleapis.com/ajax/libs/jquery/1.7.1/jquery.min.js" type="text/javascript"></script>
      <script type="text/javascript">
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
              var table = '<table> <thead> <tr> <th>Name</th> <th>ID</th> <th>Age</th> </thead> <tbody>';
              var myJSONObject = eval( msg );
              for (var i = 0; i < 3; i++) {              
                  var row = '<tr>';
                  row += '<td>' + myJSONObject[i].Name + '</td>';
                  row += '<td>' + myJSONO
    bject[i].ID + '</td>';
                  row += '<td>' + myJSONObject[i].Age + '</td>';
                  row += '</tr>';
                  table += row;
              }
              table += '</tbody></table>';
              $('#Container').html(table);
          }
          </script>
    </head>
    <body>
      <div id="Container">
      </div>
    </body>
    </html>

  
  

Now let’s run the application and see the output:

  
  

[<img src="http://lh6.ggpht.com/-OeGpH-Lhj9Y/TtgRFAHduiI/AAAAAAAAALY/r8BlbXR5Atw/JSON_Demo12_thumb%25255B2%25255D.jpg?imgmax=800" title="JSON_Demo12" width="410" height="427" alt="JSON_Demo12" />](http://lh3.ggpht.com/-BV1Tl-JzV38/TtgRE5nPvJI/AAAAAAAAALQ/U494e_qrJeU/s1600-h/JSON_Demo12%25255B4%25255D.jpg)

In the previous example, we created a WebMethod, then call it from
jQuery and pass the output of it to JavaScript method
**BuildTable(msg)**. This method convert the string msg into a JSON
array of objects and then loop on that array to build the shown simple
data table. We also rendered the JSON data to the browser directly from
server-side code, just to show the original data and how it transformed
using JSON.

In this post we gave a brief background about JSON, when use it and when
use XML to send data, how .Net provides native serializer for JSON, and
how to deserialize it using JavaScript. We may look into more advanced
topics regarding JSON in future posts.

Good Luck
