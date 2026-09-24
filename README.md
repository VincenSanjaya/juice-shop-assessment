OWASP Juice Shop Web Security Assessment

Project Overview

This project documents a manual web application security assessment performed against OWASP Juice Shop in a local Docker environment.

The objective was to identify common web application vulnerabilities, validate their impact, and provide remediation recommendations.

Environment

Target: OWASP Juice Shop
Deployment: Local Docker container
Platform: macOS
Proxy: Burp Suite Community Edition
Browser: Chromium

Scope

The assessment was limited to a locally hosted OWASP Juice Shop instance intended for security training.

No external systems were tested.

Methodology

The testing process included:

Application reconnaissance
HTTP request interception
Manual input manipulation
Authentication testing
Access control testing
Client-side validation bypass
Information disclosure testing
Evidence collection
Impact analysis
Remediation recommendations

Findings Summary

SQL Injection in Login Endpoint
Severity: High

The login functionality was vulnerable to SQL Injection. A crafted email parameter allowed authentication to be bypassed and returned an authenticated administrative session.

Detailed report:
findings/01-sql-injection.md

Cross-Site Scripting in Search Functionality
Severity: Medium

The product search functionality rendered user-controlled HTML and allowed JavaScript execution through a crafted input.

Detailed report:
findings/02-xss.md

Broken Access Control in Basket Endpoint
Severity: High

An authenticated user could access another user's basket by modifying the basket ID in the request URL.

Detailed report:
findings/03-broken-access-control.md

Weak Password Policy via Client-Side Validation Bypass
Severity: Medium

The registration interface displayed password complexity requirements, but the backend accepted a weak password when the request was modified directly.

Detailed report:
findings/04-authentication.md

Exposed Confidential Document via Public FTP Directory
Severity: Medium

The application exposed a publicly accessible /ftp/ directory containing internal files.

The file acquisitions.md could be accessed without authentication and was explicitly marked as confidential.

Detailed report:
findings/05-sensitive-data-exposure.md

Tools Used

Burp Suite Community Edition
Docker
Chromium
Git
GitHub

Key Skills Demonstrated

Manual web application testing
Burp Suite Proxy and Repeater
SQL Injection testing
Cross-Site Scripting testing
Broken Access Control testing
Authentication testing
Client-side validation bypass
Information disclosure testing
HTTP request analysis
Security documentation
Remediation analysis

Evidence

Screenshots and supporting evidence are stored in:

screenshots/

Sensitive authentication tokens were removed or redacted before publishing.

Project Structure

juice-shop-security-assessment/
├── README.md
├── methodology.md
├── remediation.md
├── findings/
│ ├── 01-sql-injection.md
│ ├── 02-xss.md
│ ├── 03-broken-access-control.md
│ ├── 04-authentication.md
│ └── 05-sensitive-data-exposure.md
└── screenshots/
├── sql-injection-error.png
├── sql-injection-auth-bypass.png
├── xss-html-render.png
├── xss-alert.png
├── broken-access-control-basket.png
├── weak-password-registration.png
├── exposed-ftp-directory.png
└── exposed-confidential-document.png

Lessons Learned

This project helped me understand how vulnerabilities can appear across different layers of a web application.

I learned how to analyze HTTP requests, manipulate parameters using Burp Suite, validate security impact, and document findings in a structured format.

One important lesson was that identifying a vulnerability is only part of the process. Understanding the root cause, impact, and remediation is equally important.

Disclaimer

All testing was performed against OWASP Juice Shop running locally in an intentionally vulnerable environment.

This project was created for educational and portfolio purposes only.