---
Created: 2025-12-01T11:26
tags:
  - Compiler-Config
---
# 🔵 TypeScript — `**skipLibCheck**` **Cheat Sheet**

---

# ✅ 1. Full Explanation

## **What is** `**skipLibCheck**`**?**

The `skipLibCheck` option tells TypeScript to **skip type checking of all declaration files (**`**.d.ts**`**)** in your project, including those from `node_modules`.

- By default, TypeScript type-checks **both your code and all imported** `**.d.ts**` **files**.
- `skipLibCheck: true` **speeds up compilation** and avoids errors from third-party type definitions.

---

## **How to Set**

In `tsconfig.json`:

```JSON
{
  "compilerOptions": {
    "skipLibCheck": true}
}

```

Or via CLI:

```Bash
tsc --skipLibCheck

```

---

## **Why It Matters**

- Speeds up **TypeScript compilation**, especially for large projects
- Avoids **errors in third-party libraries** that you cannot control
- Useful when using libraries with **incomplete or slightly incorrect typings**

---

## **How It Works**

- TypeScript **does not check** `**.d.ts**` **files** for type correctness
- Your **own TypeScript code** is still fully checked
- Declaration files are still **used for type inference**, just not fully validated

---

## **Gotchas / Pitfalls**

1. May **hide type errors** in library typings
    - Example: if a library has incorrect `.d.ts`, TS won’t warn you
2. Can lead to **runtime type errors** if the typings are wrong
3. **Not a replacement** for strict type checking in your own code
4. Best used in **large projects** or when **compiling legacy projects quickly**

---

# ✅ 2. Summary Table

|Option|Behavior|Notes|
|---|---|---|
|`skipLibCheck: true`|Skips type checking of `.d.ts` files|Speeds up compilation|
|Default|false|All `.d.ts` files are checked|
|Affects|node_modules, imported libraries|Your code is still fully type-checked|
|Best Practice|Use for large projects or problematic third-party libraries|Avoid hiding real type errors if possible|

---

# ✅ 3. Real-World Example (Practical)

### **Scenario 1: Large project with many libraries**

```JSON
{
  "compilerOptions": {
    "strict": true,
    "skipLibCheck": true}
}

```

- TypeScript will **check your code strictly**
- It will **skip validation** of all `.d.ts` files in `node_modules`
- Compiles faster, especially with many dependencies

---

### **Scenario 2: Avoiding library type errors**

```TypeScript
import { problematicFunction } from "some-typed-lib";
problematicFunction(); // library has wrong .d.ts

```

- With `skipLibCheck: false` → may throw compilation error due to incorrect `.d.ts`
- With `skipLibCheck: true` → compiles fine, you rely on runtime behavior

---

### **Scenario 3: Best practice combination**

```JSON
{
  "compilerOptions": {
    "strict": true,
    "noImplicitAny": true,
    "skipLibCheck": true}
}

```

- ✅ Your code is **fully type-checked**
- ✅ Compilation is **faster**
- ⚠️ Library typing errors are ignored

---

# 🔥 Bonus Tips

1. Often combined with `**strict**` **mode** to maintain safety for your own code
2. Recommended for **projects with large** `**node_modules**` or many dependencies
3. Avoid enabling it as a shortcut for **ignoring type errors in your own code**