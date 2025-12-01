---
Created: 2025-12-01T11:26
tags:
  - Compiler-Config
---
# 🔵 TypeScript — `**resolveJsonModule**` **Cheat Sheet**

---

# ✅ 1. Full Explanation

## **What is** `**resolveJsonModule**`**?**

The `resolveJsonModule` option allows TypeScript to **import** `**.json**` **files directly** as modules with proper typing.

- Without it, TypeScript **cannot import JSON files** and will throw an error.
- With it, JSON is treated as a module, and TypeScript **infers the type from the file content**.

---

## **How to Set**

In `tsconfig.json`:

```JSON
{
  "compilerOptions": {
    "resolveJsonModule": true,
    "esModuleInterop": true}
}

```

- `esModuleInterop: true` is often required for default imports of JSON.

Or via CLI:

```Bash
tsc --resolveJsonModule

```

---

## **Why It Matters**

- Allows **configuration or data files** in JSON to be **imported safely**
- TypeScript will **infer the type** of the JSON object
- Eliminates the need for **manual typing** or using `require()`

---

## **How It Works**

Given a JSON file:

```JSON
// config.json
{
  "port": 8080,
  "host": "localhost",
  "debug": true}

```

You can import it in TypeScript:

```TypeScript
import config from "./config.json";

console.log(config.port);  // TypeScript knows it's a number
console.log(config.host);  // TypeScript knows it's a string

```

- TypeScript infers:

```TypeScript
const config: {
  port: number;
  host: string;
  debug: boolean;
}

```

---

## **Gotchas / Pitfalls**

1. Must enable `**esModuleInterop: true**` for default imports
2. TypeScript **cannot infer nested types perfectly if JSON is complex**, consider adding explicit types if needed
3. Works only for **local JSON files**, not for runtime-loaded JSON via `fetch` or `require()` in Node without compilation
4. Often paired with `**resolveJsonModule**` **+** `**strict**` for type safety

---

# ✅ 2. Summary Table

|Option|Behavior|Notes|
|---|---|---|
|`resolveJsonModule: true`|Allows importing `.json` files as modules|TypeScript infers types automatically|
|Requires|`esModuleInterop: true` for default imports|Optional if using `import * as config` syntax|
|Type inference|Automatic from JSON content|Can add explicit interface for clarity|
|Default|false|TypeScript cannot import JSON without this|

---

# ✅ 3. Real-World Example (Practical)

### **Scenario 1: Importing configuration**

```TypeScript
// config.json
{
  "apiUrl": "https://api.example.com",
  "timeout": 5000
}

```

```TypeScript
// index.ts
import config from "./config.json";

console.log(config.apiUrl);  // "https://api.example.com"
console.log(config.timeout); // 5000

```

- ✅ TypeScript knows `config.apiUrl` is `string` and `config.timeout` is `number`

---

### **Scenario 2: Nested JSON**

```JSON
// settings.json
{
  "theme": "dark",
  "layout": {
    "width": 1200,
    "height": 800
  }
}

```

```TypeScript
import settings from "./settings.json";

console.log(settings.layout.width);  // TypeScript infers number

```

- Nested types are inferred correctly

---

### **Scenario 3: Using named import (optional)**

```TypeScript
import * as settings from "./settings.json";
console.log(settings.theme);  // Works with or without esModuleInterop

```

---

# 🔥 Bonus Tips

1. Perfect for **config files, static data, or localization JSON**
2. TypeScript **infers types** from JSON automatically, reducing manual type definitions
3. Works seamlessly with **Webpack, Vite, or Node.js** projects after compilation