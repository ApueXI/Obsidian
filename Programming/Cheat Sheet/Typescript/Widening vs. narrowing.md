---
Created: 2025-11-30T14:41
tags:
  - Type-System
---
# **Widening vs. Narrowing in TypeScript**

TypeScript uses **type inference** to guess the most appropriate type.

During this process, types may:

- **Widen** → become more general
- **Narrow** → become more specific

Understanding this helps avoid bugs and explains why some inferred types behave unexpectedly.

---

# ✅ **1. Widening**

**Widening** happens when TypeScript takes a literal value and **expands it into a broader type**.

### ✔ Example (string literal widens)

```TypeScript
let dir = "left";

```

TypeScript infers:

```Plain
dir: string     // NOT "left"

```

Why?

Because with `**let**`, TypeScript assumes the variable may change later.

### Other widening examples

### ✔ Number literal

```TypeScript
let count = 1;

```

Inferred:

```Plain
count: number

```

### ✔ Boolean literal

```TypeScript
let flag = true;

```

Inferred:

```Plain
flag: boolean

```

---

## 🔧 Preventing Widening

Use `const`:

```TypeScript
const dir = "left";
// type: "left"  (literal preserved)

```

Or use `as const`:

```TypeScript
let dir = "left" as const;
// type: "left"

```

Or explicitly type it:

```TypeScript
let dir: "left" | "right" = "left";

```

---

# ✅ **2. Narrowing**

**Narrowing** is when TypeScript concludes a variable is a **more specific subtype** based on conditions or checks.

### ✔ Example (control flow narrowing)

```TypeScript
function printLength(x: string | null) {
  if (x !== null) {
    // here TypeScript knows x is string
    console.log(x.length);
  }
}

```

Inside the `if`, TypeScript **narrows**:

```Plain
x: string

```

Outside the `if`, it's still:

```Plain
x: string | null

```

---

## 🔍 Common Narrowing Techniques

### 1. **Type guards**

```TypeScript
if (typeof value === "string") {
  // narrowed to string
}

```

### 2. **Null checks**

```TypeScript
if (value != null) {
  // narrowed to non-null type
}

```

### 3. **In-operator**

```TypeScript
if ("id" in obj) {
  // obj narrowed to type that has 'id'
}

```

### 4. **Instance checks**

```TypeScript
if (x instanceof Date) {
  // x is narrowed to Date
}

```

---

# 🆚 **Widening vs. Narrowing Summary Table**

|Concept|Meaning|Example|
|---|---|---|
|**Widening**|Type becomes _more general_|`"left"` → `string`|
|**Narrowing**|Type becomes _more specific_|`string|
|When it happens|On variable initialization, mutable vars|Inside condition checks, guards|
|Prevent with|`const`, `as const`, explicit types|—|

---

# 🚀 **Real-World Example**

```TypeScript
type Direction = "left" | "right";

function move(dir: Direction | null) {
  if (dir === null) {
    console.log("No direction given.");
    return;
  }

  // TypeScript NARROWS:
  // dir: "left" | "right"
  console.log("Moving:", dir);
}

let d = "left";
// inferred as string (WIDENING)

move(d);
// ❌ ERROR: string not assignable to "left" | "right"

// fix:
let d2: Direction = "left";
move(d2); // OK

```

Here you see both:

- **Widening** causes `"left"` → `string`
- **Narrowing** reduces union types during checks