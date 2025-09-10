---
Created: 2025-08-07T20:10
tags:
  - OOP
---
## ✅ Concept Overview

- **Fields**: Variables declared directly in a class to store data. Usually **private** to enforce encapsulation.
- **Properties**: Provide controlled access to fields via **getters** and **setters**. They enable validation, lazy loading, or other logic during data access or assignment.

---

## 🧠 Syntax

### 1. Fields

```C#
public class Person
{
    private string name;  // Field
}
```

- Usually marked `private` to **hide data** from outside.
- Holds the actual data.

---

### 2. Properties (Auto-Implemented)

```C#
public class Person
{
    public string Name { get; set; }  // Property
}
```

- Simplifies encapsulation.
- Compiler creates a hidden backing field automatically.

---

### 3. Properties with Custom Logic

```C#
private int age;

public int Age
{
    get { return age; }
    set
    {
        if (value < 0) throw new ArgumentException("Age cannot be negative");
        age = value;
    }
}
```

- You can add validation or extra behavior on get/set.

---

## 🔄 Differences at a Glance

|Feature|Field|Property|
|---|---|---|
|Accessibility|Usually `private`|Usually `public`|
|Encapsulation|No control over access|Control via getters/setters|
|Syntax|Simple variable|Methods behind the scenes|
|Validation|Not possible directly|Possible via setters|
|Binding Support|No|Supports data binding|
|Auto-Implemented|No|Yes (shortcut)|

---

## 📋 Usage Guidelines

|When to Use|Recommendation|
|---|---|
|Simple, internal data storage|Use **private fields**|
|Public data exposure|Use **properties**|
|Need validation on setting|Use **custom property setter**|
|Read-only or write-only data|Use **get-only** or **set-only** properties|

---

## 🌍 Real-World Example

```C#
public class Employee
{
    private decimal salary;  // Field

    public decimal Salary   // Property with validation
    {
        get { return salary; }
        set
        {
            if (value < 0)
                throw new ArgumentOutOfRangeException("Salary cannot be negative");
            salary = value;
        }
    }

    public string Name { get; set; }  // Auto-implemented property
}
```

---

## 🧠 Extra: Read-Only and Write-Only Properties

### Read-Only

```C#
public string Id { get; }  // Can only get, set in constructor or initializer
```

### Write-Only

```C#
private string password;

public string Password
{
    set { password = value; }
}
```

---

## ⚠️ Gotchas

|Gotcha|Explanation|
|---|---|
|Exposing fields publicly|Breaks encapsulation, not recommended|
|Forgetting validation|Can allow invalid states|
|Auto-properties hiding logic|Need explicit properties if logic required|