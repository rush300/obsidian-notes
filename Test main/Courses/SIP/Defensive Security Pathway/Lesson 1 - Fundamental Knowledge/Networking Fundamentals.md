
# The OSI Model

The OSI (**O**pen **S**ystems **I**nterconnection) Model is a standardised model which is used to demonstrate the theory behind computer networking. In practice, it's actually the more compact TCP/IP model that real-world networking is based off; however the OSI model, in many ways, is easier to get an initial understanding from.

The OSI model consists of seven layers:

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/gZFYyxPhRxqf9vXWdUve)

Let's briefly take a look at each of these in turn:  

**Layer 7: Application:**

The application layer of the OSI model essentially provides networking options to programs running on a computer. It works almost exclusively with applications, providing an interface for them to use in order to transmit data. When data is given to the application layer, it is passed down into the presentation layer.

  

**Layer 6: Presentation:**

The presentation layer receives data from the application layer. This data tends to be in a format that the application understands, but it's not necessarily in a standardised format that could be understood by the application layer in the _receiving_ computer. The presentation layer translates the data into a standardised format, as well as handling any encryption, compression or other transformations to the data. With this complete, the data is passed down to the session layer.

  

**Layer 5: Session:**

When the session layer receives the correctly formatted data from the presentation layer, it looks to see if it can set up a connection with the other computer across the network. If it can't then it sends back an error and the process goes no further. If a session _can_ be established then it's the job of the session layer to maintain it, as well as co-operate with the session layer of the remote computer in order to synchronise communications. The session layer is particularly important as the session that it creates is unique to the communication in question. This is what allows you to make multiple requests to different endpoints simultaneously without all the data getting mixed up (think about opening two tabs in a web browser at the same time)! When the session layer has successfully logged a connection between the host and remote computer the data is passed down to Layer 4: the transport Layer.

  

**Layer 4: Transport:**

The transport layer is a very interesting layer that serves numerous important functions. Its first purpose is to choose the protocol over which the data is to be transmitted. The two most common protocols in the transport layer are TCP (**T**ransmission **C**ontrol **P**rotocol) and UDP (**U**ser **D**atagram **P**rotocol); with TCP the transmission is _connection-based_ which means that a connection between the computers is established and maintained for the duration of the request. This allows for a reliable transmission, as the connection can be used to ensure that the packets _all_ get to the right place.  

A TCP connection allows the two computers to remain in constant communication to ensure that the data is sent at an acceptable speed, and that any lost data is re-sent. With UDP, the opposite is true; packets of data are essentially thrown at the receiving computer - if it can't keep up then that's _its_ problem (this is why a video transmission over something like Skype can be pixelated if the connection is bad).  

What this means is that TCP would usually be chosen for situations where accuracy is favoured over speed (e.g. file transfer, or loading a webpage), and UDP would be used in situations where speed is more important (e.g. video streaming).  

With a protocol selected, the transport layer then divides the transmission up into bite-sized pieces (over TCP these are called _segments_, over UDP they're called _datagrams_), which makes it easier to transmit the message successfully.

  

**Layer 3: Network:**

The network layer is responsible for locating the destination of your request. For example, the Internet is a huge network; when you want to request information from a webpage, it's the network layer that takes the IP address for the page and figures out the best route to take. At this stage we're working with what is referred to as _Logical_ addressing (i.e. IP addresses) which are still software controlled. Logical addresses are used to provide order to networks, categorising them and allowing us to properly sort them. Currently the most common form of logical addressing is the IPV4 format, which you'll likely already be familiar with (i.e 192.168.1.1 is a common address for a home router).

  

**Layer 2: Data Link:**

The data link layer focuses on the _physical_ addressing of the transmission. It receives a packet from the network layer (that includes the IP address for the remote computer) and adds in the physical (MAC) address of the receiving endpoint. Inside every network enabled computer is a Network Interface Card (NIC) which comes with a unique MAC (Media Access Control) address to identify it.  

MAC addresses are set by the manufacturer and literally burnt into the card; they can't be changed - although they _can_ be spoofed. When information is sent across a network, it's actually the physical address that is used to identify where exactly to send the information.

Additionally, it's also the job of the data link layer to present the data in a format suitable for transmission.

The data link layer also serves an important function when it receives data, as it checks the received information to make sure that it hasn't been corrupted during transmission, which could well happen when the data is transmitted by layer 1: the physical layer.

  

**Layer 1: Physical:**

The physical layer is right down to the hardware of the computer. This is where the electrical pulses that make up data transfer over a network are sent and received. It's the job of the physical layer to convert the binary data of the transmission into signals and transmit them across the network, as well as receiving incoming signals and converting them back into binary data.

  

**_Additional Learning:_** _DNS_

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/g2sZYZceTlK5stMVGfda)

  

