---
Created: 2025-07-13T15:01
---
### 🔹 Basic Syntax

```CSS
selector {
  transition: property duration timing-function delay;
}
```

### 🔹 Shorthand Example

```CSS
.box {
  transition: all 0.3s ease-in-out 0s;
}
```

---

## 🔧 Transition Properties

|Property|Description|Example|
|---|---|---|
|`transition-property`|Specifies the CSS property to transition|`transition-property: background-color;`|
|`transition-duration`|Time it takes for the transition to complete|`transition-duration: 0.5s;`|
|`transition-timing-function`|Defines speed curve|`transition-timing-function: ease-in-out;`|
|`transition-delay`|Delays the start of the transition|`transition-delay: 0.2s;`|

---

## ⏱ Timing Functions

|Function|Description|
|---|---|
|`linear`|Same speed from start to end|
|`ease`|Slow start, fast, then slow end|
|`ease-in`|Slow start|
|`ease-out`|Slow end|
|`ease-in-out`|Slow start and end|
|`steps(n)`|Jump between steps (e.g., sprite animation)|
|`cubic-bezier(x1, y1, x2, y2)`|Custom timing curve|

---

## 🛠 Example Use Case

### HTML

```HTML
<div class="box"></div>
```

### CSS

```CSS
.box {
  width: 100px;
  height: 100px;
  background: blue;
  transition: background 0.5s ease, transform 0.3s ease-in-out;
}

.box:hover {
  background: red;
  transform: scale(1.2);
}
```

---

## 💡 Tips

- You can transition multiple properties separated by commas.
- Not all CSS properties are animatable (e.g., `display` cannot be transitioned).
- Use `will-change` to hint at properties that will change for better performance:
    
    ```CSS
    .box {
      will-change: transform, opacity;
    }
    ```