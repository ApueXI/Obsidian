---
Created: 2025-08-03T16:52
tags:
  - William-Fiset
---
## ==Computational Complexity Analysis==

**Computational Complexity Analysis** is the study of how the **resource usage** of an algorithm (like time and memory) grows as the size of the input increases. It helps us evaluate the **efficiency** of an algorithm.

The most common resources analyzed are:

- **Time complexity** – How fast an algorithm runs.
- **Space complexity** – How much memory it uses.

  

### ✅ Why It Matters:

- Helps compare different algorithms.
- Predicts performance on large inputs.
- Guides choosing the best algorithm for a given problem.

  

### ⏱️ Time Complexity

Time complexity measures the number of **basic operations or steps** an algorithm takes as a function of input size `n`.

Common notations:

- **O(1)** – Constant time (fastest)
- **O(log n)** – Logarithmic time (e.g., binary search)
- **O(n)** – Linear time (e.g., loop through array)
- **O(n log n)** – Log-linear (e.g., merge sort)
- **O(n²)** – Quadratic time (e.g., nested loops)
- **O(2ⁿ)** – Exponential (very slow)

  

### 🧠 Big O Notation

**Big O** is used to describe the **upper bound** of an algorithm’s growth rate—how it behaves in the worst-case scenario.

Example:

```Python
for i in range(n):       # O(n)
    print(i)
```

### 🧮 Space Complexity

Measures how much **memory** an algorithm uses relative to the input size.

Includes:

- Input data storage
- Temporary variables
- Recursive call stack

Example:

```Python
def sum_array(arr):
    total = 0           # O(1) extra space
    for num in arr:
        total += num
    return total
```

  

### 📝 Quick Reference Table

|Complexity|Name|Example Use|
|---|---|---|
|O(1)|Constant|Accessing array index|
|O(log n)|Logarithmic|Binary search|
|O(n)|Linear|Single loop through data|
|O(n log n)|Log-linear|Merge sort, quicksort avg|
|O(n²)|Quadratic|Bubble sort, nested loops|
|O(2ⁿ)|Exponential|Recursive Fibonacci|

  

### 📌 Summary:

- **Goal:** Measure and compare efficiency.
- **Focus:** Time and space usage as input grows.
- **Tool:** Use **Big O notation** to express performance trends.

  

  

---

  

## ==Complexity Analysis==

**Complexity Analysis** is the process of determining the **efficiency** of an algorithm in terms of the **resources it consumes**, primarily **time** and **space**, as the input size increases.

It helps programmers understand how algorithms **scale** and which one to choose for a given problem.

  

### 🔍 Types of Complexity

### 1. **Time Complexity**

- Describes **how long** an algorithm takes to run as a function of input size `n`.
- Measured by counting the **number of operations** performed.
- Expressed using **Big O Notation**.

### 2. **Space Complexity**

- Describes **how much memory** an algorithm uses.
- Includes input size, auxiliary space (temporary variables), and call stack (for recursion).

### 🧠 Why Complexity Analysis is Important

- Helps choose the **most efficient** algorithm for large datasets.
- Reveals performance in **worst-case**, **best-case**, and **average-case**.
- Avoids algorithms that are too slow or memory-intensive.

  

### ⚙️ Common Time Complexities

|Time Complexity|Name|Example Use Case|
|---|---|---|
|O(1)|Constant|Accessing array element|
|O(log n)|Logarithmic|Binary Search|
|O(n)|Linear|Looping through an array|
|O(n log n)|Log-linear|Merge Sort, Quick Sort|
|O(n²)|Quadratic|Nested loops, Bubble Sort|
|O(2ⁿ), O(n!)|Exponential/Factorial|Recursive brute force|

  

### 📌 Example:

```Python
# Example: O(n) Time Complexity
def print_elements(arr):
    for item in arr:
        print(item)
```

- This loop runs once for each element → **O(n)**.

  

### ✅ Summary

- **Complexity Analysis** tells you _how efficient_ an algorithm is.
- Focuses on **time** and **space** usage as input grows.
- Uses **Big O Notation** to express growth rate.

  

---

  

## ==Big-O Notation==

**Big-O Notation** is a mathematical way to describe the **upper bound** or worst-case scenario of an algorithm’s running time or space usage as the input size (`n`) grows large.

It focuses on the **growth rate** of an algorithm’s resource consumption, ignoring constant factors and lower-order terms to simplify comparison between algorithms.

  

### Key Points:

- Describes how the **time or space** grows relative to input size.
- Helps compare the **efficiency** of different algorithms.
- Only the **dominant term** matters as `n` becomes large.
- Ignores constant multipliers and less significant terms.

  

### Common Big-O Classifications:

|Big-O|Name|Description|Example Scenario|
|---|---|---|---|
|**O(1)**|Constant|Time/space does not grow with input size|Accessing array element|
|**O(log n)**|Logarithmic|Grows slowly as input grows|Binary search|
|**O(n)**|Linear|Grows proportionally to input size|Simple loop through data|
|**O(n log n)**|Log-linear|Common in efficient sorting algorithms|Merge sort, Quick sort (average)|
|**O(n²)**|Quadratic|Time grows quadratically with input|Nested loops, Bubble sort|
|**O(2ⁿ)**|Exponential|Doubles with each addition to input size|Recursive Fibonacci|