In OSI stack terms, **DNS runs in parallel to HTTP in the Application Layer (layer 7)**. DNS is in effect an application that is invoked to help out the HTTP application, and therefore does not sit "below" HTTP in the OSI stack. DNS itself also makes use of UDP and more rarely TCP, both of which in turn use IP.  

All computers on the Internet, from your smart phone or laptop to the servers that serve content for massive retail websites, find and communicate with one another by using numbers. These numbers are known as **IP addresses**. When you open a web browser and go to a website, you don't have to remember and enter a long number. Instead, you can enter a **domain name** like example.com and still end up in the right place.

A DNS service such as Amazon Route 53 is a globally distributed service that translates human readable names like [www.example.com](http://www.example.com) into the numeric IP addresses like 192.0.2.1 that computers use to connect to each other. The Internet’s DNS system works much like a phone book by managing the mapping between names and numbers. DNS servers translate requests for names into IP addresses, controlling which server an end user will reach when they type a domain name into their web browser. These requests are called **queries**.

  

**Types of DNS Service**

**Authoritative DNS:** An **authoritative DNS** service provides an update mechanism that developers use to manage their public DNS names. It then answers DNS queries, translating domain names into IP address so computers can communicate with each other. Authoritative DNS has the final authority over a domain and is responsible for providing answers to **recursive DNS** servers with the IP address information. **Amazon Route 53 is an authoritative DNS system.**

**Recursive DNS**: Clients typically do not make queries directly to authoritative DNS services. Instead, they generally connect to another type of DNS service known a **resolver**, or a **recursive DNS** service. A recursive DNS service acts like a hotel concierge: while it doesn't own any DNS records, it acts as an intermediary who can get the DNS information on your behalf. If a recursive DNS has the DNS reference **cached**, or stored for a period of time, then it answers the DNS query by providing the source or IP information. If not, it passes the query to one or more authoritative DNS servers to find the information.

# Encapsulation

As the data is passed down each layer of the model, more information containing details specific to the layer in question is added on to the start of the transmission.  

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/YXzKD4fZTMuwqEiDi2Ui)  

As an example, the header added by the Network Layer would include things like the source and destination IP addresses, and the header added by the Transport Layer would include (amongst other things) information specific to the protocol being used. The data link layer also adds a piece on at the _end_ of the transmission, which is used to verify that the data has not been corrupted on transmission; this also has the added bonus of increased security, as the data can't be intercepted and tampered with without breaking the trailer. This whole process is referred to as _encapsulation;_ the process by which data can be sent from one computer to another.  

Notice that the encapsulated data is given a different name at different steps of the process. In layers 7,6 and 5, the data is simply referred to as data. In the transport layer the encapsulated data is referred to as a segment or a datagram (depending on whether TCP or UDP has been selected as a transmission protocol). At the Network Layer, the data is referred to as a packet. When the packet gets passed down to the Data Link layer it becomes a frame, and by the time it's transmitted across a network the frame has been broken down into bits.  

When the message is received by the second computer, it reverses the process -- starting at the physical layer and working up until it reaches the application layer, stripping off the added information as it goes. This is referred to as _de-encapsulation._ As such you can think of the layers of the OSI model as existing inside every computer with network capabilities. Whilst it's not actually as clear cut in practice, computers all follow the same process of encapsulation to send data and de-encapsulation upon receiving it.  

The processes of encapsulation and de-encapsulation are very important -- not least because of their practical use, but also because they give us a standardised method for sending data. This means that all transmissions will consistently follow the same methodology, allowing any network enabled device to send a request to any other reachable device and be sure that it will be understood -- regardless of whether they are from the same manufacturer; use the same operating system; or any other factors.

# The TCP/IP Model

The TCP/IP model is, in many ways, very similar to the OSI model. It's a few years older, and serves as the basis for real-world networking. The TCP/IP model consists of four layers: Application, Transport, Internet and Network Interface. Between them, these cover the same range of functions as the seven layers of the OSI Model.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/yzYlb6NgRiiRajSDKbzE)

