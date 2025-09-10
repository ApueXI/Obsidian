---
Created: 2025-08-07T20:10
tags:
  - Array-&-Collections
---
## ✅ What are 2D Arrays?

- **Rectangular (Multidimensional) Arrays:**
    
    A grid-like structure with **fixed rows and columns**.
    
    Memory is continuous (all rows have the same length).
    
- **Jagged Arrays:**
    
    An array of arrays, where each “row” can have **different lengths** (like a jagged edge).
    

---

## 🧠 Rectangular 2D Arrays

### Declaration & Initialization

```C#
int[,] matrix = new int[3, 4];  // 3 rows, 4 columns (all rows same length)
```

Or with values:

```C#
int[,] matrix = {
    {1, 2, 3, 4},
    {5, 6, 7, 8},
    {9, 10, 11, 12}
};
```

### Access Elements

```C#
int value = matrix[1, 2];  // Row 1, Col 2 → 7
matrix[0, 0] = 100;
```

### Iteration

```C#
for (int i = 0; i < matrix.GetLength(0); i++)       // Rows
{
    for (int j = 0; j < matrix.GetLength(1); j++)   // Columns
    {
        Console.Write(matrix[i, j] + " ");
    }
    Console.WriteLine();
}
```

---

## 🧠 Jagged Arrays (Array of Arrays)

### Declaration & Initialization

```C#
int[][] jagged = new int[3][];   // 3 rows, but columns not set

jagged[0] = new int[] {1, 2};
jagged[1] = new int[] {3, 4, 5};
jagged[2] = new int[] {6};
```

Or inline:

```C#
int[][] jagged = {
    new int[] {1, 2},
    new int[] {3, 4, 5},
    new int[] {6}
};
```

### Access Elements

```C#
int value = jagged[1][2];  // → 5
jagged[0][1] = 99;
```

### Iteration

```C#
for (int i = 0; i < jagged.Length; i++)  // Rows
{
    for (int j = 0; j < jagged[i].Length; j++)  // Columns in row i
    {
        Console.Write(jagged[i][j] + " ");
    }
    Console.WriteLine();
}
```

---

## 📌 Key Differences

|Feature|Rectangular 2D Array|Jagged Array|
|---|---|---|
|Syntax|`int[,]`|`int[][]`|
|Memory layout|Continuous block (fixed size)|Array of arrays (rows can vary)|
|Row length|All rows have the **same length**|Rows can have **different lengths**|
|Access syntax|`[row, col]`|`[row][col]`|
|Performance|Slightly faster due to locality|Slightly slower, more flexible|

---

## 🧪 Real-world Example: Rectangular

```C#
int[,] grid = new int[2,3] { {1,2,3}, {4,5,6} };

Console.WriteLine(grid[1,2]);  // Output: 6
```

---

## 🧪 Real-world Example: Jagged

```C#
int[][] jaggedGrid = new int[2][];
jaggedGrid[0] = new int[] {1, 2, 3};
jaggedGrid[1] = new int[] {4, 5};

Console.WriteLine(jaggedGrid[1][1]);  // Output: 5
```

---

## ⚠️ Gotchas

|Pitfall|Why it matters|
|---|---|
|Mixing rectangular & jagged|Syntax differences lead to compile-time errors|
|Assuming jagged rows equal|Jagged rows can have different lengths|
|Forgetting `.Length` on jagged subarrays|Jagged arrays require checking each row length|

---

## 🧾 Summary Table

|Action|Rectangular Array|Jagged Array|
|---|---|---|
|Declaration|`int[,] matrix = new int[3,4];`|`int[][] jagged = new int[3][];`|
|Initialization|`int[,] m = { {1,2}, {3,4} };`|`int[][] j = { new int[]{1,2}, new int[]{3} };`|
|Access Element|`matrix[0,1]`|`jagged[0][1]`|
|Iterate Rows|`matrix.GetLength(0)`|`jagged.Length`|
|Iterate Columns|`matrix.GetLength(1)`|`jagged[i].Length`|