---
Created: 2025-08-07T20:10
tags:
  - OOP
---
## ✅ Concept

The `new` keyword in C# serves **multiple purposes**, depending on the context:

|Purpose|Description|
|---|---|
|**Object creation**|Instantiates objects from classes or structs|
|**Method hiding**|Hides a member (method, property, etc.) of a base class|
|**Type instantiation**|Creates arrays, delegates, anonymous types, etc.|

---

## 🧠 1. Object Creation

```C#
Dog myDog = new Dog();  // Creates a new Dog object
```

- Used with class constructors.
- Can also be used with `struct`, `List<T>`, etc.

---

## 🧠 2. Method Hiding (vs Overriding)

```C#
public class Animal
{
    public void Speak()
    {
        Console.WriteLine("Animal speaks");
    }
}

public class Dog : Animal
{
    public new void Speak()  // Hides Animal.Speak()
    {
        Console.WriteLine("Dog barks");
    }
}
```

- Hides the base class method **instead of overriding it**.
- Base method is still accessible using `base.Speak()` or by casting.

```C#
Animal a = new Dog();
a.Speak();  // Outputs: "Animal speaks" (because it's hidden, not overridden)

Dog d = new Dog();
d.Speak();  // Outputs: "Dog barks"
```

---

## 🧠 3. Use with Types

```C#
int[] numbers = new int[5];          // Array
var anon = new { Name = "Nein" };   // Anonymous type
Action print = new Action(() => {}); // Delegate
```

---

## ⚠️ Gotchas

|Gotcha|Explanation|
|---|---|
|Hidden ≠ overridden|Hidden methods are **not polymorphic**|
|Use `override` for polymorphism|If you want runtime binding, use `virtual` + `override`|
|Signature must match|Hiding a method with a different signature can lead to confusion|

---

## 🧠 Comparison: `new` vs `override`

|Feature|`new`|`override`|
|---|---|---|
|Behavior|Hides base method|Overrides base method|
|Requires base `virtual`?|❌ No|✅ Yes|
|Supports polymorphism?|❌ No (based on reference type)|✅ Yes (based on actual type)|
|Use case|Intentional hiding|Substitution behavior|

---

## 📌 Summary Table

|Keyword Usage|Example|Description|
|---|---|---|
|Object instantiation|`new ClassName()`|Creates a new object|
|Method hiding|`public new void Method()`|Hides inherited method|
|Array declaration|`new int[10]`|Creates a new array|
|Anonymous type|`new { Name = "Alice" }`|Creates a dynamic object|
|Delegate instantiation|`new Action(MyMethod)`|Creates a delegate instance|