---
Created: 2025-06-18T13:10
---
### **Function Declaration (Named Function)**

```JavaScript
function greet(name) {
  console.log("Hello, " + name);
}

greet("Alice"); // Output: Hello, Alice
```

✅ **Use when you want to reuse a block of code by name.**

  

### **Function Expression (Anonymous Function)**

```JavaScript
const greet = function(name) {
  console.log("Hi, " + name);
};

greet("Bob"); // Output: Hi, Bob
```

✅ Can be stored in a variable, passed to other functions, etc.

  

### **Arrow Function (ES6+)**

```JavaScript
const greet = (name) => {
  console.log("Hey, " + name);
};

greet("Carol"); // Output: Hey, Carol
```

🔹 **Shorter syntax**, especially good for simple logic.

  

### **Return Values**

```JavaScript
function add(a, b) {
  return a + b;
}

let result = add(3, 4); // result is 7
```

🧠 Use `return` to send back a value from the function.

  

### **Default Parameters**

```JavaScript
function greet(name = "Guest") {
  console.log("Welcome, " + name);
}

greet(); // Output: Welcome, Guest
```

✅ Use default values for parameters to avoid `undefined`.

  

### **Function with Loops**

```JavaScript
function countTo(n) {
  for (let i = 1; i <= n; i++) {
    console.log(i);
  }
}

countTo(3);
// Output: 1 2 3
```

  

### **Function Calling Another Function**

```JavaScript
\function square(x) {
  return x * x;
}

function doubleSquare(y) {
  return square(y) * 2;
}

console.log(doubleSquare(3)); // Output: 18
```

---

  

### **Function Scope**

```JavaScript
function test() {
  let x = 10; // Local to the function
}
console.log(x); // ❌ Error: x is not defined
```

🔒 Variables inside a function are **not accessible outside**.

  

### Function Types Overview

  

|   |   |   |
|---|---|---|
|Type|Syntax Example|Notes|
|Declaration|`function sayHi() {}`|Hoisted to the top of scope|
|Expression|`const sayHi = function() {}`|Not hoisted|
|Arrow Function|`const sayHi = () => {}`|Shorter, lexical `this`|

  

```JavaScript
function happybday(username, age) {
  console.log(`Happy birthday to you`);
  console.log(`Happy birthday to ${username}`);
  console.log(`You are ${age} years old`);
}

happybday("Broccode", 26);
```

  

```JavaScript
function add(x, y) {
  let result = x + y;
  return result;
}

console.log(add(5, 3));
```

  

```JavaScript
function isEven(number) {
  return number % 2 === 0 ? true : false;
}

console.log(isEven(5));
```

  

```JavaScript
function isEmail(email) {
    
    if (email.includes("@")) {
        return true;
    }
    else{
        return false;
    }
    
}
console.log(isEmail(`bro@gmail.com`));
```