---
Created: 2025-11-30T15:09
tags:
  - Advance-Tpes
---
# **Discriminated Unions in TypeScript**

Discriminated unions (also called **tagged unions**) let you create a **union of types with a common literal property** that identifies the variant.

- Useful for **type-safe conditional logic**.
- Combines **unions**, **literal types**, and **type narrowing**.

---

## ✅ **1. Basic Discriminated Union**

```TypeScript
interface Square {
  kind: "square";
  size: number;
}

interface Circle {
  kind: "circle";
  radius: number;
}

type Shape = Square | Circle;

function area(shape: Shape) {
  if (shape.kind === "square") {
    return shape.size ** 2;
  } else {
    return Math.PI * shape.radius ** 2;
  }
}

const s: Square = { kind: "square", size: 5 };
console.log(area(s)); // 25

```

- `kind` is the **discriminant property**.
- TypeScript uses it to **narrow the type** inside conditional blocks.

---

## ✅ **2. Using** `**switch**` **With Discriminated Unions**

```TypeScript
function area2(shape: Shape) {
  switch (shape.kind) {
    case "square":
      return shape.size ** 2;
    case "circle":
      return Math.PI * shape.radius ** 2;
  }
}

```

- `switch` on the discriminant ensures **all cases are handled**.
- TypeScript provides **exhaustiveness checking** when used with `never`.

---

## ✅ **3. Exhaustive Checking With** `**never**`

```TypeScript
function area3(shape: Shape) {
  switch (shape.kind) {
    case "square":
      return shape.size ** 2;
    case "circle":
      return Math.PI * shape.radius ** 2;
    default:
      const _exhaustive: never = shape; // Error if a new shape is added
      return _exhaustive;
  }
}

```

- Helps catch **unhandled union members** at compile time.

---

## ✅ **4. Discriminated Unions With More Properties**

```TypeScript
interface Triangle {
  kind: "triangle";
  base: number;
  height: number;
}

type AllShapes = Square | Circle | Triangle;

function perimeter(shape: AllShapes) {
  if (shape.kind === "triangle") {
    return shape.base + shape.height; // Example: simplified
  }
}

```

- Can extend with **more types** while maintaining **type safety**.

---

## ✅ **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Discriminant property|`kind: "type"`|`Square.kind`|Must be a literal type|
|Union type|`type Shape = Square|Circle`||
|Type narrowing|`if(shape.kind === "square")`|shape is inferred as Square|Safe access to properties|
|Exhaustive checking|`const _exhaustive: never = shape`|Catch missing cases|Useful in `switch`|
|Extendable|Add more interfaces|`Triangle` added to union|Safe scalability|

---

**Rule of Thumb**:

- Use **discriminated unions** for **type-safe polymorphism**.
- Always have a **literal property as a tag**.
- Combine with **switch or if statements** for **automatic type narrowing**.
- Use `never` in `default` for **exhaustiveness checking**.