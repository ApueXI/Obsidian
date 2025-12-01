---
Created: 2025-12-01T11:21
tags:
  - Compiler-Config
---
# 🔵 TypeScript — **Compiler** `**module**` **Option Cheat Sheet**

---

# ✅ 1. Full Explanation

## **What is the** `**module**` **option?**

The `module` option in TypeScript specifies the **module system** that TypeScript should use when emitting JavaScript code.

- Modules control **how imports and exports work at runtime**
- TypeScript supports **multiple module systems**, so you can target **Node.js, browsers, or bundlers**.

---

## **How to Set**

In `tsconfig.json`:

```JSON
{
  "compilerOptions": {
    "module": "CommonJS"
  }
}

```

Or via CLI:

```Bash
tsc --module ESNext

```

---

## **Supported Values & What They Do**

|Module|Description|Use Case / Environment|
|---|---|---|
|`CommonJS`|Standard Node.js module system (`require` / `module.exports`)|Node.js, older bundlers|
|`ES6` / `ES2015`|Standard ECMAScript modules (`import` / `export`)|Modern browsers, bundlers like Webpack/Rollup|
|`ESNext`|Latest ECMAScript module syntax|Future-proof; supports top-level `await`|
|`AMD`|Asynchronous Module Definition|Older browser module loaders (RequireJS)|
|`UMD`|Universal Module Definition|Works in both Node and browsers|
|`System`|SystemJS loader|Older dynamic module loader systems|
|`None`|No module generation|When you want global scripts or concatenation|

---

## **Why It Matters**

- Ensures **runtime compatibility** with your environment
- Determines **how imports/exports are transpiled**
- Affects **tree-shaking, bundling, and code size**
- Works in tandem with the `**target**` option

---

## **Gotchas / Pitfalls**

1. `CommonJS` supports Node.js but **does not support top-level** `**await**`
2. `ESNext` modules may require **modern bundlers** (Webpack, Vite, Rollup)
3. `AMD`, `System` are rarely used today
4. `UMD` is useful for **libraries distributed to browsers and Node**
5. Mixing `target` and `module` incorrectly can lead to runtime errors

---

# ✅ 2. Summary Table

|Module|JS Syntax|Environment / Use Case|
|---|---|---|
|`CommonJS`|`require(...)`, `module.exports`|Node.js, legacy bundlers|
|`ES6` / `ES2015`|`import ... from ...`, `export`|Modern browsers, bundlers|
|`ESNext`|Same as ES6, supports top-level `await`|Latest runtimes & bundlers|
|`AMD`|`define([...], function(){})`|Older browsers, RequireJS|
|`UMD`|Works as CommonJS + AMD|Library distributed to Node + Browser|
|`System`|SystemJS loader|Older module systems|
|`None`|No module wrapping|Global scripts, simple concatenation|

---

# ✅ 3. Real-World Example (Practical)

### **Scenario 1: Node.js project**

```JSON
{
  "compilerOptions": {
    "module": "CommonJS",
    "target": "ES2017"
  }
}

```

TypeScript output:

```TypeScript
// TypeScript
import { readFile } from "fs";

// Compiled JS (CommonJS)
const fs_1 = require("fs");

```

- Works directly with Node.js

---

### **Scenario 2: Modern Browser / Bundler**

```JSON
{
  "compilerOptions": {
    "module": "ESNext",
    "target": "ES2020"
  }
}

```

TypeScript output:

```TypeScript
// TypeScript
import { hello } from "./hello.js";

// Compiled JS (ESNext)
import { hello } from "./hello.js";

```

- Supports top-level `await` and tree-shaking
- Ideal for Vite, Webpack, Rollup

---

### **Scenario 3: UMD for Library Distribution**

```JSON
{
  "compilerOptions": {
    "module": "UMD",
    "target": "ES5"
  }
}

```

- Allows library code to work **both in Node and browsers**
- Provides backward compatibility with legacy environments

---

# 🔥 Bonus Tips

1. **ESNext + ES2020/ES2022** → enables latest features like `optional chaining`, `nullish coalescing`, top-level `await`
2. **UMD + ES5** → safe default for libraries distributed to many environments
3. **CommonJS + ES5/ES6** → safe for Node projects that don’t need modern module features