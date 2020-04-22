--- 
title: "Introduction to Peer-to-Peer Computing" 
date: '2009-05-24T23:10:00.001-05:00' 
tags: 
    - Peer-to-Peer 
modified_time: '2009-05-24T23:10:15.906-05:00' 
thumbnail: http://lh6.ggpht.com/\_R1exOFT\_lVs/ShoaJVKe6zI/AAAAAAAAAEs/VPkR3Vhciws/s72-c/P2P\_thumb%5B2%5D.jpg?imgmax=800
blogger_id: tag:blogger.com,1999:blog-59384554657271185.post-6631312720756478463
blogger_orig_url: http://ebeid-soliman.blogspot.com/2009/05/introduction-to-peer-to-peer-computing.html
---

Peer-to-peer (P2P) has become a buzzword that subsumes concepts used in
communication technologies, distributed system models, applications,
platforms, etc. It is not a particular initiative, nor architecture or
specific technology; it rather describes a set of concepts and
mechanisms for decentralized distributed computing and direct
peer-to-peer information and data interchange.

So, **What is Peer-to-Peer Computing ?**

There is no one definition of P2P.

-   P2P is a class of applications that takes advantages of resources
    available at the edges of the internet.
-   The sharing of computer resources and services by direct exchange
    between systems.
-   In Peer-to-Peer computing, each computer can serve the function of
    both client and server. Any computer in the network can initiate
    questions (as a client), receive questions and transmit data (as a
    server).

We could conclude these definitions by proposing the following
definition.

> P2P computing is a distributed computing architecture with the
> following properties:

-   Resource sharing
-   Dual client/server role of network nodes.
-   Decentralization/Autonomy
-   Scalability
-   Robustness/Self-Organization

Once you understood that P2P is a distributed computing architecture,
you might be started asking: **Why P2P architecture since we have
Client/Server architecture ?**

Client/Server architecture is a well known, powerful architecture. In
it, the server is the data and functionality source, and clients
requests data and processing from it. Although Client/Server
architecture is very successful (www \[HTTP\], FTP, Web services, etc…),
it have some issues; which are:

-   Scalability is hard to achieve.
-   Presents a single point of failure.
-   Requires administration.
-   Didn’t utilize the resources at the network edges (clients).

Although many of these issues had been solved with many solutions, P2P
tried to address these issues in a new and very different way. The
following figure emphasizes the general difference between P2P and
client/server architecture models.

[<img src="http://lh6.ggpht.com/_R1exOFT_lVs/ShoaJVKe6zI/AAAAAAAAAEs/VPkR3Vhciws/P2P_thumb%5B2%5D.jpg?imgmax=800" title="P2P" width="540" height="268" alt="P2P" />](http://lh4.ggpht.com/_R1exOFT_lVs/ShoaHaBowYI/AAAAAAAAAEo/SRIc5hmTU70/s1600-h/P2P%5B4%5D.jpg)

**Why P2P Now ?**

Since the concepts that underlie the P2P computing model is not a new
computing concept, it is reasonable to ask why the P2P model has burst
on the scene at this time. This happened due to many recent changes in
the computing world:

-   The ubiquity of connected computers has come close to enabling
    anywhere, anytime access to the Net and its resources.
-   The critical mass of computer users.
-   Improvements in communications bandwidth, still on a fast-track
    growth curve, make it possible to move large amounts of data and
    rich media content from one location to another.
-   Today’s PCs are sufficiently robust, in terms of processing power
    and storage capacity, to handle the extra services required in a P2P
    environment.
-   the emergence of complementary technologies, including recent
    advances in wireless and software agents that provide more avenues
    for interesting P2P applications.

While all of these are necessary conditions for P2P computing, something
more is required. History shows that a trigger is needed for a new
technology to really take off. In the computer industry this is often
referred to as a “killer app” The electronic spreadsheet triggered the
proliferation of the PC, and the Mosaic browser triggered the
transformation of the Internet into the World Wide Web.

The P2P computing model found its trigger with **Napster**, followed by
**Gnutella**. Their huge popularity got everyone talking about P2P and
helped further stimulate other P2P applications such as **Freenet** and
**<SETI@home>**.

**P2P Benefits**

-   Efficient use of resources.
    -   Unused bandwidth, storage, processing power at the edge of the
        network.
-   Scalability
    -   Consumers of resources also donate resources.
    -   Aggregate resources grow naturally with utilization.
-   Reliability
    -   Replicas of data.
    -   Geographic distribution
    -   No single point of failure.
-   Ease of administration
    -   Nodes are self organize.
    -   No need to deploy servers to satisfy demand.
    -   Built-in fault tolerance, replication, and load balancing.

Since P2P is not well-defined and it is only defined by set of
characteristics and properties that are attributed to P2P systems, we
will discuss some of common characteristics of P2P systems. This does
not imply that every P2P system has to comply with all of these
characteristics or even with a fixed number of them. These are general
features that can be used to identify P2P systems.

1.  **Structural Characteristics**
    1.  **Decentralization**
        1.  This includes distributed storage, processing, information
            sharing, etc..
        2.  **Advantage** 
            1.  increased extensibility.
            2.  Higher system availability and resilience.
        3.  **Disadvantage**
            1.  Difficult to get or maintain a global view of the system
                state.
            2.  System behavior is not deterministic.
            3.  Interoperability is a big issue.
    2.  **Self-organizing**
        1.  The different system components work together without any
            central management instance assigning roles and tasks.
        2.  **Disadvantage**
            1.  It is difficult to determine the system structure or
                predict the system behavior as long as no system-wide,
                governing policies apply.
    3.  **Fault-tolerance**
        1.  Since there is no central point of failure.
            1.  The system performance variance due to nodes leaves and
                joins might imply that there is a lack of consistency.
2.  **Operational Characteristics**
    1.  **Transparency**
        1.  This means transparency to the application or user in forms
            of communications, location, access, replication
            transparency for data and information.  Also the scale of
            system should be kept transparent to the user.
        2.  This requires a middleware layer.

**P2P Applications**

P2P is good for:

-   File sharing (Napster, Gnutella, Kazza)
-   Multiplayer games (Unreal Tournament, DOOM)
-   Collaborative applications (ICQ, share whiteboard)
-   Distributed computation (<Seti@home>)
-   Ad-hoc networks

P2P can be applied in many areas, and there are massive work in many
areas to utilize the P2P concepts and techniques.
