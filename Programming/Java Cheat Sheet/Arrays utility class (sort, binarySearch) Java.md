---
Created: 2025-08-25T20:07
tags:
  - Arrays-&-Collections-(Core)
---
## 1. Full Explanation

### 🔹 What is `Arrays` Class?

- The `**java.util.Arrays**` class provides **utility methods** to **manipulate arrays**.
- Includes methods for:
    - **Sorting** (`sort`)
    - **Searching** (`binarySearch`)
    - **Comparing** (`equals`)
    - **Filling** (`fill`)
    - **Converting to String** (`toString`)
    - **Copying** (`copyOf`, `copyOfRange`)
- All methods are **static**, so no need to create an object.

---

### 🔹 Import Statement

```Java
import java.util.Arrays;

```

---

### 🔹 Sorting Arrays

```Java
int[] arr = {5, 2, 8, 1, 3};
Arrays.sort(arr); // ascending order

System.out.println(Arrays.toString(arr)); // [1, 2, 3, 5, 8]

```

- Can also sort **subarrays**:

```Java
Arrays.sort(arr, 1, 4); // sorts index 1 to 3

```

- For **objects**, can provide **Comparator**:

```Java
String[] names = {"Alice", "Bob", "Charlie"};
Arrays.sort(names, (a, b) -> b.compareTo(a)); // descending

```

---

### 🔹 Binary Search

- Searches a **sorted array** and returns **index of element**, or **negative** if not found.

```Java
int[] arr = {1, 2, 3, 5, 8};
int index = Arrays.binarySearch(arr, 5); // 3
int notFound = Arrays.binarySearch(arr, 4); // -4 (insertion point -1)

```

- **Array must be sorted** before using `binarySearch`.

---

### 🔹 Other Useful Methods

```Java
int[] arr = {1, 2, 3, 4, 5};

// Fill array
Arrays.fill(arr, 0); // [0, 0, 0, 0, 0]

// Copy array
int[] copy = Arrays.copyOf(arr, arr.length); // [0, 0, 0, 0, 0]
int[] part = Arrays.copyOfRange(arr, 1, 4); // [0, 0, 0]

// Compare arrays
int[] a1 = {1,2,3};
int[] a2 = {1,2,3};
System.out.println(Arrays.equals(a1, a2)); // true

// Convert array to string
System.out.println(Arrays.toString(arr)); // [0, 0, 0, 0, 0]

```

---

### 🔹 Key Points

1. All methods are **static** → `Arrays.method(array)`.
2. `sort()` → ascending order by default, comparator for custom sorting.
3. `binarySearch()` → requires **sorted array**.
4. `fill()` → sets all elements to a specific value.
5. `copyOf()` / `copyOfRange()` → clone arrays or subarrays.

---

### 🔹 Gotchas / Notes

- Binary search **does not work on unsorted arrays**.
- `equals()` checks **elements order**, not reference equality.
- `Arrays.toString()` is for **1D arrays**, `Arrays.deepToString()` for **multidimensional arrays**.

---

## 2. 📊 Summary Table

|Method|Syntax / Example|Notes|
|---|---|---|
|sort|`Arrays.sort(arr)`|ascending order|
|binarySearch|`Arrays.binarySearch(arr, 5)`|array must be sorted|
|fill|`Arrays.fill(arr, 0)`|fill with single value|
|copyOf|`Arrays.copyOf(arr, length)`|copy array|
|copyOfRange|`Arrays.copyOfRange(arr, from, to)`|copy subarray|
|equals|`Arrays.equals(a1, a2)`|element-wise comparison|
|toString|`Arrays.toString(arr)`|1D array to string|
|deepToString|`Arrays.deepToString(arr2D)`|multi-dimensional array to string|

---

### 🔹 Real-World Example

**Sort and Search Student Marks**

```Java
import java.util.Arrays;

public class Main {
    public static void main(String[] args) {
        int[] marks = {75, 85, 60, 90, 70};

        // Sort marks
        Arrays.sort(marks);
        System.out.println("Sorted marks: " + Arrays.toString(marks)); // [60, 70, 75, 85, 90]

        // Find index of a mark
        int idx = Arrays.binarySearch(marks, 85);
        System.out.println("Index of 85: " + idx); // 3

        // Fill new array
        int[] bonusMarks = new int[5];
        Arrays.fill(bonusMarks, 5);
        System.out.println("Bonus marks: " + Arrays.toString(bonusMarks)); // [5,5,5,5,5]
    }
}

```

- Demonstrates **sorting, searching, and filling arrays** using `Arrays` class.