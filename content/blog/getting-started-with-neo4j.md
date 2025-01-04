---
title: 'Getting started with Neo4j'
date: 2013-07-17T17:19:00.001-05:00
draft: true
url: 
tags: 
- NoSQL
---

[Neo4j](http://www.neo4j.org "Neo4j official website") is an open-source graph database implemented in Java. The developers describe Neo4j as "embedded, disk-based, fully transactional Java persistence engine that stores data structured in graphs rather than in tables". According to DB-Engines [report](http://db-engines.com/en/ranking/graph+dbms "DB-Engines Ranking of Graph DBMS"), Neo4j is the most popular graph database.

As a graph database, Neo4j focuses more on the relationships between values than on the commonalities among sets of values (such as collections of documents or tables of rows). Neo4j is small enough to be embedded into nearly any application. On the other hand, Neo4j can store tens of billions of nodes and as many edges. Let’s get started with Neo4j !

### Download and Installation

*   Download the latest community release for your platform from [here](http://www.neo4j.org/download "Download and Install Neo4j") (in my case it is 1.9.1 for windows ).
*   Extract the archive to your preferred location (in my case it is C:\\neo4j\\)
*   Double click Neo4j.bat in the bin directory. You will see a lot of output appears and then the window will close and leave a blank command window.
    *   If you don’t have JDK installed, you need to install it first and configure its environment variables.
*   Now open your browser and navigate to [http://localhost:7474](http://localhost:7474). If everything went fine you will see the welcome message of the webadmin interface of Neo4j

[![Neo4j - 1.9.1 - Google Chrome_2013-07-17_17-16-44](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi_9dURX122Z89ZIMSR_YrGedI8_9WpQHR0KS8vDgiVx1-8xtczi_QKH73mROsGyZ4vFmjBcvfYMUTRMcGtJ6TLJu8vIogu04s7dOv6r55yI7SJ7dRGsPObuc-0GBkBmjsdUPPMsymTQQ/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-17_17-16-44")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhfV56pkLX5VSChuzaRaqUfOt7aEntscKjE-Rx2DJ8OI58OtNr8uPKwzEYsmBtVLu-yhKKzk2shE-zP90DnF4E-zFmPrI8kxEvYdJJg98BrlYHO5MAy3TqtMiDyzuWY4jVb6MXCZ7nhjw/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-17_17-16-44%25255B3%25255D.png)

*   When you close this message you will see the webadmin interface. You can reopen the welcome message by clicking on the _Guide_ button on the top-right corner on the webadmin.

[![Neo4j - 1.9.1 - Google Chrome_2013-07-17_17-20-31](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgqlCdnQWAmWstYfjF5IYOx6IfWKZpeUrp1EkUCk7Z5HcPCR7S3LZMBRu6eoJWN1peUGCTUNZbWzwsiNO4vFYA5HkV-8tg938zmYoiKfNKnKidXxVNiu_PdjIM6erAPohPwB8mDeNniYw/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-17_17-20-31")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhhfxY3UfDCrvWRiaZzt_TlOK8aWh8msrNb38qaN7o876HILwfE1SnuUedVoJVohk8lBfRjusOnZv9OKUwO1Zh446VPOQ-voukMep-8GkvyoNwX-e_IMUxk9JKdqXkCguehb1lsMPQmLg/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-17_17-20-31%25255B3%25255D.png)

### Neo4j’s Web Interface

The above screenshot is for the **_Dashboard_** tab of the Neo4j’s webadmin interface. It shows a summary totals of the nodes and relations in the current installation. It also shows a timeline of their creation. Till now we have nothing.

Click on the **_Data browser_** tab. This tab will be used to CRUD operations on our database.

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_11-21-17](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEibQ96TlwQYRNfM_2dclAtNSFcTtNvR4BLX2nNRPDeYs8AZG-PYYocQA_SasukeTwB9RKGBLo9s82GRmXAO6156eccu9-Ihlw4TxhCdBYNnWFQAFLu8srbnAAgbyY3jkbFcr4zhJPwsmw/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_11-21-17")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg9iFEtG8VJ4ayTg0tp2XpBkhSov6I0MMx4IH47qFGcCrrh4btWGxOS7w0mPISRqCwQ7R3vniCUhfyI795T-OPM85NJVGtyBU5EUjQvu435XTIYHeDuVoWY8Tyk9Fqrq0qHmWGdxxihMA/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-18_11-21-17%25255B3%25255D.png)

click on **_\+ Node_** to create a new node.

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_11-25-18](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjzfMesqVS2uk3Uf0yvqn_ypcpsn6NUL-0r8HnTDtvGSTizQ5fov4A13CaBqo-B8mjYKIrSGtB2RNA1eojxJOv7CfWrGD7G9FSHFzAOqj5ZyExQPIoIcfXNXQqshi3O19VHpIrNW9YPpA/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_11-25-18")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEivp1yFN5qy0ZMs7fyvWdqAX0h2AlEbyrALMbURY1CfhGhV7RQEkArWhSJFfzXptjVOQcBTV4CKZzRPs_V8ot2uWXsxoTMAX__Cc_5evczA6o7FPVz-k8N20KagolxeTdm89DQyhhszRw/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-18_11-25-18%25255B3%25255D.png)

**Node** is a vertex between edges that may hold data as a set of key-value pairs. The box on the top-left shows the node number (auto-increment). Now click on **_\+ Add property_** to add key-value pairs, you can add as much as you want.

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_11-40-57](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhXD2c2ZRaMdX2sykIaQ5fqBPDopbVGrsimBNgXTXdTOjvTFH5tBuIsOYsQywY9ZheHql6AbFL1_IC5d-DrS7Zz25HQ_D5EqhBHWpDYl9A2Wrv9jfenYRGvYV7knmR6OBn7uj4kNnw7CA/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_11-40-57")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjSdDPe2MeJ6qAU7LKBB2b_y4qdxt7avE2aR_02b22jJpU1wyUP81eXyFHs62NMW6qfpanmZUQvBVIKCnoZQ5EZBi16TRYV2McfK_FBCxsQlJUSUMo3rQKlKUMdw9CC6MMRCbP3bZLYgg/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-18_11-40-57%25255B4%25255D.png)

let’s add another node with \[firstName: Mark, lastName: Anthony\]

Now let’s add a friend relationship between mark and john. Click **_\+ Relationship_** to add a relationship. Enter from node number, to node number, and the relationship type (just a string). Then click **_Create_**.

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_11-45-54](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiwLvv9TzUOY3iMMIzaEnvY86TlpaUNlTtm5CxowycFGNhd-Suv6k2tb-qsC1kQArqlv-I9W16W13B7rcKI4ZAX0D3b9Mt_QNDg-z2DAMdkDruM7LG_5NJyVuCvJVHk8lPIm6ArrZ1qNA/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_11-45-54")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiL7iUZyI07r-BDwnlSDqOJEY4smjiPR1p8T6XyL9-YXtLJtTlLACDxLjO42BC3W2loqsXHX3hCNhwU7z7nTJK0xaSJbkLmCs1SoS8H8zPwBpqOXLs2WQ_bMfxa6CQsLS6-6kRg2cMXXg/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-18_11-45-54%25255B2%25255D.png)

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_12-50-05](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhc3N2qk0Ccgkofu6ZeYaBuaQ5fsDGDrp_ZMBcnqMDYHKZEUbNVl5kENub4yXIklofmOaj_DyRky-Tp9H6ayLqfsHlzGyjc3OswOaI6YeFFfjKeXDIwcJ0vg7Ibrtr7sE75aV65StGKxQ/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_12-50-05")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgYew_luqQhXe5L_NfaIlI5y-A_tv1Q14fPyhFyOAy6uhkCrscINqJ-hQpIp_qnzcQ5WjtKBre_3UKovlS3TDSglCbafgE_1G21tcdGh4RHcM4NDC3NlLERSrgHfnetIt8pKTQtFXVK0g/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-18_12-50-05%25255B3%25255D.png)

Just like nodes, relationships can contain properties. Click the **_\+ Add Property_** button and enter the properties \[firstmet : “SXSW Conference”, LinkedIn : “Yes”\] so we can keep track of where john and mark first met and weather they connected on LinkedIn or not.

Now let’s click switch view mode button [![Neo4j - 1.9.1 - Google Chrome_2013-07-18_13-14-16](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiLPruWt5ZZV21D2NZ7U1pvWSAYXzo924lVvqypFM8iTk4CMx4MV-87riaSTE3fFxSwYzqCvq9QkcmPH3-IThYdgSrNfQDFS1U9AGB0PYrblzXN7GG7_sO2SnvfXCh_i1Bo1gUTO7CrjA/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_13-14-16")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh4uXPGFgBrD_Ki8yxGp75RZTNYapOZeVuDRKIDz9fRljNV2bwEvZQQkgq35tLa_l-n3ro0gq8PwjjmfaSEPMCFPok1H11SNNAu-cobpWu0ICtU_4rrVNSTnxAa_-MjRs1EdKYwZZgVTQ/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-18_13-14-16%25255B2%25255D.png) and see how our graph is look like

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_13-15-27](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgjcbKtkEUQibso20IOZzgiaHFEnficciUP7FQE8mybe7GD225Ksu4gMJnKHim5ygyNtHBgNkJNj8OUUQr-uiP1kcYPP9IPjultt0z9ATAvytVKs3pJglAM5EiGHyMjM1u7_l32oyNgOg/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_13-15-27")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgXdwc_XxyNf7nL_6N9mVf5AN83AKVGtofRag5DrEi5EW1Vn6Tv4cQktvmoWu2LM5k5oBtjZ5MTKK_LObtJorXGFxiJf0KsFiHfvzw5-UdA_1IGw4QBDa-THokjUc_hu8D9rrKLOgnlCg/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-18_13-15-27%25255B3%25255D.png)

The Style button brings up a menu where you can choose which profile is used for rendering the graph visualization. To see more useful information on the diagram, click Style and then New Profile. This will take you to the “Create new visualization profile” page.

Enter “Social Network” as the new visualization profile name. Select Box from the **_Show as_** dropdown box. Change the Label from {id} to {id}: {prop.firstName} (prop.lastName}. You may change the font size or color. Click **_Save_**. Now your graph should look like:

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_13-37-52](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi8VE5j67ql1a1d8Uhz3NJEDXJFHVI7wskPcpnlCImZHpR1h4M4sw1-MdCDjaEXN5hyn4Myyc2FgUPtnVA_rMveiHv2SBBi7hV929dZ9EZRv_R5Rw_Pw70fOqBfgK6iG2gYucNR2etrkA/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_13-37-52")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgJUDIsg11rs3HpSv4KmJu3CA4ywJgg0bU8Vn5D4P1BNoDnTpspYx4mMZQcorBkKLuR8f1gLJ4-zalx7tiWsPg8XujMpCGdw1T7m-h7TJaGzCYU7ByOR6kOv2ceEZQe7xLtKU0ocSWCLw/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-18_13-37-52%25255B3%25255D.png)

Although the web interface is an easy way to make a few edits, we need a more powerful interface.

### Neo4j via Gremlin

There are several languages that interoperate with Neo4j: Java code, REST, Cypher, Ruby console, and others. The one we’ll use today is called Gremlin. [Gremlin](https://github.com/tinkerpop/gremlin/wiki) is a graph traversal language written in the [Groovy](http://groovy.codehaus.org/) programming language. You don’t not need any knowledge of Groovy to use Gremlin. The Gremlin console is available in the Web Admin; just click the  
Console link at the top, and choose Gremlin.

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_14-14-10](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhF3-60NYYWyoejmwRKR4YisJ_gYcVzD5qGSFuGlDBujYZcILSFoAFBql4ifEiIF6mlE2esdJrdS1P9rXkZ6mybTRGRmWG25-jsABFOF7BKBs1nKLNfYIvejm88KGzC7NJ4H4FEyJMVUQ/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_14-14-10")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhPf_wHZAa34UHFhtdUMfZ0sAUYP9uQ1dN70Wk2qxfFo_lJqLHINIOasiyEdThaCVkeQvmMjp-e1VrdjO3Q5vo_WzRGdCpjS8z5yO8pNBosziPwE4ee0PoCOeaLBjZPk_tutkCZ-dXwmg/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-18_14-14-10%25255B3%25255D.png)

Since Gremlin is a general-purpose graph traversal language, it uses general mathematic graph terms. Where Neo4j calls a graph data point a node, Gremlin prefers vertex, and rather than relationship, Gremlin calls it an edge. g is a variable that represents the graph object. Graph actions are functions called on it.

*   **g.V** gets the graph vertices
*   **g.E** gets the graph edges
*   **g.v(0)** gets vertex 0.

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_14-19-39](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjory-oxQNHE_0s8o4QaIvChA1fU1lWTsH1qkHz_hYnixXNXJZ81sRM0cxlEoDq71Jdo5LsZovlAYnKKWQia6BnYecKsOUSdoMkbRkWY_Cju0dYmeXV8VU1QD-Hv0K9X1OogME-ldQjfA/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_14-19-39")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEir5-9Qzx84mIe-1tAjyp5PbgWYMp-lcOEleOMUkQ_vUQfOse0NkT-ahj-HQsTE-VX0eq2k2jGLcntBwuhWbpiBa_oyqccHfhiCf4_rmYKTIcLEJ6nV0-0iQ0ztR6fb4EYg1z_2ce3Q_w/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-18_14-19-39%25255B2%25255D.png)

*   **g.v(1).map()** lists all vertex 1 properties
*   **g.v(1).firstName** returns property _firstName_ of vertex 1

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_14-39-10](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgAADfE7q10u_-P1PLAJNfflGI-o5hKkVTZPhGOLDLVB_DOc18LoJyfxTscMovUS6qC2eTCBlvLJrkRrM1jYEz8vn107mQ1z44wo-pCUjhFd5D_7Oo5V2NylvNrK793HiUBRSML_0ceqw/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_14-39-10")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhQkGEGSw8_EG-r5TvGkKPTC65W2jQaz2yDW-0Z5ChhP8s5xgNNt03wvagngq5cq8KU8ELTN1AOPjYrOIcnXHaMri5TRZq1mUZd56i3VYbl63XUAVny_Y9yf81dV__AsPJVpWk89oIlLA/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-18_14-39-10%25255B2%25255D.png)

*   **g.V.filter { }** gets (walk in Groovy terminology) the vertices that evaluate true according to the filter condition (closure in Groovy terminology) between the curly braces {}. The **it** keyword inside the closure represents the current object and is automatically populated. g.V.filter{it.firstName == 'Mark'}
*   **g.v(2).outE** gets the outgoing edges of the given vertex(2).
*   **g.v(1).inE** gets the incoming edges for the given vertex(1).
*   **g.v(2).outE**.firstMet gets the firstMet property of the outgoing edge from vertex 2. Can be applied for **inE**.

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_15-34-18](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjQ19D73mzJy0RwqJWsVfGz1m3Y_BDXIbMCqZxmlzHDfe77VM-_OY31tlIPXckQk8qcqXg_1v779P0tGDQcNeqka_2UEG9YPQbTSFle_hnJ3YMFMd40d6PkSDGTPcZSp8PFYgZ6_lHM0g/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_15-34-18")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhgCxmqEnk79JTxD76bqS-1ayKvoft5e8BOa7iA6GsSTw6TJbBERky59GnLDixWZvN5WN2SRdTCZc3YbZXDXUi1HJdxOLo48byf5dmWCCogfK5UZblN6ATNDm33ShoX3NF7a0AvRnStVQ/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-18_15-34-18%25255B2%25255D.png)

*   **inV** gets the incoming vertices. You could retrieve any property of these vertices

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_15-51-25](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhNlcR61N21aA7p_DtA-Cjhz0qSxe0iqCNayqjJEnc-KrlV3K5FqDvOwj45ufaXyK24UV3uVlgHjlQQwG4vAm5lnHnrZbIbnKuRuQ7iBSST3WRTV4XCQ6tq4Ig2uh7KUXgpJHabZhWcRA/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_15-51-25")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEixlaXkH7R7o1C2EV8X9wnS1qMuqgcGKv8sbUx-IiTv_3TfohdxSjheT6Xk2LHXmZRWm6G2Cf_WYK1ePtOT3ARnvp4EkYxG6sXnfCYuOCvBCAuMrfGgMi9AfUDTcvvMr0655hpQam3WNw/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-18_15-51-25%25255B2%25255D.png)

*   **outV** gets the outgoing vertices
*   **out** shorthand version of **outE.inV**
*   **in** shorthand version of **inE.outV**
*   **g.addVertex(\[_propertyName_ : ‘_Property value_’\])** add a vertex to graph with the specified properties.
*   **g.addEdge(_vertex1_, _vertex2_, ‘_relationName_’)** add an edge from _vertex1_ to _vertex2_ with relation _relationName_.

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_16-11-55](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEisTYKl-RvDMpFyEYTU9dwcsz_KftTdEuMXtsJ_VADeE4lp2NpTn3SCU-5AVCAET6_u4Ognt-eDU7akrQIgEAZYXWf_1kELJ5-e2jq0tbyVPriOfTnFP5TgwfNUVTbZETWl3c9KmIXG7w/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_16-11-55")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjfg2swl1Q3payV7l6cRHcA5MmoPd3mTZ3cQkhm2OLawgAK87xixcBy70ZZt2yagTdaXVeDbNDfgmnzLgsJ87p0BZ4cjZq8uwtaldaWHnvxBOZxKfuIobeAWgmMN8tjBkv3U1I9ENSjbQ/s1600-h/Neo4j%252520-%2525201.9.1%252520-%252520Google%252520Chrome_2013-07-18_16-11-55%25255B3%25255D.png)

### Pipes

Gremlin operations can be treated as a series of pipes. Each pipe takes a collection as input and pushes a collection as output. A collection may have one item, many items, or no items at all. The items may be vertices, edges, or property values.  Gremlin, Pipes, and many more are parts of a bigger system developed by [Tinkerpop](https://github.com/tinkerpop/blueprints/wiki).

![](https://github.com/tinkerpop/rexster/raw/master/doc/images/rexster-system-arch.png)  
For example, the outE pipe takes in a collection of vertices and sends out a collection of edges. The series of pipes is called a pipeline and expresses declaratively what the problem is (not the steps to solve the problem like in imperative programming).

Gremlin is built on top of a Java project named Pipes. Suppose that Mark would like to know the colleagues of his friend John.

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_17-14-58](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhb1jsjQWvhYM16Xp7Yn7aW3k-5L5VS5yRmSZxKxjR2G4WjUkGocnTe7LKzwBQM2glUnpFNZ3lftxTt_6scByjbiJQ-r_ANHaLztlecYuR_x4O88EX5b7L2t76iRvjWicAs29esZLCiig/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_17-14-58")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiHZhbEnVzwmpPFJGv1A0vgO-JiU279Wv0Porku7yTzc_l7ps96PjWuINbyjESZK6x6sZeuuQtoU0WC1Fdk8pq70q1OF5sQe5yE41CU_oBNrWRw4X4Ug5GHLLGLUXhyphenhyphen_pBUGdsZhescww/s1600-h/Neo4j---1.9.1---Google-Chrome_2013-0%25255B24%25255D.png)

the query will be something like that:

[![Neo4j - 1.9.1 - Google Chrome_2013-07-18_17-26-12](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh5I29UrnbF_Sa_wsiR3ZYbJzbrL2l7BXCZ4nbmwHuhQwrDh0rYK9qMj16KBT67Etsc6avGRz5JpvYhs62wkHSVTgMvx7JdKS3KSBskXNr3brReam3pb6O_zcgZMO8uubpu7Q9pc1IKyg/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-18_17-26-12")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiVqLg9vXQa7tJ5Tzu25H-bvLb2nehHWX1spnsZX2KEfDIAvx5EoQmnnGdzNouO1v5TAkcIrXOS7yw-AAeNFXP9Xf8wfG7sbxhAN6Visr739Rsh9FUmH5CXfNrP2BTfxdM0yd6rJmp1cQ/s1600-h/Neo4j---1.9.1---Google-Chrome_2013-0%25255B10%25255D.png)

Gremlin query works quite similar to jQuery in terms of expressing the graph traversal process. Consider the following HTML snippet:

```


  
*     
    section 1  
      
    
*     
    section 2  
      
    

  

```  

  
*   Getting the _section 1_ string using jQuery  
    
      
    *   **$('\[id=navigation\]').children('li').children('\[name=section1\]').text()**
    
      
    
*   Getting the _section 1_ string using Gremlin  
      
    *   **g.V.filter{it.id=='navigation'}.out.filter{it.tag=='li'}.  
        out.filter{it.name=='section1'}.text**

  

### Pipeline vs. Vertex

  

To get a collection containing just one specific vertex, we can filter it from the list of all nodes. This is what we have been doing so far using g.V.filter{}. The The V property is the list of all nodes, from which we subset the desired set. But when we want the vertex itself, we need to  
call next(). This method retrieves the first vertex from the pipeline. It’s similar to the difference between an array of one element and the element itself. To show the difference, call the _class_ property of _filter_ and _next_ and see the returned object.[![Neo4j - 1.9.1 - Google Chrome_2013-07-19_09-14-15](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiup8tPTR03F3bazvM5R55c8kYXXqNdyrGMqHL9nJrSZy9WTksoZ_ycD59LCQ8m6zsENTAQjvW1BSay7bgJSBkGKGIPzods1545ERGdvijuiwBNc9wKAwNLYxLODfSoEi_Mso13bgFkxQ/?imgmax=800 "Neo4j - 1.9.1 - Google Chrome_2013-07-19_09-14-15")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEicg3WiBEFEFrRb5SYpz6UY8jWnw5Jb1vRH-YDzX0GLICitVHOLRw9FCQffSa3mUzC-f0gK4sYmDgSAaPfkm3ZoLVlnBX3MaLYavQQpkhfjKKw8hckovpuo-Lup8dkENkJVrT5_ZS2hIA/s1600-h/Neo4j---1.9.1---Google-Chrome_2013-0%25255B48%25255D.png)

  

Pipe-processing units called steps in Gremlin and it falls in the following types.

  

  
*   Transform steps : take an object and emit a transformation of it.  
    
*   Filter steps : decide whether to allow an object to pass or not.  
    
*   sideEffect : pass the object, but yield some side effect.  
    
*   branch : decide which step to take.

  

For a complete list of steps in each type, refer to [this](https://github.com/tinkerpop/gremlin/wiki/Gremlin-Steps "Gremlin Steps"). Groovy also has a map function (a la mapreduce) named **collect()** and a reduce function named **inject()**. Using these, you can preform  
mapreduce-like queries.

  

### Domain-Specific Steps

  

Graph traversal is sufficient but it is not business friendly. Business is not talking in edges and vertices. Gremlin lets us creating new steps that are semantically meaningful to the data stored in the graph.