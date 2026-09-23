Cross-Site Scripting in Search Functionality

Severity: Medium

Affected Function:
Product Search

Description:
The product search functionality renders user-controlled input as HTML without sufficient sanitization or output encoding.

Discovery:
The following HTML input was submitted:

<b>hello</b>

The application rendered the text in bold, indicating that HTML input was interpreted by the browser.

Exploitation:
The following payload was submitted:

<img src=x onerror=alert(1)>

The browser executed the JavaScript event handler and displayed an alert dialog.

Impact:
An attacker may execute JavaScript in the context of the application.

Depending on how the vulnerable input is delivered to other users, this could be used to manipulate page content, access browser-accessible data, or perform actions using the victim's session.

Root Cause:
User-controlled input is inserted into the page without sufficient sanitization or contextual output encoding.

Remediation:
Apply contextual output encoding.
Sanitize untrusted HTML input.
Avoid inserting raw user input into the DOM.
Use safe DOM APIs such as textContent where possible.
Deploy a restrictive Content Security Policy as an additional defense.

Evidence:
screenshots/xss-html-render.png
screenshots/xss-alert.png