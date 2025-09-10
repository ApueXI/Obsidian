---
Created: 2025-08-16T09:51
tags:
  - BroCode
---
## ==What is Bubble Sort==

## **Definition**

**Bubble Sort** is a simple **sorting algorithm** that repeatedly **compares adjacent elements** in an array and **swaps them** if they are in the wrong order.

- This process is repeated **until the entire array is sorted**.
- The largest (or smallest) element "bubbles up" to its correct position in each pass.

## **How it Works**

1. Start from the beginning of the array.
2. Compare the first two elements:
    - If the first is greater than the second (for ascending sort), swap them.
3. Move to the next pair and repeat until the end of the array.
4. After one pass, the **largest element is at the end**.
5. Repeat the process for the remaining array (excluding the last sorted elements).
6. Continue until no swaps are needed.

## **Complexity**

- **Best Case:** O(n) → already sorted (optimized version)
- **Worst Case:** O(n²) → reverse sorted array
- **Average Case:** O(n²)
- **Space Complexity:** O(1) → in-place sorting

## **When to Use**

- Small datasets.
- Educational purposes (easy to understand).
- Rarely used in real-world large datasets because it is **inefficient**.

## **Example**

```Plain
Array: [5, 3, 8, 4, 2]

Pass 1:
[3, 5, 8, 4, 2] → swap 5 & 3
[3, 5, 8, 4, 2] → 5 & 8 no swap
[3, 5, 4, 8, 2] → swap 8 & 4
[3, 5, 4, 2, 8] → swap 8 & 2

Pass 2:
[3, 5, 4, 2, 8]
[3, 4, 5, 2, 8] → swap 5 & 4
[3, 4, 2, 5, 8] → swap 5 & 2
[3, 4, 2, 5, 8] → 5 & 8 no swap

Pass 3:
[3, 4, 2, 5, 8]
[3, 2, 4, 5, 8] → swap 4 & 2
[3, 2, 4, 5, 8] → 4 & 5 no swap
...
Final Sorted Array: [2, 3, 4, 5, 8]
```

---

  

## ==Where to use Bubble Sort==

**Bubble Sort** is simple but **inefficient for large datasets**. Use it in these scenarios:

## **1. Small Datasets**

- Works fine for **small arrays or lists** because the overhead of more complex sorting algorithms isn’t justified.
- Example: Sorting a few scores or names.

## **2. Educational Purposes**

- Great for **learning the basics of sorting algorithms**.
- Helps understand concepts like **swapping, iteration, and comparisons**.

## **3. Nearly Sorted Data**

- Bubble Sort can be **optimized** with a flag to detect no swaps.
- If the array is **almost sorted**, it performs better (O(n) in best case).
- Example: Sorting a nearly sorted leaderboard.

## **4. Stable Sorting Needed**

- Bubble Sort is **stable**: it preserves the relative order of equal elements.
- Useful when order matters for equal elements.
- Example: Sorting students by marks, keeping the original order for ties.

## **5. Simple Implementation Needed**

- When simplicity is more important than performance.
- Useful in **scripts or small programs** where performance isn’t critical.

## **Summary Table**

|Condition|Bubble Sort Suitable?|
|---|---|
|Small dataset|✅|
|Educational purposes|✅|
|Large dataset|❌|
|Nearly sorted data|✅|
|Stable sort required|✅|

---

  

## ==Complexity Analysis==

**Bubble Sort** repeatedly compares and swaps adjacent elements until the array is sorted.

## **Time Complexity**

|Case|Description|Complexity|
|---|---|---|
|**Best Case**|Array is **already sorted** (with optimization)|O(n)|
|**Worst Case**|Array is **reverse sorted**|O(n²)|
|**Average Case**|Array is in random order|O(n²)|

- `n` = number of elements in the array.
- Best case optimization requires a **swap flag** to stop if no swaps occur.

## **Space Complexity**

- Bubble Sort is **in-place**, so it requires **no extra space**.
- **Space Complexity:** O(1)

## **Summary**

- Simple and intuitive but inefficient for large datasets.
- Works best for **small or nearly sorted arrays**.
- Preserves the **relative order** of equal elements (**stable sort**).

---

  

## ==Code==

### Python

