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

![alt text](/img/0020.png "Logo Title Text 1")

-   **Column Family** is a set of key-value pairs (columns in
    Cassandra’s terminology). They are sorted by their keys. Families
    are referenced and sorted by row keys.

![alt text](/img/0021.png "Logo Title Text 1")

-   **Super Column** the value of a key-value pair can be a sequence of
    key-value pairs as well. In this case, the outer column would be
    called *super column*.

![alt text](/img/0022.png "Logo Title Text 1")

-   Columns and Super Columns can equally be used within Column Families

![alt text](/img/0023.png "Logo Title Text 1")

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

![alt text](/img/0024.png "Logo Title Text 1")

Now we have a running Cassandra server is expecting incoming connections
on port 9160.

Once Cassandra is up and running on your machine, we can connect to the
running instance using the Cassandra command-line interface, launched by
running “cassandra-cli.bat”, from the Cassandra “bin” directory.

![alt text](/img/0025.png "Logo Title Text 1")

#### Commads

-   **show api version;** to show the current api version.
-   **describe cluster;** to show a description of the current cluster.

![alt text](/img/0026.png "Logo Title Text 1")

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

![alt text](/img/0027.png "Logo Title Text 1")

-   **del** *TestCF\[ascii(‘TestKey’)\]\[ascii(‘column2’)\];* rows and
    columns can be deleted by specifying the row key and/or the column
    name  
    with the del (delete) command.

![alt text](/img/0028.png "Logo Title Text 1")

-   **list** *TestCF;* list the data inside a column family

![alt text](/img/0029.png "Logo Title Text 1")

-   **drop column family** *TestCF;* removes a column family.
-   **drop** **keyspace** *TestKS;* removes a key space.

![alt text](/img/0030.png "Logo Title Text 1")

==&gt; You can insert to super columns much like inserting to normal
columns. They can be read with get, written with set, and deleted with
del. The super column version of these commands uses an extra \['xxx'\]
to represent the extra sub-index level.

![alt text](/img/0031.png "Logo Title Text 1")

-   **assume** *TestCF* **comparator as ascii;** it decodes and helps
    display results of get and list requests inside the command-line
    interface. It can be used in the same way to set the **validator**
    and **keys**. By default, columns with no metadata are displayed in
    a hex format. This is done because row keys, column names, and
    column values are byte arrays. After using assume the column and
    value will be displayed rather than the hex code.

![alt text](/img/0032.png "Logo Title Text 1")


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
