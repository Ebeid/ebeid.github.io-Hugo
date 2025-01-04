---
title: 'Python Notes – 10 : Threading'
date: 2009-03-28T07:55:00.000-05:00
draft: false
url: /2009/03/python-notes-10.html
tags: 
- Python
---

Welcome to our tenth note in the Python learning process. In this note we will talk about threading, threads communication and synchronization.

#### Threads basics

A running program is called a "process". Each process has memory, list of open files, stack, program counter, etc…. Normally, a process executes statements in a single sequence of control-flow.

The following commands create an entirely new process: fork(),system(), popen(), etc… This child process runs independently of the parent. Has own set of resources. There is minimal sharing of information between parent and child.

On the other side, a thread is kind of like a process (it’s a sequence of control-flow). Except that it exists entirely inside a process and shares resources. A single process may have multiple threads of execution. This is extremely useful when an application wants to perform many concurrent tasks on shared data.

#### Problems with Threads

*   Scheduling : To execute a threaded program, must rapidly switch between threads. This can be done by the user process (user-level threads) or Can be done by the kernel (kernel-level threads).
*   Resource Sharing : Since threads share memory and other resources, you must be very careful. Operation performed in one thread could cause problems in another.
*   Synchronization : Threads often need to coordinate actions because they can get "race conditions" (outcome dependent on order of thread execution). You will often need to use locking primitives (mutual exclusion locks, semaphores, etc...)

#### Python Threads

Python supports threads on the following platforms : Solaris, Windows, systems that support the POSIX threads library (pthreads).

Thread scheduling is tightly controlled by a global interpreter lock and scheduler. Only a single thread is allowed to be executing in the Python interpreter at once. Thread switching only occurs between the execution of individual byte-codes. Long-running calculations in C/C++ can block execution of all other threads. However, most I/O operations do not block.

Python threads are somewhat more restrictive than in C. Effectiveness may be limited on multiple CPUs (due to interpreter lock). Threads can interact strangely with other Python modules (especially signal handling). Not all extension modules are thread-safe.

#### The thread module

The thread module provides low-level access to threads, thread creation, and Simple mutex locks.

##### Creating a new thread

Thread.start\_new\_thread(func,\[args \[,kwargs\]\]) Executes a function in a new thread. Syntax like:

> import thread

> import time

> def print\_time(delay):

>     while 1:

>     time.sleep(delay)

>     print time.ctime(time.time())

> thread.start\_new\_thread(print\_time,(5,))      \# Start the thread

> \# Go do something else

> statements

> …….

The function print\_time will execute in a separate thread and will continue printing the time every 5 seconds. Python will continue executing our statements also.

##### Thread termination

Thread silently exits when the function returns. Thread can explicitly exit by calling thread.exit() or sys.exit(). Also uncaught exception causes thread termination (and prints error message). Other threads continue to run even if one had an error.

##### Simple locks

allocate\_lock(). Creates a lock object, initially unlocked. Only one thread can acquire the lock at once. Threads block indefinitely until lock becomes available.

> import thread

> lk = thread.allocate\_lock()

> def foo():

>     lk.acquire()         # Acquire the lock

>     …                     #critical section

>     lk.release()         # Release the lock

You might use this if two or more threads were allowed to update a shared data structure.

##### The main thread

When Python starts, it runs as a single thread of execution. This is called the "main thread." which is on its own and it’s not a big deal. However, if you launch other threads it has some special properties.

##### Termination of the main thread

If the main thread exits and other threads are active, the behavior is system dependent. Usually, this immediately terminates the execution of all other threads without cleanup. Cleanup actions of the main thread may be limited as well.

##### Signal handling

Signals can only be caught and handled by the main thread of execution. Otherwise you will get an error (in the signal module). The keyboard-interrupt can be caught by any thread (non-deterministically).

#### The threading module

The threading module is a high-level threads module that implements threads as classes (similar to Java). It provides an assortment of synchronization and locking primitives. It is built using the low-level thread module.

##### Creating a new thread (as a class)

When defining threads as classes all you need to supply is the following:

1.  A constructor that calls threading.Thread.\_\_init\_\_(self)
2.  A run() method that performs the actual work of the thread.

A few additional methods are also available

*   t.join(\[timeout\])    # Wait for thread t to terminate
*   t.getName()          # Get the name of the thread
*   t.setName(name)   # Set the name of the thread
*   t.isAlive()             # Return 1 if thread is alive.
*   t.isDaemon()         # Return daemonic flag
*   t.setDaemon(val)   # Set daemonic flag

Example: Inherit from the "Thread" class, provide required methods, and utilize the available methods.

> import threading, time

> class PrintTime(threading.Thread):

>     def \_\_init\_\_(self,interval):

>         threading.Thread.\_\_init\_\_(self)         # Required

>         self.interval = interval

