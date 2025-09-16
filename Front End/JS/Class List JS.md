---
Created: 2025-06-25T16:48
---
### **What is** `**classList**`**?**

- The `classList` property gives you easy access to an element’s **CSS classes**.
- It acts like a mini-array of class names with helper methods.

```JavaScript
const box = document.querySelector(".box");
console.log(box.classList); // e.g., ["box", "active"]
```

  

### **Add a Class**

```JavaScript
box.classList.add("highlight");
```

- ✅ Adds one or more classes.
- Ignores duplicates.

  

### **Remove a Class**

```JavaScript
box.classList.remove("active");
```

- ✅ Removes one or more class names.

  

### **Toggle a Class**

```JavaScript
box.classList.toggle("hidden");
```

- ✅ Adds the class if it’s missing, removes it if it’s present.

🔁 Optional second argument:

```JavaScript
box.classList.toggle("dark", true);  // Force add
box.classList.toggle("dark", false); // Force remove
```

  

### **Check if a Class Exists**

```JavaScript
if (box.classList.contains("visible")) {
  console.log("Box is visible!");
}
```

- ✅ Returns `true` or `false`.

  

### **Replace a Class**

```JavaScript
box.classList.replace("old-class", "new-class");
```

- ✅ Changes class name efficiently.

  

### **Loop Through Classes**

```JavaScript
for (const className of box.classList) {
  console.log(className);
}
```

- `classList` is iterable!

  

### Summary Table

|   |   |
|---|---|
|Method|Purpose|
|`add(className)`|Add one or more classes|
|`remove(className)`|Remove one or more classes|
|`toggle(className)`|Toggle class on/off|
|`toggle(class, true)`|Force add or remove|
|`contains(className)`|Check if class exists (`true/false`)|
|`replace(old, new)`|Replace one class with another|

  

### Example

```HTML
<div id="box" class="box active"></div>

<script>
  const box = document.getElementById("box");
  box.classList.remove("active");
  box.classList.add("hidden");
  box.classList.toggle("highlight");
</script>
```

  

```JavaScript
const myButton = document.getElementById("myButton");


myButton.addEventListener("mouseover", (event) => {
    event.target.classList.add("hover");
});
myButton.addEventListener("mouseout", (event) => {
    event.target.classList.remove("hover");
});
```

```JavaScript
const myButton = document.getElementById("myButton");

myButton.addEventListener("mouseover", handleHover);
myButton.addEventListener("mouseout", handleHover);

function handleHover(event) {
    if (event.type === "mouseover") {
        event.target.classList.add("hover");
    } else if (event.type === "mouseout") {
        event.target.classList.remove("hover");
    }
}
```

  

```JavaScript
const myButton = document.getElementById("myButton");

myButton.classList.add("enabled");

myButton.addEventListener("click", (event) => {
    event.target.classList.replace("enabled", "disabled");
});
```

  

```JavaScript
const myButton = document.getElementById("myButton");
const myh1 = document.getElementById("myh1");

myButton.classList.add("enabled");
myh1.classList.add("enabled");

myButton.addEventListener("click", (event) => {
    if (event.target.classList.contains("disabled")) {
        event.target.textContent += "⭐";
    } else {
        event.target.classList.replace("enabled", "disabled");
    }
});

myh1.addEventListener("click", (event) => {
    if (event.target.classList.contains("disabled")) {
        event.target.textContent += "⭐";
    } else {
        event.target.classList.replace("enabled", "disabled");
    }
});
```

  

```JavaScript
let buttons = document.querySelectorAll(".myButtons");

buttons.forEach((button) => {
    button.classList.add("enabled");
});

buttons.forEach((button) => {
    button.addEventListener("mouseout", handleHover);
    button.addEventListener("mouseover", handleHover);
});

buttons.forEach((button) => {
    button.addEventListener("click", (event) => {
        if (event.target.classList.contains("disabled")) {
            event.target.textContent += "⭐";
        } else {
            event.target.classList.replace("enabled", "disabled");
        }
    });
});
```

  

```JavaScript
let buttons = document.querySelectorAll(".myButtons");

buttons.forEach((button) => {
    button.classList.add("enabled");
});

buttons.forEach((button) => {
    button.addEventListener("mouseout", handleHover);
    button.addEventListener("mouseover", handleHover);
});

function handleHover(event) {
    if (event.type === "moseoveer") {
        event.target.classList.toggle("hover");
    } else if (event.type === "mouseout") {
        event.target.classList.toggle("hover");
    }
}

buttons.forEach((button) => {
    button.addEventListener("click", (event) => {
        if (event.target.classList.contains("disabled")) {
            event.target.textContent += "⭐";
        } else {
            event.target.classList.replace("enabled", "disabled");
        }
    });
});
```