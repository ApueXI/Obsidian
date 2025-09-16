---
Created: 2025-07-13T07:49
---
## What is IndexedDB?

- A **low-level API** for client-side **structured data storage**.
- Allows storing large amounts of **indexed** data (not just strings).
- Works with objects, arrays, blobs, files, and more.
- **Asynchronous**, unlike localStorage/sessionStorage.

---

## 📚 Basic Concepts

|Term|Description|
|---|---|
|**Database**|A named DB that stores all your data.|
|**Object Store**|Like a table in SQL. Holds records (objects).|
|**Key**|A unique identifier for each object.|
|**Index**|A way to query records on a specific property.|
|**Transaction**|Ensures atomicity when reading/writing data.|

---

## 🚀 Opening a Database

```JavaScript
const request = indexedDB.open('MyDatabase', 1);

request.onupgradeneeded = function (e) {
  const db = e.target.result;
  const store = db.createObjectStore('users', { keyPath: 'id' });
  store.createIndex('name', 'name', { unique: false });
};

request.onsuccess = function (e) {
  const db = e.target.result;
  console.log('Database opened');
};

request.onerror = function (e) {
  console.error('Error opening database:', e);
};
```

---

## ✍️ Add / Read / Update / Delete Data

### ➕ Add Data

```JavaScript
const tx = db.transaction('users', 'readwrite');
const store = tx.objectStore('users');
store.add({ id: 1, name: 'nein' });
```

### 📖 Read Data

```JavaScript
const tx = db.transaction('users', 'readonly');
const store = tx.objectStore('users');
const getRequest = store.get(1);

getRequest.onsuccess = () => {
  console.log(getRequest.result); // { id: 1, name: 'nein' }
};
```

### ✏️ Update Data

```JavaScript
store.put({ id: 1, name: 'updatedNein' }); // Same as add, but updates if exists
```

### ❌ Delete Data

```JavaScript
store.delete(1);
```

---

## 🔍 Using Indexes

```JavaScript
const index = store.index('name');
const query = index.get('nein');

query.onsuccess = () => {
  console.log(query.result); // Gets the object with name 'nein'
};
```

---

## 🧠 Notes & Best Practices

|Tip|Description|
|---|---|
|Always use `onupgradeneeded`|For creating/updating object stores|
|Use Promises (via wrappers)|e.g., [idb](https://github.com/jakearchibald/idb) simplifies syntax|
|Use versioning wisely|Each upgrade triggers `onupgradeneeded`|
|Store large complex data|Perfect for offline-first apps|
|Not for small/simple tasks|Use `localStorage` or `sessionStorage` instead|