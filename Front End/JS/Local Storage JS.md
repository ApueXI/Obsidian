---
Created: 2025-07-13T07:47
---
### What is Local Storage?

- A web storage object that allows you to store key-value pairs **in the browser**.
- Stored **persistently** — data stays even after the page is reloaded or the browser is closed.
- Maximum size: ~5MB per origin.
- Only supports **strings**.

---

### 📦 Basic API

|Operation|Syntax Example|
|---|---|
|**Set Item**|`localStorage.setItem('key', 'value')`|
|**Get Item**|`localStorage.getItem('key')`|
|**Remove Item**|`localStorage.removeItem('key')`|
|**Clear All Items**|`localStorage.clear()`|
|**Get Key by Index**|`localStorage.key(index)`|
|**Get Storage Length**|`localStorage.length`|

---

### 📚 Example Usage

```JavaScript
// Set item
localStorage.setItem('username', 'nein');

// Get item
let user = localStorage.getItem('username');
console.log(user); // 'nein'

// Remove item
localStorage.removeItem('username');

// Clear all storage
localStorage.clear();
```

---

### 🧱 Storing Objects/Arrays

Since localStorage stores strings, you need to **stringify** objects and **parse** them back:

```JavaScript
// Save object
const user = { name: 'nein', age: 20 };
localStorage.setItem('user', JSON.stringify(user));

// Retrieve object
const savedUser = JSON.parse(localStorage.getItem('user'));
console.log(savedUser.name); // 'nein'
```

---

### 🛑 Common Pitfalls

|Issue|Solution|
|---|---|
|`null` return|Happens if key doesn't exist|
|Only strings allowed|Use `JSON.stringify()` / `JSON.parse()`|
|Storage full|Catch `QuotaExceededError`|
|Not secure|Don't store sensitive data|

---

### 🛡️ Best Practices

- **Use try-catch** to handle `JSON.parse()` errors.
- Prefix keys (e.g. `app_user`) to avoid conflicts.
- Always check if `localStorage` is available:

```JavaScript
if (typeof(Storage) !== "undefined") {
  // Safe to use localStorage
}
```