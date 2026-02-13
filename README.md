OWASP Juice Shop Web Application Penetration Testing Project
Project Title

OWASP Juice Shop Web Application Vulnerability Assessment and Penetration Testing

Overview

This repository contains a comprehensive penetration testing project performed on OWASP Juice Shop, aligned with the OWASP Top 10:2025 security risks.
The project demonstrates real-world web vulnerabilities, exploitation techniques, impact analysis, and remediation strategies.

Project Structure
JuiceShop-Pentest/
├── Broken_Access_Control
│   ├── IDOR_Horizontal_Privilege_Escalation
│   │   ├── Evidence
│   │   └── Notes.md
│   └── IDOR_Vertical_Privilege_Escalation
│       ├── Evidence
│       └── Notes.md
│
├── Injection
│   ├── Cross_Site_Scripting_XSS
│   │   ├── Evidence
│   │   └── Notes.md
│   └── SQL Injection
│       ├── Evidence
│       └── Notes.md
│
├── Security_Misconfiguration
│   ├── Screenshots
│   └── Notes.md
│
├── Scope.txt
├── Tools.txt
└── README.md

Scope of Testing

Target: OWASP Juice Shop

Environment: Localhost (http://localhost:3000)

Testing Type: Web Application Penetration Testing (Black-box & Gray-box)

Tools Used:
Burp Suite
Nmap
Nikto
Browser Developer Tools
Manual Payload Testing

Vulnerabilities Identified
A01 – Broken Access Control

IDOR (Horizontal Privilege Escalation)
Accessed other users’ data by manipulating object IDs.

Vertical Privilege Escalation (Admin Access)
Discovered and accessed admin functionality without proper authorization.

A03 – Injection

Cross-Site Scripting (XSS)
Reflected XSS executed via search input field.

SQL Injection
Authentication bypass using payload:

' OR 1=1 --

A02 – Security Misconfiguration

Directory listing enabled on /ftp

Sensitive backup/configuration files exposed

Impact Summary:
Vulnerability	Impact
IDOR	User data exposure
Vertical Privilege Escalation	Full admin control
XSS	Session hijacking, phishing
SQL Injection	Full database compromise
Security Misconfiguration	Internal config and secrets leakage

Remediation Recommendations:

Implement server-side RBAC (Role-Based Access Control)

Use prepared statements / ORM for database queries

Apply output encoding and Content Security Policy (CSP)

Disable directory listing

Remove backup files from web root

Follow secure DevSecOps deployment practices

How to Run OWASP Juice Shop:
docker run -p 3000:3000 bkimminich/juice-shop


Open in browser:

http://localhost:3000

Author:

Yuvaraj S
Certified Penetration Tester (CPT)

Disclaimer:

This project is for educational and authorized security testing purposes only.
Do not test any system without proper permission.
