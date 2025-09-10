---
Created: 2025-08-07T20:20
tags:
  - Basics-&-Syntax
---
## 📘 Console Input & Output in C#

In C#, **console I/O** is used for interacting with users through text. It’s done via:

- `Console.WriteLine()` → Output with newline
- `Console.Write()` → Output without newline
- `Console.ReadLine()` → Input as **string**

---

## 🔹 1. **Console Output**

### ✅ `Console.WriteLine()`

- Prints output followed by a **newline**.

```C#
Console.WriteLine("Hello, World!");
```

### ✅ `Console.Write()`

- Prints output **without newline**.

```C#
Console.Write("Enter name: ");
```

---

## 🔹 2. **Console Input**

### ✅ `Console.ReadLine()`

- Reads **entire line** as a **string**.

```C#
string name = Console.ReadLine();
```

- Always returns `string` → You must **convert** for other types.

---

## 🔹 3. **Converting Input**

To use user input as `int`, `double`, etc., convert using:

### 🔸 `Convert`:

```C#
int age = Convert.ToInt32(Console.ReadLine());
```

### 🔸 `Parse`:

```C#
double price = double.Parse(Console.ReadLine());
```

### 🔸 `TryParse` (Safe):

```C#
int value;
bool success = int.TryParse(Console.ReadLine(), out value);
```

---

## 🧠 Gotchas

|Issue|Explanation|
|---|---|
|All input is string|Even if user types a number, it’s received as a string|
|`Convert`/`Parse` crash on invalid input|Use `TryParse` to avoid exceptions|
|No built-in prompt support|Must use `Console.Write()` before `ReadLine()`|
|Trimming may be needed|User input may include leading/trailing spaces|

---

## 📋 Summary Table

|Method|Description|Returns|
|---|---|---|
|`Console.Write()`|Writes text (no newline)|void|
|`Console.WriteLine()`|Writes text with newline|void|
|`Console.ReadLine()`|Reads user input from console|`string`|
|`Convert.To<Type>()`|Converts input to numeric type|Typed value|
|`TryParse()`|Safely converts input|`bool` + out|

---

## 🌍 Real-World Example

```C#
using System;

class Program
{
    static void Main()
    {
        Console.Write("Enter your name: ");
        string name = Console.ReadLine();

        Console.Write("Enter your age: ");
        int age = Convert.ToInt32(Console.ReadLine());

        Console.WriteLine($"Hello, {name}! You are {age} years old.");
    }
}
```

### 💬 Output:

```Plain
Enter your name: Alice
Enter your age: 25
Hello, Alice! You are 25 years old.
```

---

## 🔄 Bonus: Multi-Type Input Handling (Safe)

```C#
Console.Write("Enter a number: ");
if (int.TryParse(Console.ReadLine(), out int number))
{
    Console.WriteLine($"Square is: {number * number}");
}
else
{
    Console.WriteLine("Invalid input.");
}
```