---
Created: 2025-11-30T14:38
tags:
  - Basic-Types
---
# ⭐ **Tuples in TypeScript (**`**[number, string]**`**)**

A **tuple** is like an array, but with:

- **Fixed length**
- **Fixed order**
- **Known types at each position**

This makes tuples perfect when each element has a specific meaning.

---

# ✅ **Basic Tuple Example**

```TypeScript
let person: [number, string] = [25, "Alice"];

```

Meaning:

- Index 0 → number
- Index 1 → string

You **cannot** put extra items or swap types:

```TypeScript
person = ["Alice", 25]; // ❌ Wrong order
person = [25, "Alice", true]; // ❌ Too many items

```

---

# 🔹 Using Tuples for Return Values

Useful when returning multiple values:

```TypeScript
function getCoordinates(): [number, number] {
  return [10, 20];
}

```

---

# 🔹 Named Tuples (Optional Syntax)

Helps readability:

```TypeScript
let user: [id: number, username: string] = [1, "nein"];

```

---

# 🔹 Tuple with Mixed Types

```TypeScript
let data: [string, number, boolean] = ["Score", 95, true];

```

---

# 🔹 Tuple with Optional Elements

```TypeScript
let settings: [string, number?] = ["Volume"];

```

---

# 🔹 Rest Elements in Tuples

Allows flexibility while maintaining structure:

```TypeScript
let nums: [number, ...number[]] = [1, 2, 3, 4];

```

---

# ❗ Common Pitfalls

### 1. Tuples Are Still Arrays at Runtime

You can do array operations:

```TypeScript
person.push("extra"); // ✔️ Allowed at runtime

```

But TypeScript will complain **when you try to read it** if it violates the tuple type.

### 2. Order Always Matters

Tuples are not just typed arrays — **the position defines the meaning**.

---

# 📋 Summary Table

|Tuple Example|Meaning|
|---|---|
|`[number, string]`|Exactly two items: number then string|
|`[string, boolean, number]`|Three items, fixed order|
|`[id: number, name: string]`|Named tuple (more readable)|
|`[string, number?]`|Second value optional|
|`[number, ...number[]]`|Starts with one number, rest are numbers|