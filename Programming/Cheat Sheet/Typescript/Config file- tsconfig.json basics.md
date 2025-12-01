---
Created: 2025-11-30T14:35
tags:
  - Intro-to-Typescript
---
## ⭐ **TypeScript Configuration File: tsconfig.json Basics**

`tsconfig.json` is a **TypeScript project configuration file**.

It tells the TypeScript compiler (`tsc`) **how to compile your project**, which files to include, and what JavaScript version to output.

---

### 🔹 **Creating a tsconfig.json**

Run this in your project folder:

```Bash
tsc --init

```

This generates a basic `tsconfig.json` with default settings.

---

### 🔹 **Basic Structure**

```JSON
{
  "compilerOptions": {
    "target": "ES6",         // JavaScript version to output
    "module": "commonjs",    // Module system
    "outDir": "./dist",      // Output folder for compiled JS
    "rootDir": "./src",      // Source folder
    "strict": true           // Enable all strict type-checking options
  },
  "include": ["src/**/*"],   // Which files to include
  "exclude": ["node_modules"] // Which files to ignore
}

```

---

### ✔️ **Key Options Explained**

|Option|Description|
|---|---|
|`target`|Sets JavaScript version (`ES5`, `ES6`, `ES2017`, etc.)|
|`module`|Module system used (`commonjs`, `es6`, `amd`, etc.)|
|`outDir`|Directory for compiled JavaScript files|
|`rootDir`|Directory containing TypeScript source files|
|`strict`|Enables strict type-checking (recommended)|
|`include`|Files or folders to include in compilation|
|`exclude`|Files or folders to ignore|

---

### 🔹 **Example Project Structure**

```Plain
my-project/
├─ src/
│  ├─ index.ts
│  └─ utils.ts
├─ tsconfig.json
└─ dist/

```

- `src` → your TypeScript source code
- `dist` → compiled JavaScript goes here (configured by `outDir`)

---

### 🔹 **Compiling With tsconfig.json**

Once `tsconfig.json` is in place, you can compile the whole project by simply running:

```Bash
tsc

```

- No need to specify individual files; `tsc` reads the config.
- It respects `include`, `exclude`, and `compilerOptions`.

---

### 🔹 **Summary**

- `tsconfig.json` **manages your TypeScript project settings**.
- Helps organize source and output folders.
- Enables strict type-checking and modern JavaScript features.
- Simplifies compilation of multiple `.ts` files.