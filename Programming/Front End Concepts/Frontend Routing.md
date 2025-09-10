---
Created: 2025-06-23T19:03
---
## What is Frontend Routing?

- Technique to handle **navigation inside Single Page Applications (SPAs)** without full page reloads.
- Changes the URL and view dynamically using JavaScript.
- Improves user experience by making apps feel faster and more responsive.

  

## Types of Routing

|   |   |
|---|---|
|Type|Description|
|**Hash-based Routing**|Uses URL fragment after `#` (e.g., `/index.html#about`) to track views; works without server config.|
|**History API Routing**|Uses HTML5 History API (`pushState`, `popState`) to manipulate URL paths (e.g., `/about`) without reload; cleaner URLs but requires server setup.|

  

## How It Works

- Intercept link clicks or URL changes.
- Update browser URL using JavaScript.
- Render corresponding page/component dynamically.
- Prevent default full page reload.

  

## Common Methods & APIs

|   |   |   |
|---|---|---|
|API / Method|Purpose|Example|
|`window.location.hash`|Get or set hash part of URL|`window.location.hash = '#home'`|
|`window.history.pushState()`|Change URL without reload|`history.pushState({}, '', '/home')`|
|`window.onpopstate`|Detect back/forward navigation|`window.onpopstate = (e) => { ... }`|

  

## Popular Frontend Routers

- **React Router** (React)
- **Vue Router** (Vue.js)
- **Angular Router** (Angular)
- **Page.js** (lightweight vanilla JS)

  

## Example: Simple Hash Routing

```Plain
window.addEventListener('hashchange', () => {
  const page = window.location.hash.substring(1); // remove '#'
  renderPage(page);
});

function renderPage(page) {
  if (page === 'about') {
    document.body.textContent = 'About Page';
  } else {
    document.body.textContent = 'Home Page';
  }
}
```

  

## Server Setup for History API Routing

- Server must **serve the SPA’s** `**index.html**` **for all routes** (fallback) to allow client routing.
- Otherwise, direct URL access will cause 404 errors.

  

## Benefits of Frontend Routing

- Faster navigation (no full reload).
- State preservation between views.
- Ability to animate transitions and load content dynamically.
- Deep linking support (URL reflects current view).