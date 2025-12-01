---
Created: 2025-11-30T14:38
tags:
  - Basic-Types
---
# ⭐ **Arrays in TypeScript (**`**number[]**`**,** `**Array<string>**`**)**

In TypeScript, arrays hold **multiple values of the same type**.

You can declare arrays in **two different syntaxes**, and both are valid.

---

# ✅ **1. Shorthand Syntax:** `**type[]**`

This is the most commonly used form.

### Example:

```TypeScript
let numbers: number[] = [1, 2, 3];
let names: string[] = ["Alice", "Bob", "Charlie"];

```

✔️ Clean and readable

✔️ Most developers prefer this style

---

# ✅ **2. Generic Syntax:** `**Array<type>**`

This uses TypeScript’s generic `Array<T>` type.

### Example:

```TypeScript
let numbers: Array<number> = [1, 2, 3];
let names: Array<string> = ["Alice", "Bob"];

```

✔️ Useful when nesting types:

```TypeScript
Array<Array<number>> // 2D array

```

---

# 📌 Both syntaxes are equivalent

These are the same:

```TypeScript
let nums1: number[] = [1, 2, 3];
let nums2: Array<number> = [1, 2, 3];

```

Choose whichever style you prefer.

---

# 🔹 Array with Other Types

```TypeScript
let flags: boolean[] = [true, false, true];
let mixed: (string | number)[] = ["hello", 10];

```

---

# 🔹 Arrays of objects

```TypeScript
let users: { name: string; age: number }[] = [
  { name: "Alice", age: 20 },
  { name: "Bob", age: 25 },
];

```

---

# 🔹 Common Pitfall: Array of any

```TypeScript
let anything: any[] = [1, "two", true]; // ❌ Avoid unless needed

```

---

# 📋 Summary Table

|Syntax|Example|Meaning|
|---|---|---|
|`number[]`|`[1, 2, 3]`|Array of numbers|
|`string[]`|`["a", "b"]`|Array of strings|
|`Array<number>`|`[1, 2, 3]`|Generic array of numbers|
|`Array<string>`|`["a", "b"]`|Generic array of strings|
|`(string|number)[]`|`["x", 2]`|