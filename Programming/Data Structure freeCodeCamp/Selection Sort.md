---
Created: 2025-08-16T09:51
tags:
  - BroCode
---
## ==What is Selection Sort==

## **Definition**

**Selection Sort** is a simple **comparison-based sorting algorithm**.

It works by **repeatedly finding the smallest (or largest) element** from the unsorted part of the array and moving it to its correct position in the sorted part.

## **How it Works**

1. Start with the first element.
2. Find the **minimum element** in the unsorted portion.
3. Swap it with the first element.
4. Move the boundary of the sorted portion one step forward.
5. Repeat until the array is completely sorted.

## **Complexity**

- **Best Case:** O(n²)
- **Worst Case:** O(n²)
- **Average Case:** O(n²)
- **Space Complexity:** O(1) (in-place sorting)

## **When to Use**

- Small datasets.
- When **memory space is very limited** (since it’s in-place).
- Not efficient for large datasets compared to algorithms like QuickSort or MergeSort.

## **Example**

```Plain
Array: [64, 25, 12, 22, 11]

Pass 1: Minimum = 11 → swap with 64
[11, 25, 12, 22, 64]

Pass 2: Minimum = 12 → swap with 25
[11, 12, 25, 22, 64]

Pass 3: Minimum = 22 → swap with 25
[11, 12, 22, 25, 64]

Pass 4: Minimum = 25 → already in place
[11, 12, 22, 25, 64]

Sorted Array: [11, 12, 22, 25, 64]
```

---

  

## ==Where to use Selection Sort==

**Selection Sort** is simple but **inefficient for large datasets**. It’s best suited for specific scenarios:

## **1. Small Datasets**

- Works well on **small arrays or lists** because its simplicity outweighs inefficiency.
- Example: Sorting a few test scores or short lists of names.

## **2. Memory-Limited Situations**

- Selection Sort is **in-place** and does not require extra memory.
- Space Complexity = O(1).
- Useful when **minimizing memory usage is important**.

## **3. When Writing Simple, Predictable Code**

- Easy to implement and understand.
- Example: Teaching sorting concepts or simple scripts.

## **4. Minimal Swaps Required**

- Selection Sort performs **at most n-1 swaps**, which is fewer than Bubble Sort in some cases.
- Useful when **swaps are costly** (e.g., writing to flash memory).

## **When NOT to Use**

- Large datasets (O(n²) time complexity).
- Datasets that require **stable sorting**, because Selection Sort is **not stable** by default.

## **Summary Table**

|Condition|Selection Sort Suitable?|
|---|---|
|Small dataset|✅|
|Memory-limited environment|✅|
|Large dataset|❌|
|Need stable sorting|❌|
|Minimal swaps required|✅|

---

  

## ==Complexity Analysis==

**Selection Sort** repeatedly finds the minimum (or maximum) element from the unsorted part of the array and swaps it with the first unsorted element.

## **Time Complexity**

|Case|Description|Complexity|
|---|---|---|
|**Best Case**|Array is already sorted|O(n²)|
|**Worst Case**|Array is reverse sorted|O(n²)|
|**Average Case**|Array is in random order|O(n²)|

- `n` = number of elements in the array.
- **Number of comparisons** is always the same: n*(n-1)/2 → O(n²).
- Number of swaps is at most n-1, which is **less than Bubble Sort** in some cases.

## **Space Complexity**

- Selection Sort is **in-place** → no extra array needed.
- **Space Complexity:** O(1)

## **Summary**

- Simple, predictable algorithm.
- Not efficient for large datasets due to **O(n²) time complexity**.
- Best when memory is limited or **few swaps** are preferred.
- Not stable by default.

---

  

## ==Code==

### Python

```Python
def selection_sort(arr):
    """
    Basic selection sort implementation.
    
    Args:
        arr: List of comparable elements
    
    Returns:
        Sorted list
    """
    n = len(arr)
    arr = arr.copy()  # Don't modify original array
    
    for i in range(n):
        # Find the minimum element in remaining unsorted array
        min_idx = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        
        # Swap the found minimum element with the first element
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
    
    return arr

def selection_sort_descending(arr):
    """
    Selection sort in descending order.
    
    Args:
        arr: List of comparable elements
    
    Returns:
        Sorted list in descending order
    """
    n = len(arr)
    arr = arr.copy()
    
    for i in range(n):
        # Find the maximum element in remaining unsorted array
        max_idx = i
        for j in range(i + 1, n):
            if arr[j] > arr[max_idx]:
                max_idx = j
        
        # Swap the found maximum element with the first element
        arr[i], arr[max_idx] = arr[max_idx], arr[i]
    
    return arr

def selection_sort_in_place(arr):
    """
    In-place selection sort that modifies the original array.
    
    Args:
        arr: List of comparable elements (modified in place)
    """
    n = len(arr)
    
    for i in range(n):
        min_idx = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        
        arr[i], arr[min_idx] = arr[min_idx], arr[i]

def selection_sort_with_stats(arr):
    """
    Selection sort that returns sorting statistics.
    
    Args:
        arr: List of comparable elements
    
    Returns:
        Tuple of (sorted_array, comparisons, swaps)
    """
    n = len(arr)
    arr = arr.copy()
    comparisons = 0
    swaps = 0
    
    for i in range(n):
        min_idx = i
        
        for j in range(i + 1, n):
            comparisons += 1
            if arr[j] < arr[min_idx]:
                min_idx = j
        
        if min_idx != i:
            arr[i], arr[min_idx] = arr[min_idx], arr[i]
            swaps += 1
    
    return arr, comparisons, swaps
```

