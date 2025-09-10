---
Created: 2025-08-07T20:20
tags:
  - Basics-&-Syntax
---
## 🔹 1. **Arithmetic Operators**

Used for **basic math** operations.

|Operator|Meaning|Example|Result|
|---|---|---|---|
|`+`|Addition|`5 + 3`|`8`|
|`-`|Subtraction|`5 - 3`|`2`|
|`*`|Multiplication|`5 * 3`|`15`|
|`/`|Division|`5 / 2`|`2` (int)|
|`%`|Modulo (remainder)|`5 % 2`|`1`|
|`++`|Increment|`x++`|`x + 1`|
|`--`|Decrement|`x--`|`x - 1`|

> ⚠️ Division of two ints returns int. Use 5 / 2.0 for decimal division.

---

## 🔹 2. **Relational (Comparison) Operators**

Used to **compare** values. Return `true` or `false`.

|Operator|Meaning|Example|Result|
|---|---|---|---|
|`==`|Equal to|`5 == 5`|`true`|
|`!=`|Not equal to|`5 != 3`|`true`|
|`>`|Greater than|`5 > 3`|`true`|
|`<`|Less than|`5 < 3`|`false`|
|`>=`|Greater than or equal to|`5 >= 5`|`true`|
|`<=`|Less than or equal to|`5 <= 4`|`false`|

---

## 🔹 3. **Logical Operators**

Used for **boolean logic**, often in `if` statements.

|Operator|Meaning|Example|Result|
|---|---|---|---|
|`&&`|Logical AND|`true && false`|`false`|
|`\|`|Logical OR|`true \| false`|`true`|
|`!`|Logical NOT|`!true`|`false`|

> ✅ Short-circuiting: && and || skip evaluating second operand if not needed.

---

## 🔹 4. **Assignment Operators**

Assign and sometimes operate on the variable in a single step.

|Operator|Meaning|Equivalent To|
|---|---|---|
|`=`|Assignment|`x = 5`|
|`+=`|Add and assign|`x = x + 2`|
|`-=`|Subtract and assign|`x = x - 2`|
|`*=`|Multiply and assign|`x = x * 2`|
|`/=`|Divide and assign|`x = x / 2`|
|`%=`|Modulus and assign|`x = x % 2`|

---

## 🔹 5. **Bitwise Operators**

Operate at the **bit level**. Useful for low-level programming.

|Operator|Name|Example|Result (Binary)|
|---|---|---|---|
|`&`|AND|`5 & 3`|`0101 & 0011 = 0001`|
|`\|`|OR|`6 \| 3`|`0110 \| 0011 = 0111`|
|`^`|XOR|`5 ^ 3`|`0101 ^ 0011 = 0110`|
|`~`|NOT|`~5`|`~0101 = 1010` (inverted bits)|
|`<<`|Left shift|`5 << 1`|`0101 << 1 = 1010`|
|`>>`|Right shift|`5 >> 1`|`0101 >> 1 = 0010`|

---

## 🧠 Gotchas

|Issue|Explanation|
|---|---|
|`5 / 2` → `2`|Integer division truncates decimal|
|`x++` vs `++x`|Post-increment returns old value; pre-increment returns new|
|Division by 0|Causes `DivideByZeroException` for `int`, `Infinity` for `double`|
|Bitwise ≠ Logical|Don’t confuse `&` with `&&` or `|

---

## 📋 Summary Table

|Category|Operators|
|---|---|
|Arithmetic|`+`, `-`, `*`, `/`, `%`, `++`, `--`|
|Relational|`==`, `!=`, `>`, `<`, `>=`, `<=`|
|Logical|`&&`, `|
|Assignment|`=`, `+=`, `-=`, `*=`, `/=`, `%=`|
|Bitwise|`&`, `|

---

## 🌍 Real-World Example

```C#
using System;

class Program
{
    static void Main()
    {
        int x = 10;
        int y = 3;

        int sum = x + y;          // Arithmetic
        bool isEqual = x == y;    // Relational
        bool logic = (x > 5) && (y < 5); // Logical
        x += 5;                   // Assignment
        int bits = x & y;         // Bitwise AND

        Console.WriteLine($"Sum: {sum}");
        Console.WriteLine($"Is Equal: {isEqual}");
        Console.WriteLine($"Logic Result: {logic}");
        Console.WriteLine($"Updated x: {x}");
        Console.WriteLine($"Bitwise AND: {bits}");
    }
}
```

**Output:**

```Plain
Sum: 13
Is Equal: False
Logic Result: True
Updated x: 15
Bitwise AND: 3
```