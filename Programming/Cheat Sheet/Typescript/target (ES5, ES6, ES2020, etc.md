---
Created: 2025-12-01T11:20
tags:
  - Compiler-Config
---
# 🔵 TypeScript — **Compiler** `**target**` **Cheat Sheet**

---

# ✅ 1. Full Explanation

## **What is the** `**target**` **option?**

The `target` option in TypeScript specifies the **JavaScript language version** that the compiler should output.

- TypeScript supports **modern syntax and features**, but not all environments support them.
- `target` controls **how TypeScript transpiles code** so it can run in older browsers or runtimes.

---

## **How to Set**

In `tsconfig.json`:

```JSON
{
  "compilerOptions": {
    "target": "ES5"
  }
}

```

Or via CLI:

```Bash
tsc --target ES6

```

---

## **Supported Values**

TypeScript supports multiple targets (common ones):

|Target|ECMAScript Version|Notes|
|---|---|---|
|`ES3`|ECMAScript 3|Very old, legacy browsers|
|`ES5`|ECMAScript 5|IE9+, safe for old browsers|
|`ES6` / `ES2015`|ECMAScript 2015|Modern syntax: classes, arrow functions, `let`/`const`|
|`ES2016`|ECMAScript 2016|Includes `**` (exponentiation)|
|`ES2017`|ECMAScript 2017|Async/await support|
|`ES2018`|ECMAScript 2018|`Rest/Spread` for objects|
|`ES2019`|ECMAScript 2019|`Array.flat`, `Object.fromEntries`|
|`ES2020`|ECMAScript 2020|`BigInt`, `Optional Chaining`, `Nullish Coalescing`|
|`ES2021`|ECMAScript 2021|`String.replaceAll`, `Promise.any`|
|`ES2022`|ECMAScript 2022|`Class static blocks`, `Top-level await`|
|`ESNext`|Latest ECMAScript|Always transpiles to latest features, may require runtime polyfills|

---

## **Why it matters**

- Ensures your code **runs on the intended JS environment**
- Influences **what features need downlevel compilation**
- Affects **async/await, generators, module syntax**, and other language features
- Can reduce **bundle size** if targeting modern environments

---

## **Gotchas / Pitfalls**

1. **Older targets cannot use modern syntax directly**
    - Example: Target `ES5` → arrow functions are compiled to `function` expressions
2. **Async/await requires** `**ES2017+**` **or generator downleveling**
3. **Optional chaining, nullish coalescing** → ES2020+
4. **Top-level** `**await**` → ES2022+ or `ESNext`
5. **Some runtime methods** may need polyfills even if TypeScript compiles them

---

# ✅ 2. Summary Table

|Target|Key Features Supported|Notes / Browser Support|
|---|---|---|
|ES3|Basic JS|Very legacy, not recommended|
|ES5|`function`, `var`, prototype inheritance|Safe for IE9+|
|ES6 / ES2015|`let`, `const`, classes, arrow functions, template strings, modules|Modern browsers|
|ES2016|Exponentiation `**`|Minor upgrade|
|ES2017|Async/await|Node 7.6+, modern browsers|
|ES2018|Object rest/spread|Supported in Chrome 69+, Node 10+|
|ES2019|Array.flat, Object.fromEntries|Modern runtime support|
|ES2020|Optional chaining `?.`, Nullish coalescing `??`, BigInt|Modern browsers only|
|ES2021|String.replaceAll, Promise.any|Latest features|
|ES2022|Top-level await, Class static blocks|Latest runtimes|
|ESNext|Always latest ECMAScript|May require polyfills|

---

# ✅ 3. Real-World Example (Practical)

### **Scenario 1:** Targeting older browsers (IE11)

```JSON
{
  "compilerOptions": {
    "target": "ES5"
  }
}

```

TypeScript converts modern features to **ES5-compatible code**:

```TypeScript
// TypeScript input
const add = (a: number, b: number) => a + b;

// Compiled to ES5
var add = function (a, b) {
    return a + b;
};

```

---

### **Scenario 2:** Targeting modern environments (ES2020)

```JSON
{
  "compilerOptions": {
    "target": "ES2020"
  }
}

```

You can safely use:

```TypeScript
const user = { name: "Alice" };
console.log(user?.address?.city ?? "Unknown"); // Optional chaining + nullish coalescing

```

- Compiles mostly **as-is**, no downlevel transformation needed
- Smaller output, faster runtime

---

### **Scenario 3:** Async/await support

```JSON
{
  "compilerOptions": {
    "target": "ES2017"
  }
}

```

```TypeScript
async function fetchData() {
  const res = await fetch("/api/data");
  return res.json();
}

```

- Async/await is supported natively in ES2017+
- Targeting ES5 would transpile it to generator-based downlevel code