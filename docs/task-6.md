# Task 6 - Security Notes

## Session Vulnerabilities

A session is used so the website can remember the user after login.
Instead of logging in every time, the system gives the user a session ID stored in cookies.

### The Problem

If an attacker gets access to the session ID, they can use the account without needing the password.

### Types of Attacks

* Session Hijacking
  This happens when someone steals the session ID and uses it.

* Session Fixation
  The attacker forces the user to use a session ID he already knows, then waits until the user logs in.

### Protection

To make sessions more secure:

* Regenerate the session ID after login
* Use HTTPS
* Make cookies HttpOnly and Secure
* Add session timeout

I think session protection is very important because most websites depend on it for login.

---

## CSRF

### What is CSRF?

It is an attack where a user sends a request without realizing it.

For example, if a user is logged in and opens another website, that site might send a request using the same session.

### The Problem

The server trusts the session and thinks the request is coming from the real user.

### Solution

We use a CSRF token.

* Each form contains a unique token
* The server checks it before processing the request

If the token is missing or incorrect, the request is rejected.

Simple example: a hidden input field that contains a random token.

---

## XSS

### What is XSS?

XSS is when an attacker injects JavaScript code into a website.

### Example

If the website prints user input directly, an attacker can insert a script like:

<script>alert('test')</script>

### Types

* Stored XSS → saved in database
* Reflected XSS → returned in response

### Risks

* Stealing cookies
* Stealing sessions
* Performing actions as the user

### Protection

* Use htmlspecialchars
* Do not trust any user input

In my opinion, XSS is dangerous because it directly affects users.

---

## SQL Injection

### Idea

The attacker adds SQL code inside input fields to change the query.

### Example

Query:
SELECT * FROM users WHERE email = 'input'

Attacker input:
' OR 1=1

This makes the query always true and allows login without password.

### Protection

* Use prepared statements
* Validate input data

---

## File Upload Vulnerabilities

### The Problem

If the system allows file uploads without checking, attackers can upload harmful files.

### Risk

They might upload a PHP file and run it on the server.

### Protection

* Check file type
* Rename uploaded files
* Store them in a secure location

---

## Authentication Issues

### Problems

* Storing passwords without encryption
* Weak passwords
* No limit on login attempts

### Solutions

* Use password_hash
* Use password_verify
* Limit login attempts

---

## Validation vs Sanitization

* Validation means checking if the data is correct
* Sanitization means cleaning the data

Both should be used together to improve security.

---

## Best Practices

* Use HTTPS
* Never trust user input
* Always validate and sanitize
* Use prepared statements

---

## Conclusion

Any data coming from users should be treated as unsafe until checked.

Important attacks to understand:

* XSS
* SQL Injection
* CSRF
* Session attacks

If I focus on these points, I can build a more secure web application.
