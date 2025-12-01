---
Created: 2025-11-30T14:42
tags:
  - Type-System
---
# **Type Aliases in TypeScript**

A **type alias** lets you create a **custom name** for any type — primitive, union, intersection, object, tuple, etc.

It’s a way to **make code more readable and reusable**.

---

## ✅ **Basic Syntax**

```TypeScript
type Age = number;

let myAge: Age = 25;  // equivalent to number

```

Here:

- `Age` is now an alias for `number`
- You can use `Age` anywhere a `number` would work

---

## 🔹 **Aliases with Objects**

```TypeScript
type Person = {
  name: string;
  age: number;
};

const user: Person = {
  name: "Alice",
  age: 30
};

```

Aliases make complex types reusable and easier to read.

---

## 🔹 **Aliases with Union Types**

```TypeScript
type Direction = "left" | "right" | "up" | "down";

let move: Direction;
move = "left";  // OK
move = "forward";  // ❌ Error

```

---

## 🔹 **Aliases with Intersections**

```TypeScript
type A = { name: string };
type B = { age: number };

type Person = A & B;

const p: Person = {
  name: "Bob",
  age: 25
};

```

---

## 🔹 **Aliases with Tuples**

```TypeScript
type Point = [number, number];

let start: Point = [0, 0];
let end: Point = [10, 5];

```

---

## ✅ **Why Use Type Aliases?**

- Make code **more readable**
- Give semantic meaning (`Age` instead of `number`)
- Reuse types across objects, functions, and modules
- Work with unions, intersections, tuples, and complex types

---

## ⚠️ Gotchas

- Type aliases **cannot be reopened** like interfaces (no merging)
- Prefer interfaces for **extensible object types**
- Type aliases work well with **unions, intersections, tuples, primitives**

---

## 📋 Summary Table

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Primitive alias|`type Age = number;`|`let myAge: Age = 25`|Simple renaming|
|Object alias|`type Person = {name:string; age:number}`|Reusable object type|Immutable, cannot merge|
|Union alias|`type Dir = "left"|"right"`|Restricts allowed strings|
|Intersection alias|`type P = A & B`|Combine multiple types|Must satisfy all|
|Tuple alias|`type Point = [number, number]`|Fixed-length array|Readable and reusable|