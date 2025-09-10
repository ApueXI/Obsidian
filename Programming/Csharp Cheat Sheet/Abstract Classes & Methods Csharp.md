---
Created: 2025-08-07T20:10
tags:
  - OOP
---
## ✅ Concept

- An **abstract class** is a class that **cannot be instantiated** and is meant to be **inherited**.
- An **abstract method** is a method with **no body** that **must be overridden** in derived classes.
- Abstract classes can contain **both abstract and non-abstract members**.

---

## 🧠 Syntax

### Abstract Class

```C#
public abstract class Animal
{
    public abstract void Speak();   // Must be overridden

    public void Eat()               // Concrete method
    {
        Console.WriteLine("Animal is eating");
    }
}
```

### Derived Class

```C#
public class Dog : Animal
{
    public override void Speak()
    {
        Console.WriteLine("Dog barks");
    }
}
```

---

## 🧩 Abstract Method Rules

|Rule|Description|
|---|---|
|Must be declared inside abstract class|You **cannot** have abstract methods in non-abstract classes|
|Cannot have a method body|`abstract void Speak();` — no braces `{}`|
|Must be overridden in derived class|Otherwise it’s a compile error|
|Can be `public`, `protected`, etc.|But cannot be `private` or `static`|

---

## 📋 Abstract vs Concrete Class

|Feature|Abstract Class|Concrete Class|
|---|---|---|
|Can be instantiated|❌ No|✅ Yes|
|Can have fields|✅ Yes|✅ Yes|
|Can have constructors|✅ Yes|✅ Yes|
|Can contain abstract methods|✅ Yes|❌ No|
|Can contain full methods|✅ Yes|✅ Yes|

---

## ✅ Real-world Example

```C#
public abstract class Shape
{
    public abstract double Area();
}

public class Circle : Shape
{
    public double Radius { get; set; }

    public Circle(double radius) => Radius = radius;

    public override double Area() => Math.PI * Radius * Radius;
}
```

```C#
Shape s = new Circle(5);
Console.WriteLine(s.Area());  // Output: 78.5398...
```

---

## 🔐 Access Modifiers

Abstract methods:

- Cannot be `private` (must be visible to derived class).
- Can be `protected` or `public`.

```C#
protected abstract void Calculate(); // OK
```

---

## 🚫 Gotchas

|Gotcha|Why it matters|
|---|---|
|You can’t `new` an abstract class|It's meant only to be inherited|
|Constructors run on base first|Even in abstract classes, constructors are executed|
|Can’t be `sealed` and `abstract`|Sealed classes can’t be inherited|
|Must override all abstract methods|Even indirectly, through intermediate derived classes|

---

## ✅ Use Cases

- When you want to **force derived classes** to implement specific behavior (like a contract).
- When you have **shared implementation** (non-abstract methods) and **enforced behavior** (abstract methods).
- Common in **frameworks**, **template method patterns**, or **base entity models**.

---

## 🔁 Abstract Class vs Interface

|Feature|Abstract Class|Interface|
|---|---|---|
|Inheritance|Single|Multiple (via interface chaining)|
|Members|Fields, methods, etc.|Methods, properties, events (no fields)|
|Implementation|Can provide some|Must provide none (pre-C# 8)|
|Instantiation|Cannot be instantiated|Cannot be instantiated|

---

## 🧠 Quick Summary Table

|Keyword|Purpose|
|---|---|
|`abstract class`|Defines a base class with incomplete implementation|
|`abstract method`|Declares a method to be implemented by subclasses|
|`override`|Implements abstract method in derived class|