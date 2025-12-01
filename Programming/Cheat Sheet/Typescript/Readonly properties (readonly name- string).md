---
Created: 2025-11-30T14:50
tags:
  - Object-Types
---
# **Readonly Properties in TypeScript**

Readonly properties allow you to **make object properties immutable** after they are initialized.

- They **cannot be changed** once assigned.
- Useful for **ensuring data integrity** and preventing accidental mutation.

---

## ✅ **1. Basic Syntax**

```TypeScript
interface Person {
  readonly name: string;
  age: number;
}

const person: Person = { name: "Alice", age: 25 };

console.log(person.name); // Alice
person.age = 26;          // ✅ OK
// person.name = "Bob";    // ❌ Error: Cannot assign to 'name' because it is a read-only property

```

- `readonly name: string` → property cannot be reassigned.
- Non-readonly properties (like `age`) can still be updated.

---

## 🔹 **2. Readonly in Inline Object Types**

```TypeScript
function logUser(user: { readonly id: number; name: string }) {
  console.log(user.id, user.name);
}

const u = { id: 1, name: "Neo" };
logUser(u);
// u.id = 2; ❌ Error: readonly

```

- Works the same way in inline object types.

---

## 🔹 **3. Readonly Arrays**

- TypeScript also provides `ReadonlyArray<T>` for **immutable arrays**:

```TypeScript
const nums: ReadonlyArray<number> = [1, 2, 3];
// nums.push(4); ❌ Error: Property 'push' does not exist
// nums[0] = 10; ❌ Error: Index signature in type 'readonly number[]' only permits reading

```

- Prevents **mutation methods** (`push`, `pop`, `splice`, etc.) from being called.

---

## 🔹 **4. Readonly in Classes**

```TypeScript
class User {
  readonly id: number;
  name: string;

  constructor(id: number, name: string) {
    this.id = id;
    this.name = name;
  }
}

const user = new User(1, "Alice");
user.name = "Bob";   // ✅ OK
// user.id = 2;      // ❌ Error

```

- Readonly properties **must be assigned at declaration or in the constructor**.

---

## 🔹 **5. Readonly with Optional Properties**

```TypeScript
interface Config {
  readonly apiKey?: string;
}

const cfg: Config = {};
// cfg.apiKey = "123"; ❌ Error

```

- Optional properties can still be readonly.
- Once assigned, they **cannot be modified**.

---

## 📋 **Readonly Properties Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Object property|`readonly name: string`|`interface Person { readonly name: string }`|Cannot be reassigned|
|Inline object|`{ readonly id: number }`|Function param or variable|Works the same as interface|
|Arrays|`ReadonlyArray<T>`|`const arr: ReadonlyArray<number>`|Immutable array methods|
|Class property|`readonly id: number`|Assigned in constructor|Cannot change afterward|
|Optional readonly|`readonly prop?: string`|Can be undefined, but immutable if assigned|Useful for config objects|

---

**Rule of Thumb**:

- Use `**readonly**` to protect important data that should **not change** after initialization.
- Use `**ReadonlyArray**` for arrays that must remain immutable.