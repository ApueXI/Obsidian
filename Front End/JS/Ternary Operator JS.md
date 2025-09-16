---
Created: 2025-06-15T20:48
---
### **Basic Syntax**

```JavaScript
condition ? expressionIfTrue : expressionIfFalse;
```

It’s a shorthand for `if...else`.

  

### **Basic Example**

```JavaScript
let age = 18;
let message = age >= 18 ? "Adult" : "Minor";
console.log(message); // "Adult"
```

  

### **Nested Ternary Example**

```JavaScript
let score = 85;
let grade = score >= 90 ? "A" :
            score >= 80 ? "B" :
            score >= 70 ? "C" : "F";
console.log(grade); // "B"
```

✅ Be careful — **nested ternaries** can get hard to read!

  

### **Inside HTML (JSX or Template)**

```JavaScript
<h1>{isLoggedIn ? "Welcome!" : "Please log in."}</h1>
```

Or:

```HTML
<p id="greeting"></p>

<script>
  document.getElementById("greeting").textContent =
    isMorning ? "Good morning!" : "Good evening!";
</script>
```

  

### Tip

Use ternary when:

- The condition is **simple**
- It returns **a value**

Avoid it when:

- You have **multiple conditions**
- You need to run **statements, not expressions**

  

```JavaScript
let age = 21;
let message = age >= 18 ? `Adult` : `Minor`;

console.log(message);
```