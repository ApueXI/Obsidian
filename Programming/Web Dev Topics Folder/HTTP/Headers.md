---
Created: 2025-06-23T18:39
---
### HTTP headers are key-value pairs sent with requests and responses to pass metadata.

  

## Request Headers

Headers sent **by the client** (browser/app) to the server.

|   |   |   |   |
|---|---|---|---|
|Header|Purpose|Example|Notes|
|**Host**|Domain name of the server|`Host: example.com`|Required in HTTP/1.1|
|**User-Agent**|Info about the client|`User-Agent: Mozilla/5.0`|Identifies browser/app|
|**Accept**|Desired response format|`Accept: application/json`|Can request JSON, HTML, etc.|
|**Accept-Encoding**|Compression accepted|`gzip, deflate`|Server sends compressed content|
|**Accept-Language**|Preferred language|`en-US`|Helps with language selection|
|**Authorization**|Auth credentials|`Authorization: Bearer <token>`|Used for API keys, tokens|
|**Content-Type**|Format of request body|`Content-Type: application/json`|Required for POST/PUT/PATCH|
|**Content-Length**|Size of request body|`Content-Length: 349`|Auto-handled usually|
|**Cookie**|Session cookies|`Cookie: sessionId=abc123`|Sent with each request|
|**Referer**|URL of the previous page|`Referer: https://google.com`|Useful for analytics, tracking|
|**Origin**|Origin of request|`Origin: https://site.com`|Used in CORS checks|

  

## Response Headers

Headers sent **by the server** to the client.

|   |   |   |   |
|---|---|---|---|
|Header|Purpose|Example|Notes|
|**Content-Type**|Response format|`Content-Type: text/html`|Tells browser how to render|
|**Content-Length**|Size of response|`Content-Length: 1024`|Optional in chunked transfer|
|**Set-Cookie**|Set cookies on client|`Set-Cookie: userId=abc123`|Used in sessions|
|**Cache-Control**|Caching rules|`Cache-Control: no-cache`|Can prevent or allow caching|
|**ETag**|Resource version ID|`ETag: "abc123"`|Helps with 304 Not Modified|
|**Location**|Redirect location|`Location: /login`|Used with 3xx codes|
|**Access-Control-Allow-Origin**|CORS access|`*` or `https://example.com`|Required for cross-origin|
|**Retry-After**|Delay before retry|`Retry-After: 120`|Used with `503` or rate limits|
|**WWW-Authenticate**|Auth required|`Basic realm="example"`|Returned with `401 Unauthorized`|
|**X-Content-Type-Options**|Prevent MIME sniffing|`nosniff`|Security header|
|**X-Frame-Options**|Frame embedding control|`DENY` or `SAMEORIGIN`|Blocks clickjacking|

  

## Security-Related Headers

|   |   |   |
|---|---|---|
|Header|Purpose|Example|
|**Strict-Transport-Security**|Enforce HTTPS|`max-age=31536000; includeSubDomains`|
|**Content-Security-Policy**|Prevent XSS|`default-src 'self'`|
|**X-XSS-Protection**|XSS filter (legacy)|`1; mode=block`|
|**X-Content-Type-Options**|Prevent MIME sniffing|`nosniff`|
|**Referrer-Policy**|Controls `Referer` header|`no-referrer`|

  

## Common Usage Patterns

### ✅ Sending JSON in a POST request:

```Plain
POST /api/login HTTP/1.1
Content-Type: application/json
Authorization: Bearer abc123
```

### ✅ Setting a cookie in a response:

```Plain
Set-Cookie: sessionId=xyz789; HttpOnly; Secure
```