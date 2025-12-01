---
Created: 2025-11-30T14:39
tags:
  - Basic-Types
---
# **Literal Types in TypeScript**

Literal types let you restrict a variable to a **specific fixed value**, instead of allowing the full broader type like `string` or `number`.

They are extremely useful for:

- Writing safer code
- Preventing invalid values
- Creating function parameters that accept only specific “allowed options”

---

## ✅ **Definition**

A **literal type** is a type that represents **exact values**, like:

- Specific strings
- Specific numbers
- Specific booleans

For example:

```TypeScript
let direction: "left" | "right";

```

This means:

- `direction` **can only be** `**"left"**` **or** `**"right"**`
- Any other string is **not allowed** and TypeScript will throw an error

---

## ✅ **Why Literal Types Are Useful**

They create **strict, predictable** APIs because they:

### ✔ Prevent invalid inputs

```TypeScript
direction = "forward";  // ❌ Error

```

### ✔ Enable autocomplete

VS Code will only suggest `"left"` and `"right"`.

### ✔ Work great with discriminated unions

(This becomes powerful when building complex types.)

---

## 🚀 **Examples**

### **Basic usage**

```TypeScript
let direction: "left" | "right";

direction = "left";   // OK
direction = "right";  // OK
direction = "up";     // ❌ Error

```

---

### **With functions**

Literal types shine when defining safe function parameters:

```TypeScript
function move(direction: "left" | "right") {
  console.log(`Moving ${direction}`);
}

move("left");  // OK
move("right"); // OK
move("back");  // ❌ Error

```

---

### **With numbers**

```TypeScript
let httpStatus: 200 | 404 | 500;

httpStatus = 200; // OK
httpStatus = 403; // ❌ Error

```

---

## 🧩 **Combining with type aliases**

This makes reusable literal-type groups:

```TypeScript
type Direction = "left" | "right" | "up" | "down";

let d: Direction = "up"; // OK

```

---

## ⚠️ Gotchas

### ❗ Literal types don’t allow anything outside the allowed set

TypeScript is strict here — `"Left"` is not `"left"`.

### ❗ If you store it in a wider type, it widens

```TypeScript
let x = "left"; // type: string (widened)

```

Use `as const` to preserve literal:

```TypeScript
const x = "left"; // type: "left"

```