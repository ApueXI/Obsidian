---
Created: 2025-08-25T20:06
tags:
  - Arrays-&-Collections-(Core)
---
## 1. Full Explanation

### 🔹 What is a 1D Array?

- A **1D array** is a **collection of elements** of the **same type** stored in **contiguous memory locations**.
- Arrays are **fixed in size** once created.
- Elements are **accessed using index**, starting from **0**.

---

### 🔹 Declaring & Creating 1D Arrays

```Java
// Declaration
int[] numbers;         // preferred
double values[];       // also valid

// Creation
numbers = new int[5];  // array of size 5, default values 0

// Declaration + Creation
int[] arr = new int[5];

```

---

### 🔹 Initializing Arrays

```Java
// Static Initialization
int[] nums = {1, 2, 3, 4, 5};

// Dynamic Initialization
int[] dynamicNums = new int[5];
dynamicNums[0] = 10;
dynamicNums[1] = 20;
// rest default to 0

```

---

### 🔹 Accessing Array Elements

```Java
int[] arr = {10, 20, 30, 40, 50};

System.out.println(arr[0]); // 10
arr[1] = 25;                // modify element
System.out.println(arr[1]); // 25

```

- **IndexOutOfBoundsException** occurs if you access index < 0 or ≥ array length.

---

### 🔹 Looping through Arrays

```Java
int[] arr = {1, 2, 3, 4, 5};

// Using for loop
for(int i = 0; i < arr.length; i++) {
    System.out.println(arr[i]);
}

// Using enhanced for loop
for(int num : arr) {
    System.out.println(num);
}

```

---

### 🔹 Key Points

1. Arrays are **homogeneous** (same type).
2. **Fixed size** → cannot grow or shrink dynamically.
3. **Index starts at 0**.
4. Can use `**length**` **property** to get array size.
5. Default values:
    - `int` → 0
    - `double` → 0.0
    - `boolean` → false
    - Object → null

---

### 🔹 Gotchas / Notes

- Arrays in Java are **objects**, even for primitives.
- Multidimensional arrays are **arrays of arrays** (covered separately).
- Be careful of **IndexOutOfBoundsException**.

---

## 2. 📊 Summary Table

|Operation|Syntax / Example|Notes|
|---|---|---|
|Declaration|`int[] arr;`|preferred style|
|Creation|`arr = new int[5];`|size fixed at runtime|
|Initialization|`int[] arr = {1,2,3};`|static initialization|
|Access|`arr[0]`|get or set element|
|Loop|`for(int i=0;i<arr.length;i++)`|index-based|
|Enhanced Loop|`for(int num : arr)`|for-each style|
|Length|`arr.length`|number of elements|

---

### 🔹 Real-World Example

**Sum of Array Elements**

```Java
public class Main {
    public static void main(String[] args) {
        int[] numbers = {10, 20, 30, 40, 50};
        int sum = 0;

        for(int num : numbers) { // enhanced for loop
            sum += num;
        }

        System.out.println("Sum: " + sum); // Sum: 150
    }
}

```

- Demonstrates **array declaration, initialization, looping, and sum calculation**.