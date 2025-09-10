---
Created: 2025-08-07T20:10
tags:
  - Methods-(Functions)
---
  

## ✅ Concept

**Recursion** is when a method **calls itself**, either **directly** or **indirectly**, to solve a problem **by breaking it into smaller instances** of the same problem.

Every recursive method needs:

1. A **base case** (to stop recursion)
2. A **recursive case** (the self-call)

---

## 🧠 Syntax

```C#
return_type MethodName(parameters)
{
    if (base condition)
        return result; // base case

    return MethodName(smaller_problem); // recursive call
}
```

---

## 📋 Real-World Examples

### 1. Factorial

```C#
int Factorial(int n)
{
    if (n <= 1)
        return 1; // base case
    return n * Factorial(n - 1); // recursive case
}
```

Call with: `Factorial(5)` → returns `120`

---

### 2. Fibonacci (naive version)

```C#
int Fibonacci(int n)
{
    if (n <= 1)
        return n;
    return Fibonacci(n - 1) + Fibonacci(n - 2);
}
```

Call with: `Fibonacci(5)` → returns `5`

⚠️ **Note**: This is inefficient for large `n`.

---

### 3. Recursive Sum of Array

```C#
int Sum(int[] arr, int index)
{
    if (index >= arr.Length)
        return 0;

    return arr[index] + Sum(arr, index + 1);
}
```

Call with: `Sum(new[] {1, 2, 3, 4}, 0)` → returns `10`

---

### 4. Tree Traversal Example

```C#
void Traverse(Node node)
{
    if (node == null) return;

    Console.WriteLine(node.Value); // pre-order
    Traverse(node.Left);
    Traverse(node.Right);
}
```

---

## 🔄 Use Cases

|Use Case|Example|
|---|---|
|Mathematical functions|Factorial, Fibonacci|
|Tree/graph traversal|DOM, binary trees, game AI|
|File system traversal|Search folders/files|
|Backtracking problems|Maze solving, Sudoku|
|Divide & conquer|MergeSort, QuickSort|

---

## ⚠️ Common Gotchas

|Gotcha|Explanation|
|---|---|
|❌ No base case|Causes infinite recursion → `StackOverflowException`|
|💣 Stack size limit|Deep recursion can crash the program|
|😵 Too many allocations|Each recursive call uses memory on the call stack|
|🔄 Better iterative?|Some problems are more efficient with loops (e.g. Fibonacci)|

---

## 🚀 Tips for Safe Recursion

- ✅ Always define a **base case**
- ✅ Make progress **toward the base case**
- ✅ Consider **tail recursion** (not optimized by C# natively though)
- ✅ Use **memoization** or **caching** for overlapping subproblems (e.g., Fibonacci)
- ✅ Use **iterative** methods for performance-critical code

---

## 📌 Quick Reference Summary

|Part|Description|
|---|---|
|Base Case|Stops recursion (no self-call)|
|Recursive Case|Self-call with smaller/simpler input|
|Stack Overflow|Happens if base case is missing or too deep|
|Use with Trees|Very common for traversal|
|Use with Math|Great for breaking down complex logic|

---

## 🧠 Bonus: Tail Recursion

Not optimized by C# (as of now), but still readable:

```C#
int FactorialTail(int n, int acc = 1)
{
    if (n <= 1) return acc;
    return FactorialTail(n - 1, n * acc);
}
```