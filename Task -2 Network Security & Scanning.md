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


### 2.** Active Reconnaissance:**

* Gather information by directly interacting with the target system or network. This involves sending probes or packets to the target.

* **Key Characteristic**:  Higher risk of detection (it leaves logs), but it often yields more detailed and real-time information. 
