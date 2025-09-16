## 🔵 **1xx – Informational**

|Code|Name|Description|
|---|---|---|
|100|Continue|Client should continue with request|
|101|Switching Protocols|Server agrees to protocol switch|
|102|Processing _(WebDAV)_|Server processing request|
|103|Early Hints|Pre-final response hints|

  

## 🟢 **2xx – Success**

|   |   |   |
|---|---|---|
|200|OK|Request succeeded|
|201|Created|Resource created|
|202|Accepted|Request accepted, not yet processed|
|203|Non-Authoritative Information|Returned meta-info differs from origin|
|204|No Content|No content in response|
|205|Reset Content|Reset document view|
|206|Partial Content|Partial GET success|
|207|Multi-Status _(WebDAV)_|Multiple statuses|
|208|Already Reported _(WebDAV)_|Element already reported|
|226|IM Used _(RFC 3229)_|Delta encoding used|

## 🟡 **3xx – Redirection**

|   |   |   |
|---|---|---|
|300|Multiple Choices|Multiple resource options|
|301|Moved Permanently|Resource moved permanently|
|302|Found|Temporary redirection|
|303|See Other|Redirect after POST|
|304|Not Modified|Cached content still valid|
|305|Use Proxy|Use proxy server|
|306|(Unused)|Reserved; not used|
|307|Temporary Redirect|Temporary redirect, method unchanged|
|308|Permanent Redirect|Permanent redirect, method unchanged|

  

  

  

## 🔴 **4xx – Client Errors**

|   |   |   |
|---|---|---|
|400|Bad Request|Malformed request syntax|
|401|Unauthorized|Authentication needed|
|402|Payment Required _(Experimental)_|Reserved for future use|
|403|Forbidden|Request refused|
|404|Not Found|Resource not found|
|405|Method Not Allowed|HTTP method not allowed|
|406|Not Acceptable|Cannot generate acceptable response|
|407|Proxy Authentication Required|Authenticate with proxy|
|408|Request Timeout|Client took too long|
|409|Conflict|Request conflicts with resource state|
|410|Gone|Resource permanently gone|
|411|Length Required|Content-Length header missing|
|412|Precondition Failed|Preconditions not met|
|413|Payload Too Large|Request body too big|
|414|URI Too Long|URI too long|
|415|Unsupported Media Type|Media type not supported|
|416|Range Not Satisfiable|Invalid range requested|
|417|Expectation Failed|Expect header not fulfilled|
|418|I'm a teapot _(RFC joke)_|April Fools’ joke|
|421|Misdirected Request|Sent to wrong server|
|422|Unprocessable Entity _(WebDAV)_|Semantically invalid request|
|423|Locked _(WebDAV)_|Resource locked|
|424|Failed Dependency _(WebDAV)_|Dependent request failed|
|425|Too Early|Request too early|
|426|Upgrade Required|Must switch protocols|
|428|Precondition Required|Requires conditional request|
|429|Too Many Requests|Rate limit exceeded|
|431|Request Header Fields Too Large|Header fields too big|
|451|Unavailable For Legal Reasons|Blocked due to legal reasons|

  

## 🔴 **5xx – Server Errors**

|   |   |   |
|---|---|---|
|500|Internal Server Error|Generic server error|
|501|Not Implemented|Feature not implemented|
|502|Bad Gateway|Invalid response from upstream|
|503|Service Unavailable|Server unavailable|
|504|Gateway Timeout|Upstream server timed out|
|505|HTTP Version Not Supported|HTTP version not supported|
|506|Variant Also Negotiates|Negotiation error|
|507|Insufficient Storage _(WebDAV)_|Not enough storage on server|
|508|Loop Detected _(WebDAV)_|Infinite loop detected|
|510|Not Extended|Further extensions required|
|511|Network Authentication Required|Network auth needed|

  

> [!important]
> 
> ## ✅ **Quick Tips:**
> 
> ### **1xx** → Informational
> 
> ### **2xx** → Successful request.
> 
> ### **3xx** → Redirects; client needs to act.
> 
> ### **4xx** → Client mistakes (bad requests, missing auth, etc.).
> 
> ### **5xx** → Server mistakes.

  