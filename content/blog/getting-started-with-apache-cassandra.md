---
title: 'Getting Started with Apache Cassandra'
date: 2013-07-09T17:27:00.000-05:00
draft: false
url: /2013/07/getting-started-with-apache-cassandra.html
tags: 
- Apache Cassandra
- Cassandra
- NoSQL
---

Apache [Cassandra](http://cassandra.apache.org/) is “an open source, distributed, decentralized, elastically scalable, highly available, fault-tolerant, tuneably consistent, column-oriented database that bases its distribution design on Amazon’s [Dynamo](http://www.read.seas.harvard.edu/~kohler/class/cs239-w08/decandia07dynamo.pdf "Dynamo: Amazon’s Highly Available Key-value Store") and its data model on Google’s [Bigtable](http://static.googleusercontent.com/external_content/untrusted_dlcp/research.google.com/en/us/archive/bigtable-osdi06.pdf "Bigtable: A Distributed Storage System for Structured Data")” (source: “Cassandra: The Definitive Guide,” O’Reilly Media, 2010, p. 14).

Cassandra is built to store lots of data across a variety of machines arranged in a ring, in other words scaling horizontally, rather than vertically.

#### Data Model

**Cassandra is based on a key-value model** and it is organized according to the following concepts:

*   **Column** is a key-value pair.

[![Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_15-59-51](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiRSp7Sc55ChGWklMt2D84EK5RPwAYDOQaWmpGdKfr88FboLoeNBx0pnC4Es3pVqQQumtObbk-mphtdOv51y6_VGqz1DO8n7Pn3W0kgIMLBPKGmluo2CafcnBy5MS8Ef_2E9HT4qG1LeQ/?imgmax=800 "Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_15-59-51")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEieuEmXEk_jQRd-uDAXqw4Zizz4z0Tuw65PluyAZlZYTSgLa9_FAoAbsZ1lQO2pJueJsDnOdpZMsy7Ri5uyTaBOGpNwJ_XZH1msUh9ber17GBo2wKXOrhkEEeHuvTsYV3YVYvtFi_OOLQ/s1600-h/Cassandra_DataModel_CheatSheet.pdf%252520-%252520Adobe%252520Reader_2013-07-03_15-59-51%25255B2%25255D.png)

*   **Column Family** is a set of key-value pairs (columns in Cassandra’s terminology). They are sorted by their keys. Families are referenced and sorted by row keys.

[![Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_16-03-39](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgG0vZ7gScgYK-7yKYb2ku8bvPvPrm4hL4MZKQ-QcUmP0ABrB-yuCZkWP9IrXrpuzGESGWHfI0kRSGzHiCpQFTje9zgDKTjhCAARr6SaCCuGe_AFTVEJqIs35rcTiH6lSyAVqXeXy_yxQ/?imgmax=800 "Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_16-03-39")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgFjDd8UKOLhd1nYvohZ6dyw9oLy1w8jGcMps-3aPjLjl5thMkuHFxDUaFw3350ID5KafhyTkrL6lHqmzQhthwW2YFB7cIifw_LRrP4Dxpl_Egdrek_uzLQcJRxc5UqqDHVIamdt5qjog/s1600-h/Cassandra_DataModel_CheatSheet.pdf%252520-%252520Adobe%252520Reader_2013-07-03_16-03-39%25255B5%25255D.png)

*   **Super Column** the value of a key-value pair can be a sequence of key-value pairs as well. In this case, the outer column would be called _super column_.

[![Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_16-39-29](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgZ0YmJmmeHGx184kC1NvLOBH9JUgfjSweyK1atdmTEG7RSI3rrkPauI6nqJ1macSKtVKwTDnaYhWLxkDp0gDISGsUpxvBrpBPLFLKp4wmC1TI3VKFuaGUb6QhsLw7yrHOoXJcheuXGiQ/?imgmax=800 "Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_16-39-29")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhOu37rIMIok0kaHfj00SP7HRJg0M4MCKy5tvD6Kdjrmwk2oBcFIiBr34_bsX5x5hI18mgsUmBpQbF_WEFbSx2JiptHos8geqIFp_IpI9RY2zMUz_LJ0A4JNox-1JBSeo0L1iyel7MkQw/s1600-h/Cassandra_DataModel_CheatSheet.pdf%252520-%252520Adobe%252520Reader_2013-07-03_16-39-29%25255B2%25255D.png)

*   Columns and Super Columns can equally be used within Column Families

[![Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_16-44-41](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjgWgMCGeNv6jJoYOw-FWn0JN4yS49zQuvp2v5cRFYvSYX1A5Ug9KaGRwmHVJAacocUN-uDkDyJzjGFc4cbKW21c14wAd8AiEqbZpwEEyfWkJWemEMZTtl2YkqkIXoPWXaVLqPvF55apw/?imgmax=800 "Cassandra_DataModel_CheatSheet.pdf - Adobe Reader_2013-07-03_16-44-41")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhkAhRk3bMy6j1fTbwWfivvj-di1YCMLBKwYrsgXg4Rd2a-FWttlerL5brBcd9rC7cy2YKwHE1qwfhrCK9nVxvikxeTv5rxbXIIJ_bfN4C1uLK0gYS8imMXtLDuMV4X63t5_AssDdpavw/s1600-h/Cassandra_DataModel_CheatSheet.pdf%252520-%252520Adobe%252520Reader_2013-07-03_16-44-41%25255B3%25255D.png)

*   Columns or Super Columns are stored ordered by names within their Column Families

For a better understanding of Cassandra’s data model, refer to this [article](http://maxgrinev.com/2010/07/09/a-quick-introduction-to-the-cassandra-data-model/ "A Quick Introduction to the Cassandra Data Model") by [Maxim Grinev](https://twitter.com/maxgrinev).

#### Installation

1.  Download the latest Cassandra version from [here](http://cassandra.apache.org/download/ "Cassandra Downloads Page") (I got version 1.2.6).
2.  Extract the archive (I extracted it to _C:\\apache-cassandra-1.2.6_ )
3.  If you don’t have Java installed on your machine, go and get it installed.
4.  Add environment variables
    1.  Reight-click the my Computer icon on your desktop or start menu.
    2.  Click the Advanced tab (or the Advanced System Settings)
    3.  Under System Variables, click New (adjust for your own directories)
        1.  Variable Name :  CASSANDRA\_HOME
        2.  Variable Value : C:\\apache-cassandra-1.2.6
        3.  click OK
    4.  Under System Variables, click New (adjust for your own directories)
        1.  Variable Name : JAVA\_HOME
        2.  Variable Value : C:\\Program Files\\Java\\jre7
        3.  click OK
5.  Now, open command window and navigate to your bin directory inside Cassandra directory (C:\\apache-cassandra-1.2.6\\bin in my case).
6.  Launch Cassandra by executing the comand **_cassandra –f_** (the “-f” causes it to run in the foreground). You will see lots of messages coming out. If everything goes fine, it will end up with something like this:

[![CWindowssystem32cmd.exe - cassandra  -f_2013-07-03_11-18-19](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjASUlDRUSqrSs1rgK6GU76BuYgJ00AOWDuwuLklhP90_zuziFvkczNIrF5vS3c7h11i9z0udnZSRRl27z0hyphenhyphenrQhLSbsTjIs6fN6udMcLXTD7IbT2bFQsYcy2wwqf0S-13mVfrYO3FkqA/?imgmax=800 "CWindowssystem32cmd.exe - cassandra  -f_2013-07-03_11-18-19")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjBIrfoe_Fl44YIKeXwyUCZ9EXV065NSDqckXcoTJpXCkHTw6XHBF9nzmGRWSnxdtJ2bBoydO0pQz0-BmxzH1kF87EbNamdvrU3WY7nLzTnpMGwgvVfgo2ae1u4wjAImVbmNJrHsQnrsg/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra%252520%252520-f_2013-07-03_11-18-19%25255B4%25255D.png)

Now we have a running Cassandra server is expecting incoming connections on port 9160.

Once Cassandra is up and running on your machine, we can connect to the running instance using the Cassandra command-line interface, launched by running “cassandra-cli.bat”, from the Cassandra “bin” directory.

[![CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-03_12-16-36](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj19NwqP4z5eU3L9KjSk758pLxJ_cQSgj3mY9ycqJTJi917p96hnfW2G9ZRYDGuF0iFWDhci1JQSCF1u8sA8l4KMQVFwoN1deOEpIlS3-Sf5M8FHBoc9L7_8oUn-qTtS_Aw2C2TJytQbQ/?imgmax=800 "CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-03_12-16-36")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgr4IDPCGnsimyJod4ayyEcIanOZneJtTLnpA9EPafUKj188eNE0kR-znSoWApVNdTlI4W5_GcJpkjpQcQ_HVHmX-gXibN3ADhY-KajBt_3dt45rQEiU_Vrxac3eZQKuuvHzuqKEHN1gg/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-03_12-16-36%25255B3%25255D.png)

#### Commads

*   **show api version;** to show the current api version.
*   **describe cluster;** to show a description of the current cluster.

[![CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_12-59-46](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjxlCzUZ9x9HPzgJyi3zS4A2dRF1Zg798OqcEZ1ZoxqkYbAxf7DtlCaf_LGFSiKDMT2DVOzZJR6NHfuulAc5MrCpvv84LWVH0naAMlLtRtj0xY3aVsRWOVnMGEPEVEJs-SfXaN8JQ3ABA/?imgmax=800 "CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_12-59-46")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj2qcID2u-J3QQmMoV0W8gOfoQ1-ZqZLNNTjhPbRz_3guiEJdkG1t0edzGljzGORgi3PjYsWbmV6AsTWWOaJtlgzjf7Y_7tU7RLSqI0UrJitEwGk4dwfs5siqzSmzZi_3SuccFqE6RaEg/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_12-59-46%25255B3%25255D.png)

*   **create keyspace** _TestKS;_ to create a keyspace and it have to be a unique name.
*   **use** _TestKS;_ to switch to keyspace TestKS.
*   **create column family** _TestCF;_ to create a column family TestCF within the current keyspace.
    *   No other schema definition is required, the column family is a collection of name/value pairs.
*   `**set** _TestCF[ascii('TestKey')][ascii('column1')]=ascii('TestValue');_ `to insert the TestKey/TestValue key/value pair into the column named column1 within the column family TestCF. You can use the **with ttl =** _x_ setting at the end of the set command to make the column self-delete aft _x_ seconds of the insertion time.
    *   by default Cassandra treats data as byte arrays but you can convert to other types such as **Long**, **int**, **integer**,…. Also **timeuuid()** generates new UUID. For full information about set command: **type help set;**
*   `**get** _TestCF[ascii("TestKey")];_ to retrieve the value stored in the key _TestKey_ within the column family _TestCF_`

[![CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_11-15-32](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjJJAqUr1UEzB-2r4mQecz8NJC_h95pzszydWVghREBgwRmOyJYBMKr3SLhvqHE4L2DqZ3lEgKvYcffCFjWci5ww91iyVPyshLNqd6etlOPaXSNV_ujGd7QtqX7_h83Vbf4bEghINoZZg/?imgmax=800 "CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_11-15-32")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhShKlZ8zPZJJhv77bjhyNqCWO554MiLjPTbTtXyhxhHLtSA5Fck2oxnVRguDBcjHDJEWLYquV2WDUjIrJ5AAiMvx4LQ3Us6zVK-frJ0pJD8YVhTC5g375GMIJZuBzCIq7D8T_q_cfk4g/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_11-15-32%25255B3%25255D.png)

*   **del** _TestCF\[ascii(‘TestKey’)\]\[ascii(‘column2’)\];_ rows and columns can be deleted by specifying the row key and/or the column name  
    with the del (delete) command.

[![CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_15-29-44](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhbdXo6htnz8sT5Mfw60aRYmNihTgMXFBEXk7EnkNHmBJVkC1xe9h1Fa_bTFKlGwWlTOlZeE4IhA-wIARdofYqYSdVFO1uNmP_jzcB7eoHNOYpuA4BJaeXByQxymlDXvyf4pXgxSHUQ3g/?imgmax=800 "CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_15-29-44")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgIkl_wSGgTtqI1LfbBnfTOn1vYOdzazWnYKYfuVS9qJt_ZdW7GfTJSwx7cyKWe4APnisNGtNAh5ZPCp2o111ABc8S_SZCpmdoEaM4Ut9vxuNg8N-tGgMAA94xeXdyn0tCroigIyj5WMw/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_15-29-44%25255B3%25255D.png)

*   **list** _TestCF;_ list the data inside a column family

[![CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_16-05-31](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjOdYodtR_tvEPOiUjUC7taADm_OLzUbCWa6RF0_afJmWqym4aIV-o5jUkt6Ri9fxazB3_YLEJzAA_93b9tdEWdrcXfdck9lQ2dCwhB9ub35iAQp5jtKb-5AKJwYDOJCkyEM3zcTASJxg/?imgmax=800 "CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_16-05-31")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhrwtfKfTXa_5IyryBUxHrARrVEPyOTDAsmusJRFJ4UMT2bVSaBdf0YL0f1Stc22f18kW0b5NndPZgjgoXCHwdMbnuieoASHhIifQMDE0dWY_oLgvvzQdNbvMNYXPTAA7PtGjC2Bc3-eg/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_16-05-31%25255B3%25255D.png)

*   **drop column family** _TestCF;_ removes a column family.
*   **drop** **keyspace** _TestKS;_ removes a key space.

[![CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_16-25-05](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiMNHlIqTYT2MzHy2C-LSbSPi76wd6tiZHDYs3Rj0GYc4zcyoAU5SqZpstPgJDtJ-At_8G80xvYBBZ5mR-Z-c8TcQKDSHqVQtgIz_K-fNuA8yb_kYshd_WrXLlrNd87OLF9eviSQHWZYg/?imgmax=800 "CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_16-25-05")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh-E74Mh8VuQX2QhObOHPrENUNKTIJmYEL44DJj1wuC4R3T4OUSsVCILb7mkjU80S_zAm_wugohytVPS1TMVP-N4O9JjGWijWY4EC7Jb0RMgbdLhl6hngCXNoUO3qki8hEq02GwJWL6cA/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_16-25-05%25255B3%25255D.png)

\==> You can insert to super columns much like inserting to normal columns. They can be read with get, written with set, and deleted with del. The super column version of these commands uses an extra \['xxx'\] to represent the extra sub-index level.

[![CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_17-07-44](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiclu6hDysZrNtrRjfERFw9UCqPeBw17rSaN2GbJ36bFwfTI2I3EWDzSRmOjtuFOHhzBoFwcaBYjyDB82Zeu4Mcag7u-EWWeYxd13AF2YyVmkOhuABpK7_dCEPHwh1p3ru0B13vUc_2GA/?imgmax=800 "CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_17-07-44")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgYpHGepOlrvITYzPI-t98z9H954ciPLLRXHm48X1BgdSoYLcAEKk2_48Xx1uQ3j2aJr3Z_1txHcQWlRY2Yz7jX-aljbVrr76GKPg9y4S7OOSWaLOvR66v1aBsl9ngBVdOxMH6h1OKYNg/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_17-07-44%25255B5%25255D.png)

*   **assume** _TestCF_ **comparator as ascii;** it decodes and helps display results of get and list requests inside the command-line interface. It can be used in the same way to set the **validator** and **keys**. By default, columns with no metadata are displayed in a hex format. This is done because row keys, column names, and column values are byte arrays. After using assume the column and value will be displayed rather than the hex code.

[![CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_17-29-07](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEggPN3MKKqXpNy44720XNZi1PMDz2x_PcIaKEGp5TXHH8jyYz9MDgifvmAqwNPRqLA6YRs0nV9_j7RmWQBv1mJluuWTuc_3HMatJFh4eBysYPhDog1uwAsZ2IeJn2WfKBKg0ZJpYbstpA/?imgmax=800 "CWindowssystem32cmd.exe - cassandra-cli.bat_2013-07-05_17-29-07")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjxdp-3i938W01fLU6N_KOSb3a8Mk5r9wQyd2jhFvc1Vq8rtBfMuGwjzcKRNHL6esI0FYJGQRNfComM_5ywRA-ERjmaK-BrKUeKx8DG5phVb_lUVP4sQQDfjsYdheJHH9KTusMkLmMQYg/s1600-h/CWindowssystem32cmd.exe%252520-%252520cassandra-cli.bat_2013-07-05_17-29-07%25255B4%25255D.png)

*   **Type Enforcement** : Cassandra is designed to store and retrieve simple byte arrays but it also have support for [built-in types](http://www.datastax.com/docs/1.1/references/cql/cql_data_types "CQL Data Types"). When creating or updating a column family, the user can supply column metadata that instructs the CLI Cassandra client on how to display data and help the server enforce types during insertion operations.  
    **create column family User with comparator = UTF8Type;  
    update column family User with  
            column\_metadata =  
            \[  
            {column\_name: first, validation\_class: AsciiType},  
            {column\_name: last, validation\_class: AsciiType},  
            {column\_name: age, validation\_class: IntegerType, index\_type: KEYS}  
            \];**
*   **Querying data** :

**set User\[ascii('jsmith')\]\[ascii('first')\] = ascii('John');  
set User\[ascii('jsmith')\]\[ascii('last')\] = ascii('Smith');  
set User\[ascii('jsmith')\]\[ascii('age')\] = '38';**

**get User where age = '38';**

*   **Update** is the same as set.

**set User\[ascii('jsmith')\]\[ascii('first')\] = ascii('Jack');**

*   **Quite** the client;

**quit;**

In this post we just touched the Cassandra’s iceberg. In later posts we will dig more in it and how to write .net programs against it.