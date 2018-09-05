# Introduction

This guide provides basic overview of some common networking concepts. Discussed here in are basic terminology, common protocols, and the responsibilities and characterisitics of different layers of networking.

## Networking Glossary

This section lists the common terms that will be used throughout this and any other guide on networking.

The terms introduced here will be expanded in the sections following:

* **Connection:** A connection refers to the pieces of related information that are transferred through a network. This generally refers that a connection is built before the data transfer(by following the proocedures laid out in the protocol) and then is deconstructed at the end of the data transfer.

* **Packet:** A packet is, generally speaking, the most basic unit of transfer over a network. When communicating over a network, packets are the envelopes that carry your data(in pieces) from one point to the other.

* **Network Interface:** Network Interface refers to any piece of software interface to networking hardware. For instance, if you have two network cards in your computer, you can control and configure each network interface associated with them individually.

A network interface may be associated with a physical device, or it may be a representation of a virtual interface. The "loopback" device, which is a virtual interface to the local machine is an example of this.

* **LAN:** Local Area Network(LAN) refers to a network or a protion of network that is not publicly accessible to the greater network. A home or office network is an example of a LAN

* **WAN:** Wide Area Network(WAN) refers to a network that is much more extensive than a LAN.

* **Protocol:** A protocol is a set of rules and standards that define a language that devices use to communicate. There are a diverse range of protocols used by various devices for networking and are often implemented in the various levels of networking.

Some low level protocols are UDP, TCP, IP and ICMP. Some familiar examples of application level protocols are HTTP, SSH, TLS/SSL, and FTP.

* **Port:** A port is an address on a single machine that can be tied to a piece of software. A port is not a physical interface or a location, but it allows your server to communicate using more than one application.

* **Firewall:** A firewall is a program that decides whether traffic coming into a server or  going out should be allowed. A firewall usually works by creating rules for which type of traffic is acceptable on which ports. Generally, firewalls block ports that are not used on by a specific application onn server.

* **NAT:** Network Address Translation. It is a way to translate the requests that are incoming into a routing server to the relevant devices or servers it knows about in the LAN. This is usually implemented in physical LANs as a way to route requests through oone IP address to the necessary backend servers.

* **VPN:** Virtual Private Network. A means to connect several LAN's via the internet, while maintaining Privacy. This is used as a means for connecting remote systems as if they were on a local network, often for security reasons.

# Network Layers

There are multiple protocols and technologies that are built on top of each other in order foor th communication to function more easily. Each successive, higher layer abstracts the raw data a little bit more, and makes it simpler to use for applications in and users.

As data is sent out of one machine, it begins at the top of the stack and filters downwards. At the lowest level actual transmission to another machine takes place. At this point, the data travels back up through the layers of the other computer.

Each layer has the ability to add its own "wrapper" around the data that it receives from the adjacent layer, which will help the layers that come after decide what to do with the data when it is passed off.

## **OSI Model**

It is one model of talking about the different layers of network communication in the OSI model. OSI stands for Open systems Interconnect.

The model defines seven layers as follows:

* **Application:** Application layer is the layer that the users and user-applications often interact with. Network communication is discussed in terms of availability of the resources, partners to communicate with and data synchronization.

* **Presentation:** Presentation layer is responsible for the mapping of resources and creating context. It is used to translate the lower level networking data into data that applications expect to see.

* **Session:** The session layer is a connection handler. It creates, maintains, and destroys connections between nodes in a persisten way.

* **Transport:** This layer is responsible for handling the layers above it a reliable connection. In this context, reliable refers to the ability to verify that a piece of data was received intact at the other end of connection.

This layer can resend information that has been dropped or corrupted and can acknowledge the receipt of remote computers.

* **Network:** The network layer is used to route the data between different nodes on the network. It uses addresses to tell which computer too send information to. This layer can also break the layer messages into smaller messages to be re-assembled at the other end.

* **Data Link:** This layer is implemented as a method of establishing and maintaining reliable links between different nodes or devices on a network using existing physical connections.

* **Physical Link:** The physical layer is responsible for handling the actual physical devices that are used to make the connection. This layer involves the bare software that manages the physical connection as well as the hardware itself.

## **TCP/IP Moodel**

This is another layering model and is simpler than the OSI model and has been adopted widely. It defines 4 layers which overlap with the OSI model:

* **Application:** In this model, the application layer is responnsible for creating and transmitting users data between applications. The applications can be on remote systems, and should appear to operate as if locally to the end user.

The communication is said to be taking between peers.

