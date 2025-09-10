---
Created: 2025-08-13T20:23
tags:
  - William-Fiset
---
# ==Discussion & Examples==

---

  

## ==Data Structure Motivation==

## The Problem

We often need to handle **dynamic array queries** such as:

- **Prefix sum query**: Find the sum of the first i elements.
- **Update**: Change the value of an element.

### Naïve Approaches:

|Approach|Prefix Sum Complexity|Update Complexity|Issue|
|---|---|---|---|
|Simple Loop|O(n)|O(1)|Too slow for large queries.|
|Prefix Sum Array|O(1)|O(n)|Updates require recomputing many sums.|

## The Goal

We want **both**:

- **Prefix sum queries in O(log⁡ n)**
- **Updates in O(log⁡ n)**

## The Idea

A **Fenwick Tree** (Binary Indexed Tree) is a clever data structure that stores **partial sums** in a way that:

- Breaks the array into overlapping ranges (based on powers of 2).
- Each node stores the sum of a range of elements.
- We can compute prefix sums and updates by **traversing only log ⁡n** relevant nodes.

## Why It Works Better

- Unlike **segment trees**, it's simpler to implement and uses **less memory** (O(n)).
- Unlike **prefix arrays**, updates are fast.
- Unlike **simple loops**, queries are fast.

## Example

Array: `[3, 2, -1, 6, 5, 4, -3, 3]`

Fenwick Tree internal representation stores **partial sums** like:

- Index 1 → sum of 1 element
- Index 2 → sum of 2 elements
- Index 4 → sum of 4 elements
- Index 8 → sum of 8 elements

This overlapping structure allows **logarithmic traversal** for both updates and queries.

## Summary Table

|Operation|Naïve Loop|Prefix Array|Fenwick Tree|
|---|---|---|---|
|Prefix Sum|O(n)|O(1)|O(log⁡ n)|
|Update Value|O(1)|O(n)|O(log⁡ n)|
|Memory Usage|O(1)|O(n)|O(n)|
|Ease of Coding|Easy|Easy|Moderate|

---

  

## ==What is a Fenwick Tree==

## Definition

A **Fenwick Tree**, also known as a **Binary Indexed Tree (BIT)**, is a data structure that efficiently supports:

- **Prefix sum queries** (sum from index 1 to i)
- **Updates** (change the value at a specific index)

Both operations work in **O(log⁡ n)** time using an **array-based tree structure**.

## Key Idea

The Fenwick Tree stores **partial sums** of the array in a way that allows:

- Quickly computing prefix sums by **jumping across overlapping ranges**.
- Quickly updating sums by **propagating changes to relevant ranges**.

It achieves this using **index manipulation based on the binary representation of indices**.

## How It Works

1. **Array Indexing Rule**:
    
    - Each index `i` in the Fenwick Tree covers a **range length** equal to the value of its **least significant bit (LSB)**.
    - LSB is found with:
    
    LSB(i)=i&(−i)
    
2. **Prefix Sum Query**:
    - Start at index `i` and move **backwards** by subtracting the LSB each time.
    - Sum all the ranges you pass through.
3. **Update**:
    - Start at index `i` and move **forwards** by adding the LSB each time.
    - Update all ranges that include `i`.

## Example

Original Array: `[3, 2, -1, 6, 5, 4, -3, 3]`

Fenwick Tree Internal Array (1-indexed):

|Index|Stores sum of:|
|---|---|
|1|A[1]|
|2|A[1] + A[2]|
|3|A[3]|
|4|A[1] + A[2] + A[3] + A[4]|
|5|A[5]|
|6|A[5] + A[6]|
|7|A[7]|
|8|A[1] + A[2] + ... + A[8]|

## Complexity

|Operation|Time Complexity|Space Complexity|
|---|---|---|
|Prefix Sum Query|O(log⁡ n)|O(n)|
|Update Value|O(log⁡ n)|O(n)|

## Advantages

- **Efficient** — Both queries and updates are O(log⁡ n).
- **Simple** — Easier to implement than a Segment Tree.
- **Memory Efficient** — Requires only O(n) space.

---

  

## ==Complexity Analysis==

## Time Complexity

