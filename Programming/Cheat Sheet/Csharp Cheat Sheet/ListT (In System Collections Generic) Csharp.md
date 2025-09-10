---
Created: 2025-08-07T20:10
tags:
  - Array-&-Collections
---
## ✅ What is `List<T>`?

- `List<T>` is a **generic collection class** that represents a **resizable array** of a specific type `T`.
- It automatically resizes when elements are added or removed.
- Part of `System.Collections.Generic`.

```C#
using System.Collections.Generic;
```

---

## 🧠 Declaration & Initialization

```C#
List<int> numbers = new List<int>();  // Empty list of integers
List<string> names = new List<string> { "Alice", "Bob" };
```

You can also initialize with a collection:

```C#
int[] arr = {1, 2, 3};
List<int> nums = new List<int>(arr);
```

---

## 📦 Common `List<T>` Methods

|Method|Description|Example|
|---|---|---|
|`.Add(item)`|Adds an item|`list.Add(10);`|
|`.AddRange(collection)`|Adds multiple items|`list.AddRange(new[] {1,2,3});`|
|`.Insert(index, item)`|Inserts at specific index|`list.Insert(1, 99);`|
|`.Remove(item)`|Removes first match|`list.Remove(2);`|
|`.RemoveAt(index)`|Removes at index|`list.RemoveAt(0);`|
|`.RemoveRange(index, count)`|Removes range|`list.RemoveRange(1, 2);`|
|`.Clear()`|Removes all elements|`list.Clear();`|
|`.Contains(item)`|Checks if item exists|`list.Contains("Bob");`|
|`.IndexOf(item)`|Gets index of first match|`list.IndexOf("Alice");`|
|`.Sort()`|Sorts in ascending order|`list.Sort();`|
|`.Reverse()`|Reverses order|`list.Reverse();`|
|`.Count`|Gets number of items|`int count = list.Count;`|
|`.ToArray()`|Converts to array|`int[] arr = list.ToArray();`|
|`.Find(predicate)`|Finds first match|`list.Find(x => x > 10);`|
|`.FindAll(predicate)`|Finds all matches|`list.FindAll(x => x % 2 == 0);`|
|`.Exists(predicate)`|Checks if any match|`list.Exists(x => x < 0);`|
|`.TrueForAll(predicate)`|All items satisfy condition|`list.TrueForAll(x => x < 100);`|
|`.ForEach(action)`|Applies action to each element|`list.ForEach(x => Console.WriteLine(x));`|

---

## 🔁 Iteration

### `for` loop

```C#
for (int i = 0; i < numbers.Count; i++)
{
    Console.WriteLine(numbers[i]);
}
```

### `foreach` loop

```C#
foreach (int num in numbers)
{
    Console.WriteLine(num);
}
```

### `.ForEach()` method

```C#
numbers.ForEach(n => Console.WriteLine(n));
```

---

## 🧪 Real-World Example

```C#
List<string> tasks = new List<string> { "Buy milk", "Call mom", "Email boss" };
tasks.Add("Workout");
tasks.Remove("Call mom");

foreach (string task in tasks)
{
    Console.WriteLine(task);
}
```

---

## 🔄 Differences: `List<T>` vs Arrays

|Feature|`List<T>`|`T[]` (Array)|
|---|---|---|
|Size flexibility|Dynamically resizes|Fixed size|
|Add/remove items|Easy with `.Add()`, `.Remove()`|Requires manual resizing|
|Built-in methods|Many methods (Find, Exists, etc.)|Limited methods|
|Performance|Slightly slower due to overhead|Faster access and iteration|
|Use case|Preferred for unknown size lists|Preferred for performance-critical, fixed-size data|

---

## ⚠️ Gotchas

|Pitfall|Why it's a problem|
|---|---|
|Modifying collection while iterating (`foreach`)|Throws exception — use `for` loop instead|
|Null reference in `.Find()`|If no match, returns `null` — check before using|
|Forgetting `using System.Collections.Generic;`|Causes compile errors|

---

## 🧾 Summary Table

|Action|Example|
|---|---|
|Create|`new List<int>()`|
|Add|`list.Add(5);`|
|Remove|`list.Remove(5);`|
|Contains|`list.Contains(5)`|
|Count|`list.Count`|
|Convert|`list.ToArray();`|
|Sort|`list.Sort();`|
|Reverse|`list.Reverse();`|
|Find|`list.Find(x => x > 10);`|