>     def run(self):

>         while 1:

>         time.sleep(self.interval) 

>         print time.ctime(time.time())

> t = PrintTime(5)                                   # Create a thread object

> t.start()                                             # Start it

##### Daemon threads

Normally, interpreter exits only when all threads have terminated. However, a thread can be flagged as a daemon thread (runs in background). Interpreter really only exits when all non-daemonic threads exit. You can use this to launch threads that run forever, but which can be safely killed.

#### Threads synchronization

The threading module provides the following synchronization primitives:

*   Mutual exclusion locks
*   Reentrant locks
*   Conditional variables
*   Semaphores
*   Events

When would you need these threads synchronization mechanisms ?

*   When threads are updating shared data structures.
*   When threads need to coordinate their actions in some manner (events).

##### The Lock object

Provides a simple mutual exclusion lock. Only one thread is allowed to acquire the lock at once. Most useful for coordinating access to shared data.

> import threading

> data = \[ \]                            # Some data

> lck = threading.Lock()            # Create a lock

> def put\_obj(obj):

>     lck.acquire()

>     data.append(obj)

>     lck.release()

> def get\_obj():

>     lck.acquire()

>     r = data.pop()

>     lck.release()

>     return r

##### The RLock object

A mutual-exclusion lock that allows repeated acquisition by the same thread. Allows nested acquire(), release() operations in the thread that owns the lock. Only the outermost release() operation actually releases the lock.

> import threading

> data = \[ \]                  # Some data

> lck = threading.Lock()  # Create a lock

> def put\_obj(obj):

>     lck.acquire()

>     data.append(obj)

>     ...

>     put\_obj(otherobj)   # Some kind of recursion

>     ...

>     lck.release()

> def get\_obj():

>     lck.acquire()

>     r = data.pop()

>     lck.release()

>     return r

##### The Condition object

Creates a condition variable. Synchronization primitive typically used when a thread is interested in an event or state change. Could help in the producer-consumer classic problem.

> data = \[\]                      # Create data queue and a condition variable

> cv = threading.Condition()

> \# Consumer thread

> def consume\_item():

>     cv.acquire()              # Acquire the lock

>     while not len(data):

>         cv.wait()             # Wait for data to show up

>     r = data.pop()

>     cv.release()             # Release the lock

>     return r

> \# Producer thread

> def produce\_item(obj):

>     cv.acquire()            # Acquire the lock

>     data.append(obj)

>     cv.notify()              # Notify a consumer

>     cv.release()           # Release the lock

##### Semaphores

A locking primitive based on a counter. Each acquire() method decrements the counter. Each release() method increments the counter. If the counter reaches zero, future acquire() methods block. Common use: limiting the number of threads allowed to execute code

> sem = threading.Semaphore(5)      # No more than 5 threads allowed

> def fetch\_file(host,filename):

>     sem.acquire()                         # Decrements count or blocks if zero

>     ...

>     sem.release()                         # Increment count

##### Events

A communication primitive for coordinating threads. One thread signals an "event" while other threads wait for it to happen.

> e = Event()                       \# Create an event object

> def signal\_event():             \# Signal the event

>      e.set()

> def wait\_for\_event():         # Wait for event

>     e.wait()

> def clear\_event():             \# Clear event

>     e.clear()

Event is similar to a condition variable, but all threads waiting for event are awakened.

##### Locks and Blocking

By default, all locking primitives block until lock is acquired. In general, this is uninterruptible. Fortunately, most primitives provide a non-blocking option

> if not lck.acquire(0):

>      # lock couldn’t be acquired!

This works for Lock, RLock, and Semaphore objects. On the other hand condition variables and events provide a timeout option

> cv = Condition()

> ...

> cv.wait(60.0)                  # Wait 60 seconds for notification

On timeout, the function simply returns. Up to caller to detect errors.

#### The Queue Module

Provides a multi-producer, multi-consumer FIFO queue object. It can be used to safely exchange data between multiple threads.

*   q = Queue(maxsize)    # Create a queue.
*   q.qsize()                   # Return current size.
*   q.empty()                 # Test if empty.
*   q.full()                     # Test if full.
*   q.put(item)               # Put an item on the queue.
*   q.get()                    # Get item from queue

The Queue object also supports non-blocking put/get.

*   q.put\_nowait(item).
*   q.get\_nowait()

These raise the Queue.Full or Queue.Empty exceptions if an error occurs. Return values for qsize(), empty(), and full() are approximate.

#### Things to consider when using threads

*   Global interpreter lock makes it difficult to fully utilize multiple CPUs.
*   You don’t get the degree of parallelism you might expect.
*   Not all modules are thread-friendly. Example: gethostbyname() blocks all threads if nameserver down.

In this note we will talked about threading, threads communication and synchronization. In the upcoming notes, we will talk about more advanced topics in Python programming.