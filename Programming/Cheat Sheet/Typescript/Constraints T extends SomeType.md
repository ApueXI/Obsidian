---
Created: 2025-11-30T15:05
tags:
  - Generics
---
# **Generic Constraints in TypeScript**

Generic constraints allow you to **restrict the types that can be used as generic parameters**.

- Ensures **type safety** while keeping flexibility.
- Denoted with `<T extends SomeType>`.

---

## ✅ **1. Basic Constraint With Interface**

```TypeScript
interface Lengthwise {
  length: number;
}

function logLength<T extends Lengthwise>(arg: T): T {
  console.log(arg.length);
  return arg;
}

logLength("Hello");       // 5
logLength([1, 2, 3]);    // 3
// logLength(123);        ❌ Error: number has no .length

```

- `T extends Lengthwise` → `T` **must have a** `**.length**` **property**.
- Prevents using **incompatible types**.

---

## ✅ **2. Generic Constraint With Classes**

```TypeScript
class Person {
  constructor(public name: string) {}
}

function greet<T extends Person>(person: T) {
  console.log(`Hello, ${person.name}`);
}

greet(new Person("Alice")); // Hello, Alice
// greet({ age: 25 });      ❌ Error: missing name property

```

- Ensures **only compatible objects** are used with the generic function.

---

## ✅ **3. Using** `**keyof**` **With Generic Constraints**

```TypeScript
function getProperty<T, K extends keyof T>(obj: T, key: K) {
  return obj[key];
}

const user = { id: 1, name: "Alice" };

console.log(getProperty(user, "name")); // Alice
// console.log(getProperty(user, "age")); ❌ Error: 'age' not in 'user'

```

- `K extends keyof T` → restricts `key` to **valid keys of object T**.
- Prevents **accessing undefined properties**.

---

## ✅ **4. Multiple Constraints**

```TypeScript
interface Serializable {
  serialize(): string;
}

interface Loggable {
  log(): void;
}

function processItem<T extends Serializable & Loggable>(item: T) {
  console.log(item.serialize());
  item.log();
}

```

- `T extends Serializable & Loggable` → **T must satisfy multiple constraints**.
- Supports **intersection types** in generics.

---

## ✅ **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Single constraint|`T extends Interface`|`logLength<T extends Lengthwise>`|Restrict generic to compatible type|
|Class constraint|`T extends ClassName`|`greet<T extends Person>`|Only instances of class or subclasses allowed|
|keyof constraint|`K extends keyof T`|`getProperty<T,K extends keyof T>`|Restrict keys to object’s keys|
|Multiple constraints|`T extends A & B`|`processItem<T extends Serializable & Loggable>`|Intersection of types/interfaces|
|Type safety|N/A|`logLength(123)` ❌|Prevents incompatible types at compile time|

---

**Rule of Thumb**:

- Use `<T extends SomeType>` to **limit acceptable types** for generics.
- Ensures **compile-time safety** while keeping code reusable.
- Combine with `**keyof**` **or intersection types** for **more precise constraints**.