---
Created: 2025-08-07T20:10
tags:
  - Control-Flow
---
## ✅ Concept

The `continue` statement **skips the rest of the current loop iteration** and **jumps to the next one**. It’s useful when you want to **ignore certain values or conditions** without stopping the loop entirely.

---

## 🧠 Syntax

```C#
continue;
```

- Used inside `for`, `while`, `do...while`, and `foreach` loops.
- When encountered, the rest of the code in the loop block is **skipped** for that iteration.

---

## 🔄 Usage Scenarios

1. **Skip invalid or unwanted data** in a collection.
2. **Ignore even/odd values**, empty strings, or nulls.
3. **Filter without breaking the loop**.

---

## ⚠️ Common Gotchas

|Gotcha|Explanation|
|---|---|
|❌ Doesn't exit loop|Unlike `break`, `continue` just skips to the next iteration.|
|🔂 Skips logic|Code **after** `continue;` is not executed in the current iteration.|
|🧱 Nested Loops|Only affects the **innermost** loop where it appears.|
|⛔ Not in `switch`|`continue` is not allowed in `switch`; it’s only for loops.|

---

## 📋 Quick Reference Table

|Loop Type|Can use `continue`?|Effect|
|---|---|---|
|`for` loop|✅|Skips to next iteration|
|`while` loop|✅|Skips to condition check|
|`do...while`|✅|Skips to condition check|
|`foreach` loop|✅|Skips to next element|
|`switch` block|❌|Not allowed|

---

## 🆚 `break` vs `continue`

|Feature|`break`|`continue`|
|---|---|---|
|Exits loop?|✅ Yes|❌ No, skips to next iteration|
|Used for?|Exit loop early|Skip specific iterations|
|Control flow|Goes outside loop|Jumps to loop's next evaluation|

---

## 🌍 Real-World Examples

### 🧼 Skip empty strings in a list

```C#
List<string> names = new List<string> { "Anna", "", "Mark", "John" };

foreach (string name in names)
{
    if (string.IsNullOrEmpty(name))
        continue;

    Console.WriteLine($"Name: {name}");
}
```

**Output:**

```Plain
Name: Anna
Name: Mark
Name: John
```

---

### 🔢 Skip odd numbers in a `for` loop

```C#
for (int i = 1; i <= 5; i++)
{
    if (i % 2 != 0)
        continue;

    Console.WriteLine(i);
}
```

**Output:**

```Plain
2
4
```

---

### ⏳ In a `while` loop (skip 3)

```C#
int count = 0;

while (count < 5)
{
    count++;
    if (count == 3)
        continue;

    Console.WriteLine(count);
}
```

**Output:**

```Plain
1
2
4
5
```