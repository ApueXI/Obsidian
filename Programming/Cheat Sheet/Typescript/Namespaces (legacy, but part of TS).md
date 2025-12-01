---
Created: 2025-12-01T11:51
tags:
  - Extra-Advanced-Topics
---
# 🔵 TypeScript — **Namespaces (Legacy)**

---

## 1. **Full Explanation**

### **What Are Namespaces?**

- Namespaces are **TypeScript’s way of organizing code** under a **single named scope**, typically to avoid global variable conflicts.
- They were previously called **internal modules** before ES6 modules became standard.
- While **ES6 modules are now preferred**, namespaces are still supported in TS for **legacy code** or **internal organization**.

---

### **Why Use Namespaces**

1. Encapsulate **variables, functions, interfaces, and classes**.
2. Prevent **pollution of the global scope**.
3. Useful for **legacy codebases** that don’t use ES modules.

---

### **Key Points**

- Everything inside a namespace is **scoped** to that namespace.
- Can **export members** to make them accessible outside the namespace.
- Supports **nested namespaces**.
- Can **merge namespaces** (declaration merging) in TypeScript.

---

## 2. **How It Works**

### 1. **Basic Namespace**

```TypeScript
namespace Utils {
  export function greet(name: string) {
    console.log("Hello " + name);
  }
}

Utils.greet("Alice"); // ✅ "Hello Alice"

```

- Must use `export` for members you want to access outside.

---

### 2. **Nested Namespaces**

```TypeScript
namespace MathUtils {
  export namespace Algebra {
    export function add(a: number, b: number) {
      return a + b;
    }
  }
}

console.log(MathUtils.Algebra.add(2, 3)); // ✅ 5

```

---

### 3. **Namespace Merging**

```TypeScript
namespace Logger {
  export function log(msg: string) { console.log(msg); }
}

namespace Logger {
  export function warn(msg: string) { console.warn(msg); }
}

Logger.log("Hello"); // ✅ "Hello"
Logger.warn("Warning"); // ✅ "Warning"

```

- Multiple namespace declarations with the **same name** merge their members.

---

### 4. **Interface + Namespace Merging**

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
Person.greet(p); // ✅ "Hello Alice"

```

- This allows adding **static methods or utilities** to interfaces.

---

## 3. **Gotchas / Pitfalls**

1. **Namespaces are legacy** → prefer ES modules (`import` / `export`) for modern code.
2. Overuse can make code **nested and hard to read**.
3. Must explicitly **export** members to use them outside the namespace.
4. Cannot merge **classes or functions** like namespaces do (only namespaces, interfaces).

---

## 4. **Summary Table**

|Feature|Syntax|Notes|
|---|---|---|
|Basic Namespace|`namespace MyNS { ... }`|Encapsulates members|
|Exported Members|`export function ...`|Accessible outside the namespace|
|Nested Namespaces|`namespace Outer { namespace Inner { ... } }`|Use dot notation to access|
|Namespace Merging|Multiple `namespace` declarations with same name|Members combined|
|Interface + Namespace|`interface I { ... } namespace I { ... }`|Adds static helpers|
|Modern Alternative|ES Modules|Prefer `import`/`export` over namespaces|

---

## 5. **Real-World Examples**

### **Example 1: Basic Namespace**

```TypeScript
namespace Utils {
  export function greet(name: string) {
    console.log("Hello " + name);
  }
}
Utils.greet("Alice"); // ✅ "Hello Alice"

```

### **Example 2: Nested Namespace**

```TypeScript
namespace MathUtils {
  export namespace Algebra {
    export function multiply(a: number, b: number) {
      return a * b;
    }
  }
}
console.log(MathUtils.Algebra.multiply(3, 4)); // ✅ 12

```

### **Example 3: Namespace Merging**

```TypeScript
namespace Logger {
  export function info(msg: string) { console.log(msg); }
}
namespace Logger {
  export function error(msg: string) { console.error(msg); }
}
Logger.info("Info");  // ✅ "Info"
Logger.error("Error"); // ✅ "Error"

```

### **Example 4: Interface + Namespace**

```TypeScript
interface User {
  name: string;
}

namespace User {
  export function greet(user: User) {
    console.log("Hello " + user.name);
  }
}

const u: User = { name: "Alice" };
User.greet(u); // ✅ "Hello Alice"

```

---

## 6. **Key Takeaways**

1. Namespaces are **legacy internal modules** → mainly for old codebases.
2. Useful for **grouping related code** and **avoiding global pollution**.
3. Modern TypeScript prefers **ES6 modules** (`import` / `export`) over namespaces.
4. Supports **nested namespaces**, **merging**, and **interface augmentation**.