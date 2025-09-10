---
Created: 2025-08-07T20:10
tags:
  - OOP
---
## ✅ Concept

A **constructor** is a special method in a class that is **called automatically when an object is created**. It **initializes the object’s state**.

---

## 🔄 Types of Constructors in C#

|Constructor Type|Description|Called When?|
|---|---|---|
|Default constructor|No parameters; initializes default values|When creating object without arguments|
|Parameterized constructor|Takes parameters to initialize with specific data|When creating object with arguments|
|Static constructor|Initializes static members of the class|Once, before first instance or static member access|

---

## 🧠 Syntax & Examples

### 1. Default Constructor

- **Provided by compiler** if no constructor is declared.
- You can explicitly define it too.

```C#
public class Person
{
    public string Name;

    public Person()  // Default constructor
    {
        Name = "Unknown";
    }
}

// Usage
Person p = new Person();
Console.WriteLine(p.Name);  // Output: Unknown
```

---

### 2. Parameterized Constructor

- Used to initialize object with custom values.

```C#
public class Person
{
    public string Name;

    public Person(string name)  // Parameterized constructor
    {
        Name = name;
    }
}

// Usage
Person p = new Person("Alice");
Console.WriteLine(p.Name);  // Output: Alice
```

---

### 3. Static Constructor

- Called **once** before any instance or static member is accessed.
- Used to initialize **static fields**.
- Cannot take parameters or access instance members.

```C#
public class Logger
{
    public static DateTime StartTime;

    static Logger()  // Static constructor
    {
        StartTime = DateTime.Now;
        Console.WriteLine("Static constructor called.");
    }

    public Logger()
    {
        Console.WriteLine("Instance constructor called.");
    }
}

// Usage
Console.WriteLine(Logger.StartTime);  // Triggers static constructor first
Logger log = new Logger();             // Then instance constructor
```

---

## 📋 Summary Table

|Constructor Type|Parameters|Can Access Instance Members?|Called Automatically?|
|---|---|---|---|
|Default|None|Yes|Yes (on new instance)|
|Parameterized|Yes|Yes|Yes (on new instance)|
|Static|None|No (only static members)|Yes (once before use)|

---

## ⚠️ Notes & Gotchas

|Gotcha|Explanation|
|---|---|
|Multiple constructors allowed|Use **constructor overloading** to create variants|
|Static constructor can’t be called explicitly|It’s called automatically by the runtime|
|If you declare any constructor, compiler doesn’t create default automatically|You must explicitly declare default constructor if needed|
|Static constructors can’t have access modifiers|Always `private` by design|

---

## 🧠 Bonus: Constructor Overloading Example

```C#
public class Box
{
    public int Length, Width, Height;

    // Default constructor
    public Box()
    {
        Length = Width = Height = 1;
    }

    // Parameterized constructor
    public Box(int l, int w, int h)
    {
        Length = l;
        Width = w;
        Height = h;
    }
}
```