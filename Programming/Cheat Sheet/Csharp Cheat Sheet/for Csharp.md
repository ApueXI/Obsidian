---
Created: 2025-08-07T20:10
tags:
  - Control-Flow
---
---

## 🔹 1. **Basic Syntax**

```C#
for (initialization; condition; increment)
{
    // Code to repeat
}
```

### 🔸 Example:

```C#
for (int i = 0; i < 5; i++)
{
    Console.WriteLine($"i = {i}");
}
```

**Output:**

```Plain
i = 0
i = 1
i = 2
i = 3
i = 4
```

---

## 🔹 2. **How It Works**

|Part|Role|
|---|---|
|Initialization|Runs **once** at the start (`int i = 0`)|
|Condition|Checked **before** each loop (`i < 5`)|
|Increment|Runs **after** each loop (`i++`)|

---

## 🔹 3. **Reverse Loop**

```C#
for (int i = 10; i >= 0; i--)
{
    Console.WriteLine(i);
}
```

---

## 🔹 4. **Skipping Iteration with** `**continue**`

```C#
for (int i = 0; i < 5; i++)
{
    if (i == 2) continue;
    Console.WriteLine(i);
}
```

**Output:** `0 1 3 4`

---

## 🔹 5. **Exiting Early with** `**break**`

```C#
for (int i = 0; i < 5; i++)
{
    if (i == 3) break;
    Console.WriteLine(i);
}
```

**Output:** `0 1 2`

---

## 🔹 6. **Nested** `**for**` **Loops**

```C#
for (int row = 1; row <= 3; row++)
{
    for (int col = 1; col <= 3; col++)
    {
        Console.Write($"{row},{col}  ");
    }
    Console.WriteLine();
}
```

---

## 🧠 Gotchas

|Issue|Explanation|
|---|---|
|Infinite loop|Happens if condition never becomes false|
|Off-by-one errors|Common when using `<` vs `<=` incorrectly|
|Modifying counter inside loop|Can lead to unexpected behavior|
|Using `var` with loop variables|Allowed, but be explicit in most cases for clarity|

---

## 📋 Summary Table

|Element|Example|Description|
|---|---|---|
|Initialization|`int i = 0`|Start value|
|Condition|`i < 5`|When to continue|
|Increment|`i++`|Update step per loop|
|`continue`|Skips current|Skips rest of code in this loop|
|`break`|Exits early|Immediately leaves the loop|

---

## 🌍 Real-World Example: Multiplication Table

```C#
for (int i = 1; i <= 10; i++)
{
    Console.WriteLine($"5 x {i} = {5 * i}");
}
```

**Output:**

```Plain
5 x 1 = 5
5 x 2 = 10
...
5 x 10 = 50
```

---

## 🔄 Bonus: `for` with Arrays

```C#
string[] fruits = { "Apple", "Banana", "Cherry" };

for (int i = 0; i < fruits.Length; i++)
{
    Console.WriteLine(fruits[i]);
}
```