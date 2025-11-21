## Objectives :

The primary objectives of this module are to build strong fundamentals in:

* Cybersecurity
* Networking
* Cryptography
* Professional lab setup

Sub-Tasks : 

1. Cybersecurity Basics.
2. Lab Environment Setup.
3. Linux Fundamentals.
4. Networking Fundamentals.
5. Cryptography Basics.
6. Tool Familiarisation.

---

# **1. Cybersecurity Basics**

---

## **1.1 CIA Triad**

The CIA Triad represents the three essential pillars of information security.
They form the baseline framework followed globally across organizations.

---

### **1.1.1 Confidentiality**

Confidentiality ensures that information is accessible only to authorised individuals.

**Implementation Methods**

* Authentication (passwords, MFA)
* Role-based Access Control (RBAC)
* Least privilege enforcement
* Encryption (AES, TLS)
* Physical security controls

**Common Attacks**

* Unauthorised access
* Identity theft
* Credential harvesting
* Phishing-based breaches

---

### **1.1.2 Integrity**

Integrity ensures information remains accurate, consistent, and unaltered.

**Implementation Methods**

* Cryptographic hashing (SHA-256)
* Checksums and data verification
* Digital signatures
* Message Authentication Codes (MAC)
* Version control

**Common Attacks**

* Man-in-the-Middle
* Unauthorised data modification
* SQL injection
* Packet tampering

---

### **1.1.3 Availability**

Availability ensures information and services are accessible to authorised users at all times.

**Implementation Methods**

* Redundancy and failover systems
* Backups and disaster recovery planning
* Load balancing
* Patch and maintenance cycles

**Common Attacks**

* DoS and DDoS
* Resource exhaustion
* System failures
* Network outages

---

## **1.2 Threats**

A threat refers to any event or action with the potential to harm systems, networks, or data by impacting confidentiality, integrity, or availability.

Threats may be:

* **Intentional:** malware, hacking, targeted attacks
* **Unintentional:** human error, misconfiguration, natural incidents

---

### **👉 Common Threat Types**

* Phishing : Deceptive communication designed to steal credentials, financial data, or personal information.

* Malware : Software created to infiltrate, damage, or gain unauthorised access.

      Malware Types Include
  
                  * Virus
                  * Worm
                  * Trojan
                  * Spyware
                  * Adware
  
* DDoS : Overwhelms a target network/service with excessive traffic, causing downtime.

* SQL Injection : Injects malicious SQL commands to manipulate or extract database information.

* Brute Force : Systematically attempting every possible credential combination.

* Ransomware : Encrypts files and demands payment for decryption.

---

## **1.3 Attack Vectors**

An attack vector is the route or method through which an attacker gains unauthorised access or delivers malicious content.

---

### **1.3.1 Social Engineering**

Exploits human behavior rather than technical vulnerabilities.

**Examples**

* Phishing
* Vishing (voice phishing)
* Smishing (SMS phishing)
* Pretexting

---

### **1.3.2 Wireless Attacks**

Targets weaknesses in Wi-Fi networks and wireless devices.

**Examples**

* Rogue access points
* Packet sniffing
* Wireless DoS

---

### **1.3.3 Insider Threats**

Threats originating from individuals with internal access.

**👉 Types**

* Malicious insiders
* Accidental insiders

**Note**: Sub-task 3 (Linux Fundamentals) is maintained in a separate file to ensure modular access and streamlined reading.

---
# **4. Networking Basic Behaviour** 


 ## **OSI Model Layers And Functions**: 

The OSI (Open Systems Interconnection) Model is a set of rules that explains how different computer systems communicate over a network. The OSI Model was developed by the International Organisation for Standardisation (ISO). The OSI Model comprises seven layers, each with specific functions and responsibilities. This layered approach makes it easier for different devices and technologies to work together.   
 

   ![OSI Model](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/OSI_Model.jpg?raw=1)
  

## **Layer 1: Physical Layer** : 

The lowest layer of the OSI reference model is the Physical Layer. It is responsible for the actual physical connection between the devices. The physical layer contains information in the form of bits.

 ![physical layer](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/physical-layer-768.png?raw=true)
                        
 * The Physical Layer is responsible for transmitting individual bits from one node to the next.
 * When receiving data, this layer will get the signal received and convert it into 0s and 1s and send them to the Data Link layer, which will put the frame back together.

## **Layer 2: Data Link Layer (DLL)** :

The data link layer is responsible for the node-to-node delivery of the message. The main function of this layer is to make sure data transfer is error-free from one node to another, over the physical layer.

