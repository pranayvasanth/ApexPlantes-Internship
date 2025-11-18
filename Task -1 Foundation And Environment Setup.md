Objectives:

* The primary objectives of this module are to build strong fundamentals in:

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
### **4.Networing Basics**:
---
 *OSI Model Layers And Functions:

 The OSI (Open Systems Interconnection) Model is a set of rules that explains how different computer systems communicate over a network. The OSI Model was developed by the International Organisation for Standardisation (ISO). The OSI Model consists of 7 layers, and each layer has specific functions and responsibilities. This layered approach makes it easier for different devices and technologies to work together.   

 ![OSI Model](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/OSI_Model.jpg?raw=1)

## **Layer 1: Physical Layer** : 
--

The lowest layer of the OSI reference model is the Physical Layer. It is responsible for the actual physical connection between the devices. The physical layer contains information in the form of bits.

 * The Physical Layer is responsible for transmitting individual bits from one node to the next.
 * When receiving data, this layer will get the signal received and convert it into 0s and 1s and send them to the Data Link layer, which will put the frame back together.      