```Python
def selection_sort_recursive(arr):
    """
    Recursive implementation of selection sort.
    
    Args:
        arr: List of comparable elements
    
    Returns:
        Sorted list
    """
    def selection_sort_rec(arr, start_idx):
        # Base case
        if start_idx >= len(arr):
            return
        
        # Find minimum element in remaining array
        min_idx = start_idx
        for i in range(start_idx + 1, len(arr)):
            if arr[i] < arr[min_idx]:
                min_idx = i
        
        # Swap minimum element with first element
        arr[start_idx], arr[min_idx] = arr[min_idx], arr[start_idx]
        
        # Recursively sort the rest
        selection_sort_rec(arr, start_idx + 1)
    
    arr = arr.copy()
    selection_sort_rec(arr, 0)
    return arr

def selection_sort_with_custom_key(arr, key_func=None, reverse=False):
    """
    Selection sort with custom comparison key.
    
    Args:
        arr: List of elements to sort
        key_func: Function to extract comparison key from each element
        reverse: If True, sort in descending order
    
    Returns:
        Sorted list
    """
    n = len(arr)
    arr = arr.copy()
    
    if key_func is None:
        key_func = lambda x: x
    
    for i in range(n):
        target_idx = i
        
        for j in range(i + 1, n):
            if reverse:
                if key_func(arr[j]) > key_func(arr[target_idx]):
                    target_idx = j
            else:
                if key_func(arr[j]) < key_func(arr[target_idx]):
                    target_idx = j
        
        arr[i], arr[target_idx] = arr[target_idx], arr[i]
    
    return arr

def find_kth_smallest(arr, k):
    """
    Find the kth smallest element using selection sort approach.
    
    Args:
        arr: List of comparable elements
        k: Position of element to find (1-indexed)
    
    Returns:
        The kth smallest element
    """
    if k < 1 or k > len(arr):
        raise ValueError("k must be between 1 and len(arr)")
    
    arr = arr.copy()
    n = len(arr)
    
    # Only need to do k iterations
    for i in range(k):
        min_idx = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
    
    return arr[k - 1]
```

```Python
if __name__ == "__main__":
    import random
    import time
    
    # Test arrays
    test_arrays = [
        [64, 34, 25, 12, 22, 11, 90],
        [5, 2, 4, 6, 1, 3],
        [1, 2, 3, 4, 5],  # Already sorted
        [5, 4, 3, 2, 1],  # Reverse sorted
        [42],             # Single element
        [],               # Empty array
        [3, 3, 3, 3, 3],  # All same elements
        [1, 3, 2, 3, 1]   # Duplicates
    ]
    
    print("=== Selection Sort Implementations ===\n")
    
    for i, arr in enumerate(test_arrays):
        print(f"Test {i + 1}: {arr}")
        
        # Basic selection sort
        sorted_arr = selection_sort(arr)
        print(f"Ascending:   {sorted_arr}")
        
        # Descending order
        sorted_desc = selection_sort_descending(arr)
        print(f"Descending:  {sorted_desc}")
        
        # With statistics
        sorted_arr, comps, swaps = selection_sort_with_stats(arr)
        print(f"Stats:       {sorted_arr} (Comparisons: {comps}, Swaps: {swaps})")
        
        # Recursive
        sorted_rec = selection_sort_recursive(arr)
        print(f"Recursive:   {sorted_rec}")
        
        print()
    
    # Test custom key function
    print("=== Custom Key Function Examples ===")
    
    # Sort strings by length
    strings = ["python", "java", "c", "javascript", "go"]
    print(f"Original strings: {strings}")
    sorted_by_length = selection_sort_with_custom_key(strings, key_func=len)
    print(f"Sorted by length: {sorted_by_length}")
    
    # Sort tuples by second element
    tuples = [(1, 5), (3, 2), (2, 8), (4, 1)]
    print(f"Original tuples: {tuples}")
    sorted_tuples = selection_sort_with_custom_key(tuples, key_func=lambda x: x[1])
    print(f"Sorted by 2nd element: {sorted_tuples}")
    
    # Sort numbers by absolute value
    numbers = [-5, 2, -8, 1, -3, 7]
    print(f"Original numbers: {numbers}")
    sorted_abs = selection_sort_with_custom_key(numbers, key_func=abs)
    print(f"Sorted by absolute value: {sorted_abs}")
    
    print()
    
    # Test kth smallest element
    print("=== Finding Kth Smallest Element ===")
    test_arr = [7, 10, 4, 3, 20, 15]
    print(f"Array: {test_arr}")
    for k in range(1, len(test_arr) + 1):
        kth = find_kth_smallest(test_arr, k)
        print(f"{k}{'st' if k==1 else 'nd' if k==2 else 'rd' if k==3 else 'th'} smallest: {kth}")
    
    print()
    
    # Performance comparison
    print("=== Performance Test ===")
    sizes = [100, 500, 1000]
    
    for size in sizes:
        # Generate random array
        arr = [random.randint(1, 1000) for _ in range(size)]
        
        print(f"\nArray size: {size}")
        
        # Test selection sort
        start_time = time.time()
        selection_sort(arr)
        selection_time = time.time() - start_time
        
        # Test built-in sort for comparison
        start_time = time.time()
        sorted(arr)
        builtin_time = time.time() - start_time
        
        print(f"Selection sort: {selection_time:.4f}s")
        print(f"Built-in sort:  {builtin_time:.4f}s")
        if builtin_time > 0:
            print(f"Ratio:          {selection_time / builtin_time:.1f}x slower")
    
    print("\n=== Algorithm Analysis ===")
    print("Time Complexity:")
    print("  - Best case:    O(n²) - always performs same number of comparisons")
    print("  - Average case: O(n²)")
    print("  - Worst case:   O(n²)")
    print("\nSpace Complexity: O(1) - constant extra space")
    print("\nCharacteristics:")
    print("  - Unstable: Equal elements may not maintain relative order")
    print("  - In-place: Sorts without using extra space")
    print("  - Minimum swaps: At most n-1 swaps (better than bubble sort)")
    print("  - Good for: Small datasets, when swap cost is high")
```