* When a packet arrives in a network, it is the responsibility of the DLL to transmit it to the Host using its MAC address.
* A packet in the Data Link layer is referred to as Frame. Switches and Bridges are common Data Link Layer devices.
* The packet received from the Network layer is further divided into frames depending on the frame size of the NIC (Network Interface Card). DLL also encapsulates the       Sender and Receiver’s MAC addresses in the header.
* The Receiver’s MAC address is obtained by placing an ARP (Address Resolution Protocol) request onto the wire asking, "Who has that IP address?" and the destination host will reply with its MAC address.

**Sublayers of Data Link Layer** :

* Logical Link Control (LLC)

* Media Access Control (MAC)

## **Layer 3: Network Layer** :

The network layer works for the transmission of data from one host to the other located in different networks. It also takes care of packet routing i.e. selection of the shortest path to transmit the packet, from the number of routes available.

* The sender and receiver's IP address are placed in the header by the network layer.
* Segment in the Network layer is referred to as a Packet.
* The network layer is implemented by networking devices such as routers and switches.

## **Layer 4: Transport Layer** :
The transport layer provides services to the application layer and takes services from the network layer. The data in the transport layer is referred to as Segments. It is responsible for the end-to-end delivery of the complete message.

* The transport layer also provides the acknowledgement of the successful data transmission and re-transmits the data if an error is found.
* Protocols used in the Transport Layer are TCP, UDP NetBIOS, PPTP.
* At the sender's side, the transport layer receives the formatted data from the upper layers, performs Segmentation, and also implements Flow and error control to ensure proper data transmission.
* It also adds Source and Destination port number in its header and forwards the segmented data to the Network Layer.
* Generally, this destination port number is configured, either by default or manually.
* Example: when a web application requests a web server, it typically uses port number 80, because this is the default port assigned to web applications. Many applications have default ports assigned.
* At the Receiver’s side, Transport Layer reads the port number from its header and forwards the Data which it has received to the respective application. It also performs sequencing and reassembling of the segmented data.
      
## **Layer 5: Session Layer** :

Session Layer in the OSI Model is responsible for the establishment of connections, management of connections, terminations of sessions between two devices. It also provides authentication and security. Protocols used in the Session Layer are NetBIOS, PPTP.

 ![session layer](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/communication.jpg?raw=true)

**=> Functions of the Session Layer** :

* Session Establishment, Maintenance, and Termination: The layer allows the two processes to establish, use, and terminate a connection.
* Synchronisation: This layer allows a process to add checkpoints that are considered synchronisation points in the data. These synchronisation points help to identify the error so that the data is re-synchronised properly, and ends of the messages are not cut prematurely,and data loss is avoided.
* Dialog Controller: The session layer allows two systems to start communication with each other in half-duplex or full-duplex.


## **Layer 6: Presentation Layer** :
The presentation layer is also called the Translation layer. The data from the application layer is extracted here and manipulated as per the required format to transmit over the network. Protocols used in the Presentation Layer are TLS/SSL (Transport Layer Security / Secure Sockets Layer).JPEG, MPEG, GIF, are standards or formats used for encoding data, which is part of the presentation layer’s role.

**=> Functions of the Presentation Layer** :

* Translation: For example, ASCII to EBCDIC.
* Encryption/ Decryption: Data encryption translates the data into another form or code. The encrypted data is known as the ciphertext, and the decrypted data is known as plain text. A key value is used for encrypting as well as decrypting data.
* Compression: Reduces the number of bits that need to be transmitted on the network.


## **Layer 7: Application Layer** : 

At the very top of the OSI Reference Model stack of layers, we find the Application layer which is implemented by the network applications. These applications produce the data to be transferred over the network.
      
* This layer also serves as a window for the application services to access the network and for displaying the received information to the user.
* Protocols used in the Application layer are SMTP, FTP, DNS, etc.

![application layer](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/application-layer.gif?raw=true)

**Functions of the Application Layer** :
The main functions of the application layer are given below.

* Network Virtual Terminal (NVT): It allows a user to log on to a remote host.
* File Transfer Access and Management (FTAM): This application allows a user to access files in a remote host, retrieve files in a remote host, and manage or control files from a remote computer.
* Mail Services: Provide email service.
* Directory Services: This application provides distributed database sources and access for global information about various objects and services. 


## Data Flows in the OSI Model?

When we transfer information from one device to another, it travels through 7 layers of OSI model. First data travels down through 7 layers from the sender's end and then climbs back 7 layers on the receiver's end. 

**Data flows through the OSI model in a step-by-step process:**

* Application Layer: Applications create the data.
* Presentation Layer: Data is formatted and encrypted.
* Session Layer: Connections are established and managed.
* Transport Layer: Data is broken into segments for reliable delivery.
* Network Layer: Segments are packaged into packets and routed.
* Data Link Layer: Packets are framed and sent to the next device.      
* Physical Layer: Frames are converted into bits and transmitted physically.