**_Note:_** _Some recent sources split the TCP/IP model into five layers -- breaking the Network Interface layer into Data Link and Physical layers (as with the OSI model). This is accepted and well-known; however, it is not officially defined (unlike the original four layers which are defined in RFC1122). It's up to you which version you use -- both are generally considered valid._

You would be justified in asking why we bother with the OSI model if it's not actually used for anything in the real-world. The answer to that question is quite simply that the OSI model (due to being less condensed and more rigid than the TCP/IP model) tends to be easier for learning the initial theory of networking.

The two models match up something like this:

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/zkQZgNCbQa5coHhlJ1e0)  

The processes of encapsulation and de-encapsulation work in exactly the same way with the TCP/IP model as they do with the OSI model. At each layer of the TCP/IP model a header is added during encapsulation, and removed during de-encapsulation.

Now let's get down to the practical side of things.

A layered model is great as a visual aid -- it shows us the general process of how data can be encapsulated and sent across a network, but how does it actually happen?

When we talk about TCP/IP, it's all well and good to think about a table with four layers in it, but we're actually talking about a suite of protocols -- sets of rules that define how an action is to be carried out. TCP/IP takes its name from the two most important of these: the **T**ransmission **C**ontrol **P**rotocol (which we touched upon earlier in the OSI model) that controls the flow of data between two endpoints, and the **I**nternet **P**rotocol, which controls how packets are addressed and sent. There are many more protocols that make up the TCP/IP suite; we will cover some of these in later tasks. For now though, let's talk about TCP.

  

As mentioned earlier, TCP is a _connection-based_ protocol. In other words, before you send any data via TCP, you must first form a stable connection between the two computers. The process of forming this connection is called the _three-way handshake_.

When you attempt to make a connection, your computer first sends a special request to the remote server indicating that it wants to initialise a connection. This request contains something called a _SYN_ (short for _synchronise_) bit, which essentially makes first contact in starting the connection process. The server will then respond with a packet containing the SYN bit, as well as another "acknowledgement" bit, called _ACK_. Finally, your computer will send a packet that contains the ACK bit by itself, confirming that the connection has been setup successfully. With the three-way handshake successfully completed, data can be reliably transmitted between the two computers. Any data that is lost or corrupted on transmission is re-sent, thus leading to a connection which appears to be lossless.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/y8WsonDuTBiOEipLUSw8)  

We're not going to go into exactly _how_ this works on a step-to-step level -- not in this room at any rate. It is sufficient to know that the three-way handshake must be carried out before a connection can be established using TCP.

## Curriculum

At this stage, hopefully all of the theory has made sense and you now understand the basic models behind computer networking. For the rest of the room we're going to be taking a look at some of the command line networking tools that we can use in practical applications. Many of these tools do work on other operating systems, but for the sake of simplicity, I'm going to assume that you're running Linux for the rest of this room. The first tool that we're going to look at will be the ping command.  

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/gIPKmD6YSKlvEnfJFGnq)

  

The ping command is used when we want to test whether a connection to a remote resource is possible. Usually this will be a website on the internet, but it could also be for a computer on your home network if you want to check if it's configured correctly. Ping works using the ICMP protocol, which is one of the slightly less well-known TCP/IP protocols that were mentioned earlier. The ICMP protocol works on the Network layer of the OSI Model, and thus the Internet layer of the TCP/IP model. The basic syntax for ping is ping <target>. In this example we are using ping to test whether a network connection to Google is possible:

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/Zn6HiL0RXi9oV53V3s2c)

Notice that the ping command actually returned the IP address for the Google server that it connected to, rather than the URL that was requested. This is a handy secondary application for ping, as it can be used to determine the IP address of the server hosting a website. One of the big advantages of ping is that it's pretty much ubiquitous to any network enabled device. All operating systems support it out of the box, and even most embedded devices can use ping!

# Traceroute

The logical follow-up to the ping command is 'traceroute'. Traceroute can be used to map the path your request takes as it heads to the target machine.

The internet is made up of many, many different servers and end-points, all networked up to each other. This means that, in order to get to the content you actually want, you first need to go through a bunch of other servers. Traceroute allows you to see each of these connections -- it allows you to see every intermediate step between your computer and the resource that you requested. The basic syntax for traceroute on Linux is this: traceroute <destination>  

By default, the Windows traceroute utility (tracert) operates using the same ICMP protocol that ping utilises, and the Unix equivalent operates over UDP. This can be altered with switches in both instances.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/lxB32cyMTRirH0B6UYqT)

