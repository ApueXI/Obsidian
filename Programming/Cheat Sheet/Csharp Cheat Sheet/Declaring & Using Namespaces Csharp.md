---
Created: 2025-08-07T20:10
tags:
  - Namespaces
---
## ✅ What is a Namespace?

- A **namespace** groups related classes, structs, interfaces, enums, and delegates.
- Helps **organize code** logically.
- Prevents **name collisions** in larger projects or when using libraries.

---

## 🧠 Declaring a Namespace

```C#
namespace MyCompany.Project.Module
{
    public class MyClass
    {
        public void SayHello()
        {
            Console.WriteLine("Hello from MyClass");
        }
    }
}
```

- Use dot `.` notation for **nested namespaces**.
- Namespace name typically reflects **company/project/module** structure.

---

## 🧩 Using Namespaces (`using` Directive)

- To access classes in other namespaces, use:

```C#
using MyCompany.Project.Module;

class Program
{
    static void Main()
    {
        MyClass obj = new MyClass();
        obj.SayHello();
    }
}
```

- Place `using` directives at the **top of the file**.

---

## 🧮 Fully Qualified Names

- You can **use types without** `**using**` by specifying full namespace:

```C#
MyCompany.Project.Module.MyClass obj = new MyCompany.Project.Module.MyClass();
```

- Useful to resolve name conflicts.

---

## 🛠️ Nested Namespaces (C# 10+)

- C# 10 supports **file-scoped namespaces** for cleaner syntax:

```C#
namespace MyCompany.Project.Module;

public class MyClass
{
    // Class code here
}
```

Equivalent to the curly-brace form but less indentation.

---

## ⚠️ Tips & Best Practices

- Use **PascalCase** for namespaces.
- Keep namespace names **meaningful and hierarchical**.
- Avoid overly deep nesting.
- Group related classes logically.

---

## 📋 Summary Table

|Action|Syntax/Example|
|---|---|
|Declare namespace|`namespace MyNamespace { ... }`|
|Use namespace|`using MyNamespace;`|
|Fully qualified name|`MyNamespace.MyClass obj = new MyNamespace.MyClass();`|
|File-scoped namespace|`namespace MyNamespace;` (no braces)|

---

## 🧪 Real-World Example

```C#
// File: Utilities.cs
namespace Utils
{
    public static class MathHelper
    {
        public static int Square(int x) => x * x;
    }
}

// File: Program.cs
using Utils;

class Program
{
    static void Main()
    {
        int result = MathHelper.Square(5);
        Console.WriteLine(result); // Output: 25
    }
}
```