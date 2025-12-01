---
Created: 2025-11-30T14:51
tags:
  - Object-Types
---
# **Structural Typing in TypeScript**

Structural typing is one of TypeScript’s **core concepts**.

- TypeScript is **structurally typed**, not nominally typed.
- **Compatibility is determined by the shape of the object**, not its explicit type or name.
- If two objects have the **same structure**, TypeScript considers them **compatible**, even if they don’t share a declared type.

---

## ✅ **1. Basic Example**

```TypeScript
interface Point {
  x: number;
  y: number;
}

function printPoint(p: Point) {
  console.log(`x: ${p.x}, y: ${p.y}`);
}

const point = { x: 10, y: 20, z: 30 }; // Extra property z
printPoint(point); // ✅ Works because structure matches Point

```

- TypeScript only cares about **required properties** (`x` and `y`).
- Extra properties (`z`) do not prevent compatibility.

---

## 🔹 **2. Structural Typing vs Nominal Typing**

- **Structural typing**: compatibility based on **shape**.
- **Nominal typing** (like Java, C#): compatibility based on **explicit type names**.

```TypeScript
interface A { x: number; }
interface B { x: number; }

let a: A = { x: 5 };
let b: B = a; // ✅ Works in TS (structural)

```

- Even though `A` and `B` are different interfaces, assignment works because **structure matches**.

---

## 🔹 **3. Function Compatibility**

```TypeScript
type Fn1 = (a: number) => void;
type Fn2 = (a: number, b: string) => void;

let f1: Fn1 = (a) => console.log(a);
let f2: Fn2 = f1; // ✅ Works: fewer params allowed

```

- Functions are compatible if **parameters and return types match structurally**.
- Extra parameters in the target function are ignored if unused.

---

## 🔹 **4. Class Compatibility**

```TypeScript
class Person { name: string = ""; age: number = 0; }
class Employee { name: string = ""; age: number = 0; salary: number = 0; }

let p: Person = new Employee(); // ✅ Works

```

- Class instances are compatible based on **properties**, not class name.
- Extra properties in the assigned object are allowed.

---

## 🔹 **5. Optional Properties & Structural Typing**

```TypeScript
interface PartialPoint { x: number; y?: number; }
const pt = { x: 5 };
const pp: PartialPoint = pt; // ✅ Works

```

- Optional properties make **partial matches** possible.
- Only **required properties** are enforced for compatibility.

---

## 🔹 **6. Practical Implications**

- **Flexible API design**: functions can accept objects with extra fields.
- **Interoperability**: allows third-party libraries to work together if structures match.
- **Duck typing**: "If it walks like a duck and quacks like a duck…"

```TypeScript
interface Quacker { quack(): void }
function makeItQuack(q: Quacker) { q.quack(); }

const duck = { quack: () => console.log("Quack!"), swim: () => {} };
makeItQuack(duck); // ✅ Works

```

- Structural typing enables **duck typing** in TypeScript.

---

## 📋 **Structural Typing Summary Table**

|Concept|Explanation|Example|Notes|
|---|---|---|---|
|Structural typing|Compatibility based on **object shape**|`interface A {x:number}; interface B {x:number}; let b:B=a;`|Extra properties are OK|
|Function compatibility|Compatible if param & return types match structurally|`(a:number)=>void` assigned to `(a:number,b:string)=>void`|Extra params ignored if unused|
|Class compatibility|Compatible if instance properties match|`let p:Person = new Employee()`|Extra class fields allowed|
|Optional properties|Allow partial matches|`interface {x:number; y?:number}`|Only required properties checked|
|Duck typing|Works like a duck, structurally|Object with `quack()` assigned to `Quacker`|Enables flexible APIs|

---

**Rule of Thumb**:

- In TypeScript, **what matters is the shape of the object**, not its declared type.
- This enables **flexible and safe code**, but you should still be mindful of extra properties when designing APIs.