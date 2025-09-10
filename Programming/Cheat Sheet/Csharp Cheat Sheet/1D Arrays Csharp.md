---
Created: 2025-08-07T20:10
tags:
  - Array-&-Collections
---
## ✅ What is a 1D Array?

A **1-dimensional array** in C# is a **fixed-size, ordered collection** of elements of the **same type**, accessible by an **index (0-based)**.

---

## 🧠 Declaration & Initialization

### 1. Declare and initialize later

```C#
int[] numbers;
numbers = new int[5];  // default values are 0
```

### 2. Declare and initialize together

```C#
int[] numbers = new int[5] { 1, 2, 3, 4, 5 };
```

### 3. Shorthand initialization

```C#
int[] numbers = { 1, 2, 3, 4, 5 };
```

---

## 🚀 Accessing and Modifying Elements

```C#
int[] nums = { 10, 20, 30 };
int second = nums[1];     // Access (20)
nums[2] = 99;             // Modify: {10, 20, 99}
```

---

## 🔁 Iterating Through Arrays

### Using `for` loop

```C#
for (int i = 0; i < nums.Length; i++)
{
    Console.WriteLine(nums[i]);
}
```

### Using `foreach` loop

```C#
foreach (int num in nums)
{
    Console.WriteLine(num);
}
```

---

## 📦 Common Operations

|Operation|Code Example|
|---|---|
|Length of array|`nums.Length`|
|Sort array|`Array.Sort(nums);`|
|Reverse array|`Array.Reverse(nums);`|
|Copy array|`Array.Copy(nums, newNums, nums.Length);`|
|Find index|`Array.IndexOf(nums, 20);`|
|Clear array|`Array.Clear(nums, 0, nums.Length);`|

---

## 🧪 Real-World Example

```C#
string[] fruits = { "Apple", "Banana", "Cherry" };

for (int i = 0; i < fruits.Length; i++)
{
    Console.WriteLine($"{i}: {fruits[i]}");
}
```

---

## ⚠️ Gotchas

|Mistake|Why it matters|
|---|---|
|Index out of bounds|`nums[5]` when length is 5 throws exception|
|Forgetting `.Length`|Hardcoding loop limits causes bugs|
|Arrays are fixed size|Use `List<T>` if you need dynamic size|

---

## 🧾 Summary Table

|Action|Example|
|---|---|
|Declare|`int[] a;`|
|Initialize|`int[] a = new int[5];`|
|With values|`int[] a = {1, 2, 3};`|
|Access element|`a[0]`|
|Change element|`a[1] = 10;`|
|Length|`a.Length`|
|Sort|`Array.Sort(a);`|
|Reverse|`Array.Reverse(a);`|