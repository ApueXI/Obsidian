## What is JWT?

A compact, URL-safe token format for transmitting information securely between parties as a JSON object.

  

### 🔗 Typical JWT Structure:

JWTs have **three base64url-encoded parts** separated by dots:

```PHP
<Header>.<Payload>.<Signature>
```

Example:

```Plain
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9
.
eyJ1c2VySWQiOiIxMjM0NTY3ODkwIiwibmFtZSI6Ik5laW4iLCJpYXQiOjE1MTYyMzkwMjJ9
.
SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
```

  

### 🛡️ Parts Breakdown:

✅ **Header**

- JSON describing token type & algorithm:

```JSON
{
  "alg": "HS256",  // or RS256, ES256, etc.
  "typ": "JWT"
}
```

✅ **Payload**

- JSON with your claims (info you want to send), e.g.:

```JSON
{
  "sub": "1234567890",
  "name": "Nein",
  "admin": true,
  "iat": 1516239022  // issued at
}
```

✅ **Signature**

- Ensures data integrity and authenticity:

```Scss
HMACSHA256(
  base64UrlEncode(header) + "." + base64UrlEncode(payload),
  secret
)
```

  

### 🔑 Common Claims:

|   |   |
|---|---|
|Claim|Meaning|
|`iss`|Issuer|
|`sub`|Subject (e.g., user ID)|
|`aud`|Audience|
|`exp`|Expiration time (UNIX timestamp)|
|`nbf`|Not before|
|`iat`|Issued at|
|`jti`|JWT ID (unique identifier)|

  

### 🛠️ Creating a JWT (Example in JS):

```JavaScript
const jwt = require('jsonwebtoken');

const token = jwt.sign(
  { userId: '12345', name: 'Nein' }, // payload
  'your_secret_key',                 // secret
  { expiresIn: '1h' }                // options
);

console.log(token);
```

  

### ✅ Verifying a JWT (Example in JS):

```Plain
js
CopyEdit
try {
  const decoded = jwt.verify(token, 'your_secret_key');
  console.log(decoded);
} catch (err) {
  console.error('Invalid or expired token:', err.message);
}

```

  

### 🔓 Decode Without Verification (just to read payload):

```Plain
js
CopyEdit
const decoded = jwt.decode(token);
console.log(decoded);

```

  

### ⚠️ Best Practices:

✔️ Use HTTPS to transmit tokens — don’t expose JWTs over insecure channels.

✔️ Keep tokens short-lived (`exp` claim) to limit risk if stolen.

✔️ Store JWTs securely — **never in localStorage if you’re worried about XSS; use httpOnly cookies**.

✔️ Rotate & revoke tokens on logout or credential compromise.

✔️ Prefer asymmetric algorithms (e.g., RS256) if you have a distributed system or want to avoid sharing secrets.

  

### 🔎 Useful Online Tools:

- [jwt.io](https://jwt.io/) — decode & debug tokens.
- [Token Validator](https://jwt.ms/) — Microsoft’s validator.
