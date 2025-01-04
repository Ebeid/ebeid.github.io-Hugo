---
title: 'Python Notes 11 : Introduction to Network Programming'
date: 2009-05-15T03:00:00.001-05:00
draft: false
url: /2009/05/python-notes-11-introduction-to-network.html
---

**Network Overview**

Python provides a wide assortment of network support.

*   Low-level programming with sockets (if you want to create a protocol).
*   Support for existing network protocols (HTTP, FTP, SMTP, etc...).
*   Web programming (CGI scripting and HTTP servers).
*   Data encoding

**Network Basics: TCP/IP**

Python’s networking modules primarily support TCP/IP.

*   TCP - A reliable connection-oriented protocol (streams).
*   UDP - An unreliable packet-oriented protocol (datagrams).

TCP is the most common (HTTP, FTP, SMTP, etc...). Both protocols are supported using "sockets".

A socket is a file-like object. Allows data to be sent and received across the network like a file. But it also includes functions to accept and establish connections. Before two machines can establish a connection, both must create a socket

**Network Basics: Ports**

In order to receive a connection, a socket must be bound to a port (by the server). A port is a number in the range 0-65535 that’s managed by the OS. Used to identify a particular network service (or listener). Ports 0-1023 are reserved by the system and used for common protocols:

*   FTP Port 20
*   Telnet Port 23
*   SMTP (Mail) Port 25
*   HTTP (WWW) Port 80

Ports above 1024 are reserved for user processes.

**Socket programming in a nutshell**

*   Server creates a socket, binds it to some well-known port number, and starts listening.
*   Client creates a socket and tries to connect it to the server (through the above port).
*   Server-client exchange some data.
*   Close the connection (of course the server continues to listen for more clients).

**Socket Programming Example**

**The socket module**

Provides access to low-level network programming functions. The following example is a simple server that returns the current time

> import time, socket

> s = socket(AF\_INET, SOCK\_STREAM)#Create TCP socket

> s.bind(("",8888))                      #Bind to port 8888

> s.listen(5)                                #Start listening

> while 1:

>     client,addr = s.accept()          #Wait for a connection

>     print "Got a connection from ", addr

>     client.send(time.ctime(time.time())) #Send time back

>     client.close()

**Notes**: The socket first opened by server is not the same one used to exchange data.Instead, the accept() function returns a new socket for this (’client’ above).listen() specifies max number of pending connections

The following example is the client program for the above time server which connect to time server and get current time.

> from socket import \*

> s = socket(AF\_INET,SOCK\_STREAM) #Create TCP socket

> s.connect(("google.com",8888))       #Connect to server

> tm = s.recv(1024)                #Receive up to 1024 bytes

> s.close()                             # Close connection

> print "The time is", tm

**Notes:** Once connection is established, server/client communicate using send() and recv(). Aside from connection process, it’s relatively straightforward. Of course, the devil is in the details. And are there ever a LOT of details.

**The Socket Module**

The socket module used for all low-level networking, creation and manipulation of sockets, and general purpose network functions (hostnames, data conversion, etc...). It’s a direct translation of the BSD socket interface.

**Utility Functions**

*   socket.gethostbyname(hostname) # Get IP address for a host
*   socket.gethostname() # Name of local machine
*   socket.ntohl(x) # Convert 32-bit integer to host order
*   socket.ntohs(x) # Convert 16-bit integer to host order
*   socket.htonl(x) # Convert 32-bit integer to network order
*   socket.htons(x) # Convert 16-bit integer to network order

**Comments:** Network order for integers is big-endian. Host order may be little-endian or big-endian (depends on the machine).

The socket(family, type, proto) function creates a new socket object. _F__amily_ is usually set to AF\_INET. _T__ype_ is one of:

*   SOCK\_STREAM          Stream socket (TCP)
*   SOCK\_DGRAM           Datagram socket (UDP)
*   SOCK\_RAW               Raw socket

_Proto_ is usually only used with raw sockets:

*   IPPROTO\_ICMP
*   IPPROTO\_IP
*   IPPROTO\_RAW
*   IPPROTO\_TCP
*   IPPROTO\_UDP

**Socket methods**

*   s.accept()                  # Accept a new connection
*   s.bind(address)          # Bind to an address and port
*   s.close()                    # Close the socket
*   s.connect(address)      # Connect to remote socket
*   s.fileno()                   # Return integer file descriptor
*   s.getpeername()         # Get name of remote machine
*   s.getsockname()    #Get socket address as (ipaddr,port)
*   s.getsockopt(...)        # Get socket options
*   s.listen(backlog)        # Start listening for connections
*   s.makefile(mode)   # Turn socket into a file like object
*   s.recv(bufsize)           # Receive data
*   s.recvfrom(bufsize)    # Receive data (UDP)
*   s.send(string)           # Send data
*   s.sendto(string, address)    # Send packet (UDP)
*   s.setblocking(flag)   #Set blocking or nonblocking mode
*   s.setsockopt(...)      #Set socket options
*   s.shutdown(how)     #Shutdown one or both halves of connection

