---
Created: 2025-08-07T20:10
tags:
  - Control-Flow
---
## ✅ Concept

The `foreach` loop is used to **iterate over collections** (arrays, lists, dictionaries, etc.) **without needing an index**. It’s best when you just want to **read or process items** sequentially.

---

## 🧠 Syntax

```C#
foreach (var item in collection)
{
    // Code to use item
}
```

- `item` is a local variable representing the current element.
- `collection` can be an array, `List<T>`, `Dictionary<K,V>`, etc.

---

## 🔄 How It Works

- Starts at the beginning of the collection.
- Runs once per element.
- Ends automatically at the end of the collection.

---

## ⚠️ Common Gotchas

|Gotcha|Explanation|
|---|---|
|❌ Modifying Collection|You **can’t change the collection's structure** (e.g., add/remove elements) while inside the loop.|
|🔒 Read-Only Items|The `item` is **read-only**, so you **can’t modify it directly** (especially with structs).|
|❓ Index Access|`foreach` **doesn't give you access to indexes**. Use `for` if you need indices.|
|🔁 Use `break` / `continue`|Yes, you **can** use `break` and `continue` inside `foreach`.|

---

## 📋 Quick Reference Table

|Element|Description|
|---|---|
|`foreach`|Loop type|
|`var` / `type`|Declares the loop variable|
|`in`|Specifies the collection to loop through|
|Read-only items|✅|
|Index available?|❌|

---

## 🌍 Real-World Example

```C#
using System;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        List<string> fruits = new List<string> { "Apple", "Banana", "Cherry" };

        foreach (string fruit in fruits)
        {
            Console.WriteLine($"I like {fruit}");
        }
    }
}
```

### ✅ Output:

```Plain
I like Apple
I like Banana
I like Cherry
```

---

## 🧠 Bonus: Dictionary Example

```C#
Dictionary<string, int> stock = new Dictionary<string, int>
{
    {"Apples", 10},
    {"Bananas", 5},
    {"Cherries", 7}
};

foreach (var kvp in stock)
{
    Console.WriteLine($"{kvp.Key}: {kvp.Value}");
}
```

---

Let me know if you want a visual diagram or comparison with `for` and `while` in specific use cases (e.g. performance, readability, safety).