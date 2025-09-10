---
Created: 2025-06-23T20:22
---
## What Are Core Web Vitals?

**Core Web Vitals** are a set of performance metrics defined by Google to measure **user experience quality** — especially **loading**, **interactivity**, and **visual stability**.

  

## Core Web Vitals Overview

|   |   |   |
|---|---|---|
|Metric|Purpose|Good Value (Target)|
|**LCP** (Largest Contentful Paint)|Measures **loading speed**|⬇️ Less than **2.5s**|
|**FID** (First Input Delay)|Measures **input responsiveness**|⬇️ Less than **100ms**|
|**CLS** (Cumulative Layout Shift)|Measures **visual stability**|⬇️ Less than **0.1**|

  

## Core Web Vitals in Detail

### 1. **LCP (Largest Contentful Paint)**

- Measures how long it takes to render the **largest visible element**.
- Includes images, videos, large text blocks.
- ⚠️ Slow LCP = users think your site is slow.

📌 Improve by:

- Optimizing images (WebP, compression)
- Reducing server response time
- Removing render-blocking CSS/JS

  

### **FID (First Input Delay)**

- Measures the time between **first user interaction** and the browser’s **response**.
- Example: Clicking a button but nothing happens for 300ms.

📌 Improve by:

- Reducing JS bundle size
- Breaking up long tasks
- Deferring non-essential scripts

> 📝 Note: FID only measures real user interactions, not synthetic tests.

  

### **CLS (Cumulative Layout Shift)**

- Measures **how much the layout shifts unexpectedly** during load.
- Lower score = more stable visual experience.

📌 Improve by:

- Always set width/height for images/videos
- Avoid inserting DOM elements above existing content
- Don’t load fonts or ads late without space reservation

  

## Other Important Metrics

|   |   |   |
|---|---|---|
|Metric|Description|Ideal Value|
|**TTFB**|Time to First Byte (server responsiveness)|< 200ms|
|**FCP**|First Contentful Paint (first visible paint)|< 1.8s|
|**TTI**|Time to Interactive|< 5s|
|**TBT**|Total Blocking Time (correlates with FID)|< 200ms|
|**SI**|Speed Index (visual progress)|< 4.3s|

  

## Tools to Measure Performance

|   |   |
|---|---|
|Tool|Purpose|
|**Google Lighthouse**|Audit CWV, SEO, accessibility, PWA|
|**PageSpeed Insights**|Web version of Lighthouse|
|**Web.dev/measure**|User-friendly Lighthouse runner|
|**Chrome DevTools → Performance**|Detailed timeline view|
|**Web Vitals JS Library**|Real-user monitoring in production|

  

## Where Core Web Vitals Matter

- Google **ranks your site** partly based on CWV (especially on mobile)
- Impacts **SEO**, **bounce rates**, and **user satisfaction**
- Essential for **e-commerce**, **blogs**, and **landing pages**

  

## Optimization Checklist

- ✅ Lazy-load images (`loading="lazy"`)
- ✅ Minify & defer JS/CSS
- ✅ Use efficient image formats (WebP, AVIF)
- ✅ Set width/height on images
- ✅ Use a CDN and cache static assets
- ✅ Eliminate long-running JavaScript tasks
- ✅ Optimize third-party scripts (ads, trackers)