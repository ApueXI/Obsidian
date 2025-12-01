---
Created: 2025-11-30T14:44
tags:
  - Type-System
---
# **Extending Interfaces in TypeScript**

In TypeScript, **interfaces can inherit from other interfaces**.

- This allows you to **reuse properties** from one interface in another.
- Helps organize complex object shapes and avoid repetition.

Syntax:

```TypeScript
interface Child extends Parent { ... }

```

---

## ✅ **Basic Example**

```TypeScript
interface Animal {
  species: string;
}

interface Pet extends Animal {
  name: string;
}

const dog: Pet = {
  species: "Dog",
  name: "Buddy"
};

```

- `Pet` inherits the `species` property from `Animal`.
- Any object of type `Pet` must have both `species` and `name`.

---

## 🔹 **Extending Multiple Interfaces**

```TypeScript
interface A { a: number }
interface B { b: number }

interface C extends A, B {
  c: number
}

const obj: C = { a: 1, b: 2, c: 3 };

```

- TypeScript supports **multiple inheritance** using `extends`.
- Object must satisfy **all inherited properties**.

---

## 🔹 **Extending With Methods**

```TypeScript
interface Animal {
  eat(): void;
}

interface Pet extends Animal {
  play(): void;
}

const cat: Pet = {
  eat() { console.log("Eating"); },
  play() { console.log("Playing"); }
};

```

- Both methods must exist in objects implementing `Pet`.

---

## 🔹 **Combining Optional & Readonly Properties**

```TypeScript
interface Animal {
  readonly species: string;
  age?: number;
}

interface Pet extends Animal {
  name: string;
}

const parrot: Pet = {
  species: "Parrot",
  name: "Polly",
  age: 2
};

parrot.species = "Macaw"; // ❌ Error: readonly

```

---

## 🔹 **Extending Type Aliases vs Interfaces**

|Feature|Interface|Type Alias|
|---|---|---|
|Extending|✅ `extends`|❌ cannot extend directly (must use intersections)|
|Multiple inheritance|✅ Yes|✅ With `&` (intersection)|
|Mergeable|✅ Yes|❌ No|

---

## ✅ **Real-World Example**

```TypeScript
interface ResponseBase {
  status: number;
  error?: string;
}

interface UserResponse extends ResponseBase {
  data: {
    id: number;
    name: string;
  }
}

const response: UserResponse = {
  status: 200,
  data: { id: 1, name: "Neo" }
};

```

- `UserResponse` automatically gets `status` and optional `error` from `ResponseBase`.
- Avoids repeating common response fields across multiple API response types.