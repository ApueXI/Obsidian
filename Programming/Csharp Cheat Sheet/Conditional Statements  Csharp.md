---
Created: 2025-08-07T20:10
tags:
  - Control-Flow
---
## 🔹 1. `**if**` **Statement**

### 🔸 Syntax:

```C#
if (condition)
{
    // Code runs if condition is true
}
```

### 🔸 Example:

```C#
if (age >= 18)
{
    Console.WriteLine("You can vote.");
}
```

---

## 🔹 2. `**if-else**` **Statement**

### 🔸 Syntax:

```C#
if (condition)
{
    // If true
}
else
{
    // If false
}
```

### 🔸 Example:

```C#
if (isLoggedIn)
{
    Console.WriteLine("Welcome back!");
}
else
{
    Console.WriteLine("Please log in.");
}
```

---

## 🔹 3. `**else if**` **Ladder**

Use when testing **multiple exclusive conditions**.

### 🔸 Syntax:

```C#
if (score >= 90)
{
    Console.WriteLine("A");
}
else if (score >= 80)
{
    Console.WriteLine("B");
}
else
{
    Console.WriteLine("F");
}
```

---

## 🔹 4. **Ternary Operator (**`**? :**`**)**

Short form of `if-else` (one-line condition).

### 🔸 Syntax:

```C#
condition ? result_if_true : result_if_false;
```

### 🔸 Example:

```C#
string result = (age >= 18) ? "Adult" : "Minor";
```

---

## 🔹 5. `**switch**` **Statement**

Efficient alternative to long `if-else if` chains for **discrete values** (like `int`, `char`, `string`).

### 🔸 Syntax:

```C#
switch (day)
{
    case "Monday":
        Console.WriteLine("Start of week");
        break;
    case "Friday":
        Console.WriteLine("End of week");
        break;
    default:
        Console.WriteLine("Midweek");
        break;
}
```

---

## 🧠 Gotchas

|Issue|Explanation|
|---|---|
|No `break` in switch|Will "fall through" to next case (unless using C# 8+ with switch expressions)|
|`==` vs `=`|Always use `==` for comparison, not assignment|
|Nesting too deeply|Makes code hard to read — consider switch or early returns|
|`if (condition = true)`|Assignment instead of comparison — logic bug!|

---

## 📋 Summary Table

|Keyword|Use Case|Notes|
|---|---|---|
|`if`|Single condition|Executes if true|
|`if-else`|True/false choice|Only one block runs|
|`else if`|Multiple branches|Ordered, exclusive checks|
|`switch`|Many discrete values|Faster than many ifs; must `break`|
|`? :`|One-line if-else|Great for assignments|

---

## 🌍 Real-World Example

```C#
using System;

class Program
{
    static void Main()
    {
        Console.Write("Enter your grade (A-F): ");
        string grade = Console.ReadLine();

        switch (grade.ToUpper())
        {
            case "A":
                Console.WriteLine("Excellent!");
                break;
            case "B":
                Console.WriteLine("Good job.");
                break;
            case "C":
                Console.WriteLine("You passed.");
                break;
            case "D":
                Console.WriteLine("Needs improvement.");
                break;
            case "F":
                Console.WriteLine("Failed.");
                break;
            default:
                Console.WriteLine("Invalid grade.");
                break;
        }
    }
}
```

---

## 🔄 Bonus: `switch` Expression (C# 8+)

```C#
string message = grade switch
{
    "A" => "Excellent!",
    "B" => "Good job.",
    _   => "Unknown grade."
};
```