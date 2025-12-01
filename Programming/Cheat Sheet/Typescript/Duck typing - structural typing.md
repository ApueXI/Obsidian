---
Created: 2025-12-01T11:47
tags:
  - Core-Typescript-Philosophy
---
# 🔵 TypeScript — **Duck Typing / Structural Typing**

---

# ✅ 1. Full Explanation

## **What is Duck Typing / Structural Typing?**

- TypeScript uses **structural typing**, which is also known as **duck typing**.
- Meaning: **a type is determined by its structure (shape), not its name**.
- Famous saying:
    
    > "If it walks like a duck and quacks like a duck, it’s a duck."
    
- In practice:
    
    If an object has the **required properties and methods**, TypeScript considers it compatible, regardless of explicit type names.
    

---

## **Why It Matters**

- Allows **flexible code reuse**
- Supports **interface compatibility without explicit inheritance**
- Reduces boilerplate by **not requiring nominal typing**

---

## **How It Works**

### 1. **Object Compatibility**

```TypeScript
interface Point { x: number; y: number; }

const p = { x: 10, y: 20, z: 30 }; // Extra property z
const pt: Point = p; // ✅ OK, compatible with Point

```

- Extra properties are **allowed** in structural typing when assigned to a variable of a compatible interface.

---

### 2. **Function Compatibility**

```TypeScript
type Fn = (x: number, y: number) => number;

const sum = (a: number, b: number) => a + b;
const f: Fn = sum; // ✅ OK, signature matches

```

- Functions are compatible if **parameter types and return type match structurally**

---

### 3. **Class Compatibility**

```TypeScript
class A { x = 1; y = 2; }
class B { x = 10; y = 20; z = 30; }

let a: A;
let b: B = new B();

a = b; // ✅ OK, B has all properties of A

```

- Type names **don’t matter**, only the shape of the object

---

### 4. **Interface Compatibility**

```TypeScript
interface Named { name: string }
interface Person { name: string; age: number }

const person: Person = { name: "Alice", age: 30 };
const named: Named = person; // ✅ OK, structure compatible

```

---

## **Gotchas / Pitfalls**

1. **Extra property checks** apply when assigning **object literals** directly

```TypeScript
const named: Named = { name: "Alice", age: 30 }; // ❌ Error: Object literal may only specify known properties

```

- Use a **variable** to bypass:

```TypeScript
const obj = { name: "Alice", age: 30 };
const named: Named = obj; // ✅ OK

```

1. **Structural typing may hide accidental matches**
    - Two objects may match structurally but **semantically differ**
2. Duck typing is **compile-time only** — runtime behavior is unchanged

---

# ✅ 2. Summary Table

|Concept|Description|Example|
|---|---|---|
|Duck Typing / Structural Typing|Type compatibility is based on **shape**, not name|`{ x: number, y: number }` is compatible with `interface Point { x: number; y: number }`|
|Object Compatibility|Extra properties allowed when assigned from variable|`const p = { x: 1, y: 2, z: 3 }; const pt: Point = p;` ✅ OK|
|Function Compatibility|Parameters and return type must match|`(a: number, b: number) => number`|
|Class Compatibility|Compatible if **all required members** exist|`a = b;` if `b` has all properties of `a`|
|Interface Compatibility|Compatible if **structure matches**|`const named: Named = person;` ✅ OK|

---

# ✅ 3. Real-World Examples

### **Example 1: Object Compatibility**

```TypeScript
interface Point { x: number; y: number; }
const point3D = { x: 1, y: 2, z: 3 };
const pt: Point = point3D; // ✅ OK

```

### **Example 2: Function Compatibility**

```TypeScript
type Callback = (a: number) => void;
const fn = (x: number, y: number) => console.log(x + y);
const cb: Callback = fn; // ✅ OK, extra parameters are ignored

```

### **Example 3: Class Compatibility**

```TypeScript
class Foo { x = 1; y = 2; }
class Bar { x = 10; y = 20; z = 30; }
let foo: Foo;
foo = new Bar(); // ✅ OK, Bar has all properties of Foo

```

### **Example 4: Interface Compatibility**

```TypeScript
interface Named { name: string }
interface Person { name: string; age: number }

const person: Person = { name: "Alice", age: 30 };
const named: Named = person; // ✅ OK

```

---

# 🔥 Bonus Tips

1. Use **structural typing** to simplify **API integration** and **data modeling**
2. Combine with **type guards** for safe runtime property access
3. Be mindful of **object literal extra property checks** when assigning directly