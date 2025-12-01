---
Created: 2025-11-30T15:10
---
# **Exhaustiveness Checking in TypeScript**

Exhaustiveness checking ensures that **all possible cases of a union type are handled**.

- Commonly used with **discriminated unions**.
- Helps prevent **runtime errors** due to unhandled cases.
- Achieved using the `never` type.

---

## ✅ **1. Basic Example With** `**switch**`

```TypeScript
type Shape =
  | { kind: "circle"; radius: number }
  | { kind: "square"; size: number };

function area(shape: Shape) {
  switch (shape.kind) {
    case "circle":
      return Math.PI * shape.radius ** 2;
    case "square":
      return shape.size ** 2;
  }
}

```

- This works, but if a new shape is added, TypeScript won’t warn **unless we enforce exhaustiveness**.

---

## ✅ **2. Enforcing Exhaustiveness With** `**never**`

```TypeScript
type Shape =
  | { kind: "circle"; radius: number }
  | { kind: "square"; size: number };

function area(shape: Shape) {
  switch (shape.kind) {
    case "circle":
      return Math.PI * shape.radius ** 2;
    case "square":
      return shape.size ** 2;
    default:
      const _exhaustiveCheck: never = shape;
      return _exhaustiveCheck;
  }
}

```

- `_exhaustiveCheck: never` will **cause a compile-time error** if a case is not handled.
- Ensures **all union members are covered**.

---

## ✅ **3. Using** `**if**` **Statements**

```TypeScript
type Status = "success" | "error" | "loading";

function handleStatus(status: Status) {
  if (status === "success") {
    console.log("Success!");
  } else if (status === "error") {
    console.log("Error!");
  } else {
    const _exhaustive: never = status;
    // ❌ Compile-time error if a new status is added
  }
}

```

- Works similarly to `switch` statements.
- Helps catch **unhandled union members** at compile-time.

---

## ✅ **4. Why Exhaustiveness Checking Matters**

- Prevents **runtime errors** due to missing cases.
- Helps **maintainability**: if new types are added, the compiler forces you to update logic.
- Works best with **discriminated unions** and **type guards**.

---

## ✅ **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Enforce `switch`|`default: const _exhaustive: never = var`|See area(shape) example|Ensures all union members handled|
|Enforce `if`|`else { const _exhaustive: never = var }`|See handleStatus|Works with boolean chains|
|Compile-time safety|`_exhaustive: never`|❌ Error if case missing|Catches missing types at compile time|
|Works with|Discriminated unions|`Shape`, `Status`|TypeScript infers unhandled cases|

---

**Rule of Thumb**:

- Always include **a default branch with** `**never**` when working with **union types or discriminated unions**.
- Forces **compile-time safety** and avoids **runtime bugs**.
- Very useful in **switch statements, event handlers, and status management**.