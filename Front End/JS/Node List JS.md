---
Created: 2025-06-25T16:05
---
**What Is a NodeList?**

A **NodeList** is a **collection of DOM nodes** (like elements, text nodes, comments) returned by DOM query methods such as:

```JavaScript
const items = document.querySelectorAll(".item"); // NodeList
```

- Looks like an array ✅
- But **not a real array** ❗

  

### **How to Get a NodeList**

```JavaScript
// Returns a static NodeList
const list = document.querySelectorAll("li");

// Returns a live NodeList (auto-updates)
const liveList = document.getElementsByTagName("li");
```

|   |   |
|---|---|
|Method|Type of NodeList|
|`querySelectorAll()`|**Static**|
|`getElementsByClassName()`|**Live**|
|`getElementsByTagName()`|**Live**|

  

### **Looping Through a NodeList**

```JavaScript
list.forEach((el, i) => {
  console.log(i, el.textContent);
});
```

✅ `NodeList` supports `.forEach()` (but not `.map`, `.filter`, etc.)

  

### **Convert NodeList to Array**

```JavaScript
const itemsArray = Array.from(list);
// or
const itemsArray2 = [...list];

itemsArray.map(el => el.textContent.toUpperCase());
```

- Enables use of full array methods: `.map()`, `.filter()`, etc.

  

### **Access Individual Nodes**

```JavaScript
const first = list[0];
const last = list[list.length - 1];
```

  

### **Node vs Element**

A **NodeList** may include:

- `Element` nodes (like `<div>`, `<p>`)
- `Text` nodes
- `Comment` nodes

So be careful: `NodeList` ≠ just elements unless you know your selector only returns elements (e.g. `querySelectorAll("div")`).

  

### Summary Table

|   |   |
|---|---|
|Feature|Notes|
|Looks like an array|Indexed, has `.length`, supports `forEach()`|
|Not a real array|No `.map()`, `.filter()` unless converted|
|Live vs static|`getElementsBy*` = live, `querySelectorAll` = static|
|Convert to array|`Array.from()` or `[...NodeList]`|
|Common source methods|`querySelectorAll`, `getElementsByTagName`|

  

### Example

```HTML
<ul>
  <li class="item">A</li>
  <li class="item">B</li>
</ul>

<script>
  const items = document.querySelectorAll(".item");
  items.forEach(el => el.style.color = "blue");
</script>
```

  

```JavaScript
let myButton = document.querySelectorAll(".myButtons");

myButton.forEach((button) => {
    button.style.backgroundColor = "green";
    button.textContent += "⭐";
});
```

  

```JavaScript
let myButton = document.querySelectorAll(".myButtons");

myButton.forEach((button) => {
    button.addEventListener("click", (event) => {
        event.target.style.backgroundColor = "tomato";
    });
});
```

  

```JavaScript
let myButton = document.querySelectorAll(".myButtons");

myButton.forEach((button) => {
    button.addEventListener("mouseover", (event) => {
        event.target.style.backgroundColor = "hsl(205, 100%, 40%)";
    });
    button.addEventListener("mouseout", (event) => {
        event.target.style.backgroundColor = "hsl(205, 100%, 60%)";
    });
});
```

  

```JavaScript
const myButton = document.querySelectorAll(".myButtons");

myButton.forEach((button) => {
    button.addEventListener("mousedown", (event) => {
        event.target.style.backgroundColor = "hsl(0, 100%, 50%)";
    });
    button.addEventListener("mouseup", (event) => {
        event.target.style.backgroundColor = "hsl(150, 100%, 50%)";
    });
    button.addEventListener("mouseover", (event) => {
        event.target.style.backgroundColor = "hsl(205, 100%, 40%)";
    });
    button.addEventListener("mouseout", (event) => {
        event.target.style.backgroundColor = "hsl(205, 100%, 60%)";
    });
});
```

  

### Use queryselectall to update the node buttons since it is a static collection not live

```JavaScript
let myButton = document.querySelectorAll(".myButtons");

const newButton = document.createElement("Button");

newButton.textContent = "Button 5";
newButton.className = "myButtons";

document.body.appendChild(newButton);

myButton = document.querySelectorAll(".myButtons");

console.log(myButton);
```

  

```JavaScript
let myButton = document.querySelectorAll(".myButtons");

myButton.forEach((button) => {
    button.addEventListener("click", (event) => {
        event.target.remove();
        button = document.querySelectorAll('.myButtons');
        console.log(button);
    });
});
```