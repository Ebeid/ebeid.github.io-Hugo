---
title: 'Redis 101'
date: 2013-06-26T15:29:00.000-05:00
draft: false
url: /2013/06/redis-101.html
tags: 
- Redis
- NoSQL
---

[Redis](http://redis.io/ "Redis") (REmote DIctionary Service) is an open-source networked in-memory key-value data store. First released in 2009, currently sponsored by [VMware](http://www.vmware.com/), and since then it have been ranked [the most popular key-value store by DB-Engine](http://db-engines.com/en/ranking/key-value+store "DB-Engines Ranking of Key-value Stores"). Redis creator [Salvatore Sanfilippo](http://invece.org/ "Salvatore Sanfilippo aka antirez") refers to his project as a “data structure server” to capture its unique handling of complex data types and other features. Interested ? Enough talking, let’s get down to business.

**Download** Redis installer from [here](https://github.com/rgl/redis/downloads).

**Installation** is straight forward:

[![Setup - Redis_2013-06-27_11-42-13](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjoEXLL_igfXyQnZo3wstBJ7pWfE3S2lFRkWo4JgubuL1hiB5OaqOVz4N46SbPJQ6evoySooryIKnoaYbpWvYWf1wcSdb60vmiEU4gpYo39Z8SaSA4w_TyWzsEV8aK-fsaqBLqCiBFJJA/?imgmax=800 "Setup - Redis_2013-06-27_11-42-13")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh_Fprqb6SmBqLWdt0b3jH9GAvKaaYJoikaSKOhAJBYzGZ8WxL3GGaIaPRpanuVOd0hmUGiaQVLCQlK0BK8RqnHT2Rafs4N3NE-JIwDDyzH5yVUif2Ao9TXAhgTVaEpZa0YmVOxpbb3kQ/s1600-h/Setup%252520-%252520Redis_2013-06-27_11-42-13%25255B4%25255D.png)

[![Setup - Redis_2013-06-27_11-42-21](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiWSj_fGxvvv2S95VH83Or1fVi_CpJeD7VZ9hFX5eINoa-KY6KRT02pnj_qtenQhmKucx6JwAziB-BmJaY1rcLmikO-iS3k6PS-dwEsLDePh0UpbNRHv2Wuo1gC5rIGsOyGCvbYtLmrRg/?imgmax=800 "Setup - Redis_2013-06-27_11-42-21")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhQ9bK6OJC3nOeAkzzfNJZEhUIBIjfuhCbxRRxemqr19iCyC3s6F8uOZAk-m8QysPCnjanyAGpZqlcdLiY8LiPVj0-6RYsFHeOoo769GnM845uhyphenhyphenmGY281JnsRnfH0KXNznhAcEMzyAXw/s1600-h/Setup%252520-%252520Redis_2013-06-27_11-42-21%25255B3%25255D.png)

[![Setup - Redis_2013-06-27_11-42-25](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhO3w25pbPFBl083gH9GgWXDyS9N_BXHw_9fCWgOLRw26NqnUCQvAceEKjJGkMUy096sZ92BDzRnFni2_kxo56NNjm_9ShUIL9DAZcXtTSH9EXme6xv5hppczQGeLofTbF5usTWx4FLhg/?imgmax=800 "Setup - Redis_2013-06-27_11-42-25")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgVCihTR61nbRyMkLhSViBLLbVoj3y5ZmXjFI6R6caYNcuNnqKdRXVLYWDiH03zBJExcbaot3KFPvAAFlem76NGM2a8znpINTvJZZl4DEaVOPQbuA4DsLcs1pRG-m2juwDj4RXG0ABusQ/s1600-h/Setup%252520-%252520Redis_2013-06-27_11-42-25%25255B3%25255D.png)

[![Setup - Redis_2013-06-27_11-42-29](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhUUZCVu0kZmXDcYkzyjJQ5LX_4-Qa9Dc0yXmn7Pfia1PYdfhGm8eWAV4Spcx_KMpQtpN3SJPjlg8R0tmi1k5t-7_uAvOXS0SvppyFaFEQ_3uV_Y0Gqcy5US-wIkyCZRzIcwvriPPOf5Q/?imgmax=800 "Setup - Redis_2013-06-27_11-42-29")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgeVbsDendgOfQkIjc3-rfsNLMcWoMjltyap0IY8i8EsNrYrWSX4MbDlt2U7lI2MylrQT6u1pepNb3zMBI7z_767Rd2aMoP-jr582zVsUF4Hwvv50202U5QMDsNu6M97zJNwT1-fyRz8g/s1600-h/Setup%252520-%252520Redis_2013-06-27_11-42-29%25255B3%25255D.png)

[![Setup - Redis_2013-06-27_11-42-32](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg4UynYlqcz84mG7_2qd1LiIwUDJlvUJ3_16ntvaPnwe04dTQYuic8w6DLxNNXJnlJgKtXDH-Us6uT9CaJcrJayzbGc-eKefp5vfeh03G-3Nl48YM2bX-V1fApdjAmRNOP_OuF1AlJilA/?imgmax=800 "Setup - Redis_2013-06-27_11-42-32")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEipK9TTeCffkzC1OMMDZ_rq4N28UHIkOCjrh_OfU-wp2oeCZ1AjB7Ezj_p5cFToO2u4F7wteSbav-XiMLuXsW2J5_Z7x0K98g8kEXcRhQjaom_F7eaJIE06-COK8Ly3ncwbE3QFIJ2W4w/s1600-h/Setup%252520-%252520Redis_2013-06-27_11-42-32%25255B3%25255D.png)

[![Setup - Redis_2013-06-27_11-42-36](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhRbOv_vPSjOznE6FRiR4d4Ap-y51y1DWYNnh1fEWeLVDtD8ZEj2FSYOabZ6DdEEbOVMPyPvmToi-FVZUBtgVjvkUy5Atp0NYToejS1N29073qgDzTeHaEy_ajOD4dkm96fgInVRahy0Q/?imgmax=800 "Setup - Redis_2013-06-27_11-42-36")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEifrrX265e2fxWyPpgCxVM5gUpHY69jhVscuP3ODw4xYpzw8sOsd-PLHkLoVXyF_Gp1sYhMq41qtZr510bjYXGpl0-4fGDFy2di9Y2hSv8HPk0yJR7M6Wko2uETZ_rYFUESifUHlo3SSQ/s1600-h/Setup%252520-%252520Redis_2013-06-27_11-42-36%25255B3%25255D.png)

[![Setup - Redis_2013-06-27_11-45-05](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgM56dX0Dqpyp17J11frtgSESFukDA6w0z0ASzIrJ_UnEML_dTfTJ8wTZBWund66ZkEQ5o_-QLQb-ecvqlHaDIcPAsFypKxcz1vrIQxJa3aQmFtRf2BYaOkP0YMviI7YOtK3DqYcy7ZyA/?imgmax=800 "Setup - Redis_2013-06-27_11-45-05")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiM9OSCEQQxBWVYGW3PXeiT_URXI-zS5tsF-ZjnGrsP2lRVWzdbBCIprJsUXZC-Qw7G_6drkMP73CjmTqrTe_18uCla9_YpPe7A7hykPpt1btcPyo_OxLqMEcXh6plLVAte1aU7RisXYw/s1600-h/Setup%252520-%252520Redis_2013-06-27_11-45-05%25255B3%25255D.png)

**Start the Server** go to Control Panel >> Administrative Tools >> Services , right click _Redis Server_ and select Start.

[![Services_2013-06-27_11-49-50](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgSCJb84ueJglYofAG2pcZDBP4wxU67p8lYL21gVEdQ2JDX9Du92CC6th1TOwRVO6Pcct7fh68qK5S3WduPOG9MVPlklv6aQZ6kMtqoYuP36h6BWCnHPHjd6vSxf4KmgvBi-KKdnY_hqg/?imgmax=800 "Services_2013-06-27_11-49-50")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjawyLeLulDQL4MkI2pMfkqHwWolh_APjCAN682ZlncwAZ2uqPdxx1sWnR8xiqrYbmKTDb8ULJ4rzAXcLi9LuvWOQArSW4doh7C_WDMB7xvdnV0vIvSDp40LtrczHTB4Z5j1f0IVm_d_Q/s1600-h/Services_2013-06-27_11-49-50%25255B3%25255D.png)

**Start the Client** look for Redis Client (with red cube icon) in your start menu and open it. As you see it listens to port 6379 by default. You could ping your server by writing PING, if everything is good you will get PONG in return.

[![Redis Client_2013-06-27_11-56-46](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjjYtA55TfaTCv07vE3LjyvsLXXNP9jdpACM-85BGpVe-SC0tRrNpTJTk9ow9fv6YHJepHIX0gu0dMN4-m6yTTUo7dHojDYpD-HwJVAyJg0BnnZMXik9d5szxLAKKHFPr3ec4mCJScfbQ/?imgmax=800 "Redis Client_2013-06-27_11-56-46")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh4Y09UQXzxuDmMHuwQObvMjtAFHT2MPxDXowj3DsuZw7ssTCgo9CI8i5N-vmEgvzqXKB4_8J-e5dM-w4wlysXJl2LsfoCwz5ADHTUuMEypXkfPhh6nJEJrE7DuvsWWZeJw5vKCEUOcJw/s1600-h/Redis%252520Client_2013-06-27_11-56-46%25255B4%25255D.png)

### GET & SET

As we said before, Redis is a key-value store. We store value inside a key and retrieve it later using that key. We can use the command SET to store the value "fido" at key "server:name" (server replies with Ok if everything is good) (Note that we used colons \[:\] within our key. This is a valid character that often logically separates a key into segments. It’s merely a matter of convention, with no deeper meaning in Redis.)

```
 SET server:name "fido"
``````
To retrieve our value, we use GET command (server replies with “fido”)
``````
 GET server:name 
``````
You could also delete a given key and its associated value using DEL command and you can check for key existence using EXISTS (1 exists, 0 otherwise). `We get and set multiple values in one command using MSET & MGET`
``````
 MSET 1 valueA 2 valueB
``````
 MGET 1 2
```  

Although Redis stores strings, it recognizes integers and provides some simple operations for them. If we want to keep a running total of something, we can create a count and then increment it with the INCR command (gives error for noninteger values).

```
 SET count 2
``````
 INCR count
``````
 GET count
``````
[![Redis Client_2013-06-27_13-01-40](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgxmGAbcs-MJWv_ylJ18V-ZqOLD8DOtKg51gSXg84cvLUtdhVEUtFh3716USFQRdnJ40ZeXOOTpZsDqzVYyYo6uWJj1_8dx-eVmqQ16JvYA_1WlmHCC-GG4FfX3BtrN6MNOuZFfGDQ67A/?imgmax=800 "Redis Client_2013-06-27_13-01-40")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhbnzmOSf7ugpqxmL3MMYUYEsyXWB1tTl29Gn5oeQ83p1rB7z4W6DM9Cp3uC6JprElOyihqRJmiYdwW9a9w_0bTZ_V9edZRggSolYYYAZflRubMwyT1BnX6KR_3MYNgxq8GkMLzyv1j9Q/s1600-h/Redis%252520Client_2013-06-27_13-01-40%25255B4%25255D.png)
```  

You can also increment by any integer (INCRBY) or decrement (DECR, DECRBY).

  

[![Redis Client_2013-06-27_13-04-08](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgERA8E2TG65GSvEJtOhcGSb5fQmlLRHWXASSGgVytlyaWa7KvQAMdTzwSJ8AqZfEKcX_ZaoP5GHO6VdsVvcG__1woB8LropaNfwZ7Fp64NOof1xSXpH8FZQscHM4YgxpzY7fRhJ7jlgw/?imgmax=800 "Redis Client_2013-06-27_13-04-08")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEj0oXZ10bHufgNWbupSXlMjpJROggV5nJhycKuIMcA60bPS6uvNe-6oheY2UpF5pTSCM6GadEqI6sf53d0MYMKyM-B5TS_O17cquCNhPvHEdaR9qAzod8G_sm9vdU2POhXp7N9H1-elyA/s1600-h/Redis%252520Client_2013-06-27_13-04-08%25255B3%25255D.png)

  

It is good to know that these simple operations are atomic in Radis.

  

### Expire

  

You can tell Radis to hold a key only for a certain period of time (in seconds) using EXPIRE command. You can test how long a key will exist for with the TTL command. It returns the number of seconds until it will be deleted (-1 means the key will never expire). All keys are permanent by default.

  

[![Redis Client_2013-06-27_13-40-01](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg1LRqZvcDmrE3aRoS0eAPn9zfxtVgvaB7lKkEQP702cSB8bjITCitFQdOpTXbLEcmpVXlwmw-oj4usP5yFBNpiihpcaVRoxssYUOYMNeMNvqv8CwliVull_2srsoXkIIZOjouvCy6eOQ/?imgmax=800 "Redis Client_2013-06-27_13-40-01")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhm2hCbBtab_ozHQN1uRGQoJkyH6IBHHsB8bXCa2OgseYrWY-HesjpYtV0kRjjaj1cFtTe9EcTethDTLDWWXryi4_-sPSYMzpd6EPOoj1-sg2xSHO1X58cnpNIFjAoEISvZqhyphenhyphenYhEa5PA/s1600-h/Redis%252520Client_2013-06-27_13-40-01%25255B3%25255D.png) 

  

Setting and expiring keys is so common that Redis provides a shortcut command called SETEX. Also at any moment before the key expires, you can remove the timeout by running PERSIST KeyName.

  

A common trick for keeping only recently used keys is to update the expire time whenever you retrieve a value. This will ensure that your most recently used keys will remain in Redis, while [the least recently used](http://en.wikipedia.org/wiki/Cache_algorithms#Least_Recently_Used) keys will just expire as normal.

  

### Transactions

  

Redis like most DBMSs supports transactions. We begin the transaction with the MULTI command and execute it with EXEC command. So, wrapping two operations like SET and INCR in a single block will complete either successfully or not at all.

  

[![Redis Client_2013-06-27_13-17-56](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhh55u2lDfJIT3VHmPIVfuQlL8NcOwtAO2FDTogwuXB6xUPA4fhV8mOn0j78ZcqLdl-8anEP6FBHo1VRZSp82hSI5DdtfLDqOP0qjwKtqlP1x2gOPtZIchgy51ogdXebMRpSXiBpXEyeQ/?imgmax=800 "Redis Client_2013-06-27_13-17-56")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgbKuz-whMIjUeGmws7qtixnTkJmSJhzLQawzQeIXbtJJg_gKrvNGJawak9IKK_OSEcAoU3-2efstSNfe7JAgVSeCfC_8RuOx8VcVjT01BC5SRHb2aHLyuT1WZF4lcObIcl0mVmDfdIaA/s1600-h/Redis%252520Client_2013-06-27_13-17-56%25255B3%25255D.png)

  

As you may guess from the server response inside the transaction, commands are not executed instantly. Instead, they are queued and then executed in sequence.

  

Similar to ROLLBACK in SQL, you can stop a transaction with the DISCARD command, which will clear the transaction queue. Unlike ROLLBACK, it won’t revert the database; it will simply not run the transaction at all. The effect is identical, although the underlying concept is a different mechanism (transaction rollback vs. operation cancellation).

  

### Complex Data Types

  

Radis can store lists, hashes, sets, and sorted sets natively. These collection data types can contain a huge number of values (up to 2^32 elements or more than 4 billion) per key. That’s more than enough for all [Facebook](http://facebook.com) accounts to live as a list under a single key.

  

#### List

  

A list is a series of ordered values that can act both as queues (first value in, first value out) and as stacks (last value in, first value out). Some of the important commands for interacting with lists are RPUSH, LPUSH, LLEN, LRANGE, LPOP, and RPOP. You can immediately begin working with a key as a list, as long as it doesn't already exist as a different type.

  

  
*   **RPUSH** puts the new value at the end (right) of the list.
  
*   **LPUSH** puts the new value at the start (left) of the list.

  

[![Redis 101 - Windows Live Writer_2013-06-27_14-42-33](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhDxpRddWeQs86q5YNCidxaxdr6BTdHUgqzXXRiC7sFUghg_KCEnGzq9IvSC-bbVrwR0JDmJ7PXVI7u-nRJknzQ0C_GNa7yQ33cG8VeLiNn1vAf5eH_5vReGrpybTtfYKGaYOV98inyow/?imgmax=800 "Redis 101 - Windows Live Writer_2013-06-27_14-42-33")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjFNkxSfYmDXZ8AEoETR6wbCxlS4EH2d6l80PtFHkB7HhxlfhoakbhdH_A5uThA0OOeUSXh4vsdDrrgeD-iPMhaw_TZoWm6wwN36xg6hlA5gxNanDNPCN0KCx7X79CdNm-rjivlD4LHYQ/s1600-h/Redis%252520101%252520-%252520Windows%252520Live%252520Writer_2013-06-27_14-42-33%25255B3%25255D.png)

  

  
*   **LRANGE** gives a subset of the list. It takes the index of the first element you want to retrieve as its first parameter and the index of the last element you want to retrieve as its second parameter. A value of -1 for the second parameter means to retrieve all elements in the list.

  

[![Redis Client_2013-06-27_14-46-47](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg-qZI8nASUcm5tP1jaMXn3OgBRkk3zsuiECAzZxHxOxkfOjbUDgNu5_uCCfLqgADJrpkCV7G3u3GGilpJumyRjrGjM-e6kbe_yK6xDT2T7tcAQQHK13ZkeRea_miNt4Gpy5I8ey841bg/?imgmax=800 "Redis Client_2013-06-27_14-46-47")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg103xF-3LKGnQ9QI9rYPvGIfylcy33MEKE7aXz8GgUe2SVh55tzVPdfMcLTT0n5npJjlTuocDbC14gxe2r3FV_wp5sptSiN6QY14PCZXT_KDgel0JuKKSbGxc8K_OToneeDqBJpyA67g/s1600-h/Redis%252520Client_2013-06-27_14-46-47%25255B3%25255D.png)

  

  
*   **LLEN** returns the current length of the list.
  
*   **LPOP** removes the first (left) element from the list and returns it.
  
*   **RPOP** removes the last (right) element from the list and returns it.
  

  
*   Use LPUSH/RPOP to make List act like a queue.
  
*   Use LPUSH/LPOP to make List act like a stack.

  
*   **LREM** removes (some or all) matching elements from the list. It also requires a number to know how many matches to remove. Setting the count to 0 as we do here just removes them all. Setting the count greater than 0 will remove only that number of matches, and setting the count to a negative number will remove that number of  
    matches but scan the list from the end (right side).

  

[![Redis Client_2013-06-27_14-53-25](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjVs-9PYTrrmzKxZC61_YDZdOQgDGfYp13_3G7OxzIUolNRoeqH8fQpJr5a9hXhdDCyEMDLh8yvREr5ZEACgKTSPvfduhOk0KiSRoIX1faGuaD2UtVMGnNqUQn8FdABB1LRwwuSUC1AIA/?imgmax=800 "Redis Client_2013-06-27_14-53-25")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjAgK5zmlmPkm007ILLq7QTTa1s3QzIwmwYEyv1tNTl_lzRenUMeLk9sweqlMGsQwdNTYMRWeV5TvGEuMson9NTjlX7LSwTvr2Ry5K0bZmE7ArJTKouPHjXj9QXJD37y4xslhUS-DERCw/s1600-h/Redis%252520Client_2013-06-27_14-53-25%25255B3%25255D.png)

  

  
*   **RPOPLPUSH** a single command for popping values from the tail of one  
    list (right pop) and pushing to the head of another (left push). Surprisingly, there is no commands for RPOPRPUSH, LPOPLPUSH, or LPOPRPUSH.

  

#### Blocking Lists

  

It really interesting to know that Redis provides message queuing APIs natively. So, assume you want to write a simple messaging system where multiple clients can push data to one side of the queue and one or more listeners pop data from the other side of the queue. Listeners should just listen for new data and pop them as they arrive.

  

  
*   **BRPOP** the blocking version of RPOP, it blocks the connection when there are no elements to pop from any of the given lists.

  

[![Redis Client_2013-06-28_11-04-25](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgc3EU-rtGPXvkv5b4pVnqPukk8M1UeaIXh1F_0CUS9XeX1xg_zZOttbisHAjPRain-PGinDUF8OOHVjzNqK57gPdMx6PmMH9dVIjKoqKG-02-1J7dR4Fvm9MJ79GUdc82Q3vD8vpE0SQ/?imgmax=800 "Redis Client_2013-06-28_11-04-25")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEigSVdruqK_vG6INjvRQ1ClC9QNQiYfjfxkRsSHlUeTahutwKAm7KLpHIQxqkvrsDGhk914ZovFVDXqpOg-DHnan9KSuFYPp6IaR6IJOSxv32yaX6StRkELZmTofVuh0A-cy-d8m-AwLQ/s1600-h/Redis%252520Client_2013-06-28_11-04-25%25255B3%25255D.png)

  

now open another Redis client window and push a message into messages list

  

[![Redis Client_2013-06-28_11-04-53](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEghxCPnHlXSUSIFZIfhsVnKV2SGvFbVcloaJgSi1rmBFxHlvAjLtC2fSgV3ot2eETvRju4_CnQsclSL5pl1Eusd7LHnzz0jKuZlDQdrIOO-tmc9ZkZH04N_7dA6_fqyTP2K69q_NkHHsA/?imgmax=800 "Redis Client_2013-06-28_11-04-53")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEirHCSycy9IGFIbVEH3EXHxuhEHLGKkwtrtCf4aiC9LOzxWaFx_gjMbIPOQoEwybedBOBGWqLuIsC-nLuZqkkdSTyXjFLK_pSC7oZsX30D1XfQhVbJEcMt1ckOIJg5V7Hp-TerJ7ppE2g/s1600-h/Redis%252520Client_2013-06-28_11-04-53%25255B3%25255D.png)

  

if you switched back to the blocking BRPOP command window, you will find it return the key, the popped value, and the time spent blocking

  

[![Redis Client_2013-06-28_11-05-11](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhUW21MRsaKnBbdvHHxZoGBNeYWWqmD2ZGAY1eE86eO4W9wONGlCPIgiPYKLw08Z0D7uW-tNzshEyUeR7QnaTdbd5v1cHrZmNzAvpah56EbGkh1nw2euD5YG8Q8R40qm2szaOzjyMeF4Q/?imgmax=800 "Redis Client_2013-06-28_11-05-11")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhVFr2C9mGZM_HMbl3Jhfvp_OkdXI1MXYtEexFZF8Y-voRLMmPvlO6cMN51tjWYUQEk5XeepcBYEGlJ1VBoJK3gI5ustr1u9prx9ttzB1BaKIYUo5QtJlZRFWoe43fvoHk_AI3xEO3Cxg/s1600-h/Redis%252520Client_2013-06-28_11-05-11%25255B3%25255D.png)

  

  
*   **BLPOP** the blocking version of left pop LPOP
  
*   **BRPOPLPUSH** the blocking version of right pop left push BRPOPLPUSH

  

#### Set

  

Sets are unordered collections with no duplicate values and are an excellent choice for performing complex operations between two or more key values, such as unions or intersections.

  

  
*   **SADD** adds the given value to the set (duplication is not allowed).
  
*   **SREM** removes the given value from the set.

  

[![Redis Client_2013-06-27_16-41-05](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh-gN-IA2DrzSkh3jSo-woUch-nZTgtOwdQG24hnCpH9VL8vvm4tCpFC_5JoQ91QrFomB_xroGdXMnsHEfYmk4PsjLuTTAP8sVDnqwges9FS-JZIEPp8cfiPc5rFsgqseitnTzxTgQaHw/?imgmax=800 "Redis Client_2013-06-27_16-41-05")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgB7THAuUhbwkJ2MLzMcwVlY7P9o-5kQ8ziyVriUCM-j-eQ_4OTlzX5ZWLUivSbJsj9S3uNL4W6hCakBiM7RP4zxUNQh-yQASNuD5qmXNs3dPiQPY9uEyxQPurp8BaCYWkS070lsdHlMA/s1600-h/Redis%252520Client_2013-06-27_16-41-05%25255B4%25255D.png)

  

  
*   **SISMEMBER** tests if the given value is in the set.
  
*   **SMEMBERS** returns a list of all the members of this set.
  
*   **SUNION** combines two or more sets and returns the list of all elements.
  
*   **SINTER** returns the intersection of two or more lists.
  
*   **SDIFF** returns the elements that exist in the first list only but not in the second list.

  

[![Redis 101 - Windows Live Writer_2013-06-27_17-00-54](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg6RTQTnQBrv0RE28rJ3li2ukzn2dUkWDx7_HMr8Fh3Bbv4lPNpAzLJqqniGnrPWi4XWMBsBSE0ejUh2XZqa5ztRE-RmbNTz6fpOTf1wObUiLReE3XhXQDcI1DpIeaGpmonIsAYZ_j5SA/?imgmax=800 "Redis 101 - Windows Live Writer_2013-06-27_17-00-54")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhLYcZS9hj2twm8ZTy06GdA6oj78dHDlQ8Fy0IMr-TV-6fYpcjxlaMAjTpLSnUgRMdafhANUrBvlx6kwyHEnXdDVvBCe52EDEqQNilNxT-EVseCHsKhWYvnQFqbK6Mtq93cEUeyackzdA/s1600-h/Redis%252520101%252520-%252520Windows%252520Live%252520Writer_2013-06-27_17-00-54%25255B3%25255D.png)

  

  
*   **SUNIONSTORE** / **SIMTERUNION** / **SDIFF** stores the result of operation done on the second and third parameters into the first parameter.

  

[![Redis Client_2013-06-27_17-09-00](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEglXKl1iPFtWZAzqGbMDk1fjK87K-EwnCrq1z7oNLPvw_GhfLuxKQE4bUP9Y9L6KhnxKcBh0KsYsf37qmzuAePLovH8zC8tQiSCJVXNm5VfctbC_LvY0i2hYuBir-CQ-7_Hh25_3oX_Mw/?imgmax=800 "Redis Client_2013-06-27_17-09-00")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjSN-DqKZ4THBfW0qgu6hCCSrbiBH83-KEASaXkKBhrC6kWEN7GkjTlANOqNMqJpttt85-UAfzTanz53gV7EIg7m7AymW6FH8KQZCcsO2ygpqGbaZoLtrYJjDQaAt4WbWk6cZLAUL1aOw/s1600-h/Redis%252520Client_2013-06-27_17-09-00%25255B3%25255D.png)

  

  
*   **SMOVE** moves one element from one set to another.
  
*   **SCARD** counts the set elements (set cardinality).

  

[![Redis Client_2013-06-27_17-21-00](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgHgvZd0lbOm3SgkKlvNS1xhoi9VHpJd52LCzx1B68lfiNurA23u3BtJQJW2LotTdYXq0D728bK6qxbXVNGI-2WceqjhfHRXd0McTckrdeM3VTyoFtVQIIAXfgTNdc8IgtlKN6p56D0cw/?imgmax=800 "Redis Client_2013-06-27_17-21-00")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgnSOIbs3Raiv12kHEoHjaVRBCkqg3uX_xXr8evt9PHOmdIc8jcG75Lau3iEJ2EpAuNhFlkluUdMZITXRlwCl1v3Tphe5m0xKxjbuo60fAoyjkU7ZeFcR7cAIEIvwQluQjszLmR2qAeqw/s1600-h/Redis%252520Client_2013-06-27_17-21-00%25255B3%25255D.png)

  

  
*   **SPOP** returns a random element from a set and removes it.
  
*   **SRANDMEMBER** returns a random element from a set but does not remove it

  

#### Sorted Sets

  

Sorted set is similar to a regular set, but now each value has an associated score. This score is used to sort the elements in the set. Sorted sets take something from each of the other collections data types. They are ordered like lists and are unique like sets. They have field-value pairs like hashes, but rather than string fields, they are instead numeric scores that denote the order of the values. Internally, sorted sets keep values in order, so inserts can take log(N) time to insert (where N is the size of the set), rather than the constant time complexity of hashes or lists.

  

  
*   **ZADD** add a value with a specified score.
  
*   **ZRANGE** returns the elements between start index (zero-based) and end index (-1 means to the end of the sorted set. Put **WITHSCORES** at the end of command to get elements and scores, not only the elements. To get them in reverse, insert the word REV, as in **ZREVRANGE**.

  

[![Redis Client_2013-06-28_08-51-02](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEiNxclUowRHPVpbCKqq7myg08H7vQdXDDwnxQzkEaNJmRhl1UL9EYJHipGgnXV6OCC02uPHNJ7OBVxBBXMHDVx6DpLEJ9Otc7poaC0mvhEg5PTYqZR_4DSVdtd0gXXJx8l0l0vCZArEzA/?imgmax=800 "Redis Client_2013-06-28_08-51-02")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjWZWFoyf3D30eVD0CgVo5hPW6k17B_eP5dEhFdAJgJHG1xJzsZ59o3y-MAqSIqJF4z8_qFc7k6WUzmMOik3KA5MsVgviX2-e4RQh9z1Dbidze6eNH01fFyoUNaILjJzDYN0OAHwWm7cg/s1600-h/Redis%252520Client_2013-06-28_08-51-02%25255B3%25255D.png)

  

  
*   **ZRANGEBYSCORE** since we are using a sorted set, it’s more likely to get elements by score ranges instead of index ranges (x <= score <= y). We can make a score number exclusive by prefixing it with an opening parenthesis ( x < score <= y).

  

[![Redis Client_2013-06-28_11-49-34](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjpcySMvTYgEjVe5G0TYd-7TYccRS-duBiLDVt845vsOWvKMEoPxwHwbW9vjICWq5HjFDttX1mxK5OLmc8K3rWt-nbH6-mSPnas3k4l3YbRohg376MDNA3fl8AJYKt1sp5-QrCIWZ1uLw/?imgmax=800 "Redis Client_2013-06-28_11-49-34")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEga_HMevZVt1n4JREj3tJlWEDyGnI5e32MY1bUQ3htlRqwVDxlfzSgj_SVhv-LFRQ1ycpWKwcICtdrMLclYsA_vR6loHHFnttFk_PvQS5IVXWiovLDf-Fuxf0e__6_zWTykpU_kU9M0hg/s1600-h/Redis%252520Client_2013-06-28_11-49-34%25255B3%25255D.png)

  

  
*   **\-inf / inf** negative / positive infinities. can be used in retrieval (by index or by score). We can also range by both positive and negative values.
  
*   **ZREMRANGEBYRANK** / **ZREMRANGEBYSCORE** remove values by rank or score.
  
*   **ZINCRBY** Increments the score of member in the sorted set stored at key by increment. If member does not exist in the sorted set, it is added with increment as its score (as if its previous score was 0.0). If key does not exist, a new sorted set with the specified member as its sole member is created. It is possible to provide a negative value to decrement the score.

  

[![Redis Client_2013-06-28_08-58-48](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgBRp8Lg8MVJEJ7iR5At31wN7nwMPvva0pIKosng-xOSxUYR9kJXcWRTQ4zvqArHi9REn0kFqDKChGgRa3FOs1feBd5o4VH52aT9yo66U3wWfPcpTQHnNFEYX0R9fVx4msGucz9BruF1A/?imgmax=800 "Redis Client_2013-06-28_08-58-48")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhkjljOKk9pPEoCYmDt4MjDDVl_Z10KsRllW24zpGoDwO_bKBaPTAZZlM9j3hb3MkSuD4UVvdIdz1j7699bx8XFiau4_5hQ97WrIvlJoR2_c3-XAtIeqlznRpHszBXQThCaaPV4BzS2vg/s1600-h/Redis%252520Client_2013-06-28_08-58-48%25255B4%25255D.png)

  

  
*   **ZUNIONSTORE** Computes the union of numkeys sorted sets given by the specified keys, and stores the result in destination set. It is mandatory to provide the number of input keys (numkeys) before passing the input keys and the other (optional) arguments. Parameters needed:
  

  
*   destination ==> a set to hold the union operation result
  
*   numkeys ==> number of keys you are going to join.
  
*   weight ==> optional number(s) to multiply each score of the relative key by (if you have two keys, you can have two weights and son on)
  
*   aggregate ==> optional rule to specify how the results of the union are aggregated. This option defaults to SUM, where the score of an element is summed across the inputs where it exists. When this option is set to either MIN or MAX, the resulting set will contain the minimum or maximum score of an element across the inputs where it exists.

  

[![Redis 101 - Windows Live Writer_2013-06-28_12-29-14](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEju7SafK9ClMcPsCFysBEG7tVEGhgZGIz7hR2LiGEe4UoZ1f6oHpaXzxoqf2e85efzd41X90lORlFFgaHMiPt-jWh9-6wwHRmITsACRdfw1u_PYYkatlLy_2FJFZs_9OegoYsMZYCCJcA/?imgmax=800 "Redis 101 - Windows Live Writer_2013-06-28_12-29-14")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEizYXG_2ys9itVluYfL8iV4PZ7rewF-f3V9UaTE56fBrpSjuigSyUyZDSx_cuJEyhYS0-OLziW3WMhtnZnVPudd0KhO2Dyb0N0mt4xgVGNjzi0v8-q5h-87y3ZKXSvMv4gzEh4T3BVUyw/s1600-h/Redis%252520101%252520-%252520Windows%252520Live%252520Writer_2013-06-28_12-29-14%25255B3%25255D.png)

  

In the above example we prepared two sorted sets, sset1 with elements (1 “one” 2 “two”) , sset2 with elements (1 “one” 2 “two” 3 “three”). Then tell Redis to merge these two sets with the following parameters:

  

  

  
*   store the operation result in sorted set named _out_
  
*   we going to merge _2_ sorted sets, then provide them _sset1 sset2_.
  
*   we going to use _WEIGHTS_, then provide these weights _2 3_.

  

#### Hash

  

Hash is a collections object that can hold any number of key-value pairs.

  

  
*   **HMSET** store the key-value pairs into the hash (first parameter.
  
*   **HVALS** returns the values of a hash.
  
*   **HKEYS** returns the keys of a hash.
  
*   **HGET** returns the value of of a single key in a hash.

  

[![Redis Client_2013-06-28_10-09-24](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhwPslMAwg6Z2yqbKNlU8_sFhcyrXRf6T1LGmhv7RMtkC7IBfRridYmUzseXZ_sW26o5xnr_DmZPKMM-Fn9CSewWhdWnzzTVSZQIVj9TJmO4YQxJYODU-GyyGyqTXU-opR0VLHYoPBQiQ/?imgmax=800 "Redis Client_2013-06-28_10-09-24")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEjV9RvKa2Z4Tc9a8EW6r-k00aNu_gjPLTbx3w7ZUOoLVMxq79UD-Tjrso_0rezVttEYvaaqQQzUTipSJC0jpiYHd90ViQZF_TuPUo7liKllCPfTpyx9F5Y1eFCt2LbCl79OjFcrpyY6Kg/s1600-h/Redis%252520Client_2013-06-28_10-09-24%25255B4%25255D.png)

  

  
*   **HDEL** deletes a key-value pair from a hash.
  
*   **HSET** updates or adds a value at a specified key in a hash.
  
*   **HINCRBY** increments an integer field value by some count in a hash. It is possible to provide a negative value to decrement.
  
*   **HLEN** returns the number of fields in a hash.

  

[![Redis Client_2013-06-28_10-17-28](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEh6Tkr8RYopnfJ7Eo6Ygnixhdfv-Y5bE2mUwRbDs9xTgFhrGFZD_BS17wTtB_hyk1g4nP6HD-vIktbCo0oVX5WVhEMEcZj2Zi1arvXbqlmMFHgnbQrDbLMTZoxAQsHn0xpfL82bUltxIA/?imgmax=800 "Redis Client_2013-06-28_10-17-28")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEi9ZmTlgYC57wzOZ5puSjK-2cG7dIpG0SoUHBuDiFMi6VnD1YwjXYbcFZ6Mcil9JVtrMTldEmog8k6v7HKcWwGU5N5EPI70PyadEH1aoW-MudWBe8SArfmafzwhyOhgNLTtL-eiQ_43rQ/s1600-h/Redis%252520Client_2013-06-28_10-17-28%25255B6%25255D.png)

  
  
  
  

#### Database Namespaces

  

You may have been wondering, which database we working on. So far, we have interacted only with a single namespace. In Redis’s terminology, a namespace is called a _database_ and is keyed by a number. So far, we’ve always interacted with the default namespace 0 (also known as database 0).  

  
*   Use **SELECT** command to switch to different database and provide it a DB number. Setting a value to a key in one database will not affect any other key in other databases.

  

[![clip_image001](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhKi-VGqnhDVuhyphenhyphenAmjQOs0Dx2_bP6AgikzJDC9uKfyu-VtWR6s2aAKE50iplNqiGlVp6RwVyaPDSzqQ4Oq7LAnphvV39jk9bmqSVIGUv3Anc7TFidKrTOhZi648GqnNrHOG-Mc_u9tQ1g/?imgmax=800 "clip_image001")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgqLw3Ih0Ir6AP7YFmwDhp0zQ3YhgnCNX0XUPhKM7HsU2gsN0tjcjcA0u5OYqAJnCd2rjhZ84eY4-0Vu1iLqmEgPP0naSl-qo3sOyTj-pjAg0PfB-fjpGMsBxd6g11S9iNxn8tEH1sGRw/s1600-h/clip_image001%25255B6%25255D.png)

  

  
*   Since all databases are running in the same server instance, Redis lets us move keys from one database to another with the **MOVE** command.

  

[![clip_image002](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhsf36p8rbF2S2VI-doYpKuT8SAfGxkMASzHYFNz8MiGRCh8Lcvnwm72sI3BVPGXA1_d_h-FG5H2-3D0NOrJ7NH177E1xqBTcz3b7NmqvKpaLLdUT6imuimMh1Qnslcl6cxasl1pnaGuA/?imgmax=800 "clip_image002")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhZvbYe9PGa5bmEl7U4tkjedIJJpVRLyndZYhrauQnSkRclaXBxXYRCcylF1IfxAs5OWIJNUBRT3jy7T6yYeovZ3jDWUEou-uoOmajrM6dPBX-xVOQW17sJ6P2oCDJXvDMCRn2pQtflUw/s1600-h/clip_image002%25255B5%25255D.png)

  

This can be useful for running different applications against a single Redis server but still allow these multiple applications to trade data between each other.  

#### More commands

  

  
*   **RENAME** rename a key
  
*   **TYPE** return the type of a key’s value
  
*   **DEL** deletes a key-value pair
  
*   **FLUSHDB** removes all keys in database
  
*   **FLUSHALL** removes all keys from all databases on this server instance.

  

Redis’s data types and the complex queries it can perform make it much more than a standard key-value store. It can act as a stack, queue, or priority queue; can be an object store (via hashes); and even can perform complex set operations such as unions, intersections, and subtractions (diff). It provides many atomic commands, and for those multistep commands, it provides a transaction mechanism. It has a built-in ability to expire keys, which is useful as a cache.

  
  
  

In this post we just introduced Redis as a data structure server. In later post we going to cover the advanced features of Redis.