---
Created: 2025-08-07T20:10
tags:
  - Struct-vs-Enums
---
## ✅ Concept Overview

|Type|Value Type (`struct`)|Reference Type (`class`)|
|---|---|---|
|Memory|Stored on the **stack** (usually)|Stored on the **heap**|
|Copy|**Copied by value**|**Copied by reference**|
|Usage|Lightweight, short-lived data|Complex, long-lived objects|

---

## 🧠 Syntax

### `struct`

```C#
public struct Point
{
    public int X;
    public int Y;

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

### `class`

```C#
public class Person
{
    public string Name;
    public int Age;

    public Person(string name, int age) => (Name, Age) = (name, age);
}
```

---

## 🔄 Copy Behavior

```C#
Point p1 = new Point(1, 2);
Point p2 = p1;
p2.X = 99;

Console.WriteLine(p1.X);  // Still 1 (value copy)
```

```C#
Person p1 = new Person("Alex", 30);
Person p2 = p1;
p2.Name = "John";

Console.WriteLine(p1.Name);  // Now "John" (reference copy)
```

---

## 🔍 Key Differences

|Feature|`struct`|`class`|
|---|---|---|
|Type|Value type|Reference type|
|Stored in|Stack (usually)|Heap|
|Inheritance|❌ Cannot inherit from another struct/class|✅ Can inherit and be inherited|
|Implements interface|✅ Yes|✅ Yes|
|Default constructor allowed|❌ No (except implicit one)|✅ Yes (customizable)|
|Supports finalizers|❌ No|✅ Yes|
|`null` assignment|❌ Not allowed unless nullable (`Point?`)|✅ Yes|
|Performance|✅ Better for small data|❌ More overhead|

---

## 📌 Use Cases

### When to use `struct`:

- Represents **small, immutable** data (like coordinates, colors, ranges).
- You don’t need polymorphism or inheritance.
- You want **high performance** and **low allocation overhead**.

### When to use `class`:

- Represents **large, complex entities** (like users, accounts, services).
- Requires **inheritance**, **polymorphism**, or **reference sharing**.
- Needs to hold **state changes** over time.

---

## 🧪 Real-world Example

### ✅ `struct` for lightweight data

```C#
public struct Color
{
    public byte R, G, B;
    public Color(byte r, byte g, byte b) => (R, G, B) = (r, g, b);
}
```

### ✅ `class` for application model

```C#
public class User
{
    public string Username;
    public List<string> Roles;
}
```

---

## 🧾 Summary Table

|Feature|`struct`|`class`|
|---|---|---|
|Inheritance|❌|✅|
|Performance|✅ Fast (stack-based)|⚠️ Slower (heap + GC)|
|Ideal for|Small data objects|Complex objects|
|Default constructor|❌|✅|
|Reference sharing|❌ Copies by value|✅ Shared by ref|

---

## ⚠️ Gotchas

|Mistake|Why It's a Problem|
|---|---|
|Using struct for large objects|Copies are expensive; performance degrades|
|Modifying struct in foreach loop|Leads to bugs—copy is modified, not original|
|Expecting inheritance in struct|Not supported—no polymorphic behavior|