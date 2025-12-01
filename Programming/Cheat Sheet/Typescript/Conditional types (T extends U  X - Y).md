---
Created: 2025-11-30T15:07
tags:
  - Advance-Tpes
---
# **Conditional Types in TypeScript**

Conditional types allow you to **select a type based on a condition**.

- Syntax: `T extends U ? X : Y`
- Works at **compile-time**, not runtime.
- Useful for **type transformations and advanced type logic**.

---

## ✅ **1. Basic Conditional Type**

```TypeScript
type CheckString<T> = T extends string ? "Yes" : "No";

type A = CheckString<string>; // "Yes"
type B = CheckString<number>; // "No"

```

- `T extends string` → if true, type is `"Yes"`, else `"No"`.

---

## ✅ **2. Conditional Type With Generics**

```TypeScript
function process<T>(value: T): T extends string ? string : number {
  if (typeof value === "string") {
    return value.toUpperCase() as any;
  }
  return (value as unknown as number) * 2 as any;
}

const strResult = process("hello"); // inferred as string
const numResult = process(5);       // inferred as number

```

- Conditional types can **change the return type** based on input type.

---

## ✅ **3. Using** `**extends**` **With** `**infer**`

```TypeScript
type ReturnType<T> = T extends (...args: any[]) => infer R ? R : never;

type Fn = (x: number) => string;
type Result = ReturnType<Fn>; // string

```

- `infer R` allows **extracting types** from other types.
- Extremely useful for **utility types like** `**ReturnType**`**,** `**Parameters**`.

---

## ✅ **4. Nested Conditional Types**

```TypeScript
type TypeCheck<T> =
  T extends string ? "String" :
  T extends number ? "Number" :
  "Other";

type A = TypeCheck<string>; // "String"
type B = TypeCheck<number>; // "Number"
type C = TypeCheck<boolean>; // "Other"

```

- Conditional types can be **nested** for more complex logic.

---

## ✅ **5. Distributive Conditional Types**

```TypeScript
type ToArray<T> = T extends any ? T[] : never;

type Result = ToArray<string | number>; // string[] | number[]

```

- Conditional types **distribute over unions** automatically.
- Useful for **transforming union types element-wise**.

---

## 🔹 **6. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Basic conditional|`T extends U ? X : Y`|`CheckString<T>`|Select type based on condition|
|Conditional in function|`T extends string ? string : number`|`process<T>(value: T)`|Return type depends on generic|
|`infer` keyword|`T extends (...args: any[]) => infer R ? R : never`|`ReturnType<Fn>`|Extract type from function or structure|
|Nested conditional|`T extends A ? X : T extends B ? Y : Z`|`TypeCheck<T>`|Handle multiple type cases|
|Distributive conditional|`T extends any ? T[] : never`|`ToArray<string|number>`|

---

**Rule of Thumb**:

- Use **conditional types** for **type-level logic and transformations**.
- Combine with `**infer**` for extracting types.
- Use nested or distributive conditionals for **complex type scenarios**.