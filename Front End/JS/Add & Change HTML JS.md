---
Created: 2025-06-24T13:46
---
### `**innerHTML**` **– Add or Replace HTML Content**

```JavaScript
const box = document.getElementById("box");
box.innerHTML = "<p>Hello <strong>World</strong></p>";
```

- ✅ Replaces **all** existing HTML inside the element.
- ❗ Can introduce security issues (XSS) if used with untrusted input.

  

  

### `**textContent**` **– Set or Get Plain Text**

```JavaScript
box.textContent = "Just text!";
```

- ✅ Strips HTML and sets **only text**.
- Safe for user input.

  

### `**insertAdjacentHTML()**` **– Add HTML Without Replacing Existing Content**

```JavaScript
box.insertAdjacentHTML("beforeend", "<p>Appended!</p>");
```

Positions:

- `"beforebegin"` → **Before** the element
- `"afterbegin"` → **First child**
- `"beforeend"` → **Last child** (append)
- `"afterend"` → **After** the element

  

### **Creating Elements with** `**createElement**` **+** `**appendChild**`

```JavaScript
const newEl = document.createElement("div");
newEl.textContent = "I am new!";
document.body.appendChild(newEl);
```

- ✅ Clean and safe way to build elements dynamically.

  

### **Replacing Content Safely**

```JavaScript
const title = document.querySelector("h1");
title.innerHTML = "New <em>Title</em>";
```

- Replaces existing HTML content inside `h1`.

  

### **Remove or Clear Content**

```JavaScript
box.innerHTML = "";      // Clear content
element.remove();        // Remove element itself
```

  

### **Example Use Case**

```HTML
<div id="container"></div>

<script>
  const container = document.getElementById("container");
  container.innerHTML = "<h2>Hello</h2>"; // Add heading
  container.insertAdjacentHTML("beforeend", "<p>Welcome!</p>"); // Add paragraph
</script>
```

  

### Summary Table

|   |   |   |
|---|---|---|
|Method|Use Case|Notes|
|`innerHTML`|Replace or add raw HTML|Overwrites content, use carefully|
|`textContent`|Set/get plain text|Safer than `innerHTML`|
|`insertAdjacentHTML()`|Insert without replacing|Precise positioning|
|`createElement()`|Create element in JS|Combine with `.appendChild()`|
|`.remove()`|Remove an element|Clean removal|

  

```JavaScript
const newh1 = document.createElement("h1");

newh1.textContent = "I like pizza";
newh1.id = "myh1";
newh1.style.color = "red";
newh1.style.textAlign = "center";

// document.getElementById("box1").append(newh1);
document.getElementById("box1").prepend(newh1);

// add as the last element
// document.body.append(newh1);

// add as the first elemet
// document.body.prepend(newh1);
```

  

```JavaScript
const newh1 = document.createElement("h1");

newh1.textContent = "I like pizza";
newh1.id = "myh1";
newh1.style.color = "red";
newh1.style.textAlign = "center";

const box2 = document.getElementById("box2");

document.body.insertBefore(newh1, box2);
```

  

```JavaScript
const newh1 = document.createElement("h1");

newh1.textContent = "I like pizza";
newh1.id = "myh1";
newh1.style.color = "red";
newh1.style.textAlign = "center";

const boxes = document.querySelectorAll(".box");

document.body.insertBefore(newh1, boxes[2]);
```

  

```JavaScript
const newh1 = document.createElement("h1");

newh1.textContent = "I like pizza";
newh1.id = "myh1";
newh1.style.color = "red";
newh1.style.textAlign = "center";

const boxes = document.querySelectorAll(".box");

document.body.insertBefore(newh1, boxes[2]);
```

  

```JavaScript
const newh1 = document.createElement("h1");

newh1.textContent = "I like pizza";
newh1.id = "myh1";
newh1.style.color = "red";
newh1.style.textAlign = "center";

document.body.append(newh1);
// document.getElementById('box1').append(newh1)

document.body.removeChild(newh1);
```

  

```JavaScript
const newh1 = document.createElement("h1");

newh1.textContent = "I like pizza";
newh1.id = "myh1";
newh1.style.color = "red";
newh1.style.textAlign = "center";

// document.body.append(newh1);
document.getElementById("box1").append(newh1);

document.getElementById("box1").removeChild(newh1);
```

  

```JavaScript
const listItem = document.createElement("li");

listItem.textContent = "coconut";
listItem.id = "coconut";
listItem.style.fontWeight = "bold";
listItem.style.backgroundColor = "lightgreen";

document.getElementById("fruits").prepend(listItem);
```

  

```JavaScript
const listItem = document.createElement("li");
const orange = document.getElementById("orange");
const apple = document.getElementById("apple");

listItem.textContent = "coconut";
listItem.id = "coconut";
listItem.style.fontWeight = "bold";
listItem.style.backgroundColor = "lightgreen";

document.getElementById("fruits").insertBefore(listItem, apple);
```

  

```HTML
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Add and Change HTML</title>
        <style>
            \#fruits {
                border: 3px solid;
                font-size: 2rem;
            }
        </style>
    </head>
    <body>
        <ol id="fruits">
            <li>apple</li>
            <li>orange</li>
            <li>banana</li>
        </ol>

        <script src="../AddAndChangeHTML.js">
                        const listItem = document.createElement("li");
            const orange = document.getElementById("orange");
            const apple = document.getElementById("apple");

            listItem.textContent = "coconut";
            listItem.id = "coconut";
            listItem.style.fontWeight = "bold";
            listItem.style.backgroundColor = "lightgreen";

            const TheListitems = document.querySelectorAll("\#fruits li");
            document.getElementById("fruits").insertBefore(listItem, TheListitems[2]);
        </script>
    </body>
</html>
```