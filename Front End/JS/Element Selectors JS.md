---
Created: 2025-06-24T09:26
---
### `**getElementById**`

```JavaScript
const title = document.getElementById("main-title");
```

- ✅ Selects a single element **by ID**.
- ❗ Only works for IDs.
- Returns: **Element** or `null`.

  

### `**getElementsByClassName**`

```JavaScript
const items = document.getElementsByClassName("menu-item");
```

- ✅ Selects **all elements** with a specific class.
- Returns: **HTMLCollection** (live list, not array).
- Access items with `items[0]`, use `Array.from()` to loop easily.

  

### `**getElementsByTagName**`

```JavaScript
const paragraphs = document.getElementsByTagName("p");
```

- ✅ Selects all elements with a specific tag (like `"p"`, `"div"`, etc.).
- Returns: **HTMLCollection**.

  

### `**querySelector**`

```JavaScript
const firstItem = document.querySelector(".menu-item");
const title = document.querySelector("\#main-title");
const input = document.querySelector("input[name='email']");
```

- ✅ Selects the **first match** of a CSS selector.
- Works with classes, IDs, attributes, and nested selectors.

  

### `**querySelectorAll**`

```JavaScript
const allItems = document.querySelectorAll(".menu-item");
```

- ✅ Selects **all matching elements** (like `getElementsByClassName`, but better).
- Returns: **NodeList** (can use `.forEach()` directly).

  

### **Convert Collections to Arrays**

```JavaScript
const items = Array.from(document.getElementsByClassName("box"));
items.forEach(el => el.style.color = "blue");
```

- `HTMLCollection` and `NodeList` aren’t full arrays — use `Array.from()` or `[...spread]` to make them iterable like arrays.

  

### `element.closest(selector)`

Selects the **closest ancestor (or self)** that matches the selector.

```JavaScript
el.closest(".container");
```

  

### `element.parentElement`, `children`, `firstElementChild`, `lastElementChild`

Navigates DOM relationships.

```JavaScript
el.parentElement;
el.children;
el.firstElementChild;
el.lastElementChild;
```

  

### Bonus: Convert Collections to Arrays

For `HTMLCollection` or `NodeList`, to use `map`, `filter`, etc.:

```JavaScript
const items = Array.from(document.getElementsByClassName("card"));
```

  

### Selector Summary Table

|   |   |   |   |
|---|---|---|---|
|Selector|Method|Returns|Notes|
|By ID|`getElementById("id")`|Element / null|Only one match|
|By Class|`getElementsByClassName("class")`|HTMLCollection|Live list|
|By Tag|`getElementsByTagName("p")`|HTMLCollection|Live list|
|First match (CSS)|`querySelector("selector")`|Element / null|Powerful, supports full CSS|
|All matches (CSS)|`querySelectorAll("selector")`|NodeList|Can `.forEach()` directly|

  

### Example Use Case

```HTML
<ul>
  <li class="item">A</li>
  <li class="item">B</li>
</ul>

<script>
  const items = document.querySelectorAll(".item");
  items.forEach(el => el.style.color = "red");
</script>
```

  

```JavaScript
const heading = document.getElementById("h1");

heading.style.backgroundColor = "red";
heading.style.color = "white";
heading.style.textAlign = "center";

const fruits = document.getElementsByClassName("fruits");
fruits[0].style.backgroundColor = "yellow";

for (let fruit of fruits) {
    fruit.style.backgroundColor = "yellow";
}

console.log(fruits);

console.log(heading);
```

  

```JavaScript
const fruits = document.getElementsByClassName("fruits");

Array.from(fruits).forEach((fruit) => (fruit.style.backgroundColor = "yellow"));
```

  

```JavaScript
const h4elem = document.getElementsByTagName("h4");


for (let h4elements of h4elem) {
    h4elements.style.backgroundColor = "yellow";
}
```

  

```JavaScript
const h4elem = document.getElementsByTagName("h4");
const liItems = document.getElementsByTagName("li");

for (let h4elements of h4elem) {
    h4elements.style.backgroundColor = "yellow";
}

for (let listitems of liItems) {
    listitems.style.backgroundColor = "lightgreen";
}


```

  

```JavaScript
const h4elem = document.getElementsByTagName("h4");
const liItems = document.getElementsByTagName("li");

Array.from(h4elem).forEach((h4elemts) => {
    h4elemts.style.backgroundColor = "yellow";
    h4elemts.style.fontSize = "2em";
});

Array.from(liItems).forEach((listItems) => {
    listItems.style.backgroundColor = "lightgreen";
    listItems.style.fontSize = "1.5em";
});
```

  

```JavaScript
const element = document.querySelector("li");

element.style.backgroundColor = "yellow";

console.log(element);
```

  

```JavaScript
const element = document.querySelectorAll("li");

element.forEach((foods) => {
    foods.style.backgroundColor = "yellow";
});
```