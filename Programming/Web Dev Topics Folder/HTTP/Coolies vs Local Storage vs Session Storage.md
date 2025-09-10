---
Created: 2025-06-23T18:45
---
# Cookies vs 🗃️ LocalStorage vs 🧭 SessionStorage

|   |   |   |   |
|---|---|---|---|
|Feature|🍪 Cookies|🗃️ LocalStorage|🧭 SessionStorage|
|**Storage Limit**|~4 KB|~5–10 MB|~5–10 MB|
|**Expiration**|Manually set with `expires` or `max-age`|Never expires (until manually deleted)|Expires on tab/browser close|
|**Accessible In**|Client (JS) & Server (HTTP headers)|Client only (JavaScript)|Client only (JavaScript)|
|**Automatic Sending**|✅ Sent with every HTTP request|❌ Not sent|❌ Not sent|
|**Persistence**|Customizable (can persist, or expire)|Persistent across sessions|Lost after session (tab/window) ends|
|**Security**|Can be `HttpOnly` and `Secure`|Accessible by JS (less secure)|Accessible by JS (less secure)|
|**Use Case Examples**|Auth tokens, user preferences, tracking|Long-term caching, theme, preferences|Temp form data, tab-specific state|
|**API Access (JS)**|`document.cookie` (manual parsing)|`localStorage.setItem()` / `getItem()`|`sessionStorage.setItem()` / `getItem()`|

  

## Security Note

- **Cookies** can be made more secure by using:
    - `HttpOnly`: Not accessible via JavaScript (prevents XSS)
    - `Secure`: Only sent over HTTPS
    - `SameSite`: Controls cross-site cookie behavior
- **LocalStorage & SessionStorage**:
    - Vulnerable to **XSS** (if a script runs on your page, it can read them).
    - Not accessible from the server (frontend only).

  

## When to Use

|   |   |
|---|---|
|Use Case|Best Option|
|Storing access tokens securely|✅ Cookies (with `HttpOnly` + `Secure`)|
|Storing theme settings or layout|✅ LocalStorage|
|Saving tab-specific input temporarily|✅ SessionStorage|
|Tracking analytics or user visits|✅ Cookies|
|Caching API responses across sessions|✅ LocalStorage|

  

## Sample Usage (JavaScript)

### 🍪 Cookie

```JavaScript
document.cookie = "user=Alice; expires=Fri, 31 Dec 2025 12:00:00 UTC; path=/";
```

### LocalStorage

```JavaScript
localStorage.setItem("theme", "dark");
let theme = localStorage.getItem("theme");
```

### 🧭 SessionStorage

```JavaScript
sessionStorage.setItem("draft", "Hello World");
let draft = sessionStorage.getItem("draft");
```