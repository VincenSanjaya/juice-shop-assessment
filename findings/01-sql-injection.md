SQL Injection in Login Endpoint

Severity: High

Affected Endpoint:
POST /rest/user/login

Description:
The login endpoint is vulnerable to SQL Injection because user-controlled input in the email field is directly incorporated into a SQL query.

Discovery:
A single quote character was submitted in the email parameter.

Payload:
'

The application returned a 500 Internal Server Error and exposed an SQLITE_ERROR message. The response also revealed the generated SQL query.

Exploitation:
The following payload was submitted:

' OR 1=1--

The server returned HTTP 200 OK and issued an authentication token for:

admin@juice-sh.op

This confirms that the vulnerability can be used to bypass authentication.

Impact:
An attacker may authenticate without knowing a valid password. Depending on the database query and application logic, the vulnerability may also expose or modify sensitive data.

Root Cause:
User input is inserted into the SQL query without safe parameterization.

Remediation:
Use parameterized queries or prepared statements.
Do not concatenate user input into SQL statements.
Return generic error messages to users.
Avoid exposing database errors and internal queries.
Apply server-side input validation.
Use least-privileged database accounts.

Evidence:
screenshots/sql-injection-error.png
screenshots/sql-injection-auth-bypass.png