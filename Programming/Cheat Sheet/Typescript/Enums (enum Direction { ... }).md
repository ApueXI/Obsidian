---
Created: 2025-11-30T14:39
tags:
  - Basic-Types
---
# ⭐ **Enums in TypeScript (**`**enum Direction { ... }**`**)**

Enums let you define a **set of named constants**.

They’re useful when a value should only come from a predefined category—like directions, roles, modes, statuses, etc.

---

# ✅ **1. Basic Enum Example**

```TypeScript
enum Direction {
  Up,
  Down,
  Left,
  Right
}

let move: Direction = Direction.Up;

```

### How it works:

- Each member gets a numeric value starting from **0** by default.
    - `Up = 0`
    - `Down = 1`
    - `Left = 2`
    - `Right = 3`

---

# ✅ **2. Custom Numeric Values**

You can change the default numbering:

```TypeScript
enum Status {
  Success = 200,
  NotFound = 404,
  ServerError = 500
}

```

---

# ✅ **3. String Enums**

String enums prevent bugs caused by unexpected numbers and are more readable.

```TypeScript
enum Role {
  Admin = "ADMIN",
  User = "USER",
  Guest = "GUEST"
}

let r: Role = Role.Admin;

```

---

# ✅ **4. Reverse Mapping (Numeric Enums Only)**

TypeScript creates two-way mappings for numeric enums:

```TypeScript
enum Color {
  Red,
  Green,
  Blue
}

Color.Green; // 1
Color[1];    // "Green"

```

String enums do **not** support reverse mapping.

---

# ✅ **5. Const Enums (Compile-Time Removal)**

`const enum` removes runtime footprint and inlines values:

```TypeScript
const enum Direction {
  Up,
  Down
}

let d = Direction.Up; // Compiled directly to the number 0

```

✔️ Faster

✔️ Smaller output

❗ Requires `preserveConstEnums` to be `false`

---

# ❗ Pitfall: Enums Emit JavaScript Code

Unlike interfaces or types, **enums generate actual JavaScript**.

If you don’t want any emitted code, prefer:

- **string literal unions**, e.g.:

```TypeScript
type Direction = "up" | "down" | "left" | "right";

```

---

# 📋 **Summary Table**

|Type of Enum|Example|Notes|
|---|---|---|
|Numeric Enum|`enum Dir { Up, Down }`|Auto-numbered (0,1,2…)|
|Numeric (Custom)|`enum Code { OK=200 }`|Custom numbers|
|String Enum|`enum Role { Admin="ADMIN" }`|No reverse mapping|
|Const Enum|`const enum X { A }`|Inlined, no JS output|
|Union Alternative|`type Role = "admin"|"user"`|

---

# 🧠 When to Use Enums

✔️ When you need **stable named constants**

✔️ When values have semantic meaning

✔️ When TypeScript’s reverse mapping is useful

✔️ When you want readable, standardized values