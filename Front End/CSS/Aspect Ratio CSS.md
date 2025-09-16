---
Created: 2025-07-12T20:55
---
## **CSS** `**aspect-ratio**` **Cheat Sheet**

### ✅ **Basic Syntax**

```CSS
aspect-ratio: WIDTH / HEIGHT;
```

- Example:
    
    ```CSS
    .box {
      aspect-ratio: 16 / 9;
    }
    
    ```
    

---

### 🎯 **Common Aspect Ratios**

|Ratio|Use Case|
|---|---|
|`1 / 1`|Square|
|`16 / 9`|Widescreen video|
|`4 / 3`|Old TVs / standard cams|
|`3 / 2`|Photography|
|`21 / 9`|Ultrawide monitors|

---

### 📦 **Minimum Required Styles**

You **must** set either:

- A **width**, and aspect ratio auto-calculates height
- Or a **height**, and aspect ratio auto-calculates width
- Or use `width: 100%` to make it responsive

```CSS
.box {
  width: 100%;
  aspect-ratio: 4 / 3;
  background: lightblue;
}
```

---

### 🛠️ **With** `**clamp()**` **for Responsive Ratios**

```CSS
.box {
  aspect-ratio: clamp(1 / 1, 16 / 9, 21 / 9); /* Not valid! ❌ */
}
```

⚠️ `clamp()` **doesn't work** directly inside `aspect-ratio`.

👉 Instead, use it to affect width or height **indirectly**:

```CSS
.box {
  width: clamp(300px, 50%, 800px);
  aspect-ratio: 16 / 9;
}
```

---

### 📱 **Responsive Example**

```CSS
.responsive-video {
  width: 100%;
  aspect-ratio: 16 / 9;
}
```

---

### 🧾 **Fallback (Pre-Aspect-Ratio Support)**

```CSS
.box {
  position: relative;
  padding-top: 56.25%; /* 16:9 = 9/16 = 0.5625 */
  height: 0;
}

.box > * {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
```

---

### 🧪 **Browser Support**

- ✅ Chrome, Firefox, Safari, Edge
- ❌ Not supported in **Internet Explorer**