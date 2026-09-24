Weak Password Policy via Client-Side Validation Bypass

Severity: Medium

Affected Endpoint:
POST /api/Users/

Description:
The registration interface enforces password requirements in the browser, but the server accepts weak passwords when the request is modified directly.

Discovery:
The registration form displayed password complexity requirements.

Exploitation:
The registration request was intercepted and modified so the password value became:

12345

The modified request was sent directly to the server.

Result:
The server returned:

201 Created

and successfully created the account.

Impact:
An attacker or user can bypass the password policy enforced by the client and create accounts protected by weak passwords.

This increases the risk of password guessing and credential attacks.

Root Cause:
Password complexity requirements are enforced on the client side without equivalent server-side validation.

Remediation:
Enforce password requirements on the server.
Reject passwords that do not meet the required policy.
Do not rely on browser-side validation for security controls.
Apply rate limiting and account protection controls for authentication endpoints.

Evidence:
screenshots/weak-password-registration.png