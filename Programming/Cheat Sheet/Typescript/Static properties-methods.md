---
Created: 2025-11-30T14:56
tags:
  - Classes
---
# **Static Properties and Methods in TypeScript**

Static members belong to the **class itself**, not to instances of the class.

- Use them for **utility functions or shared data** that doesn’t depend on individual objects.

---

## ✅ **1. Static Property**

```TypeScript
class Counter {
  static count: number = 0; // static property

  static increment() {
    Counter.count++;
  }
}

console.log(Counter.count); // 0
Counter.increment();
console.log(Counter.count); // 1

const c1 = new Counter();
// c1.count ❌ Error: Property 'count' does not exist on type 'Counter'

```

- Access with `**ClassName.member**`, not via instance.
- Static properties are shared across all instances.

---

## ✅ **2. Static Method**

```TypeScript
class MathUtils {
  static square(x: number): number {
    return x * x;
  }
}

console.log(MathUtils.square(5)); // 25

const util = new MathUtils();
// util.square(5) ❌ Error: static method cannot be called on instance

```

- Methods defined with `static` are **called on the class**, not instances.

---

## 🔹 **3. Combining Static and Instance Members**

```TypeScript
class Example {
  static description = "I am a class";
  name: string;

  constructor(name: string) {
    this.name = name;
  }

  greet() {
    console.log(`Hello, ${this.name}`);
  }

  static showDescription() {
    console.log(Example.description);
  }
}

const obj = new Example("Alice");
obj.greet();               // ✅ Hello, Alice
Example.showDescription(); // ✅ I am a class

```

- Static members **cannot access instance properties (**`**this.name**`**)**.
- Instance members **cannot access static members** directly — must use `ClassName.staticMember`.

---

## 🔹 **4. Practical Use Cases**

- **Counters / IDs shared by all instances**:

```TypeScript
class User {
  static nextId = 1;
  id: number;

  constructor() {
    this.id = User.nextId++;
  }
}

const u1 = new User();
const u2 = new User();
console.log(u1.id, u2.id); // 1, 2

```

- **Utility functions** (like `Math.sqrt`):

```TypeScript
class Utils {
  static toUpper(s: string) {
    return s.toUpperCase();
  }
}

console.log(Utils.toUpper("hello")); // HELLO

```

---

## 🔹 **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Static property|`static propName: type`|`static count: number`|Shared across all instances|
|Static method|`static methodName()`|`static square(x:number)`|Called on the class|
|Accessing|`ClassName.prop` or `ClassName.method()`|`Counter.count`|Cannot use `this` for instance members|
|Instance vs static|Instance: `this.name`|Static: `ClassName.member`|Static cannot access instance directly|

---

**Rule of Thumb**:

- Use **static members** for **class-wide data or utility functions**.
- Use **instance members** for **individual object state and behavior**.
- Static members exist **independently of any object**.