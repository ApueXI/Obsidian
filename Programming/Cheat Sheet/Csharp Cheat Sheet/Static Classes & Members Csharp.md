---
Created: 2025-08-07T20:10
tags:
  - OOP
---
## ✅ Concept

- **Static class**: A class that **cannot be instantiated** and can **only contain static members**.
- **Static members**: Belong to the **class itself**, not any object instance.

Use **static** when you need **global functionality or shared state**.

---

## 🧠 Syntax

### Static Class

```C#
public static class MathHelper
{
    public static double Square(double x) => x * x;
}
```

```C#
double result = MathHelper.Square(5);  // No need to create an object
```

---

### Static Member in Non-static Class

```C#
public class Counter
{
    public static int TotalCount = 0;

    public Counter() => TotalCount++;
}
```

```C#
Counter c1 = new Counter();
Counter c2 = new Counter();
Console.WriteLine(Counter.TotalCount);  // Output: 2
```

---

## 📌 Rules of Static Classes

|Rule|Applies?|
|---|---|
|Cannot be instantiated|✅|
|Cannot inherit from or be inherited by others|✅|
|Can only contain static members|✅|
|Cannot have constructors (except static ones)|✅|

---

## 📌 Rules of Static Members

|Rule|Applies?|
|---|---|
|Belong to the class itself|✅|
|Shared across all instances|✅|
|Can be called using `ClassName.Member`|✅|
|Accessed without an object|✅|

---

## ✅ Real-world Examples

### Utility Class

```C#
public static class StringUtils
{
    public static bool IsEmpty(string str) => string.IsNullOrEmpty(str);
}
```

### Shared Counter

```C#
public class User
{
    public static int Count = 0;
    public User() => Count++;
}
```

### Static Constructor

```C#
public class Database
{
    static Database()
    {
        Console.WriteLine("Connecting to DB...");
    }

    public static void Query(string sql)
    {
        Console.WriteLine($"Querying: {sql}");
    }
}
```

> Static constructors are called once before any static member is accessed.

---

## 🔐 Access Modifiers

- Static classes and members follow the same access modifiers: `public`, `private`, `internal`, etc.

---

## 🧠 Static vs Instance

|Feature|Static|Instance|
|---|---|---|
|Bound to class|✅ Yes|❌ No (bound to object)|
|Can be inherited|❌ No|✅ Yes|
|Requires instantiation|❌ No|✅ Yes|
|Shared state|✅ Yes|❌ No (unique per instance)|

---

## ⚠️ Gotchas

|Mistake|Why it's a problem|
|---|---|
|Trying to instantiate static class|Compile-time error|
|Using instance members in static class|Not allowed — all members must be static|
|Forgetting thread safety in static data|Can cause bugs in concurrent environments|

---

## 🧠 When to Use Static

- Utility/helper methods (e.g., `Math`, `Convert`, `Path`)
- Global configuration or constants
- Singleton-like patterns (careful with state)
- Extension methods containers

---

## 🧪 Example of Static + Instance

```C#
public class Account
{
    public static double InterestRate = 0.05; // Shared
    public double Balance;                    // Per instance

    public double CalculateInterest() => Balance * InterestRate;
}
```

---

## 🧾 Summary Table

|Keyword|Purpose|
|---|---|
|`static class`|Prevents instantiation and inheritance|
|`static`|Defines a member that belongs to the class, not the instance|
|`static constructor`|Initializes static members once before use|