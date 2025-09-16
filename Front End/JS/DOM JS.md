---
Created: 2025-06-24T06:58
---
### **What is the DOM?**

- The **DOM** is a **tree structure** of your HTML elements.
- JavaScript uses the DOM to **read and modify** the web page dynamically.

  

### **Selecting Elements**

```JavaScript
// One element
document.getElementById("title");
document.querySelector(".item"); // CSS selector

// Multiple elements
document.getElementsByClassName("box");
document.querySelectorAll("li");
```

  

### **Reading and Changing Content**

```JavaScript
const title = document.getElementById("title");

console.log(title.textContent);      // Read all text
title.textContent = "New Title";     // Change text

title.innerHTML = "<em>Styled</em>"; // Set HTML content
```

  

### **Reading and Changing Attributes**

```JavaScript
const img = document.querySelector("img");

console.log(img.src);                     // Get src
img.setAttribute("alt", "New image");     // Set alt
img.removeAttribute("width");             // Remove attribute
```

  

### **Changing Styles**

```JavaScript
const box = document.querySelector(".box");

box.style.color = "red";            // Inline style
box.style.backgroundColor = "blue"; // camelCase for CSS props
```

  

### **Working with Classes**

```JavaScript
box.classList.add("active");
box.classList.remove("hidden");
box.classList.toggle("visible");
box.classList.contains("dark"); // true/false
```

  

### **Create and Append Elements**

```JavaScript
const newEl = document.createElement("p");
newEl.textContent = "I'm new!";
document.body.appendChild(newEl);
```

  

### **Remove Elements**

```JavaScript
const btn = document.querySelector("button");
btn.remove(); // Modern way
```

  

### **Events (Click, Input, etc.)**

```JavaScript
const btn = document.querySelector("button");

btn.addEventListener("click", () => {
  alert("Button clicked!");
});
```

  

### **Get Input Values**

```JavaScript
const input = document.querySelector("\#username");

input.addEventListener("input", () => {
  console.log(input.value);
});
```

  

### Summary Table

|   |   |   |
|---|---|---|
|Task|Example|Notes|
|Select one|`document.querySelector("tag")`|Use CSS selectors|
|Select all|`document.querySelectorAll(".class")`|Returns a NodeList|
|Read/change content|`.textContent`, `.innerHTML`|Read or set text/HTML|
|Change attribute|`.setAttribute("src", "img.jpg")`|Also use `.removeAttribute()`|
|Modify style|`.style.property = value`|Inline styles only|
|Class manipulation|`.classList.add/remove/toggle()`|Edit classes easily|
|Add element|`document.createElement()`|Append with `.appendChild()`|
|Remove element|`.remove()`|Remove from DOM|
|Event listener|`.addEventListener("click", fn)`|Handle clicks, input, etc.|