---
Created: 2025-08-07T20:10
tags:
  - Methods-(Functions)
---
## ✅ Concept

**Method Overloading** means creating **multiple methods with the same name** but **different parameter lists** (by **type**, **number**, or **order** of parameters).

C# decides **which method to call at compile time** based on the arguments passed.

---

## 🧠 Syntax

```C#
public void Print(string text) { ... }

public void Print(int number) { ... }

public void Print(string text, int count) { ... }
```

---

## 🧩 Valid Overload Differences

|Difference|Example|
|---|---|
|✅ Number of parameters|`Print(string)` vs `Print(string, int)`|
|✅ Parameter types|`Print(int)` vs `Print(string)`|
|✅ Parameter order|`Log(string, int)` vs `Log(int, string)`|

---

## ❌ Not Valid

- ❌ Return type **alone** is **not enough** to overload a method:

```C#
// ❌ Compile error
int Add(int a) { ... }
double Add(int a) { ... }  // Invalid: same signature
```

---

## ⚠️ Common Gotchas

|Gotcha|Explanation|
|---|---|
|❌ Return type doesn’t overload|Changing return type **only** causes a compile error.|
|😵 Ambiguous calls|Too-similar overloads confuse the compiler (`null`, `default`, `optional`).|
|🧱 Overuse hurts readability|Too many overloads = confusing maintenance.|
|🧠 Optional parameters can cause overload ambiguity|Prefer one approach (overload or optional).|

---

## 📋 Quick Reference Table

|Feature|Overloading Allowed?|
|---|---|
|Different parameter **count**|✅ Yes|
|Different parameter **type**|✅ Yes|
|Different parameter **order**|✅ Yes|
|Different **return type only**|❌ No|
|Different **access modifiers**|❌ No (doesn't count as overload)|

---

## 🌍 Real-World Example

```C#
public class Printer
{
    public void Print(string text)
    {
        Console.WriteLine($"Text: {text}");
    }

    public void Print(int number)
    {
        Console.WriteLine($"Number: {number}");
    }

    public void Print(string text, int count)
    {
        for (int i = 0; i < count; i++)
            Console.WriteLine($"#{i + 1}: {text}");
    }
}

// Usage
Printer p = new Printer();
p.Print("Hello");
p.Print(123);
p.Print("Repeat", 3);
```

---

### 🧠 Advanced: Combine with Optional Parameters

```C#
public void Log(string message, int level = 1) { ... }
// Overload example
public void Log(string message, Exception ex) { ... }
```

⚠️ Be careful — optional parameters + overloads can create **ambiguity** if you’re not specific.

---

## ✅ Best Practices

- Use method overloading when methods do **similar tasks** but need different inputs.
- Don’t overdo it—keep overloads **readable** and **clearly distinct**.
- Document overloads clearly, especially in public APIs.