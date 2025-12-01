---
Created: 2025-11-30T14:55
tags:
  - Classes
---
# **Readonly Class Fields in TypeScript**

Readonly class fields are properties that **cannot be changed after initialization**.

- Useful for **constants, IDs, or values that should never change** once the object is created.

---

## ✅ **1. Basic Syntax**

```TypeScript
class Person {
  readonly name: string;
  age: number;

  constructor(name: string, age: number) {
    this.name = name; // initialization allowed
    this.age = age;
  }
}

const alice = new Person("Alice", 25);
console.log(alice.name); // "Alice"
alice.age = 26;           // ✅ OK
// alice.name = "Bob";    // ❌ Error: Cannot assign to 'name' because it is a read-only property

```

- `readonly` ensures the property **cannot be reassigned after initialization**.

---

## 🔹 **2. Readonly With Parameter Properties**

```TypeScript
class Employee {
  constructor(public readonly id: number, public name: string) {}
}

const emp = new Employee(1, "Bob");
console.log(emp.id);   // 1
// emp.id = 2;          // ❌ Error: readonly
emp.name = "Alice";    // ✅ OK

```

- You can declare **readonly properties directly in the constructor parameters**.
- Saves lines by combining **declaration and initialization**.

---

## 🔹 **3. Readonly With Optional Properties**

```TypeScript
class Config {
  readonly apiKey?: string;

  constructor(apiKey?: string) {
    this.apiKey = apiKey;
  }
}

const cfg = new Config("12345");
// cfg.apiKey = "67890"; ❌ Error

```

- Optional readonly properties can be **undefined initially**, but once set, they **cannot be changed**.

---

## 🔹 **4. Readonly With Arrays**

```TypeScript
class DataStore {
  readonly items: readonly string[];

  constructor(items: string[]) {
    this.items = items;
  }
}

const store = new DataStore(["a", "b"]);
// store.items.push("c"); ❌ Error: 'push' does not exist on type 'readonly string[]'

```

- `readonly` arrays cannot be **mutated**.
- Use `readonly` to protect both **reference and content**.

---

## 🔹 **5. Readonly vs Private**

|Modifier|Can change inside class?|Can change outside class?|Notes|
|---|---|---|---|
|`readonly`|✅ Only during initialization|❌ After initialization|Can be public or private|
|`private`|✅ Anywhere in class|❌ Outside class|Can be changed anytime inside the class|

- `readonly` protects **from reassignment**, not from modification inside methods (unless `private readonly`).

---

## 📋 **Readonly Class Fields Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Basic readonly|`readonly name: string`|Assigned in constructor|Cannot reassign afterward|
|Constructor parameter|`constructor(public readonly id: number)`|Directly declares + initializes|Concise syntax|
|Optional readonly|`readonly prop?: string`|Can be undefined|Once set, cannot change|
|Readonly array|`readonly items: readonly string[]`|Immutable array|Prevents push/pop/splice|
|Difference from private|`readonly` vs `private`|`readonly` restricts reassignment|`private` restricts access|

---

**Rule of Thumb**:

- Use `**readonly**` for **immutable class properties**.
- Combine with **constructor parameter properties** for concise and safe code.
- Use **readonly arrays** to protect collections from mutation.