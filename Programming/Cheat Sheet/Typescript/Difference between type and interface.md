---
Created: 2025-11-30T14:44
tags:
  - Type-System
---
# **Type vs Interface in TypeScript**

Both `**type**` and `**interface**` can describe object shapes, unions, intersections, and more.

The difference lies in **capabilities, flexibility, and usage**.

---

## ✅ **1. Basic Syntax Comparison**

### **Interface**

```TypeScript
interface Person {
  name: string;
  age: number;
}

```

### **Type Alias**

```TypeScript
type Person = {
  name: string;
  age: number;
};

```

- Both define an object with the same properties.
- Both can be used to type variables, function parameters, and return values.

---

## ✅ **2. Extending / Combining**

|Feature|Interface|Type Alias|
|---|---|---|
|Extending|✅ `interface Child extends Parent`|❌ Cannot extend directly (use intersections `&`)|
|Merging|✅ Multiple interfaces with same name merge|❌ Type aliases cannot merge|

### Example: Interface Extending

```TypeScript
interface A { a: number }
interface B extends A { b: number }

const obj: B = { a: 1, b: 2 };

```

### Example: Type Intersection

```TypeScript
type A = { a: number };
type B = A & { b: number };

const obj: B = { a: 1, b: 2 };

```

---

## ✅ **3. Unions and Intersections**

- **Type aliases** can define **unions** and **intersections**:

```TypeScript
type ID = number | string;
type Person = { name: string } & { age: number };

```

- **Interfaces** cannot directly define union types.

---

## ✅ **4. Implements / Classes**

- Classes can **implement interfaces** and **type aliases** (for object types), but interfaces are more common.

```TypeScript
interface Person {
  name: string;
}

class User implements Person {
  name: string;
  constructor(name: string) {
    this.name = name;
  }
}

```

---

## ✅ **5. Readability & Semantic Meaning**

- Use `**type**` for:
    - Primitives, unions, intersections
    - Aliases for complex or reusable types
- Use `**interface**` for:
    - Object shapes
    - Extensible APIs
    - Classes

---

## ✅ **6. Key Differences Table**

|Feature|Interface|Type Alias|
|---|---|---|
|Object shape|✅ Yes|✅ Yes|
|Extending other types|✅ Yes (`extends`)|❌ No direct `extends` (use `&`)|
|Merging declarations|✅ Yes|❌ No|
|Union types|❌ No|✅ Yes|
|Intersection types|❌ No|✅ Yes|
|Readability for objects|✅ Very good|✅ Good|

---

## ⚡ **Rule of Thumb**

- **Interface** → Best for **objects and classes**, especially if it may be extended or merged.
- **Type alias** → Best for **unions, intersections, tuples, primitives**, or when you need flexibility.