---
Created: 2025-08-07T20:10
tags:
  - Methods-(Functions)
---
## ✅ Concept

**Default parameters** allow you to **specify default values** for method parameters. If an argument is **not provided** during the call, the **default value is used**.

---

## 🧠 Syntax

```C#
void PrintMessage(string message = "Hello", int repeat = 1)
{
    for (int i = 0; i < repeat; i++)
        Console.WriteLine(message);
}
```

### Valid Calls

```C#
PrintMessage();                  // Uses both defaults: "Hello", 1
PrintMessage("Hi");              // Uses default repeat: 1
PrintMessage("Bye", 3);          // Uses no defaults
```

---

## 📋 Quick Reference Table

|Feature|Allowed?|Example|
|---|---|---|
|Skip arguments|✅|`PrintMessage()`|
|Use with overloads|⚠️|Possible, but can cause ambiguity|
|Use with `ref/out`|❌|Not allowed with `ref` or `out`|
|Combine with `params`|✅ (last)|`Log(params string[] logs = null)`|
|Use named arguments|✅|`PrintMessage(repeat: 2)`|

---

## ✅ Benefits

- **Reduces method overloading**
- **Simplifies method calls**
- **Improves readability with named parameters**

---

## ⚠️ Gotchas

|Gotcha|Explanation|
|---|---|
|🧠 Must be at the end|All default parameters must follow non-default ones.|
|🧱 Compile-time only|Default values are determined **at compile time**, not dynamically.|
|❌ Can't use `ref`/`out`|These can’t be used with default values.|
|⚠️ Ambiguity with overloads|Avoid mixing with method overloading unless intentional and tested.|

---

## 🧩 Real-World Examples

### 1. Basic Logging Function

```C#
void Log(string message = "No message", string level = "INFO")
{
    Console.WriteLine($"[{level}] {message}");
}

Log();                        // [INFO] No message
Log("Something failed");      // [INFO] Something failed
Log("DB down", "ERROR");      // [ERROR] DB down
```

---

### 2. Using with Named Arguments

```C#
void Notify(string user = "admin", bool urgent = false)
{
    Console.WriteLine($"{user} - Urgent: {urgent}");
}

Notify(urgent: true);  // admin - Urgent: True
```

---

### 3. Invalid Usage (compile error)

```C#
// ❌ This causes an error
void Invalid(int x = 5, string y) { ... }
```

> ❗Fix: Put default parameters after required ones:

```C#
void Valid(string y, int x = 5) { ... }
```

---

## 🧠 Bonus Tip: Default Values Are Literal

These are allowed as defaults:

- Constants (`int`, `bool`, `string`, `null`)
- `const` fields
- `default(T)` (for generic methods)
- `new()` (for structs from C# 7.1+)