---
Created: 2025-08-07T20:10
tags:
  - Struct-vs-Enums
---
## ✅ What is an `enum`?

An `enum` is a **special value type** that lets you define a **set of named constants** (integral values).

Use it to improve **readability**, **type safety**, and **code clarity** when working with a known set of values.

---

## 🧠 Syntax: Defining an Enum

```Csharp
enum Days
{
    Sunday,     // 0
    Monday,     // 1
    Tuesday,    // 2
    Wednesday,  // 3
    Thursday,   // 4
    Friday,     // 5
    Saturday    // 6
}
```

> You can optionally assign custom values:

```Csharp
enum Status
{
    Inactive = 0,
    Active = 1,
    Banned = 10,
    Suspended = 20
}
```

---

## 🚀 Using an Enum

```Csharp
Status userStatus = Status.Active;

if (userStatus == Status.Active)
{
    Console.WriteLine("User is active.");
}
```

---

## 🔄 Convert Enum to Int and Vice Versa

```Csharp
int val = (int)Status.Suspended;      // → 20
Status s = (Status)10;                // → Status.Banned
```

---

## 🧾 Enum with Switch Case

```csharp
void PrintStatus(Status status)
{
    switch (status)
    {
        case Status.Active:
            Console.WriteLine("Active user");
            break;
        case Status.Banned:
            Console.WriteLine("User is banned");
            break;
        default:
            Console.WriteLine("Unknown status");
            break;
    }
}
```

---

## 🛠 Real-world Example

```csharp
enum UserRole
{
    Guest,
    User,
    Admin
}

class User
{
    public string Name;
    public UserRole Role;

    public void PrintRole()
    {
        Console.WriteLine($"{Name} is a {Role}");
    }
}
```

---

## 🧠 Advanced: Enum Flags

Add `[Flags]` to combine enum values with bitwise operators:

```Csharp
[Flags]
enum Permissions
{
    None = 0,
    Read = 1,
    Write = 2,
    Execute = 4
}

// Combine
Permissions p = Permissions.Read | Permissions.Write;

// Check
bool hasWrite = p.HasFlag(Permissions.Write);  // true
```

---

## ⚠️ Gotchas

|Mistake|Why it's a problem|
|---|---|
|Using enums for unknown sets|Enums are for fixed sets, not dynamic values|
|Not using `Flags` for bitwise enums|Bitwise logic fails if not marked with `[Flags]`|
|Casting invalid int to enum|No compile error — runtime logic may break|

---

## 📌 Summary Table

|Feature|Example|Notes|
|---|---|---|
|Declare enum|`enum Color { Red, Green }`|Default starts at 0|
|Set values|`Red = 10`|Custom numeric values|
|Cast to int|`(int)Color.Red`|→ 10|
|Cast from int|`(Color)10`|→ Color.Red|
|Use in switch|`switch(color)`|Cleaner logic|
|Combine values|`[Flags]`|Enables bitwise operations|