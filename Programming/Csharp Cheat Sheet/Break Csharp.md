---
Created: 2025-08-07T20:10
tags:
  - Control-Flow
---
## ✅ Concept

The `break` statement is used to **exit a loop or** `**switch**` **block immediately**, regardless of whether the loop condition has been met or not.

---

## 🧠 Syntax

```C#
break;
```

- **Used inside**: `for`, `while`, `do...while`, `foreach`, and `switch` blocks.
- Once executed, control **jumps out** of the innermost loop or switch.

---

## 🔄 Usage Scenarios

1. **Exit early from a loop when a condition is met** (e.g., found item).
2. **Stop iterating once you get the desired result.**
3. **Avoid unnecessary iterations for performance.**
4. **Exit a** `**switch**` **case** to prevent fallthrough.

---

## ⚠️ Common Gotchas

|Gotcha|Explanation|
|---|---|
|🧱 Only exits one level|`break` only exits the _innermost_ loop or `switch`. Use flags or methods for nested loops.|
|🚫 Not a function return|`break` just exits a loop; it doesn’t exit a method. Use `return` for that.|
|🔄 Only valid in loops/switch|Using `break` outside of a loop or `switch` causes a compile error.|

---

## 📋 Quick Reference Table

|Context|Can use `break`?|Effect|
|---|---|---|
|`for` loop|✅|Exits the loop early|
|`while` loop|✅|Exits the loop early|
|`do...while`|✅|Exits the loop early|
|`foreach` loop|✅|Exits the loop early|
|`switch`|✅|Exits the current case|
|Outside block|❌|Compile-time error|

---

## 🌍 Real-World Examples

### 🔎 Exit a `foreach` loop when a match is found

```C#
string[] colors = { "Red", "Green", "Blue", "Yellow" };

foreach (var color in colors)
{
    if (color == "Blue")
    {
        Console.WriteLine("Found Blue!");
        break;
    }
}
```

---

### 🧠 Inside a `switch` block

```C#
int day = 3;

switch (day)
{
    case 1:
        Console.WriteLine("Monday");
        break;
    case 2:
        Console.WriteLine("Tuesday");
        break;
    case 3:
        Console.WriteLine("Wednesday");
        break;
    default:
        Console.WriteLine("Other day");
        break;
}
```

---

### 🔁 In a `while` loop (infinite loop breaker)

```C#
int count = 0;

while (true)
{
    Console.WriteLine($"Count is {count}");
    if (count >= 5) break;
    count++;
}
```