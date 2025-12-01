---
Created: 2025-12-01T11:22
tags:
  - Compiler-Config
---
# 🔵 TypeScript — **Source Maps Cheat Sheet**

---

# ✅ 1. Full Explanation

## **What is** `**sourceMap**`**?**

The `sourceMap` option in TypeScript tells the compiler to **generate** `**.map**` **files** alongside the compiled JavaScript.

- A source map maps the **compiled JavaScript code** back to the **original TypeScript code**.
- This is **essential for debugging** in browsers or Node.js.

---

## **How to Set**

In `tsconfig.json`:

```JSON
{
  "compilerOptions": {
    "sourceMap": true}
}

```

Or via CLI:

```Bash
tsc --sourceMap

```

- Generates `.js.map` files alongside each `.js` output file.

---

## **Why It Matters**

- Debug TypeScript **directly in the browser or Node**
- Supports **breakpoints, stack traces, and console logging** showing TypeScript lines
- Works with **bundlers** like Webpack, Vite, Rollup for development mode

---

## **How It Works**

- Each `.js.map` file contains:
    - Original `.ts` filename
    - Line/column mappings
    - Source content (optional)
- Browsers (or Node.js with `-enable-source-maps`) can use this to **map errors back to TypeScript**.

---

## **Gotchas / Pitfalls**

1. **Do not enable** `**sourceMap**` **in production** unless you want `.ts` source exposed.
2. Works best with `**inlineSources**` if you want the TypeScript code embedded in the map:

```JSON
{
  "compilerOptions": {
    "sourceMap": true,
    "inlineSources": true}
}

```

1. `**outDir**` **matters** — maps are created relative to `outDir`.
2. Bundlers may override source maps; always check your build pipeline.
3. Node.js requires `-enable-source-maps` to use source maps in stack traces.

---

# ✅ 2. Summary Table

|Option|Behavior|Notes|
|---|---|---|
|`sourceMap: true`|Generates `.js.map` files|Maps JS → TS for debugging|
|`inlineSourceMap: true`|Embeds map inside JS file|No separate `.map` file|
|`inlineSources: true`|Embeds original TS code in the map|Useful for debugging without `.ts` files|
|`sourceRoot`|Base path for sources in map|Adjust if sources are served from a different folder|
|`mapRoot`|Path to write map files|Defaults to `outDir`|

---

# ✅ 3. Real-World Example (Practical)

### **Scenario: Browser Development**

```JSON
{
  "compilerOptions": {
    "outDir": "dist",
    "sourceMap": true,
    "inlineSources": true,
    "target": "ES2020",
    "module": "ESNext"
  }
}

```

Compile TypeScript:

```Bash
tsc

```

Generated files:

```Plain
dist/
 ├─ app.js
 ├─ app.js.map

```

- In browser dev tools, you can see and debug `**app.ts**` **directly**
- Breakpoints, console logs, and stack traces show **TypeScript lines** instead of compiled JS

---

### **Scenario: Node.js Development**

```Bash
node --enable-source-maps dist/app.js

```

- Error stack traces now point to TypeScript lines instead of compiled JavaScript
- Works well with `ts-node` for development

---

# 🔥 Bonus Tips

1. Combine `**sourceMap**` **+** `**inlineSources**` for easy debugging without copying `.ts` files.
2. For **production builds**, consider **disabling** `**inlineSources**` to avoid exposing source code.
3. Works seamlessly with **Webpack / Vite / Rollup dev mode** — most modern bundlers respect `sourceMap` from TypeScript.