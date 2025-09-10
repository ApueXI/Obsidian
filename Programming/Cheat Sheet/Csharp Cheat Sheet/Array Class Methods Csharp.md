---
Created: 2025-08-07T20:10
tags:
  - Array-&-Collections
---
## ✅ What is the `Array` Class?

In C#, `Array` is an abstract base class for all arrays (1D, 2D, jagged).

It provides **static methods** for common operations like sorting, searching, copying, and clearing.

---

## 📦 Common `Array` Class Methods

|Method|Purpose|Example|
|---|---|---|
|`Array.Sort()`|Sorts array in ascending order|`Array.Sort(arr);`|
|`Array.Reverse()`|Reverses array order|`Array.Reverse(arr);`|
|`Array.IndexOf()`|Returns index of element|`Array.IndexOf(arr, 10);`|
|`Array.LastIndexOf()`|Returns last index of element|`Array.LastIndexOf(arr, 10);`|
|`Array.Clear()`|Sets a range to default values|`Array.Clear(arr, 0, arr.Length);`|
|`Array.Copy()`|Copies elements to another array|`Array.Copy(src, dest, 3);`|
|`Array.Resize()`|Changes the size of array (1D only)|`Array.Resize(ref arr, 10);`|
|`Array.Exists()`|Checks if any element matches condition|`Array.Exists(arr, x => x > 5);`|
|`Array.Find()`|Finds first element matching condition|`Array.Find(arr, x => x > 5);`|
|`Array.FindAll()`|Returns all matching elements|`Array.FindAll(arr, x => x % 2 == 0);`|
|`Array.TrueForAll()`|Checks if all elements match condition|`Array.TrueForAll(arr, x => x < 100);`|
|`Array.BinarySearch()`|Fast search on **sorted** array|`Array.BinarySearch(arr, 25);`|
|`Array.Clone()`|Shallow copy of array|`int[] copy = (int[])arr.Clone();`|
|`Array.GetLength()`|Gets length of dimension (for multi-D)|`arr.GetLength(0);`|

---

## 🧠 Examples

### Sort and Reverse

```C#
int[] arr = { 3, 1, 4, 2 };
Array.Sort(arr);     // {1, 2, 3, 4}
Array.Reverse(arr);  // {4, 3, 2, 1}
```

### IndexOf / LastIndexOf

```C#
int index = Array.IndexOf(arr, 3);       // → 1
int last = Array.LastIndexOf(arr, 3);    // → 1
```

### Resize

```C#
int[] arr = {1, 2, 3};
Array.Resize(ref arr, 5);   // {1, 2, 3, 0, 0}
```

### Clear

```C#
Array.Clear(arr, 0, 2);   // First 2 elements → 0
```

### Copy

```C#
int[] src = {1, 2, 3};
int[] dest = new int[5];
Array.Copy(src, dest, src.Length);  // dest: {1, 2, 3, 0, 0}
```

### Find / Exists

```C#
bool hasEven = Array.Exists(arr, x => x % 2 == 0);
int firstEven = Array.Find(arr, x => x % 2 == 0);
```

---

## ⚠️ Gotchas

|Mistake|Why it's a problem|
|---|---|
|Using `Array.BinarySearch()` on unsorted arrays|May return wrong index|
|Using `Resize()` on multidimensional arrays|Only works for **1D arrays**|
|Using `Clear()` without range awareness|Could accidentally wipe more than expected|
|Confusing `Clone()` with deep copy|Only creates **shallow copy**|

---

## 📌 Summary Table

|Operation|Code Example|
|---|---|
|Sort|`Array.Sort(arr);`|
|Reverse|`Array.Reverse(arr);`|
|Search|`Array.IndexOf(arr, val);`|
|Copy|`Array.Copy(src, dest, length);`|
|Clear|`Array.Clear(arr, 0, arr.Length);`|
|Resize|`Array.Resize(ref arr, newSize);`|
|Exists|`Array.Exists(arr, cond);`|
|Find|`Array.Find(arr, cond);`|
|TrueForAll|`Array.TrueForAll(arr, cond);`|