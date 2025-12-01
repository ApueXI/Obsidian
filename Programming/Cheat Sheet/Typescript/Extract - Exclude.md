---
Created: 2025-12-01T11:13
tags:
  - Utility-Types
---
# 🔵 TypeScript Utility Types — **Extract / Exclude**

**Cheat Sheet (Full Explanation • Summary Table • Real-World Example)**

---

# ✅ 1. Full Explanation

## **1.** `**Exclude<T, U>**`

### **Concept**

`Exclude` removes from type `T` all members that are assignable to type `U`.

It filters OUT unwanted types.

### **Syntax**

```TypeScript
Exclude<T, U>

```

### **Usage**

Use this when:

- You want to **remove one or more possibilities** from a union type.
- You want to **prevent certain values** from being allowed.
- You are performing **negative type filtering**.

### **Gotchas**

- Works only on **union types**.
- If `U` doesn’t overlap with `T`, nothing is removed.
- This does **not** alter objects — only unions.

---

## **2.** `**Extract<T, U>**`

### **Concept**

`Extract` keeps **only** the members of `T` that are assignable to `U`.

It filters IN desired types.

### **Syntax**

```TypeScript
Extract<T, U>

```

### **Usage**

Use this when:

- You want to **pick only certain types** from a union.
- You need to ensure a value is one of the **approved subset**.
- You want to filter for **specific types** inside a complex union.

### **Gotchas**

- Also works only on **union types**.
- If there is **no** overlap, the result is `never`.
- Extraction is based on **assignability**, not equality.

---

# ✅ 2. Summary Table

|Utility Type|Purpose|Keeps|Removes|Output Example|
|---|---|---|---|---|
|**Exclude<T, U>**|Remove types from a union|Types in `T` **not assignable to** `U`|Types assignable to `U`|`Exclude<"a" \| "b", "a"> → "b"`|
|**Extract<T, U>**|Keep only some types from a union|Types in `T` **assignable to** `U`|Types not assignable to `U`|`Extract<"a" \| "b", "a"> → "a"`|

---

# ✅ 3. Real-World Example (Practical, Not Basic)

### **Scenario:**

You are designing a role-based access system.

Your union type includes all possible user roles:

```TypeScript
type Roles = "ADMIN" | "EDITOR" | "VIEWER" | "GUEST";

```

### **Problem:**

- Only **ADMIN** and **EDITOR** can manage content.
- You want:
    - A type that represents **restricted roles** (no access) → use `Exclude`
    - A type that represents **roles allowed to edit** → use `Extract`

---

## **Using** `**Extract**` **(allowed roles)**

```TypeScript
type CanEdit = Extract<Roles, "ADMIN" | "EDITOR">;
// "ADMIN" | "EDITOR"

```

Used for enforcing that only valid editing roles pass through:

```TypeScript
function editContent(role: CanEdit) {
  console.log(role + " can edit!");
}

```

Fails if you try:

`editContent("VIEWER")` ❌

---

## **Using** `**Exclude**` **(roles with no access)**

```TypeScript
type CannotEdit = Exclude<Roles, "ADMIN" | "EDITOR">;
// "VIEWER" | "GUEST"

```

Used for access denial logic:

```TypeScript
function denyAccess(role: CannotEdit) {
  console.log(role + " cannot edit content.");
}

```

Prevents incorrectly passing an editing role:

`denyAccess("ADMIN")` ❌

---

# 🔥 Extra (Bonus Example for Objects & Narrowing)

```TypeScript
type APIResponse =
  | { status: 200; data: string }
  | { status: 404; error: string }
  | { status: 500; message: string };

// Extract only success responses
type Success = Extract<APIResponse, { status: 200 }>;

// Exclude error responses
type Errors = Exclude<APIResponse, { status: 200 }>;

```

Useful for response handling, routing, or switch-case type narrowing.