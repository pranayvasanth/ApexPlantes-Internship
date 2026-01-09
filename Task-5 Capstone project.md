# Web Application Penetration Test Report

**Target Application:** DVWA (Damn Vulnerable Web App)

**Security Level:** Low / Medium (Simulated)

---

## 1. Objectives, Scope, Tools, & Timeline

### 1.1 Objectives

* To identify security vulnerabilities within the DVWA web application.
* To demonstrate the potential impact of these vulnerabilities if exploited by a malicious actor.
* To provide actionable remediation strategies to secure the application.

### 1.2 Scope

* **In Scope:**
* Target URL: `http://[Target_IP]/dvwa/`
* Modules: Brute Force, Command Injection, SQL Injection, XSS (Stored & Reflected).


* **Out of Scope:**
* Denial of Service (DoS) attacks.
* Physical security of the server.
* Social Engineering of users.



### 1.3 Tools Used

* **Kali Linux:** Operating System.
* **Burp Suite Community:** Proxy and traffic analysis.
* **Nmap:** Network scanning.
* **Nikto:** Web server scanning.
* **Hydra:** Brute force testing.
* **SQLMap:** Automated SQL injection (controlled).

### 1.4 Timeline

* **Start Date:** Jan 08, 2026
* **End Date:** Jan 09, 2026
* **Phase 1:** Reconnaissance (2 Hours)
* **Phase 2:** Exploitation (4 Hours)
* **Phase 3:** Reporting (2 Hours)

---

## 2. Network Architecture Diagram

*Below is a representation of the test environment. The attacker (Kali Linux) connects to the target (Metasploitable/DVWA) over a local network.*

```mermaid
graph LR
    A[Attacker Machine<br/>(Kali Linux)<br/>IP: 192.168.1.10] -- HTTP/TCP --> B[Firewall / Router]
    B -- Port 80 --> C[Web Server<br/>(Apache/DVWA)<br/>IP: 192.168.1.15]
    C -- Queries --> D[(MySQL Database)]
    
    style A fill:#f9f,stroke:#333,stroke-width:2px
    style C fill:#bbf,stroke:#333,stroke-width:2px
    style D fill:#dbd,stroke:#333,stroke-width:2px

```

---

## 3. Reconnaissance & Scanning

### 3.1 Nmap Network Scan

**Objective:** Identify open ports and running services.
**Command:** `nmap -sV -sC -p- 192.168.1.15`

**Findings:**

* **Port 80 (HTTP):** Apache Web Server running DVWA.
* **Port 3306 (MySQL):** Database service accessible.

 **[Insert Screenshot Here: Nmap scan output showing open ports]**

### 3.2 Nikto Web Scan

**Objective:** Scan for outdated server software and misconfigurations.
**Command:** `nikto -h http://192.168.1.15/dvwa`

**Findings:**

* Server leaks version headers (Apache 2.x).
* `config.inc.php` backup files found.
* Directory indexing enabled.

---

## 4. Exploitation & Findings (Documented with Evidence)

### Finding #1: Remote Command Injection

* **Severity:** **CRITICAL**
* **Vulnerability Type:** CWE-78: OS Command Injection
* **Location:** `/vulnerabilities/exec/`

**Description:**
The application allows users to "Ping" an IP address. The input is not properly sanitized, allowing an attacker to chain system commands using the `;` or `|` operators.

**Exploitation Steps:**

1. Navigate to "Command Injection".
2. Enter the payload: `127.0.0.1; cat /etc/passwd`
3. The application executes the ping and *then* executes the `cat` command, displaying the server's password file.

**Tool Output / Evidence:**

```text
uid=0(root) gid=0(root) groups=0(root)
uid=33(www-data) gid=33(www-data) groups=33(www-data)

```

> **[Insert Screenshot Here: Browser showing the contents of /etc/passwd appearing on the page]**

---

### Finding #2: SQL Injection (Union Based)

* **Severity:** **HIGH**
* **Vulnerability Type:** CWE-89: SQL Injection
* **Location:** `/vulnerabilities/sqli/`

**Description:**
The "User ID" input field is susceptible to SQL injection. It fails to validate numerical input, allowing an attacker to inject SQL queries to retrieve sensitive data from the database.

**Exploitation Steps:**

1. Navigate to "SQL Injection".
2. Input a standard test payload: `1' OR '1'='1`
3. The application dumps all user information (First Name, Surname) because the statement evaluates to True.
4. Advanced Payload to extract database version: `1' UNION SELECT null, version() #`

**Tool Output / Evidence:**

> **[Insert Screenshot Here: DVWA page listing all users (admin, gordonb, pablo) after the injection]**

---

### Finding #3: Stored Cross-Site Scripting (XSS)

* **Severity:** **MEDIUM**
* **Vulnerability Type:** CWE-79: Stored XSS
* **Location:** `/vulnerabilities/xss_s/` (Guestbook)

**Description:**
The "Guestbook" feature stores user comments without sanitizing HTML/JavaScript tags. When other users view the guestbook, the malicious script executes in their browser.

**Exploitation Steps:**

1. Navigate to "XSS (Stored)".
2. In the "Message" field, enter: `<script>alert('Hacked by Gemini')</script>`
3. Click "Sign Guestbook".
4. Reload the page. The alert box pops up immediately.

**Evidence:**

> **[Insert Screenshot Here: Browser showing the Alert Pop-up box over the DVWA interface]**

---

## 5. Mitigation Strategies

| Vulnerability | Remediation Strategy |
| --- | --- |
| **Command Injection** | **Avoid System Calls:** Do not use `exec()` or `passthru()` functions with user input. Use built-in PHP functions instead. <br>

<br> **Input Validation:** Use whitelist validation (only allow IP address patterns). |
| **SQL Injection** | **Prepared Statements:** Use PDO (PHP Data Objects) with parameterized queries. This ensures input is treated as data, not executable code. |
| **Stored XSS** | **Output Encoding:** Convert special characters to HTML entities (e.g., `<` becomes `&lt;`) using `htmlspecialchars()` before displaying data. |
| **Weak Credentials** | **Enforce Strong Passwords:** Require complex passwords and implement rate-limiting (e.g., Fail2Ban) to stop brute-force attacks. |

---

## 6. Executive Summary (Professional Wrap-up)

**Assessment Overview:**
A security assessment was conducted on the DVWA (Damn Vulnerable Web App) platform on January 9, 2026. The goal was to identify critical security flaws that could compromise the confidentiality, integrity, and availability of the system.

**Key Findings:**
The application is **highly insecure** in its current state. Critical vulnerabilities were identified, including **Remote Command Execution**, which allows an attacker full control over the server, and **SQL Injection**, which allows unrestricted access to the database. Additionally, **XSS** vulnerabilities pose a risk to client-side security.

**Recommendation:**
It is recommended to immediately patch the application by implementing **input validation** and **parameterized queries**. A full code review is required before deploying this application to any production environment.
