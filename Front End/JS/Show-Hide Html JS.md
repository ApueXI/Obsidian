---
Created: 2025-06-25T12:06
---
### **Using** `**.style.display**`

```JavaScript
const box = document.getElementById("box");

// Hide
box.style.display = "none";

// Show
box.style.display = "block"; // or "inline", "flex", etc.
```

- `display = "none"` → completely hides the element (removes from layout).
- `display = "block"` → makes it visible again.

  

### **Toggle Show/Hide**

```JavaScript
function toggleBox() {
  const box = document.getElementById("box");
  box.style.display = box.style.display === "none" ? "block" : "none";
}
```

  

### **Using** `**.classList**` **with CSS (Recommended)**

### ✅ HTML

```HTML
<div id="menu" class="hidden">This is a menu</div>
<button onclick="toggleMenu()">Toggle</button>
```

### ✅ CSS

```CSS
.hidden {
  display: none;
}
```

### ✅ JavaScript

```JavaScript
function toggleMenu() {
  const menu = document.getElementById("menu");
  menu.classList.toggle("hidden");
}
```

- ✅ Clean, reusable, separates style from logic.

  

### **Other Visibility Methods**

|   |   |
|---|---|
|Property|Effect|
|`style.display`|Removes element from layout (`none`)|
|`style.visibility`|Hides element but **still takes up space**|
|`style.opacity`|Sets transparency (`0` = invisible)|

```JavaScript
// Make invisible but keep layout space
element.style.visibility = "hidden";

// Make visible again
element.style.visibility = "visible";
```

  

### **Example Toggle Function (All-in-One)**

```JavaScript
function toggleVisibility(id) {
  const el = document.getElementById(id);
  if (el.style.display === "none" || getComputedStyle(el).display === "none") {
    el.style.display = "block";
  } else {
    el.style.display = "none";
  }
}
```

  

### Summary Table

|   |   |   |
|---|---|---|
|Task|Method|Notes|
|Hide element|`el.style.display = "none"`|Fully removes from layout|
|Show element|`el.style.display = "block"`|Or `"flex"`, `"inline"`, etc.|
|Toggle class|`el.classList.toggle("hidden")`|Clean + scalable|
|Keep layout|`visibility: hidden`|Still takes up space|
|Fade only|`opacity: 0`|Use for animations|

  

```JavaScript
const myButton = document.getElementById("myButton");
const myImg = document.getElementById("myImg");

myButton.addEventListener("click", () => {
    if (myImg.style.visibility === "hidden") {
        myImg.style.visibility = "visible";
        myButton.textContent = "Hide";
    } else {
        myImg.style.visibility = "hidden";
        myButton.textContent = "Show";
    }
});
```