---
Created: 2025-06-23T20:21
---
## What Is Caching?

- **Caching** is storing data temporarily so future requests can be **served faster**.
- Reduces load time, bandwidth usage, and server load.
- Commonly used for: **static files, API responses, database queries, images**.

  

## Types of Caching

|   |   |   |
|---|---|---|
|Type|Where It Happens|Example Use Case|
|**Browser Cache**|Client-side|HTML, CSS, JS, images|
|**CDN Cache**|Edge/server-side (near user)|Static files, media|
|**Server-side Cache**|In backend/API server memory|Reused query results or page fragments|
|**Database Cache**|Between server & DB|Store expensive DB query results|
|**Application Cache**|In memory (e.g., Redis)|Session tokens, frequently used data|

  

## HTTP Caching Headers

|   |   |   |
|---|---|---|
|Header|Purpose|Example|
|`Cache-Control`|Main caching directive|`public, max-age=86400`|
|`Expires`|Sets an expiration date/time|`Expires: Fri, 01 Jul 2025 12:00:00 GMT`|
|`ETag`|Resource version identifier (hash)|`ETag: "abc123"`|
|`Last-Modified`|Timestamp of last change|`Last-Modified: Mon, 01 Jun 2025`|
|`Pragma: no-cache`|(Legacy) forces cache validation||

  

## Cache Strategies

|   |   |   |
|---|---|---|
|Strategy|Description|Use Case|
|**Cache First**|Use cache, fetch from network if missing|Images, static content|
|**Network First**|Try network, fallback to cache|News feeds, APIs|
|**Stale-While-Revalidate**|Serve cached, update in background|Blogs, partial data|
|**No-Cache / No-Store**|Always fetch fresh data|Auth pages, sensitive data|

  

## Example: Cache-Control Header

```Plain
Cache-Control: public, max-age=86400
```

- `public` → can be cached by browser and CDN
- `max-age=86400` → cache for 1 day (in seconds)

  

## How to View Caching (DevTools)

- Open **Chrome DevTools → Network tab**
- Reload the page
- Look at **Status** column:
    - **200 (from memory cache)** = super fast
    - **304 Not Modified** = cache validated, not re-downloaded
    - **200 OK** = fresh request
- Check **Response Headers** → `Cache-Control`, `ETag`, etc.

  

## Tools & Libraries

|   |   |
|---|---|
|Tool|Purpose|
|**Redis / Memcached**|In-memory app/data cache|
|**CDNs (Cloudflare, Vercel)**|Cache static content|
|**Service Workers**|Custom client-side caching for PWA|
|**Express middleware**|`apicache`, `node-cache`|

  

## Best Practices

- Cache static assets aggressively with **fingerprinting** (e.g., `main.abc123.js`)
- Avoid caching **dynamic/private data** unless safe
- Use **versioning** for cache busting
- Use **ETag** or **Last-Modified** for revalidation
- Monitor cache hit/miss rates (CDN, server logs)