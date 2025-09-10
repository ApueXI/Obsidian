---
Created: 2025-08-16T09:51
tags:
  - BroCode
---
## ==What is Recursion==

## **Definition**

**Recursion** is a programming technique where a function **calls itself** in order to solve a problem.

- Each recursive call works on a **smaller subproblem**.
- The recursion continues until it reaches a **base case**, which stops further recursive calls.

## **Key Concepts**

1. **Recursive Case** → The part of the function where it **calls itself**.
2. **Base Case** → The condition that **stops recursion** and prevents infinite loops.

Without a base case, recursion will run forever (causing a stack overflow).

## **Example (Factorial)**

Factorial of `n` (denoted as `n!`) is defined as:

```Plain
n! = n × (n-1) × (n-2) × ... × 1
```

**Recursive Formula:**

```Plain
n! = n × (n-1)!
Base Case: 0! = 1
```

**Trace for n = 5:**

```Plain
5! = 5 × 4!
4! = 4 × 3!
3! = 3 × 2!
2! = 2 × 1!
1! = 1 × 0!
0! = 1 (base case)
```

Final Result: `5! = 120`

## **Complexity**

- Depends on the problem. Some recursive algorithms can be inefficient if they recompute results (e.g., naive Fibonacci).
- Can be optimized with **memoization** or **dynamic programming**.
- Uses **function call stack** (extra memory).

## **When to Use**

- Problems that can be broken down into **smaller subproblems** (e.g., factorial, Fibonacci, tree traversal, divide and conquer algorithms).
- When the recursive solution is **simpler and clearer** than an iterative one.

---

  

## ==Where to use Recursion==

**Recursion** is a programming technique where a function calls itself to solve a problem. It is most useful when a problem can be **broken into smaller subproblems** of the same type.

## **1. Divide and Conquer Problems**

- Problems that can be split into smaller instances of the same problem.
- Example: **Merge Sort**, **Quick Sort**, **Binary Search**.

## **2. Problems with Repetitive Substructure**

- When the same computation or logic is applied repeatedly on smaller inputs.
- Example: **Factorial**, **Fibonacci numbers**, **Tower of Hanoi**.

## **3. Tree or Graph Traversals**

- Ideal for **recursive structures** like trees and graphs.
- Example: **Binary Tree Traversal (inorder, preorder, postorder)**, **DFS (Depth-First Search)**.

## **4. Backtracking Problems**

- Useful for exploring all possible solutions in **constraint-based problems**.
- Example: **Sudoku solver**, **N-Queens problem**, **Maze solving**.

## **5. When a Problem is Naturally Recursive**

- Some problems are **simpler to express recursively** than iteratively.
- Example: **Recursive calculation of GCD**, **nested data structures**.

## **Summary Table**

|Problem Type|Recursion Suitable?|
|---|---|
|Divide and conquer algorithms|✅|
|Repetitive substructure problems|✅|
|Tree or graph traversal|✅|
|Backtracking / constraint problems|✅|
|Simple linear iteration problems|❌|

---

  

## ==Complexity Analysis==

**Recursion** solves problems by **breaking them into smaller subproblems** and calling the function on these subproblems. The **complexity** depends on:

1. Number of recursive calls.
2. Work done in each call.

## **Time Complexity**

|Type of Problem|Time Complexity|Explanation|
|---|---|---|
|**Simple linear recursion**|O(n)|Each call reduces the problem by 1. Example: Factorial of n.|
|**Binary recursion**|O(2^n)|Each call spawns two calls. Example: naive Fibonacci.|
|**Divide and Conquer recursion**|O(n log n)|Problem splits in halves. Example: Merge Sort.|
|**Tail recursion (optimized)**|Same as iterative equivalent, often O(n)|Can be optimized by compiler to reuse stack space.|

- `n` = size of the input or number of recursive levels.
- Recursive algorithms can be **slower** than iterative ones if they recompute results (e.g., naive Fibonacci).

## **Space Complexity**

- Depends on the **recursion depth** (stack frames).
- **Linear recursion:** O(n) stack space
- **Binary recursion:** O(n) stack space in worst case
- **Tail recursion:** O(1) if compiler optimizes

## **Summary**

- Recursion is **intuitive and elegant** for many problems.
- Can be **memory-intensive** if recursion depth is large.
- Often optimized with **memoization** or **iterative conversion**.

---

  

## ==Code==

### Python

