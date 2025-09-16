---
Created: 2025-07-12T20:55
---
## **CSS** `**calc()**` **Cheat Sheet**

### ✅ **Basic Syntax**

```CSS
property: calc(expression);
```

- Combines different **units** (%, px, rem, etc.)
- Example:
    
    ```CSS
    width: calc(100% - 50px);
    ```
    

---

### ⚒️ **Common Use Cases**

### 1. **Fixed + Fluid Layouts**

```CSS
main {
  width: calc(100% - 250px); /* subtract sidebar width */
}
```

### 2. **Centering Elements**

```CSS
.left {
  left: calc(50% - 100px); /* center a 200px-wide element */
}
```

### 3. **Responsive Typography**

```CSS
h1 {
  font-size: calc(1rem + 2vw);
}
```

### 4. **Padding with Gaps**

```CSS
.section {
  padding: calc(2rem + 10px);
}
```

---

### 🧠 **Math Operators**

|Operator|Use|
|---|---|
|`+`|Addition|
|`-`|Subtraction|
|`*`|Multiplication|
|`/`|Division|

⚠️ Only `+` and `-` work with **mixed units**

✅ `*` and `/` only work with **same-unit** values (like `10px * 2`)

---

### 🚫 **Spaces Are Required**

✅ Correct:

```CSS
width: calc(100% - 20px);
```

❌ Wrong:

```CSS
width: calc(100%-20px); /* Invalid */
```

---

### 🔄 **Combining with Variables**

```CSS
:root {
  --sidebar: 200px;
}

main {
  width: calc(100% - var(--sidebar));
}
```

---

### 📱 **Responsive Example**

```CSS
.card {
  padding: calc(1rem + 1vw);
  font-size: calc(1rem + 0.5vw);
}
```

---

### 📊 **Useful Combinations**

- `clamp()` + `calc()`
    
    ```CSS
    font-size: clamp(1rem, calc(1rem + 1vw), 2rem);
    ```
    
- `min()`, `max()` with `calc()`
    
    ```CSS
    width: min(100%, calc(600px + 2rem));
    ```