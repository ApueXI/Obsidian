---
Created: 2025-08-21T19:29
tags:
  - Function
---
## 1. What is Recursion?

- **A function calling itself** directly or indirectly.
- Used to solve problems that can be broken into **smaller subproblems** of the same type.
- Always needs a **base case** to stop the recursion, otherwise it causes an **infinite loop** → `RecursionError`.

---

## 2. Basic Recursive Structure

```Python
def recursive_function(params):
    if base_case_condition:  # Base case
        return result
    else:  # Recursive case
        return recursive_function(smaller_problem)

```

✅ **Base Case** → Stops recursion

✅ **Recursive Case** → Breaks down into smaller subproblems

---

## 3. Simple Examples

### Countdown Example

```Python
def countdown(n):
    if n == 0:  # Base case
        print("Done!")
    else:
        print(n)
        countdown(n - 1)  # Recursive call

countdown(5)
```

---

### Factorial Example

```Python
def factorial(n):
    if n == 0 or n == 1:  # Base case
        return 1
    else:
        return n * factorial(n - 1)  # Recursive case

print(factorial(5))  # 120
```

---

## 4. Common Recursive Problems

- **Mathematical**
    - Factorial, Fibonacci numbers, GCD
- **Data Structures**
    - Tree traversal, Graph traversal
- **Divide & Conquer Algorithms**
    - Merge Sort, Quick Sort
- **Backtracking**
    - Sudoku Solver, N-Queens Problem

---

## 5. Tail Recursion (Not Optimized in Python)

Python **does NOT optimize tail recursion** (like some languages do), so deep recursion can hit the limit.

```Python
import sys
sys.setrecursionlimit(2000)  # Increase limit if needed
```

---

## 6. When to Use Recursion

✅ When the problem is naturally **recursive** (trees, nested structures)

✅ When it makes code **simpler & more readable**

❌ Avoid for very deep problems → use **loops** or **stacks** instead.

---

## Summary Table

|Concept|Example Syntax|Purpose / Description|
|---|---|---|
|Base Case|`if n == 0: return 1`|Stops recursion to prevent infinite loop|
|Recursive Case|`return n * f(n-1)`|Breaks down into smaller subproblem|
|Factorial|`factorial(n)`|Classic recursion example|
|Tree Recursion|`dfs(node.left); dfs(node.right)`|Used in tree/graph traversal|
|Recursion Limit|`sys.setrecursionlimit(n)`|Adjust max recursion depth in Python|

---

## Real-World Example: Directory Scanner

A recursive function to list all files in a folder **and its subfolders**.

```Python
import os

def list_files(directory):
    for item in os.listdir(directory):
        path = os.path.join(directory, item)
        if os.path.isdir(path):
            list_files(path)  # Recursive call for subfolder
        else:
            print(path)

list_files("C:/Users/YourName/Documents")
```

✅ Scans **nested folders** easily

✅ Without recursion, would require manual loops & stacks