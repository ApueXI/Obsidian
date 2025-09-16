---
Created: 2025-06-24T10:25
---
## JavaScript DOM Navigation Cheat Sheet

DOM navigation means moving between elements in the DOM tree: **parent**, **child**, and **sibling** nodes.

  

### **Parent Element**

```JavaScript
element.parentElement
```

- Gets the **direct parent** of an element.

```JavaScript
const child = document.querySelector(".child");
const parent = child.parentElement;
```

  

### **Child Elements**

```JavaScript
element.children
```

- Gets an **HTMLCollection** of all direct children (**elements only**).

```JavaScript
const list = document.querySelector("ul");
console.log(list.children); // All <li> inside
```

  

### **First and Last Child**

```JavaScript
element.firstElementChild
element.lastElementChild
```

- Get the **first** or **last child element**.

  

### **All Descendants**

```JavaScript
element.querySelectorAll("li")
```

- Use this to find **any nested match** under a parent element.

  

### **Sibling Elements**

```JavaScript
element.previousElementSibling
element.nextElementSibling
```

- Get the element **before** or **after** the current one (same parent level).

```JavaScript
const current = document.querySelector(".active");
const next = current.nextElementSibling;
```

  

### **Node vs Element**

|   |   |
|---|---|
|Property|What it includes|
|`.childNodes`|All child **nodes** (elements, text, etc.)|
|`.children`|Only child **elements**|
|`.parentNode`|Like `parentElement`, but may return `#document`|
|`.firstChild`|May return a **text node** (like whitespace)|

✅ Prefer `Element` versions unless you need to work with **text** or **comments**.

  

### **Closest Ancestor (with selector)**

```JavaScript
element.closest(".container")
```

- Walks **up** the tree to find the **nearest ancestor** matching a CSS selector.

  

### **Example**

```HTML
html
CopyEdit
<ul>
  <li>One</li>
  <li class="target">Two</li>
  <li>Three</li>
</ul>

```

```JavaScript
const target = document.querySelector(".target");
console.log(target.parentElement); // <ul>
console.log(target.previousElementSibling.textContent); // "One"
console.log(target.nextElementSibling.textContent);     // "Three"
```

  

### Summary Table

|   |   |
|---|---|
|Property|Description|
|`.parentElement`|Direct parent element|
|`.children`|Direct child elements only|
|`.firstElementChild`|First child element|
|`.lastElementChild`|Last child element|
|`.nextElementSibling`|Next element on the same level|
|`.previousElementSibling`|Previous element on the same level|
|`.closest(selector)`|Nearest matching ancestor|
|`.childNodes`|All children (elements + text)|
|`.parentNode`|Parent node (not always an element)|

  

```JavaScript
const ulelements = document.querySelectorAll("ul");

ulelements.forEach((unorderedList) => {
    const firstchild = unorderedList.firstElementChild;
    firstchild.style.backgroundColor = "yellow";
});
```

  

  

```JavaScript
const elme = document.getElementById("fruits");

const lastchiild = elme.lastElementChild;

lastchiild.style.backgroundColor = "yellow";
```

  

```JavaScript
const ulElements = document.querySelectorAll("ul");

ulElements.forEach((ulElem) => {
    const lastchild = ulElem.lastElementChild;
    lastchild.style.backgroundColor = "yellow";
});
```

  

```JavaScript
const ulElements = document.querySelectorAll("ul");

ulElements.forEach((ulElem) => {
    const lastchild = ulElem.lastElementChild;
    lastchild.style.backgroundColor = "yellow";
});

```

```JavaScript
const element = document.getElementById("fruits");

const nextSibling = element.nextElementSibling;

nextSibling.style.backgroundColor = "yellow";
```

  

```JavaScript
const element = document.getElementById("orange");

const prevSibling = element.previousElementSibling;

prevSibling.style.backgroundColor = "yellow";
```

  

```JavaScript
const element = document.getElementById("cake");

const parent = element.parentElement;
parent.style.backgroundColor = "yellow";
```

  

```JavaScript
const element = document.getElementById("fruits");

const children = element.children;

Array.from(children).forEach((child) => {
    child.style.backgroundColor = "yellow";
    child.style.fontSize = "1.3em";
});
```

```JavaScript
const element = document.getElementById("fruits");

const children = element.children;


children[1].style.backgroundColor = "yellow";
```