--- 
title: "Running multiple Redis instances on the same server" 
date: '2013-07-02T11:42:00.001-05:00' 
tags: 
    - Redis 
    - NoSQL 
modified_time: '2013-07-02T11:42:51.399-05:00' 
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-4558320522262868780
blogger_orig_url: http://ebeid-soliman.blogspot.com/2013/07/running-multiple-redis-instances-on.html
---

Redis runs as a background process that listens to a specific port (6379
by default) for incoming requests from clients. Running multiple
instances requires a separate conf file and a new init script. The conf
file specifies details for the new instance, and the init script handles
starting/stopping of the instance background process.

Make a copy of the [redis](http://redis.io/ "Redis").conf file at
C:\\Program Files\\Redis\\Conf and give it a new name redis-s1.conf.
Leave both files in the same directory C:\\Program Files\\Redis\\Conf

Open the redis-s1.conf with your favorite text editor (e.g. notepad )
and change the following:

PID File

-   pidfile /var/run/redis-s1.pid

Port

-   port 6380

Log File

-   logfile "C:/Program Files/Redis/logs/redis-s1.log

Data Directory (don’t forget to create that directory)

-   dir "C:/Program Files/Redis/data2"

For replication only : If you planning to use this instance as a slave
in master-slave replication setting (where 127.0.0.1 is the master
instance IP, 6379 in the master instance port)

-   slaveof 127.0.0.1 6379

To start the new instance

1.  Open a new command window
2.  Navigate to C:\\Program Files\\Redis
3.  Run redis-server conf\\redis-s1.conf

To connect to the new instance

1.  Open a new command window
2.  Navigate to C:\\Program Files\\Redis
3.  Run redis-cli –h 127.0.0.1 –p 6380

Now you can have multiple Redis instances on the same server like any
other DBMS.
