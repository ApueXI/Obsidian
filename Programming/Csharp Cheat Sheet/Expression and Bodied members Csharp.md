---
Created: 2025-08-07T20:10
tags:
  - Advance-Concepts
---
### ✅ What is an Expression-Bodied Member?

It’s a shorthand **syntax for members** (like methods, properties, constructors, etc.) that contain **a single expression**.

🔹 Uses the `=>` (lambda-style) syntax

🔹 Introduced in **C# 6**, expanded in later versions

---

## 🧱 General Syntax

```C#
// For methods, properties, etc.
returnType MemberName(parameters) => expression;
```

It’s functionally identical to:

```C#
returnType MemberName(parameters) { return expression; }
```

---

## 🧪 Where You Can Use Expression-Bodied Members

|Member Type|Syntax Example|
|---|---|
|Method|`int Square(int x) => x * x;`|
|Property (getter)|`string Name => _name;`|
|Property (set/get)|`string FullName => $"{First} {Last}";`|
|Constructor|`public Person(string name) => Name = name;`|
|Destructor|`~Person() => Console.WriteLine("Destroyed");`|
|Indexer|`string this[int i] => items[i];`|
|Operator|`public static MyClass operator +(MyClass a, MyClass b) => new MyClass(...);`|

---

## ✅ Method Example

```C#
public int Add(int x, int y) => x + y;
```

Instead of:

```C#
public int Add(int x, int y) {
    return x + y;
}
```

---

## ✅ Property Example

```C#
public string Name => "Nein Neutral";
```

With backing field:

```C#
private string _title;
public string Title => _title;
```

---

## ✅ Constructor Example

```C#
public Person(string name) => Name = name;
```

---

## ✅ Expression-Bodied Setters (C# 7.0+)

```C#
private string _name;
public string Name
{
    get => _name;
    set => _name = value;
}
```

---

## ✅ Indexer Example

```C#
public int this[int i] => data[i];
```

---

## ✅ Operator Overload

```C#
public static Point operator +(Point a, Point b) => new Point(a.X + b.X, a.Y + b.Y);
```

---

## ⚠️ Gotchas

|Issue|Notes|
|---|---|
|Only for **single expressions**|Can't be used for multi-statement logic|
|Not ideal for complex logic|Use full block syntax for clarity|
|Sometimes less readable|Especially for long expressions or with nested logic|

---

## 📋 Summary Table

|Target|Expression-Bodied Syntax|
|---|---|
|Method|`int GetAge() => 25;`|
|Property (get)|`string Title => "C# Guide";`|
|Property (get/set)|`get => value; set => field = value;`|
|Constructor|`public MyClass(string x) => this.X = x;`|
|Destructor|`~MyClass() => Console.WriteLine("Bye");`|
|Indexer|`this[int i] => items[i];`|

---

## ✅ When to Use Expression-Bodied Members

- Short, simple logic (e.g., calculations, accessors)
- When aiming for **clean, readable code**
- Great for **data models**, **utility functions**