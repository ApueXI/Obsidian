---
Created: 2025-08-07T20:20
tags:
  - Basics-&-Syntax
---
## 🔹 1. **Value Types**

Stored **directly in memory**, usually on the **stack**.

### 🔸 Common Value Types:

|Type|Size|Range/Example|Usage|
|---|---|---|---|
|`int`|4 bytes|-2,147,483,648 to 2,147,483,647|Whole numbers|
|`float`|4 bytes|±1.5e−45 to ±3.4e38 (7 digits)|Approximate decimals|
|`double`|8 bytes|±5.0e−324 to ±1.7e308 (15–16 digits)|Precise decimals|
|`decimal`|16 bytes|±1.0e−28 to ±7.9e28 (28–29 digits)|Money/financial calc|
|`bool`|1 byte|`true` or `false`|Logical conditions|
|`char`|2 bytes|Single character (`'A'`, `'9'`)|Single Unicode characters|
|`byte`|1 byte|0 to 255|Small unsigned numbers|
|`short`|2 bytes|-32,768 to 32,767|Small integers|
|`long`|8 bytes|Very large integers|Large numbers|

---

## 🔹 2. **Reference Types**

Store **references (pointers)** to actual data, usually stored in the **heap**.

### 🔸 Common Reference Types:

|Type|Description|Example|
|---|---|---|
|`string`|Sequence of characters|`"Hello"`|
|`object`|Base type for all types in C#|Can hold any data|
|`dynamic`|Type determined at runtime|Flexible, less safe|
|`array`|Collection of elements of same type|`int[] arr = {1,2,3};`|
|`class`, `interface`, `delegate`|Custom or advanced types|-|

---

## 🔹 3. **Type Inference (**`**var**`**)**

Let the compiler **infer the type** based on the assigned value.

```C#
var age = 30;         // Treated as int
var name = "Alice";   // Treated as string
```

> 🔐 Still strongly-typed—type is fixed at compile time.

---

## 🔹 4. **Nullable Types**

Allow value types to store `null`.

```C#
csharp
CopyEdit
int? age = null;
bool? isOnline = true;

```

Useful in databases or optional values.

---

## 🧠 Gotchas

|Issue|Explanation|
|---|---|
|`float` requires `f`|`float x = 3.14;` → Error → Use `3.14f`|
|`decimal` needs `m`|`decimal price = 9.99;` → Use `9.99m`|
|`char` uses `' '` not `"`|`char c = "A";` → Error → use `'A'`|
|`string` is immutable|You can’t change characters directly|
|`dynamic` bypasses compile-time checks|Use with care|

---

## 📋 Summary Table

|Category|Type Examples|Notes|
|---|---|---|
|Value Types|`int`, `bool`, `char`, `double`|Stored in stack, fast access|
|Reference Types|`string`, `object`, `array`|Stored in heap, more flexible|
|Inferred|`var`|Compiler infers type|
|Nullable|`int?`, `bool?`|Allows null in value types|

---

## 🌍 Real-World Example

```C#
using System;

class Program
{
    static void Main()
    {
        string name = "John";
        int age = 28;
        double salary = 55000.75;
        bool isEmployed = true;
        char grade = 'A';

        Console.WriteLine($"{name}, Age: {age}, Salary: {salary}, Grade: {grade}, Employed: {isEmployed}");
    }
}
```

**Output:**

```Plain
John, Age: 28, Salary: 55000.75, Grade: A, Employed: True
```