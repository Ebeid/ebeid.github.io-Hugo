---
title: 'SQL Server Metadata'
date: 2010-04-11T11:44:00.001-05:00
draft: false
url: /2010/04/sql-server-metadata.html
tags: 
- SQL
---

Many times when you need to troubleshoot an SQL Server issue, you will need to collect metadata about the server, databases, and server resources in general. Here we will briefly review the mechanisms to collect these metadata.

### System Base Tables

SQL server maintains a set of tables that store information about all the objects, data types, constraints, configuration options, and resources available to SQL Server. These tables are called the _system base tables._

*   Some of these tables exist in _master_ database –> contain system-wide information.
*   Some exist in every database –> contain database specific information.

You can access these tables names only if you are logged in as a system administrator. You can access through:

*   Run sp\_help
*   Run```
    ```
    [use](http://search.microsoft.com/default.asp?so=RECCNT&siteid=us%2Fdev&p=1&nq=NEW&qu=use&IntlSearch=&boolean=PHRASE&ig=01&i=09&i=99) master;   
    
    ``````
    [select](http://search.microsoft.com/default.asp?so=RECCNT&siteid=us%2Fdev&p=1&nq=NEW&qu=select&IntlSearch=&boolean=PHRASE&ig=01&i=09&i=99) name [from](http://search.microsoft.com/default.asp?so=RECCNT&siteid=us%2Fdev&p=1&nq=NEW&qu=from&IntlSearch=&boolean=PHRASE&ig=01&i=09&i=99) sys.objects   
    
    ``````
    [where](http://search.microsoft.com/default.asp?so=RECCNT&siteid=us%2Fdev&p=1&nq=NEW&qu=where&IntlSearch=&boolean=PHRASE&ig=01&i=09&i=99) type\_desc = 'SYSTEM\_TABLE';  
    
    ```
    ```  
    
  

  
  

If you tried to select data from any of these system tables, you will got 208 error indicating that the object name is invalid. The only way to access these data is through [dedicated administrator connection (DAC)](http://ebeid-soliman.blogspot.com/2010/04/sql-server-dedicated-administrator.html "dedicated administrator connection (DAC)").

  
  

Keep in mind that these system base tables are used for internal purposes only within the database engine and are not intended for general use. They are subject to change and compatibility is not guaranteed.

  
  

### Compatibility Views

  
  

Although it is possible to see data in the system tables in versions of SQL Server before 2005, it wasn’t recommended. For compatibility, SQL server 2005 and 2008 provided a set of [compatibility views](http://msdn.microsoft.com/en-us/library/ms187376.aspx "Compatibility Views on MSDN") that allow access to a subset of the SQL server 2000 system tables. These views should be used for backward compatibility only; going forward, you should use catalog views.

  
  

### Catalog Views

  
  

SQL Server 2005 introduced a set of catalog views as a general interface to the persisted system metadata. All the catalog views are in the sys schema, and you must reference the schema name when access the objects like:

  
  
```
```
[select](http://search.microsoft.com/default.asp?so=RECCNT&siteid=us%2Fdev&p=1&nq=NEW&qu=select&IntlSearch=&boolean=PHRASE&ig=01&i=09&i=99) name [from](http://search.microsoft.com/default.asp?so=RECCNT&siteid=us%2Fdev&p=1&nq=NEW&qu=from&IntlSearch=&boolean=PHRASE&ig=01&i=09&i=99) sys.databases;
```
```  
  

For a complete list of catalog views categories, please consult [http://msdn.microsoft.com/en-us/library/ms174365.aspx.](http://msdn.microsoft.com/en-us/library/ms174365.aspx. "http://msdn.microsoft.com/en-us/library/ms174365.aspx")

  
  

### Information Schema Views

  
  

The information schema views comply with SQL-92 standard and all of it are in a schema called INFORMATION\_SCHEMA. If you need to write a portable application that access the metadata you should use these views. This compliance come with the price of limited provided information (it provide the standard defined information only). If you need metadata about non-standard features, use catalog views.

  
  

For a complete list of Information schema views and its closest map to catalog views, please consult [http://msdn.microsoft.com/en-us/library/ms186778.aspx](http://msdn.microsoft.com/en-us/library/ms186778.aspx "http://msdn.microsoft.com/en-us/library/ms186778.aspx")

  
  

### System Functions

  
  

Give us individual property values for many SQL Server instance, objects, databases. The values returned by system functions are scalar, so they can be used as values returned by _SELECT_ statements like:

  
  
```
```
[select](http://search.microsoft.com/default.asp?so=RECCNT&siteid=us%2Fdev&p=1&nq=NEW&qu=select&IntlSearch=&boolean=PHRASE&ig=01&i=09&i=99) DATABASEPROPERTYEX('msdb','Recovery');
```
```  
  

For a complete list of system functions and its types, review [http://msdn.microsoft.com/en-us/library/ms187786.aspx](http://msdn.microsoft.com/en-us/library/ms187786.aspx "http://msdn.microsoft.com/en-us/library/ms187786.aspx")

  
  

### System Stored Procedures

  
  

System Stored Procedures are the original metadata access tool but it had a drawback, basically you have to accept the data that it returns. Some of the procedures allow parameters but they are very limited. Catalog views are more enhanced and flexible in controlling what data appears.

  
  

I hope this brief post gives you an overall image about SQL Server metadata access mechanisms and which one to use according to your situation.