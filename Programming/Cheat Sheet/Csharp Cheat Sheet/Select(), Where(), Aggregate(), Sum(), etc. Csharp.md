---
Created: 2025-08-07T20:10
tags:
  - LINQ
---
## ✅ Setup

```C#
using System;
using System.Linq;
using System.Collections.Generic;
```

```C#
int[] numbers = { 1, 2, 3, 4, 5 };
List<string> names = new List<string> { "Alice", "Bob", "Charlie" };
```

---

## 🧰 Most Common LINQ Methods

### 🔹 `Select()` – Projection (transform items)

```C#
var squares = numbers.Select(n => n * n);
```

**Output:** `1, 4, 9, 16, 25`

---

### 🔹 `Where()` – Filtering

```C#
var evens = numbers.Where(n => n % 2 == 0);
```

**Output:** `2, 4`

---

### 🔹 `Sum()` – Add all numeric elements

```C#
var total = numbers.Sum();
```

**Output:** `15`

---

### 🔹 `Aggregate()` – Custom accumulation (like reduce)

```C#
var factorial = numbers.Aggregate((acc, n) => acc * n);
```

**Output:** `120` (1×2×3×4×5)

---

### 🔹 `Count()` – Count elements or those matching a condition

```C#
var count = names.Count(n => n.Length > 3);
```

**Output:** `2` (`Alice`, `Charlie`)

---

### 🔹 `First()`, `FirstOrDefault()` – First match

```C#
var firstEven = numbers.First(n => n % 2 == 0);
```

```C#
var safe = numbers.FirstOrDefault(n => n > 10); // returns 0 (default int)
```

---

### 🔹 `Max()`, `Min()`, `Average()`

```C#
var max = numbers.Max(); // 5
var min = numbers.Min(); // 1
var avg = numbers.Average(); // 3.0
```

---

### 🔹 `Distinct()` – Unique values

```C#
int[] dupes = { 1, 2, 2, 3 };
var unique = dupes.Distinct(); // 1, 2, 3
```

---

### 🔹 `OrderBy()`, `OrderByDescending()`

```C#
var sorted = names.OrderBy(n => n.Length);
var reverseSorted = names.OrderByDescending(n => n);
```

---

### 🔹 `Take()`, `Skip()`

```C#
var firstTwo = numbers.Take(2); // 1, 2
var afterTwo = numbers.Skip(2); // 3, 4, 5
```

---

### 🔹 `Any()`, `All()` – Boolean checks

```C#
bool anyEven = numbers.Any(n => n % 2 == 0); // true
bool allPositive = numbers.All(n => n > 0); // true
```

---

### 🔹 `ToList()`, `ToArray()`

```C#
var list = numbers.Where(n => n > 2).ToList();
var array = numbers.Select(n => n * 2).ToArray();
```

---

## 🧠 Real-World Example

### Get Names Starting with 'A' in Uppercase

```C#
var aNames = names
    .Where(n => n.StartsWith("A"))
    .Select(n => n.ToUpper());
```

### Get Sum of Even Numbers > 2

```C#
var evenSum = numbers
    .Where(n => n % 2 == 0 && n > 2)
    .Sum(); // 4
```

---

## 📋 Summary Table

|Method|Description|
|---|---|
|`Select()`|Transforms elements (projection)|
|`Where()`|Filters items|
|`Sum()`|Adds numeric items|
|`Aggregate()`|Reduces to a single result (custom logic)|
|`Count()`|Counts items or matching items|
|`First()`|First match (throws if none)|
|`FirstOrDefault()`|First match or default|
|`Max()`, `Min()`|Finds extremes|
|`Average()`|Finds average of numeric values|
|`Distinct()`|Removes duplicates|
|`OrderBy()`|Sorts ascending|
|`OrderByDescending()`|Sorts descending|
|`Take()`, `Skip()`|Pagination-like filtering|
|`Any()`, `All()`|Boolean conditions|
|`ToList()`, `ToArray()`|Materializes results|

---

## ⚠️ Gotchas

|Issue|Fix|
|---|---|
|`First()` throws if no match|Use `FirstOrDefault()`|
|`Aggregate()` crashes on empty|Use overload with seed value|
|`Select()` does not modify original collection|It's a projection, not in-place|