---
title: 'SQL Server Dedicated Administrator Connection'
date: 2010-04-11T05:08:00.001-05:00
draft: false
url: /2010/04/sql-server-dedicated-administrator.html
---

Microsoft SQL Server provides a dedicated administrator connection (DAC) which allows an administrator to access a running instance of SQL Server Database Engine to troubleshoot problems on the server—even when the server is unresponsive to other client connections. The DAC is available through the **sqlcmd** utility and SQL Server Management Studio. The connection is only allowed from a client running on the server. No network connections are permitted.

To use SQL Server Management Studio with the DAC, connect to an instance of the SQL Server Database Engine with Query Editor by typing **ADMIN:** before the server name. Object Explorer cannot connect using the DAC.

To connect to a server using the DAC

1.  In SQL Server Management Studio, with no other DACs open, on the toolbar, click **Database Engine Query**.
    
2.  In the **Connect to Database Engine** dialog box, in the **Server name** box, type **ADMIN:** followed by the name of the server instance. For example, to connect to a server instance named **ACCT\\PAYABLE**, type **ADMIN:****ACCT\\PAYABLE**.
    
3.  Complete the **Authentication** section, providing credentials for a member of the **sysadmin** group, and then click **Connect**.
    
    The connection is made.
    
    If the DAC is already in use, the connection will fail with an error indicating it cannot connect.
    

If you are trying to that and got the following error:

> Dedicated administrator connections are not supported. (ObjectExplorer)

It means that you are trying to connect Object Explorer using the DAC. Object Explorer cannot connect using the DAC; only Query Window can. That means that you cannot press the New Query button; you have to use the Database Engine Query button.

  
[![](http://photos1.blogger.com/blogger2/7616/913/400/pic2440.2.png)](http://photos1.blogger.com/blogger2/7616/913/1600/pic2440.2.png)