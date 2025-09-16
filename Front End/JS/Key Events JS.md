---
Created: 2025-06-25T10:21
---
## Common Input Events

|Event|Triggered When...|Elements|
|---|---|---|
|`click`|Element is clicked|buttons, any|
|`dblclick`|Element is double-clicked|buttons, any|
|`mousedown`|Mouse button is pressed|any|
|`mouseup`|Mouse button is released|any|
|`mousemove`|Mouse is moved|any|
|`mouseenter`|Mouse enters an element|any|
|`mouseleave`|Mouse leaves an element|any|
|`keydown`|Key is pressed down|inputs, window|
|`keyup`|Key is released|inputs, window|
|`keypress` 🔶|Key is pressed (deprecated, use `keydown`)|inputs, window|
|`input`|Value of input/textarea changes|inputs, textarea|
|`change`|Input loses focus and value changed|inputs, select|
|`focus`|Element receives focus|inputs, textarea|
|`blur`|Element loses focus|inputs, textarea|

🔶 **Note:** `keypress` is deprecated; prefer `keydown`/`keyup`.

  

### **Key Event Types**

|   |   |
|---|---|
|Event|When it fires|
|`keydown`|When a key is **pressed down**|
|`keypress`|(Deprecated) When key is **pressed**|
|`keyup`|When a key is **released**|

> ✅ Use keydown and keyup — keypress is outdated.

  

### **Basic Example: Detect a Key**

```JavaScript
document.addEventListener("keydown", (e) => {
  console.log("Key:", e.key);       // e.g. "a", "Enter", "ArrowUp"
  console.log("Code:", e.code);     // e.g. "KeyA", "Enter", "ArrowUp"
});
```

- `e.key`: actual character or key label
- `e.code`: physical key on keyboard (good for shortcuts)

  

### **Detecting Specific Keys**

```JavaScript
document.addEventListener("keydown", (e) => {
  if (e.key === "Enter") {
    console.log("You pressed Enter!");
  }

  if (e.code === "ArrowUp") {
    console.log("Up arrow key!");
  }
});
```

  

### **Prevent Default Behavior**

```JavaScript
document.addEventListener("keydown", (e) => {
  if (e.key === "Tab") {
    e.preventDefault(); // stops tab from changing focus
    console.log("Tab key blocked");
  }
});
```

  

### **Key Combinations (Ctrl, Shift, etc.)**

```JavaScript
document.addEventListener("keydown", (e) => {
  if (e.ctrlKey && e.key === "s") {
    e.preventDefault(); // prevent browser save
    console.log("Ctrl + S pressed");
  }
});
```

- Modifiers: `e.ctrlKey`, `e.shiftKey`, `e.altKey`, `e.metaKey` (⌘ on Mac)

  

### **Input Field Example**

```HTML
<input id="name" placeholder="Type something..." />

<script>
  const input = document.getElementById("name");

  input.addEventListener("keyup", (e) => {
    console.log("You typed:", e.key);
  });
</script>
```

  

### Summary Table

|   |   |
|---|---|
|Property|Description|
|`e.key`|The actual key pressed (`"a"`, `"Enter"`)|
|`e.code`|The physical key on the keyboard|
|`e.ctrlKey`|`true` if Ctrl is held down|
|`e.shiftKey`|`true` if Shift is held down|
|`e.altKey`|`true` if Alt is held down|
|`e.metaKey`|`true` if ⌘ (Mac) or Win key (Windows)|

  

```JavaScript
const myBox = document.getElementById("myBox");

document.addEventListener("keydown", (callback) => {
    myBox.textContent = "✖️";
    myBox.style.backgroundColor = "tomato";
});

document.addEventListener("keyup", (callback) => {
    myBox.textContent = "⭐";
    myBox.style.backgroundColor = "lightblue";
});
```

  

  

```JavaScript
const myBox = document.getElementById("myBox");
const moveAmount = 10;
let x = 0;
let y = 0;

document.addEventListener("keydown", () => {
    myBox.style.backgroundColor = "red";
    myBox.textContent = "✖️";
});

document.addEventListener("keyup", () => {
    myBox.style.backgroundColor = "lightblue";
    myBox.textContent = "⭐";
});

document.addEventListener("keydown", (event) => {
    if (event.key.startsWith("Arrow")) {
        event.preventDefault();
        switch (event.key) {
            case "ArrowUp":
                y -= moveAmount;
                break;
            case "ArrowDown":
                y += moveAmount;
                break;
            case "ArrowLeft":
                x -= moveAmount;
                break;
            case "ArrowRight":
                x += moveAmount;
                break;
            default:
                break;
        }
        myBox.style.top = `${y}px`;
        myBox.style.left = `${x}px`;
    }
});
```