You can see that it took 13 hops to get from my router (_gateway) to the Google server at 216.58.205.46

# WHOIS

Domain Names -- the unsung saviours of the internet.  

Can you imagine how it would feel to remember the IP address of every website you want to visit? Horrible thought.  

Fortunately, we've got domains.  

We'll talk a little bit more about how this works in the next task, but for now suffice to know that a domain translates into an IP address so that we don't need to remember it (e.g. you can type saferinternetproject.com, rather than the Safer Internet Project IP address). Domains are leased out by companies called Domain Registrars. If you want a domain, you go and register with a registrar, then lease the domain for a certain length of time.  

**WHOIS**

Whois essentially allows you to query who a domain name is registered to. In some countries/ regions, personal details are redacted; however, elsewhere you can potentially get a great deal of information from a whois search.  

There is a [web version](https://www.whois.com/whois/) of the whois tool if you're particularly adverse to the command line. Either way, let's get started!  

> **_(Note: You may need to install whois before using it. On Debian based systems this can be done with_ sudo apt update && sudo apt-get install whois_)_**  

Whois lookups are very easy to perform. Just use whois <domain> to get a list of available information about the domain registration:

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/3tlMmBTCQpzeWr5tfC0H)  

This is comparatively a very small amount of information as can often be found. Notice that we've got the domain name, the company that registered the domain, the last renewal, and when it's next due, and a bunch of information about nameservers (which we'll look at in the next task).

# Dig

We talked about domains in the previous task -- now lets talk about how they work.

Ever wondered how a URL gets converted into an IP address that your computer can understand? The answer is a TCP/IP protocol called [DNS](https://learn.saferinternetproject.com.au/admin-app/courses/1856258/curriculum/lessons/42234234#viewer-undefined) (**D**omain **N**ame **S**ystem).

At the most basic level, [DNS](https://learn.saferinternetproject.com.au/admin-app/courses/1856258/curriculum/lessons/42234234#viewer-undefined) allows us to ask a special server to give us the IP address of the website we're trying to access. For example, if we made a request to [www.google.com](http://www.google.com), our computer would first send a request to a special DNS server (which your computer already knows how to find). The server would then go looking for the IP address for Google and send it back to us. Our computer could then send the request to the IP of the Google server.  

Let's break this down a bit.  

You make a request to a website. The first thing that your computer does is check its local cache to see if it's already got an IP address stored for the website; if it does, great. If not, it goes to the next stage of the process.  

Assuming the address hasn't already been found, your computer will then send a request to what's known as a _recursive_ [DNS](https://learn.saferinternetproject.com.au/admin-app/courses/1856258/curriculum/lessons/42234234#viewer-undefined) server. These will automatically be known to the router on your network. Many Internet Service Providers (ISPs) maintain their own recursive servers, but companies such as Google and OpenDNS also control recursive servers. This is how your computer automatically knows where to send the request for information: details for a recursive DNS server are stored in your router. This server will also maintain a cache of results for popular domains; however, if the website you've requested isn't stored in the cache, the recursive server will pass the request on to a _root name_ server.  

Before 2004 there were precisely 13 root name DNS servers in the world. These days there are many more; however, they are still accessible using the same 13 IP addresses assigned to the original servers (balanced so that you get the closest server when you make a request). The root name servers essentially keep track of the DNS servers in the next level down, choosing an appropriate one to redirect your request to. These lower level servers are called _Top-Level_ _Domain_ servers.  

Top-Level Domain (TLD) servers are split up into extensions. So, for example, if you were searching for tryhackme**.com** your request would be redirected to a TLD server that handled .com domains. If you were searching for bbc**.co.uk** your request would be redirected to a TLD server that handles .co.uk domains. As with root name servers, TLD servers keep track of the next level down: _Authoritative name servers_. When a TLD server receives your request for information, the server passes it down to an appropriate Authoritative name server.  

Authoritative name servers are used to store DNS records for domains directly. In other words, every domain in the world will have its DNS records stored on an Authoritative name server somewhere or another; they are the source of the information. When your request reaches the authoritative name server for the domain you're querying, it will send the relevant information back to you, allowing your computer to connect to the IP address behind the domain you requested.  

When you visit a website in your web browser this all happens automatically, but we can also do it manually with a tool called dig . Like ping and traceroute, dig should be installed automatically on Linux systems.

Dig allows us to manually query recursive DNS servers of our choice for information about domains:

dig <domain> @<dns-server-ip>  

It is a very useful tool for network troubleshooting.  

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/NpPQcbVSIaL3Xe846oXk)  

This is a _lot_ of information. We're currently most interested in the ANSWER section for this room; however, taking the time to learn what the rest of this means is a very good idea. In summary, that information is telling us that we sent it one query and successfully (i.e. No Errors) received one full answer -- which, as expected, contains the IP address for the domain name that we queried.  

Another interesting piece of information that dig gives us is the TTL (**T**ime **T**o **L**ive) of the queried DNS record. As mentioned previously, when your computer queries a domain name, it stores the results in its local cache. The TTL of the record tells your computer when to stop considering the record as being valid -- i.e. when it should request the data again, rather than relying on the cached copy.  

The TTL can be found in the second column of the answer section:

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/XiKglc2sTDOx9kP0yhCX)  

It's important to remember that TTL (in the context of DNS caching) is measured in _seconds,_ so the record in the example will expire in two minutes and thirty-seven seconds.

# Arp-Scan

Arp-scan is a command line utility for linux that can be used to scan the network of a certain interface for alive hosts. It shows the IP address and mac addresses of all the hosts/nodes found.  

Project website

[http://www.nta-monitor.com/tools-resources/security-tools/arp-scan](http://www.nta-monitor.com/tools-resources/security-tools/arp-scan)  

Install on ubuntu

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/h7zSGP3BSgWDhxBYNUSN)

### Usage

Quick example

$ sudo arp-scan --interface=eth0 --localnet
Interface: eth0, datalink type: EN10MB (Ethernet)
Starting arp-scan 1.8.1 with 256 hosts (http://www.nta-monitor.com/tools/arp-scan/)
192.168.1.1     00:21:2c:82:08:87       SemIndia System Private Limited
192.168.1.2     6c:f0:49:69:c1:25       GIGA-BYTE TECHNOLOGY CO.,LTD.
2 packets received by filter, 0 packets dropped by kernel
Ending arp-scan 1.8.1: 256 hosts scanned in 1.435 seconds (178.40 hosts/sec). 2 responded

So in the above example arp-scan was used to scan the network of the device eth0, and it discovered 2 alive nodes apart from localhost machine. The option localnet makes arp-scan scan the local network.

In place of the localnet option arp-scan can also take a range of IP addresses to scan. For example :

$ sudo arp-scan --interface=eth0 192.168.1.1/24
Interface: eth0, datalink type: EN10MB (Ethernet)
WARNING: host part of 192.168.1.1/24 is non-zero
Starting arp-scan 1.8.1 with 256 hosts (http://www.nta-monitor.com/tools/arp-scan/)
192.168.1.1     00:21:2c:82:08:87       SemIndia System Private Limited
192.168.1.2     6c:f0:49:69:c1:25       GIGA-BYTE TECHNOLOGY CO.,LTD.
2 packets received by filter, 0 packets dropped by kernel
Ending arp-scan 1.8.1: 256 hosts scanned in 1.421 seconds (180.15 hosts/sec). 2 responded

The IP range has been given in CIDR notation. The number after the forward slash indicates how many bits stay constant from the left. So 24 means that the first 24 left bits stays constant and rest can change, which implies that the last octet can change, so the range is effectively 192.168.1.1 to 192.168.1.256

# VLAN

Virtual local area networks, or VLANs, have become important as network complexity has exceeded the capacity of typical local area networks (LANs). Originally, a LAN connected a group of computers and associated devices to a server via cables in a shared physical location (hence the term “local”). Many LANs now connect devices via wireless internet, rather than Ethernet, although most LANs use a combination of both connectivity types. Over time, organizations have grown in their networking needs, requiring solutions that enable networks to grow in size, flexibility, and complexity.  

VLANs circumvent the physical limitations of a LAN through their virtual nature, allowing organizations to scale their networks, segment them to increase security measures, and decrease network latency.

![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://www.filepicker.io/api/file/edxgxWAeQnOwMhyD4YVf)

## **What is a VLAN and what is its purpose?**

In essence, a VLAN is a collection of devices or network nodes that communicate with one another as if they made up a single LAN, when in reality they exist in one or several LAN segments. In a technical sense, a segment is separated from the rest of the LAN by a bridge, router, or switch, and is typically used for a particular department. This means that when a workstation broadcasts packets, they reach all other workstations on the VLAN but none outside it.  

This simplifies many of the potential complications caused by LANs, including excessive network traffic and collisions. When two workstations send data packets at the same time on a LAN connected via a hub, the data collides and is not transmitted properly. The collision propagates through the entire network, meaning that the LAN is busy and requires users to wait until the collision has been fully transferred throughout the network before it is operable again—at which point the original data must be resent.  

VLANs reduce the incidence of collisions and decrease the number of network resources wasted by acting as LAN segments. Data packets sent from a workstation in a segment are transferred by a bridge or switch, which will not forward collisions but will send on broadcasts to every network devices. For this reason, segments are called “collision domains” because they contain collisions within the bounds of that section.  

However, VLANs have more functionality than even a LAN segment because they allow for increased data security and logical partition. Remember, a VLAN acts as a single LAN although it only makes up a segment. This means that the broadcast domain of a VLAN is the VLAN itself, rather than each network segment. Additionally, the partitions do not have to be defined by the physical location of the network devices. They can be grouped instead by department, project team, or any other logical organizational principle.

## **Why would you use a VLAN?**

Organizations benefit greatly from the advantages of VLAN usage, including increased performance, more flexibility in network configuration and workgroup formation, and reduced administrative efforts.

- **VLANs are cost-effective**, because workstations on VLANs communicate with one another through VLAN switches and don’t require routers unless they are sending data outside the VLAN. This empowers the VLAN to manage an increased data load because, while switches have fewer capabilities than a router, routers cause bottlenecks. VLANs do not need to forward information through a router to communicate with devices within the network, decreasing overall network latency.
- **VLANs offer more flexibility than nonvirtual networking solutions**. VLANs can be configured and assigned based on port, protocol, or subnet criteria, making it possible to alter VLANs and change network design when necessary. Furthermore, because VLANs are configured on a basis outside their physical connection to hardware or proximity to other devices, they allow for groups who collaborate—and presumably transfer a great deal of data to one another’s devices—to share a VLAN even if they work on separate floors or in different buildings.
- **VLANs decrease the amount of administrative oversight required** by network overseers like managed services providers (MSPs). VLANs allow network administrators to automatically limit access to a specified group of users by dividing workstations into different isolated LAN segments. When users move their workstations, administrators don’t need to reconfigure the network or change VLAN groups. These factors decrease the amount of time and energy administrators must devote to configuration and security measures.

  

## **What is an example of a VLAN?**

Many organizations have a WAN (wide area network) due to their expansive offices and large teams. In these scenarios, having multiple VLANs would greatly expedite network operations. Often, large companies work on cross-functional projects. The ease of configuring VLANs—and redistributing users to VLANs—makes it possible to put even interdepartmental teams on the same VLAN to facilitate a high volume of data sharing. Marketing, sales, IT, and business analysts can work together to achieve high-stakes objectives most efficiently when network segmentation facilitates flexible teamwork.  

While VLANs have their own complications, such as VLAN mismatches, MSPs who know how to configure a VLAN properly can leverage their powerful network segmentation benefits to make their clients’ networks faster and more secure while giving them physical flexibility. As all networks evolve over time, MSPs who know how to conduct VLAN maintenance and check device distribution can increase and sustain network performance.

## Lesson Summary

- Ping, Traceroute, Whois, Dig, Arp-Scan, and VLAN are networking tools used for network diagnosis and management.
- Ping is used to check network connectivity.
- Traceroute maps network paths.
- Whois retrieves domain registration information.
- Dig converts URLs to IP addresses.
- Arp-Scan scans network hosts.
- VLANs create virtual local area networks for increased scalability, segmentation, and security.
- VLANs reduce network congestion and simplify administration.
- VLANs allow separate groups to collaborate and share data.
- VLANs are useful in large organizations with expansive offices and teams.
- Properly configured VLANs enhance network speed, security, and flexibility.
- The OSI Model is a standardized model for understanding computer networking.
- The OSI Model has seven layers: Application, Presentation, Session, Transport, Network, Data Link, and Physical.
- The TCP/IP Model, based on the OSI Model, is the basis for real-world networking.
- The TCP/IP Model has four layers: Application, Transport, Internet, and Network Interface.
- Both models use encapsulation and de-encapsulation to add and remove headers at each layer during data transmission.
- The TCP/IP Model uses protocols such as TCP and IP.
- TCP is a connection-based protocol that requires a three-way handshake.
- Understanding these models and protocols is essential for practical networking applications.
- Ping is a useful tool for testing connectivity to remote resources.