|Operation|Steps Involved|Complexity|
|---|---|---|
|**Prefix Sum Query**|Traverses indices by subtracting LSB until reaching index 0. At most log⁡_2 n steps.|**O(log⁡ n)**|
|**Update Value**|Traverses indices by adding LSB until exceeding array size. At most log⁡_2 n steps.|**O(log⁡ n)**|
|**Build from Array**|If built by calling `update` for each element → n ⋅ O(log⁡ n). Optimized build possible in O(n)|**O(n log ⁡n)** (or **O(n)** optimized)|

## Space Complexity

- **Storage Requirement**:
    
    - Fenwick Tree uses **one extra array** of size n+1 (1-indexed).
    - Space usage: **O(n)**.
    
      
    

## Comparison with Other Approaches

|Operation|Naïve Loop|Prefix Sum Array|Fenwick Tree|Segment Tree|
|---|---|---|---|---|
|Prefix Sum Query|O(n)|O(1)|O(log⁡ n)|O(log ⁡n)|
|Update Value|O(1)|O(n)|O(log⁡ n)|O(log⁡ n)|
|Build Structure|O(1)|O(n)|O(n log ⁡n) O(n) optimized|O(n)|
|Space Usage|O(1)|O(n)|O(n)|O(2n)|

## Summary

- **Best for**: Fast updates + fast prefix queries in **dynamic arrays**.
- **Performance sweet spot** when nnn is large and **updates/queries are frequent**.
- **Limitations**:
    - Only supports operations that can be expressed as **invertible prefix operations** (like sum, XOR, min if carefully adapted).
    - Does not directly handle range updates without modification.

---

  

# ==Implementation Details==

---

  

## ==Range Query==

## 1. Problem

A **Fenwick Tree** natively supports **prefix sum queries**:

$$prefixSum(i)=A[1]+A[2]+⋯+A[i]$$

To get the **sum over a range** [l,r]:

$$rangeSum(l,r)=A[l]+A[l+1]+⋯+A[r]$$

We can use **prefix sums** to compute it in O(log⁡ n) time.

## 2. Formula

Given:

- `prefix_sum(i)` → sum of first `i` elements.

Range sum:

$$rangeSum(l,r)=prefixSum(r)−prefixSum(l−1)$$

## 3. Steps

1. Compute `sum_r = prefix_sum(r)`
2. Compute `sum_l_minus_1 = prefix_sum(l - 1)`
3. Return `sum_r - sum_l_minus_1`

## 4. Example

Array: `[3, 2, -1, 6, 5]`

- `prefix_sum(4) = 3 + 2 + (-1) + 6 = 10`
- `prefix_sum(2) = 3 + 2 = 5`
- **Range sum (3, 5)** = `prefix_sum(5) - prefix_sum(2)`
    
    → `(3 + 2 - 1 + 6 + 5) - (3 + 2)`
    
    → `15 - 5 = 10`
    

## 5. Complexity

|Operation|Complexity|
|---|---|
|Range Query|O(log⁡ n)|
|Update Value|O(log⁡ n)|

## 6. Summary Table

|Term|Meaning|
|---|---|
|`prefix_sum(i)`|Sum from index 1 to i|
|`range_sum(l, r)`|Sum from l to r|
|Formula|`prefix_sum(r) - prefix_sum(l-1)`|

---

  

## Point Updates

## 1. What is a Point Update?

A **point update** means changing the value of **a single element** in the original array, either by:

- **Adding** a value to it (`A[i] += delta`)
- **Setting** it to a new value (`A[i] = new_value`)

The Fenwick Tree efficiently updates all **relevant partial sums** affected by this change.

## 2. How It Works

- Each index in the Fenwick Tree stores the sum of a **range** of the original array.
- Updating one element affects all Fenwick Tree nodes that **cover** that element’s index.
- We find those nodes by repeatedly **adding the Least Significant Bit (LSB)** to the current index.

## 3. Algorithm (Add `delta` to `A[i]`)

1. Start at `index = i` (1-indexed).
2. While `index <= n`:
    - `tree[index] += delta`
    - `index += index & (-index)` ← move to the next responsible node.

## 4. Example

Original array: `[3, 2, -1, 6, 5]`

Fenwick tree built for this array.

**Update:** Add `+4` to `A[3]` (currently `-1` → becomes `3`).

Steps in Fenwick Tree:

- Update index 3 → add 4
- Move to index `3 + LSB(3) = 4` → add 4
- Move to index `4 + LSB(4) = 8` → stop (out of bounds).

## 5. Complexity

|Operation|Complexity|
|---|---|
|Point Update|O(log⁡ n)|

## 6. Summary Table

