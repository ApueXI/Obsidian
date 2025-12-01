---
Created: 2025-12-01T11:48
tags:
  - Core-Typescript-Philosophy
---
# 🔵 TypeScript Philosophy — **Shape Over Class**

---

## 1. **Structural Typing vs Nominal Typing**

|Concept|Description|
|---|---|
|**Structural Typing**|Type compatibility is based on **object shape** (properties and their types), not the name of the type or class.|
|**Nominal Typing**|Type compatibility depends on **explicit type identity** (like classes in Java, C#). Type names must match.|

**TypeScript is structural**, meaning:

```TypeScript
class A { x = 1; y = 2; }
class B { x = 10; y = 20; z = 30; }

let a: A;
let b: B = new B();

a = b; // ✅ OK, B has all properties of A (extra property z is ignored)

```

- `a` and `b` are compatible **because they share the same shape**, not because they share the same class.

---

## 2. **Key Implications**

1. **Extra properties are usually ignored**

```TypeScript
interface Point { x: number; y: number; }
const point3D = { x: 1, y: 2, z: 3 };
const pt: Point = point3D; // ✅ OK

```

1. **Classes are just object shapes**

- Class names **don’t enforce type identity**.
- Only the **members’ presence and type** matter.

1. **Functions follow the same rule**

```TypeScript
type Fn = (x: number) => number;

const sum = (a: number, b: number) => a + b;
const f: Fn = sum; // ✅ OK, extra parameters are ignored

```

1. **Interfaces are also structural**

```TypeScript
interface Named { name: string }
interface Person { name: string; age: number }

const person: Person = { name: "Alice", age: 30 };
const named: Named = person; // ✅ OK

```

---

## 3. **Why This Matters**

- **Flexibility**: You don’t need explicit inheritance or implements keyword to reuse types.
- **Type Safety**: You can rely on **object shapes** for checking compatibility.
- **Code Reuse**: Easier to integrate third-party libraries that may not use your classes.

---

## 4. **Gotchas / Pitfalls**

1. Object literals assigned **directly** must not have extra properties:

```TypeScript
const named: Named = { name: "Alice", age: 30 }; // ❌ Error: extra property 'age'

```

1. Classes with extra properties are compatible **only when assigned from a variable**, not from object literal directly:

```TypeScript
let b = { x: 10, y: 20, z: 30 };
let a: A = b; // ✅ OK

```

1. Runtime identity is **not checked**:

```TypeScript
class Foo {}
class Bar {}

const foo: Foo = new Bar() as any; // TS only cares about shape, not class name

```

---

## 5. **Summary Table**

|Feature|Structural Typing Behavior|
|---|---|
|Object|Compatible if shape matches|
|Class|Compatible if members match, name ignored|
|Interface|Compatible if structure matches|
|Function|Compatible if parameters & return type match|
|Literal Assignment|Extra properties checked only for object literals|