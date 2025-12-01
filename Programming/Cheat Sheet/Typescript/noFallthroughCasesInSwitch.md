---
Created: 2025-12-01T11:24
tags:
  - Compiler-Config
---
# 🔵 TypeScript — `**noFallthroughCasesInSwitch**` **Cheat Sheet**

---

# ✅ 1. Full Explanation

## **What is** `**noFallthroughCasesInSwitch**`**?**

The `noFallthroughCasesInSwitch` option in TypeScript **prevents accidental fall-through in** `**switch**` **statements**.

- Fall-through happens when a `case` does **not have a** `**break**`**,** `**return**`**, or** `**throw**`, and execution continues into the next case.
- With this option **enabled**, TypeScript will report an **error if a case can fall through**.

---

## **How to Set**

In `tsconfig.json`:

```JSON
{
  "compilerOptions": {
    "noFallthroughCasesInSwitch": true}
}

```

Or via CLI:

```Bash
tsc --noFallthroughCasesInSwitch

```

---

## **Why It Matters**

- Prevents **logic bugs** in `switch` statements
- Ensures **each case is explicit**
- Useful in **strict type-checked projects**, especially with union types

---

## **How It Works**

```TypeScript
const color = "red";

switch (color) {
  case "red":
    console.log("Stop");
  case "green": // Error: fallthrough case not allowed
    console.log("Go");
    break;
}

```

- TypeScript flags the fall-through from `"red"` → `"green"`
- **Fix:** add `break`, `return`, or `throw` at the end of each case:

```TypeScript
switch (color) {
  case "red":
    console.log("Stop");
    break;
  case "green":
    console.log("Go");
    break;
}

```

---

## **Gotchas / Pitfalls**

1. **Empty cases** must use `break` if you intend to avoid fall-through
2. Works best with **union types** to ensure **exhaustive checking**
3. Can be combined with `**strict**` **and** `**noImplicitReturns**` for safer code
4. `**return**` **or** `**throw**` counts as a valid end, no need for `break`

---

# ✅ 2. Summary Table

|Option|Behavior|Example|
|---|---|---|
|`noFallthroughCasesInSwitch: true`|Prevents accidental fall-through|Fall-through without break → Error|
|Requires|Each `case` must end with `break`, `return`, or `throw`|✅|
|Works well with|`strict` mode, union types|Safer `switch` logic|
|Default|false|Falls through allowed|

---

# ✅ 3. Real-World Example (Practical)

### **Scenario 1: Accidentally falling through**

```TypeScript
type Direction = "up" | "down" | "left" | "right";
const dir: Direction = "up";

switch (dir) {
  case "up":
    console.log("Move Up");
  case "down":
    console.log("Move Down"); // Error: fallthrough
    break;
}

```

**Fix: Add** `**break**` **or** `**return**`

```TypeScript
switch (dir) {
  case "up":
    console.log("Move Up");
    break;
  case "down":
    console.log("Move Down");
    break;
}

```

---

### **Scenario 2: Using** `**return**` **instead of** `**break**`

```TypeScript
function move(dir: Direction) {
  switch (dir) {
    case "left":
      console.log("Move Left");
      return;
    case "right":
      console.log("Move Right");
      return;
  }
}

```

- ✅ No fall-through error because `return` ends the case

---

### **Scenario 3: Using union types for exhaustive switch**

```TypeScript
type Shape = "circle" | "square" | "triangle";

function describeShape(shape: Shape) {
  switch (shape) {
    case "circle":
      console.log("Round");
      break;
    case "square":
      console.log("Four sides");
      break;
    case "triangle":
      console.log("Three sides");
      break;
  }
}

```

- Each case ends properly → TypeScript is happy
- No accidental fall-through

---

# 🔥 Bonus Tips

1. Combine with `strict` + `noImplicitReturns` to **catch missing returns in functions handling unions**
2. Helps prevent **hard-to-find runtime bugs** in large `switch` statements
3. Always end a case with `**break**`**,** `**return**`**,** `**throw**`, or intentionally comment it with `// fallthrough`