# 🛡️ OWASP Web Application Penetration Testing

## Project Title  
**OWASP Web Application Vulnerability Assessment and Penetration Testing**

---

## Overview  
This repository contains a practical web application penetration testing project conducted on **OWASP Juice Shop**, mapped to **OWASP Top 10:2025**.  
The project demonstrates real-world vulnerabilities, exploitation techniques, impact analysis, and remediation strategies.

---

## Project Structure

```text
OWASP-Web-Application-Penetration-Testing/
├── Broken_Access_Control/
│   ├── IDOR_Horizontal_Privilege_Escalation/
│   │   ├── Evidence/
│   │   └── Notes.md
│   └── IDOR_Vertical_Privilege_Escalation/
│       ├── Evidence/
│       └── Notes.md
├── Injection/
│   ├── Cross_Site_Scripting_XSS/
│   │   ├── Evidence/
│   │   └── Notes.md
│   └── SQL_Injection/
│       ├── Evidence/
│       └── Notes.md
├── Security_Misconfiguration/
│   ├── Evidence/
│   └── Notes.md
├── OWASP_Web_Application_Penetration_Testing_Report.pdf
├── Scope.txt
└── Tools.txt
```

## Scope of Testing

Target Application: OWASP Juice Shop

Environment: Localhost (http://localhost:3000)

Testing Type: Web Application Penetration Testing

---

## Tools Used

Burp Suite

OWASP ZAP

Nmap

Nikto

Browser Developer Tools

Manual Payload Testing

---

## Vulnerabilities Identified
A01 – Broken Access Control

IDOR (Horizontal Privilege Escalation)

Vertical Privilege Escalation (Admin Access)

A02 – Security Misconfiguration

Directory listing enabled

Sensitive backup/config files exposed

A03 – Injection

Cross-Site Scripting (XSS)

SQL Injection (Authentication Bypass)

---

## Impact Summary

| Vulnerability              | Impact                         |
| -------------------------- | ------------------------------ |
| IDOR                       | User data exposure             |
| Admin Privilege Escalation | Full admin takeover            |
| XSS                        | Session hijacking, phishing    |
| SQL Injection              | Full database compromise       |
| Security Misconfiguration  | Internal configuration leakage |

---

## Remediation Recommendations

Implement server-side Role-Based Access Control (RBAC)

Use prepared statements / ORM

Apply output encoding and Content Security Policy (CSP)

Disable directory listing

Remove backup files from web root

Follow secure deployment and DevSecOps practices

---

 How to Run OWASP Juice Shop:

docker run -p 3000:3000 bkimminich/juice-shop

Open in browser:

http://localhost:3000

---

## Author

Yuvaraj S
Certified Penetration Tester (CPT)
Cybersecurity Enthusiast

---

## Disclaimer

This project is for educational and authorized testing only.
Do not test systems without explicit permission.
