---
Created: 2025-08-07T20:10
tags:
  - OOP
---
## ✅ Concept

- A **class** is a blueprint/template that defines **data (fields/properties)** and **behavior (methods)**.
- An **object** is an **instance** of a class — an actual entity with data.
- Classes enable **Object-Oriented Programming (OOP)**: encapsulation, abstraction, inheritance, and polymorphism.

---

## 🧠 Syntax

### Class Declaration

```C#
[access_modifier] class ClassName
{
    // Fields (variables)
    private int age;

    // Properties
    public string Name { get; set; }

    // Constructor
    public ClassName(string name, int age)
    {
        Name = name;
        this.age = age;
    }

    // Methods
    public void Greet()
    {
        Console.WriteLine($"Hello, my name is {Name} and I am {age} years old.");
    }
}
```

---

### Creating Objects (Instantiation)

```C#
ClassName obj = new ClassName("Alice", 30);
obj.Greet();  // Output: Hello, my name is Alice and I am 30 years old.
```

---

## 🔄 Key Concepts

|Concept|Description|
|---|---|
|Fields|Variables inside class holding data|
|Properties|Encapsulated fields with getters/setters|
|Constructor|Special method to initialize objects|
|Methods|Functions inside classes to define behavior|
|Access Modifiers|Control visibility (`public`, `private`, etc.)|
|`this` keyword|Refers to current object instance|

---

## 📋 Members Overview

|Member Type|Example|Purpose|
|---|---|---|
|Field|`private int age;`|Store object data|
|Property|`public string Name {get; set;}`|Encapsulate data with control|
|Constructor|`public Person(string n) {...}`|Initialize object state|
|Method|`public void Speak() {...}`|Define object behavior|

---

## 🧩 Real-World Example: Simple Class

```C#
public class Car
{
    public string Make { get; set; }
    public int Year { get; set; }

    public Car(string make, int year)
    {
        Make = make;
        Year = year;
    }

    public void DisplayInfo()
    {
        Console.WriteLine($"Car: {Make}, Year: {Year}");
    }
}

// Usage
Car myCar = new Car("Toyota", 2020);
myCar.DisplayInfo();
```

---

## ⚠️ Common Gotchas

|Gotcha|Explanation|
|---|---|
|Forgetting `new`|Must instantiate objects with `new` keyword|
|Not initializing fields|Uninitialized fields get default values|
|Access modifiers|Private members aren’t accessible outside class|
|No constructor|Compiler provides a default parameterless one|

---

## 🧠 Bonus: Object Initializer Syntax

You can create and initialize objects more succinctly:

```C#
Car myCar = new Car("Honda", 2019)
{
    Make = "Honda",
    Year = 2019
};
```