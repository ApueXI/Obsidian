---
Created: 2025-08-07T20:10
tags:
  - OOP
---
## ✅ Concept

**Method Overriding** allows a **derived class** to provide a **new implementation** for a method **defined in the base class**.

- The base method must be marked as `virtual`, `abstract`, or `override`.
- The derived method uses the `override` keyword.
- Enables **runtime polymorphism** — the method called depends on the object’s actual type, not the reference type.

---

## 🧠 Syntax

```C#
public class BaseClass
{
    public virtual void Show()
    {
        Console.WriteLine("Base show");
    }
}

public class DerivedClass : BaseClass
{
    public override void Show()
    {
        Console.WriteLine("Derived show");
    }
}
```

---

## 📋 Key Rules

|Rule|Explanation|
|---|---|
|Base method must be `virtual`, `abstract`, or already `override`|Only those methods can be overridden.|
|Derived method must use `override` keyword|Explicitly marks the method as overriding.|
|Signature must match exactly|Same name, return type, and parameters.|
|Can call base method with `base.MethodName()`|Allows reusing base functionality.|
|Overriding is **runtime polymorphism**|Method called depends on the actual object's type.|

---

## 🧩 Example

```C#
public class Animal
{
    public virtual void Speak()
    {
        Console.WriteLine("Animal makes a sound");
    }
}

public class Dog : Animal
{
    public override void Speak()
    {
        Console.WriteLine("Dog barks");
    }
}

Animal a = new Dog();
a.Speak();  // Output: Dog barks (runtime polymorphism)
```

---

## ⚠️ Gotchas

|Gotcha|Explanation|
|---|---|
|Forgetting `virtual` in base|Derived class cannot override non-virtual methods.|
|Using `new` keyword instead|`new` hides the base method instead of overriding it (not polymorphic).|
|Signature mismatch|Causes compile error or method hiding instead of overriding.|
|Overriding sealed methods|`sealed` methods cannot be overridden further.|

---

## 🧠 Bonus: Calling Base Method

```C#
public override void Speak()
{
    base.Speak();   // Call base implementation
    Console.WriteLine("Dog barks");
}
```

---

## 📌 Quick Reference Summary

|Keyword|Purpose|
|---|---|
|`virtual`|Marks base method overridable|
|`override`|Implements overriding in derived class|
|`new`|Hides base method (not polymorphic)|
|`sealed override`|Prevents further overriding|