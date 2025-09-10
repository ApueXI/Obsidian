---
Created: 2025-06-23T20:22
---
## What is a CDN?

A **Content Delivery Network (CDN)** is a network of servers distributed globally that:

- **Store cached content** (e.g., images, JS, CSS, videos, HTML)
- Serve it to users **from the nearest geographic location**
- Improve **website speed, scalability, and security**

  

## Benefits of Using a CDN

|   |   |
|---|---|
|Benefit|Description|
|⚡ Faster Load Times|Delivers content from nearest server (edge location)|
|📈 Scales Easily|Handles large traffic without hitting your origin|
|🔒 Improves Security|Offers DDoS protection, TLS/SSL, and firewall rules|
|💵 Reduces Server Load|Offloads static files to CDN servers|
|🌍 Global Reach|Optimizes access for users worldwide|

  

## How It Works (Simplified Flow)

1. User requests a resource (e.g., `main.js`)
2. CDN checks if it has a cached copy
    - If yes → delivers it (**cache hit**)
    - If no → fetches from origin server, stores it (**cache miss**)
3. User gets faster content delivery

  

## Common CDN Providers

|   |   |
|---|---|
|CDN Provider|Notable Features|
|**Cloudflare**|Free tier, DDoS protection, edge functions|
|**Akamai**|Enterprise-level performance and security|
|**Fastly**|Real-time caching and purging|
|**Amazon CloudFront**|Deep AWS integration|
|**Google Cloud CDN**|Global infrastructure, low latency|
|**Vercel/Netlify**|Built-in CDN for static site hosting|

  

## What Can You Serve via CDN?

- Static assets: JS, CSS, HTML, images, fonts
- Videos or media files
- Entire websites (static hosting)
- APIs (via edge proxy caching)
- Edge logic (edge functions, redirects, A/B testing)

## Key CDN Concepts

|   |   |
|---|---|
|Term|Description|
|**Edge Location**|The nearest CDN server to the user|
|**Origin Server**|Your actual server where original content is hosted|
|**Cache-Control**|HTTP header that controls how long files stay in cache|
|**TTL (Time to Live)**|How long a file is cached before refreshing from origin|
|**Purge**|Manually clear outdated content from CDN cache|
|**Cache Hit/Miss**|Whether CDN had the file or had to fetch from origin|

  

## DevTools & Testing

- Use **Network tab → Headers**
    - Look for `cf-cache-status`, `x-cache`, or `via` headers
- Use `curl` to inspect headers:

```Shell
curl -I https://yourdomain.com/image.png
```

  

## Best Practices

- Use long `max-age` with **hashed filenames** (e.g., `app.9f4a1.js`)
- Use **versioning** or **purge tools** to update files
- Set proper cache headers: `Cache-Control`, `ETag`, `Expires`
- Use CDN with **SSL/TLS** for security
- Avoid caching private or sensitive content

  

## Example Cache-Control Header (HTML or assets)

```Plain
Cache-Control: public, max-age=31536000, immutable
```

- `max-age=31536000` → Cache for 1 year
- `immutable` → Browser won’t revalidate unless file name changes