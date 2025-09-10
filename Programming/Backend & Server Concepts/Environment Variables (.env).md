---
Created: 2025-06-23T20:21
---
## What Are Environment Variables?

- **Key-value pairs** used to configure apps **without hardcoding sensitive or environment-specific data**.
- Stored in a `.env` file (not committed to version control).
- Loaded into the runtime environment, often via libraries like `dotenv`.

  

## Why Use `.env`?

|   |   |
|---|---|
|Benefit|Description|
|✅ Separation of config|Keeps sensitive data out of source code|
|🔐 Security|Avoids exposing secrets (e.g., passwords, API keys)|
|📦 Easy deployment|Use different settings for dev, staging, prod|
|🔁 Reusability|Use same code across multiple environments|

  

## Example `.env` File

```Plain
PORT=3000
DB_HOST=localhost
DB_USER=admin
DB_PASS=supersecret
JWT_SECRET=myjwtkey
NODE_ENV=development
```

> Note: No quotes. No spaces around =. Comments start with #.

  

## How to Use `.env` in Node.js (with `dotenv`)

1. Install dotenv:

```Shell
npm install dotenv
```

1. Add this at the top of your entry file (e.g., `server.js`):

```Plain
require('dotenv').config();
```

1. Use variables in your app:

```Plain
const port = process.env.PORT;
const dbPassword = process.env.DB_PASS;
```

  

## Best Practices

|   |   |
|---|---|
|Rule|Why it matters|
|✅ Add `.env` to `.gitignore`|Protect sensitive data from being pushed to Git|
|✅ Use `process.env.VAR_NAME`|Standard Node.js way to access env vars|
|✅ Use defaults or fallback|Ensure app doesn't crash without env vars|
|❌ Don’t log secrets|Never log tokens, passwords, or secrets|
|✅ Use `NODE_ENV`|Distinguish between development, test, production|

  

## Fallback Example

```Plain
const port = process.env.PORT || 4000;
```

  

## Using in Other Frameworks

|   |   |
|---|---|
|Environment|How to load `.env`|
|**Express**|`dotenv` package|
|**Next.js**|`NEXT_PUBLIC_` prefix required for browser exposure|
|**NestJS**|`@nestjs/config` module|
|**Django** (Python)|`python-dotenv` or `os.environ.get()`|
|**Laravel** (PHP)|`.env` used by default|

  

## Security Tips

- Never expose private keys in frontend `.env` files (e.g., React).
- In frontend, only variables prefixed with `NEXT_PUBLIC_` (Next.js) or `VITE_` (Vite) are accessible in browser.