---
title: 'Python Notes 14: Advanced Network Operations'
date: 2009-05-15T21:07:00.001-05:00
draft: false
url: /2009/05/python-notes-14-advanced-network.html
---

We have explored the usual issues in network programming, both on client side and server side. In this post we will discuss some advanced topics in network programming.

**Half-Open Sockets**  
Normally, sockets are bidirectional—data can be sent across them in both directions. Sometimes, you may want to make a socket be unidirectional so data can only be sent in one direction. A socket that's unidirectional is said to be a half-open socket. A socket is made half-open by calling shutdown(), and that procedure is irreversible for that socket. Half-open sockets are useful when

*   You want to ensure that all data written has been transmitted. When shutdown() is called to close the output channel of a socket, it will not return until all buffered data has been successfully transmitted.
*   You want to have a way to catch potential programming errors that may cause the program to write to a socket that shouldn't be written to, or read from a socket that shouldn't be read from.
*   Your program uses fork() or multiple threads, and you want to prevent other processes or threads from doing certain operations, or you want to force a socket to be closed immediately.  
    

The socket. shutdown() call is used to accomplish all of these tasks.

The call to shutdown() requires a single argument that indicates how you want to shut down the socket. Its possible values are as follows:

*   0 to prevent future reads
*   1 to prevent future writes
*   2 to prevent future reads and writes

Once shut down in a given direction, the socket can never be reopened in that direction. Calls to shutdown() are cumulative; calling shutdown(0) followed by shutdown(1) will achieve the same effect as calling shutdown(2).

**Timeouts**

TCP connections can be held open indefinitely, even if there's no traffic flowing across them. Timeouts are useful  
for discovering error conditions or communication problems in some instances.

To enable timeout detection on a Python socket, you call settimeout() on the socket, passing it the number of seconds until a timeout is reached. Later, when you make a socket call and nothing has happened for that amount of time, a socket.timeout exception is raised.

**Transmitting Strings**  
One common problem that arises when sending data across the network is that of transmitting variable-length strings. When you read information from a TCP stream you don't know when the sender has finished giving you a piece of data unless you build some sort of indication into your protocol. There are two common approaches to solving this problem:

*   End-of-string identifier

*   Terminate the string with ‘\\n’ or NULL
*   Problem: Terminator might occur in the data if we transmit binary data.
*   Solutions:

*   Escape the identifier.
*   Encode data in base64
*   use different if found in data and send the new identifier before the data.

*   Leading fixed-length size indicator

*   Send a constant number of bytes containing the size of the string.
*   The “size” itself could be sent as characters or as binary data, characters are simpler, however you have to pad them to get a constant length.

**Using Broadcast Data**

When you broadcast a UDP packet, it's sent to all machines  
connected to your LAN. The underlying transport, such as Ethernet, will have a special mode that lets you do this without having to repeat the packet for each computer.  
On the receiver's side, when a broadcast packet is received, the kernel looks at the destination port number. If it has a process listening to that port, the packet is sent to that process. Otherwise, it's silently discarded. Therefore, simply sending out a broadcast packet will not harm or impact machines that don't have a server listening for it.  
Broadcast packets are often used for the following types of activities:

*   Automatic service discovery: For instance, a computer might send out a broadcast packet looking for all print servers of a particular type.
*   Automatic service announcements: A server providing a service for a LAN might periodically broadcast the availability of that service. Clients would listen for those broadcasts.
*   Searching for LAN computers that implement a specific protocol. For instance, a chat program might send out a broadcast packet looking for other people on the LAN with the same chat program. It might then compile a list and present it to the user.

To be able to broadcast data, you need to set the socket option on client and server as follows:

s.setsockopt(socket.SOL\_SOCKET, socket.SO\_BROADCAST, 1)

On the sender, instead of sending to a particular IP, send to ‘<broadcast>’

s.sendto(‘<broadcast>’,123)

In this post we dealt with a few advanced issues in network programming.