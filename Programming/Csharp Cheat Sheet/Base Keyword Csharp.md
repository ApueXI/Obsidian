---
Created: 2025-08-07T20:10
tags:
  - OOP
---
## ✅ Concept

The `**base**` keyword in C# is used within a derived class to:

- Access **members (methods, properties, indexers, constructors)** of the **base (parent) class** that are **hidden or overridden**.
- Call the **base class constructor** from a derived class constructor.

---

## 🧠 Common Uses of `base`

### 1. Calling a base class constructor

```C#
public class Animal
{
    public string Name;
    public Animal(string name)
    {
        Name = name;
    }
}

public class Dog : Animal
{
    public Dog(string name) : base(name)  // Call base constructor
    {
        Console.WriteLine($"Dog named {Name} created.");
    }
}
```

---

### 2. Calling a base class method or property (especially overridden methods)

```C#
public class Animal
{
    public virtual void Speak()
    {
        Console.WriteLine("Animal sound");
    }
}

public class Dog : Animal
{
    public override void Speak()
    {
        base.Speak();  // Calls Animal.Speak()
        Console.WriteLine("Dog barks");
    }
}
```

---

### 3. Accessing base class members hidden by `new` keyword

```C#
public class BaseClass
{
    public void Display()
    {
        Console.WriteLine("Base display");
    }
}

public class DerivedClass : BaseClass
{
    public new void Display()
    {
        Console.WriteLine("Derived display");
    }

    public void ShowBoth()
    {
        Display();        // Calls Derived.Display()
        base.Display();   // Calls BaseClass.Display()
    }
}
```

---

## 📋 Summary Table

|Use Case|Syntax Example|Purpose|
|---|---|---|
|Call base constructor|`public Derived() : base()`|Initialize base part of object|
|Call base method/property|`base.Method()`|Access overridden or hidden member|
|Access base members|`base.Member`|Resolve ambiguity in name hiding|

---

## ⚠️ Notes & Gotchas

- `base` can only be used **inside instance methods or constructors** of derived classes.
- Cannot use `base` in **static** methods.
- If base class method is **not virtual or hidden**, calling it with `base` behaves same as calling normally.
- `base` call in constructor **must appear in the constructor initializer list** (after colon `:`).