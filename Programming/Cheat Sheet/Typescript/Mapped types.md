---
Created: 2025-11-30T15:06
tags:
  - Advance-Tpes
---
# **Built-in Generics in TypeScript**

TypeScript includes **several built-in generic types** that allow **type-safe handling of collections, asynchronous operations, and more**.

- Common examples: **Promise<T>**, **Map<K, V>**, **Set<T>**.
- Provide **compile-time type safety** without losing flexibility.

---

## ✅ **1.** `**Promise<T>**`

`Promise<T>` represents a **value that may be available now, later, or never**.

- `T` is the **type of the resolved value**.

```TypeScript
const fetchNumber = (): Promise<number> => {
  return new Promise((resolve) => {
    setTimeout(() => resolve(42), 1000);
  });
};

fetchNumber().then((value) => {
  console.log(value); // 42
});

```

- Ensures **TypeScript knows the resolved type** (`number` in this case).

---

## ✅ **2.** `**Array<T>**` **/** `**T[]**`

Arrays can use generics to **enforce element type**.

```TypeScript
const numbers: Array<number> = [1, 2, 3];
const strings: string[] = ["a", "b", "c"];

// numbers.push("hello"); ❌ Error: string not allowed

```

- Guarantees **all elements in the array are of type T**.

---

## ✅ **3.** `**Map<K, V>**`

`Map<K, V>` stores **key-value pairs** with type safety.

```TypeScript
const map: Map<string, number> = new Map();

map.set("one", 1);
map.set("two", 2);

console.log(map.get("one")); // 1
// map.set(3, "three"); ❌ Error: key must be string, value must be number

```

- `K` → type of keys
- `V` → type of values

---

## ✅ **4.** `**Set<T>**`

`Set<T>` stores **unique values** of a certain type.

```TypeScript
const set: Set<number> = new Set();

set.add(1);
set.add(2);
set.add(2); // ignored, duplicate

console.log(set.has(2)); // true
// set.add("hello"); ❌ Error: string not allowed

```

- `T` → type of stored values
- Ensures **uniqueness and type safety**

---

## ✅ **5. Other Common Built-in Generics**

|Generic|Purpose|Example|
|---|---|---|
|`ReadonlyArray<T>`|Array that cannot be modified|`const arr: ReadonlyArray<number> = [1,2,3]`|
|`Record<K, V>`|Object with keys K and values V|`const obj: Record<string, number> = {a:1}`|
|`Partial<T>`|All properties of T optional|`const p: Partial<{a:number, b:string}> = {a:1}`|
|`Required<T>`|All properties of T required|`const r: Required<{a?:number}> = {a:1}`|
|`ReturnType<T>`|Return type of function T|`type R = ReturnType<() => string>`|

---

## 🔹 **6. Summary Table**

|Built-in Generic|Type Parameters|Notes|Example|
|---|---|---|---|
|`Promise<T>`|`T`|Type of resolved value|`Promise<number>`|
|`Array<T>`|`T`|Array element type|`Array<string>`|
|`Set<T>`|`T`|Unique values|`Set<number>`|
|`Map<K,V>`|`K,V`|Key-value pairs|`Map<string,number>`|
|`ReadonlyArray<T>`|`T`|Immutable array|`ReadonlyArray<string>`|
|`Record<K,V>`|`K,V`|Object with typed keys/values|`Record<string,boolean>`|
|`Partial<T>`|`T`|All properties optional|`Partial<User>`|
|`Required<T>`|`T`|All properties required|`Required<User>`|

---

**Rule of Thumb**:

- Use **Promise<T>** for async values.
- Use **Map<K,V>** and **Set<T>** for collections with type safety.
- Combine with other **utility types** to manipulate and enforce type safety in complex structures.