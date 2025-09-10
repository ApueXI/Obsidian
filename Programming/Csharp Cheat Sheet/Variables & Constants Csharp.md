---
Created: 2025-08-07T20:20
tags:
  - Basics-&-Syntax
---
### 🔹 1. Variables

Variables are containers for storing data values. In C#, every variable has a **type**, which determines what kind of data it can store.

### 🔸 Syntax:

```C#
<datatype> <variableName> = <value>;
```

### 🔸 Example:

```C#
int age = 25;
string name = "Alice";
double price = 99.99;
```

### 🔸 Rules:

- Must start with a letter or underscore.
- Cannot use C# **keywords** as names (`int`, `class`, `new`, etc.).
- C# is **case-sensitive** (`age` ≠ `Age`).
- Variables **must be initialized** before use.

### 🔸 Common Data Types:

|Type|Description|Example|
|---|---|---|
|`int`|Whole numbers|`int x = 5;`|
|`double`|Decimal numbers|`double pi = 3.14;`|
|`char`|Single character|`char grade = 'A';`|
|`string`|Sequence of characters|`string name = "Bob";`|
|`bool`|Boolean (true/false)|`bool isOnline = true;`|

---

### 🔹 2. Constants

Constants are **immutable** values—once set, they **cannot be changed**.

### 🔸 Syntax:

```C#
const <datatype> <name> = <value>;
```

### 🔸 Example:

```C#
const double Pi = 3.14159;
const int DaysInWeek = 7;
```

### 🔸 Rules:

- Must be initialized **at declaration**.
- Value **cannot** be changed later.
- Usually named in **PascalCase** or **UPPER_CASE** for visibility.

---

### 🔹 3. Readonly (Bonus)

`readonly` is another way to make a variable immutable—but only **after initialization**, usually used with **fields**.

### 🔸 Example:

```C#
readonly int myId;

public MyClass(int id)
{
    myId = id; // Can only assign in constructor
}
```

---

## 🧠 Gotchas to Watch For

|Issue|Explanation|
|---|---|
|Forgetting initialization|Uninitialized variables cause compiler errors|
|Changing const|You **cannot** assign a new value to a `const` after declaration|
|Type mismatch|`int x = "hello";` → Error due to incompatible types|
|Shadowing|Declaring the same variable name in a smaller scope can hide outer variables|

---

## 📋 Quick Reference Table

|Keyword|Purpose|Mutable?|Scope|
|---|---|---|---|
|`var`|Implicit type variable|Yes|Local|
|`<type>`|Explicit type variable|Yes|Local/Global|
|`const`|Constant value|No|Local/Global|
|`readonly`|Immutable after set|No|Field-level|

---

## 🌍 Real-World Example

```C#
using System;

class CoffeeShop
{
    const double CoffeePrice = 2.5;   // constant price
    static void Main()
    {
        string customerName = "Jake";
        int quantity = 3;
        double total = quantity * CoffeePrice;

        Console.WriteLine($"{customerName} bought {quantity} coffees for ${total}.");
    }
}
```

**Output:**

```Plain
Jake bought 3 coffees for $7.5.
```