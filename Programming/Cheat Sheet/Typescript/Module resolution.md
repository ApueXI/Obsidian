---
Created: 2025-12-01T11:21
tags:
  - Compiler-Config
---
# 🔵 TypeScript — **Module Resolution Cheat Sheet**

---

# ✅ 1. Full Explanation

## **What is** `**moduleResolution**`**?**

The `moduleResolution` option in TypeScript tells the compiler **how to find modules** when using `import` statements.

- It determines **how TypeScript looks for files** and **resolves module paths**.
- Works closely with `**module**`, `**baseUrl**`, and `**paths**` options.

---

## **How to Set**

In `tsconfig.json`:

```JSON
{
  "compilerOptions": {
    "moduleResolution": "node"
  }
}

```

Or via CLI:

```Bash
tsc --moduleResolution node

```

---

## **Supported Values**

|Value|Description|Use Case|
|---|---|---|
|`classic`|Legacy TypeScript resolution (pre-1.6)|Old TypeScript projects, rarely used|
|`node`|Mimics Node.js module resolution strategy|Most modern projects, Node.js, bundlers|
|`node16`|Node.js 16+ module resolution for ESM|Projects using `"type": "module"` in package.json|
|`nodenext`|Node.js next-gen module resolution|Latest Node.js ESM support|

---

## **Node Module Resolution Details**

- Searches **relative paths** first (`./`, `../`)
- Searches **node_modules folders** recursively
- Supports `.ts`, `.tsx`, `.d.ts`, `.js`, `.jsx` by default
- Works with **package.json** `**exports**` and `"main"` fields (ESM/CJS)

---

## **Classic Module Resolution Details**

- Old TypeScript default before v1.6
- Only searches **relative paths** and **paths defined via** `**baseUrl**`
- **Does not support node_modules recursion**
- Rarely used now

---

## **Why It Matters**

- Correct module resolution ensures **imports actually find the files**
- Avoids **“cannot find module” errors**
- Necessary for **TypeScript + Node.js ESM** projects
- Works with **custom path mapping** (e.g., `paths` in tsconfig)

---

## **Gotchas / Pitfalls**

1. Using `moduleResolution: classic` with `module: ESNext` can break imports
2. Node.js resolution (`node`) **ignores** `**paths**` **for non-relative imports** unless `baseUrl` is set
3. When using `"type": "module"` in Node, prefer `node16` or `nodenext`
4. Mixing `module: CommonJS` with `moduleResolution: node16` may not work
5. Extensions must sometimes be explicitly added (`import './file.js'`) when using Node ESM

---

# ✅ 2. Summary Table

|Option|Description|When to Use|
|---|---|---|
|`classic`|Legacy TypeScript resolution|Very old projects|
|`node`|Node.js-like resolution|Most modern projects|
|`node16`|Node 16 ESM resolution|Node.js ESM projects|
|`nodenext`|Latest Node ESM resolution|Modern Node.js + ES modules|
|Works With|`module`, `baseUrl`, `paths`|Resolving imports correctly|

---

# ✅ 3. Real-World Example (Practical)

### **Scenario 1: Node.js project (CommonJS)**

```JSON
{
  "compilerOptions": {
    "module": "CommonJS",
    "moduleResolution": "node",
    "target": "ES2017"
  }
}

```

```TypeScript
import fs from "fs"; // TypeScript finds node_modules/fs/index.d.ts
import { helper } from "./utils"; // Relative path resolution

```

- Node-style resolution finds both **relative files** and **packages in node_modules**

---

### **Scenario 2: Node.js ESM project**

```JSON
{
  "compilerOptions": {
    "module": "ESNext",
    "moduleResolution": "nodenext",
    "target": "ES2020"
  }
}

```

```TypeScript
import { readFile } from "fs/promises"; // Node 16+ style import
import { myFunc } from "./utils.js";     // Explicit extension required

```

- Uses **Node 16+ module resolution**, compatible with `"type": "module"`
- TypeScript can resolve `.ts` → `.js` mapping automatically for ESM

---

### **Scenario 3: Classic resolution (legacy)**

```JSON
{
  "compilerOptions": {
    "module": "AMD",
    "moduleResolution": "classic"
  }
}

```

- Only relative imports are supported
- Node-style `node_modules` lookup is ignored

---

# 🔥 Bonus Tips

1. For **most modern projects**, use:

```JSON
"moduleResolution": "node"

```

1. For **Node.js ESM projects**, use:

```JSON
"moduleResolution": "node16" // or nodenext

```

1. Combine with `"baseUrl"` and `"paths"` for **absolute imports**:

```JSON
{
  "compilerOptions": {
    "baseUrl": "./src",
    "paths": {
      "@utils/*": ["utils/*"]
    }
  }
}

```