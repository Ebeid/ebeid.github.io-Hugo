---
title: 'Python Notes 13: Network servers'
date: 2009-05-15T18:38:00.001-05:00
draft: false
url: /2009/05/python-notes-13-network-servers.html
---

For a client, the process of establishing a TCP connection is a two-step process that includes the creation of the socket object and a call to connect() to establish a connection to the server. For a server, the process requires the following four steps:

1.  Create the socket object.
2.  Set the socket options (optional).
3.  Bind to a port (and, optionally, a specific network card).
4.  Listen for connections.

Example of these steps:

> host = '' # Bind to all interfaces  
> port = 51423  
> \# Step 1 (Create the socket object)  
> s = socket. socket(socket.AF\_INET, socket.SOCK\_STREAM)  
> \# Step 2 (Set the socket options)  
> s.setsockopt(socket.SOL\_SOCKET, socket.SOREUSEADDR, l)  
> \# Step 3 (Bind to a port and interface)  
> s.bind((host, port))  
> \# Step 4 (Listen for connections)  
> s.listen(5)

**Setting and Getting Socket Options**  
There are many different options that can be set for a socket. For general-purpose servers, the socket option of greatest interest is called SOREUSEADDR. Normally, after a server process terminates, the operating system reserves its port for a few minutes, thereby preventing any other process (even another instance of your server itself) from opening it until the timeout expires. If you set the SOREUSEADDR flag to true, the operating system releases the server port as soon as the server socket is closed or the server process terminates.This is done through:

s.setsockopt(socket.SOL\_SOCKET, socket.SOJEUSEADDR, l)

**Binding the Socket**

The next step is to claim a port number for the server. This process is called binding. To bind to a port, you call:  
s.bind((‘’, 111))

The first argument to bind() specifies the IP address to bind to it. It's generally left blank, which means "bind to all interfaces and addresses."

**Listening for Connections**  
The last step before actually accepting client connections is to call listen(). This call tells the operating system to prepare to receive connections. It takes a single parameter, which indicates how many pending connections the operating system should allow to remain in queue before the server actually gets around to processing them.

**Accepting Connections**

Most servers designed to run indefinitely and service multiple connections, this is usually done with a carefully designed infinite loop. Example:

> import socket  
> host = '' # Bind to all interfaces  
> port = 51423  
> s = socket.socket(socket.AF\_INET, socket.SOCKJTREAM)  
> s.setsockopt(socket.SOL\_SOCKET, socket.SO\_REUSEADDR, l)  
> s.bind((host, port))  
> print "Waiting for connections..."  
> s.listen(l)  
> while l:  
>     clientsock, clientaddr = s.acceptQ  
>     print "Got connection from", clientsock.getpeername()  
>     clientsock.close()

**Using User Datagram Protocol**

To use UDP on the server, you create a socket, set the options, and bind () just like with TCP However, there's no need for listen () or accept ()—just use recvf rom().  
This function actually returns two pieces of information: the received data, and the address and port number of the program that sent the data. Because UDP is connectionless, this is all you need to be able to send back a reply. Example, echo server:

> import socket, traceback  
> host = '' # Bind to all interfaces  
> port = 51423  
> s = socket.socket(socket.AF\_INET, socket.SOCK\_DCRAM)  
> s.setsockopt(socket.SOL\_SOCKET, socket.SO\_REUSEADDR, l)  
> s.bind((host, port))  
> while l:  
>     try:  
>         message, address = s.recvfrom(8l92)  
>         print "Cot data from", address  
>         s.sendto(message, address)   #Echo it back  
>     except (Keyboardlnterrupt, SystemExit):  
>         raise  
>     except:  
>         traceback.print\_exc()

In this post we have clarified some points in network servers.