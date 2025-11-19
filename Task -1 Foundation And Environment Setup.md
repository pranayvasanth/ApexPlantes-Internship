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
