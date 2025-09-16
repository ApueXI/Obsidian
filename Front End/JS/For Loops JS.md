---
Created: 2025-06-18T09:42
---
## `**for**` **Loop – Cheat Sheet**

### 🧩 **Basic Syntax**

```JavaScript
for (initialization; condition; update) {
  // Code to run each loop
}
```

- **initialization** – Runs once before the loop starts.
- **condition** – Checked before every loop iteration.
- **update** – Runs after each iteration.

  

### **Example: Count from 1 to 5**

```JavaScript
for (let i = 1; i <= 5; i++) {
  console.log(i);
}
```

**Output:**

```Plain
1
2
3
4
5
```

  

### **Using** `**break**` **in a** `**for**` **loop**

```JavaScript
for (let i = 1; i <= 5; i++) {
  if (i === 4) break;
  console.log(i);
}
```

**Output:**

```Plain
1
2
3
```

  

### **Using** `**continue**` **to skip iteration**

```JavaScript
for (let i = 1; i <= 5; i++) {
  if (i === 3) continue;
  console.log(i);
}
```

**Output:**

```Plain
1
2
4
5
```

  

### **Looping Backwards**

```JavaScript
for (let i = 5; i >= 1; i--) {
  console.log(i);
}
```

**Output:**

```Plain
5
4
3
2
1
```

  

### **Looping Through Arrays**

```JavaScript
let fruits = ["apple", "banana", "cherry"];
for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```

**Output:**

```Plain
apple
banana
cherry
```

  

### **When to use** `**for**` **loop**

- When you **know how many times** you want to repeat something.
- When **iterating through arrays or sequences**.

  

### `for` vs `while` vs `do...while`

|   |   |   |   |
|---|---|---|---|
|Feature|`for`|`while`|`do...while`|
|Initialization|Inside loop syntax|Outside loop|Outside loop|
|Runs at least once|❌ No|❌ No|✅ Yes|
|Best for|Known repeat count|Unknown conditions|One guaranteed execution|

  

```JavaScript
for (let index = 1; index <= 20; index++) {
  if (index == 13) {
    continue;
  }
  console.log(index);
}
```