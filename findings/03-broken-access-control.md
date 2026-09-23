Broken Access Control in Basket Endpoint

Severity: High

Affected Endpoint:
GET /rest/basket/{id}

Description:
The basket endpoint allows an authenticated user to access another user's basket by modifying the basket ID in the request URL.

Discovery:
User A accessed the following endpoint:

GET /rest/basket/6

This returned the basket associated with User A.

Exploitation:
The basket ID was changed to:

GET /rest/basket/5

The server returned HTTP 200 OK and exposed basket data associated with a different user.

Evidence:
The response contained:

UserId: 16
Basket ID: 5

Impact:
An authenticated attacker can access another user's basket data by modifying the object identifier.

Root Cause:
The server accepts the basket ID from the request without properly verifying that the requested basket belongs to the authenticated user.

Remediation:
Validate resource ownership on the server for every request.
Do not rely on client-provided object IDs for authorization.
Use the authenticated user's identity when retrieving basket data.
Return 403 Forbidden or 404 Not Found when a user requests another user's resource.

Evidence:
screenshots/broken-access-control-basket.png