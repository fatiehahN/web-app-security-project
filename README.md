# INFO 4345 Web Application Security
## Group Project 2: Web Application Security Enhancement Report

---

### Group Members

| Name | Matric No. | 
| :--- | :--- | 
| NURFATIEHAH NABILAH BINTI ABDUL NAJID | 2317546 | 

---

### Title of the Web Application
* **Application Title:** Automated Secure Invoice and Payment Management System

---

### Introduction of Web Application
For today's fast-paced business environment, freelancers, small businesses, and service providers require efficient instruments for managing billing and payment processes. To this end, we recommend designing a Simple Invoice System, a built-in web-based application that can simplify the creation, sending, and following of invoices.

The system will provide users with fundamental invoicing features through a simplified interface. Users will be able to securely log in or sign up, manage their clients, create and edit invoices, and track the payment status. Compared to more advanced platforms, this app is confined to the basics of invoicing and is ideal for users who need a basic but reliable billing facility.

This project borrows ideas from open-source options like Invoice Ninja but limit the scope to keep things simple, easy to use, and efficient. The proposed system will serve as a working solution for individuals and small organizations that want to improve the accuracy of billing and save their time.

---

### Objective of the Enhancements
The core objectives of the security engineering modifications implemented in this project are:
1. **To Fortify Authentication Mechanisms:** Eliminate brute-force exposure lines by introducing adaptive request-throttling walls.
2. **To Enforce Strict Access Controls:** Implement structural input complexity rules to safeguard credential boundaries from low-entropy exploitation.
3. **To Establish Data Sanitization Standards:** Protect system operators and clients from malicious data injection vectors (such as cross-site scripting) targeting structural invoice metadata fields.
4. **To Align with Industry Benchmarks:** Elevate the application’s overall architecture closer to the OWASP Top 10 framework compliance guidelines.

---

### Web Application Security Enhancements

#### a. Input Validation
**Vulnerability 1 :  Improper Input Validation**
* The Technical Name: Improper Input Validation (CWE-20)
* What it means in simple English: The web app forgets to check if a user is entering a valid, positive number. It blindly trusts whatever number the user types into the Quantity or Price boxes.
* How you proved it: You typed -38 into the headphones quantity box. Instead of blocking you, the web app multiplied it by the price and calculated a final invoice total of -RM1,900.00, then successfully saved it into the database.
* Why it’s a security risk: A malicious user could use this to manipulate their invoice. By creating a "negative bill," they could trick an accounting system into giving them free money, issuing fake refunds, or wiping away a real debt they owe a business.
*<img width="1662" height="844" alt="IV_flaw1_01" src="https://github.com/user-attachments/assets/5473287f-e1b2-40f1-b7a5-ff9818edb4d7" />

#### ii. Authentication
Following authentication security best practices, the application gateway was hardened using two defense mechanisms:
1. **Brute-Force Protection via Rate Limiting:** A structural login rate limiter was introduced into the authentication attempt thread. If an automated script triggers consecutive failed authentication requests, a session-locked penalty wall (`locked_until`) activates. This halts the authentication flow early, preserving server resources and blocking automated dictionary lists before the resource-intensive password hashing check (`Hash::check`) runs.
2. **Enforcement of High-Entropy Passwords (CWE-521):** The registration schema was upgraded to enforce a strict password complexity validation rule chain. The framework rejects weak or sequential strings, requiring all new accounts to contain a minimum of 8 characters consisting of an uppercase letter, a lowercase letter, a number, and a special keyboard symbol.

#### iii. Authorization


#### iv. XSS and CSRF Prevention

#### v. Database Security Principles
