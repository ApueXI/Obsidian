---
Created: 2025-08-07T20:10
tags:
  - LINQ
---
## 📌 What is LINQ?

LINQ (Language Integrated Query) lets you query collections (arrays, lists, etc.) in a readable, SQL-like manner.

✅ Namespace:

```C#
using System.Linq;
```

✅ Example Data:

```C#
List<int> numbers = new List<int> { 5, 3, 9, 1, 4 };
```

---

## 🧱 Basic LINQ Query Structure

```C#
var result = from item in collection
             where condition
             orderby something
             select something;
```

---

## 🧮 LINQ Keywords

### 1. `from`

Starts the query and introduces the range variable.

```C#
from n in numbers
```

### 2. `where`

Filters elements based on a condition.

```C#
where n > 3
```

### 3. `select`

Projects the result (like a return).

```C#
select n
```

### 4. `orderby`

Sorts results ascending (default) or descending.

```C#
orderby n descending
```

### 5. `let`

Creates a local variable within the query.

```C#
let square = n * n
```

### 6. `group`

Groups data by a key.

```C#
group n by n % 2 into g
```

### 7. `into`

Continues query after `group` or `select`.

---

## ✅ Real Example

```C#
List<string> names = new List<string> { "Anna", "Mike", "John", "Maria", "David" };

var filtered = from name in names
               where name.StartsWith("M")
               orderby name
               select name;

foreach (var n in filtered)
    Console.WriteLine(n);
```

**Output:**

```Plain
Maria
Mike
```

---

## 🧠 Advanced Example (Grouping)

```C#
int[] numbers = { 1, 2, 3, 4, 5, 6 };

var grouped = from n in numbers
              group n by n % 2 == 0 into g
              select new { IsEven = g.Key, Numbers = g };

foreach (var group in grouped)
{
    Console.WriteLine(group.IsEven ? "Even:" : "Odd:");
    foreach (var num in group.Numbers)
        Console.WriteLine(num);
}
```

---

## 📋 Summary Table

|Keyword|Purpose|
|---|---|
|`from`|Starts query, defines iteration|
|`where`|Filters elements|
|`select`|Projects result|
|`orderby`|Sorts results (asc/desc)|
|`let`|Declares a sub-variable|
|`group`|Groups elements|
|`into`|Continues query after `group/select`|
|`join`|Joins two collections (like SQL JOIN)|

---

## 🔥 Tips

- Use `descending` with `orderby` to sort high-to-low.
- Combine `let` with `where` for clean logic.
- Query syntax is interchangeable with method syntax:
    
    ```C#
    var res = numbers.Where(n => n > 3).OrderBy(n => n);
    ```