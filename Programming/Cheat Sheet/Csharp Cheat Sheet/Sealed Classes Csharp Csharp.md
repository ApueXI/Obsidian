---
Created: 2025-08-07T20:10
tags:
  - OOP
---
## ✅ Concept

A **sealed class** is a class that **cannot be inherited**.

- Useful when you want to **prevent further extension or modification**.
- Improves **security**, **performance**, and **code clarity**.

---

## 🧠 Syntax

```C#
public sealed class FinalLogger
{
    public void Log(string message)
    {
        Console.WriteLine($"Log: {message}");
    }
}
```

### ❌ Attempting to Inherit Will Fail:

```C#
public class ExtendedLogger : FinalLogger
{
    // Error: cannot derive from sealed type
}
```

---

## 📌 When to Use `sealed`

|Scenario|Why Use `sealed`?|
|---|---|
|Security|Prevent sensitive logic from being overridden|
|Performance|Allows the JIT compiler to optimize method calls|
|Design Finality|Enforce a class as final (similar to Java's `final`)|
|Prevent misuse of base class|Protect core behavior from being accidentally changed|

---

## 🔁 Sealed Methods in Inheritance

You can seal **individual methods** in a derived class to prevent further overriding:

```C#
public class Parent
{
    public virtual void Print() => Console.WriteLine("Parent");
}

public class Child : Parent
{
    public sealed override void Print() => Console.WriteLine("Child");
}

public class GrandChild : Child
{
    // public override void Print() {} ❌ Not allowed — sealed in Child
}
```

---

## 📋 Summary Table

|Feature|Sealed Class|Sealed Method|
|---|---|---|
|Prevents Inheritance|✅ Entire class|✅ Method only|
|Use with `override`|❌ Not applicable|✅ Use with `sealed override`|
|Improves performance|✅ Allows better JIT optimization|✅ When method dispatch is known|

---

## 🔐 Sealed vs Abstract

|Feature|`sealed`|`abstract`|
|---|---|---|
|Can be inherited?|❌ No|✅ Yes|
|Can be instantiated?|✅ Yes|❌ No|
|Purpose|Prevent extension|Force extension and implementation|
|Can contain logic?|✅ Yes|✅ Partial (abstract + concrete)|

---

## 🧪 Real-world Use Case

```C#
public sealed class AppConfig
{
    public static string GetSetting(string key) => "value";
}
```

- Prevents unwanted modification or extension of critical config logic.

---

## ⚠️ Gotchas

|Mistake|Problem|
|---|---|
|Trying to inherit a sealed class|Compile-time error|
|Sealing base class too early|Prevents future extensibility (design dead-end)|
|Not using `sealed` when needed|Leaves class open to modification when it shouldn’t be|

---

## ✅ Best Practices

- Use `sealed` for **utility classes**, **core services**, or **configuration handlers**.
- Seal classes that are **not designed to be extended**.
- Don’t seal classes **too early** — it restricts flexibility.