### Example:

```Python
for i in range(n):          # O(n)
    print(i)

for i in range(n):
    for j in range(n):      # O(n²)
        print(i, j)
```

  

### Why Big-O Matters:

- Predicts how an algorithm performs as data scales.
- Helps in writing efficient, scalable programs.
- Guides selection of appropriate algorithms for real-world problems.

  

---

  

## ==Big-O Properties==

Big-O notation has several important properties that help simplify and analyze algorithm complexities effectively.

  

### 1. **Ignore Constants**

- Constants do not affect growth rate as input size grows large.
- Example:
    
    O(3n)=O(n)O(3n) = O(n)O(3n)=O(n)
    

  

### 2. **Drop Lower-Order Terms**

- When multiple terms exist, keep only the term with the highest growth rate.
- Example:
    
    O(n2+n)=O(n2)O(n^2 + n) = O(n^2)O(n2+n)=O(n2)
    

  

### 3. **Multiplicative Constants**

- Multiplying by a constant factor does not change the Big-O class.
- Example:
    
    O(5×nlog⁡n)=O(nlog⁡n)O(5 \times n \log n) = O(n \log n)O(5×nlogn)=O(nlogn)
    

  

### 4. **Additive Property**

- When combining sequential steps, the overall complexity is dominated by the largest term.
- Example:
    
    If step 1 is O(n)O(n)O(n) and step 2 is O(n2)O(n^2)O(n2), total is:
    
    O(n+n2)=O(n2)O(n + n^2) = O(n^2)O(n+n2)=O(n2)
    

### 5. **Multiplying Complexities**

- When algorithms are nested (one inside another), multiply their complexities.
- Example:
    
    Nested loops of O(n)O(n)O(n) inside another O(n)O(n)O(n) → O(n)×O(n)=O(n2)O(n) \times O(n) = O(n^2)O(n)×O(n)=O(n2)
    

  

### 6. **Big-O is an Upper Bound**

- It describes the worst-case scenario, not the exact time.
- Ensures algorithm won’t be worse than the stated complexity.

  

### Summary Table

|Property|Explanation|Example|
|---|---|---|
|Ignore constants|Constants don’t matter|O(7n)=O(n)O(7n) = O(n)O(7n)=O(n)|
|Drop lower terms|Keep highest order term|O(n2+n)=O(n2)O(n^2 + n) = O(n^2)O(n2+n)=O(n2)|
|Multiplicative constants|Ignore constant multipliers|O(4nlog⁡n)=O(nlog⁡n)O(4n \log n) = O(n \log n)O(4nlogn)=O(nlogn)|
|Additive property|Largest term dominates|O(n+n2)=O(n2)O(n + n^2) = O(n^2)O(n+n2)=O(n2)|
|Multiplying complexities|Nested loops multiply complexities|O(n)×O(n)=O(n2)O(n) \times O(n) = O(n^2)O(n)×O(n)=O(n2)|
|Upper bound meaning|Worst-case behavior|Big-O is max growth rate|

---

  

## ==Big-O Examples==

Here are some typical examples of algorithms or code snippets and their Big-O time complexities:

---

### 1. **O(1) – Constant Time**

The operation takes the same time regardless of input size.

Example: Accessing an element by index in an array.

```Python
arr = [10, 20, 30]
print(arr[1])  # O(1)
```

### 2. **O(log n) – Logarithmic Time**

The time grows logarithmically as input grows.

Example: Binary Search on a sorted array.

```Python
def binary_search(arr, target):
    low, high = 0, len(arr) - 1
    while low <= high:
        mid = (low + high) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            low = mid + 1
        else:
            high = mid - 1
```

### 3. **O(n) – Linear Time**

The time grows linearly with input size.

Example: Looping through an array.

```Python
for item in arr:
    print(item)  # O(n)
```

### 4. **O(n log n) – Log-linear Time**

Common in efficient sorting algorithms like merge sort and quicksort (average case).

Example: Merge Sort.

### 5. **O(n²) – Quadratic Time**

Time grows proportionally to the square of input size.

Example: Nested loops over the same data.

```Python
for i in range(n):
    for j in range(n):
        print(i, j)  # O(n²)
```

### 6. **O(2ⁿ) – Exponential Time**

Time doubles with each additional input element.

Example: Recursive Fibonacci (naive approach).

```Python
def fib(n):
    if n <= 1:
        return n
    return fib(n-1) + fib(n-2)  # O(2ⁿ)
```

### Summary Table

|Complexity|Description|Example Code|
|---|---|---|
|O(1)|Constant|Access array element|
|O(log n)|Logarithmic|Binary Search|
|O(n)|Linear|Simple loop|
|O(n log n)|Log-linear|Efficient sorting|
|O(n²)|Quadratic|Nested loops|
|O(2ⁿ)|Exponential|Naive recursive Fibonacci|

---