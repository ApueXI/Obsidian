---
Created: 2025-08-07T20:10
tags:
  - Math-Class
---
The `System.Math` class provides **static methods** for common mathematical operations.

```C#
using System;
```

---

## 🔢 Common `Math` Methods

|Method|Description|Example|Output|
|---|---|---|---|
|`Math.Pow(x, y)`|Returns `x` raised to power `y`|`Math.Pow(2, 3)`|`8`|
|`Math.Sqrt(x)`|Square root of `x`|`Math.Sqrt(16)`|`4`|
|`Math.Abs(x)`|Absolute (non-negative) value|`Math.Abs(-5)`|`5`|
|`Math.Floor(x)`|Largest integer ≤ `x`|`Math.Floor(3.9)`|`3`|
|`Math.Ceiling(x)`|Smallest integer ≥ `x`|`Math.Ceiling(3.1)`|`4`|
|`Math.Round(x)`|Nearest whole number (or to N decimals)|`Math.Round(2.5)`|`2`|
|`Math.Max(a, b)`|Larger of `a` or `b`|`Math.Max(5, 10)`|`10`|
|`Math.Min(a, b)`|Smaller of `a` or `b`|`Math.Min(5, 10)`|`5`|

---

## 🧮 Trigonometric Methods

|Method|Description|
|---|---|
|`Math.Sin(x)`|Sine (x in radians)|
|`Math.Cos(x)`|Cosine (x in radians)|
|`Math.Tan(x)`|Tangent (x in radians)|
|`Math.Asin(x)`|Arcsine (returns radians)|
|`Math.Acos(x)`|Arccosine (returns radians)|
|`Math.Atan(x)`|Arctangent (returns radians)|

> Convert degrees to radians: Math.PI / 180

---

## 🧾 Summary Table

|Task|Code|Output|
|---|---|---|
|Power of 2^3|`Math.Pow(2, 3)`|`8`|
|Square root of 9|`Math.Sqrt(9)`|`3`|
|Absolute value of -10|`Math.Abs(-10)`|`10`|
|Floor of 4.8|`Math.Floor(4.8)`|`4`|
|Ceiling of 4.2|`Math.Ceiling(4.2)`|`5`|
|Round 5.6|`Math.Round(5.6)`|`6`|
|Max of 15 and 20|`Math.Max(15, 20)`|`20`|
|Min of 15 and 20|`Math.Min(15, 20)`|`15`|

---

## 🧰 Real-World Example

```C#
double price = 99.99;
double discount = 15.25;

double final = Math.Floor(price - discount); // round down total
Console.WriteLine($"Final price: {final}");  // Final price: 84
```

---

## 🎯 Extra Utilities

- `Math.Log(x)` – Natural logarithm (ln)
- `Math.Log10(x)` – Base-10 logarithm
- `Math.Exp(x)` – `e^x`
- `Math.Sign(x)` – Returns `1`, `0`, or `1`