---
Created: 2025-11-30T14:34
tags:
  - Intro-to-Typescript
---
## ⭐ **Compiling TypeScript Files**

Once you have **TypeScript installed**, you can compile `.ts` files into plain JavaScript using the `tsc` command.

### Command:

```Plain
tsc file.ts

```

### ✔️ What Happens:

1. `tsc` reads your TypeScript code in `file.ts`.
2. It checks for **type errors**.
3. If no blocking errors, it generates a `file.js` in the **same directory**.
4. You can now run `file.js` in Node.js or in the browser.

---

### 🧠 Notes:

- By default, TypeScript outputs **JavaScript compatible with your environment** (usually ES5).
- To specify output options, you can use a `tsconfig.json` file or command-line flags:

```Bash
tsc file.ts --target ES6 --outDir dist

```

- `-target ES6` → sets JS version
- `-outDir dist` → outputs JS to the `dist` folder

---

### 🔹 Example

**TypeScript (file.ts):**

```TypeScript
function greet(name: string) {
  console.log("Hello, " + name);
}

greet("Alice");

```

**Compile:**

```Bash
tsc file.ts

```

**Generated JavaScript (file.js):**

```JavaScript
function greet(name) {
    console.log("Hello, " + name);
}
greet("Alice");

```

Now you can run it with Node.js:

```Bash
node file.js

```