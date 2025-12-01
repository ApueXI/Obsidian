---
Created: 2025-11-30T15:03
tags:
  - Generics
---
# **Generic Functions in TypeScript**

Generics allow you to **write functions that work with multiple types** while maintaining **type safety**.

- Useful for **reusable, type-safe code**.
- Denoted with **angle brackets** `**<T>**` for type parameters.

---

## ✅ **1. Basic Generic Function**

```TypeScript
function identity<T>(arg: T): T {
  return arg;
}

console.log(identity<number>(42));   // 42
console.log(identity<string>("Hi")); // Hi

```

- `<T>` is a **type parameter**.
- `T` can be **any type**, determined when calling the function.
- Ensures **input and output types match**.

---

## ✅ **2. Type Inference in Generics**

```TypeScript
function identity<T>(arg: T): T {
  return arg;
}

const num = identity(123);     // TypeScript infers T = number
const str = identity("Hello"); // T = string

```

- TypeScript **automatically infers the type** in most cases.
- You only need to explicitly specify the type when necessary.

---

## ✅ **3. Generic Function With Array**

```TypeScript
function firstElement<T>(arr: T[]): T | undefined {
  return arr[0];
}

const nums = [1, 2, 3];
const firstNum = firstElement(nums); // Type inferred as number

const strs = ["a", "b", "c"];
const firstStr = firstElement(strs); // Type inferred as string

```

- Works with **arrays of any type**.
- Maintains type safety: `firstNum` is number, `firstStr` is string.

---

## ✅ **4. Generic Constraints**

```TypeScript
interface Lengthwise {
  length: number;
}

function logLength<T extends Lengthwise>(arg: T): T {
  console.log(arg.length);
  return arg;
}

logLength("Hello");   // 5
logLength([1, 2, 3]); // 3
// logLength(123);    ❌ Error: number does not have .length

```

- `T extends Lengthwise` → restricts `T` to types with a `.length` property.
- Ensures **type safety while being flexible**.

---

## ✅ **5. Multiple Type Parameters**

```TypeScript
function merge<T, U>(obj1: T, obj2: U): T & U {
  return { ...obj1, ...obj2 };
}

const merged = merge({ name: "Alice" }, { age: 25 });
console.log(merged.name); // Alice
console.log(merged.age);  // 25

```

- Functions can take **multiple generic types**.
- Return type can **combine multiple types** (`T & U`).

---

## 🔹 **6. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Generic function|`function fn<T>(arg: T): T`|`identity<T>(arg)`|Type-safe reusable function|
|Type inference|`fn(arg)`|`identity(123)`|TS automatically infers type|
|Array generics|`function first<T>(arr: T[]): T`|`firstElement(nums)`|Works with arrays of any type|
|Constraints|`T extends Interface`|`logLength<T extends Lengthwise>`|Restrict generics to certain types|
|Multiple generics|`function merge<T,U>(a:T,b:U)`|`merge(obj1,obj2)`|Combine multiple types safely|

---

**Rule of Thumb**:

- Use **generic functions** to **write flexible, reusable, type-safe code**.
- Use **constraints** to limit acceptable types when needed.
- Multiple type parameters allow **combining or transforming types safely**