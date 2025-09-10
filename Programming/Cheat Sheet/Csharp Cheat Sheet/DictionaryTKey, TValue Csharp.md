---
Created: 2025-08-07T20:10
tags:
  - Array-&-Collections
---
## ✅ What is `Dictionary<TKey, TValue>`?

- A **generic collection** of **key-value pairs**.
- Fast **lookup**, **insert**, and **remove** operations.
- Part of `System.Collections.Generic`.

```C#
using System.Collections.Generic;
```

---

## 🧠 Declaration & Initialization

```C#
Dictionary<int, string> idToName = new Dictionary<int, string>();
Dictionary<string, int> fruitStock = new Dictionary<string, int>
{
    { "Apple", 10 },
    { "Banana", 20 }
};
```

---

## 📦 Common Methods & Properties

|Operation|Example|Description|
|---|---|---|
|`.Add(key, value)`|`dict.Add("Key", 123);`|Adds new entry|
|`.Remove(key)`|`dict.Remove("Key");`|Removes entry by key|
|`.ContainsKey(key)`|`dict.ContainsKey("Key");`|Checks if key exists|
|`.ContainsValue(val)`|`dict.ContainsValue(123);`|Checks if value exists|
|`.TryGetValue()`|`dict.TryGetValue("Key", out var val);`|Safe way to access value|
|`.Clear()`|`dict.Clear();`|Removes all key-value pairs|
|`.Count`|`dict.Count;`|Gets number of entries|
|`.Keys`|`foreach (var k in dict.Keys)`|Gets all keys|
|`.Values`|`foreach (var v in dict.Values)`|Gets all values|
|Indexer access|`dict["Key"] = 456;` / `var v = dict["Key"];`|Get/set value for a key|

---

## 🧪 Example

```C#
Dictionary<string, int> stock = new Dictionary<string, int>();

stock.Add("Apples", 100);
stock["Oranges"] = 50; // same as Add or update
stock["Apples"] += 10;

if (stock.ContainsKey("Oranges"))
    Console.WriteLine("Oranges in stock: " + stock["Oranges"]);

foreach (var item in stock)
    Console.WriteLine($"{item.Key}: {item.Value}");
```

---

## 🔁 Iteration

```C#
foreach (KeyValuePair<string, int> pair in stock)
{
    Console.WriteLine($"Item: {pair.Key}, Qty: {pair.Value}");
}

// Or use deconstruction (C# 7.0+)
foreach (var (key, value) in stock)
{
    Console.WriteLine($"{key} → {value}");
}
```

---

## 🛡️ `TryGetValue` — Safe Access

```C#
if (stock.TryGetValue("Mangoes", out int qty))
{
    Console.WriteLine($"Mangoes: {qty}");
}
else
{
    Console.WriteLine("Mangoes not found.");
}
```

---

## ⚖️ Dictionary vs List

|Feature|`Dictionary<TKey, TValue>`|`List<T>`|
|---|---|---|
|Key-based access|✅ Constant time|❌ Not supported|
|Order maintained?|❌ Unordered (use `SortedDictionary`)|✅ Maintains order|
|Use case|Fast lookup by key|Ordered, index-based access|
|Key must be unique?|✅ Yes|❌ Not applicable|

---

## ⚠️ Gotchas

|Mistake|Why it's a problem|
|---|---|
|Accessing nonexistent key with `[]`|Throws `KeyNotFoundException`|
|Duplicate key on `.Add()`|Throws exception|
|Modifying collection during loop|Causes `InvalidOperationException`|
|Using complex objects as keys|Must override `Equals()` and `GetHashCode()`|

---

## 🧾 Summary Table

|Task|Code Example|
|---|---|
|Create|`new Dictionary<string, int>()`|
|Add item|`dict.Add("Cat", 3);`|
|Check key|`dict.ContainsKey("Dog");`|
|Get item safely|`dict.TryGetValue("Dog", out var d);`|
|Update value|`dict["Dog"] = 5;`|
|Iterate entries|`foreach (var kvp in dict)`|
|Count|`dict.Count;`|

---

## 🧰 Use Cases

- Storing student ID → name mappings
- Caching computed values
- Counting word frequencies
- Configuration settings (e.g., `"theme": "dark"`)