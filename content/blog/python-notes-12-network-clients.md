---
title: 'Python Notes 12 : Network clients'
date: 2009-05-15T18:17:00.001-05:00
draft: false
url: /2009/05/python-notes-12-network-clients.html
---

After we have explored the basics of network programming in brief in the [previous post](http://ebeid-soliman.blogspot.com/2009/05/python-notes-11-introduction-to-network.html), we will discuss network clients in more details in this post.

**Understanding Sockets**  
Sockets are an extension to the operating system's I/O system that enable communication between processes and machines. It can be treated the same as standard files, with the same interface methods so in many cases, a program need not know whether it's writing data to a file, the terminal, or a TCP connection. While many files are opened with the open () call, sockets are created with the socket () call and additional calls are needed to connect and activate them.

**Creating Sockets**

For a client program, creating a socket is generally a two-step process.

1.  Create the actual socket object.
2.  Connect the socket to the remote server.

When you create a socket object, you need to tell the system two things:

*   The communication type: the underlying protocol used to transmit data. Examples of protocols include IPv4 (current Internet standard), IPv6 (future Internet standard), IPX/ SPX (NetWare), and AFP (Apple file sharing). By far the most common is IPv4.
*   The protocol family: defines how data is transmitted.  
    For Internet communications, which make up the bulk of this book, the communication type is almost always AF\_INET (corresponding to IPv4). The protocol family is typically either:
    *   SOCK\_STREAM for TCP communications or
    *   SOCK\_DGRAM for UDP communications

For a TCP connection, creating a socket generally uses  
code like this:

s = socket.socket(socket.AF\_INET, socket.SOCK\_STREAM) To connect the socket, you'll generally need to provide a tuple containing the remote hostname or IP address and the remote port. Connecting a socket typically looks like this:  
s.connect(("www.example.com", 80))

**Finding the port number**

Most operating systems ship with a list of well-known server port numbers which you can query. On windows systems, you can find this file at C:\\Windows\\System32\\drivers\\etc\\services. To query this list, you need two parameters:

*   A protocol name
*   A port name.

This query is like:

> \>>>print socket.getservbyname(‘ftp’,’tcp’)

> 21

You didn't have to know in advance that FTP uses port 80.

**Getting Information from a Socket**  
Once you've established a socket connection, you can find out some useful information from it.

s.getsockname() #Get your IP address and port number

s.getpeername() #Get the remote machine IP address and port number

**Socket Exceptions**

Different network calls can raise different exceptions when network errors occur. Python's socket module actually defines four possible exceptions:

*   socket.error for general I/O and communication problems.
*   socket.gaierror for errors looking up address information
*   socket.herror for other addressing errors.
*   socket.timeout for handling timeouts that occur after settimeout() has been called on a socket.

**Complete Example**

The example program takes three command-line arguments: a host to which it will connect, a port number or name on the server, and a file to request from the server. The program will connect to the server, send a simple HTTP  
request for the given filename, and display the result. Along the way, it exercises care to handle various types of potential errors.

> import socket, sys  
> host = sys.argv\[l\]  
> textport = sys.argv\[2\]  
> filename = sys.argv\[3\]  
> try:  
>     s = socket.socket(socket.AF\_INET,socket.SOCK\_STREAM)  
> except socket.error, e:   
>     print "Strange error creating socket: %s" % e   
>     sys.exit(l)  
>     # Try parsing it as a numeric port number.  
> try:  
>     port = int(textport)  
> except ValueError:  
>     # That didn't work, so it's probably a protocol name.  
>     # Look it up instead,  
> try:  
>     port = socket.getservbyname(textport, 'tcp')  
>     except socket.error, e:  
>     print "Couldn't find your port: %s" % e  
>     sys.exit(i)

> try:  
>     s.connect((host, port))  
> except socket.gaierror, e:  
>     print "Address-related error connecting to server: %s" % e  
>     sys.exit(i)  
> except socket.error, e:  
>     print "Connection error: %s" % e  
>     sys.exit(l)  
> try:  
>     s.sendall("CET %s HTTP/1.0\\r\\n\\r\\n" % filename)  
> except socket.error, e:  
>     print "Error sending data: %s" % e  
>     sys.exit(i)  
> while 1:  
>     try:  
>         buf = s.recvB048)  
>     except socket.error, e:  
>         print "Error receiving data: %s" % e  
>         sys.exit(l)  
>     if not len(buf):  
>         break  
>     sys.stdout.write(buf)

**Using User Datagram Protocol**

In UDP there is no sufficient control over how data is sent and received. Working with UDP clients differs than TCP clients in the following:

*   When create the socket ask for SOCKDGRAM  
    instead of SOCKSTREAM; this indicates to the operating system that the socket will  
    be used for UDP instead of TCP communications.
*   When call socket.getservbyname(), pass ‘udp’ instead of ‘tcp’.

In this post we discussed network clients in a little bit depth. In the next post we will discuss network servers.