## **TCP/IP Protocol Suite**:

The TCP/IP model is a framework that is used to model the communication in a network. It is mainly a collection of network protocols and organization of these protocols in different layers for modeling the network.

* It has four layers, Application, Transport, Network/Internet and Network Access.
* While the OSI model has seven layers, the 4 layer TCP/IP model is simpler and commonly used in today’s Internet and networking systems.

### **Role of TCP/IP** :

One of its main goals is to make sure that the data sent by the sender arrives safely and correctly at the receiver’s end. To do this, the data is broken down into smaller parts called packets before being sent. These packets travel separately and are reassembled in the correct order when they reach the destination.

![Tcp image-2](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/tcp_ip-2.webp?raw=true)


## **Layers of TCP/IP Model** :

***1. Application Layer*** : 

The Application Layer is the top layer of the TCP/IP model and the one closest to the user. This is where all the apps you use like web browsers, email clients, or file sharing tools connect to the network.

* It acts like a bridge between your software (like Chrome, Gmail, or WhatsApp) and the lower layers of the network that actually send and receive data.
* It supports different protocols like HTTP (for websites), FTP (for file transfers), SMTP (for emails), and DNS (for finding website addresses).
* It also manages things like data formatting, so both sender and receiver understand the data, encryption to keep data safe, and session management to keep track of ongoing connections.
 
***2. Transport Layer*** :

The Transport Layer is responsible for making sure that data is sent reliably and in the correct order between devices. It checks that the data you send like a message, file, or video arrives safely and completely.

* This layer uses two main protocols: TCP and UDP, depending on whether the communication needs to be reliable or faster.
* TCP is used when data must be correct and complete, like when loading a web page or downloading a file.
* It checks for errors, resends missing pieces, and keeps everything in order. On the other hand, UDP (User Datagram Protocol) is faster but doesn’t guarantee delivery useful for things like live video or online games where speed matters more than perfect accuracy.

***3. Internet Layer*** :

The Internet Layer is used for finding the best path for data to travel across different networks so it can reach the right destination. It works like a traffic controller, helping data packets move from one network to another until they reach the correct device.

* This layer uses the Internet Protocol (IP) to give every device a unique IP address, which helps identify where data should go.
* The main job of this layer is routing deciding the best way for data to travel.
* It also takes care of packet forwarding (moving data from one point to another), fragmentation (breaking large data into smaller parts), and addressing.

***4. Network Access Layer*** :

The Network Access Layer is the bottom layer of the TCP/IP model. It deals with the actual physical connection between devices on the same local network like computers connected by cables or communicating through Wi-Fi.

* This layer makes sure that data can travel over the hardware, such as wires, switches, or wireless signals.
* It also handles important tasks like using MAC addresses to identify devices, creating frames (the format used to send data over the physical link), and checking for basic errors during transmission.

## ***Working of TCP/IP Model*** :

The working of TCP/IP can be explained with the help of the diagram given below and explained :

![Tcp image-1](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/tcp_ip-1.webp?raw=true)



### When Sending Data (From Sender to Receiver)

* Application Layer: Prepares user data using protocols like HTTP, FTP, or SMTP.
* Transport Layer (TCP/UDP): Breaks data into segments and ensures reliable (TCP) or fast (UDP) delivery.
* Internet Layer (IP): Adds IP addresses and decides the best route for each packet.
* Link Layer (Network Access Layer): Converts packets into frames and sends them over the physical network.

### When Receiving Data (At the Destination)

* Link Layer: Receives bits from the network and rebuilds frames to pass to the next layer.
* Internet Layer: Checks the IP address, removes the IP header, and forwards data to the Transport Layer.
* Transport Layer: Reassembles segments, checks for errors, and ensures data is complete.
* Application Layer: Delivers the final data to the correct application (e.g., displays a web page in the browser).

## Domain Name System (DNS) :

DNS is a hierarchical and distributed naming system that translates domain names into IP addresses. When you type a domain name like www.github.com into your browser, DNS ensures that the request reaches the correct server by resolving the domain to its corresponding IP address.

### ***Working of DNS*** :

The DNS process can be broken down into several steps, ensuring that users can access websites by simply typing a domain name into their browser. 


