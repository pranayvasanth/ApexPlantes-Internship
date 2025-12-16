## Objective :

* SQL Injection.
* Cross-Site Scripting (XSS).
* Cross-Site Request Forgery (CSRF).
* File-Inclusion Attacks.
* Burp Suite Advanced.
* Web Security Headers.

### 🛡️ SQL Injection :

SQL Injection (SQLi) is a type of vulnerability that occurs when an attacker can interfere with the queries that an application makes to its database. 
This interference is usually achieved by injecting malicious SQL code into fields intended for user data.
  
* When a web application takes user input and directly includes it in a SQL query without proper sanitation or validation, it becomes vulnerable.
  The injected SQL code can be interpreted by the database as part of the original query, allowing the attacker to:

* View data they are not normally able to retrieve (e.g., unauthorised customer information or credentials).
* Modify or delete existing data.
* Gain administrative control over the database server.

 **Use-Case :**

* ***Retrieving Users data :***

   Query Used : **1' OR '1' = '1 UNION SELECT user,passwords FROM users#**  

![SQli Image-data](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/SQLI%20users-data.png?raw=true)

* ***Cracking the hash-codes to get Passwords :***

![SQLi image-pass](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/SQLi%20users-pass.png?raw=true)


### 🛑 Prevention Methods for SQL Injection

* Preventing SQL Injection requires implementing secure coding practices. Here are the most effective and widely recommended methods:

* **Using  Prepared Statements (with Parameterized Queries)**
  
 This is the most effective defense mechanism. Instead of building a query string by concatenating user input, you use a prepared statement. The query structure is sent to the database first, and then the user input is sent as a parameter.

* ***How it works :*** The database engine treats the user input as a literal string value, never as executable SQL code, regardless of what characters it contains (like ' or --).


## Cross-Site Scripting (XSS):

Cross-Site Scripting (XSS) is a type of security vulnerability typically found in web applications. It occurs when an application includes untrusted data in a web page without proper validation or escaping. This allows an attacker to inject malicious scripts (usually JavaScript) into the web pages viewed by other users.

* The victim's browser has no way to know that the script is untrustworthy and will execute it, potentially leading to session hijacking, unauthorized data access, or website defacement.

### 1. Stored XSS Attack (on DVWA)

Stored XSS (also known as Persistent XSS) is the most dangerous type because the malicious script is permanently stored on the target server (e.g., in a database, a comment field, or a guestbook).

* Example on DVWA (Damn Vulnerable Web Application):
Navigate to the "XSS (Stored)" security module.

* The Goal: Inject a script into the "Message" or "Name" field that will trigger every time a user visits the page.


***The Payload: Enter the following into the comment box:***

![xss stored code-injected](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/XSS%20Stored.png?raw=true)


***Result:*** 
![xss result of stored](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/XSS%20Reflect.png?raw=true)

### 2. Reflected XSS using Query Parameters

Reflected XSS occurs when the malicious script is "reflected" off a web application to the victim's browser. It isn't stored permanently; instead, it is delivered via a link (usually in a URL parameter).

 **Code I injected:**
 ![XSS reflected Source-code](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/XSS%20Reflect%202.png?raw=true)


### How it works:
* If a website takes a search query and displays it back on the page (e.g., "You searched for: [query]"), an attacker can craft a URL that includes a script instead of a search term.

* Vulnerable URL: http://example.com/search?q=laptops

* Malicious URL: http://example.com/search?q=<script>alert('XSS')</script>

  ![XSS Reflected image](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/XSS%20Reflect.png?raw=true)
When a victim clicks this link, the server receives the script in the q parameter and reflects it back into the HTML. The victim's browser then executes the script.

### Mitigation Strategies

To defend against XSS, you must implement a "defense-in-depth" approach.

***A. Input Validation & Output Encoding:***

* Input Validation: Ensure that the data received matches expected formats (e.g., a "Age" field should only accept numbers). Use "allow-lists" rather than "deny-lists."

* Output Encoding: This is the most effective defense. Before rendering user-supplied data in HTML, convert special characters into their HTML entity equivalents.

* "< becomes &lt;"

* "> becomes &gt;"

* This ensures the browser treats the input as text rather than executable code.

***B. Content Security Policy (CSP):***

* A Content Security Policy is an HTTP response header that tells the browser which sources of scripts are trusted.

* How it helps: Even if an attacker manages to inject a <script> tag, a strong CSP can prevent it from running by:

* Disallowing inline scripts (scripts written directly in the HTML).

* Restricting script execution to trusted domains only.

* Example Header: Content-Security-Policy: default-src 'self'; script-src https://trustedscripts.com; (This tells the browser to only execute scripts from the site's own origin or a specific trusted domain.)


## Cross-Site Request Forgery (CSRF) 

Cross-Site Request Forgery (CSRF) is a web security vulnerability that allows an attacker to trick an authenticated user's browser into sending an unauthorized request to a web application.

* The attack exploits the way browsers automatically handle session cookies. If you are logged into a site (like your bank or a webmail service), your browser sends your session cookie with every request to that site. An attacker can use this behavior to "forge" a request—such as changing a password or transferring funds—without your knowledge or consent.

### CSRF Attack Example (on DVWA)
In the Damn Vulnerable Web Application (DVWA), the "CSRF" module allows you to change the current user's password. Under Low security, the application does not verify where the request came from or if the user intended to make it.

### The Vulnerability
When you change your password in DVWA, the browser sends a GET request like this: http://127.0.0.1/vulnerabilities/csrf/?password_new=secret&password_conf=secret&Change=Change

### The Exploit

An attacker can create a malicious HTML page and host it on a different server. They then trick the logged-in victim into visiting this page (e.g., via a phishing email).

Example Malicious Payload (attack.html):

![csrf forged-site](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/after%20pass%20changed.png?raw=true)

#### HTML

    <html><form action="http://127.0.0.1/DVWA/CSRF/" method="POST">  
    Click to Get a New Iphone <input type="hidden" value="12345" name="new_password">
    <input type="hidden" name="user_token" value="12345">
    <input type="submit" value="submit">
    </form>
    </body>
    </html>

***HTML Page***
![csrf image index.html](https://github.com/pranayvasanth/ApexPlantes-Internship/blob/main/forged%20site.png?raw=true)

* When the victim opens attack.html, their browser automatically tries to "fetch" the image. Because the URL is actually a password change command, and because the victim is already logged into DVWA, the browser attaches the victim's session cookies. DVWA receives the request, sees a valid session, and changes the password to "hacked" silently in the background.


### Token-Based Protection (Mitigation)

The most effective way to prevent CSRF is the Synchronizer Token Pattern.

***How it Works:*** 

* Generation: When the server sends a sensitive form (like "Change Password") to the user, it generates a unique, cryptographically strong, and unpredictable CSRF Token.

* Embedding: This token is embedded into the HTML form as a hidden field.

Verification: When the user submits the form, the browser sends the token back to the server. The server compares the token in the request with the one stored in the user's session.

***Why it Stops the Attack:***

* In a CSRF attack, the attacker's malicious site can trigger a request to the vulnerable server, but the attacker cannot see or guess the unique token required to validate that request. Because the server expects a token and the forged request doesn't have the correct one, the server rejects the action.

Example Secure Form:

#### HTML

<form action="/change-password" method="POST">
    <input type="password" name="new_password">
    <input type="hidden" name="user_token" value="8f3a92b1c4e5d6f7a8b9c0d1e2f3a4b5">
    <input type="submit" value="Change">
</form>



*
? (The input is bound to ? as a value, not code.)
