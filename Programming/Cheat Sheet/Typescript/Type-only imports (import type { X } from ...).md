---
Created: 2025-11-30T15:03
tags:
  - Modules
---
# **Type-Only Imports in TypeScript**

Type-only imports allow you to **import types without including any runtime code**.

- Useful for **interfaces, type aliases, or classes used only for typing**.
- Reduces **bundle size** in projects using module bundlers like Webpack or Vite.

---

## ✅ **1. Basic Type-Only Import**

```TypeScript
// types.ts
export interface User {
  id: number;
  name: string;
}

export type ID = number;

```

```TypeScript
// app.ts
import type { User, ID } from "./types";

const user: User = { id: 1, name: "Alice" };
const userId: ID = 1;

```

- `import type` ensures **only type information** is imported.
- No JavaScript code is generated for these imports during compilation.

---

## ✅ **2. Using Classes as Types Only**

```TypeScript
// models.ts
export class Person {
  constructor(public name: string) {}
}

```

```TypeScript
// app.ts
import type { Person } from "./models";

function greet(person: Person) {
  console.log(`Hello, ${person.name}`);
}

```

- Even though `Person` is a class, using `import type` **imports it as a type only**, no runtime reference.

---

## ✅ **3. Type-Only Imports vs Regular Imports**

```TypeScript
import type { User } from "./types"; // ✅ Type-only
import { User } from "./types";      // ❌ Imports both type & runtime (if class)

```

- **Type-only imports** are erased in emitted JavaScript.
- Regular imports include **runtime code**, which may increase bundle size unnecessarily.

---

## ✅ **4. Type-Only Imports With Aliases**

```TypeScript
import type { User as IUser } from "./types";

const user: IUser = { id: 1, name: "Bob" };

```

- Can **rename types** with `as` while keeping it type-only.

---

## ✅ **5. Type-Only Re-Exports**

```TypeScript
// index.ts
export type { User, ID } from "./types";

```

- Useful for creating a **centralized type module**.
- Consumers can import **types without runtime code**:

```TypeScript
import type { User } from "./index";

```

---

## 🔹 **6. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Type-only import|`import type { X } from './file'`|`import type { User } from './types'`|Only type info, erased at runtime|
|Alias|`import type { X as Y } from './file'`|`import type { User as IUser } from './types'`|Rename imported type|
|Type-only re-export|`export type { X } from './file'`|`export type { User, ID } from './types'`|Centralizes type exports|
|vs regular import|`import { X } from './file'`|`import { Person } from './models'`|Regular imports include runtime code|

---

**Rule of Thumb**:

- Use `**import type**` for **interfaces, types, or classes used only as types**.
- Reduces **runtime overhead** and **bundle size**.
- Use **regular imports** when you need the **actual runtime value or class**.