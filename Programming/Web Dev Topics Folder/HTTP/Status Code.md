---
Created: 2025-06-23T18:37
---
### HTTP status codes are 3-digit numbers returned by the server to indicate the result of a request.

  

## 1xx – _Informational_

> "Request received, still processing"

|   |   |   |
|---|---|---|
|Code|Meaning|Explanation|
|100|Continue|Client can proceed with the request|
|101|Switching Protocols|Server switching to a different protocol|
|102|Processing (WebDAV)|Request is still being processed|

  

## 2xx – _Success_

> "Everything went well"

|   |   |   |
|---|---|---|
|Code|Meaning|Explanation|
|200|OK|Request succeeded (standard success)|
|201|Created|Resource successfully created|
|202|Accepted|Request accepted, processing later|
|204|No Content|Success, but no data returned|
|206|Partial Content|Partial content (for range requests)|

  

## 3xx – _Redirection_

> "Need to go elsewhere"

|   |   |   |
|---|---|---|
|Code|Meaning|Explanation|
|301|Moved Permanently|Resource moved to a new URL|
|302|Found (Temporary)|Temporary redirect|
|303|See Other|Redirect to a different endpoint|
|304|Not Modified|Cached version is still valid|
|307|Temporary Redirect|Use new location for now, keep method|
|308|Permanent Redirect|Use new location permanently, keep method|

  

## 4xx – _Client Errors_

> "Client messed up"

|   |   |   |
|---|---|---|
|Code|Meaning|Explanation|
|400|Bad Request|Invalid request syntax/data|
|401|Unauthorized|Needs authentication (no/invalid credentials)|
|403|Forbidden|Access denied even with credentials|
|404|Not Found|Resource doesn’t exist|
|405|Method Not Allowed|Method not allowed on this resource|
|409|Conflict|Request conflicts with current state|
|410|Gone|Resource permanently removed|
|413|Payload Too Large|Request body too big|
|415|Unsupported Media Type|Server can’t process the format|
|429|Too Many Requests|Rate-limiting — slow down|

  

## 5xx – _Server Errors_

> "Server messed up"

|   |   |   |
|---|---|---|
|Code|Meaning|Explanation|
|500|Internal Server Error|Generic server error|
|501|Not Implemented|Server doesn’t support the request method|
|502|Bad Gateway|Server got an invalid response from upstream|
|503|Service Unavailable|Server overloaded or under maintenance|
|504|Gateway Timeout|Upstream server didn’t respond in time|

  

## Common Ones to Remember

- **200 OK** – Success!
- **201 Created** – New resource added
- **204 No Content** – Success with no body
- **301/302 Redirect** – URL moved
- **400 Bad Request** – Invalid input
- **401 Unauthorized** – Needs login/token
- **403 Forbidden** – You’re not allowed
- **404 Not Found** – Doesn’t exist
- **500 Internal Error** – Server broke