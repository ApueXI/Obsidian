---
Created: 2025-07-02T19:52
---
## 📜 **Cheat Sheet: HTML Form → JS Object**

### ✅ 1) Get the form element

```JavaScript
const form = document.getElementById('myForm');
```

### ✅ 2) Add submit handler

```JavaScript
form.addEventListener('submit', (e) => {
  e.preventDefault();  // Prevent default page reload
  // ... see next steps
});
```

### ✅ 3) Create `FormData` from the form

```JavaScript
const formData = new FormData(e.target); // e.target is the form element
```

### ✅ 4) Convert `FormData` to a plain JS object

```JavaScript
const data = Object.fromEntries(formData);
// Example result: { username: "alice", password: "secret" }
```

### ✅ 5) Convert to JSON string if sending with fetch

```JavaScript
const jsonData = JSON.stringify(data);
```

### ✅ 6) Send with fetch

```JavaScript
fetch('/api/login', {
  method: 'POST',
  headers: {'Content-Type': 'application/json'},
  body: jsonData
})
.then(res => res.json())
.then(responseData => console.log(responseData))
.catch(err => console.error(err));
```

  

## **What each piece does**

|   |   |
|---|---|
|Code|What it does|
|`new FormData(form)`|Collects form fields into key-value pairs|
|`Object.fromEntries(formData)`|Converts those pairs into a JS object|
|`JSON.stringify(data)`|Prepares object for sending in JSON format|
|`fetch()`|Sends data to your backend|

  

## **Example HTML**

```HTML
<form id="myForm">
  <input name="username" placeholder="Username">
  <input name="password" type="password" placeholder="Password">
  <button type="submit">Login</button>
</form>
```

  

**Full Example Together**

```HTML
<form id="myForm">
  <input name="username" placeholder="Username">
  <input name="password" type="password" placeholder="Password">
  <button type="submit">Login</button>
</form>

<script>
document.getElementById('myForm').addEventListener('submit', async (e) => {
  e.preventDefault();

  const formData = new FormData(e.target);
  const data = Object.fromEntries(formData);

  try {
    const response = await fetch('/api/login', {
      method: 'POST',
      headers: {'Content-Type': 'application/json'},
      body: JSON.stringify(data)
    });

    const result = await response.json();
    console.log('Server response:', result);
  } catch (err) {
    console.error('Error:', err);
  }
});
</script>
```

  

**Pro Tip**:

- `FormData` works seamlessly with `<input>`, `<select>`, and `<textarea>` elements with a `name` attribute.
- Always call `e.preventDefault()` inside submit handlers to stop the form from reloading the page.