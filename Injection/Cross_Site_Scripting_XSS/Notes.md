Vulnerability Report: A03:2025 – Cross-Site Scripting (XSS)

1. Technical Summary

    The application is vulnerable to Reflected XSS because it fails to sanitize or encode user-supplied input before rendering it in the browser. By injecting HTML tags and JavaScript pseudo-protocols into the search bar, an attacker   can force the execution of arbitrary code in the context of the user's session.
    
2. Proof of Concept 

    Target Feature: Product Search Bar.

    Payload: <iframe src="javascript:alert(1)"></iframe>

    Execution Steps:

        Navigate to the main page of the Juice Shop.

        Enter the <iframe> payload into the search field.

        The application reflects the search string into the "Search Results" header without filtering the < or > characters.

        Result: The browser renders the iframe, which immediately executes the javascript:alert(1) source, triggering a popup.

3. Impact Analysis

    Session Hijacking: An attacker can use document.cookie to steal session tokens.

    Phishing: Malicious iframes can be used to overlay fake login forms on the legitimate site.

    Unauthorized Actions: The script can perform actions (like changing a password) on behalf of the logged-in user.

4. Remediation (The Fix)

    Context-Aware Output Encoding: Ensure that all user input is encoded (e.g., < becomes &lt;) before being rendered in HTML.

    Content Security Policy (CSP): Implement a policy that forbids inline scripts and restricted source domains for iframes.

    Use Safe Sinks: In the frontend code, use .textContent instead of .innerHTML to prevent the browser from parsing input as HTML.
