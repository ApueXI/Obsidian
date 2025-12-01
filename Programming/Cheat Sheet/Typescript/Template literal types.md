---
Created: 2025-11-30T15:07
tags:
  - Advance-Tpes
---
# **Template Literal Types in TypeScript**

Template literal types allow you to **construct string types dynamically** using **other string literal types**.

- Similar to JavaScript template literals (`` `${}` ``), but at the **type level**.
- Useful for **type-safe string patterns, event names, or keys**.

---

## ✅ **1. Basic Template Literal Type**

```TypeScript
type Greeting = `Hello ${string}`;

const greet1: Greeting = "Hello World";  // ✅ OK
// const greet2: Greeting = "Hi World"; // ❌ Error: does not match template

```

- Any string that matches the pattern `"Hello ${string}"` is allowed.
- TypeScript **checks the shape of the string at compile-time**.

---

## ✅ **2. Combining String Literal Types**

```TypeScript
type Direction = "left" | "right";
type UpperDirection = `move-${Direction}`;

const dir1: UpperDirection = "move-left";  // ✅ OK
const dir2: UpperDirection = "move-right"; // ✅ OK
// const dir3: UpperDirection = "move-up"; // ❌ Error

```

- Combine **literal types** to create **restricted string unions**.
- Ensures only **valid combinations** are allowed.

---

## ✅ **3. With Generic Types**

```TypeScript
type EventName<T extends string> = `${T}-event`;

type ClickEvent = EventName<"click">;
type HoverEvent = EventName<"hover">;

const clickEvent: ClickEvent = "click-event"; // ✅ OK
// const wrongEvent: ClickEvent = "hover-event"; // ❌ Error

```

- Generics can **dynamically generate string types**.
- Useful for **typed event systems** or **API endpoints**.

---

## ✅ **4. Uppercase / Lowercase / Capitalize Modifiers**

```TypeScript
type Name = "alice" | "bob";

type CapitalizedName = Capitalize<Name>; // "Alice" | "Bob"
type UpperName = Uppercase<Name>;        // "ALICE" | "BOB"
type LowerName = Lowercase<Name>;        // "alice" | "bob"

```

- Works with template literals for **more controlled string patterns**:

```TypeScript
type Event<T extends string> = `on${Capitalize<T>}`;
type ClickEvent = Event<"click">; // "onClick"
type HoverEvent = Event<"hover">; // "onHover"

```

---

## ✅ **5. Mapped Types With Template Literals**

```TypeScript
type Actions = "create" | "update" | "delete";

type ActionHandlers = {
  [K in Actions as `on${Capitalize<K>}`]: () => void;
};

const handlers: ActionHandlers = {
  onCreate: () => console.log("create"),
  onUpdate: () => console.log("update"),
  onDelete: () => console.log("delete")
};

```

- Template literals can **rename keys in mapped types**.
- Ensures **consistent naming patterns** for object keys.

---

## 🔹 **6. Summary Table**

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Basic template literal|`` `Hello ${string}` ``|`type Greeting =` Hello ${string}``|Match string patterns|
|Combine literal types|`` `move-${Direction}` ``|`"move-left"|"move-right"`|
|Generic template literal|`` `${T}-event` ``|`EventName<"click">`|Dynamic string types|
|Case modifiers|`Capitalize<T>`, `Uppercase<T>`|`"onClick"`|Works in template literals|
|Mapped types|`[K in Actions as` on${Capitalize<K>}`]: ...`|Creates typed keys|Enforces naming patterns|

---

**Rule of Thumb**:

- Use **template literal types** for **typed strings, keys, and events**.
- Combine with **generics, literal types, and mapped types** for maximum type safety.
- Great for **API endpoints, event handlers, and strongly-typed object keys**.