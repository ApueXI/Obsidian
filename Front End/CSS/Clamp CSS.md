---
Created: 2025-07-12T20:55
---
### **What is** `**clamp()**`**?**

```CSS
clamp(MIN, PREFERRED, MAX)
```

- It sets a **responsive value** that:
    - **Never goes below** the `MIN`
    - **Scales fluidly** toward the `PREFERRED` value
    - **Never exceeds** the `MAX`

---

### 🧠 **Basic Usage**

```CSS
font-size: clamp(1rem, 2vw, 2rem);
```

- `1rem` → Minimum font size
- `2vw` → Preferred scaling with viewport width
- `2rem` → Maximum font size

---

### 📐 **Common Use Cases**

### 1. **Font Sizes**

```CSS
h1 {
  font-size: clamp(2rem, 5vw, 4rem);
}
```

### 2. **Padding**

```CSS
section {
  padding: clamp(1rem, 2vw, 3rem);
}
```

### 3. **Margin**

```CSS
.container {
  margin-top: clamp(1rem, 5vh, 4rem);
}
```

### 4. **Width / Height**

```CSS
img {
  width: clamp(200px, 50vw, 600px);
}
```

---

### 📏 **Units You Can Use**

- `rem`, `em`, `px`, `%`, `vw`, `vh`
- You can mix units!

---

### 🧮 **Advanced: Calculated Clamp**

```CSS
font-size: clamp(1rem, calc(1rem + 2vw), 3rem);
```

- Adds `2vw` scaling on top of `1rem`

---

### 🚨 **Browser Support**

- ✅ **All modern browsers**
- ❌ Not supported in **IE**