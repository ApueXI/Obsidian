---
Created: 2025-07-13T07:48
---
### What is `sessionStorage`?

- Similar to `localStorage` but **data is cleared when the page session ends** (tab/window closed).
- Stores data **per tab** — not shared between tabs.
- Stores **string key-value pairs**.
- Max size: ~5MB per origin.

---

### 📦 Basic API

|Operation|Syntax Example|
|---|---|
|**Set Item**|`sessionStorage.setItem('key', 'value')`|
|**Get Item**|`sessionStorage.getItem('key')`|
|**Remove Item**|`sessionStorage.removeItem('key')`|
|**Clear All Items**|`sessionStorage.clear()`|
|**Get Key by Index**|`sessionStorage.key(index)`|
|**Get Length**|`sessionStorage.length`|

---

### 📚 Example Usage

```JavaScript
// Set session data
sessionStorage.setItem('theme', 'dark');

// Get session data
let theme = sessionStorage.getItem('theme');
console.log(theme); // 'dark'

// Remove one item
sessionStorage.removeItem('theme');

// Clear everything
sessionStorage.clear();
```

---

### 🧱 Store Objects/Arrays

```JavaScript
const user = { name: 'nein', loggedIn: true };
sessionStorage.setItem('user', JSON.stringify(user));

const savedUser = JSON.parse(sessionStorage.getItem('user'));
console.log(savedUser.loggedIn); // true
```

---

### 🛡️ Tips & Caveats

|Tip|Description|
|---|---|
|Use JSON for objects|`JSON.stringify()` and `JSON.parse()`|
|One tab only|Not shared across tabs|
|Temporary use only|Cleared when tab/window is closed|
|No sensitive data|Not secure|