### C#

```C#
using System;
using System.Diagnostics;

public class SelectionSort
{
    /// <summary>
    /// Basic selection sort implementation.
    /// </summary>
    /// <param name="arr">Array to sort</param>
    /// <returns>New sorted array</returns>
    public static int[] Sort(int[] arr)
    {
        int[] result = new int[arr.Length];
        Array.Copy(arr, result, arr.Length);
        
        int n = result.Length;
        
        for (int i = 0; i < n - 1; i++)
        {
            // Find the minimum element in remaining unsorted array
            int minIdx = i;
            for (int j = i + 1; j < n; j++)
            {
                if (result[j] < result[minIdx])
                {
                    minIdx = j;
                }
            }
            
            // Swap the found minimum element with the first element
            if (minIdx != i)
            {
                int temp = result[i];
                result[i] = result[minIdx];
                result[minIdx] = temp;
            }
        }
        
        return result;
    }
    
    /// <summary>
    /// Selection sort in descending order.
    /// </summary>
    /// <param name="arr">Array to sort</param>
    /// <returns>New sorted array in descending order</returns>
    public static int[] SortDescending(int[] arr)
    {
        int[] result = new int[arr.Length];
        Array.Copy(arr, result, arr.Length);
        
        int n = result.Length;
        
        for (int i = 0; i < n - 1; i++)
        {
            // Find the maximum element in remaining unsorted array
            int maxIdx = i;
            for (int j = i + 1; j < n; j++)
            {
                if (result[j] > result[maxIdx])
                {
                    maxIdx = j;
                }
            }
            
            // Swap the found maximum element with the first element
            if (maxIdx != i)
            {
                int temp = result[i];
                result[i] = result[maxIdx];
                result[maxIdx] = temp;
            }
        }
        
        return result;
    }
    
    /// <summary>
    /// In-place selection sort that modifies the original array.
    /// </summary>
    /// <param name="arr">Array to sort (modified in place)</param>
    public static void SortInPlace(int[] arr)
    {
        int n = arr.Length;
        
        for (int i = 0; i < n - 1; i++)
        {
            int minIdx = i;
            for (int j = i + 1; j < n; j++)
            {
                if (arr[j] < arr[minIdx])
                {
                    minIdx = j;
                }
            }
            
            if (minIdx != i)
            {
                int temp = arr[i];
                arr[i] = arr[minIdx];
                arr[minIdx] = temp;
            }
        }
    }
    
    /// <summary>
    /// Selection sort with statistics tracking.
    /// </summary>
    /// <param name="arr">Array to sort</param>
    /// <returns>Tuple with sorted array, comparisons count, and swaps count</returns>
    public static (int[] sortedArray, int comparisons, int swaps) SortWithStats(int[] arr)
    {
        int[] result = new int[arr.Length];
        Array.Copy(arr, result, arr.Length);
        
        int n = result.Length;
        int comparisons = 0;
        int swaps = 0;
        
        for (int i = 0; i < n - 1; i++)
        {
            int minIdx = i;
            
            for (int j = i + 1; j < n; j++)
            {
                comparisons++;
                if (result[j] < result[minIdx])
                {
                    minIdx = j;
                }
            }
            
            if (minIdx != i)
            {
                int temp = result[i];
                result[i] = result[minIdx];
                result[minIdx] = temp;
                swaps++;
            }
        }
        
        return (result, comparisons, swaps);
    }
    
    /// <summary>
    /// Generic selection sort for any comparable type.
    /// </summary>
    /// <typeparam name="T">Type that implements IComparable</typeparam>
    /// <param name="arr">Array to sort</param>
    /// <returns>New sorted array</returns>
    public static T[] SortGeneric<T>(T[] arr) where T : IComparable<T>
    {
        T[] result = new T[arr.Length];
        Array.Copy(arr, result, arr.Length);
        
        int n = result.Length;
        
        for (int i = 0; i < n - 1; i++)
        {
            int minIdx = i;
            for (int j = i + 1; j < n; j++)
            {
                if (result[j].CompareTo(result[minIdx]) < 0)
                {
                    minIdx = j;
                }
            }
            
            if (minIdx != i)
            {
                T temp = result[i];
                result[i] = result[minIdx];
                result[minIdx] = temp;
            }
        }
        
        return result;
    }
    
    /// <summary>
    /// Generic selection sort with custom comparer.
    /// </summary>
    /// <typeparam name="T">Type of elements</typeparam>
    /// <param name="arr">Array to sort</param>
    /// <param name="comparer">Custom comparer function</param>
    /// <returns>New sorted array</returns>
    public static T[] SortWithComparer<T>(T[] arr, Func<T, T, int> comparer)
    {
        T[] result = new T[arr.Length];
        Array.Copy(arr, result, arr.Length);
        
        int n = result.Length;
        
        for (int i = 0; i < n - 1; i++)
        {
            int targetIdx = i;
            for (int j = i + 1; j < n; j++)
            {
                if (comparer(result[j], result[targetIdx]) < 0)
                {
                    targetIdx = j;
                }
            }
            
            if (targetIdx != i)
            {
                T temp = result[i];
                result[i] = result[targetIdx];
                result[targetIdx] = temp;
            }
        }
        
        return result;
    }
    
    /// <summary>
    /// Recursive implementation of selection sort.
    /// </summary>
    /// <param name="arr">Array to sort</param>
    /// <returns>New sorted array</returns>
    public static int[] SortRecursive(int[] arr)
    {
        int[] result = new int[arr.Length];
        Array.Copy(arr, result, arr.Length);
        
        SelectionSortRecursive(result, 0);
        
        return result;
    }
    
    private static void SelectionSortRecursive(int[] arr, int startIdx)
    {
        // Base case
        if (startIdx >= arr.Length - 1)
            return;
        
        // Find minimum element in remaining array
        int minIdx = startIdx;
        for (int i = startIdx + 1; i < arr.Length; i++)
        {
            if (arr[i] < arr[minIdx])
            {
                minIdx = i;
            }
        }
        
        // Swap minimum element with first element
        if (minIdx != startIdx)
        {
            int temp = arr[startIdx];
            arr[startIdx] = arr[minIdx];
            arr[minIdx] = temp;
        }
        
        // Recursively sort the rest
        SelectionSortRecursive(arr, startIdx + 1);
    }
    
    /// <summary>
    /// Find the kth smallest element using selection sort approach.
    /// </summary>
    /// <param name="arr">Array to search in</param>
    /// <param name="k">Position of element to find (1-indexed)</param>
    /// <returns>The kth smallest element</returns>
    public static int FindKthSmallest(int[] arr, int k)
    {
        if (k < 1 || k > arr.Length)
            throw new ArgumentException("k must be between 1 and arr.Length");
        
        int[] result = new int[arr.Length];
        Array.Copy(arr, result, arr.Length);
        
        // Only need to do k iterations
        for (int i = 0; i < k; i++)
        {
            int minIdx = i;
            for (int j = i + 1; j < result.Length; j++)
            {
                if (result[j] < result[minIdx])
                {
                    minIdx = j;
                }
            }
            
            if (minIdx != i)
            {
                int temp = result[i];
                result[i] = result[minIdx];
                result[minIdx] = temp;
            }
        }
        
        return result[k - 1];
    }
}
```

