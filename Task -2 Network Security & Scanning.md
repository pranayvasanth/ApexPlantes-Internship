# Objective:
* Learn reconnaissance, scanning, and network traffic analysis.

### Sub-Tasks:

1. Reconnaissance.
2. Port & Service Scanning.
3. Vulnerability Scanning.
4. Packet Analysis with Wireshark.
5. Firewall Basics.

## 1. Reconnissance :
  
### **Definition** : 
  Recconnaissance is the initial phase of a cyberattack or Penetration test where the attacker gathers as much information as possible about a target system, network, or organisation.

### Types of Reconnaissance :
---
  
#### **1.Passive Reconnaissance:** 
  
* Gathering information about a target without directly interacting with the target system or network. It's like observing from a distance.

* **Key Characteristic**: Low risk of detection, as it relies on publicly available information (Open-Source intelligence, or OSINT).

**Tools & Commands:**

1.**Whois :**

* The Whois protocol is a query and response protocol used widely for querying databases that store the registered users or assignees of an Internet resource, such as a domain name, an IP address block, or an autonomous system.

![Whois -image](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/Screenshot%202025-11-25%20183110.png?raw=true)

* Whois provided the Registry Domain Id, Registrar WHOIS Server.
* Creation date, Expiration date, registrar company name.
* censored Registrar Contact email and Phone (which are not accurate).
* Also provides information about the Registry country, city, and several Name servers.
  
![Whois -image](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/Screenshot%202025-11-25%20183147.png?raw=true)

2.**NslookUp :**

* Nslookup is used to illustrate:
  1. Find the IP address of a host.
  2. Find the domain name os a domain.
  3. Find mail servers for a domain.
  4. Find Name servers for a host.

#### How to use Ns-lookup: 

 * Nslookup is a network administration command-line tool available for many computer operating systems.
* Nslookup is used for troubleshooting DNS-related problems.
* Nslookup can be used in interactive and non-interactive mode.
* To use in interactive mode, type nslookup at the command line and hit return.
* You should get  an nslookup command prompt.

### Use-Case :

![nslookup image](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/nslookup.png?raw=true)

* In this Use-case I used Nslookup to obtain IPv6 and IPv4 addresses of Goboult.
* To obtain the MailTransfer servers used by the ApexPlanet website.


3.**Google Dorking:**

Google dorking is often termed as "Google hacking."

* This is a technique designed to utilise Google's Search services to research data and in file data  from different domains through the use of different search operators.

#### Search Operators :

* **Site :** This Operator signifies the specific site required.
*  **In-url :** Check for the keyword in different URLs.
*  **In-title :** To search for the specified Keyword in the title of the webpage.
*   **In-text :** This is to search for a keyword in the body of the webpage.
*   **FileType :** Defines the type of data to search for specific files.

### Use-Case :
![image google-dorking](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/googledork.png?raw=true)

![image dorking](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/googledorking.png?raw=true)


### **2. Active Reconnaissance :**

* Gather information by directly interacting with the target system or network. This involves sending probes or packets to the target.

* **Key Characteristic**:  Higher risk of detection (it leaves logs), but it often yields more detailed and real-time information. 

* **Tools & Commands :**

#### **1. Ping Sweep :** 

A Ping Sweep is a method used to find out which IP addresses in a specific range are "alive" (active) and which are not. Instead of pinging one computer at a time, you scan an entire subnet (e.g., 192.168.1.1 to 192.168.1.254) simultaneously.

* It works by sending ICMP Echo Request packets to multiple IP addresses. If a computer is active and configured to reply, it sends back an ICMP Echo Reply (the "Pong").

  **Tool,Command,Explanation :**
  
* Telnet,telnet 192.168.1.10 21, : "Connects to IP 192.168.1.10 on port 21 (FTP). If open, the server might reply: 220 vsFTPd 3.0.3."

* Netcat (nc),nc -v 192.168.1.10 80, : Connects to port 80 (Web). You might need to type HEAD / HTTP/1.0 and hit Enter twice to see the web server version.

* Nmap,nmap -sV 192.168.1.10, : The -sV flag specifically instructs Nmap to probe open ports to determine service/version info.

* Curl,curl -I 192.168.1.10, : "The -I flag fetches the HTTP Header only, which usually contains the Server: banner (e.g., nginx/1.18.0)."

![Ping sweep image](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/ping%20sweep.png?raw=true)

#### **2. Banner grabbing :**

Banner Grabbing is the process of connecting to a specific open port on a device to read the "Welcome Banner." This banner usually contains the software name and version number running on that port.

* When you establish a connection (handshake) with a service (like an FTP, SSH, or Web server), the service often sends a text string to identify itself before you even log in.

  **Tool,Command,Explanation :**
  
* Telnet,telnet 192.168.1.10 21, : "Connects to IP 192.168.1.10 on port 21 (FTP). If open, the server might reply: 220 vsFTPd 3.0.3."
* Netcat (nc),nc -v 192.168.1.10 80, : Connects to port 80 (Web). You might need to type HEAD / HTTP/1.0 and hit Enter twice to see the web server version.
*  Nmap,nmap -sV 192.168.1.10, : The -sV flag specifically instructs Nmap to probe open ports to determine service/version info.
* Curl,curl -I 192.168.1.10, : "The -I flag fetches the HTTP Header only, which usually contains the Server: banner (e.g., nginx/1.18.0)."
  ![Banner image](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/banner.png?raw=true).

## 2.Ports & Service Scanning :  

### Nmap :

Nmap (Network Mapper) is a free, open-source utility used for network discovery and security auditing. It is the industry standard tool for network administrators and security professionals to map out networks, identifying what devices are running, what services they offer, and what operating systems they are using.

#### **Functions of Nmap :**

Nmap is versatile, but its primary functions generally fall into four categories:

**1.Host Discovery (Ping Scanning):**

* Determines which hosts (computers, servers, routers) on a network are actually "alive" or online.

* It filters out IP addresses that are not currently in use so you don't waste time scanning empty space.

**2.Port Scanning:**

* This is Nmap's bread and butter. It probes specific "ports" on a target machine to see which ones are open.

* Open Port: Indicates a service is listening (e.g., Port 80 for a web server).

* Closed/Filtered Port: Indicates the port is rejecting connections or is hidden behind a firewall.

**3.Service Version Detection:**

* Once Nmap finds an open port, it can query it further to find out exactly what application is running and what version it is (e.g., "Apache Web Server 2.4.41"). This is crucial for finding vulnerabilities associated with specific software versions.

**Operating System (OS) Detection:**

* Nmap analyzes the subtle characteristics of the data packets returned by the target (a process called "TCP/IP stack fingerprinting") to guess the operating system (e.g., Linux, Windows 10, macOS).
