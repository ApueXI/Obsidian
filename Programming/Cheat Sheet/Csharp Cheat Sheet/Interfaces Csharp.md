---
Created: 2025-08-07T20:10
tags:
  - OOP
---
## ✅ Concept

An **interface** defines a **contract** — a set of method and property signatures that implementing classes **must fulfill**, but without **any implementation** (prior to C# 8.0).

Think of an interface as a **blueprint** that multiple unrelated classes can follow.

---

## 🧠 Syntax

### Interface Declaration

```C#
public interface IShape
{
    double Area();
    void Draw();
}
```

### Class Implementation

```C#
public class Circle : IShape
{
    public double Radius { get; set; }

    public Circle(double radius) => Radius = radius;

    public double Area() => Math.PI * Radius * Radius;

    public void Draw() => Console.WriteLine("Drawing Circle");
}
```

---

## 🔁 Multiple Interface Implementation

```C#
public interface IMovable
{
    void Move();
}

public interface IDrawable
{
    void Draw();
}

public class Player : IMovable, IDrawable
{
    public void Move() => Console.WriteLine("Player moves");
    public void Draw() => Console.WriteLine("Player drawn");
}
```

✅ **C# supports multiple interfaces** — unlike classes (which only allow single inheritance).

---

## 🧩 Interface Characteristics

|Feature|Description|
|---|---|
|Cannot contain fields|Only method/property signatures|
|No access modifiers|All members are **implicitly public**|
|Cannot be instantiated|Must be implemented by a class or struct|
|Can inherit from other interfaces|Supports multiple interface inheritance|
|C# 8+ default methods|Supports default implementations in interfaces (optional)|

---

## ✅ Real-world Use Case

```C#
public interface ILogger
{
    void Log(string message);
}

public class ConsoleLogger : ILogger
{
    public void Log(string message)
    {
        Console.WriteLine("Log: " + message);
    }
}

public class App
{
    private readonly ILogger _logger;

    public App(ILogger logger) => _logger = logger;

    public void Run()
    {
        _logger.Log("Application started.");
    }
}
```

> This promotes loose coupling and makes it easy to swap loggers (e.g., to a file, database, or cloud logger).

---

## 🔐 Interface Access

All members are:

- **Implicitly public**
- **Cannot be protected/private/internal**
- You cannot use access modifiers inside interfaces.

---

## ⚠️ Gotchas

|Gotcha|Explanation|
|---|---|
|Must implement **all** members|Unless the class is also abstract|
|Can’t have method bodies (pre-C# 8)|Only signatures allowed|
|No fields allowed|Only properties, methods, events, indexers|
|Interface methods are always virtual|No need to declare `virtual`/`override`|

---

## 🧠 Interface vs Abstract Class

|Feature|Interface|Abstract Class|
|---|---|---|
|Inheritance|Multiple|Single|
|Fields|❌ Not allowed|✅ Allowed|
|Default Implementation|❌ (before C# 8) / ✅ (C# 8+)|✅ Yes|
|Constructors|❌ No|✅ Yes|
|Use when...|You need behavior **contracts**|You need shared **code & logic**|

---

## 📌 Quick Summary Table

|Keyword|Purpose|
|---|---|
|`interface`|Declares a contract (method/property signatures)|
|`:`|Used to **implement** or **inherit** interfaces|
|`implements`|(Java only) In C#, use `:` instead|

---

## 🧪 Example: Interface Polymorphism

```C#
IShape shape = new Circle(5);
shape.Draw();           // Outputs: Drawing Circle
Console.WriteLine(shape.Area());  // Polymorphism in action!
```

You can treat **different types** that implement `IShape` the **same way** — this is runtime polymorphism through interfaces.