There are a huge variety of configuration/connection options. You’ll definitely want a good reference at your side

**The SocketServer Module**

Provides a high-level class-based interface to sockets. Each protocol is encapsulated in a class (TCPServer, UDPServer, etc.). It also provides a series of handler classes that specify additional server behavior.

To create a network service, need to inherit from both a protocol and handler class. Example, the same time server we done before:

> import SocketServer

> import time

> \# This class actually implements the server functionality

> class TimeHandler(SocketServer.BaseRequestHandler):

>     def handle(self):

>         self.request.send(time.ctime(time.time()))

> \# Create the server

> server = SocketServer.TCPServer("",8888),TimeHandler)

> server.serve\_forever()

**Notes:** The module provides a number of specialized server and handler types. Ex: ForkingTCPServer, ThreadingTCPServer, StreamRequestHandler, etc.

**Common Network Protocols**

Modules are available for a variety of network protocols:

*   ftplib                FTP protocol
*   smtplib             SMTP (mail) protocol
*   nntplib              News
*   gopherlib          Gopher
*   poplib               POP3 mail server
*   imaplib             IMAP4 mail server
*   telnetlib            Telnet protocol
*   httplib              HTTP protocol

These modules are built using sockets, but operate on a very low-level. Working with them requires a good understand of the underlying protocol. But can be quite powerful if you know exactly what you are doing

**The httplib Module**

Implements the HTTP 1.0 protocol and can use to talk to a web server.

HTTP in two bullets:

*   Client (e.g., a browser) sends a request to the server

> GET /index.html HTTP/1.0

> Connection: Keep-Alive

> Host: [www.python.org](http://www.python.org)

> User-Agent: Mozilla/4.61 \[en\] (X11; U; SunOS 5.6 sun4u)

> \[blank line\]

*   Server responds with something like this:

> HTTP/1.0 200 OK

> Content-type: text/html

> Content-length: 72883

> Headers: blah

> \[blank line\]

> Data

> ...

**Making an HTTP connection**

> import httplib

> h = httplib.HTTP("www.python.org")

> h.putrequest(’GET’,’/index.html’)

> h.putheader(’User-Agent’,’Lame Tutorial Code’)

> h.putheader(’Accept’,’text/html’)

> h.endheaders()

> errcode,errmsg, headers = h.getreply()

> f = h.getfile()        # Get file object for reading data

> data = f.read()

> f.close()

You should understand some HTTP to work with httplib.

**The urllib Module**

A high-level interface to HTTP and FTP which provides a file-like object that can be used to connect to remote servers

> import urllib

> f = urllib.urlopen("http://www.python.org/index.html")

> data = f.read()

> f.close()

**Utility functions**

*   urllib.quote(str)         # Quotes a string for use in a URL
*   urllib.quote\_plus(str)    # Also replaces spaces with ’+’
*   urllib.unquote(str)         # Opposite of quote()
*   urllib.unquote\_plus(str)  # Opposite of quote\_plus()
*   urllib.urlencode(dict)
*   \# Turns a dictionary of key=value pairs into a HTTP query-string

Examples

urllib.quote("ebeid@ieee")         #Produces "ebeid%40ieee"

urllib.unquote("%23%21/bin/sh")    #Produces "/bin/sh"

**The urlparse Module**

Contains functions for manipulating URLs

*   URL’s have the following general format

> scheme:/netloc/path;parameters?query#fragment

*   urlparse(urlstring) - Parses a URL into components

> import urlparse

> t = urlparse.urlparse("http://www.python.org/index.html")

> #Produces (’http’,’[www.python.org’,’/index.html](http://www.python.org’,’/index.html)’,’’,’’,’’)

*   urlunparse(tuple) - Turns tuple of components back into a URL string

> url = urlparse.urlunparse((’http’,’www.python.org’,’foo.html’, ’bar=spam’,’’))

> \# Produces "[http://www.python.org/foo.html?bar=spam](http://www.python.org/foo.html?bar=spam)"

*   urljoin(base, url) - Combines a base and relative URL

> urlparse.urljoin("http://www.python.org/index.html","help.html")

> \# Produces "[http://www.python.org/help.html](http://www.python.org/help.html)"

In this note we explored horizontally the network programming capabilities of Python. Every single module and topic mentioned here, needs multiple posts to cover it. In the upcoming posts, we will dig into network programming in detail.