```C#
class Program
{
    static void Main(string[] args)
    {
        // Test arrays
        int[][] testArrays = {
            new int[] { 64, 34, 25, 12, 22, 11, 90 },
            new int[] { 5, 2, 4, 6, 1, 3 },
            new int[] { 1, 2, 3, 4, 5 },    // Already sorted
            new int[] { 5, 4, 3, 2, 1 },    // Reverse sorted
            new int[] { 42 },               // Single element
            new int[] { },                  // Empty array
            new int[] { 3, 3, 3, 3, 3 },    // All same elements
            new int[] { 1, 3, 2, 3, 1 }     // Duplicates
        };
        
        Console.WriteLine("=== Selection Sort Implementations ===\n");
        
        for (int i = 0; i < testArrays.Length; i++)
        {
            int[] arr = testArrays[i];
            Console.WriteLine($"Test {i + 1}: [{string.Join(", ", arr)}]");
            
            // Basic selection sort
            int[] sorted = SelectionSort.Sort(arr);
            Console.WriteLine($"Ascending:   [{string.Join(", ", sorted)}]");
            
            // Descending order
            int[] sortedDesc = SelectionSort.SortDescending(arr);
            Console.WriteLine($"Descending:  [{string.Join(", ", sortedDesc)}]");
            
            // With statistics
            var (sortedWithStats, comparisons, swaps) = SelectionSort.SortWithStats(arr);
            Console.WriteLine($"Stats:       [{string.Join(", ", sortedWithStats)}] (Comparisons: {comparisons}, Swaps: {swaps})");
            
            // Recursive
            int[] sortedRec = SelectionSort.SortRecursive(arr);
            Console.WriteLine($"Recursive:   [{string.Join(", ", sortedRec)}]");
            
            Console.WriteLine();
        }
        
        // Test generic version with strings
        string[] stringArray = { "banana", "apple", "cherry", "date" };
        Console.WriteLine($"String array: [{string.Join(", ", stringArray)}]");
        string[] sortedStrings = SelectionSort.SortGeneric(stringArray);
        Console.WriteLine($"Sorted:       [{string.Join(", ", sortedStrings)}]\n");
        
        // Test custom comparer - sort strings by length
        string[] strings = { "python", "java", "c", "javascript", "go" };
        Console.WriteLine($"Original strings: [{string.Join(", ", strings)}]");
        string[] sortedByLength = SelectionSort.SortWithComparer(strings, 
            (s1, s2) => s1.Length.CompareTo(s2.Length));
        Console.WriteLine($"Sorted by length: [{string.Join(", ", sortedByLength)}]\n");
        
        // Test kth smallest element
        Console.WriteLine("=== Finding Kth Smallest Element ===");
        int[] testArr = { 7, 10, 4, 3, 20, 15 };
        Console.WriteLine($"Array: [{string.Join(", ", testArr)}]");
        for (int k = 1; k <= testArr.Length; k++)
        {
            int kth = SelectionSort.FindKthSmallest(testArr, k);
            string suffix = k == 1 ? "st" : k == 2 ? "nd" : k == 3 ? "rd" : "th";
            Console.WriteLine($"{k}{suffix} smallest: {kth}");
        }
        
        Console.WriteLine();
        
        // Performance test
        Console.WriteLine("=== Performance Test ===");
        int[] sizes = { 1000, 2000, 5000 };
        
        foreach (int size in sizes)
        {
            // Generate random array
            Random rand = new Random();
            int[] arr = new int[size];
            for (int i = 0; i < size; i++)
                arr[i] = rand.Next(1, 1000);
            
            Console.WriteLine($"\nArray size: {size}");
            
            // Test selection sort
            Stopwatch sw = Stopwatch.StartNew();
            SelectionSort.Sort(arr);
            sw.Stop();
            double selectionTime = sw.Elapsed.TotalMilliseconds;
            
            // Test built-in sort for comparison
            int[] arrCopy = new int[arr.Length];
            Array.Copy(arr, arrCopy, arr.Length);
            sw.Restart();
            Array.Sort(arrCopy);
            sw.Stop();
            double builtinTime = sw.Elapsed.TotalMilliseconds;
            
            Console.WriteLine($"Selection sort: {selectionTime:F2}ms");
            Console.WriteLine($"Built-in sort:  {builtinTime:F2}ms");
            
            if (builtinTime > 0)
            {
                double ratio = selectionTime / builtinTime;
                Console.WriteLine($"Ratio:          {ratio:F1}x slower");
            }
        }
        
        Console.WriteLine("\n=== Algorithm Analysis ===");
        Console.WriteLine("Time Complexity:");
        Console.WriteLine("  - Best case:    O(n²) - always performs same number of comparisons");
        Console.WriteLine("  - Average case: O(n²)");
        Console.WriteLine("  - Worst case:   O(n²)");
        Console.WriteLine("\nSpace Complexity: O(1) - constant extra space");
        Console.WriteLine("\nCharacteristics:");
        Console.WriteLine("  - Unstable: Equal elements may not maintain relative order");
        Console.WriteLine("  - In-place: Sorts without using extra space");
        Console.WriteLine("  - Minimum swaps: At most n-1 swaps (better than bubble sort)");
        Console.WriteLine("  - Good for: Small datasets, when swap cost is high");
    }
}
```

