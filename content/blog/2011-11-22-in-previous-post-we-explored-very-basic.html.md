--- 
title: "An introduction to Microsoft Message Queuing–Part 2" 
date: '2011-11-22T11:52:00.004-06:00' 
tags: 
    - MSMQ 
modified_time: '2011-12-01T12:36:07.637-06:00' 
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-5646394697131614938
blogger_orig_url: http://ebeid-soliman.blogspot.com/2011/11/in-previous-post-we-explored-very-basic.html
---

In the [previous
post](http://ebeid-soliman.blogspot.com/2011/11/introduction-to-microsoft-message.html "An introduction to Microsoft Message Queuing"),
we explored very basic concepts of MSMQ. We used non-transactional queue
to send and receive a message. In this post we will try to dive more
into Message Queuing Queues.

Simply, queues are logical containers that Message Queuing uses to store
and later forward messages, providing the bases for the loosely coupled
aspects of Message Queuing. Queues can be created by applications and by
Message Queuing. Queues created by applications or by users in an MMC
snap-in are referred to as ***application queues***. Queues created by
Message Queuing are referred to as ***system-generated queues*** (we
will talk about system- generated queues in another post).

Depending on the service provided by the queue, **application queues**
can be <span class="underline">public</span> or <span
class="underline">private</span>, and they can be <span
class="underline">transactional</span> or <span
class="underline">nontransactional</span>.

**Application queues** can play any of the following roles:

-   Destination queues : any queue used to send/receive messages between
    applications.
-   Administration queues : used for *acknowledgment messages* returned
    by Message Queuing or *connector applications*.
-   Response queues : used by receiving applications to return *response
    messages* to the sending application.
-   Report queues : used to store *report messages* returned by Message
    Queuing.

##### Destination Queues

Destination queues are any queue used to send/receive messages between
applications. The sending application on computer 1 sends the messages
to the queue and the receiving application on computer 2 reads the
messages from the queue. Typically, destination queues are located on
the same computer as the receiving application in order to minimize
network traffic.

**<span class="underline">Public Versus Private Queues</span>** The
decision to use public or private destination queues depends primarily
on whether you want other applications to be able to locate the queues
or not. Message Queuing registers private queues locally by storing a
description of each queue in a separate file in the local queue storage
(LQS) folder on the local computer (the default Lqs folder is
%windir%\\System32\\MSMQ\\Storage\\Lqs). Also a description of each
public queue created on the local computer is also stored locally in a
separate file in the Lqs folder.

Adv. of Public Queues:

-   Registered in the directory service, so it can be located by other
    Message Queuing applications.
-   Persistent and its registration information can be backed up.

Adv. of Private Queues:

-   Requires minimal directory service overhead(faster to create, no
    latency, and no replication)
-   Can be created and deleted when the *directory service* is not
    working
-   Can be accessed directly by name without query the directory
    service.

Div. of Private Queues:

-   It is registered on local computer, so it is properties cannot be
    obtained by Message Queuing applications running on remote
    computers. Private queues can be exposed to other applications by
    making the location of the private queue known to the applications.
    To distribute the location of a private queue, an application can
    send the format name of the private queue as the response queue
    property of a message.

**<span class="underline">Transactional Versus Nontransactional
Queues</span>** The decision to use transactional or nontransactional
queues is based on whether the applications accessing the queue will be
sending and receiving messages within the context of a transaction. So,
what is a transaction ? a transaction is to execute a multiple-steps
process such that either all or none of the steps will complete. In
reality, transactions are handled by rolling back any steps that have
already occurred if the entire transaction is not completed
successfully.

When sending messages, only transactional queues can accept messages
sent in the context of a transaction. These messages are also referred
to as transactional messages. In a similar way, nontransactional queues
can only accept messages sent outside the context of a transaction. Note
that only transactional messages are delivered with
exactly-once-delivery (EOD) guarantees.

When receiving messages, only local transactional queues can be accessed
within the context of a transaction. The transactional queue must be
local to the receiving application. On the other hand, nontransactional
queues can be accessed within or outside of a transaction. Also,
transactional queues, local or remote, can be accessed outside of a
transaction (because we ask it to do less than what it can do).

If you just want to be able to recover lost messages, don’t use
transactional queues. You can set the *Recoverable* property of a every
message you sent. Or you can sent the queue property
DefaultPropertiesToSend.Recoverable to true.

##### Creating a Transactional Queue

-   Through the snap in : just check the check-box Transactional below
    the queue name textbox.
-   Programmatically : just like privateQueue =
    MessageQueue.Create(".\\\\Private$\\\\privateQueue", true);

MessageQueue have a property called Transactional that you can check to
ensure that the queue is transactional

MSMQ supports two types of transactions: Internal and External.

##### Internal Transactions

Class MessageQueueTransaction can be used to Begin(), Commit(), Abort()
the transaction. It also can be passed through Send() and Receive()
methods to that operation falls under a transaction. The class also
exposes a Status property to give the transaction status. Transaction
status can be one of:

-   Initialized : The transaction has been initialized but not yet
    started.
-   Pending : The transaction has been began but not committed or
    aborted yet.
-   Committed : The transaction has been committed.
-   Aborted : The transaction has been aborted.

**Transaction Types** when sending or receiving using MessageQueue class
through transactional queues, you could pass one of the values in
MessageQueueTransactionType enumeration. This specifies how you would
like to interact with the queue. These values are:

-   Single : each queue operation will be doine in a separate internal
    transaction.
-   None : enable you to receive a message from a transactional queue,
    but outside a transaction. It also enables us to send a
    transactional message to a non-transactional queue.
-   Automatic : used with external transactions to direct the send or
    receive operations to use an already existing transaction context.

Now lets compile these pieces into one example to get sense of what
internal transactional queues means.

    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Messaging;

    namespace MSMQ_Demo3
    {
     class Program
     {
         static void Main(string[] args)
         {
             MessageQueueTransaction mqTran = new MessageQueueTransaction();
             MessageQueue queueA = MessageQueue.Create(".\\Private$\\TranQueueA", true);
             MessageQueue queueB = MessageQueue.Create(".\\Private$\\TranQueueB", true);
             mqTran.Begin();
             try
             {
                 queueA.Send("Message A", "Label A", mqTran );
                 queueB.Send("Message B", "Label B", mqTran );
                 mqTran.Commit();
             }
             catch(Exception ex)
             {

             mqTran.Abort();
                 Console.WriteLine(ex.Message);
             }             

             MessageQueue queueC = new MessageQueue(".\\Private$\\TranQueueA");
             MessageQueue queueD = new MessageQueue(".\\Private$\\TranQueueB");
             string strMsg = "";
             mqTran.Begin();
             try
             {
                 Message msg = queueC.Receive(mqTran);
                 msg.Formatter = new XmlMessageFormatter(new Type[1] { typeof(string) });
                 strMsg = msg.Body.ToString();
                 msg = queueD.Receive(mqTran);
                 msg.Formatter = new XmlMessageFormatter(new Type[1] { typeof(string) });
                 strMsg += " \n ";
                 strMsg += msg.Body.ToString();
                 Console.WriteLine(strMsg);
                 mqTran.Commit();
             }
             catch (Exception ex)
             {
                 mqTran.Abort();
                 Console.WriteLine(ex.Message);
             }
             Console.WriteLine();
         }
      
     }
    }

  
  
<span class="Apple-style-span"
style="font-family: Georgia, serif; font-size: 16px; white-space: normal; ">In
this example we created two transactional queues, send two messages to
them. Then we received these messages. Both the sending and receiving
done in a transaction that commits only after the success of all
operations. If any errors happened, we abort the whole transaction and
rollback all operations done in it.</span>

In future posts we will talk more about MSQM details.
