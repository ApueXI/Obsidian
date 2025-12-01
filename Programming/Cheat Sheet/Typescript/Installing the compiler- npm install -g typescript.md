---
Created: 2025-11-30T14:34
tags:
  - Intro-to-Typescript
---
## ⭐ **Installing the TypeScript Compiler**

To use TypeScript on your machine, you need the **TypeScript compiler**, called `tsc`.

You install it globally using npm (Node Package Manager):

```Bash
npm install -g typescript

```

### ✔️ What this command does:

- Installs the TypeScript compiler **system-wide**
- Makes the `tsc` command available in your terminal
- Allows you to compile `.ts` files anywhere on your computer

After installing, check version:

```Bash
tsc --version

```

If it prints a version number, TypeScript is ready.

---

### 🧠 Quick Note

- Installing globally (`g`) makes `tsc` available everywhere.
- You can also install TypeScript locally per project:

```Bash
npm install typescript --save-dev

```

But the **global install** is ideal when you're just learning or experimenting.