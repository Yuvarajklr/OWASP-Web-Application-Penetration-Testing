Category: A02:2025 – Security Misconfiguration
1. Technical Summary

The web server is misconfigured to allow directory listing on the /ftp path. Additionally, this directory contains sensitive files (backups, configuration files, and legal documents) that should not be web-accessible. This "leaky" configuration allows an attacker to gain deep insights into the application's infrastructure and sensitive data without needing any credentials.
2. Proof of Concept (PoC)

  Step 1: Discovery
    During a routine scan using Nikto or a manual check of the robots.txt file, the /ftp directory is identified.

    Target: http://localhost:3000/ftp

  Step 2: Exploration
     By navigating to the URL, the browser renders a list of files. Among standard images, we find:

    acquisition.md

    coupons_2023.json.bak

    package.json.bak

  Step 3: Exploitation (Bypassing File Restrictions)
    The server has a "security" configuration that prevents downloading .bak or .md files directly (e.g., it returns a 403 error). However, this is a Misconfiguration because it only checks the end of the filename.

    The Trick: Use a Null Byte Injection or a simple URL encoding trick. In many Juice Shop versions, you can bypass this by appending a supported extension after the "forbidden" one.

    Target URL: http://localhost:3000/ftp/package.json.bak%2500.md (or similar Poison Null Byte techniques).

3. Impact Analysis

    Information Leakage: Access to package.json.bak reveals all internal dependencies and their exact versions, making A03: Software Supply Chain attacks much easier.

    Credential Exposure: Backup files often contain hardcoded API keys or database connection strings.

    Risk Score: High. It provides the blueprint for a total system compromise.

4. Remediation

    Disable Directory Listing: Configure the web server (Nginx/Apache/Node.js) to deny listing of directory contents.

    Proper "Ignore" Rules: Ensure backup files (.bak, .old, .swp) are never stored in the web root (public_html or equivalent).

    Hardened File Handling: Use a "Allow-list" for file extensions rather than a "Block-list."
