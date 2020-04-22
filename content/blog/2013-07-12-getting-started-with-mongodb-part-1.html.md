--- 
title: "Getting Started with MongoDB – Part 1" 
date: '2013-07-12T13:46:00.000-05:00' 
tags: 
    - MongoDB 
    - JSON 
    - NoSQL
modified_time: '2013-07-12T15:54:21.770-05:00' 
thumbnail: http://lh3.ggpht.com/-m2ZNUOKu82Y/UdyKMjaQRMI/AAAAAAAABvI/ESn0UCWYT8g/s72-c/CWindowssystem32cmd.exe%252520-%252520mongod.exe%252520%252520--dbpath%252520Cmongodbdata\_2013-07-09\_16-10-49\_thumb.png?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-2830278696665579012
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/07/getting-started-with-mongodb-part-1.html
---  
**MongoDB** (from "hu**mongo**us") is an open source [document-oriented
database](http://en.wikipedia.org/wiki/Document-oriented_database)
system developed and supported by
[10gen](http://www.blogger.com/www.10gen.com) (founded by [Dwight
Merriman](https://twitter.com/dmerr)). First publicly released in 2009,
and since then it have been a rising star in the NoSQL world. MongoDB
stores structured data as [JSON](http://en.wikipedia.org/wiki/JSON)-like
documents with dynamic schemas (technically data is stored in a binary
form of JSON known as [BSON](http://en.wikipedia.org/wiki/BSON)), making
the integration of data in certain types of applications easier and
faster.  

#### Installation

1.  Download the latest mongoDB version from
    [here](http://www.mongodb.org/downloads "downloads page").
2.  Extract the archive to your preferred location (in my case
    C:\\mongodb). MongoDB is self-contained and does not have any other
    system dependencies. You can run MongoDB from any folder you choose.
    You may install MongoDB in any directory.
3.  MongoDB requires a data folder to store its files (default is
    C:\\data\\db ). You may specify a different path with the dbpath
    setting when lunching mongod.exe.

#### Starting the Server

To start MongoDB, open the command prompt window, and run mongod.exe
from the bin directory (specify the data path if needed)  
[<img src="http://lh3.ggpht.com/-m2ZNUOKu82Y/UdyKMjaQRMI/AAAAAAAABvI/ESn0UCWYT8g/CWindowssystem32cmd.exe%252520-%252520mongod.exe%252520%252520--dbpath%252520Cmongodbdata_2013-07-09_16-10-49_thumb.png?imgmax=800" title="CWindowssystem32cmd.exe - mongod.exe  --dbpath Cmongodbdata_2013-07-09_16-10-49" width="565" height="109" alt="CWindowssystem32cmd.exe - mongod.exe --dbpath Cmongodbdata_2013-07-09_16-10-49" />](http://lh4.ggpht.com/-usyjMRcQvaY/UeBs-Hy35mI/AAAAAAAABvE/H8AjQbagqRs/s1600-h/CWindowssystem32cmd.exe%252520-%252520mongod.exe%252520%252520--dbpath%252520Cmongodbdata_2013-07-09_16-10-49.png)The
`waiting for connections` message in the console output indicates that
the mongod.exe process is running successfully and waiting for
connections on port 27017  

#### Connecting to the Server

To connect to the server, open another command prompt window and run
mongo.exe from the bin directory.  
[<img src="http://lh5.ggpht.com/-cSLcxLVa1co/UdyKNTQDzhI/AAAAAAAABuE/8EPLDqel4As/CWindowssystem32cmd.exe%252520-%252520mongo_2013-07-09_16-27-37_thumb%25255B1%25255D.png?imgmax=800" title="CWindowssystem32cmd.exe - mongo_2013-07-09_16-27-37" width="493" height="165" alt="CWindowssystem32cmd.exe - mongo_2013-07-09_16-27-37" />](http://lh6.ggpht.com/-yAQeNKOIJ7E/UdyKNGd5VrI/AAAAAAAABt4/HJt-3Qz1R0U/s1600-h/CWindowssystem32cmd.exe%252520-%252520mongo_2013-07-09_16-27-37%25255B3%25255D.png)  

#### Run MongoDB as a Windows Service

1.  Create a log file for MongoDB (in my case
    c:\\mongodb\\log\\mongo.log ).
2.  Create a data directory for MongoDB (in my case c:\\mongodb\\data ).
3.  Open the command prompt window as an administrator.
4.  Run the following command <span
    style="color: blue">*C:\\mongodb\\bin&gt;mongod.exe –install –rest
    –master --logpath "c:\\mongodb\\log\\mongo.log"*</span>
5.  Run <span style="color: blue">regedit</span> from start menu.
6.  Go to *HKEY\_LOCAL\_MACHINE &gt;&gt; SYSTEM &gt;&gt;
    CurrentControlSet &gt;&gt; services*
7.  Find the MongoDB directory & edit the <span
    style="color: blue">*ImagePath*</span> key.
8.  Set value as *<span style="color: blue">c:\\mongodb\\bin\\mongod
    --service  --rest&n bsp; --master 
    --logpath=C:\\mongodb\\log\\mongo.log 
    --dbpath=C:\\mongodb\\data</span>*
9.  Save and exit registry editor
10. Open ComponentServices from Start menu &gt;&gt; Run
11. Locate the Mongo DB service, and reigh click &gt;&gt; Properties.
12. Set the Startup Type to Automatic. Then start the service.
    1.  To run the MongoDB service from command window, use *<span
        style="color: blue">net start MongoDB</span>*
13. Check at <http://localhost:28017/> to see , MongoDB should return
    stats.

<span style="color: black">In case you want to remove MongoDB service
</span>*<span style="color: blue">C:\\mongodb\\bin\\mongod.exe
–remove</span>*  

#### Data Model

Data in MongoDB has a *flexible* schema.  

-   Database consists on a set of collections.
-   Collections consists of a set of documents.
    -   Documents in the same collection do not need to have the same
        set of fields or structure.
    -   Common fields in a collection’s documents can hold different
        types of data.

Based on what we mentioned, you could say that MongoDB is schema-less.
But you may refer to this [data modeling
article](http://docs.mongodb.org/manual/core/data-modeling/ "Data Modeling Considerations for MongoDB Applications")
before doing real work on MongoDB.  

#### CRUD operations

-   When you start the mongo shell, it connect to test database by
    default. To create a new database or switch to another database, use
    ***<span style="color: blue">use newdb</span>***
-   <span style="color: black">To show a list of databases, use ***show
    dbs*** (databases are created when you insert the first values in
    it. This means that any database have been created but no values
    inserted in it, it really doesn’t exist).</span>
-   <span style="color: black">To confirm the current session database,
    use ***db***</span>
-   <span style="color: black">To create a collection, just insert an
    initial record to it. Since Mongo is schema-less, there is no need
    to define anything up front. The following code creates/inserts a
    towns collection:</span>

<span style="color: blue">db.towns.insert({  
name: "New York",  
population: 22200000,  
last\_census: ISODate("2009-07-31"),  
famous\_for: \[ "statue of liberty", "food" \],  
mayor : {  
name : "Michael Bloomberg",  
party : "I"  
}  
})</span>  

-   brackets like {...} denote an object with key-value pairs.
-   brackets like \[...\] denote an array.
-   You can nest these values to any depth.

To show a list of collections, use ***show collections***.

To list the contents of a collection, use ***db.towns.find()***

-   You will see a system generated field **\_id** ( composed of a
    timestamp, client machine ID, client process ID, and a 3-byte
    incremented counter) (you can override this system generated

MongoDB commands are JavaScript functions.

-   **db** is a JavaScript object that contains information about the
    current database. Try <span style="color: blue">**typeof db**</span>
-   **db.*x*** is a JavaScript object that represent a collection named
    *x* within the current database. Try <span
    style="color: blue">**typeof db.towns**</span>
-   **db.*x*.help()** will list available functions related to the given
    object. Try <span style="color: blue">**typeof
    db.towns.insert**</span>
-   <span style="color: black">If you want to inspect the source code of
    a function, call it without parameter or parentheses.</span>

<span style="color: black">**Functions** You can create JavaScript
functions and call them on the mongo shell like:</span>

> <span style="color: blue">function insertCity( name, population,
> last\_census, famous\_for, mayor\_info) {  
> db.towns.insert({  
> name:name,  
> population:population,  
> last\_census: ISODate(last\_census),  
> famous\_for:famous\_for,  
> mayor : mayor\_in fo  
> });  
> }</span>  
> <span style="color: blue">insertCity("Punxsutawney", 6200,
> '2008-31-01', \["phil the groundhog"\], { name : "Jim Wehrle" } )  
> insertCity("Portland", 582000, '2007-20-09', \["beer", "food"\], {
> name : "Sam Adams", party : "D" } )</span>  
> <span style="color: black">Now have three towns in our
> collection</span>  
> [<img src="http://lh5.ggpht.com/-HMED6vMJ-xU/Ud8r2fqEPSI/AAAAAAAABvc/wOO7EdlP9wA/Command%252520Prompt%252520-%252520mongo_2013-07-11_14-35-39_thumb%25255B1%25255D.png?imgmax=800" title="Command Prompt - mongo_2013-07-11_14-35-39" width="543" height="208" alt="Command Prompt - mongo_2013-07-11_14-35-39" />](http://lh5.ggpht.com/-xbNkGCPlb9o/Ud8r1wrCQ9I/AAAAAAAABvU/WjQaiWPOKL8/s1600-h/Command%252520Prompt%252520-%252520mongo_2013-07-11_14-35-39%25255B1%25255D.png)

-   To get a specific document, we only need \_id passed to **find()**
    function in type ObjectId(**findOne()** retrieves only one matching
    document). String can be converted to ObjectId using
    **ObjectId(str)** function.

 <span style="color: blue">db.towns.find({ "\_id" :
ObjectId("51def56c1cf66f4c40bb7f4a") })</span>  

-   The find() function also accepts an optional second parameter: a
    fields object we can use to filter which fields are retrieved. If we
    want only the town name (along with \_id), pass in name with a value
    resolving to 1 (or true).

<span style="color: blue">db.towns.find({ "\_id" :
ObjectId("51def56c1cf66f4c40bb7f4a") }, { name : 1})</span>  

-   To retrieve all fields except name, set name to 0 (or false or
    null).

<span style="color: blue">db.towns.find({ "\_id" :
ObjectId("51def56c1cf66f4c40bb7f4a") }, { name : 0})</span>  

-   <span style="color: black">You can retrieve documents based on
    criteria other than \_id. You can use regular expressions or any
    [operator](http://docs.mongodb.org/manual/reference/operator/ "Query, Update and Projection Operators").</span>

db.towns.find( { name : /^P/, population : { $lt : 10000 } }, { name :
1, population : 1 } )  
We said before that the query language is JavaScript, which means we can
construct operations as we would construct objects. In the following
query, we build a criteria where the population must be between 10.000
and 1 million. Ranges work also on dates.  
<span style="color: blue">&gt; var population\_range = {}  
&gt; population\_range\['$lt'\] = 100000  
100000  
&gt; population\_range\['$gt'\] = 10000  
10000  
&gt; population\_range\['$lt'\] = 1000000  
1000000  
&gt; population\_range\['$gt'\] = 10000  
10000  
&gt; db.towns.find( {name : /^P/, population : population\_range },
{name: 1})  
{ "\_id" : ObjectId("51df08e72476b99608460870"), "name" : "Portland"
}</span>  

-   <span style="color: black">You can also query based on values in
    nested arrays, either matching exact values or matching partial
    values or all matching values or the lack of matching values.</span>

<span style="color: blue">&gt; db.towns.find( { famous\_for : 'food' },
{ \_id : 0, name : 1, famous\_for : 1 } )  
{ "name" : "New York", "famous\_for" : \[  "statue of liberty",  "food"
\] }  
{ "name" : "Portland", "famous\_for" : \[  "beer",  "food" \] }  
&gt; db.towns.find( { famous\_for : /statue/ }, { \_id : 0, name : 1,
famous\_for : 1 } )  
{ "name" : "New York", "famous\_for" : \[  "statue of liberty",  "food"
\] }  
&gt; db.towns.find( { famous\_for : { $all : \['food', 'beer'\] } }, {
\_id : 0, name:1, famous\_for:1 } )  
{ "name" : "Portland", "famous\_for" : \[  "beer",  "food" \] }  
&gt; db.towns.find( { famous\_for : { $nin : \['food', 'beer'\] } }, {
\_id : 0, name : 1, famous\_for : 1 } )  
{ "name" : "Punxsutawney", "famous\_for" : \[  "phil the groundhog" \]
}</span>  

-   You can query a sub-document by giving the field name as a string
    separating nested layers with a dot.

<span style="color: blue">&gt; db.towns.find( { 'mayor.party' : 'I' }, {
\_id : 0, name : 1, mayor : 1 } )  
{ "name" : "New York", "mayor" : { "name" : "Michael Bloomberg", "party"
: "I" } }</span>  

-   To query the nonexistence of a field value

<span style="color: blue">&gt; db.towns.find( { 'mayor.party' : {
$exists : false } }, { \_id : 0, name : 1, mayor : 1 } )  
{ "name" : "Punxsutawney", "mayor" : { "name" : "jim Wehrle" }
}</span>  

-   ### elemMatch

$elemMatch helps us specify if a document or a nested document matches
all of our criteria, the document counts as a match and returned. We can
use any advanced operators within this criteria. To show it in action,
let’s insert some data into a new collection *countries*  
<span style="color: blue">&gt; db.countries.insert({ \_id : "us",  
... name : "United States",  
... exports : {  
...  foods : \[  
...   { name : "bacon", tasty : true },  
...   { name : "burgers" }  
...          \]  
...            }  
... })  
&gt; db.countries.insert({ \_id : "ca",  
... name : "Canada",  
... exports : {  
...  foods : \[  
...   { name : "bacon", tasty : false },  
...   { name : "syrup", tasty : true }  
...          \]  
...             }  
... })  
&gt; db.countries.insert({ \_id : "mx",  
... name : "Mexico",  
... exports : {  
...  foods : \[  
...   { name : "salsa", tasty : true, condiment : true }  
...          \]  
...           }  
... })  
&gt; print( db.countries.count() )  
3</span>  
Now if we need to select countries that export tasty bacon, we should
$elemMatch in a query like:  
<span style="color: blue">&gt; db.countries.find(  
... {  
...   'exports.foods' : {  
...    $elemMatch : {  
...      name : "bacon",  
...      tasty : true  
...     }  
...   }  
... },  
... { \_id : 0, name : 1 }  
... )  
{ "name" : "United States" }</span>  
If we didn’t used $elemMatch and wrote a query like the following, it
will return countries that export bacon or tasty food, not tasty bacon  
<span style="color: blue">&gt; db.countries.find(  
... { 'exports.foods.name' : 'bacon' , 'exports.foods.tasty' : true },  
... { \_id : 0, name : 1 }  
... )  
{ "name" : "United States" }  
{ "name" : "Canada" }</span>  

-   ### Boolean Operators

**$or** a prefix for criteria to return document that match either
condition1 or condition2. There is a a lot of
[operators](http://docs.mongodb.org/manual/reference/operator/ "Query, Update and Projection Operators")
you can use.  
<span style="color: blue">&gt; db.countries.find({  
... $or : \[ { \_id : "mx" } , { name : "United States" } \] },  
... {\_id : 1} )  
{ "\_id" : "us" }  
{ "\_id" : "mx" }</span>  

### Update

The find() function toke two parameters, criteria and list of fields to
return. The update() function works the same way. The first parameter is
a criteria (the same way you will use to retreive the document through
find()). The second parameter is an object whose fields will replace the
matched document(s) or a modifier operation (**$set** to set a field
value, $unset to delete a field, **$inc** to increment a field value by
a number).  
The following query will set the field state with the string OR for the
matching document.  
db.towns.update( { \_id : ObjectId("4d0ada87bb30773266f39fe5") }, { $set
: { "state" : "OR" } } )  
but the f ollowing query will replace the matching document with a new
document { state : “OR”}  
db.towns.update( { \_id : ObjectId("4d0ada87bb30773266f39fe5") }, {
state : "OR" } )  

### References

Although MongoDB is schema-less but you can make one document reference
another document using a construct like { $ref : “*collection\_name*”,
$id : “*reference\_id*” }. In the following query we linking New York
town with the country US. Notice the display of the new country field in
the New York town document.  
<span style="color: blue">&gt; db.towns.update(  
... { \_id : ObjectId("51def56c1cf66f4c40bb7f4a") },  
... { $set : { country : { $ref : "countries", $id : "us" } } }  
... )  
&gt; db.towns.find( { \_id : ObjectId("51def56c1cf66f4c40bb7f4a") } )  
{ "\_id" : ObjectId("51def56c1cf66f4c40bb7f4a"), <span
class="underline">"country" : DBRef("countries", "us")</span>,
"famous\_for" : \[  "statue of liberty",  "food" \], "last\_census" :
ISODate("2009-07-31T00:00:00Z"), "mayor" : { "na  
me" : "Michael Bloomberg", "party" : "I" }, "name" : "New York",
"population" : 22200000 }</span><span style="color: black">Now we can
retrieve New york from towns collection, then use it to retrieve its
country </span>  
<span style="color: blue">&gt; var NY = db.towns.findOne( { \_id :
ObjectId("51def56c1cf66f4c40bb7f4a") } )  
&gt; db.countries.findOne( { \_id : NY.country.$id })  
{  
        "\_id" : "us",  
        "name" : "United States",  
        "exports" : {  
                "foods" : \[  
                        {  
                                "name" : "bacon",  
                                "tasty" : true  
                        },  
                        {  
                                "name" : "burgers"  
                        }  
                \]  
        }  
}</span>  
or in a different way <span style="color: blue">&gt; db\[
NY.country.$ref \].findOne( { \_id : NY.country.$id} )</span>  

### Delete

<span style="color: blue"><span style="color: black">Removing documents
from a collections is simple, use your criteria with a call to
**remove()** function and all matching documents will be removed. It’s a
recommended practice to build your criteria in an object, use that
criteria to ensure that matching documents are the expected ones, pass
this criteria to remove() function.</span></span>  
&gt; var bad\_bacon = { 'exports.foods' : {  
... $elemMatch : { name : 'bacon', tasty : false }  
... } }  
&gt; db.countries.find ( bad\_bacon)  
{ "\_id" : "ca", "name" : "Canada", "exports" : { "foods" : \[   
{       "name" : "bacon",       "tasty" : false },      {       "name" :
"syrup",       "tasty" : true } \] } }  
&gt; db.coun tries.remove( bad\_bacon)  
&gt; db.countries.count()  
2  
  

### Reading with Code

You could ask MongoDb to run a decision function across documents.  

> <span style="color: blue">db.towns.find(  function() {  
> return this.population &gt; 6000 && this.population &lt; 600000;  
> } )</span>

or in a short-hand format <span
style="color: blue">db.towns.find("this.population &gt; 6000 &&
this.population &lt; 600000")</span>  
<span style="color: black">or combine custom code with other criteria
using **$where**</span>  

> <span style="color: blue">db.towns.find( {  
> $where : "this.population &gt; 6000 && this.population &lt; 600000",  
> famous\_for : /groundhog/  
> } )</span>

Custom code should be your last resort due to the following:  

1.  Custom code queries run slower than regular queries.
2.  Custom code queries can’t be indexed.
3.  MongoDb can’t optimize custom code queries.
4.  If your custom code assume the existence of a particular field and
    this field is missing in a single, the entire query will fail.

In this post we explored the basics of MongoDB, a rising star in the
NoSQL family and the most common document database. We saw how to
install and configure it. We saw how we can store nested structured data
as JSON objects and query that data at any depth. We How we can update
and delete data. In the next post we going to dig deep into MongoDB.