### C++

```C++
\#include <iostream>
\#include <vector>
\#include <chrono>
\#include <random>
\#include <algorithm>
\#include <tuple>
\#include <string>
\#include <functional>

class SelectionSort {
public:
    /**
     * Basic selection sort implementation.
     * @param arr Vector to sort
     * @return New sorted vector
     */
    static std::vector<int> sort(const std::vector<int>& arr) {
        std::vector<int> result = arr;
        int n = result.size();
        
        for (int i = 0; i < n - 1; i++) {
            // Find the minimum element in remaining unsorted array
            int minIdx = i;
            for (int j = i + 1; j < n; j++) {
                if (result[j] < result[minIdx]) {
                    minIdx = j;
                }
            }
            
            // Swap the found minimum element with the first element
            if (minIdx != i) {
                std::swap(result[i], result[minIdx]);
            }
        }
        
        return result;
    }
    
    /**
     * Selection sort in descending order.
     * @param arr Vector to sort
     * @return New sorted vector in descending order
     */
    static std::vector<int> sortDescending(const std::vector<int>& arr) {
        std::vector<int> result = arr;
        int n = result.size();
        
        for (int i = 0; i < n - 1; i++) {
            // Find the maximum element in remaining unsorted array
            int maxIdx = i;
            for (int j = i + 1; j < n; j++) {
                if (result[j] > result[maxIdx]) {
                    maxIdx = j;
                }
            }
            
            // Swap the found maximum element with the first element
            if (maxIdx != i) {
                std::swap(result[i], result[maxIdx]);
            }
        }
        
        return result;
    }
    
    /**
     * In-place selection sort that modifies the original vector.
     * @param arr Vector to sort (modified in place)
     */
    static void sortInPlace(std::vector<int>& arr) {
        int n = arr.size();
        
        for (int i = 0; i < n - 1; i++) {
            int minIdx = i;
            for (int j = i + 1; j < n; j++) {
                if (arr[j] < arr[minIdx]) {
                    minIdx = j;
                }
            }
            
            if (minIdx != i) {
                std::swap(arr[i], arr[minIdx]);
            }
        }
    }
    
    /**
     * Selection sort with statistics tracking.
     * @param arr Vector to sort
     * @return Tuple with sorted vector, comparisons count, and swaps count
     */
    static std::tuple<std::vector<int>, int, int> sortWithStats(const std::vector<int>& arr) {
        std::vector<int> result = arr;
        int n = result.size();
        int comparisons = 0;
        int swaps = 0;
        
        for (int i = 0; i < n - 1; i++) {
            int minIdx = i;
            
            for (int j = i + 1; j < n; j++) {
                comparisons++;
                if (result[j] < result[minIdx]) {
                    minIdx = j;
                }
            }
            
            if (minIdx != i) {
                std::swap(result[i], result[minIdx]);
                swaps++;
            }
        }
        
        return std::make_tuple(result, comparisons, swaps);
    }
    
    /**
     * Template selection sort for any comparable type.
     * @param arr Vector to sort
     * @return New sorted vector
     */
    template<typename T>
    static std::vector<T> sortTemplate(const std::vector<T>& arr) {
        std::vector<T> result = arr;
        int n = result.size();
        
        for (int i = 0; i < n - 1; i++) {
            int minIdx = i;
            for (int j = i + 1; j < n; j++) {
                if (result[j] < result[minIdx]) {
                    minIdx = j;
                }
            }
            
            if (minIdx != i) {
                std::swap(result[i], result[minIdx]);
            }
        }
        
        return result;
    }
    
    /**
     * Template selection sort with custom comparator.
     * @param arr Vector to sort
     * @param comp Comparison function
     * @return New sorted vector
     */
    template<typename T, typename Compare>
    static std::vector<T> sortWithComparator(const std::vector<T>& arr, Compare comp) {
        std::vector<T> result = arr;
        int n = result.size();
        
        for (int i = 0; i < n - 1; i++) {
            int targetIdx = i;
            for (int j = i + 1; j < n; j++) {
                if (comp(result[j], result[targetIdx])) {
                    targetIdx = j;
                }
            }
            
            if (targetIdx != i) {
                std::swap(result[i], result[targetIdx]);
            }
        }
        
        return result;
    }
    
    /**
     * Recursive implementation of selection sort.
     * @param arr Vector to sort
     * @return New sorted vector
     */
    static std::vector<int> sortRecursive(const std::vector<int>& arr) {
        std::vector<int> result = arr;
        
        selectionSortRecursive(result, 0);
        
        return result;
    }
    
    /**
     * Find the kth smallest element using selection sort approach.
     * @param arr Vector to search in
     * @param k Position of element to find (1-indexed)
     * @return The kth smallest element
     */
    static int findKthSmallest(const std::vector<int>& arr, int k) {
        if (k < 1 || k > static_cast<int>(arr.size())) {
            throw std::invalid_argument("k must be between 1 and arr.size()");
        }
        
        std::vector<int> result = arr;
        int n = result.size();
        
        // Only need to do k iterations
        for (int i = 0; i < k; i++) {
            int minIdx = i;
            for (int j = i + 1; j < n; j++) {
                if (result[j] < result[minIdx]) {
                    minIdx = j;
                }
            }
            
            if (minIdx != i) {
                std::swap(result[i], result[minIdx]);
            }
        }
        
        return result[k - 1];
    }
```

