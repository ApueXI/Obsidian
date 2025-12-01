---
Created: 2025-11-30T15:05
tags:
  - Generics
---
# **Generic Interfaces in TypeScript**

Generic interfaces allow you to **define flexible type-safe structures** that work with **multiple types**.

- Similar to generic functions, but applied to **object shapes**.
- Useful for **reusable and strongly typed APIs**.

---

## ✅ **1. Basic Generic Interface**

```TypeScript
interface Box<T> {
  value: T;
}

const numberBox: Box<number> = { value: 123 };
const stringBox: Box<string> = { value: "Hello" };

console.log(numberBox.value); // 123
console.log(stringBox.value); // Hello

```

- `<T>` is a **type parameter**.
- Ensures **value type matches the generic type**.

---

## ✅ **2. Generic Interface With Methods**

```TypeScript
interface Pair<K, V> {
  key: K;
  value: V;
  display(): void;
}

const pair: Pair<string, number> = {
  key: "Age",
  value: 25,
  display() {
    console.log(`${this.key}: ${this.value}`);
  }
};

pair.display(); // Age: 25

```

- Interfaces can have **generic types in properties and methods**.
- Provides **strong typing for method implementation**.

---

## ✅ **3. Using Generic Interface With Classes**

```TypeScript
interface Repository<T> {
  add(item: T): void;
  getAll(): T[];
}

class MemoryRepository<T> implements Repository<T> {
  private items: T[] = [];

  add(item: T): void {
    this.items.push(item);
  }

  getAll(): T[] {
    return this.items;
  }
}

const userRepo = new MemoryRepository<{ id: number; name: string }>();
userRepo.add({ id: 1, name: "Alice" });
console.log(userRepo.getAll());

```

- Classes can **implement generic interfaces**.
- The **type parameter** can be **specified at instantiation**.

---

## ✅ **4. Optional & Readonly in Generic Interfaces**

```TypeScript
interface Config<T> {
  readonly name: string;
  options?: T;
}

const config: Config<{ debug: boolean }> = {
  name: "AppConfig",
  options: { debug: true }
};

// config.name = "New"; ❌ Error: readonly

```

- Generic interfaces can combine with **optional** and **readonly** properties.

---

## ✅ **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Basic generic interface|`interface Box<T> { value: T }`|`const numBox: Box<number>`|Strongly typed structure|
|Multiple generics|`interface Pair<K, V>`|`Pair<string, number>`|Different types for properties|
|Methods in generic interface|`display(): void`|`display() { ... }`|Type-safe method implementation|
|Class implements generic interface|`class MyRepo<T> implements Repository<T>`|`new MemoryRepository<User>()`|Generic type specified at instantiation|
|Optional / Readonly|`options?: T; readonly name: string`|`Config<T>`|Adds flexibility and immutability|

---

**Rule of Thumb**:

- Use **generic interfaces** to define **flexible, reusable, type-safe object shapes**.
- Combine with **classes** for **generic data structures or APIs**.
- Can use **multiple type parameters**, **readonly**, and **optional properties** for additional control.