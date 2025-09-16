---
Created: 2025-06-18T09:08
---
### `**while**` **Loop – Basic Syntax**

```JavaScript
while (condition) {
  // Code to run while condition is true
}
```

### ✅ **How it works:**

- Checks the `condition`.
- If `true`, runs the loop body.
- Repeats until `condition` becomes `false`.

  

### **Example: Counting from 1 to 5**

```JavaScript
let i = 1;
while (i <= 5) {
  console.log(i);
  i++; // Don't forget to update the variable!
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

  

### **Infinite Loop (avoid this!)**

```JavaScript
let i = 1;
while (i > 0) {
  console.log(i); // This never stops!
}
```

> 🛑 Always make sure the condition will eventually become false.

  

### **Using** `**break**` **to exit early**

```JavaScript
let i = 1;
while (i <= 10) {
  if (i === 5) {
    break; // Exit the loop when i is 5
  }
  console.log(i);
  i++;
}
```

**Output:**

```Plain
1
2
3
4
```

  

### **Using** `**continue**` **to skip an iteration**

```JavaScript
let i = 0;
while (i < 5) {
  i++;
  if (i === 3) {
    continue; // Skip the rest when i is 3
  }
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

  

### **When to use** `**while**` **loop**

- When the number of iterations is unknown.
- When looping depends on a **condition**, not a counter.

  

## `**do...while**` **Loop – Cheat Sheet**

### 🧩 **Basic Syntax**

```JavaScript
do {
  // Code to run at least once
} while (condition);
```

### ✅ **How it works:**

- Runs the loop **once**, no matter what.
- Then checks the `condition`.
- If `true`, repeats the loop.
- If `false`, stops.

  

### **Example: Count from 1 to 5**

```JavaScript
let i = 1;
do {
  console.log(i);
  i++;
} while (i <= 5);
```

**Output:**

```Plain
1
2
3
4
5
```

  

### **Difference from** `**while**`

```JavaScript
let x = 10;
while (x < 5) {
  console.log("This won't run");
}

do {
  console.log("This runs at least once");
} while (x < 5);
```

**Output:**

```Plain
This runs at least once
```

> 📌 Use do...while when at least one run is required, even if the condition is false initially.

  

### **Using** `**break**` **inside** `**do...while**`

```JavaScript
let i = 1;
do {
  if (i === 4) break;
  console.log(i);
  i++;
} while (i <= 5);
```

**Output:**

```Plain
1
2
3
```

  

### **When to use** `**do...while**`

- When you **must run code at least once**.
- When condition depends on something done **during the first iteration**.

  

### `for` vs `while` vs `do...while`

|   |   |   |   |
|---|---|---|---|
|Feature|`for`|`while`|`do...while`|
|Initialization|Inside loop syntax|Outside loop|Outside loop|
|Runs at least once|❌ No|❌ No|✅ Yes|
|Best for|Known repeat count|Unknown conditions|One guaranteed execution|

  

```JavaScript
let isLoggedIn = false;
let username;
let password;

while (!isLoggedIn) {
  username = window.prompt(`Enter your Username: `);
  password = window.prompt(`Enter your Password: `);

  if (username === "brocode" && password === "mypass") {
    isLoggedIn = true;
    console.log(`You are logged in`);
  } else {
    console.log(`Invalid Credentials`);
  }
}
```