```C#
private:
    static void selectionSortRecursive(std::vector<int>& arr, int startIdx) {
        // Base case
        if (startIdx >= static_cast<int>(arr.size()) - 1) {
            return;
        }
        
        // Find minimum element in remaining array
        int minIdx = startIdx;
        for (int i = startIdx + 1; i < static_cast<int>(arr.size()); i++) {
            if (arr[i] < arr[minIdx]) {
                minIdx = i;
            }
        }
        
        // Swap minimum element with first element
        if (minIdx != startIdx) {
            std::swap(arr[startIdx], arr[minIdx]);
        }
        
        // Recursively sort the rest
        selectionSortRecursive(arr, startIdx + 1);
    }
};

// Utility function to print vector
template<typename T>
void printVector(const std::vector<T>& vec) {
    std::cout << "[";
    for (size_t i = 0; i < vec.size(); i++) {
        std::cout << vec[i];
        if (i < vec.size() - 1) {
            std::cout << ", ";
        }
    }
    std::cout << "]";
}

int main() {
    // Test arrays
    std::vector<std::vector<int>> testArrays = {
        {64, 34, 25, 12, 22, 11, 90},
        {5, 2, 4, 6, 1, 3},
        {1, 2, 3, 4, 5},    // Already sorted
        {5, 4, 3, 2, 1},    // Reverse sorted
        {42},               // Single element
        {},                 // Empty array
        {3, 3, 3, 3, 3},    // All same elements
        {1, 3, 2, 3, 1}     // Duplicates
    };
    
    std::cout << "=== Selection Sort Implementations ===" << std::endl << std::endl;
    
    for (size_t i = 0; i < testArrays.size(); i++) {
        const auto& arr = testArrays[i];
        std::cout << "Test " << (i + 1) << ": ";
        printVector(arr);
        std::cout << std::endl;
        
        // Basic selection sort
        auto sorted = SelectionSort::sort(arr);
        std::cout << "Ascending:   ";
        printVector(sorted);
        std::cout << std::endl;
        
        // Descending order
        auto sortedDesc = SelectionSort::sortDescending(arr);
        std::cout << "Descending:  ";
        printVector(sortedDesc);
        std::cout << std::endl;
        
        // With statistics
        auto [sortedWithStats, comparisons, swaps] = SelectionSort::sortWithStats(arr);
        std::cout << "Stats:       ";
        printVector(sortedWithStats);
        std::cout << " (Comparisons: " << comparisons << ", Swaps: " << swaps << ")" << std::endl;
        
        // Recursive
        auto sortedRec = SelectionSort::sortRecursive(arr);
        std::cout << "Recursive:   ";
        printVector(sortedRec);
        std::cout << std::endl << std::endl;
    }
    
    // Test template version with strings
    std::vector<std::string> stringArray = {"banana", "apple", "cherry", "date"};
    std::cout << "String array: ";
    printVector(stringArray);
    std::cout << std::endl;
    
    auto sortedStrings = SelectionSort::sortTemplate(stringArray);
    std::cout << "Sorted:       ";
    printVector(sortedStrings);
    std::cout << std::endl << std::endl;
    
    // Test custom comparator - sort strings by length
    std::vector<std::string> strings = {"python", "java", "c", "javascript", "go"};
    std::cout << "Original strings: ";
    printVector(strings);
    std::cout << std::endl;
    
    auto sortedByLength = SelectionSort::sortWithComparator(strings, 
        [](const std::string& a, const std::string& b) {
            return a.length() < b.length();
        });
    std::cout << "Sorted by length: ";
    printVector(sortedByLength);
    std::cout << std::endl << std::endl;
    
    // Test with doubles using template
    std::vector<double> doubleArray = {3.14, 1.41, 2.71, 0.57};
    std::cout << "Double array: ";
    printVector(doubleArray);
    std::cout << std::endl;
    
    auto sortedDoubles = SelectionSort::sortTemplate(doubleArray);
    std::cout << "Sorted:       ";
    printVector(sortedDoubles);
    std::cout << std::endl << std::endl;
    
    // Sort by absolute value using custom comparator
    std::vector<int> numbers = {-5, 2, -8, 1, -3, 7};
    std::cout << "Original numbers: ";
    printVector(numbers);
    std::cout << std::endl;
    
    auto sortedByAbs = SelectionSort::sortWithComparator(numbers, 
        [](int a, int b) {
            return std::abs(a) < std::abs(b);
        });
    std::cout << "Sorted by absolute value: ";
    printVector(sortedByAbs);
    std::cout << std::endl << std::endl;
    
    // Test kth smallest element
    std::cout << "=== Finding Kth Smallest Element ===" << std::endl;
    std::vector<int> testArr = {7, 10, 4, 3, 20, 15};
    std::cout << "Array: ";
    printVector(testArr);
    std::cout << std::endl;
    
    for (int k = 1; k <= static_cast<int>(testArr.size()); k++) {
        int kth = SelectionSort::findKthSmallest(testArr, k);
        std::string suffix = (k == 1) ? "st" : (k == 2) ? "nd" : (k == 3) ? "rd" : "th";
        std::cout << k << suffix << " smallest: " << kth << std::endl;
    }
    
    std::cout << std::endl;
    
    // Performance test
    std::cout << "=== Performance Test ===" << std::endl;
    std::vector<int> sizes = {1000, 2000, 5000};
    
    std::random_device rd;
    std::mt19937 gen(rd());
    std::uniform_int_distribution<> dis(1, 1000);
    
    for (int size : sizes) {
        // Generate random array
        std::vector<int> arr(size);
        for (int& val : arr) {
            val = dis(gen);
        }
        
        std::cout << std::endl << "Array size: " << size << std::endl;
        
        // Test selection sort
        auto start = std::chrono::high_resolution_clock::now();
        SelectionSort::sort(arr);
        auto end = std::chrono::high_resolution_clock::now();
        auto selectionTime = std::chrono::duration_cast<std::chrono::milliseconds>(end - start).count();
        
        // Test built-in sort for comparison
        std::vector<int> arrCopy = arr;
        start = std::chrono::high_resolution_clock::now();
        std::sort(arrCopy.begin(), arrCopy.end());
        end = std::chrono::high_resolution_clock::now();
        auto builtinTime = std::chrono::duration_cast<std::chrono::milliseconds>(end - start).count();
        
        std::cout << "Selection sort: " << selectionTime << "ms" << std::endl;
        std::cout << "Built-in sort:  " << builtinTime << "ms" << std::endl;
        
        if (builtinTime > 0) {
            double ratio = static_cast<double>(selectionTime) / builtinTime;
            std::cout << "Ratio:          " << ratio << "x slower" << std::endl;
        }
    }
    
    // Memory usage test
    std::cout << std::endl << "=== Memory Usage Test ===" << std::endl;
    std::vector<int> largeArray(10000);
    for (int i = 0; i < 10000; i++) {
        largeArray[i] = dis(gen);
    }
    
    std::cout << "Testing in-place vs copy sorting..." << std::endl;
    
    // In-place sorting
    std::vector<int> inPlaceArray = largeArray;
    auto start = std::chrono::high_resolution_clock::now();
    SelectionSort::sortInPlace(inPlaceArray);
    auto end = std::chrono::high_resolution_clock::now();
    auto inPlaceTime = std::chrono::duration_cast<std::chrono::milliseconds>(end - start).count();
    
    // Copy sorting
    start = std::chrono::high_resolution_clock::now();
    auto copyResult = SelectionSort::sort(largeArray);
    end = std::chrono::high_resolution_clock::now();
    auto copyTime = std::chrono::duration_cast<std::chrono::milliseconds>(end - start).count();
    
    std::cout << "In-place sort: " << inPlaceTime << "ms" << std::endl;
    std::cout << "Copy sort:     " << copyTime << "ms" << std::endl;
    
    std::cout << std::endl << "=== Algorithm Analysis ===" << std::endl;
    std::cout << "Time Complexity:" << std::endl;
    std::cout << "  - Best case:    O(n²) - always performs same number of comparisons" << std::endl;
    std::cout << "  - Average case: O(n²)" << std::endl;
    std::cout << "  - Worst case:   O(n²)" << std::endl;
    std::cout << std::endl << "Space Complexity: O(1) - constant extra space" << std::endl;
    std::cout << std::endl << "Characteristics:" << std::endl;
    std::cout << "  - Unstable: Equal elements may not maintain relative order" << std::endl;
    std::cout << "  - In-place: Sorts without using extra space" << std::endl;
    std::cout << "  - Minimum swaps: At most n-1 swaps (better than bubble sort)" << std::endl;
    std::cout << "  - Good for: Small datasets, when swap cost is high" << std::endl;
    std::cout << std::endl << "Advantages:" << std::endl;
    std::cout << "  - Simple implementation" << std::endl;
    std::cout << "  - Performs well when memory write is expensive" << std::endl;
    std::cout << "  - Good for finding k smallest elements efficiently" << std::endl;
    std::cout << "  - Stable number of writes (exactly n-1 swaps)" << std::endl;
    
    return 0;
}
```

---