* User Input: You enter a website address (for example, www.github.com) into your web browser.
* Local Cache Check: Your browser first checks its local cache to see if it has recently looked up the domain. If it finds the corresponding IP address, it uses that directly without querying external servers.
* DNS Resolver Query: If the IP address isn’t in the local cache, your computer sends a request to a DNS resolver. The resolver is typically provided by your Internet Service Provider (ISP) or your network settings.
* Root DNS Server: The resolver sends the request to a root DNS server. The root server doesn’t know the exact IP address for www.geeksforgeeks.org but knows which Top-Level Domain (TLD) server to query based on the domain’s extension (e.g., .org, com, etc).
* TLD Server: The TLD server for .org directs the resolver to the authoritative DNS server for geeksforgeeks.org.
Authoritative DNS Server: This server holds the actual DNS records for geeksforgeeks.org, including the IP address of the website’s server. It sends this IP address back to the resolver.
* Final Response: The DNS resolver sends the IP address to your computer, allowing it to connect to the website’s server and load the page.

### ***Structure of DNS*** :

DNS operates through a hierarchical structure, ensuring scalability and reliability across the global internet infrastructure. Here's how it’s organized:

![DNS root-image](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/root_dns_server.webp?raw=true)

* Root DNS Servers: These are the highest-level DNS servers and know where to find the TLD servers. They are crucial for directing DNS queries to the correct locations.
* TLD Servers: These servers manage domain extensions like .com, .org, .net, .edu, .gov and others. They help route queries to the authoritative DNS servers for specific domains.
* Authoritative DNS Servers: These are the servers that store the actual DNS records for domain names. They are responsible for providing the correct IP addresses that allow users to reach websites.

### ***Types of Domains*** :

DNS helps manage a wide variety of domain types to organize the vast number of websites on the internet. Here are the primary categories:

* Generic Domains: These include top-level domains like .com, .org, .net and .edu. These are widely used and recognized across the world.
* Country Code Domains: These domains represent specific countries or regions, such as .in for India, .us for the United States, .uk for the United Kingdom and .jp for Japan.
* Inverse Domains: Used for reverse DNS lookups, these domains help map IP addresses back to domain names. Reverse DNS lookups are useful for diagnostics and security purposes, ensuring that the source of network traffic is legitimate. So DNS can provide both the mapping for example to find the IP addresses of github.com then we have to type  "nslookup www.github.com"

  ![DNS domain-root-image](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/root.webp?raw=true)

## **Domain Name Server** :

The client machine sends a request to the local name server, which, if the root does not find the address in its database, sends a request to the root name server, which in turn, will route the query to a top-level domain (TLD) or authoritative name server.

* The root name server can also contain some hostName to IP address mappings.
* The Top-level domain (TLD) server always knows who the authoritative name server is.
* So finally the IP address is returned to the local name server which in turn returns the IP address to the host.

### ***DNS Lookup*** :

DNS Lookup, also called DNS Resolution, is the process of translating a human-readable domain name into its corresponding IP address. The process involves:

* DNS Resolver: Initiates the lookup process. Also called a DNS client.
* Recursive Query: Resolver queries multiple servers on behalf of the client until the IP is found.
* Iterative Query: Resolver asks servers for the best answer available.
* Non-Recursive Query: Resolver queries a server that already has the record in its cache.

 ### ***Note** : 
 => for Deep understanding Visit (https://www.geeksforgeeks.org/computer-networks/domain-name-system-dns-in-application-layer).


## HTTPS / HTTP :

HTTP and HTTPS are protocols for transferring data between a web browser and a website; HTTP is the basic, unsecured protocol that sends data in plain text, while HTTPS is the secure, encrypted version that adds a layer of security using TLS/SSL encryption. 

* HTTPS uses port 443, whereas HTTP uses port 80. Key differences include encryption (HTTP is unsecured, HTTPS is secured), data transmission (HTTP is plain text, HTTPS is encrypted), and URL prefix (http:// vs. https://).

  ### ***HTTP(Hypertext Transfer Protocol)*** :

* What it is: The foundational protocol for data communication on the web.
* How it works: Your browser uses it to send requests to a server and receive a response, which is how web pages are loaded.
* Security: Sends data in plain text. This is like sending a postcard—anyone who intercepts it can read it.
* Port: Uses port 80 by default.
* Use case: Suitable for non-sensitive data transfer.

  ### ***HTTPS(Hypertext Transfer Protocol Secure)*** :

* What it is: The secure version of HTTP, providing encryption and verification.
* How it works: It wraps HTTP in a security layer using protocols like TLS (Transport Layer Security) or SSL (Secure Sockets Layer).
* Security: Encrypts the data sent between your browser and the server, making it unreadable to those who might intercept it. This is like sending a message in a locked box.
* Port: Uses port 443 by default.
* Use case: Essential for transmitting sensitive information like passwords, credit card numbers, and other personal data. Modern browsers will flag non-HTTPS sites as "not secure". 

   
