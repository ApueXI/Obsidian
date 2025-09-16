---
Created: 2025-06-15T10:19
---
### **Basic** `**if**` **Statement**

```JavaScript
if (condition) {
  // code runs if condition is true
}
```

**Example:**

```JavaScript
let age = 18;
if (age >= 18) {
  console.log("You are an adult.");
}
```

  

### `**if...else**` **Statement**

```JavaScript
if (condition) {
  // runs if true
} else {
  // runs if false
}
```

**Example:**

```JavaScript
let isRaining = true;
if (isRaining) {
  console.log("Bring an umbrella.");
} else {
  console.log("Enjoy the sun!");
}
```

  

### `**if...else if...else**`

```JavaScript
if (condition1) {
  // runs if condition1 is true
} else if (condition2) {
  // runs if condition2 is true
} else {
  // runs if none are true
}
```

**Example:**

```JavaScript
let score = 85;
if (score >= 90) {
  console.log("Grade: A");
} else if (score >= 80) {
  console.log("Grade: B");
} else {
  console.log("Grade: C or below");
}
```

  

### **Comparison Operators**

|   |   |   |
|---|---|---|
|Operator|Meaning|Example|
|`==`|equal (loose)|`5 == '5'` ✅|
|`===`|equal (strict)|`5 === '5'` ❌|
|`!=`|not equal (loose)|`5 != '5'` ❌|
|`!==`|not equal (strict)|`5 !== '5'` ✅|
|`>`|greater than|`5 > 3` ✅|
|`<`|less than|`5 < 3` ❌|
|`>=`|greater than or equal|`5 >= 5` ✅|
|`<=`|less than or equal|`3 <= 5` ✅|

  

### **Logical Operators**

|   |   |   |
|---|---|---|
|Operator|Meaning|Example|
|`&&`|AND|`age > 18 && hasID`|
|\||OR|\||
|`!`|NOT|`!isLoggedIn`|

  

### **Short Example**

```JavaScript
let loggedIn = false;

if (!loggedIn) {
  console.log("Please log in.");
}
```

  

```JavaScript
const text = document.getElementById(`input`);
const submit = document.getElementById(`submit`);
const result = document.getElementById(`result`);

submit.onclick = function(){
    
    age = text.value;
    age = Number(age);

    if (age >= 100) {
       result.textContent = `You are too old for this site` 
    }
    else if (age >= 18) {
       result.textContent = `You are eligible to enter` 
    }
    else if (age <= 0) {
       result.textContent = `Dead ass nigga` 
    }
    else{
        result.textContent = `You cannot enter`
    }
}
```

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>If Statements</title>
</head>
<body>

    <label for="input">Enter your age:</label><br>
    <input type="text" name="" id="input"><br>

    <input type="submit" name="" id="submit">
    <p id="result"></p>
    
    <script src="../IfStatements.js"></script>
</body>
</html>
```