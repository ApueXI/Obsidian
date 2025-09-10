---
Created: 2025-08-07T20:10
tags:
  - LINQ
---
## 🔍 What is LINQ to Objects?

LINQ to Objects allows querying in-memory collections like arrays, lists, dictionaries, etc., using expressive and readable LINQ syntax.

✅ Namespace:

```C#
using System.Linq;
```

✅ Example Collections:

```C#
int[] numbers = { 3, 6, 2, 9, 1, 4 };
List<string> names = new List<string> { "Alice", "Bob", "Charlie", "Dave" };
```

---

## 🧱 Basic LINQ Syntax Styles

### ✅ Query Syntax (SQL-like)

```C#
var result = from n in numbers
             where n > 4
             orderby n
             select n;
```

### ✅ Method Syntax (Fluent-style)

```C#
var result = numbers.Where(n => n > 4)
                    .OrderBy(n => n);
```

---

## 🧰 Common LINQ Operators

|LINQ Operator|Description|Example|
|---|---|---|
|`Where`|Filter elements|`.Where(x => x > 3)`|
|`Select`|Project/transform elements|`.Select(x => x * 2)`|
|`OrderBy`|Sort ascending|`.OrderBy(x => x)`|
|`OrderByDescending`|Sort descending|`.OrderByDescending(x => x)`|
|`First`, `FirstOrDefault`|First item / or default if not found|`.FirstOrDefault(x => x > 5)`|
|`GroupBy`|Group elements by a key|`.GroupBy(x => x.Length)`|
|`Distinct`|Remove duplicates|`.Distinct()`|
|`Any`, `All`|Conditional checks|`.Any(x => x == 3)`|
|`Count`, `Sum`, `Min`, `Max`, `Average`|Aggregation|`.Count()`, `.Sum()`|
|`Skip`, `Take`|Pagination|`.Skip(2).Take(3)`|

---

## ✅ Real-World Examples

### 🔹 Filter Names Starting With 'A'

```C#
var aNames = names.Where(name => name.StartsWith("A"));
```

### 🔹 Find Even Numbers and Sort

```C#
var evensSorted = from n in numbers
                  where n % 2 == 0
                  orderby n
                  select n;
```

### 🔹 Transform: Double the Numbers

```C#
var doubled = numbers.Select(n => n * 2);
```

### 🔹 Count Names with > 3 Letters

```C#
int count = names.Count(n => n.Length > 3);
```

---

## 🧠 Grouping Example

```C#
var grouped = from name in names
              group name by name.Length into g
              select new { Length = g.Key, Group = g };

foreach (var group in grouped)
{
    Console.WriteLine($"Length {group.Length}:");
    foreach (var name in group.Group)
        Console.WriteLine(" - " + name);
}
```

---

## 📦 Custom Object Example

```C#
class Student { public string Name; public int Age; }

List<Student> students = new()
{
    new Student { Name = "Alice", Age = 20 },
    new Student { Name = "Bob", Age = 22 },
    new Student { Name = "Cara", Age = 20 }
};

// Get names of students age 20
var result = students
    .Where(s => s.Age == 20)
    .Select(s => s.Name);
```

---

## 📋 Summary Table

|Feature|Example|
|---|---|
|Filter|`Where(x => x > 3)`|
|Transform|`Select(x => x * 2)`|
|Sort|`OrderBy(x => x)`|
|Grouping|`GroupBy(x => x.Length)`|
|Aggregates|`Sum()`, `Max()`, `Average()`|
|Take N items|`Take(3)`|
|Skip N items|`Skip(2)`|
|First match|`FirstOrDefault(x => x == 4)`|
|Check any/all|`Any(x => x < 0)`, `All(x => x > 0)`|
|Unique values|`Distinct()`|

---

## 🚫 Gotchas

|Gotcha|Explanation|
|---|---|
|`First()` crashes on empty|Use `FirstOrDefault()` to avoid exception|
|`Where().First()` vs `First()`|`Where` is lazy; `First` is immediate|
|`GroupBy` returns `IGrouping`|Need to iterate subgroups with `.Key`|