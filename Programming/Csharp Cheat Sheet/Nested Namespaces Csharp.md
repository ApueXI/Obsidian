---
Created: 2025-08-07T20:10
tags:
  - Namespaces
---
## ✅ What Are Nested Namespaces?

Nested namespaces are **namespaces within other namespaces**, used to logically group related classes and avoid naming conflicts in large applications.

---

## 🧱 Classic Declaration (Brace Style)

```C#
namespace Company
{
    namespace Project
    {
        namespace Module
        {
            public class MyClass
            {
                public void Greet() => Console.WriteLine("Hello from nested!");
            }
        }
    }
}
```

---

## ✂️ Simplified Declaration (Dot Style)

The same structure can be written more cleanly:

```C#
namespace Company.Project.Module
{
    public class MyClass
    {
        public void Greet() => Console.WriteLine("Hello from nested!");
    }
}
```

---

## 📄 C# 10+ File-Scoped Namespaces

Introduced in C# 10 for even cleaner syntax — no nesting or braces:

```C#
namespace Company.Project.Module;

public class MyClass
{
    public void Greet() => Console.WriteLine("Hello from file-scoped namespace!");
}
```

> ⚠️ All code in the file belongs to the namespace — no indentation required.

---

## 🧩 Using Nested Namespaces

To use types from a nested namespace:

```C#
using Company.Project.Module;

class Program
{
    static void Main()
    {
        MyClass obj = new MyClass();
        obj.Greet();
    }
}
```

Or use the **fully qualified name**:

```C#
Company.Project.Module.MyClass obj = new Company.Project.Module.MyClass();
```

---

## 🧠 Best Practices

|✅ Do|❌ Avoid|
|---|---|
|Use dot notation for readability|Deep nesting with too many levels|
|Match folders with namespace structure|Mixing unrelated classes in one namespace|
|Use file-scoped namespaces in C# 10+|Multiple nested braces in modern C#|

---

## 📋 Summary Table

|Style|Example|
|---|---|
|Nested braces|`namespace A { namespace B { } }`|
|Dot-style|`namespace A.B.C { ... }`|
|File-scoped (C# 10+)|`namespace A.B.C;`|
|Using nested namespace|`using A.B.C;` or `A.B.C.MyClass obj = ...`|

---

## 🧪 Real-World Example

**File: Services/Email/EmailSender.cs**

```C#
namespace MyApp.Services.Email;

public class EmailSender
{
    public void Send(string to, string subject)
    {
        Console.WriteLine($"Sending email to {to} with subject: {subject}");
    }
}
```

**File: Program.cs**

```C#
using MyApp.Services.Email;

class Program
{
    static void Main()
    {
        var sender = new EmailSender();
        sender.Send("user@example.com", "Welcome!");
    }
}
```