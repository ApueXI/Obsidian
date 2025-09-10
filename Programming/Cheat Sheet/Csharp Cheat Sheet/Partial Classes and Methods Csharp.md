---
Created: 2025-08-07T20:10
tags:
  - Advance-Concepts
---
## ✅ What Are Partial Classes?

- Allow **splitting the definition** of a class across **multiple files** or locations.
- Useful for **large classes**, **auto-generated code**, or **collaborative work**.
- At compile time, all parts are combined into one class.

---

## 🔧 Partial Class Syntax

```C#
// File1.cs
public partial class MyClass
{
    public void MethodA() { Console.WriteLine("Method A"); }
}

// File2.cs
public partial class MyClass
{
    public void MethodB() { Console.WriteLine("Method B"); }
}
```

### Usage

```C#
var obj = new MyClass();
obj.MethodA();  // Output: Method A
obj.MethodB();  // Output: Method B
```

---

## ✅ What Are Partial Methods?

- A **partial method** is a method **declared in one part** of a partial class and **optionally implemented** in another.
- If **not implemented**, compiler removes the method call and declaration — no performance hit.
- Partial methods **must return void** and are implicitly `private`.

---

## 🔧 Partial Method Syntax

```C#
public partial class MyClass
{
    partial void OnSomethingHappened();

    public void Trigger()
    {
        OnSomethingHappened();  // Call partial method
    }
}
```

```C#
// In another file or part
public partial class MyClass
{
    partial void OnSomethingHappened()
    {
        Console.WriteLine("Something happened!");
    }
}
```

---

## ⚠️ Rules for Partial Methods

|Rule|Details|
|---|---|
|Must return `void`|No return values allowed|
|Must be `private`|Cannot have access modifiers|
|Can have `ref` but not `out`|Parameters allowed, but no `out`|
|Implementation is optional|If not implemented, compiler removes it|
|Cannot be virtual or abstract|Partial methods are private implementation details|

---

## 🧩 Use Cases

- **Auto-generated code** (e.g., designer files) where you add your code without modifying generated files.
- Define **hooks** or **callbacks** in partial classes that can optionally be implemented.
- Split large classes cleanly.

---

## 📋 Summary Table

|Feature|Partial Classes|Partial Methods|
|---|---|---|
|Defined across files|Yes|Declared in one part, optionally implemented|
|Access modifiers|Must match across parts|Always private, no access modifiers|
|Return type|Any|Void only|
|Implementation|All parts combined at compile time|Optional implementation, else removed|
|Usage|Organize large or generated code|Optional hooks or callbacks|