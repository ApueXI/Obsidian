---
Created: 2025-08-07T20:10
tags:
  - Advance-Concepts
---
**Indexers** allow objects to be indexed like arrays using the `[]` bracket syntax.

They’re a way to define a property that takes one or more parameters.

---

## 🔧 Basic Syntax

```C#
class MyClass
{
    private int[] data = new int[5];

    public int this[int index]
    {
        get { return data[index]; }
        set { data[index] = value; }
    }
}
```

### ✅ Usage

```C#
MyClass obj = new MyClass();
obj[0] = 42;            // Set value
Console.WriteLine(obj[0]);  // Get value → 42
```

---

## 📦 When to Use Indexers

- To make a **collection-like class** easier to use
- Provide **array-like access** to internal data
- Hide internal implementation details while exposing logical indexing

---

## 🔄 Indexer vs Property

|Feature|Property|Indexer|
|---|---|---|
|Named|Yes (`Name`)|No (uses `this`)|
|Indexed|No|Yes (`this[int i]`)|
|Overloaded|Yes|Yes (with parameter types)|
|Used like|`obj.Property`|`obj[index]`|

---

## 📘 Example: Indexer with String Key

```C#
class StudentGrades
{
    private Dictionary<string, double> grades = new();

    public double this[string name]
    {
        get => grades.ContainsKey(name) ? grades[name] : -1;
        set => grades[name] = value;
    }
}
```

### ✅ Usage

```C#
StudentGrades sg = new StudentGrades();
sg["Alice"] = 90.5;
Console.WriteLine(sg["Alice"]); // 90.5
```

---

## 🔁 Overloading Indexers

You can define multiple indexers with different parameter types:

```C#
public string this[int index] => list[index];
public int this[string name] => dict[name];
```

---

## 🔐 Access Modifiers in Indexers

```C#
public int this[int index]
{
    get => data[index];
    private set => data[index] = value;
}
```

> You can give separate access modifiers to get and set.

---

## 🧪 Real-World Example: Matrix

```C#
class Matrix
{
    private int[,] data;

    public Matrix(int rows, int cols)
    {
        data = new int[rows, cols];
    }

    public int this[int row, int col]
    {
        get => data[row, col];
        set => data[row, col] = value;
    }
}
```

---

## ⚠️ Gotchas

|Issue|Tip|
|---|---|
|Index out of range|Add bounds checking|
|Overusing indexers|Use when truly appropriate|
|Default values|Return sentinel values (like `-1` or `null`) for invalid keys|

---

## 📋 Summary Table

|Feature|Description|
|---|---|
|`this[]`|Allows object to act like an array|
|Get/Set|Supports both read and write access|
|Overloading|Indexers can be overloaded|
|Custom key types|Use `string`, `char`, or multiple keys|
|Access control|Use modifiers on get/set individually|