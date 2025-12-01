---
Created: 2025-11-30T14:43
tags:
  - Type-System
---
# **Interfaces in TypeScript**

An **interface** defines the **shape of an object** — what properties it has and their types.

- Think of it as a **contract**: “Any object of this type must have these properties and methods.”
- Interfaces are **extendable**, unlike type aliases for objects (which cannot merge).

---

## ✅ **Basic Interface**

```TypeScript
interface Person {
  name: string;
  age: number;
}

const user: Person = {
  name: "Alice",
  age: 25
};

```

- `Person` defines the shape
- `user` must satisfy that shape

---

## 🔹 **Optional Properties**

Use `?` to mark properties as optional:

```TypeScript
interface Person {
  name: string;
  age?: number;  // optional
}

const user: Person = {
  name: "Bob"  // ✅ age is optional
};

```

---

## 🔹 **Readonly Properties**

Use `readonly` to prevent modification:

```TypeScript
interface Person {
  readonly id: number;
  name: string;
}

const user: Person = { id: 1, name: "Alice" };
user.id = 2;  // ❌ Error

```

---

## 🔹 **Methods in Interfaces**

Interfaces can define **methods with types**:

```TypeScript
interface Person {
  name: string;
  greet(): void;
}

const user: Person = {
  name: "Neo",
  greet() {
    console.log(`Hello, ${this.name}`);
  }
};

```

---

## 🔹 **Extending Interfaces**

Interfaces can **inherit from other interfaces**:

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

- Multiple interfaces can also be extended:

```TypeScript
interface A { a: number }
interface B { b: number }
interface C extends A, B { c: number }

```

---

## 🔹 **Index Signatures**

If you want dynamic keys:

```TypeScript
interface StringMap {
  [key: string]: string;
}

const colors: StringMap = {
  primary: "red",
  secondary: "blue"
};

```

---

## 🔹 **Difference Between Interfaces and Type Aliases**

|Feature|Interface|Type Alias|
|---|---|---|
|Extensible / Mergeable|✅ Yes|❌ No|
|Object shape|✅ Yes|✅ Yes|
|Unions / Intersections|❌ No|✅ Yes|
|Readable for objects|✅ Yes|✅ Yes|

---

## ✅ **Real-World Example**

```TypeScript
interface ApiResponse {
  data: object;
  status: number;
  error?: string;
}

function handleResponse(res: ApiResponse) {
  console.log(res.status);
  if (res.error) console.error(res.error);
}

```

- `ApiResponse` ensures all responses have `data` and `status`
- Optional `error` handled safely