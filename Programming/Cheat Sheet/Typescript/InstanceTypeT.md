---
Created: 2025-12-01T11:13
tags:
  - Utility-Types
---
# `**InstanceType<T>**` **in TypeScript**

`InstanceType<T>` extracts the **instance type** of a class constructor.

- `T` must be a **constructor function** (class or function that returns an object when `new` is used).
- The resulting type is the **type of the object created by** `**new T()**`.

Internally:

```TypeScript
type InstanceType<T extends new (...args: any) => any> =
    T extends new (...args: any) => infer R ? R : any;

```

(`infer R` captures the instance type.)

---

## ✅ **1. Basic Example with a Class**

```TypeScript
class User {
  constructor(
    public id: number,
    public name: string
  ) {}
}

type UserInstance = InstanceType<typeof User>;

const u: UserInstance = new User(1, "Alice");

```

`UserInstance` is **exactly the same** type as an instance created by:

```TypeScript
new User(...)

```

---

## ✅ **2. Extracting Instance Type from Constructor Functions**

```TypeScript
function Car(model: string) {
  return { model };
}

type CarInstance = InstanceType<typeof Car>; // { model: string }

```

Works with constructor functions too.

---

## ✅ **3. Using InstanceType with Factory-Like Patterns**

```TypeScript
class Database {
  connect() {}
}

function makeDB(ClassRef: typeof Database) {
  return new ClassRef();
}

type DBInstance = InstanceType<typeof Database>;

```

`DBInstance` becomes:

```TypeScript
{
  connect(): void;
}

```

---

## ✅ **4. With Classes That Have Methods**

```TypeScript
class Point {
  constructor(public x: number, public y: number) {}
  length() { return Math.sqrt(this.x ** 2 + this.y ** 2); }
}

type PointType = InstanceType<typeof Point>;

const p: PointType = new Point(3, 4);
p.length(); // OK

```

- The type includes **fields and methods**.

---

## ✅ **5. Working with Abstract Classes**

You can’t instantiate an abstract class, but you can still use `InstanceType`:

```TypeScript
abstract class Shape {
  abstract area(): number;
}

type ShapeInstance = InstanceType<typeof Shape>; // ERROR

// Must remove 'abstract'

```

TypeScript does **not** allow `InstanceType` for abstract classes unless cast.

---

## ✅ **6. Real-World Example: Dependency Injection**

```TypeScript
class Logger {
  log(msg: string) {}
}

function resolve<T extends new (...args: any) => any>(cls: T): InstanceType<T> {
  return new cls();
}

const logger = resolve(Logger); // type: Logger

```

`InstanceType<T>` lets DI containers return the correct instance type automatically.

---

## ✅ **7. Summary Table**

|Feature|Description|Example|
|---|---|---|
|Extract class instance type|Gives type of `new Class()`|`InstanceType<typeof User>`|
|Works with constructors|Class or function returning object|`InstanceType<typeof Car>`|
|Includes methods|Full instance type|Methods + properties|
|Useful in DI / factories|Ensures correct return types|`resolve<T>()`|
|Internally uses `infer`|`infer R`|Captures the created instance|

---

**Rule of Thumb**

Use `**InstanceType<T>**` when you need the **type of an object created from a class** without manually duplicating the structure.