```Python
def bubble_sort(arr):
    """
    Basic bubble sort implementation.
    
    Args:
        arr: List of comparable elements
    
    Returns:
        Sorted list
    """
    n = len(arr)
    arr = arr.copy()  # Don't modify original array
    
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    
    return arr

def bubble_sort_optimized(arr):
    """
    Optimized bubble sort with early termination.
    Stops if no swaps are made in a pass (array is already sorted).
    
    Args:
        arr: List of comparable elements
    
    Returns:
        Sorted list
    """
    n = len(arr)
    arr = arr.copy()
    
    for i in range(n):
        swapped = False
        
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swapped = True
        
        # If no swapping occurred, array is sorted
        if not swapped:
            break
    
    return arr

def bubble_sort_in_place(arr):
    """
    In-place bubble sort that modifies the original array.
    
    Args:
        arr: List of comparable elements (modified in place)
    """
    n = len(arr)
    
    for i in range(n):
        swapped = False
        
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swapped = True
        
        if not swapped:
            break

def bubble_sort_with_stats(arr):
    """
    Bubble sort that returns sorting statistics.
    
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
        swapped = False
        
        for j in range(0, n - i - 1):
            comparisons += 1
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
                swaps += 1
                swapped = True
        
        if not swapped:
            break
    
    return arr, comparisons, swaps

def bubble_sort_recursive(arr):
    """
    Recursive implementation of bubble sort.
    
    Args:
        arr: List of comparable elements
    
    Returns:
        Sorted list
    """
    def bubble_sort_rec(arr, n):
        # Base case
        if n == 1:
            return
        
        # One pass of bubble sort
        for i in range(n - 1):
            if arr[i] > arr[i + 1]:
                arr[i], arr[i + 1] = arr[i + 1], arr[i]
        
        # Recursively sort the first n-1 elements
        bubble_sort_rec(arr, n - 1)
    
    arr = arr.copy()
    if len(arr) > 1:
        bubble_sort_rec(arr, len(arr))
    
    return arr

# Example usage and testing
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
        [3, 3, 3, 3, 3]   # All same elements
    ]
    
    print("=== Bubble Sort Implementations ===\n")
    
    for i, arr in enumerate(test_arrays):
        print(f"Test {i + 1}: {arr}")
        
        # Basic bubble sort
        sorted_arr = bubble_sort(arr)
        print(f"Basic:      {sorted_arr}")
        
        # Optimized bubble sort
        sorted_arr = bubble_sort_optimized(arr)
        print(f"Optimized:  {sorted_arr}")
        
        # With statistics
        sorted_arr, comps, swaps = bubble_sort_with_stats(arr)
        print(f"Stats:      {sorted_arr} (Comparisons: {comps}, Swaps: {swaps})")
        
        # Recursive
        sorted_arr = bubble_sort_recursive(arr)
        print(f"Recursive:  {sorted_arr}")
        
        print()
    
    # Performance demonstration
    print("=== Performance Test ===")
    sizes = [100, 500, 1000]
    
    for size in sizes:
        # Generate random array
        arr = [random.randint(1, 1000) for _ in range(size)]
        
        print(f"\nArray size: {size}")
        
        # Test basic bubble sort
        start_time = time.time()
        bubble_sort(arr)
        basic_time = time.time() - start_time
        
        # Test optimized bubble sort
        start_time = time.time()
        bubble_sort_optimized(arr)
        optimized_time = time.time() - start_time
        
        print(f"Basic time:     {basic_time:.4f}s")
        print(f"Optimized time: {optimized_time:.4f}s")
        print(f"Improvement:    {((basic_time - optimized_time) / basic_time * 100):.1f}%")
    
    print("\n=== Algorithm Analysis ===")
    print("Time Complexity:")
    print("  - Best case:    O(n) - when array is already sorted (optimized version)")
    print("  - Average case: O(n²)")
    print("  - Worst case:   O(n²) - when array is reverse sorted")
    print("\nSpace Complexity: O(1) - constant extra space")
    print("\nStable: Yes - equal elements maintain their relative order")
    print("In-place: Yes - sorts the array without using extra space")
```

### C#

