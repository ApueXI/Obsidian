---
Created: 2025-11-30T14:33
tags:
  - Intro-to-Typescript
---
## ⭐ **Type Checking vs. Runtime Behavior**

Type checking and runtime behavior are two different phases of a program’s life.

Here’s the clean, clear breakdown:

---

# ✅ **1. Type Checking (Compile-Time)**

This happens **before** the program runs.

Languages like **TypeScript, C#, C++, Java** look at your code and check:

- Are you using the right types?
- Can this function receive that argument?
- Does a variable always hold the correct type?
- Are you violating type rules?

**If something is wrong, the compiler warns you early.**

Example (TypeScript):

```TypeScript
function divide(a: number, b: number) {
  return a / b;
}

divide("10", 2); // ❌ Type error before running

```

Type checking **never executes the code** — it only analyzes structure and types.

---

# ✅ **2. Runtime Behavior (When Code Actually Runs)**

This is what happens **during execution**.

Even with perfect type checking, the program can still fail at runtime.

Examples:

### Case A — Logic Errors

```TypeScript
function divide(a: number, b: number) {
  return a / b;
}

divide(10, 0); // ✔️ Compiles fine
               // ❌ Runtime: Infinity or crash

```

The type system doesn’t know you're dividing by zero — that’s a runtime issue.

---

### Case B — External Data Problems

A program might expect a number but receive a corrupted API response:

```TypeScript
let age: number = JSON.parse(apiResponse).age;
// TypeScript thinks it's a number.
// Runtime: it might actually be null or a string.

```

Type checking can’t control external data.

---

### Case C — Exceptions & Crashes

Even valid types can result in:

- File not found
- Out of memory
- Network error
- Null pointer (C#, C++, Java)

Types don’t protect you from all runtime errors.

---

# ⚖️ **The Key Difference**

|Aspect|Type Checking (Compile-Time)|Runtime Behavior (Execution-Time)|
|---|---|---|
|When it happens|Before execution|While program runs|
|Purpose|Catch type errors|Execute logic + handle real-world conditions|
|What it catches|Type mismatches|Crashes, exceptions, logic bugs|
|Can it stop bad input?|No (only checks code)|Yes (through validation logic)|
|Languages|TypeScript, C#, C++, Java|All languages|

---

# 🧠 **The Relationship Between the Two**

- **Type checking prevents certain classes of bugs early**, saving time.
- **Runtime behavior deals with actual data and real-world conditions.**
- **A strong type system reduces errors but never eliminates runtime failures.**
- You still need **exceptions, validation, error handling**, etc.

---

# 🌍 Real-World Example

Imagine a login system:

### Type Checking Phase:

- `username` must be a string
- `password` must be a string
- function must return a boolean

No syntax or type errors? ✔️ Program compiles.

### Runtime Phase:

Now real issues appear:

- Internet disconnects
- Database is down
- User entered an empty password
- Server threw an exception
- API returned malformed JSON

These are runtime behaviors — **type safety does not guarantee real-world safety**.