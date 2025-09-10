---
Created: 2025-08-07T20:10
tags:
  - Control-Flow
---
## ✅ Concept

The `goto` statement **jumps to a labeled statement** in the same method or code block. It's a **low-level control structure** often discouraged in favor of cleaner, structured flow (e.g., loops, methods).

---

## 🧠 Syntax

```C#
goto LabelName;

...

LabelName:
    // Code to jump to
```

- `LabelName` must be a **valid label** (an identifier followed by `:`).
- Label and `goto` must be in the **same function** or **code block**.

---

## 🔄 Usage Scenarios

1. **Exit nested loops** (when `break` isn’t enough).
2. **Centralized error handling** in legacy or performance-critical code.
3. **Jump to specific logic sections** (rare and discouraged in modern design).

---

## ⚠️ Common Gotchas

|Gotcha|Explanation|
|---|---|
|🚫 Spaghetti code|Overuse makes code hard to read/maintain.|
|❌ Can’t jump into blocks|You can’t jump into `if`, `while`, or `switch` blocks from outside.|
|📍 Labels must exist|Label must be in the same method; no jumping between methods.|
|🚫 Not for OOP|Bad practice in object-oriented programming unless highly justified.|

---

## 📋 Quick Reference Table

|Feature|Description|
|---|---|
|Label|Identifier followed by `:`|
|Goto jump|`goto LabelName;`|
|Scope limit|Same method only|
|Use in switch|✅ Valid, often used in fallthrough|
|Good practice?|❌ Rarely; usually better alternatives|

---

## 🆚 Alternatives

|Task|Prefer This|Instead of `goto`|
|---|---|---|
|Exit loop|`break`, `return`|`goto EndLoop;`|
|Skip iteration|`continue`|`goto Next;`|
|Jump to common logic|`method call`|`goto Label;`|
|Error handling|`try-catch`|`goto HandleError;`|

---

## 🌍 Real-World Examples

### 🔁 Exit nested loops using `goto`

```C#
for (int i = 0; i < 3; i++)
{
    for (int j = 0; j < 3; j++)
    {
        if (i + j == 3)
            goto Done;
        Console.WriteLine($"i={i}, j={j}");
    }
}

Done:
Console.WriteLine("Exited both loops.");
```

---

### 🧠 Inside `switch` for fallthrough (rare in C#)

```C#
int x = 2;

switch (x)
{
    case 1:
        Console.WriteLine("One");
        break;
    case 2:
        goto case 3;
    case 3:
        Console.WriteLine("Three");
        break;
    default:
        Console.WriteLine("Default");
        break;
}
```

---

### 🚨 Centralized error handling (discouraged, but possible)

```C#
int result;

if (!int.TryParse("abc", out result))
    goto Error;

Console.WriteLine($"Parsed number: {result}");
return;

Error:
Console.WriteLine("Failed to parse number.");
```

---

## 🧼 Best Practice

- Avoid `goto` unless necessary (e.g., in **deeply nested loops** or **generated code**).
- Use **structured control** (`for`, `if`, `return`, `break`) for readability and maintainability.