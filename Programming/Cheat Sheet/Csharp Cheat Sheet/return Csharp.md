---
Created: 2025-08-07T20:10
tags:
  - Control-Flow
---
## ✅ Concept

The `return` statement **immediately exits a method** (or property, lambda, or local function) and optionally **returns a value** to the caller.

---

## 🧠 Syntax

```C#
return;         // For void methods
return value;   // For methods with return type
```

- Ends method execution **instantly**.
- Must match the declared **return type** of the method.

---

## 🔄 Usage Scenarios

1. **Return a computed result** from a method.
2. **Exit early** if an error or invalid condition is found.
3. **Short-circuit execution** based on a condition.
4. **Return objects, strings, arrays, etc.**

---

## ⚠️ Common Gotchas

|Gotcha|Explanation|
|---|---|
|⛔ Must return required type|If your method returns `int`, you **must return an** `**int**`.|
|🚫 Not for loops|`return` exits the whole method — not just a loop. Use `break` or `continue` for loops.|
|❌ No code after `return`|Code after `return` in a block is **unreachable** and causes a compile error.|
|🧠 Use with lambdas|Works inside lambdas too, but behaves differently depending on context (e.g. expression-bodied vs. block).|

---

## 📋 Quick Reference Table

|Use Case|Syntax|Description|
|---|---|---|
|Exit `void` method|`return;`|Exits with no value|
|Return a value|`return 42;`|Must match the return type|
|In property getters|`return fieldName;`|Used in get-only or full properties|
|Inside lambda|`return something;`|Used in block-bodied lambdas|
|Inside loop?|✅ Yes, but exits method|Not just the loop|

---

## 🆚 `return` vs `break` vs `continue`

|Statement|Exits Loop|Exits Method|Skips Current Iteration|
|---|---|---|---|
|`break`|✅|❌|❌|
|`continue`|❌|❌|✅|
|`return`|✅ (indirectly)|✅|❌|

---

## 🌍 Real-World Examples

### 🧮 Return the sum of two numbers

```C#
int Add(int a, int b)
{
    return a + b;
}

```

---

### 🛑 Exit early if input is invalid

```C#
void PrintUser(string name)
{
    if (string.IsNullOrEmpty(name))
    {
        Console.WriteLine("Invalid name.");
        return;
    }

    Console.WriteLine($"Hello, {name}!");
}
```

---

### 🔁 Used inside a loop (exits the whole method)

```C#
bool ContainsNegative(int[] numbers)
{
    foreach (int n in numbers)
    {
        if (n < 0)
            return true;
    }

    return false;
}
```

---

### 🧠 Return inside a lambda expression

```C#
Func<int, string> classify = x =>
{
    if (x < 0) return "Negative";
    if (x == 0) return "Zero";
    return "Positive";
};
```