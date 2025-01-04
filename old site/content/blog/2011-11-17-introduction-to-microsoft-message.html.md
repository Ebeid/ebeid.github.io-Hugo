--- 
title: "An introduction to Microsoft Message Queuing" 
date: '2011-11-17T06:49:00.002-06:00' 
tags: 
    - MSMQ 
modified_time: '2011-11-27T17:37:29.398-06:00' 
thumbnail: http://lh3.ggpht.com/-iRV60VxSKZo/TsUC7ooDFjI/AAAAAAAAAKs/2gB3XueW\_ZU/s72-c/MSMQ1\_thumb%25255B1%25255D.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-3381795044346782183
blogger_orig_url: http://ebeid-soliman.blogspot.com/2011/11/introduction-to-microsoft-message.html
---

**What is MSMQ ?** Message Queuing (also known as MSMQ) is a messaging
infrastructure and a development tool for creating distributed messaging
applications for Microsoft Windows operating systems. Applications
developed for Message Queuing send messages to queues, which are
temporary storage locations, from which messages can proceed to their
final destination as conditions permit.

**Installing MSMQ** The procedures to install MSMQ on Windows Server
2008, Winows Server 2008 R2, Windows 7, Windows Vista, Windows XP, and
Windows Server 2003 are available
[here](http://msdn.microsoft.com/en-us/library/aa967729.aspx "Installing Message Queuing (MSMQ)")

**Basic Messaging**

[<img src="http://lh3.ggpht.com/-iRV60VxSKZo/TsUC7ooDFjI/AAAAAAAAAKs/2gB3XueW_ZU/MSMQ1_thumb%25255B1%25255D.jpg?imgmax=800" title="MSMQ1" width="555" height="337" alt="MSMQ1" />](http://lh4.ggpht.com/-BIn-NR6GGNQ/TsUC7bfFDKI/AAAAAAAAAKo/nn1sOeBP1ow/s1600-h/MSMQ1%25255B3%25255D.jpg)

The image shows the basic messaging scenario. You have two applications:
a sending application and a receiving application. A sending application
prepares a message and puts it into a queue. A message can be any piece
of information that the receiving application understands. The receiving
application receives the message from the queue and processes it. One
thing to note here is that the sender and the receiver are not tightly
coupled and they can work without the other application being online.

**Messaging in .Net** To build a messaging application we need to create
at least three components: queue, application to send messages, and
another application to receive these messages.

**Types of queues** The basic types of MSMQ queues are: private and
public. Public queues are those that are published in the active
directory. So, applications running on different servers throughout the
network can find and use public queues through the active directory.
Private queues on the other hand are available locally on a particular
machine and are not published in the active directory.

**Creating a Queue** Queues can be created either programmatically or
through the computer management snap-in (if you installed MSMQ on your
machine).

-   **Programmatically** The System.Messaging.M`essageQueue `class
    provides all the necessary functionality to work with and manipulate
    MSMQ queues. It is like a wrapper around message queuing.
    MessageQueue.Create(path) creates a non-transactional message queue
    at the specified path (we will talk about transactional and
    non-transactional queues later). For public queues, path is
    MachineName\\QueueName. For private queues,
    MachineName\\Private$\\QueueName. You can use "." for the local
    computer. Code should look like:

    MessageQueue privateQueue = MessageQueue.Create(".\\Private$\\privateQueue"); 

  

  
  

-   **Through the computer management snap-in** Open the computer
    management snap-in (right click computer, then manage). Navigate to
    Services and Applications, then Message Queuing. Right click on
    Private Queues –&gt; New –&gt; Private Queue. Or right click on
    public Queues –&gt; New –&gt; Public Queue.

  
  

[<img src="http://lh6.ggpht.com/-za1LFgBEpts/TsVgEIgQ0vI/AAAAAAAAAK4/6x4JoPYdqzY/MMC_thumb%25255B3%25255D.jpg?imgmax=800" title="MMC" width="743" height="559" alt="MMC" />](http://lh6.ggpht.com/--VAHZ6yAB10/TsVgDjIqZ8I/AAAAAAAAAKw/GdRORuiOjfI/s1600-h/MMC%25255B5%25255D.jpg)

  
  

**Sending a message** Use Send() method of your previously created
MessageQueue object like so

  

  
  

  

    privateQueue.Send("Message Body (could be any managed object)", "Message Label");

  

  
  

**Receiving a message** There are two types of operations with respect
to reading a message fom the Queue: Peeking and Receiving. When we
receive a message from the queue, the message is removed from the queue.
Peeking is similar to Receiving but here the message is not removed from
the queue. Code could look like

  

  
  

  

    MessageQueue anotherPrivateQueue = new MessageQueue(".\\Private$\\privateQueue");

  
  

    System.Messaging.Message msg = anotherPrivateQueue.Receive();

  

  
  

**Additional Considerations** before writing the first complete
messaging application

  
  

-   You have to check if there is already a Message Queuing queue with
    the same name before creating your new queue. Use
    MessageQueue.Exists(path) to check for queue existence.
-   When receiving a message and before accessing its body, you have to
    set the Formatter property of the Message object. There is a lot of
    built-in formatters. For now, we can use XMLFormatter.

  
  

Now, let’s get things together into a “Hello, World” example. Open
Visual Studio, New project, Windows forms. All reference to
System.Messaging namespace. Then edit your code to look like so:

  
  




    using System;

    using System.Collections.Generic;

    using System.Linq;

    using System.Text;

    using System.Messaging;



    namespace MSMQ_Demo

    {

        class Program

        {

            static void Main(string[] args)

            {

                try

                {

                    MessageQueue privateQueue;

                    if (!MessageQueue.Exists(".\\Private$\\privateQueue"))

                        privateQueue = MessageQueue.Create(".\\Private$\\privateQueue");

                    else

                        privateQueue = new MessageQueue(".\\Private$\\privateQueue");



                    privateQueue.Send("Hello, World !", "Message Label");

                    MessageQueue anotherPrivateQueue = new MessageQueue(".\\Private$\\privateQueue");

                    System.Messaging.Message msg = anotherPrivateQueue.Receive();

                    msg.Formatter = new System.Messaging.XmlMessageFormatter(new Type[1] { typeof(string) });

                    Console.WriteLine(msg.Body.ToString());

                }

                catch (Exception ex)

                {

                    Console.WriteLine(ex.Message);

                }

            }

        }

    }

  
  

If you run the project, you will see a message-box displaying “Hello,
World !”. This message content created by had been sent from MSMQ queue,
received by another MSMQ, and processed. In our example both the sending
and the receiving queues exist in the same application for the sake of
simplicity. In real world applications they reside in very different
areas.

This is a very basic introduction to MSMQ and non-transactional queues.
In future posts, we will explore more advanced topics in MSMQ.
