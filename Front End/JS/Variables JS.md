---
Created: 2025-06-13T08:34
---
### **Declaring Variables**

```JavaScript
var name = "Alice";    // old way (avoid)
let age = 25;          // modern, reassignable
const pi = 3.14;       // constant, cannot reassign
```

  

### `**var**` **vs** `**let**` **vs** `**const**`

|   |   |   |   |
|---|---|---|---|
|Feature|`var`|`let`|`const`|
|Scope|Function-scoped|Block-scoped|Block-scoped|
|Redeclarable|✅ Yes|❌ No|❌ No|
|Reassignable|✅ Yes|✅ Yes|❌ No|
|Hoisting|✅ Yes (undefined)|✅ Yes (TDZ*)|✅ Yes (TDZ*)|

> *TDZ = Temporal Dead Zone (can’t use before declaration)

  

### **Data Types**

```JavaScript
let name = "Bob";           // String
let age = 18;               // Number
let isAdmin = true;         // Boolean
let user = null;            // Null
let score;                  // Undefined
let person = {name: "Ana"}; // Object
let fruits = ["apple"];     // Array (object type)
```

  

### **Dynamic Typing**

JS is _loosely typed_. A variable can hold any data type:

```JavaScript
let data = 42;     // Number
data = "hello";    // Now a string
```

  

### **Reassignment Example**

```Java
let counter = 5;
counter = counter + 1;
```

> const cannot be reassigned!

  

### **Best Practices**

- ✅ Use `let` when the value **will change**
- ✅ Use `const` when the value **won’t change**
- ❌ Avoid `var` in modern JavaScript

  

### **Check a Variable Type**

```Java
console.log(typeof name); // "string"
```

  

### **Example**

```Java
const firstName = "Maria";
let age = 21;
let isStudent = true;

console.log(`${firstName} is ${age} years old.`);
```

  

```JavaScript
let x = 100;
let age = 25;
let price = 19.99;
let gpa = 2.1;
let name = "John Doe";
let email = "JohnDoe123@gmail.com";
let isActive = true;
let isStudent = false;


console.log(`The price is $${price} and the buyer is ${name}.`);
console.log(` Your age is ${age}`)
console.log(isActive)
console.log(typeof age)
console.log(typeof name)
console.log(typeof isActive)

document.getElementById('p1').textContent = `Your name is ${name}`;
document.getElementById('p2').textContent = `Your email is ${email}`;
document.getElementById('p3').textContent = `You are are student: ${isStudent}`;
```

  

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="Variable.css">
    <title>Variable</title>
</head>
<body>
    
    <p id="p1"></p>
    <p id="p2"></p>
    <p id="p3"></p>

    <script src="../Variables.js"></script>
</body>
</html>
```