```Python
def factorial(n):
    """Calculate factorial using recursion"""
    # Base case
    if n == 0 or n == 1:
        return 1
    # Recursive case
    return n * factorial(n - 1)

def fibonacci(n):
    """Calculate fibonacci number using recursion"""
    # Base cases
    if n <= 1:
        return n
    # Recursive case
    return fibonacci(n - 1) + fibonacci(n - 2)

def sum_digits(n):
    """Calculate sum of digits using recursion"""
    # Base case
    if n == 0:
        return 0
    # Recursive case
    return (n % 10) + sum_digits(n // 10)

def countdown(n):
    """Print countdown using recursion"""
    # Base case
    if n <= 0:
        print("Done!")
        return
    # Recursive case
    print(n)
    countdown(n - 1)

def power(base, exp):
    """Calculate power using recursion"""
    # Base case
    if exp == 0:
        return 1
    # Recursive case
    return base * power(base, exp - 1)

# Example usage
if __name__ == "__main__":
    print("Factorial of 5:", factorial(5))
    print("Fibonacci of 6:", fibonacci(6))
    print("Sum of digits of 123:", sum_digits(123))
    print("Power 2^4:", power(2, 4))
    
    print("\nCountdown from 5:")
    countdown(5)
```

### C#

```C#
using System;

class SimpleRecursion
{
    /// <summary>
    /// Calculate factorial using recursion
    /// </summary>
    public static int Factorial(int n)
    {
        // Base case
        if (n == 0 || n == 1)
            return 1;
        // Recursive case
        return n * Factorial(n - 1);
    }
    
    /// <summary>
    /// Calculate fibonacci number using recursion
    /// </summary>
    public static int Fibonacci(int n)
    {
        // Base cases
        if (n <= 1)
            return n;
        // Recursive case
        return Fibonacci(n - 1) + Fibonacci(n - 2);
    }
    
    /// <summary>
    /// Calculate sum of digits using recursion
    /// </summary>
    public static int SumDigits(int n)
    {
        // Base case
        if (n == 0)
            return 0;
        // Recursive case
        return (n % 10) + SumDigits(n / 10);
    }
    
    /// <summary>
    /// Print countdown using recursion
    /// </summary>
    public static void Countdown(int n)
    {
        // Base case
        if (n <= 0)
        {
            Console.WriteLine("Done!");
            return;
        }
        // Recursive case
        Console.WriteLine(n);
        Countdown(n - 1);
    }
    
    /// <summary>
    /// Calculate power using recursion
    /// </summary>
    public static int Power(int baseNum, int exp)
    {
        // Base case
        if (exp == 0)
            return 1;
        // Recursive case
        return baseNum * Power(baseNum, exp - 1);
    }
    
    static void Main(string[] args)
    {
        Console.WriteLine("Factorial of 5: " + Factorial(5));
        Console.WriteLine("Fibonacci of 6: " + Fibonacci(6));
        Console.WriteLine("Sum of digits of 123: " + SumDigits(123));
        Console.WriteLine("Power 2^4: " + Power(2, 4));
        
        Console.WriteLine("\nCountdown from 5:");
        Countdown(5);
        
        Console.ReadLine(); // Keep console open
    }
}
```

### C++

```C++
\#include <iostream>

/**
 * Calculate factorial using recursion
 */
int factorial(int n) {
    // Base case
    if (n == 0 || n == 1)
        return 1;
    // Recursive case
    return n * factorial(n - 1);
}

/**
 * Calculate fibonacci number using recursion
 */
int fibonacci(int n) {
    // Base cases
    if (n <= 1)
        return n;
    // Recursive case
    return fibonacci(n - 1) + fibonacci(n - 2);
}

/**
 * Calculate sum of digits using recursion
 */
int sumDigits(int n) {
    // Base case
    if (n == 0)
        return 0;
    // Recursive case
    return (n % 10) + sumDigits(n / 10);
}

/**
 * Print countdown using recursion
 */
void countdown(int n) {
    // Base case
    if (n <= 0) {
        std::cout << "Done!" << std::endl;
        return;
    }
    // Recursive case
    std::cout << n << std::endl;
    countdown(n - 1);
}

/**
 * Calculate power using recursion
 */
int power(int base, int exp) {
    // Base case
    if (exp == 0)
        return 1;
    // Recursive case
    return base * power(base, exp - 1);
}

int main() {
    std::cout << "Factorial of 5: " << factorial(5) << std::endl;
    std::cout << "Fibonacci of 6: " << fibonacci(6) << std::endl;
    std::cout << "Sum of digits of 123: " << sumDigits(123) << std::endl;
    std::cout << "Power 2^4: " << power(2, 4) << std::endl;
    
    std::cout << "\nCountdown from 5:" << std::endl;
    countdown(5);
    
    return 0;
}
```

---