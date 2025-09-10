---
Created: 2025-08-07T20:10
tags:
  - OOP
---
## ✅ Concept

**Polymorphism** (Greek: _"many forms"_) allows **different classes to define methods with the same name**, and lets you **interact with objects through a common interface**, with behavior determined at runtime or compile time.

---

## 🧠 Types of Polymorphism

|Type|Description|Keywords/Mechanism|
|---|---|---|
|**Compile-time (Static)**|Same method name with different **signatures**|Method Overloading|
|**Runtime (Dynamic)**|Method call determined by **object type at runtime**|Virtual + Override|

---

## 🧩 Compile-time Polymorphism (Method Overloading)

```C#
public class Calculator
{
    public int Add(int a, int b) => a + b;
    public double Add(double a, double b) => a + b;
}
```

- Resolved at compile time.
- No `virtual` or `override` needed.
- **Same method name, different parameters**.

---

## 🧩 Runtime Polymorphism (Method Overriding)

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
        Console.WriteLine("Dog barks");
    }
}

Animal a = new Dog();
a.Speak();  // Outputs: "Dog barks"
```

- Uses `virtual` in the base class.
- Uses `override` in the derived class.
- Decision made at **runtime**.

---

## 📌 Summary Table

|Feature|Compile-time|Runtime|
|---|---|---|
|Also called|Method Overloading|Method Overriding|
|Decision made at|Compile Time|Run Time|
|Keywords used|None|`virtual`, `override`|
|Signature|Must be **different**|Must be **same**|
|Return type|Can differ|Must match|
|Supports polymorphism|No|Yes|

---

## ⚠️ Gotchas

|Gotcha|Explanation|
|---|---|
|Forgetting `virtual`|Prevents overriding — leads to method hiding|
|Using `new` instead of `override`|Hides method — no polymorphism|
|Constructor behavior|Constructors **cannot be polymorphic**|
|Polymorphism needs base reference|Works when you use the **base type to refer to derived objects**|

---

## 🌍 Real-World Example

```C#
List<Animal> animals = new List<Animal>
{
    new Dog(),
    new Cat(),
    new Bird()
};

foreach (Animal a in animals)
{
    a.Speak();  // Each speaks differently via overridden method
}
```

### Output:

```Plain
Dog barks
Cat meows
Bird tweets
```

---

## 🔁 Polymorphism With Interfaces

```C#
interface IShape
{
    void Draw();
}

class Circle : IShape
{
    public void Draw() => Console.WriteLine("Drawing Circle");
}

class Square : IShape
{
    public void Draw() => Console.WriteLine("Drawing Square");
}

void Render(IShape shape)
{
    shape.Draw();  // Polymorphic behavior
}
```

---

## 💡 When to Use Polymorphism

- You want **one interface, multiple behaviors**.
- You’re designing **extensible, modular, or testable** code.
- You need **runtime flexibility**.