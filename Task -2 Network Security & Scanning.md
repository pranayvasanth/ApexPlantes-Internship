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
  
**1.Passive Reconnaissance:** 
  
* Gathering information about a target without directly interacting with the target system or network. It's like observing from a distance.

* **Key Characteristic**: Low risk of detection, as it relies on publicly available information (Open-Source intelligence, or OSINT).

**Tools & Commands:**

i **Whois :**

* The Whois protocol is a query and response protocol used widely for querying databases that store the registered users or assignees of an Internet resource, such as a domain name, an IP address block, or an autonomous system.

![Whois -image](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/Screenshot%202025-11-25%20183110.png?raw=true)

* Whois provided the Registry Domain Id, Registrar WHOIS Server.
* Creation date, Expiration date, registrar company name.
* censored Registrar Contact email and Phone (which are not accurate).
* Also provides information about the Registry country, city, and several Name servers.
  
![Whois -image](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/Screenshot%202025-11-25%20183147.png?raw=true)

ii **NslookUp :**

 *

 
**2. Active Reconnaissance:**

* Gather information by directly interacting with the target system or network. This involves sending probes or packets to the target.

* **Key Characteristic**:  Higher risk of detection (it leaves logs), but it often yields more detailed and real-time information. 
