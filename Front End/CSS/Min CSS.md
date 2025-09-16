---
Created: 2025-07-14T11:23
---
## What is `min()` in CSS?

The `min()` function allows you to set a CSS property to the **smallest (minimum) value** from a **comma-separated list** of expressions.

```CSS
property: min(value1, value2, ...);
```

---

## 🔧 Syntax

```CSS
selector {
  property: min(<value1>, <value2>, ...);
}
```

- Accepts **length units** (px, em, rem, %, vw, vh, etc.)
- Accepts **math expressions**
- Can mix relative and absolute values

---

## 💡 Common Use Cases

### 📱 Responsive Font Size

```CSS
h1 {
  font-size: min(5vw, 32px);
}
```

> Use 5% of the viewport width but don’t exceed 32px.

---

### 📐 Constrain Container Width

```CSS
.container {
  width: min(100%, 1200px);
}
```

> Use full width unless it exceeds 1200px.

---

### 🧱 Button Padding

```CSS
button {
  padding: min(2vw, 20px);
}
```

> Dynamically responsive but capped at 20px.

---

### 🖼️ Image Height

```CSS
img {
  height: min(50vh, 300px);
}
```

> Image takes up to half the viewport height, but no more than 300px.

---

## ⚠️ Notes

- Supported in all modern browsers (Chrome, Firefox, Safari, Edge).
- Can be **nested with** `**max()**` or `clamp()`:
    
    ```CSS
    font-size: clamp(14px, min(5vw, 2rem), 24px);
    ```
    

---

## 🧮 Difference from Similar Functions

|Function|Description|
|---|---|
|`min()`|Picks the smallest value|
|`max()`|Picks the largest value|
|`clamp()`|Limits a value between a min and a max|

---

## ✅ Use Tips

- Use for **fluid layouts** and **responsive design**.
- Great for setting **limits** on dynamic values.
- Combine with media queries for powerful control.