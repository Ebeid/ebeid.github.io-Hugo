---
title: 'Redis 101– Part 2'
date: 2013-07-03T12:47:00.000-05:00
draft: false
url: /2013/07/redis-101-part-2.html
tags: 
- Redis
- NoSQL
---

We introduced many of the [Redis](http://redis.io/ "Redis")’s fundamental concepts and commands in the last post. In this post we going to introduce some advanced features.

#### Publish-Subscribe

Previously we queued data that could be read by a blocking pop command. Using that queue, we made a very basic publish-subscribe model. Any number of messages could be pushed to this queue, and a single queue reader would pop messages as they were available. This is powerful but limited. Redis provides some specialized publish-subscribe (or pub-sub) commands.

*   **SUBSCRIBE** subscribe a client to a key, known as a channel in pub-sub terminology; client will block until messages are available.

[![Redis Client_2013-07-01_16-25-11](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEip_rPKeJ1NpXyTnpHm1gG5oOWM8wcAjMEEjN0xF0XwEv1EFiFVw3XD-An1D2AN47qijPmkHNDNJa94sYWUzrJ5wdVpj6RQTU4icX03FqbQtgV3rfJ4Pswg14TQj5LEZqBFLo7kJykDcQ/?imgmax=800 "Redis Client_2013-07-01_16-25-11")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjMlSGXKPf5_H8yGrRwLoNuh_J2o-6IR2gB6gJG7x0-Furq9mcz2n_lhCK2Iupjm8_vbfQId0_PXVL8jhXkLC7q64xRs_LFHmInjBh7FFKsktHGYkp81t4by16QuWSACb97ZLY6PtwwkA/s1600-h/Redis%252520Client_2013-07-01_16-25-11%25255B3%25255D.png)

*   **PUBLISH** will push message into the channel returning how many subscribers have received it

*   Publisher window [![Redis Client_2013-07-01_16-27-41](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEii84qjPghCJzV8zEh4eXDZ8rMBoeemK-lrD-UBKuWaenMcRcz2XwbZ477HmAlXX1ya0WLhJgSrPlywbc1Jr6hr7ZWM4BoYItT-8TCB_gPtAP8S4LDO8SCPqUJoGze56UyDQ-BoUPWS2A/?imgmax=800 "Redis Client_2013-07-01_16-27-41")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhMZxalDWkAJxguo9mNAfkwG2iZWGon8uIs_C5pCw0uGsayHJ2l3WDXxZ-NTMoSgQ9apZ2_wl1BiCGVL-XtoexvBnYQbCqDSfQs3WqLbGQB3h7HxSuXV0nPYIq50IUgCY8oqV0dzsDWKA/s1600-h/Redis%252520Client_2013-07-01_16-27-41%25255B5%25255D.png)
*   Subscriber window receives : the string “message”, the channel name, the published message value [![Redis Client_2013-07-01_16-28-53](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhvWShFExdKF3ffzu9ra2uoVC-F1V7xzusCTzgBZ1qZIXBTgUpgeKrMo8FIkTLuGO_YNaMHWXWAAlQvSV000oRFUEkAkIzd9aoVcqFxIy9n8V-htO5Vm0lIPCKiH78_hW06JTAUpBolkw/?imgmax=800 "Redis Client_2013-07-01_16-28-53")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEimmQdXTnAoa_jvKHUsXgFiWTUacJUWoxf3nxbj8RniQonTLjxOxQ2bnJGIK1SunN_LU1USlV1j0y6CqwdldXQP42htNpeB1r1tdHHxc5AyaK40vkcraW72eCIHdtQ-VactRucgK5eJnw/s1600-h/Redis%252520Client_2013-07-01_16-28-53%25255B5%25255D.png)

*   UNSUBSCRIBE unsubscribe or disconnect from the specified channel. If no channel name provided, it will disconnect from all channels.

#### Server Information

*   **INFO** returns a list of server data, including version, process ID, memory used, and uptime.

In order to change any of the Redis’s default configurations, you need to edit redis.config file at C:\\Program Files\\Redis\\conf . It is fairly self-explanatory.

#### Durability

Redis has a few persistence options:

*   No persistence at all, which simply keeps all values in main memory.
*   Forced save

*   Use command **SAVE** to force server to save database to disk.
*   Use command **BGSAVE** to force server to save database to disk asynchronously in the background.
*   Use command **LASTSAVE** to get a timestamp of the last time a Redis disk write succeeded (also provided through the _last\_save\_time_ field in the server **INFO** output).

#### Snapshotting

By default Redis saves snapshots of the dataset on disk, in a binary file called dump.rdb. You can configure Redis to have it save the dataset every N seconds if there are at least M changes in the dataset, or you can manually force it by calling the SAVE or BGSAVE commands as we said before. For example, the following configuration will make Redis automatically dump the dataset to disk every 60 seconds if at least 1000 keys changed (This strategy is known as _snapshotting_.):

save 60 1000 

#### Append-only file

Snapshotting is not very durable. If your computer running Redis stops, the latest data written on Redis will get lost. While this may not be a big deal for some applications, there are use cases for full durability, and in these cases Redis was not a viable option.

The _append-only file_ is an alternative, fully-durable strategy for Redis. It became available in version 1.1. You can turn on the AOF in your configuration file:

appendonly yes

Then we must decide how often a command is appended to the file. Setting _always_ is the more durable, since every command is saved. By default _everysec_ is enabled, which saves up and writes commands only once a second. This is a decent trade-off, since it’s fast enough, and worst case you’ll lose only the last one second of data. Finally, _no_ is an option, which just lets the OS handle flushing. It can be fairly infrequent, and not recommended.

appendfsync always

\# appendfsync everysec

\# appendfsync no

From now on, every time Redis receives a command that changes the dataset (e.g. SET) it will append it to the AOF. When you restart Redis it will re-play the AOF to rebuild the state. Append-only has more detailed parameters, you could refer to the online documentation for more details.

#### Security

Redis provides command-level security through obscurity, by allowing you to hide or suppress commands. This will rename the FLUSHALL command (remove all keys from the system) into some hard-to-guess value like c283d93ac9528f986023793b411e4ba2:

rename-command FLUSHALL c283d93ac9528f986023793b411e4ba2

If we attempt to execute FLUSHALL against this server, we’ll be hit with an error. We can also disable the command entirely by setting it to a blank string.

rename-command FLUSHALL ""

You can set any number of commands to a blank string to allow only a customized subset of the Redis’s commands.

#### Benchmarking

Redis provides an excellent benchmarking tool. It connects locally to port 6379 by default and issues 10,000 requests using 50 parallel clients. Tool test many commands and have a long output report. Tool is in C:\\Program Files\\Redis\\

[![CWindowssystem32cmd.exe_2013-07-02_09-15-52](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjFkKkyntKxJwAmF7ZxyZHVe7B5WGrS7o6_puBxOD1-FftJzdJBQG-YPUdkLCYSzFvtQLaBEplFRBk1B0ZUZWd4YOINvPKtTvBzZCimPSurBJzvznTUcUWNBAy1BWJilb3KQY7YKJ9-6A/?imgmax=800 "CWindowssystem32cmd.exe_2013-07-02_09-15-52")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj2lY-BkxedOV8tfSews2zK9gkRWMgr72erS3fKUJyP0Unsi9sdmR1LMMY7ez5kTaysxjM51JTCAej6l7wGHP3cHBCDUlxdh4hEMZ6WSBtkL6MbJfXaI71atpwJbsQkTIbQBM3A5xxIgg/s1600-h/CWindowssystem32cmd.exe_2013-07-02_09-15-52%25255B3%25255D.png)

#### Replication

Redis supports master-slave replication. One server is the master by default if you don’t set it as a slave of anything. Data will be replicated to any number of slave servers. Configuring master-slave setting is the same as running another instance with the slaveof option in the salve’s conf file set to the master IP and port. Refer to our previous [post](http://ebeid-soliman.blogspot.com/2013/07/running-multiple-redis-instances-on.html "Running multiple Redis instances on the same server") for more details.

This concludes out Redis 101 tutorial, we tried to touch all basic and moderate features in it. Later we going to show how to write C# programs against Redis.