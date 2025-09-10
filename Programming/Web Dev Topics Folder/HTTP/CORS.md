---
Created: 2025-06-23T18:43
---
## What is CORS?

**CORS (Cross-Origin Resource Sharing)** is a security feature in browsers that **restricts requests** from one origin (site) to a **different origin** (domain, protocol, or port).

It helps prevent **malicious cross-origin requests** from scripts in the browser.

  

## What Counts as “Cross-Origin”?

|   |   |
|---|---|
|Situation|Same Origin?|
|`https://example.com → https://example.com`|✅ Yes|
|`https://example.com → http://example.com`|❌ No|
|`https://example.com → https://api.example.com`|❌ No|
|`https://example.com:443 → https://example.com:8080`|❌ No|

  

## Basic Flow (Simplified)

1. **Browser** sends request to another origin.
2. **Browser checks CORS policy**.
3. **Server** must respond with correct CORS headers.
4. If headers are missing or invalid → ❌ request is blocked by the browser.

  

## Important CORS Headers

### 📨 Sent by Browser

- `Origin`: Shows where the request came from
    
    ```Plain
    Origin: https://example.com
    ```
    

  

### Sent by Server

|   |   |   |
|---|---|---|
|Header|Purpose|Example|
|**Access-Control-Allow-Origin**|Allows a specific origin|`*` or `https://example.com`|
|**Access-Control-Allow-Methods**|Allowed HTTP methods|`GET, POST, PUT`|
|**Access-Control-Allow-Headers**|Allowed custom headers|`Authorization, Content-Type`|
|**Access-Control-Allow-Credentials**|Allow cookies/auth|`true`|
|**Access-Control-Expose-Headers**|Expose response headers|`X-Custom-Header`|
|**Access-Control-Max-Age**|Cache preflight time (sec)|`3600`|

  

## Preflight Requests

For **unsafe methods** (`POST`, `PUT`, `DELETE`, custom headers, etc.), browsers send a **preflight** `**OPTIONS**` **request**.

### 🧪 Example Flow:

```Plain
OPTIONS /api/data HTTP/1.1
Origin: https://myapp.com
Access-Control-Request-Method: POST
Access-Control-Request-Headers: Content-Type
```

### Server Response:

```Plain
HTTP/1.1 204 No Content
Access-Control-Allow-Origin: https://myapp.com
Access-Control-Allow-Methods: POST
Access-Control-Allow-Headers: Content-Type
```

  

## Credentials (Cookies, Tokens)

By default, **cookies and credentials** are **NOT sent** in CORS.

To allow:

### Client-side:

```Plain
fetch('https://api.com/data', {
  credentials: 'include'
})
```

### Server-side:

```Plain
Access-Control-Allow-Origin: https://yourapp.com
Access-Control-Allow-Credentials: true
```

⚠️ Cannot use `*` as `Allow-Origin` when `Allow-Credentials: true`!

  

## Common CORS Errors

|   |   |
|---|---|
|Error|Reason|
|No `Access-Control-Allow-Origin` header|Server didn't include CORS header|
|`Access-Control-Allow-Origin: *` + credentials|Not allowed — must be exact origin|
|Preflight request fails|Server doesn't handle `OPTIONS` request|
|Method not allowed|Server didn’t include method in `Access-Control-Allow-Methods`|

  

## Debug Tips

- Check **browser console** for exact error.
- Use **network tab** → filter by `OPTIONS`.
- Verify server is setting **all required headers**.
- Tools: [Postman](https://www.postman.com/), [curl](https://curl.se/), browser devtools.