---
Created: 2025-08-07T20:10
tags:
  - Methods-(Functions)
---
## ✅ Concept

**Access modifiers** control the **visibility and accessibility** of types (classes, structs, interfaces) and their members (methods, fields, properties, etc.).

They define **who can see or use** the code.

---

## 📋 Common Access Modifiers in C#

|Modifier|Accessibility Scope|Where Allowed|
|---|---|---|
|`public`|Accessible from **anywhere**|Classes, methods, fields, properties, etc.|
|`private`|Accessible **only within the containing class or struct**|Members inside classes/structs|
|`protected`|Accessible **within containing class and derived classes** (inheritance)|Members inside classes|
|`internal`|Accessible **within the same assembly (project)**|Classes, members|
|`protected internal`|Accessible **within the same assembly OR in derived classes**|Members|
|`private protected`|Accessible **within the containing class or derived classes in the same assembly**|Members (since C# 7.2)|

---

## 🧠 Summary Table

|Modifier|Within Class|Derived Class (same assembly)|Derived Class (other assembly)|Same Assembly (non-derived)|Anywhere (other assembly)|
|---|---|---|---|---|---|
|`public`|Yes|Yes|Yes|Yes|Yes|
|`private`|Yes|No|No|No|No|
|`protected`|Yes|Yes|Yes|No|No|
|`internal`|Yes|Yes|No|Yes|No|
|`protected internal`|Yes|Yes|No|Yes|No|
|`private protected`|Yes|Yes|No|No|No|

---

## 🔄 Usage Examples

```C#
csharp
CopyEdit
public class Animal
{
    public string Name;           // Accessible anywhere
    private int age;              // Accessible only within Animal class
    protected string Color;       // Accessible in Animal and subclasses
    internal string Species;      // Accessible within same assembly
    protected internal string Habitat;  // Accessible in subclasses or same assembly
    private protected bool IsWild;       // Accessible in subclasses within same assembly
}

```

---

## ⚠️ Notes and Gotchas

- **Classes** at namespace level can be `public` or `internal` only.
- Members inside **classes** can use all access modifiers.
- **Structs** follow similar rules as classes.
- `private` is **default** for class members if no modifier specified.
- Be careful with `**internal**` if you want to expose your API across assemblies.
- Use `**protected**` to enable inheritance customization.
- `private protected` is **rare** but useful to restrict derived class access within the same assembly.

---

## 🧠 Best Practices

- Use `private` by default for fields to enforce encapsulation.
- Use properties with appropriate access modifiers instead of public fields.
- Use `public` sparingly and intentionally to expose only necessary API.
- Use `internal` for types and members used **only within the project/assembly**.
- Use `protected` and `protected internal` for inheritance scenarios.