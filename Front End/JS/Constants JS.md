---
Created: 2025-06-15T07:27
---
### **Basic Syntax**

```JavaScript
const pi = 3.14159;
```

- Declares a **constant variable**.
- **Cannot be reassigned**.
- **Must be initialized** immediately.

```JavaScript
const name;       // ❌ Error: missing initializer
const name = "Ana"; // ✅ OK
```

  

### **Reassignment Not Allowed**

```JavaScript
const age = 18;
age = 20; // ❌ Error: Assignment to constant variable
```

  

### **Objects & Arrays Can Be Changed Internally**

```JavaScript
const user = { name: "Maria" };
user.name = "Ana";    // ✅ Allowed (modifying object content)

const fruits = ["apple"];
fruits.push("banana"); // ✅ Allowed
```

❗ You **can't reassign** the whole object/array:

```JavaScript
user = {};        // ❌ Error
fruits = [];      // ❌ Error
```

  

### **Why Use** `**const**`**?**

- Safer: You avoid accidental reassignments.
- Improves code readability.
- Encourages immutable patterns

  

### **When to Use** `**const**` **vs** `**let**`

|   |   |
|---|---|
|Use `const` when:|Use `let` when:|
|The value won't change|The value will change|
|You want safety & clarity|You need flexibility|

  

### Example

```JavaScript
const MAX_USERS = 100;
const user = {
  name: "Luna",
  age: 20
};

user.age = 21; // ✅ allowed
```

  

  

```JavaScript
const PI = 3.14159;
let radius;
let circumference;

document.getElementById('submit').onclick = function(){
    radius = Number(document.getElementById('text').value);
    circumference = 2 * PI * radius;
    document.getElementById('h3').textContent = circumference + 'cm';
}
```

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Constant</title>
</head>

<body>

    <h1 id="h1">radius of a circle: </h1>

    <label for="text">radius: </label>
    <input type="text" name="" id="text"><br><br>
    <button id="submit" >submit</button>

    <h3 id="h3"></h3>

    <script src="../Constants.js"></script>
</body>

</html>
```