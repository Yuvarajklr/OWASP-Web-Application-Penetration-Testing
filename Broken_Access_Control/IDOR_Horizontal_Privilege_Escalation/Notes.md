Category: A01:2025 – Broken Access Control
1. The Vulnerability

The application uses a simple ID in the URL to fetch user profile data. Because the server doesn't check who is asking for the data, any logged-in user can see anyone else's private information just by changing a number.
2. Steps to Reproduce (PoC)

    Log in to your account.

    Go to your User Profile page.

    Look at the URL in your browser. It will look like this:
    http://localhost:3000/#/user/profile?id=6

    Change the ID: Manually edit the 25 to 1 in the address bar and hit Enter.
    http://localhost:3000/#/user/profile?id=1

    Result: The page now displays the email, username, and internal details of the Administrator (User #1).

3. Impact

    Data Leakage: An attacker can write a simple script to "enumerate" (loop through) all IDs from 1 to 1000 and scrape every user's email address from the database.

    Privacy Violation: Leads to a total loss of user confidentiality.

4. The Fix

    Instead of trusting the ID in the URL, the server should use the Session Token (the cookie) to determine which user is logged in.

    Correct Logic: * Wrong: "Give me the data for ID 1." (Server obeys blindly)

    Right: "Give me the data for whoever is currently logged in." (Server checks the secure token)
