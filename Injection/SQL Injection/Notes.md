 A05:2025 – Injection (SQL Injection)

1. Technical Summary

The application is vulnerable to Unsanitized Input Injection. When a user submits data through the login form, the backend takes that string and inserts it directly into a SQL query. Because the application does not "escape" special characters (like the single quote '), an attacker can manipulate the query’s logic to bypass authentication or extract data from the database.

  Step 1: Probing for the Vulnerability

    Navigate to the Login Page.

    In the email field, enter: admin@juice-sh.op'--

    Observation: If the application returns a database error or behaves unexpectedly, it confirms the input is being processed by the database engine.

  Step 2: Crafting the Bypass Payload
    To log in without a password, we use a payload that turns the entire WHERE clause into a "True" statement.

    Payload: ' OR 1=1 --

    The Logic:

        The ' closes the email field.

        The OR 1=1 is a logical "True" (1 is always 1).

        The -- (or # in some databases) tells the database to ignore everything after it (the password check).

   Step 3: Execution

    Email: ' OR 1=1 --

    Password: (Leave blank or type anything)

    Result: The server executes the modified query, finds the first record in the Users table (the Admin), and grants full access.

2. Impact Analysis

    Authentication Bypass: Total takeover of administrative accounts.

    Data Exfiltration: An attacker could use UNION SELECT statements to dump the entire Products, Users, and Feedbacks tables.

    Risk Rating: Critical (9.8/10).

3. Remediation (The Professional Fix)

   As a Red Teamer, you must tell the "Blue Team" how to fix it.

    Primary Fix: Use Prepared Statements (Parameterized Queries). This tells the database: "Treat this input as a string of text, NOT as code to be executed."

    Secondary Fix: Use an ORM (Object-Relational Mapper) like Sequelize or Prisma, which handles sanitization automatically.

    Input Validation: Ensure only properly formatted emails are accepted.
