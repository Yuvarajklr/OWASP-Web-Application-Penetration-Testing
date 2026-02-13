Category: A01:2025 – Broken Access Control (Vertical)
1. Technical Summary

The application fails to perform Server-Side Authorization (RBAC) on administrative endpoints. While the "Administration" button is hidden in the User Interface for non-admin users, the underlying API endpoints are not protected. An attacker can bypass the UI restrictions to perform administrative actions, such as viewing all user data or deleting feedback.
2. Proof of Concept (PoC)

  Step 1: The "Guessing" Method (Reconnaissance)
    Common administrative paths are often predictable. 

    In your browser's address bar, try adding common admin paths after the main URL:
        http://localhost:3000/#/admin
        http://localhost:3000/#/administration
    Notice that if you aren't logged in, navigating to these might return a 403 Forbidden or just redirect you. 

  Step 2: The "Source Code" Method (Deep Dive)
    If guessing fails, you can find the exact path hidden in the application's client-side code. 

    Open Developer Tools (F12) and go to the Sources (Chrome) or Debugger (Firefox) tab.
    Look for a file named main.js (it might have a random string like main-es2018.js).
    Use Ctrl + F to search the file for the keyword "admin".
    You will eventually find a "route mapping" that looks like: {path: "administration", component: ...}. This confirms the hidden URL is /#/administration. 

  Step 3: Exploitation (Login Bypass)
    To actually use the panel, you usually need admin privileges. You can combine this with your previous SQL injection knowledge: 

    Go to the Login page.
    Use the SQL injection payload in the Email field: ' or 1=1-- and any password.
    Once logged in as the Administrator, navigate to: http://localhost:3000/#/administration. 

  Step 4: Success!
    You should now see the Administration dashboard where you can see all registered users and even delete customer feedback. 

3. Impact Analysis

    Confidentiality: Critical. Access to the full user database, including emails and hashed passwords.

    Integrity: High. Ability to modify application settings and delete user-generated content.

    Risk Score: 9.8 (Critical) via CVSS v3.1 calculation.

4. Remediation

    Implement Role-Based Access Control (RBAC): The backend must verify the role claim in the user's JWT (JSON Web Token) before executing any function in the /admin or /api/Feedbacks routes.

    Deny by Default: All administrative routes should be inaccessible unless a valid admin session is explicitly verified.