|Term|Meaning|
|---|---|
|LSB|Least Significant Bit (`index & -index`)|
|delta|Change applied to element|
|Point Update|Update a single element’s value in O(log ⁡n)|

---

  

## ==Fenwick Tree Construction==

## 1. Purpose

Before using a Fenwick Tree for updates and queries, we must **initialize** it based on the given array.

Construction can be done in **two main ways**:

1. **Naïve**: Repeatedly call `update()` for each element → O(n log ⁡n)
2. **Optimized**: Build directly in-place using range addition logic → O(n)

## 2. Method 1 — Naïve O(n log ⁡n)

- Start with an empty tree array of size n+1 (1-indexed).
- For each index `i` from 1 to n, call the `update(i, A[i])` function.
- Simple, but less efficient for large datasets.

## 3. Method 2 — Optimized O(n)

- Copy values from original array into tree array at same positions (1-indexed).
- For each index `i`, find its parent (`i + LSB(i)`) and add the value of `tree[i]` to `tree[parent]`.
- This way, sums propagate to higher nodes directly without extra update calls.

## 4. Example — Optimized Build

Given array A=[3,2,−1,6,5] (n = 5):

**Step 1** — Initialize tree:

```Plain
Index:  1   2   3   4   5
Tree:   3   2  -1   6   5
```

**Step 2** — Propagate values:

- i = 1 → parent = 1 + LSB(1) = 2 → tree[2] += tree[1] → tree[2] = 5
- i = 2 → parent = 4 → tree[4] += tree[2] → tree[4] = 11
- i = 3 → parent = 4 → tree[4] += tree[3] → tree[4] = 10 (11 + -1)
- i = 4 → parent = 8 (stop)
- i = 5 → parent = 6 (stop)

Final tree array (1-indexed):

```Plain
[0, 3, 5, -1, 10, 5]
```

## 5. Complexity

|Method|Time Complexity|Space Complexity|
|---|---|---|
|Naïve Build|O(n log⁡ n)|O(n)|
|Optimized|O(n)|O(n)|

## 6. Summary Table

|Step|Description|
|---|---|
|Naïve|Use update() for each element|
|Optimized|Directly propagate values using LSB|
|Advantage|Faster build for large n (O(n))|

---

  

# ==Code Implementation==

---

### Python

```C++
class FenwickTree:
    """
    Binary Indexed Tree (Fenwick Tree) implementation
    Supports range sum queries and point updates in O(log n) time
    """
    
    def __init__(self, n):
        """Initialize Fenwick Tree with size n"""
        self.n = n
        self.tree = [0] * (n + 1)  # 1-indexed
    
    def update(self, i, delta):
        """Add delta to element at index i (1-indexed)"""
        while i <= self.n:
            self.tree[i] += delta
            i += i & (-i)  # Add last set bit
    
    def query(self, i):
        """Get prefix sum from index 1 to i (1-indexed)"""
        result = 0
        while i > 0:
            result += self.tree[i]
            i -= i & (-i)  # Remove last set bit
        return result
    
    def range_query(self, l, r):
        """Get sum from index l to r (1-indexed, inclusive)"""
        return self.query(r) - self.query(l - 1)
    
    def build(self, arr):
        """Build tree from array (0-indexed input array)"""
        for i, val in enumerate(arr):
            self.update(i + 1, val)


# Example usage
if __name__ == "__main__":
    # Create Fenwick Tree
    arr = [1, 3, 5, 7, 9, 11]
    ft = FenwickTree(len(arr))
    ft.build(arr)
    
    # Test queries
    print(f"Prefix sum up to index 3: {ft.query(3)}")  # 1+3+5 = 9
    print(f"Range sum [2,4]: {ft.range_query(2, 4)}")  # 3+5+7 = 15
    
    # Update and test again
    ft.update(3, 2)  # Add 2 to element at index 3
    print(f"After update, range sum [2,4]: {ft.range_query(2, 4)}")  # 3+7+7 = 17
```

### C#

