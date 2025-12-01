---
Created: 2025-11-30T15:02
tags:
  - Modules
---
# **Default Exports in TypeScript**

Default exports allow a module to **export a single main value**, class, function, or object.

- A module can have **only one default export**.
- Consumers can import it using **any name** without curly braces.

---

## ✅ **1. Basic Default Export**

```TypeScript
// logger.ts
export default class Logger {
  log(message: string) {
    console.log("LOG:", message);
  }
}

```

- This module exports **one primary class** as the default.
- Can also be a **function** or **constant**:

```TypeScript
export default function greet(name: string) {
  console.log(`Hello, ${name}`);
}

export default 42; // exporting a constant

```

---

## ✅ **2. Importing Default Exports**

```TypeScript
// main.ts
import Logger from "./logger";

const logger = new Logger();
logger.log("Hello!"); // LOG: Hello!

```

- **No curly braces** needed.
- Can name the import **anything**:

```TypeScript
import MyLogger from "./logger"; // ✅ Works
const logger = new MyLogger();

```

---

## ✅ **3. Combining Default and Named Exports**

```TypeScript
// utils.ts
export const PI = 3.14;
export default function square(x: number): number {
  return x * x;
}

```

```TypeScript
// main.ts
import square, { PI } from "./utils";

console.log(PI);      // 3.14
console.log(square(5));// 25

```

- Default import comes **first**, followed by **named imports in curly braces**.

---

## ✅ **4. Re-exporting Default Exports**

```TypeScript
// index.ts
export { default as Logger } from "./logger";

```

```TypeScript
// app.ts
import { Logger } from "./index";
const logger = new Logger();

```

- Allows **renaming default exports** when consolidating modules.

---

## 🔹 **5. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Default export|`export default value`|`export default class Logger {}`|Only one per module|
|Default function export|`export default function()`|`export default function greet()`|Can be imported by any name|
|Import default|`import Name from './file'`|`import Logger from './logger'`|No curly braces, name flexible|
|Combine default + named|`import defaultName, { named } from './file'`|`import square, { PI } from './utils'`|Default first, named next|
|Re-export default|`export { default as Name } from './file'`|`export { default as Logger } from './logger'`|Useful for module aggregation|

---

**Rule of Thumb**:

- Use **default exports** for the **main value, class, or function** of a module.
- Use **named exports** for additional utilities.
- Combine both to **organize large modules effectively**.