* **Transport:** The transport layer is responsible for communication between processes. This level of networking utilizes ports to address different services. It can build up unreliable or reliable connections depending on the type of protocol used.

* **Internet:** The internet layer is responsible for data transfer between node to node in a network. This layer is aware of the endpoints of the connections, but does not worry aboout the actual connection needed to go from one place to another. IP addresses are defined in this layer as a way of reaching a remote systems in an addressable manner.

* **Link:** The link layer is the actual topology of the network that allows the internet layer to present an addressable interface. It establishes connections between neighboring nodes to send data.

## Interfaces

Interfaces are networking communnication points for your computer. Each interface is associated with a physical or virtual networking device.

Typically, your server will have one configurable network interface for each Ethernet or wireless internet card you have.

In addition, it will define a virtual network interface called the "loopback" or localhost interface. This is used as an interface to connect applications and processes on a single computer to other applications and processes. You can see this referenced as the "lo" interface in many tools.

Many times, administrators configure one interface to service traffic to the internet and another interface for a LAN or private network.

## Protocols

Networking works by piggybackig a number of different protocols on top of each other. In this way, one piece of data can be transmitted using multiple protocols encapsulated within one another.

### **Media Access Control**

Media access control is a communications protocol that is used to distinguish specific devices. Each device is supposed to get a unique MAC address during the manufacture process that differentiates it from the rest of the devices on thee internet.

Addressing hardware by the MAC address allows you to reference a device by a unique value even when the software on top may change the name for that specific device during operation.

Media Access control is one of the only protocols from the link layer that you are likely to interact with on a regular basis.

### **IP**

The IP protocol is the fundamental protocol that allows the internet to work. IP addresses are uinque on each network and the allow machines to address each other across a network. It is implemented on the internet layer in TCP/IP model.

The protocol assumes an unreliable network and muliple paths to the same destination that it can dynamically change between.

### **ICMP**

Internet Control Message Protocol is used for sending messages betwenn devices too indicate the availability or error conditions. These packets are used in variety of network diagnostic tools, such as ping and traceroute.

These packets serve as a feedback mechanism for network communications.

### **TCP**

Transmission Control Protocol, is implemented in thee transport layer of TCP/IP and is used to establish reliable connections.

TCP is one of the protocols that encapsulates the data into packets. It then transfers these to the remote end of the connection using the methods available on the lower layers. On the other end, it can check for errors, request certain pieces to be resent, and reassemble the information into one logical piece to send to the application layer.

The protocol builds up a connection prior to data transfer using a system called as a 3-way handshake. This is a way for 2 ends of the communication to acknowledge the request and agree upon a method of ensuring data reliability.

After the data hand been sent, the connection is toen down using a similar 4 way handshake.

TCP is the protocol of choice for may of the most popular uses on the inertnet including WWW, FTP, SSH and email.

### **UDP**

UDP stands for user datagram protocol. It is a popular companion protocol to TCP and is also implemented in the transport layer.

The fundamental difference between UDP and TCP is that UDP offers unreliable data transfer. It does not verify that data has been received on the other end of the connection. This might sound like a bad thing, and for many purposes, it is. However, it is also extremely important for some functions.

Because it is not required to wait for confirmation that the data was received and forced to resend data, UDP is much faster than TCP. It does not establish a connection with the remote host, it simply fires off the data to that host and doesn't care if it is accepted or not.

Because it is a simple transaction, it is useful for simple communications like querying for network resources. It also doesn't maintain a state, which makes it great for transmitting data from one machine to many real-time clients. This makes it ideal for VOIP, games, and other applications that cannot afford delays.

### **HTTP**

HTTP stands for hypertext transfer protocol. It is a protocol defined in the application layer that forms the basis for communication on the web.

HTTP defines a number of functions that tell the remote system what you are requesting. For instance, GET, POST, and DELETE all interact with the requested data in a different way.

### **FTP**

FTP stands for file transfer protocol. It is also in the application layer and provides a way of transferring complete files from one host to another.

It is inherently insecure, so it is not recommended for any externally facing network unless it is implemented as a public, download-only resource.

### **DNS**

DNS stands for domain name system. It is an application layer protocol used to provide a human-friendly naming mechanism for internet resources. It is what ties a domain name to an IP address and allows you to access sites by name in your browser.

### **SSH**

SSH stands for secure shell. It is an encrypted protocol implemented in the application layer that can be used to communicate with a remote server in a secure way. Many additional technologies are built around this protocol because of its end-to-end encryption and ubiquity.

There are many other protocols that we haven't covered that are equally important. However, this should give you a good overview of some of the fundamental technologies that make the internet and networking possible.