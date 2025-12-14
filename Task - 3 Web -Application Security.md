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
* This is the most effective defense mechanism. Instead of building a query string by concatenating user input, you use a prepared statement. The query structure is sent to the database first, and then the user input is sent as a parameter.

* ***How it works :*** The database engine treats the user input as a literal string value, never as executable SQL code, regardless of what characters it contains (like ' or --).

***Example (Conceptual) :***

 Vulnerable: SELECT * FROM users WHERE username = ' + user_input + '

* Secure (Prepared Statement): SELECT * FROM users WHERE username = ? (The input is bound to ? as a value, not code.)
