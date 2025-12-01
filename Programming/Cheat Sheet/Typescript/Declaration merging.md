---
Created: 2025-12-01T11:49
tags:
  - Extra-Advanced-Topics
---
# 🔵 TypeScript — **Declaration Merging**

---

## 1. **Full Explanation**

### **What is Declaration Merging?**

- Declaration merging is a **TypeScript feature** that allows you to **combine multiple declarations with the same name** into a single definition.
- Works mainly for **interfaces, namespaces, and functions**.
- Enables **extending existing types or modules without modifying original code**.

---

### **Key Rules**

1. **Interfaces** with the same name are merged **by combining their members**.
2. **Namespaces** with the same name are merged **into one**.
3. **Functions** can be overloaded by declaring multiple signatures.
4. **Classes** do not merge; they are **nominal**.

---

## 2. **How It Works**

### **1. Interface Merging**

```TypeScript
interface User {
  name: string;
}

interface User {
  age: number;
}

const user: User = { name: "Alice", age: 30 }; // ✅ Both properties exist

```

- The **final** `**User**` **interface** has both `name` and `age`.

---

### **2. Namespace Merging**

```TypeScript
namespace Utils {
  export function greet() { console.log("Hello"); }
}

namespace Utils {
  export function bye() { console.log("Goodbye"); }
}

Utils.greet(); // ✅ Hello
Utils.bye();   // ✅ Goodbye

```

- Both namespaces **merge into a single namespace** `Utils`.

---

### **3. Function Merging (Overloads)**

```TypeScript
function combine(a: string, b: string): string;
function combine(a: number, b: number): number;
function combine(a: any, b: any) {
  return a + b;
}

combine(1, 2);       // ✅ 3
combine("a", "b");   // ✅ "ab"

```

- Multiple **declarations of the same function** are merged as **overloads**.

---

### **4. Interface + Namespace Merging**

- You can merge an **interface and a namespace** with the same name:

```TypeScript
interface Person {
  name: string;
}

namespace Person {
  export function greet(p: Person) {
    console.log("Hello " + p.name);
  }
}

const p: Person = { name: "Alice" };
Person.greet(p); // ✅ Hello Alice

```

- The namespace can **augment the interface** with static functions or constants.

---

## 3. **Gotchas / Pitfalls**

1. **Classes do not merge**
    - Cannot have two class declarations with the same name.
2. **Order matters for functions**
    - Implementation must appear **after all overloads**.
3. **Be careful with property conflicts**
    - Conflicting types in merged interfaces cause compile-time errors.
4. **Use merging intentionally**
    - Overuse can make code confusing or hard to maintain.

---

## 4. **Summary Table**

|Feature|Mergable?|How it merges|Example|
|---|---|---|---|
|Interface|✅|Combine properties|`interface User {name}; interface User {age};` → `{name, age}`|
|Namespace|✅|Combine members|Two `namespace Utils { ... }` merge|
|Function|✅|Overloads|Multiple declarations with same name|
|Class|❌|❌|Classes cannot merge|
|Interface + Namespace|✅|Interface + static functions|`interface Person` + `namespace Person`|

---

## 5. **Real-World Examples**

### **Example 1: Interface Merging**

```TypeScript
interface Config { debug: boolean }
interface Config { version: string }

const cfg: Config = { debug: true, version: "1.0" }; // ✅ OK

```

### **Example 2: Namespace Merging**

```TypeScript
namespace MathUtils { export const pi = 3.14; }
namespace MathUtils { export const e = 2.71; }

console.log(MathUtils.pi, MathUtils.e); // ✅ 3.14 2.71

```

### **Example 3: Function Overloads**

```TypeScript
function greet(name: string): string;
function greet(names: string[]): string[];
function greet(name: any): any { return Array.isArray(name) ? name : [name]; }

greet("Alice");      // ✅ ["Alice"]
greet(["Bob", "Eve"]); // ✅ ["Bob", "Eve"]

```

### **Example 4: Interface + Namespace**

```TypeScript
interface Logger { level: string }
namespace Logger {
  export function log(msg: string) { console.log(msg); }
}

Logger.log("Hello"); // ✅ Hello

```

---

## 6. **Key Takeaways**

1. Declaration merging is **compile-time only** — no runtime effect.
2. Interfaces, namespaces, and functions are **mergeable**; classes are **not**.
3. Use merging to **extend third-party types** or **add static helpers**.
4. Helps keep code **modular and extensible** without modifying original code.