---
Created: 2025-08-07T20:10
tags:
  - OOP
---
## ✅ Concept

**Inheritance** allows a class (called **derived class** or **child class**) to **inherit members (fields, properties, methods) from another class** (called **base class** or **parent class**).

It promotes **code reuse** and **hierarchical relationships**.

---

## 🧠 Syntax

```C#
// Base class
public class Animal
{
    public void Eat()
    {
        Console.WriteLine("Eating");
    }
}

// Derived class
public class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Barking");
    }
}

// Usage
Dog d = new Dog();
d.Eat();  // Inherited from Animal
d.Bark(); // Defined in Dog
```

---

## 📋 Key Points

|Aspect|Description|
|---|---|
|Single inheritance|C# supports **only single class inheritance** (one base class per derived class)|
|`:` symbol|Used to specify inheritance (`class Derived : Base`)|
|`base` keyword|Access members of the base class|
|`virtual` keyword|Allows base method to be overridden|
|`override` keyword|Override a virtual method in derived class|
|`sealed` keyword|Prevents a class from being inherited|
|Constructors|Base class constructors are called automatically (can be called explicitly with `base(...)`)|

---

## 🧩 Example with Override

```C#
public class Animal
{
    public virtual void Speak()
    {
        Console.WriteLine("Animal sound");
    }
}

public class Cat : Animal
{
    public override void Speak()
    {
        Console.WriteLine("Meow");
    }
}
```

---

## 🧱 Limitations & Gotchas

|Gotcha|Explanation|
|---|---|
|No multiple class inheritance|C# does **not** support inheriting from multiple classes (use interfaces instead)|
|Base constructor calls|If base has no parameterless constructor, derived must call base constructor explicitly|
|Access modifiers|Private base members are **not accessible** directly in derived classes|
|Overriding without `virtual`|Methods not marked `virtual` **cannot** be overridden|

---

## 📌 Quick Reference Table

|Keyword|Purpose|
|---|---|
|`: BaseClass`|Specifies inheritance|
|`base.Method()`|Calls base class method|
|`virtual`|Allows overriding in derived class|
|`override`|Overrides base class virtual method|
|`sealed`|Prevents further inheritance|

---

## 🧠 Bonus: Constructor Inheritance

```C#
public class Vehicle
{
    public Vehicle(string brand)
    {
        Console.WriteLine($"Vehicle brand: {brand}");
    }
}

public class Car : Vehicle
{
    public Car(string brand) : base(brand)  // Call base constructor
    {
        Console.WriteLine("Car created");
    }
}
```