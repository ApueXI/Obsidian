---
Created: 2025-06-24T20:18
---
### **Common Mouse Events**

|   |   |
|---|---|
|Event Name|Triggered When...|
|`click`|User clicks (press & release) mouse|
|`dblclick`|User double-clicks|
|`mousedown`|Mouse button is pressed|
|`mouseup`|Mouse button is released|
|`mousemove`|Mouse moves over an element|
|`mouseenter`|Mouse enters the element (no bubbling)|
|`mouseleave`|Mouse leaves the element (no bubbling)|
|`mouseover`|Mouse enters (bubbles)|
|`mouseout`|Mouse leaves (bubbles)|
|`contextmenu`|Right-click happens|

  

### **Basic Click Example**

```JavaScript
const btn = document.querySelector("button");

btn.addEventListener("click", () => {
  alert("Button clicked!");
});
```

  

### **Detect Mouse Coordinates**

```JavaScript
document.addEventListener("mousemove", (e) => {
  console.log(`X: ${e.clientX}, Y: ${e.clientY}`);
});
```

- `e.clientX`, `e.clientY` → coordinates **relative to the viewport**.
- `e.pageX`, `e.pageY` → relative to the **entire page**.

  

### **Hover Effects (mouseenter & mouseleave)**

```JavaScript
const box = document.querySelector(".box");

box.addEventListener("mouseenter", () => {
  box.style.background = "lightblue";
});

box.addEventListener("mouseleave", () => {
  box.style.background = "";
});
```

- `**mouseenter**` **and** `**mouseleave**` **don’t bubble — good for pure hover effects.**

  

### **Right Click (Disable Context Menu)**

```JavaScript
document.addEventListener("contextmenu", (e) => {
  e.preventDefault(); // disable default right-click
  alert("Right-click disabled!");
});
```

  

### **Use Event Object Properties**

```JavaScript
element.addEventListener("click", function (e) {
  console.log("Which button:", e.button); // 0 = left, 2 = right
  console.log("Target:", e.target);       // element clicked
});
```

  

### Summary Table

|   |   |   |
|---|---|---|
|Task|Code Example|Description|
|Basic click|`addEventListener("click", fn)`|Most common mouse event|
|Right click|`addEventListener("contextmenu", fn)`|Use `e.preventDefault()` to block|
|Mouse position|`e.clientX`, `e.clientY`|Get position on screen|
|Hover|`mouseenter` / `mouseleave`|Trigger only on direct enter/exit|
|Movement|`mousemove`|Constant updates as mouse moves|

  

```JavaScript
const myBox = document.getElementById("myBox");

function changeColor(event) {
    event.target.style.backgroundColor = "red";
    event.target.textContent = "OUCH!!";
}

myBox.addEventListener("click", (event) => {
    event.target.style.backgroundColor = "red";
    event.target.textContent = "OUCH!!";
});
```

  

### My Code (fucking terrible)

```JavaScript
function changeColor(event) {
    event.target.style.backgroundColor = "red";
    event.target.textContent = "OUCH!!";
}

myBox.addEventListener("click", (event) => {
    event.target.style.backgroundColor = "red";
    let say = "OUCH!!";
    event.target.textContent = say;
    if (myBox.textContent == say) {
        myBox.addEventListener("click", (event) => {
            event.target.style.backgroundColor = "blue";
            event.target.textContent = "Again!!";
        });
    }
});
"
```

### ChatGpt

```JavaScript
const myBox = document.getElementById("myBox");

let clickedOnce = false;

function changeColor(event) {
    event.target.style.backgroundColor = "red";
    event.target.textContent = "OUCH!!";
}

myBox.addEventListener("click", (event) => {
    if (!clickedOnce) {
        event.target.style.backgroundColor = "red";
        event.target.textContent = "OUCH!!";
        clickedOnce = true;
    } else {
        event.target.style.backgroundColor = "blue";
        event.target.textContent = "Again!!";
        clickedOnce = false;
    }
});
```

### More Good way

```JavaScript
const myBox = document.getElementById("myBox");

const states = [
    { text: "OUCH!!", color: "red" },
    { text: "Again!!", color: "blue" },
    { text: "Stop it!", color: "orange" }
];

let clickCount = 0;

myBox.addEventListener("click", (event) => {
    const state = states[clickCount % states.length];
    event.target.textContent = state.text;
    event.target.style.backgroundColor = state.color;
    clickCount++;
});
```

  

```JavaScript
const myBox = document.getElementById("myBox");
const myButton = document.getElementById("myButton");

const states = [
    { text: "OUCH!!", color: "red" },
    { text: "Again!!", color: "blue" },
    { text: "Stop it!", color: "orange" },
];

let clickCount = 0;

myButton.addEventListener("click", () => {
    const state = states[clickCount % states.length];
    myBox.textContent = state.text;
    myBox.style.backgroundColor = state.color;
    clickCount++;
});

myButton.addEventListener("mouseover", () => {
    myBox.style.backgroundColor = "violet";
    myBox.textContent = "WAH!";
});

myButton.addEventListener("mouseout", () => {
    myBox.style.backgroundColor = "orange";
    myBox.textContent = "Thank God";
});
```