---
Created: 2025-06-23T20:21
---
## What Is Rate Limiting?

- **Definition:** Restricts how many **requests a user/client can make** in a specific time frame.
- **Goal:** Prevent abuse, DDoS attacks, API overuse.
- **Example:** “Max 100 requests per 15 minutes per IP.”

  

## What Is Throttling?

- **Definition:** Controls the **speed or frequency** of requests, often by **delaying** them rather than rejecting.
- **Goal:** Smooth out spikes in traffic without denying service.
- **Example:** “Allow 1 request every second per user.”

  

## Key Differences

|   |   |   |
|---|---|---|
|Feature|Rate Limiting|Throttling|
|**Main Purpose**|Enforce hard request limits|Slow down excessive request rates|
|**Behavior**|Blocks or rejects after the limit is hit|Delays or queues requests instead|
|**Common Use Cases**|API protection, security, abuse control|Smooth burst traffic, fair resource usage|
|**User Experience**|Can result in error/denial (e.g. 429)|Slower responses but still served|
|**Response Code**|Often HTTP **429 Too Many Requests**|Still returns 200, but with a delay|

  

## How It's Implemented

|   |   |
|---|---|
|Component|Details|
|**Token Bucket**|Refill tokens over time; spend 1 per request|
|**Leaky Bucket**|Requests enter a bucket and leak at a fixed rate|
|**Fixed Window**|Count requests in fixed time blocks (e.g., per minute)|
|**Sliding Window**|Smoother count over sliding time range|

  

## Example in Express.js (Node.js)

**Rate Limit:**

```JavaScript
const rateLimit = require('express-rate-limit');
const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100,                 // limit each IP to 100 requests
});
app.use(limiter);
```

**Throttle (Delay):**

```JavaScript
const slowDown = require('express-slow-down');
const speedLimiter = slowDown({
  windowMs: 60 * 1000,      // 1 minute
  delayAfter: 10,           // Allow 10 requests per minute
  delayMs: 500              // Delay every request after 10 by 500ms
});
app.use(speedLimiter);
```

  

## Best Practices

- Combine rate limiting and throttling for balance.
- Whitelist trusted IPs or users (admin, internal).
- Set clear **limits in API docs**.
- Return proper headers:
    - `Retry-After`
    - `X-RateLimit-Remaining`
    - `X-RateLimit-Reset`