```C++
using System;

/// <summary>
/// Binary Indexed Tree (Fenwick Tree) implementation
/// Supports range sum queries and point updates in O(log n) time
/// </summary>
public class FenwickTree
{
    private int n;
    private long[] tree;

    /// <summary>
    /// Initialize Fenwick Tree with size n
    /// </summary>
    /// <param name="size">Size of the array</param>
    public FenwickTree(int size)
    {
        n = size;
        tree = new long[n + 1]; // 1-indexed
    }

    /// <summary>
    /// Add delta to element at index i (1-indexed)
    /// </summary>
    /// <param name="i">Index (1-indexed)</param>
    /// <param name="delta">Value to add</param>
    public void Update(int i, long delta)
    {
        while (i <= n)
        {
            tree[i] += delta;
            i += i & (-i); // Add last set bit
        }
    }

    /// <summary>
    /// Get prefix sum from index 1 to i (1-indexed)
    /// </summary>
    /// <param name="i">Index (1-indexed)</param>
    /// <returns>Prefix sum</returns>
    public long Query(int i)
    {
        long result = 0;
        while (i > 0)
        {
            result += tree[i];
            i -= i & (-i); // Remove last set bit
        }
        return result;
    }

    /// <summary>
    /// Get sum from index l to r (1-indexed, inclusive)
    /// </summary>
    /// <param name="l">Left index</param>
    /// <param name="r">Right index</param>
    /// <returns>Range sum</returns>
    public long RangeQuery(int l, int r)
    {
        return Query(r) - Query(l - 1);
    }

    /// <summary>
    /// Build tree from array (0-indexed input array)
    /// </summary>
    /// <param name="arr">Input array</param>
    public void Build(int[] arr)
    {
        for (int i = 0; i < arr.Length; i++)
        {
            Update(i + 1, arr[i]);
        }
    }
}

// Example usage
class Program
{
    static void Main()
    {
        // Create Fenwick Tree
        int[] arr = {1, 3, 5, 7, 9, 11};
        FenwickTree ft = new FenwickTree(arr.Length);
        ft.Build(arr);

        // Test queries
        Console.WriteLine($"Prefix sum up to index 3: {ft.Query(3)}"); // 1+3+5 = 9
        Console.WriteLine($"Range sum [2,4]: {ft.RangeQuery(2, 4)}"); // 3+5+7 = 15

        // Update and test again
        ft.Update(3, 2); // Add 2 to element at index 3
        Console.WriteLine($"After update, range sum [2,4]: {ft.RangeQuery(2, 4)}"); // 3+7+7 = 17
    }
}
```

### C++

```C++
\#include <iostream>
\#include <vector>

/**
 * Binary Indexed Tree (Fenwick Tree) implementation
 * Supports range sum queries and point updates in O(log n) time
 */
class FenwickTree {
private:
    int n;
    std::vector<long long> tree;

public:
    /**
     * Initialize Fenwick Tree with size n
     */
    FenwickTree(int size) : n(size) {
        tree.resize(n + 1, 0); // 1-indexed
    }

    /**
     * Add delta to element at index i (1-indexed)
     */
    void update(int i, long long delta) {
        while (i <= n) {
            tree[i] += delta;
            i += i & (-i); // Add last set bit
        }
    }

    /**
     * Get prefix sum from index 1 to i (1-indexed)
     */
    long long query(int i) {
        long long result = 0;
        while (i > 0) {
            result += tree[i];
            i -= i & (-i); // Remove last set bit
        }
        return result;
    }

    /**
     * Get sum from index l to r (1-indexed, inclusive)
     */
    long long rangeQuery(int l, int r) {
        return query(r) - query(l - 1);
    }

    /**
     * Build tree from array (0-indexed input array)
     */
    void build(const std::vector<int>& arr) {
        for (int i = 0; i < arr.size(); i++) {
            update(i + 1, arr[i]);
        }
    }

    /**
     * Print tree for debugging
     */
    void print() {
        std::cout << "Tree: ";
        for (int i = 1; i <= n; i++) {
            std::cout << tree[i] << " ";
        }
        std::cout << std::endl;
    }
};

// Example usage
int main() {
    // Create Fenwick Tree
    std::vector<int> arr = {1, 3, 5, 7, 9, 11};
    FenwickTree ft(arr.size());
    ft.build(arr);

    // Test queries
    std::cout << "Prefix sum up to index 3: " << ft.query(3) << std::endl; // 1+3+5 = 9
    std::cout << "Range sum [2,4]: " << ft.rangeQuery(2, 4) << std::endl; // 3+5+7 = 15

    // Update and test again
    ft.update(3, 2); // Add 2 to element at index 3
    std::cout << "After update, range sum [2,4]: " << ft.rangeQuery(2, 4) << std::endl; // 3+7+7 = 17

    return 0;
	}z
```

---