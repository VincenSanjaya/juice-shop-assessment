Exposed Confidential Document via Public FTP Directory

Severity: Medium

Affected Endpoint:
/ftp/

Description:
The application exposes a publicly accessible directory that contains internal files. One of these files, acquisitions.md, can be accessed without authentication.

Discovery:
The following endpoint was accessible directly:

/ftp/

The directory listing revealed several internal and backup files.

A file named acquisitions.md was accessible without authentication.

Evidence:
The document contains the statement:

"This document is confidential! Do not distribute!"

Impact:
An unauthenticated attacker can access internal company information that should not be publicly available.

Depending on the exposed files, this may reveal internal plans, application details, operational information, or other sensitive data.

Root Cause:
Sensitive internal files are stored inside a publicly accessible directory without proper access control.

Remediation:
Remove sensitive files from publicly accessible directories.
Disable directory listing.
Restrict access to internal documents.
Store confidential files outside the public web root.
Review deployment processes to prevent accidental exposure of internal files.

Evidence:
screenshots/exposed-ftp-directory.png
screenshots/exposed-confidential-document.png