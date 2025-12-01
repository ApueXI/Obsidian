---
Created: 2025-11-30T14:48
tags:
  - Funcions
---
# `**void**` **vs** `**never**` **in TypeScript**

Both `void` and `never` are **special return types**, but they have **very different purposes**.

---

## ✅ **1.** `**void**`

- Represents a function that **does not return any meaningful value**.
- Commonly used for functions that **perform side effects** (like logging, updating UI).

### **Example**

```TypeScript
function logMessage(msg: string): void {
  console.log(msg);
}

const result = logMessage("Hello");
console.log(result); // undefined

```

- `logMessage` returns **nothing**, so TypeScript treats it as `void`.
- `void` allows `undefined` to be returned implicitly.

---

### 🔹 **Use Cases for** `**void**`

- Logging or printing
- Event handlers
- Functions that perform actions but do not return a value

```TypeScript
document.addEventListener("click", (e): void => {
  console.log("Clicked!");
});

```

---

## ✅ **2.** `**never**`

- Represents a function that **never returns**.
- Used for functions that **throw errors or run infinite loops**.
- Indicates **code that cannot continue normally**.

### **Example: Function that throws**

```TypeScript
function throwError(msg: string): never {
  throw new Error(msg);
}

```

### **Example: Infinite loop**

```TypeScript
function infiniteLoop(): never {
  while (true) {}
}

```

- TypeScript knows the function **does not complete normally**, so the type is `never`.

---

### 🔹 **Use Cases for** `**never**`

- Exhaustiveness checks in **switch/case** statements
- Functions that always **throw errors**
- Functions that run **forever** (rare)

```TypeScript
type Shape = "circle" | "square";

function assertNever(x: never): never {
  throw new Error("Unexpected value: " + x);
}

function handleShape(shape: Shape) {
  switch(shape) {
    case "circle": return "Circle";
    case "square": return "Square";
    default: return assertNever(shape); // ensures all cases are handled
  }
}

```

---

## 📋 `**void**` **vs** `**never**` **Summary Table**

|Feature|`void`|`never`|
|---|---|---|
|Meaning|Function returns **nothing**|Function **never returns**|
|Typical usage|Logging, side-effect functions|Throwing errors, infinite loops, exhaustiveness checks|
|Can return|`undefined` (implicitly)|Nothing — function cannot complete|
|Examples|`function log(): void { console.log("hi") }`|`function fail(): never { throw new Error("fail") }`|

---

**Rule of Thumb**:

- Use `void` when the function **finishes normally but returns nothing**.
- Use `never` when the function **cannot finish normally**.