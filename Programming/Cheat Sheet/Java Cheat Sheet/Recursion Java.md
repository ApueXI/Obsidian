---
Created: 2025-08-25T19:38
tags:
  - Methods-(Funciton)
---
## 1. Full Explanation

### 🔹 What is Recursion?

- **Recursion** = a method **calling itself** to solve a problem.
- Used when a problem can be **divided into smaller sub-problems** of the same type.
- Every recursive method must have a **base case** to stop recursion.

---

### 🔹 Syntax

```Java
returnType methodName(parameters) {
    if (base_condition) {
        // base case
        return value;
    } else {
        // recursive call
        return methodName(modified_parameters);
    }
}

```

---

### 🔹 Example 1: Factorial

```Java
public class Factorial {
    public static int factorial(int n) {
        if (n == 0) return 1;       // base case
        return n * factorial(n - 1); // recursive call
    }

    public static void main(String[] args) {
        int result = factorial(5);
        System.out.println("Factorial of 5 is " + result);
    }
}

```

✅ Output:

```Plain
Factorial of 5 is 120

```

---

### 🔹 Example 2: Fibonacci Sequence

```Java
public class Fibonacci {
    public static int fib(int n) {
        if (n == 0) return 0;   // base case
        if (n == 1) return 1;   // base case
        return fib(n - 1) + fib(n - 2); // recursive call
    }

    public static void main(String[] args) {
        for (int i = 0; i < 10; i++) {
            System.out.print(fib(i) + " ");
        }
    }
}

```

✅ Output:

```Plain
0 1 1 2 3 5 8 13 21 34

```

---

### 🔹 Example 3: Sum of Array Elements

```Java
public class ArraySum {
    public static int sum(int[] arr, int n) {
        if (n <= 0) return 0;            // base case
        return sum(arr, n - 1) + arr[n - 1]; // recursive call
    }

    public static void main(String[] args) {
        int[] nums = {1, 2, 3, 4, 5};
        System.out.println("Sum = " + sum(nums, nums.length));
    }
}

```

✅ Output:

```Plain
Sum = 15

```

---

### 🔹 Gotchas / Notes

- Always define a **base case**, otherwise **StackOverflowError** occurs.
- Recursive calls use **call stack**, so deep recursion can cause memory issues.
- Can often be replaced by **loops** (iterative solutions) for efficiency.
- Useful for problems like: factorial, Fibonacci, tree traversal, graph traversal, divide & conquer algorithms.

---

## 2. 📊 Summary Table

|Feature|Syntax / Example|Notes|
|---|---|---|
|Base Case|`if(condition) return value;`|Stops recursion|
|Recursive Call|`methodName(modified_parameters)`|Breaks problem into smaller parts|
|Example|Factorial, Fibonacci|Classic recursion problems|
|Stack Usage|Each call is pushed onto stack|Too deep → StackOverflowError|
|Alternatives|Iterative loops|Often more memory-efficient|

---

### 🔹 Real-World Example

**Directory/File Traversal (like** `**ls**` **command):**

```Java
import java.io.File;

public class DirectoryTraversal {
    public static void listFiles(File dir) {
        if (!dir.isDirectory()) return;
        for (File file : dir.listFiles()) {
            if (file.isDirectory()) {
                listFiles(file); // recursive call
            } else {
                System.out.println(file.getAbsolutePath());
            }
        }
    }

    public static void main(String[] args) {
        File rootDir = new File("C:\\Users\\Public");
        listFiles(rootDir);
    }
}

```

- Demonstrates recursion in **real-world file system traversal**.