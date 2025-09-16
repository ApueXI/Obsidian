---
Created: 2025-06-13T11:02
---
### **Prompt Box (Quick & Simple)**

```JavaScript
let name = prompt("What is your name?");
alert("Hello, " + name + "!");
```

📝 `prompt()` opens a dialog box where the user types something, and returns it as a **string**.

  

### **Confirm Box (Yes/No)**

```JavaScript
let isSure = confirm("Are you sure?");
console.log(isSure); // true or false
```

📝 `confirm()` returns `true` if the user clicks "OK", and `false` if "Cancel".

  

### **Form Input (HTML + JS)**

### ✅ HTML:

```HTML
<input id="username" type="text" placeholder="Enter your name">
<button onclick="getUserInput()">Submit</button>
```

### ✅ JavaScript:

```JavaScript
function getUserInput() {
  let name = document.getElementById("username").value;
  alert("Hello, " + name + "!");
}
```

📝 `.value` gets the text inside an input element.

  

### **Getting Radio/Checkbox Values**

```HTML
<input type="checkbox" id="subscribe" checked>
```

```JavaScript
let isChecked = document.getElementById("subscribe").checked;
console.log(isChecked); // true or false
```

  

### Tips

- Use `parseInt()` or `parseFloat()` if you're expecting **numbers** from `prompt()`:

```JavaScript
let age = parseInt(prompt("Enter your age:"));
```

- Always check for `null` when using `prompt()` or `confirm()`:

```JavaScript
let name = prompt("Enter name:");
if (name !== null) {
  console.log("Hi, " + name);
}
```

  

  

```JavaScript
let username = prompt("Please enter your username: ");
alert("Hello, " + username + "! Welcome to our website.");

let usernames;
document.getElementById("submit").onclick = function(){
    usernames = document.getElementById('text').value;
    document.getElementById('h1').textContent = `Hello ${usernames}`
}
```

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>User Input</title>
</head>
<body>
    
    <h1 id="h1">Welcome</h1>

    <label for="text">Username</label>
    <input type="text" name="" id="text"><br>
    <button id="submit">Submit</button>

    <script src="../UserInput.js"></script>
</body>
</html>
```