---
Created: 2025-08-25T20:07
tags:
  - Arrays-&-Collections-(Core)
---
## 1. Full Explanation

### 🔹 What is a 2D Array?

- A **2D array** is an **array of arrays**, forming a **matrix-like structure**.
- Elements are accessed using **two indices**: `[row][column]`.
- Commonly used for **tables, matrices, and grids**.

---

### 🔹 Declaring & Creating 2D Arrays

```Java
// Declaration
int[][] matrix;      // preferred
int matrix2[][];     // also valid

// Creation
matrix = new int[3][4]; // 3 rows, 4 columns

// Declaration + Creation
int[][] arr = new int[2][3]; // 2 rows, 3 columns

```

---

### 🔹 Initializing 2D Arrays

```Java
// Static Initialization
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Dynamic Initialization
int[][] grid = new int[2][2];
grid[0][0] = 10;
grid[0][1] = 20;
grid[1][0] = 30;
grid[1][1] = 40;

```

---

### 🔹 Accessing 2D Array Elements

```Java
int[][] arr = {
    {1, 2, 3},
    {4, 5, 6}
};

System.out.println(arr[0][1]); // 2
arr[1][2] = 10;                // modify element
System.out.println(arr[1][2]); // 10

```

- **IndexOutOfBoundsException** occurs if row or column index is out of bounds.

---

### 🔹 Looping through 2D Arrays

```Java
int[][] arr = {
    {1, 2, 3},
    {4, 5, 6}
};

// Using nested for loop
for(int i = 0; i < arr.length; i++) {        // rows
    for(int j = 0; j < arr[i].length; j++) { // columns
        System.out.print(arr[i][j] + " ");
    }
    System.out.println();
}

// Using enhanced for loop
for(int[] row : arr) {
    for(int val : row) {
        System.out.print(val + " ");
    }
    System.out.println();
}

```

✅ Output:

```Plain
1 2 3
4 5 6

```

---

### 🔹 Key Points

1. **2D array = array of arrays**.
2. **Indexing**: `[row][column]`.
3. Can be **rectangular** (all rows same length) or **jagged** (rows of different lengths).
4. **Default values**: same as 1D arrays (`int`→0, `double`→0.0, `boolean`→false, Object→null).
5. Use `arr.length` → number of rows, `arr[i].length` → number of columns in row `i`.

---

### 🔹 Gotchas / Notes

- **Jagged arrays** example:

```Java
int[][] jagged = new int[3][];
jagged[0] = new int[2];
jagged[1] = new int[3];
jagged[2] = new int[1];

```

- Accessing **uninitialized row** throws `NullPointerException`.

---

## 2. 📊 Summary Table

|Operation|Syntax / Example|Notes|
|---|---|---|
|Declaration|`int[][] arr;`|preferred style|
|Creation|`arr = new int[3][4];`|3 rows, 4 columns|
|Initialization|`int[][] arr = {{1,2},{3,4}};`|static initialization|
|Access|`arr[0][1]`|get or set element|
|Loop|nested for loops|`arr.length` = rows, `arr[i].length` = columns|
|Enhanced Loop|`for(int[] row : arr)`|for-each style|

---

### 🔹 Real-World Example

**Sum of All Elements in 2D Array**

```Java
public class Main {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        int sum = 0;
        for(int[] row : matrix) {
            for(int val : row) {
                sum += val;
            }
        }

        System.out.println("Sum of all elements: " + sum); // 45
    }
}

```

- Demonstrates **2D array declaration, initialization, nested looping, and aggregation**.