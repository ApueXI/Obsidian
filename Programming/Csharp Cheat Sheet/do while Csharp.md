---
Created: 2025-08-07T20:10
tags:
  - Control-Flow
---
## ✅ Concept

The `do...while` loop in C# executes the loop **at least once**, **then checks the condition** at the end of each iteration. It's useful when the loop body must run before any condition is tested.

---

## 🧠 Syntax

```C#
do
{
    // Code to execute at least once
} while (condition);
```

- `condition` is a Boolean expression.
- The loop continues **as long as** `condition` is true.
- If `condition` is false initially, the loop still runs **once**.

---

## ⚠️ Common Gotchas

|Gotcha|Description|
|---|---|
|🔁 Infinite Loop|If the condition never becomes false, the loop runs forever.|
|🧠 Semicolon|The `while` at the end must be followed by a **semicolon**.|
|❌ Break vs Continue|`break` exits the loop; `continue` jumps to the condition check.|
|🧪 Condition Logic|Always ensure the condition will eventually turn false (or use `break`).|

---

## 🔁 Comparison With `while`

|Feature|`while` Loop|`do...while` Loop|
|---|---|---|
|Condition Check|Before entering the loop|After the first iteration|
|Guaranteed Run|❌ No|✅ Yes|

---

## 📋 Quick Reference Table

|Element|Description|
|---|---|
|`do { } while();`|Loop structure|
|Semicolon|Required after `while(condition);`|
|Runs at least once|✅|
|Condition type|Boolean (`true` or `false`)|

---

## 🌍 Real-World Example

```C#
using System;

class Program
{
    static void Main()
    {
        string input;

        do
        {
            Console.Write("Enter a command (type 'exit' to quit): ");
            input = Console.ReadLine();
            Console.WriteLine($"You entered: {input}");
        } while (input != "exit");

        Console.WriteLine("Exited loop.");
    }
}
```

### ✅ What This Does:

- Prompts the user at least once.
- Repeats until they type `"exit"`.