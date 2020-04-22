--- 
title: "Getting Started with Apache Cassandra" 
date: '2013-07-09T17:27:00.000-05:00' 
tags: 
    - Apache Cassandra 
    - Cassandra 
    - NoSQL 
modified_time: '2013-07-09T17:27:00.396-05:00' 
thumbnail: http://lh6.ggpht.com/-p2bQ1oDMq2o/UdSevOL1w6I/AAAAAAAABp8/QJ53e4i7kDc/s72-c/Cassandra\_DataModel\_CheatSheet.pdf%252520-%252520Adobe%252520Reader\_2013-07-03\_15-59-51\_thumb.png?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-1260260134339026870
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/07/getting-started-with-apache-cassandra.html
---

Apache [Cassandra](http://cassandra.apache.org/) is “an open source,
distributed, decentralized, elastically scalable, highly available,
fault-tolerant, tuneably consistent, column-oriented database that bases
its distribution design on Amazon’s
[Dynamo](http://www.read.seas.harvard.edu/~kohler/class/cs239-w08/decandia07dynamo.pdf "Dynamo: Amazon’s Highly Available Key-value Store")
and its data model on Google’s
[Bigtable](http://static.googleusercontent.com/external_content/untrusted_dlcp/research.google.com/en/us/archive/bigtable-osdi06.pdf "Bigtable: A Distributed Storage System for Structured Data")”
(source: “Cassandra: The Definitive Guide,” O’Reilly Media, 2010, p.
14).

Cassandra is built to store lots of data across a variety of machines
arranged in a ring, in other words scaling horizontally, rather than
vertically.

#### Data Model

**Cassandra is based on a key-value model** and it is organized
according to the following concepts:

-   **Column** is a key-value pair.

[<img src="http://lh6.ggpht.com/-p2bQ1oDMq2o/UdSevOL1w6I/AAAAAAAABp8/QJ53e4i7kDc/Cassandra_DataModel_CheatSheet.pdf%252520-%252520Adobe%252520Reader_2013-07-03_15-59-51_thumb.png?imgmax=800" title="Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_15-59-51" width="104" height="159" alt="Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_15-59-51" />](http://lh4.ggpht.com/-Nm7Y_Z0Xj7c/UdSeu3ZA_FI/AAAAAAAABp0/CKu7ogaPdQk/s1600-h/Cassandra_DataModel_CheatSheet.pdf%252520-%252520Adobe%252520Reader_2013-07-03_15-59-51%25255B2%25255D.png)

-   **Column Family** is a set of key-value pairs (columns in
    Cassandra’s terminology). They are sorted by their keys. Families
    are referenced and sorted by row keys.

[<img src="http://lh3.ggpht.com/-pl2jIWhLwSw/UdSev4PPO8I/AAAAAAAABqM/Y_p3gGlpaHI/Cassandra_DataModel_CheatSheet.pdf%252520-%252520Adobe%252520Reader_2013-07-03_16-03-39_thumb%25255B3%25255D.png?imgmax=800" title="Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_16-03-39" width="343" height="192" alt="Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_16-03-39" />](http://lh5.ggpht.com/-KQ-fcGadYec/UdSevuHSxFI/AAAAAAAABqE/NZFQ8j55DaY/s1600-h/Cassandra_DataModel_CheatSheet.pdf%252520-%252520Adobe%252520Reader_2013-07-03_16-03-39%25255B5%25255D.png)

-   **Super Column** the value of a key-value pair can be a sequence of
    key-value pairs as well. In this case, the outer column would be
    called *super column*.

[<img src="http://lh3.ggpht.com/-8li2tYsM-3w/UdSeww5ryXI/AAAAAAAABqc/vhD24M0ZTDA/Cassandra_DataModel_CheatSheet.pdf%252520-%252520Adobe%252520Reader_2013-07-03_16-39-29_thumb.png?imgmax=800" title="Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_16-39-29" width="244" height="191" alt="Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_16-39-29" />](http://lh3.ggpht.com/-e67Sbx-MBZI/UdSewXapJpI/AAAAAAAABqU/5Yhu4wezOCw/s1600-h/Cassandra_DataModel_CheatSheet.pdf%252520-%252520Adobe%252520Reader_2013-07-03_16-39-29%25255B2%25255D.png)

-   Columns and Super Columns can equally be used within Column Families

[<img src="http://lh3.ggpht.com/-KiIm5zkI6Vs/UdSexZH1W1I/AAAAAAAABqs/eORrUHPpta4/Cassandra_DataModel_CheatSheet.pdf%252520-%252520Adobe%252520Reader_2013-07-03_16-44-41_thumb%25255B1%25255D.png?imgmax=800" title="Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_16-44-41" width="563" height="207" alt="Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_16-44-41" />](http://lh6.ggpht.com/-cX1ZLQgqBJ8/UdSexIyVfQI/A%0AAAAAAAABqg/_mOTEsywGqo/s1600-h/Cassandra_DataModel_CheatSheet.pdf%252520-%252520Adobe%252520Reader_2013-07-03_16-44-41%25255B3%25255D.png)

-   Columns or Super Columns are stored ordered by names within their
    Column Families

For a better understanding of Cassandra’s data model, refer to this
[article](http://maxgrinev.com/2010/07/09/a-quick-introduction-to-the-cassandra-data-model/ "A Quick Introduction to the Cassandra Data Model")
by [Maxim Grinev](https://twitter.com/maxgrinev).

####  

#### Installation

1.  Download the latest Cassandra version from
    [here](http://cassandra.apache.org/download/ "Cassandra Downloads Page")
    (I got version 1.2.6).
2.  Extract the archive (I extracted it to *C:\\apache-cassandra-1.2.6*
    )
3.  If you don’t have Java installed on your machine, go and get it
    installed.
4.  Add environment variables
    1.  Reight-click the my Computer icon on your desktop or start menu.
    2.  Click the Advanced tab (or the Advanced System Settings)
    3.  Under System Variables, click New (adjust for your own
        directories)
        1.  Variable Name :  CASSANDRA\_HOME
        2.  Variable Value : C:\\apache-cassandra-1.2.6
        3.  click OK
    4.  Under System Variables, click New (adjust for your own
        directories)
        1.  Variable Name : JAVA\_HOME
        2.  Variable Value : C:\\Program Files\\Java\\jre7
        3.  click OK
5.  Now, open command window and navigate to your bin directory inside
    Cassandra directory (C:\\apache-cassandra-1.2.6\\bin in my case).
6.  Launch Cassandra by executing the comand ***cassandra –f*** (the
    “-f” causes it to run in the foreground). You will see lots of
    messages coming out. If everything goes fine, it will end up with
    something like this:

[<img src="http://lh4.ggpht.com/-YQZnFRlSZjw/UdRyUioBdnI/AAAAAAAABpQ/mIptHAXzgxc/CWindowssystem32cmd.exe%252520-%252520cassandra%252520%252520-f_2013-07-03_11-18-19_thumb%25255B2%25255D.png?imgmax=800" title="CWindowssystem32cmd.exe - cassandra  -f_2013-07-03_11-18-19" width="568" height="101" alt="CWindowssystem32cmd.exe - cassandra -f_2013-07-03_11-18-19" />](http://lh3.ggpht.com/-UnPiaJX8RoY/UdRyUOwWQBI/AAAAAAAABpM/5XG9a3FWj4k/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra%252520%252520-f_2013-07-03_11-18-19%25255B4%25255D.png)

Now we have a running Cassandra server is expecting incoming connections
on port 9160.

Once Cassandra is up and running on your machine, we can connect to the
running instance using the Cassandra command-line interface, launched by
running “cassandra-cli.bat”, from the Cassandra “bin” directory.

[<img src="http://lh6.ggpht.com/-uGYNzQQB6kQ/UdRyVQqQD8I/AAAAAAAABpk/eiGHMIIklxE/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-03_12-16-36_thumb%25255B1%25255D.png?imgmax=800" title="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-03_12-16-36" width="307" height="97" alt="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-03_12-16-36" />](http://lh6.ggpht.com/-vurPz2Ai75k/UdRyUwqKVDI/AAAAAAAABpc/q_TMwpoNSpE/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-03_12-16-36%25255B3%25255D.png)

#### Commads

-   **show api version;** to show the current api version.
-   **describe cluster;** to show a description of the current cluster.

[<img src="http://lh3.ggpht.com/-USxeqWKrlGY/UddSpukxJ2I/AAAAAAAABrE/5djREoFMJTI/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_12-59-46_thumb%25255B1%25255D.png?imgmax=800" title="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_12-59-46" width="573" height="156" alt="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_12-59-46" />](http://lh6.ggpht.com/-E6BbthLOQG0/UddSpGviRLI/AAAAAAAABq8/RJxQT9gGMiM/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_12-59-46%25255B3%25255D.png)

-   **create keyspace** *TestKS;* to create a keyspace and it have to be
    a unique name.
-   **use** *TestKS;* to switch to keyspace TestKS.
-   **create column family** *TestCF;* to create a column family TestCF
    within the current keyspace.
    -   No other schema definition is required, the column family is a
        collection of name/value pairs.
-   `set TestCF[ascii('TestKey')][ascii('column1')]=ascii('TestValue'); `to
    insert the TestKey/TestValue key/value pair into the column named
    column1 within the column family TestCF. You can use the **with ttl
    =** *x* setting at the end of the set command to make the column
    self-delete aft *x* seconds of the insertion time.
    -   by default Cassandra treats data as byte arrays but you can
        convert to other types such as **Long**, **int**, **integer**,….
        Also **timeuuid()** generates new UUID. For full information
        about set command: **type help set;**
-   `get TestCF[ascii("TestKey")]; to retrieve the value stored in the key TestKey within the column family TestCF`

[<img src="http://lh6.ggpht.com/-0FwfslqY6sA/UddSqaW5V7I/AAAAAAAABrQ/BBYndnX3nMw/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_11-15-32_thumb%25255B1%25255D.png?imgmax=800" title="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_11-15-32" width="572" height="170" alt="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_11-15-32" />](http://lh3.ggpht.com/-Hn5eUsyN27I/UddSp6PwwrI/AAAAAAAABrM/GULnZQPMVF0/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_11-15-32%25255B3%25255D.png)

-   **del** *TestCF\[ascii(‘TestKey’)\]\[ascii(‘column2’)\];* rows and
    columns can be deleted by specifying the row key and/or the column
    name  
    with the del (delete) command.

[<img src="http://lh6.ggpht.com/-8Dm_ba0NsI4/UddSrNQyJoI/AAAAAAAABrk/PWgGYTStm1s/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_15-29-44_thumb%25255B1%25255D.png?imgmax=800" title="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_15-29-44" width="577" height="126" alt="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_15-29-44" />](http://lh4.ggpht.com/--hQRoa3rknY/UddSqlWO_gI/AAAAAAAABrY/FYwX-Qf8PIY/s160%0A0-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_15-29-44%25255B3%25255D.png)

-   **list** *TestCF;* list the data inside a column family

[<img src="http://lh4.ggpht.com/-yLbSOiAhAao/UddSru2O0JI/AAAAAAAABrw/cnqsNsjdwbI/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_16-05-31_thumb%25255B1%25255D.png?imgmax=800" title="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_16-05-31" width="585" height="340" alt="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_16-05-31" />](http://lh3.ggpht.com/-pShPLfMYEdk/UddSrTgOB_I/AAAAAAAABro/wvTp08iV5V8/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_16-05-31%25255B3%25255D.png)

-   **drop column family** *TestCF;* removes a column family.
-   **drop** **keyspace** *TestKS;* removes a key space.

[<img src="http://lh6.ggpht.com/-cltQ_sicXSk/UddSsXgdnLI/AAAAAAAABsE/w9dVZEAlQC4/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_16-25-05_thumb%25255B1%25255D.png?imgmax=800" title="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_16-25-05" width="433" height="90" alt="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_16-25-05" />](http://lh4.ggpht.com/-02x8jN7oqZU/UddSr2JdHKI/AAAAAAAABr4/zfbolqgsGZ8/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_16-25-05%25255B3%25255D.png)

==&gt; You can insert to super columns much like inserting to normal
columns. They can be read with get, written with set, and deleted with
del. The super column version of these commands uses an extra \['xxx'\]
to represent the extra sub-index level.

[<img src="http://lh3.ggpht.com/-scP9SmjNXJU/UddStWKip_I/AAAAAAAABsQ/BoDnyOvIcbY/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_17-07-44_thumb%25255B3%25255D.png?imgmax=800" title="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_17-07-44" width="783" height="367" alt="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_17-07-44" />](http://lh3.ggpht.com/-fHySsJpN8OU/UddSs3kUrNI/AAAAAAAABsM/zG7er1ADQJA/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_17-07-44%25255B5%25255D.png)

-   **assume** *TestCF* **comparator as ascii;** it decodes and helps
    display results of get and list requests inside the command-line
    interface. It can be used in the same way to set the **validator**
    and **keys**. By default, columns with no metadata are displayed in
    a hex format. This is done because row keys, column names, and
    column values are byte arrays. After using assume the column and
    value will be displayed rather than the hex code.

[<img src="http://lh4.ggpht.com/-ldlwwZisDns/UddStwvpxpI/AAAAAAAABsg/be4L7iHTN_8/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_17-29-07_thumb%25255B2%25255D.png?imgmax=800" title="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_17-29-07" width="657" height="317" alt="CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_17-29-07" />](http://lh6.ggpht.com/-5-u5Iae2Wr8/UddStkmE9oI/AAAAAAAABsY/YZOLw550oUo/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_17-29-07%25255B4%25255D.png)

-   **Type Enforcement** : Cassandra is designed to store and retrieve
    simple byte arrays but it also have support for [built-in
    types](http://www.datastax.com/docs/1.1/references/cql/cql_data_types "CQL Data Types").
    When creating or updating a column family, the user can supply
    column metadata that instructs the CLI Cassandra client on how to
    display data and help the server enforce types during insertion
    operations.  
    **create column family User with comparator = UTF8Type;  
    update column family User with  
            column\_metadata =  
            \[  
            {column\_name: first, validation\_class: AsciiType},  
            {column\_name: last, validation\_class: AsciiType},  
            {column\_name: age, validation\_class: IntegerType,
    index\_type: KEYS}  
            \];**
-   **Querying data** :

**set User\[ascii('jsmith')\]\[ascii('first')\] = ascii('John');  
set User\[ascii('jsmith')\]\[ascii('last')\] = ascii('Smith');  
set User\[ascii('jsmith')\]\[ascii('age')\] = '38';**

**get User where age = '38';**

-   **Update** is the same as set.

**set User\[ascii('jsmith')\]\[ascii('first')\] = ascii('Jack');**

-   **Quite** the client;

**quit;**

 

In this post we just touched the Cassandra’s iceberg. In later posts we
will dig more in it and how to write .net programs against it.
