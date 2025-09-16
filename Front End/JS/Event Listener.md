---
Created: 2025-07-11T13:32
---
## Basic Syntax

```JavaScript
element.addEventListener('event', callback, useCapture);
```

### Example:

```JavaScript
document.getElementById("btn").addEventListener("click", function() {
  alert("Button clicked!");
});
```

---

## 🧾 2. Event Types

|Type|Example Events|
|---|---|
|Mouse|`click`, `dblclick`, `mousedown`, `mouseup`, `mouseenter`, `mouseleave`, `mousemove`, `mouseover`, `mouseout`, `contextmenu`|
|Keyboard|`keydown`, `keypress`, `keyup`|
|Form|`submit`, `change`, `input`, `focus`, `blur`, `reset`|
|Window|`load`, `resize`, `scroll`, `unload`|
|Clipboard|`copy`, `cut`, `paste`|
|Drag & Drop|`drag`, `dragstart`, `dragend`, `dragenter`, `dragleave`, `dragover`, `drop`|
|Touch|`touchstart`, `touchend`, `touchmove`, `touchcancel`|
|Media|`play`, `pause`, `ended`, `volumechange`, `timeupdate`|
|Others|`animationstart`, `animationend`, `transitionend`, `error`|

---

## 🧰 3. Arrow vs Regular Functions

- **Arrow functions** don't have their own `this`, so avoid using them if you need `this`.

```JavaScript
button.addEventListener("click", function() {
  console.log(this); // Points to button
});

button.addEventListener("click", () => {
  console.log(this); // Points to outer scope, not button!
});
```

---

## 🧪 4. Accessing Event Object

```JavaScript
element.addEventListener("click", function(event) {
  console.log(event.type); // "click"
  console.log(event.target); // clicked element
});
```

---

## 🔁 5. Removing Event Listeners

```JavaScript
function handler() {
  alert("Removed!");
}

element.addEventListener("click", handler);
element.removeEventListener("click", handler);
```

- **Important:** The function reference must be the same (named, not anonymous).

---

## 🏁 6. Event Propagation

### Bubbling (default)

- Event flows from child → parent

### Capturing

- Event flows from parent → child

```JavaScript
element.addEventListener("click", handler, true); // Capture phase
```

---

## 🛑 7. Stop Propagation & Prevent Default

```JavaScript
event.stopPropagation(); // Stops bubbling/capturing
event.preventDefault(); // Prevents default action (e.g., link navigation)
```

---

## 📌 8. once, passive, capture Options (Event Listener Options)

```JavaScript
element.addEventListener("scroll", handler, {
  once: true,          // Only runs once
  passive: true,       // Tells browser not to block scroll
  capture: true        // Use capture phase
});
```

---

## 🧩 9. Delegation (Best Practice for Many Elements)

```JavaScript
document.body.addEventListener("click", function(event) {
  if (event.target.matches("button")) {
    console.log("Button clicked!");
  }
});
```

✅ Good for dynamic content

✅ Improves performance

---

## 📚 10. Custom Events

```JavaScript
const myEvent = new CustomEvent("myevent", {
  detail: { name: "ChatGPT" }
});

element.addEventListener("myevent", function(e) {
  console.log(e.detail.name); // ChatGPT
});

element.dispatchEvent(myEvent);
```

---

## 🏷️ 11. Named vs Anonymous Listeners

```JavaScript
function handleClick() {
  alert("Clicked!");
}

element.addEventListener("click", handleClick); // ✅ removable

element.addEventListener("click", function() {
  alert("Clicked!");
}); // ❌ not removable
```

---

## 📋 12. Useful Event Properties

|Property|Description|
|---|---|
|`event.type`|Type of the event (`click`, `keydown`)|
|`event.target`|Element that triggered the event|
|`event.currentTarget`|Element where the listener is attached|
|`event.key`|Keyboard key pressed|
|`event.code`|Physical key on keyboard|
|`event.clientX/Y`|Mouse position in viewport|
|`event.pageX/Y`|Mouse position relative to page|
|`event.altKey`, `event.ctrlKey`, `event.shiftKey`|Modifier keys|

---

## 🛠️ 13. Keyboard Events

```JavaScript
document.addEventListener("keydown", function(event) {
  if (event.key === "Enter") {
    console.log("Enter pressed");
  }
});
```

---

## 💡 14. Triggering Events Programmatically

```JavaScript
element.click(); // Triggers a click event

const e = new Event("change");
element.dispatchEvent(e);
```

---

## 🧼 15. Cleanup (especially in frameworks)

If you’re using event listeners in components (e.g. React, Vanilla JS modules), always clean up:

```JavaScript
function setup() {
  window.addEventListener("resize", onResize);

  return function cleanup() {
    window.removeEventListener("resize", onResize);
  };
}
```