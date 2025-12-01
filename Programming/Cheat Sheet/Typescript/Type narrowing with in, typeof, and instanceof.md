---
Created: 2025-11-30T14:51
tags:
  - Object-Types
---
# **Type Narrowing in TypeScript**

Type narrowing allows TypeScript to **refine a variable’s type at runtime** based on conditions.

- This is essential when working with **union types** or **unknown values**.
- Common tools: `typeof`, `instanceof`, `in`.

---

## ✅ **1.** `**typeof**` **Type Narrowing**

- Use `typeof` for **primitive types**: `string`, `number`, `boolean`, `symbol`, `undefined`.

```TypeScript
function formatValue(value: string | number) {
  if (typeof value === "string") {
    return value.toUpperCase(); // narrowed to string
  } else {
    return value.toFixed(2);    // narrowed to number
  }
}

console.log(formatValue("hello")); // "HELLO"
console.log(formatValue(3.1415));  // "3.14"

```

- TypeScript automatically **narrows the type inside the conditional block**.

---

## 🔹 **2.** `**instanceof**` **Type Narrowing**

- Use `instanceof` for **class or object types**.

```TypeScript
class Dog { bark() { console.log("Woof"); } }
class Cat { meow() { console.log("Meow"); } }

function speak(animal: Dog | Cat) {
  if (animal instanceof Dog) {
    animal.bark(); // narrowed to Dog
  } else {
    animal.meow(); // narrowed to Cat
  }
}

speak(new Dog()); // "Woof"
speak(new Cat()); // "Meow"

```

- Works for **custom classes and built-in objects** like `Date`, `Error`, `Array`.

---

## 🔹 **3.** `**in**` **Type Narrowing**

- Use `in` to check if a **property exists** in an object.

```TypeScript
interface Square { size: number; }
interface Rectangle { width: number; height: number; }

function area(shape: Square | Rectangle) {
  if ("size" in shape) {
    return shape.size * shape.size; // narrowed to Square
  } else {
    return shape.width * shape.height; // narrowed to Rectangle
  }
}

console.log(area({ size: 5 }));            // 25
console.log(area({ width: 4, height: 3 })); // 12

```

- Checks the **existence of a property** to determine the type.

---

## 🔹 **4. Combining Narrowing Methods**

```TypeScript
function handle(input: string | number | Date) {
  if (typeof input === "string") {
    console.log(input.toUpperCase());
  } else if (typeof input === "number") {
    console.log(input.toFixed(2));
  } else if (input instanceof Date) {
    console.log(input.toISOString());
  }
}

handle("hello");           // "HELLO"
handle(3.14);              // "3.14"
handle(new Date("2025-01-01")); // "2025-01-01T00:00:00.000Z"

```

- Type narrowing can be **chained** to handle multiple types safely.

---

## 🔹 **5. Type Guards With Custom Functions**

You can also create **custom type guard functions**:

```TypeScript
interface Bird { fly(): void; }
interface Fish { swim(): void; }

function isBird(animal: Bird | Fish): animal is Bird {
  return (animal as Bird).fly !== undefined;
}

function move(animal: Bird | Fish) {
  if (isBird(animal)) {
    animal.fly(); // narrowed to Bird
  } else {
    animal.swim(); // narrowed to Fish
  }
}

```

- `animal is Bird` tells TypeScript how to **narrow the type** inside the conditional.

---

## 📋 **Type Narrowing Summary Table**

|Method|Usage|Example|Notes|
|---|---|---|---|
|`typeof`|Primitive types (`string`, `number`, `boolean`)|`if (typeof x === "string")`|Narrow primitive union types|
|`instanceof`|Classes & objects|`if (obj instanceof Date)`|Narrow class instances|
|`in`|Check for property existence|`if ("size" in shape)`|Narrow object types in unions|
|Custom type guard|`function isBird(a): a is Bird`|Used in `if (isBird(a))`|Flexible, reusable narrowing|

---

**Rule of Thumb**:

- Use `**typeof**` for primitives.
- Use `**instanceof**` for objects or classes.
- Use `**in**` for checking **properties in union objects**.
- For complex logic, define **custom type guards** for clarity and reuse.