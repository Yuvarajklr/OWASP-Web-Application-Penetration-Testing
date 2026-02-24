 🛡️ OWASP Web Application Penetration Testing 

Poject Title

OWASP Web Application Vulnerability Assessment and Penetration Testing

Overview:

This repository contains a practical penetration testing project performed on OWASP Juice Shop, mapped to the OWASP Top 10:2025 security categories.
The project demonstrates real-world web vulnerabilities, exploitation techniques, impact analysis, and remediation recommendations.

Project Structure:
OWASP Web Application Penetration Testing
├── Broken_Access_Control
│   ├── IDOR_Horizontal_Privilege_Escalation
│   │   ├── Evidence
│   │   │   ├── idor_original_user_basket.png
│   │   │   └── idor_other_user_basket.png
│   │   └── Notes.md
│   └── IDOR_Vertical_Privilege_Escalation
│       ├── Evidence
│       │   ├── idor_admin_panel_access.png
│       │   ├── idor_hidden_admin_path.png
│       │   └── idor_payload.png
│       └── Notes.md
├── Injection
│   ├── Cross_Site_Scripting_XSS
│   │   ├── Evidence
│   │   │   ├── xss_execution.png
│   │   │   └── xss_payload.png
│   │   └── Notes.md
│   └── SQL Injection
│       ├── Evidence
│       │   ├── sqli_admin_access.png
│       │   └── sqli_payload.png
│       └── Notes.md
├── Security_Misconfiguration
│   ├── Notes.md
│   └── Screenshots
│   │   ├── misconfig_directory_listing.png
│   │   ├── misconfig_ftp_access.png
│   │   └── misconfig_md_file_exposure.png
├── OWASP Web Application Penetration Testing Report.pdf
├── Scope.txt
└── Tools.txt
Scope of Testing:

Target Application: OWASP Juice Shop

Environment: Localhost (http://localhost:3000)

Testing Type: Web Application Penetration Testing

Tools Used:

 - Burp Suite

 - OWASP ZAP

 - Nmap

 - Nikto

 - Browser Developer Tools

 - Manual Payload Testing

Vulnerabilities Identified:

  A01 – Broken Access Control:


   - IDOR (Horizontal Privilege Escalation)

   - Vertical Privilege Escalation (Admin Access)

 A02 – Security Misconfiguration:

   - Directory Listing enabled
    
   - Sensitive backup/configuration files exposed

 A03 – Injection:

   - Cross-Site Scripting (XSS)

   - SQL Injection (Authentication Bypass)

Impact Summary:

| Vulnerability              | Impact                         |
| -------------------------- | ------------------------------ |
| IDOR                       | User data exposure             |
| Admin Privilege Escalation | Full admin takeover            |
| XSS                        | Session hijacking, phishing    |
| SQL Injection              | Full database compromise       |
| Security Misconfiguration  | Internal configuration leakage |

Remediation Recommendations:

- Implement server-side Role-Based Access Control (RBAC)

- Use prepared statements / ORM for database queries

- Apply output encoding and Content Security Policy (CSP)

- Disable directory listing

- Remove backup files from web root

- Follow secure deployment and DevSecOps practices

How to Run OWASP Juice Shop:

docker run -p 3000:3000 bkimminich/juice-shop


Open in browser:

http://localhost:3000

Author:

Yuvaraj S

Certified Penetration Tester (CPT)

Cybersecurity Enthusiast

Disclaimer:

This project is for educational and authorized testing purposes only.
Do not test systems without permission.
