---
Created: 2025-11-30T14:37
tags:
  - Basic-Types
---
# ⭐ **Basic Types in TypeScript:** `**string**`**,** `**number**`**,** `**boolean**`

These are the **three core primitive types** in TypeScript. They represent the simplest forms of data.

---

# ✅ **1.** `**string**` **— Text Data**

Represents sequences of characters.

### Example:

```TypeScript
let username: string = "Alice";
let message: string = `Hello, world!`;

```

✔️ Supports single, double, or backtick (template literal) quotes.

---

# ✅ **2.** `**number**` **— Numeric Values**

Represents **all numbers** (integers, floats, NaN, Infinity).

TypeScript/JavaScript do **not** have separate int/float types.

### Example:

```TypeScript
let age: number = 25;
let height: number = 5.9;
let temperature: number = -10;

```

---

# ✅ **3.** `**boolean**` **— True or False Values**

Represents logical values.

### Example:

```TypeScript
let isLoggedIn: boolean = true;
let isAdmin: boolean = false;

```

---

# 📌 Putting Them Together

```TypeScript
let name: string = "Bob";
let score: number = 95;
let isPassed: boolean = true;

```

---

# 🧠 Why These Types Matter

- Help TypeScript catch incorrect assignments
- Improve autocompletion and editor hints
- Prevent runtime type confusion
- Make your program more predictable

---

# 📋 Summary Table

|Type|Example|Description|
|---|---|---|
|`string`|`"hello"`|Text characters|
|`number`|`42`, `3.14`, `NaN`|Any numeric value|
|`boolean`|`true`, `false`|Logical true/false|