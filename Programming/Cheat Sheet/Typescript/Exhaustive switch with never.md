---
Created: 2025-12-01T11:46
tags:
  - Type-Safety-Technique
---
# 🔵 TypeScript — **Exhaustive Switch with** `**never**`

---

# ✅ 1. Full Explanation

## **What is an Exhaustive Switch?**

- An **exhaustive switch** ensures that **all possible values of a union type** are handled in a `switch` statement.
- TypeScript’s `**never**` **type** is used to **catch unhandled cases at compile time**.
- Helps prevent **runtime bugs** when new union members are added.

---

## **Why Use** `**never**` **in Switch**

- Acts as a **compile-time safeguard**
- Forces developers to handle **all cases**
- Works well with **discriminated unions**

---

## **How It Works**

### 1. Define a Union Type

```TypeScript
type Direction = "up" | "down" | "left" | "right";

```

### 2. Use Switch with `never` for Exhaustiveness

```TypeScript
function move(direction: Direction) {
  switch (direction) {
    case "up":
      console.log("Moving up");
      break;
    case "down":
      console.log("Moving down");
      break;
    case "left":
      console.log("Moving left");
      break;
    case "right":
      console.log("Moving right");
      break;
    default:
      const _exhaustiveCheck: never = direction; // ❌ Compile-time error if any case is missing
      return _exhaustiveCheck;
  }
}

```

- If a new value is added to `Direction`, TypeScript **will error** because the `default` case is no longer `never`.

---

## **Gotchas / Pitfalls**

1. Only works with **union types** (string, number, or literal unions)
2. Useful with `**strict**` **mode enabled** for full safety
3. Avoid using `any` or `unknown` in union — breaks exhaustiveness check
4. The `never` assignment in the default ensures **compile-time checking**

---

# ✅ 2. Summary Table

|Concept|Example|Notes|
|---|---|---|
|Union Type|`type Direction = "up"|"down";`|
|Exhaustive Switch|`switch (d) { ... default: const _ex: never = d; }`|Compile-time safety|
|Purpose|Catch unhandled cases|Prevents runtime bugs|
|Works With|Literal unions|Strings, numbers, or discriminated unions|
|Requirement|`strict` mode recommended|Ensures TS enforces `never` assignment|

---

# ✅ 3. Real-World Example

### **Scenario 1: Direction Union**

```TypeScript
type Direction = "up" | "down" | "left" | "right";

function move(direction: Direction) {
  switch (direction) {
    case "up": console.log("Up"); break;
    case "down": console.log("Down"); break;
    case "left": console.log("Left"); break;
    case "right": console.log("Right"); break;
    default:
      const _exhaustiveCheck: never = direction; // ✅ Compile-time safety
      return _exhaustiveCheck;
  }
}

```

- Adding `"forward"` to `Direction` triggers a **compile-time error** until handled.

---

### **Scenario 2: Discriminated Union**

```TypeScript
type Shape =
  | { kind: "circle"; radius: number }
  | { kind: "square"; size: number }
  | { kind: "rectangle"; width: number; height: number };

function area(shape: Shape) {
  switch (shape.kind) {
    case "circle":
      return Math.PI * shape.radius ** 2;
    case "square":
      return shape.size ** 2;
    case "rectangle":
      return shape.width * shape.height;
    default:
      const _exhaustiveCheck: never = shape; // ✅ Compile-time safety
      return _exhaustiveCheck;
  }
}

```

- If a new shape type is added, TypeScript **forces you to handle it**.

---

# 🔥 Bonus Tips

1. Always combine with `**strict**` **and** `**noFallthroughCasesInSwitch**` for maximum safety
2. Works well in **large codebases** where new union members may be added over time
3. The `never` type is **purely compile-time**; no runtime overhead
4. Can be combined with **functions returning values** to enforce **complete return coverage**