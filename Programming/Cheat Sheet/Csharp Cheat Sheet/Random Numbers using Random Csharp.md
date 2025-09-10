---
Created: 2025-08-07T20:10
tags:
  - Math-Class
---
# 🎲 C# `Random` Class Cheat Sheet

The `Random` class in `System` is used to generate pseudo-random numbers.

```C#
using System;
```

---

## 🔧 Creating a Random Object

```C#
Random rand = new Random();
```

> ⚠️ Don’t create Random multiple times in a short span (like inside a loop) — it may generate the same values due to same system time seed.

---

## 🔢 Generating Numbers

|Method|Description|Example|Output Range|
|---|---|---|---|
|`Next()`|Random **non-negative int**|`rand.Next()`|`0` to `int.MaxValue`|
|`Next(max)`|Random int less than max|`rand.Next(10)`|`0` to `9`|
|`Next(min, max)`|Random int between min and max-1|`rand.Next(5, 10)`|`5` to `9`|
|`NextDouble()`|Random `double` between 0.0 and 1.0|`rand.NextDouble()`|`0.0` to `<1.0`|
|`NextBytes(byte[])`|Fills array with random bytes|`rand.NextBytes(buf)`|Random binary data|

---

## 🧮 Examples

```C#
Random rand = new Random();

// Integer 0 to 99
int num = rand.Next(100);

// Integer 10 to 19
int range = rand.Next(10, 20);

// Double between 0.0 and 1.0
double d = rand.NextDouble();

// Random byte array
byte[] bytes = new byte[5];
rand.NextBytes(bytes);
```

---

## 📌 Setting a Seed

You can control randomness (for repeatable tests) using a seed:

```C#
Random rand = new Random(42); // Always gives the same sequence
```

---

## 🎯 Real-World Usage

### 🎲 Simulate Dice Roll

```C#
int die = rand.Next(1, 7); // 1 to 6
```

### 👕 Pick Random Color

```C#
string[] colors = { "Red", "Blue", "Green" };
string randomColor = colors[rand.Next(colors.Length)];
```

### 🃏 Shuffle Array (Fisher–Yates)

```C#
void Shuffle<T>(T[] array, Random rand)
{
    for (int i = array.Length - 1; i > 0; i--)
    {
        int j = rand.Next(i + 1);
        (array[i], array[j]) = (array[j], array[i]);
    }
}
```

---

## ⚠️ Common Mistakes

|Mistake|Fix|
|---|---|
|Re-initializing `Random` too often|Create it **once** and reuse|
|Assuming `Next(0)` returns 0|It throws `ArgumentOutOfRangeException`|
|Using `NextDouble()` for integers|Use `Next()` or scale: `rand.NextDouble() * max`|

---

## 📋 Quick Summary

|Task|Code Example|Result|
|---|---|---|
|0–9 random int|`rand.Next(10)`|0 to 9|
|1–6 dice roll|`rand.Next(1, 7)`|1 to 6|
|Random double|`rand.NextDouble()`|0.0 to <1.0|
|Random byte array|`rand.NextBytes(bytes)`|Random bytes|
|Reproducible sequence|`new Random(seed)`|Fixed pattern|