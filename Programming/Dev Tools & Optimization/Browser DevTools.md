---
Created: 2025-06-23T20:21
---
## What Are DevTools?

- Built-in browser tools to **inspect, debug, analyze, and optimize** web pages.
- Essential for frontend and backend developers during development and troubleshooting.

  

## How to Open DevTools

|   |   |
|---|---|
|Platform|Shortcut|
|Windows|`Ctrl + Shift + I` or `F12`|
|Mac|`Cmd + Option + I`|
|Element Picker|`Ctrl + Shift + C` (or ⌘ + Shift + C)|

  

## Key Panels and What They Do

|   |   |
|---|---|
|Panel|Purpose|
|**Elements**|Inspect and edit HTML & CSS live|
|**Console**|View logs, run JS commands, see errors/warnings|
|**Sources**|Debug JS with breakpoints, view files, use Watch/Call Stack|
|**Network**|Inspect requests/responses, headers, status codes, payload, timing|
|**Performance**|Analyze rendering speed, frame rate, script execution time|
|**Memory**|Detect memory leaks, monitor heap usage|
|**Application**|View cookies, localStorage, sessionStorage, indexedDB, manifest|
|**Lighthouse**|Run audits for performance, accessibility, SEO|
|**Security**|Check HTTPS status, certificates, content security policies|
|**Coverage**|See unused CSS/JS to help reduce bundle size|

  

## Common Use Cases

### 🧱 Elements Panel

- Modify HTML structure and styles on the fly
- Toggle classes
- Force element states (`:hover`, `:focus`)
- Copy XPath or CSS selector

### 📜 Console Panel

- `console.log()`, `console.error()`, `console.table()` outputs
- Test JavaScript expressions
- Access selected element with `$0`
- Use `dir()`, `clear()`, `time()` for debugging

### 🌐 Network Panel

- Monitor API calls (XHR, Fetch)
- Filter by type (JS, CSS, image, etc.)
- Check request/response headers and body
- Throttle network speed (e.g., Slow 3G)

### 🪝 Sources Panel

- Set breakpoints in JS
- Step through code (Step in, Step out)
- View local and session storage
- Use Watch and Call Stack for debugging

### 📈 Performance Panel

- Record page load or user interaction
- Detect slow scripting or rendering
- Identify layout thrashing

  

## Bonus Tools

|   |   |
|---|---|
|Tool|Description|
|**Lighthouse**|Audit page performance, a11y, SEO|
|**Rendering Tab**|Visualize paint flashing, layout shifts|
|**Coverage Tab**|Find unused JS and CSS|
|**Device Mode**|Test responsive design and mobile emulation|
|**Command Menu**|`Cmd/Ctrl + Shift + P` to search DevTools actions|

  

## Pro Tips

- Right-click an element → "Inspect" to jump into code
- Use `$0` to reference the currently selected element in Console
- Use **Preserve log** to keep network history during page reloads
- Use **Copy → Copy as fetch/axios** for API replaying
- Toggle **Disable cache** when DevTools is open for accurate testing