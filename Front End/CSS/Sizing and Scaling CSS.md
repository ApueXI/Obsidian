---
Created: 2025-07-14T09:06
---
### **Absolute Units**

These do not scale with screen or user preferences.

|Unit|Meaning|Use Case|
|---|---|---|
|`px`|Pixels|Most common. 1px = 1 device pixel (usually). Fixed size.|
|`pt`|Points|1pt = 1/72 inch. Used in print styles.|
|`cm`, `mm`, `in`|Centimeters, millimeters, inches|Rare. Mostly for print.|

---

### 🔹 **Relative Units**

These scale based on something else (usually font size).

|Unit|Relative To|Description|
|---|---|---|
|`em`|Parent's font-size|`2em` = 2 × parent font size. Used for spacing and text.|
|`rem`|Root (`html`) font-size|`1rem` = 1 × `html` font-size. More predictable than `em`.|
|`%`|Parent element|`width: 50%` = 50% of parent’s width.|
|`vw`|1% of **viewport width**|`100vw` = full screen width. Good for responsive layouts.|
|`vh`|1% of **viewport height**|`100vh` = full screen height.|
|`vmin`, `vmax`|Smaller/larger of `vw` or `vh`|Useful for square scaling or font-sizing.|
|`ch`|Width of `0` character|Used for aligning text or monospace layouts.|
|`ex`|Height of lowercase `x`|Rarely used.|

---

### 🔸 **Common Font Size Setup**

```CSS
html {
  font-size: 16px; /* Default */
}

body {
  font-size: 1rem;  /* = 16px */
}

h1 {
  font-size: 2rem;  /* = 32px */
}

p {
  font-size: 1em;   /* = body font-size */
}
```

---

### 🔸 **Common Layout Sizing**

```CSS
.container {
  width: 80%;      /* 80% of parent/container */
  max-width: 1200px;  /* Cap width */
  padding: 2rem;   /* Spacing relative to root font */
}

.box {
  width: 10vw;     /* 10% of viewport width */
  height: 50vh;    /* 50% of viewport height */
}
```

---

### ✅ **Best Practices**

- ✅ Use `rem` for font sizes — easier to scale with user preferences.
- ✅ Use `%` for widths in fluid layouts.
- ✅ Use `vh`/`vw` for full-page components (e.g. modals, hero sections).
- ✅ Use `em` for spacing **inside** components (padding, margin).
- ❌ Avoid mixing units too much (`px` with `%`, for example).