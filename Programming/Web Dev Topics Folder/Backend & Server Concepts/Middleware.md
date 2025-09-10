---
Created: 2025-06-23T20:21
---
## What is Middleware?

- **Middleware** is a function that **sits between** the **incoming request** and the **final route handler** in a web server or framework.
- It can **modify the request/response**, run code, or decide whether to pass control to the next middleware.

> Think of middleware as filters or pipes through which every request flows.

  

## Common Uses of Middleware

|   |   |
|---|---|
|Use Case|Description|
|**Logging**|Track requests for debugging or analytics|
|**Authentication**|Verify user identity before allowing access|
|**Authorization**|Check user permissions for protected resources|
|**Body Parsing**|Convert request body into usable format (`req.body`)|
|**Error Handling**|Catch and respond to errors in a consistent way|
|**CORS**|Enable Cross-Origin Resource Sharing|
|**Rate Limiting / Throttling**|Prevent abuse or overuse|
|**Static File Serving**|Serve images, stylesheets, etc. from a folder|

  

## Middleware Flow (Express.js-style)

```Plain
Client Request ➡ [Middleware 1] ➡ [Middleware 2] ➡ ... ➡ [Route Handler] ➡ Server Response
```

  

## Basic Middleware in Express.js

```JavaScript
app.use((req, res, next) => {
  console.log('Request URL:', req.url);
  next(); // Pass control to the next middleware
});
```

  

## Example: Authentication Middleware

```JavaScript
function checkAuth(req, res, next) {
  if (req.headers.authorization === 'secret-token') {
    next(); // Authenticated, continue
  } else {
    res.status(401).send('Unauthorized');
  }
}
app.use('/api/secure', checkAuth);
```

  

## Error-Handling Middleware

```JavaScript
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).send('Something broke!');
});
```

> Note: Must have 4 arguments to be recognized as an error handler.

  

## Built-in Express Middleware

|   |   |
|---|---|
|Middleware|Purpose|
|`express.json()`|Parse JSON bodies into `req.body`|
|`express.urlencoded()`|Parse URL-encoded bodies|
|`express.static()`|Serve static files|

  

## Summary

|   |   |
|---|---|
|Term|Description|
|`req`, `res`|Request and response objects|
|`next()`|Moves to the next middleware/handler|
|`app.use()`|Apply middleware globally|
|`app.get/post()`|Apply to specific routes|
|Middleware Order|Matters! Runs top to bottom|