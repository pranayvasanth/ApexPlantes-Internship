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
