---
Created: 2025-11-30T14:29
tags:
  - Intro-to-Typescript
---
## **🧩 What TypeScript Is (Superset of JavaScript)**

**TypeScript is a programming language developed by Microsoft that builds on top of JavaScript.**

It is called a **“superset”** of JavaScript because:

### ✔️ **All valid JavaScript code is also valid TypeScript code.**

You can rename a `.js` file to `.ts` and it still works.

### ✔️ **TypeScript adds powerful features on top of JavaScript**, such as:

- **Static typing** (number, string, boolean, interfaces, enums, etc.)
- **Compile-time error checking** (catches bugs early before running the code)
- **Better tooling & autocompletion**
- **Modern features before they appear in JS**
- **Improved code organization** (interfaces, namespaces, generics)

### ✔️ **TypeScript must be compiled to JavaScript**

Browsers cannot run `.ts` files directly.

A TypeScript compiler (`tsc`) transforms TypeScript → JavaScript.

---

## **🔍 Simple Example**

**JavaScript:**

```TypeScript
function greet(name) {
  return "Hello " + name;
}

```

**TypeScript version with type checking:**

```TypeScript
function greet(name: string): string {
  return "Hello " + name;
}

```

If you pass a number instead of a string, TypeScript will warn you **before you run the program**.

---

## **💬 Summary**

TypeScript = **JavaScript + types + better safety + better tooling**

It makes large projects easier to maintain, reduces bugs, and improves developer experience.