```C#
using System;
using System.Diagnostics;

public class BubbleSort
{
    /// <summary>
    /// Basic bubble sort implementation.
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
            for (int j = 0; j < n - i - 1; j++)
            {
                if (result[j] > result[j + 1])
                {
                    // Swap elements
                    int temp = result[j];
                    result[j] = result[j + 1];
                    result[j + 1] = temp;
                }
            }
        }
        
        return result;
    }
    
    /// <summary>
    /// Optimized bubble sort with early termination.
    /// </summary>
    /// <param name="arr">Array to sort</param>
    /// <returns>New sorted array</returns>
    public static int[] SortOptimized(int[] arr)
    {
        int[] result = new int[arr.Length];
        Array.Copy(arr, result, arr.Length);
        
        int n = result.Length;
        
        for (int i = 0; i < n - 1; i++)
        {
            bool swapped = false;
            
            for (int j = 0; j < n - i - 1; j++)
            {
                if (result[j] > result[j + 1])
                {
                    // Swap elements
                    int temp = result[j];
                    result[j] = result[j + 1];
                    result[j + 1] = temp;
                    swapped = true;
                }
            }
            
            // If no swapping occurred, array is sorted
            if (!swapped)
                break;
        }
        
        return result;
    }
    
    /// <summary>
    /// In-place bubble sort that modifies the original array.
    /// </summary>
    /// <param name="arr">Array to sort (modified in place)</param>
    public static void SortInPlace(int[] arr)
    {
        int n = arr.Length;
        
        for (int i = 0; i < n - 1; i++)
        {
            bool swapped = false;
            
            for (int j = 0; j < n - i - 1; j++)
            {
                if (arr[j] > arr[j + 1])
                {
                    // Swap elements
                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                    swapped = true;
                }
            }
            
            if (!swapped)
                break;
        }
    }
    
    /// <summary>
    /// Bubble sort with statistics tracking.
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
            bool swapped = false;
            
            for (int j = 0; j < n - i - 1; j++)
            {
                comparisons++;
                if (result[j] > result[j + 1])
                {
                    // Swap elements
                    int temp = result[j];
                    result[j] = result[j + 1];
                    result[j + 1] = temp;
                    swaps++;
                    swapped = true;
                }
            }
            
            if (!swapped)
                break;
        }
        
        return (result, comparisons, swaps);
    }
    
    /// <summary>
    /// Generic bubble sort for any comparable type.
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
            bool swapped = false;
            
            for (int j = 0; j < n - i - 1; j++)
            {
                if (result[j].CompareTo(result[j + 1]) > 0)
                {
                    // Swap elements
                    T temp = result[j];
                    result[j] = result[j + 1];
                    result[j + 1] = temp;
                    swapped = true;
                }
            }
            
            if (!swapped)
                break;
        }
        
        return result;
    }
    
    /// <summary>
    /// Recursive implementation of bubble sort.
    /// </summary>
    /// <param name="arr">Array to sort</param>
    /// <returns>New sorted array</returns>
    public static int[] SortRecursive(int[] arr)
    {
        int[] result = new int[arr.Length];
        Array.Copy(arr, result, arr.Length);
        
        if (result.Length > 1)
            BubbleSortRecursive(result, result.Length);
        
        return result;
    }
    
    private static void BubbleSortRecursive(int[] arr, int n)
    {
        // Base case
        if (n == 1)
            return;
        
        // One pass of bubble sort
        for (int i = 0; i < n - 1; i++)
        {
            if (arr[i] > arr[i + 1])
            {
                int temp = arr[i];
                arr[i] = arr[i + 1];
                arr[i + 1] = temp;
            }
        }
        
        // Recursively sort the first n-1 elements
        BubbleSortRecursive(arr, n - 1);
    }
}

// Example usage and testing
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
            new int[] { 3, 3, 3, 3, 3 }     // All same elements
        };
        
        Console.WriteLine("=== Bubble Sort Implementations ===\n");
        
        for (int i = 0; i < testArrays.Length; i++)
        {
            int[] arr = testArrays[i];
            Console.WriteLine($"Test {i + 1}: [{string.Join(", ", arr)}]");
            
            // Basic bubble sort
            int[] sorted = BubbleSort.Sort(arr);
            Console.WriteLine($"Basic:      [{string.Join(", ", sorted)}]");
            
            // Optimized bubble sort
            sorted = BubbleSort.SortOptimized(arr);
            Console.WriteLine($"Optimized:  [{string.Join(", ", sorted)}]");
            
            // With statistics
            var (sortedWithStats, comparisons, swaps) = BubbleSort.SortWithStats(arr);
            Console.WriteLine($"Stats:      [{string.Join(", ", sortedWithStats)}] (Comparisons: {comparisons}, Swaps: {swaps})");
            
            // Recursive
            sorted = BubbleSort.SortRecursive(arr);
            Console.WriteLine($"Recursive:  [{string.Join(", ", sorted)}]");
            
            Console.WriteLine();
        }
        
        // Test generic version with strings
        string[] stringArray = { "banana", "apple", "cherry", "date" };
        Console.WriteLine($"String array: [{string.Join(", ", stringArray)}]");
        string[] sortedStrings = BubbleSort.SortGeneric(stringArray);
        Console.WriteLine($"Sorted:       [{string.Join(", ", sortedStrings)}]\n");
        
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
            
            // Test basic bubble sort
            Stopwatch sw = Stopwatch.StartNew();
            BubbleSort.Sort(arr);
            sw.Stop();
            double basicTime = sw.Elapsed.TotalMilliseconds;
            
            // Test optimized bubble sort
            sw.Restart();
            BubbleSort.SortOptimized(arr);
            sw.Stop();
            double optimizedTime = sw.Elapsed.TotalMilliseconds;
            
            Console.WriteLine($"Basic time:     {basicTime:F2}ms");
            Console.WriteLine($"Optimized time: {optimizedTime:F2}ms");
            
            if (basicTime > 0)
            {
                double improvement = ((basicTime - optimizedTime) / basicTime) * 100;
                Console.WriteLine($"Improvement:    {improvement:F1}%");
            }
        }
        
        Console.WriteLine("\n=== Algorithm Analysis ===");
        Console.WriteLine("Time Complexity:");
        Console.WriteLine("  - Best case:    O(n) - when array is already sorted (optimized version)");
        Console.WriteLine("  - Average case: O(n²)");
        Console.WriteLine("  - Worst case:   O(n²) - when array is reverse sorted");
        Console.WriteLine("\nSpace Complexity: O(1) - constant extra space");
        Console.WriteLine("\nStable: Yes - equal elements maintain their relative order");
        Console.WriteLine("In-place: Yes - sorts the array without using extra space");
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

class BubbleSort {
public:
    /**
     * Basic bubble sort implementation.
     * @param arr Vector to sort
     * @return New sorted vector
     */
    static std::vector<int> sort(const std::vector<int>& arr) {
        std::vector<int> result = arr;
        int n = result.size();
        
        for (int i = 0; i < n - 1; i++) {
            for (int j = 0; j < n - i - 1; j++) {
                if (result[j] > result[j + 1]) {
                    std::swap(result[j], result[j + 1]);
                }
            }
        }
        
        return result;
    }
    
    /**
     * Optimized bubble sort with early termination.
     * @param arr Vector to sort
     * @return New sorted vector
     */
    static std::vector<int> sortOptimized(const std::vector<int>& arr) {
        std::vector<int> result = arr;
        int n = result.size();
        
        for (int i = 0; i < n - 1; i++) {
            bool swapped = false;
            
            for (int j = 0; j < n - i - 1; j++) {
                if (result[j] > result[j + 1]) {
                    std::swap(result[j], result[j + 1]);
                    swapped = true;
                }
            }
            
            // If no swapping occurred, array is sorted
            if (!swapped) {
                break;
            }
        }
        
        return result;
    }
    
    /**
     * In-place bubble sort that modifies the original vector.
     * @param arr Vector to sort (modified in place)
     */
    static void sortInPlace(std::vector<int>& arr) {
        int n = arr.size();
        
        for (int i = 0; i < n - 1; i++) {
            bool swapped = false;
            
            for (int j = 0; j < n - i - 1; j++) {
                if (arr[j] > arr[j + 1]) {
                    std::swap(arr[j], arr[j + 1]);
                    swapped = true;
                }
            }
            
            if (!swapped) {
                break;
            }
        }
    }
    
    /**
     * Bubble sort with statistics tracking.
     * @param arr Vector to sort
     * @return Tuple with sorted vector, comparisons count, and swaps count
     */
    static std::tuple<std::vector<int>, int, int> sortWithStats(const std::vector<int>& arr) {
        std::vector<int> result = arr;
        int n = result.size();
        int comparisons = 0;
        int swaps = 0;
        
        for (int i = 0; i < n - 1; i++) {
            bool swapped = false;
            
            for (int j = 0; j < n - i - 1; j++) {
                comparisons++;
                if (result[j] > result[j + 1]) {
                    std::swap(result[j], result[j + 1]);
                    swaps++;
                    swapped = true;
                }
            }
            
            if (!swapped) {
                break;
            }
        }
        
        return std::make_tuple(result, comparisons, swaps);
    }
    
    /**
     * Template bubble sort for any comparable type.
     * @param arr Vector to sort
     * @return New sorted vector
     */
    template<typename T>
    static std::vector<T> sortTemplate(const std::vector<T>& arr) {
        std::vector<T> result = arr;
        int n = result.size();
        
        for (int i = 0; i < n - 1; i++) {
            bool swapped = false;
            
            for (int j = 0; j < n - i - 1; j++) {
                if (result[j] > result[j + 1]) {
                    std::swap(result[j], result[j + 1]);
                    swapped = true;
                }
            }
            
            if (!swapped) {
                break;
            }
        }
        
        return result;
    }
    
    /**
     * Recursive implementation of bubble sort.
     * @param arr Vector to sort
     * @return New sorted vector
     */
    static std::vector<int> sortRecursive(const std::vector<int>& arr) {
        std::vector<int> result = arr;
        
        if (result.size() > 1) {
            bubbleSortRecursive(result, result.size());
        }
        
        return result;
    }

private:
    static void bubbleSortRecursive(std::vector<int>& arr, int n) {
        // Base case
        if (n == 1) {
            return;
        }
        
        // One pass of bubble sort
        for (int i = 0; i < n - 1; i++) {
            if (arr[i] > arr[i + 1]) {
                std::swap(arr[i], arr[i + 1]);
            }
        }
        
        // Recursively sort the first n-1 elements
        bubbleSortRecursive(arr, n - 1);
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
        {3, 3, 3, 3, 3}     // All same elements
    };
    
    std::cout << "=== Bubble Sort Implementations ===" << std::endl << std::endl;
    
    for (size_t i = 0; i < testArrays.size(); i++) {
        const auto& arr = testArrays[i];
        std::cout << "Test " << (i + 1) << ": ";
        printVector(arr);
        std::cout << std::endl;
        
        // Basic bubble sort
        auto sorted = BubbleSort::sort(arr);
        std::cout << "Basic:      ";
        printVector(sorted);
        std::cout << std::endl;
        
        // Optimized bubble sort
        sorted = BubbleSort::sortOptimized(arr);
        std::cout << "Optimized:  ";
        printVector(sorted);
        std::cout << std::endl;
        
        // With statistics
        auto [sortedWithStats, comparisons, swaps] = BubbleSort::sortWithStats(arr);
        std::cout << "Stats:      ";
        printVector(sortedWithStats);
        std::cout << " (Comparisons: " << comparisons << ", Swaps: " << swaps << ")" << std::endl;
        
        // Recursive
        sorted = BubbleSort::sortRecursive(arr);
        std::cout << "Recursive:  ";
        printVector(sorted);
        std::cout << std::endl << std::endl;
    }
    
    // Test template version with strings
    std::vector<std::string> stringArray = {"banana", "apple", "cherry", "date"};
    std::cout << "String array: ";
    printVector(stringArray);
    std::cout << std::endl;
    
    auto sortedStrings = BubbleSort::sortTemplate(stringArray);
    std::cout << "Sorted:       ";
    printVector(sortedStrings);
    std::cout << std::endl << std::endl;
    
    // Test template version with doubles
    std::vector<double> doubleArray = {3.14, 1.41, 2.71, 0.57};
    std::cout << "Double array: ";
    printVector(doubleArray);
    std::cout << std::endl;
    
    auto sortedDoubles = BubbleSort::sortTemplate(doubleArray);
    std::cout << "Sorted:       ";
    printVector(sortedDoubles);
    std::cout << std::endl << std::endl;
    
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
        
        // Test basic bubble sort
        auto start = std::chrono::high_resolution_clock::now();
        BubbleSort::sort(arr);
        auto end = std::chrono::high_resolution_clock::now();
        auto basicTime = std::chrono::duration_cast<std::chrono::milliseconds>(end - start).count();
        
        // Test optimized bubble sort
        start = std::chrono::high_resolution_clock::now();
        BubbleSort::sortOptimized(arr);
        end = std::chrono::high_resolution_clock::now();
        auto optimizedTime = std::chrono::duration_cast<std::chrono::milliseconds>(end - start).count();
        
        std::cout << "Basic time:     " << basicTime << "ms" << std::endl;
        std::cout << "Optimized time: " << optimizedTime << "ms" << std::endl;
        
        if (basicTime > 0) {
            double improvement = ((double)(basicTime - optimizedTime) / basicTime) * 100;
            std::cout << "Improvement:    " << improvement << "%" << std::endl;
        }
    }
    
    std::cout << std::endl << "=== Algorithm Analysis ===" << std::endl;
    std::cout << "Time Complexity:" << std::endl;
    std::cout << "  - Best case:    O(n) - when array is already sorted (optimized version)" << std::endl;
    std::cout << "  - Average case: O(n²)" << std::endl;
    std::cout << "  - Worst case:   O(n²) - when array is reverse sorted" << std::endl;
    std::cout << std::endl << "Space Complexity: O(1) - constant extra space" << std::endl;
    std::cout << std::endl << "Stable: Yes - equal elements maintain their relative order" << std::endl;
    std::cout << "In-place: Yes - sorts the array without using extra space" << std::endl;
    
    return 0;
}
```

---