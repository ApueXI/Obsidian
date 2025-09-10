---
Created: 2025-06-23T20:22
---
## What is a PWA?

A **Progressive Web App** is a **web application that behaves like a native app** on mobile and desktop by using modern web capabilities.

> ✅ Installable, ✅ Offline-capable, ✅ Fast, ✅ Secure, ✅ Responsive

  

## Key PWA Features

|   |   |
|---|---|
|Feature|Description|
|**App Manifest**|JSON file that defines how your app appears on a device (icon, name, theme)|
|**Service Worker**|JS file that runs in background to cache assets and enable offline use|
|**HTTPS**|PWAs require secure context to function properly|
|**Responsive UI**|Works across all devices: phone, tablet, desktop|
|**Installable**|Can be added to home screen or app drawer|
|**Linkable**|Can be shared via URL (like a normal site)|
|**Fast & Reliable**|Loads instantly with cached assets, even offline|

  

## Required Files

### 1. `manifest.json`

Defines metadata about your app:

```JSON
{
  "name": "My PWA App",
  "short_name": "PWA",
  "start_url": "/",
  "display": "standalone",
  "background_color": "\#ffffff",
  "theme_color": "#000000",
  "icons": [
    {
      "src": "/icons/icon-192.png",
      "sizes": "192x192",
      "type": "image/png"
    }
  ]
}
```

  

### `service-worker.js`

Controls caching & offline support:

```JavaScript
self.addEventListener('install', event => {
  event.waitUntil(
    caches.open('static').then(cache => {
      return cache.addAll(['/index.html', '/main.js']);
    })
  );
});

self.addEventListener('fetch', event => {
  event.respondWith(
    caches.match(event.request).then(response => {
      return response || fetch(event.request);
    })
  );
});
```

  

## How to Register a Service Worker

```JavaScript
if ('serviceWorker' in navigator) {
  navigator.serviceWorker.register('/service-worker.js')
    .then(() => console.log('SW registered'))
    .catch(err => console.error('SW error', err));
}
```

  

## HTTPS is Required

- Service workers **only work on HTTPS**
- Use **localhost** for development
- Host with providers like Vercel, Netlify, Firebase

## Tools to Build/Test PWAs

|   |   |
|---|---|
|Tool|Purpose|
|**Lighthouse (Chrome)**|Audit your site for PWA compliance|
|**Workbox**|Google library for managing service workers|
|**PWA Builder**|Generates `manifest.json` and icons|
|**Vite + VitePWA**|Plugin to add PWA to Vite projects|
|**Webpack Workbox Plugin**|Adds PWA support to webpack builds|

  

## Benefits of PWAs

- ✅ Installable like native apps
- ✅ Work offline or on slow networks
- ✅ Push notifications (optional)
- ✅ Better performance with caching
- ✅ Cross-platform with one codebase

  

## How Users Install PWAs

- On mobile: "Add to Home Screen" prompt
- On desktop (Chrome): Install button in URL bar
- After install, runs in a standalone window without browser chrome

  

## Best Practices

- ✅ Use `manifest.json` with required fields
- ✅ Cache essential assets with service worker
- ✅ Test with **Lighthouse**
- ✅ Handle updates and cache versioning properly
- ✅ Use fallback content for offline pages