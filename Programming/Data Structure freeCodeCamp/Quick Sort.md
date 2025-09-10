---
Created: 2025-08-16T09:51
tags:
  - BroCode
---
## ==What is Quick Sort==

## **Definition**

**Quick Sort** is a **divide-and-conquer sorting algorithm** that works by:

1. Selecting a **pivot element** from the array.
2. **Partitioning** the array into two subarrays:
    - Elements **less than the pivot**
    - Elements **greater than the pivot**
3. **Recursively sorting** the subarrays.

- It is one of the **fastest general-purpose sorting algorithms** in practice.
- Unlike Merge Sort, it **sorts in place** and usually requires **less extra memory**.

## **How it Works**

1. Pick a pivot (e.g., first, last, or median element).
2. Rearrange the array so that:
    - Left side → elements ≤ pivot
    - Right side → elements > pivot
3. Recursively apply Quick Sort to left and right subarrays.
4. Combine the results → fully sorted array.

## **Example**

```Plain
Array: [10, 7, 8, 9, 1, 5]

Choose pivot = 5
Partition: [1] [5] [10, 7, 8, 9]

Recursively sort left [1] → already sorted
Recursively sort right [10, 7, 8, 9]:
   Pivot = 9
   Partition: [7, 8] [9] [10]
   Recursively sort left [7, 8] → [7, 8]

Final sorted array: [1, 5, 7, 8, 9, 10]
```

## **Complexity**

- **Best Case:** O(n log n) → balanced partitions
- **Worst Case:** O(n²) → unbalanced partitions (e.g., already sorted array with poor pivot choice)
- **Average Case:** O(n log n)
- **Space Complexity:** O(log n) → due to recursion stack

## **When to Use**

- Large datasets where **in-place sorting** is preferred.
- Situations where **average-case performance matters more than worst-case**.
- Useful in **systems and libraries** because it is typically faster than Merge Sort due to **lower constant factors**.

---

  

## ==Where to use Quick Sort==

**Quick Sort** is one of the fastest general-purpose sorting algorithms, but its efficiency depends on proper pivot selection and dataset characteristics.

## **1. Large Datasets**

- Very efficient for **large arrays or lists** due to O(n log n) average-case time complexity.
- Example: Sorting millions of numbers in memory.

## **2. In-Place Sorting Needed**

- Quick Sort is **in-place**, so it **does not require extra memory** like Merge Sort does.
- Example: Sorting arrays in memory-constrained environments.

## **3. Average-Case Performance is Important**

- Performs extremely well **on average** for random data.
- Example: Sorting data for database operations or search optimizations.

## **4. Systems and Libraries**

- Often used in **standard library implementations** for arrays because of speed and low overhead.

## **5. When Stability is Not Required**

- Quick Sort is **not stable** by default.
- Use when **relative order of equal elements does not matter**.

## **When NOT to Use**

- Datasets that are **already mostly sorted** (can degrade to O(n²) without good pivot selection).
- Situations where **stable sorting is required**.

## **Summary Table**

|Condition|Quick Sort Suitable?|
|---|---|
|Large dataset|✅|
|In-place sorting required|✅|
|Average-case performance important|✅|
|Stable sorting required|❌|
|Already sorted array|⚠ Use caution|

---

  

## ==Complexity Analysis==

**Quick Sort** is a divide-and-conquer sorting algorithm that partitions the array around a pivot and recursively sorts the subarrays. Its efficiency depends on **pivot selection** and the **distribution of input data**.

## **Time Complexity**

|Case|Description|Complexity|
|---|---|---|
|**Best Case**|Balanced partitions; pivot splits array into roughly equal halves|O(n log n)|
|**Worst Case**|Unbalanced partitions; pivot is smallest or largest element (e.g., already sorted array)|O(n²)|
|**Average Case**|Random data with reasonably balanced partitions|O(n log n)|

- `n` = number of elements in the array.
- Best and average cases occur when partitions are roughly equal.
- Worst case occurs with **poor pivot choice**, leading to highly unbalanced partitions.

## **Space Complexity**

- **In-place sorting** → no extra arrays needed.
- **Space Complexity:** O(log n) due to recursion stack (average case).

## **Summary**

- Very efficient on **large, random datasets**.
- Performance is sensitive to **pivot choice**.
- Not **stable** by default.
- Can be optimized using **randomized pivot selection** or **median-of-three** method.

---

  

## ==Code==

### Python

```Python
def quick_sort(arr, low=0, high=None):
    """
    Sorts an array using quick sort algorithm (in-place)
    Time Complexity: O(n log n) average, O(n²) worst case
    Space Complexity: O(log n) average (recursion stack)
    """
    if high is None:
        high = len(arr) - 1
    
    if low < high:
        # Partition the array and get the pivot index
        pivot_index = partition(arr, low, high)
        
        # Recursively sort elements before and after partition
        quick_sort(arr, low, pivot_index - 1)
        quick_sort(arr, pivot_index + 1, high)

def partition(arr, low, high):
    """
    Partition function using Lomuto partition scheme
    Places pivot at its correct position and returns pivot index
    """
    # Choose the rightmost element as pivot
    pivot = arr[high]
    
    # Index of smaller element (indicates right position of pivot)
    i = low - 1
    
    for j in range(low, high):
        # If current element is smaller than or equal to pivot
        if arr[j] <= pivot:
            i += 1
            arr[i], arr[j] = arr[j], arr[i]  # Swap elements
    
    # Place pivot at correct position
    arr[i + 1], arr[high] = arr[high], arr[i + 1]
    return i + 1

def quick_sort_hoare(arr, low=0, high=None):
    """
    Quick sort using Hoare partition scheme (alternative implementation)
    """
    if high is None:
        high = len(arr) - 1
    
    if low < high:
        pivot_index = hoare_partition(arr, low, high)
        quick_sort_hoare(arr, low, pivot_index)
        quick_sort_hoare(arr, pivot_index + 1, high)

def hoare_partition(arr, low, high):
    """
    Hoare partition scheme
    """
    pivot = arr[low]  # Choose first element as pivot
    i = low - 1
    j = high + 1
    
    while True:
        # Find element on left that should be on right
        i += 1
        while arr[i] < pivot:
            i += 1
        
        # Find element on right that should be on left
        j -= 1
        while arr[j] > pivot:
            j -= 1
        
        # If elements crossed, partitioning is done
        if i >= j:
            return j
        
        # Swap elements
        arr[i], arr[j] = arr[j], arr[i]

def quick_sort_functional(arr):
    """
    Functional approach (creates new arrays)
    """
    if len(arr) <= 1:
        return arr
    
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    
    return quick_sort_functional(left) + middle + quick_sort_functional(right)

def quick_sort_random_pivot(arr, low=0, high=None):
    """
    Quick sort with random pivot selection (helps avoid worst case)
    """
    import random
    
    if high is None:
        high = len(arr) - 1
    
    if low < high:
        # Choose random pivot and swap with last element
        random_index = random.randint(low, high)
        arr[random_index], arr[high] = arr[high], arr[random_index]
        
        pivot_index = partition(arr, low, high)
        quick_sort_random_pivot(arr, low, pivot_index - 1)
        quick_sort_random_pivot(arr, pivot_index + 1, high)

def print_array(arr):
    """Helper function to print array"""
    print(" ".join(map(str, arr)))

# Example usage
if __name__ == "__main__":
    # Test array
    numbers = [64, 34, 25, 12, 22, 11, 90, 5, 77, 30]
    
    print("Original array:")
    print_array(numbers)
    
    # Test standard quick sort
    numbers_copy1 = numbers.copy()
    quick_sort(numbers_copy1)
    print("Sorted array (Lomuto partition):")
    print_array(numbers_copy1)
    
    # Test Hoare partition
    numbers_copy2 = numbers.copy()
    quick_sort_hoare(numbers_copy2)
    print("Sorted array (Hoare partition):")
    print_array(numbers_copy2)
    
    # Test functional approach
    numbers_copy3 = numbers.copy()
    sorted_functional = quick_sort_functional(numbers_copy3)
    print("Sorted array (functional):")
    print_array(sorted_functional)
    
    # Test random pivot
    numbers_copy4 = numbers.copy()
    quick_sort_random_pivot(numbers_copy4)
    print("Sorted array (random pivot):")
    print_array(numbers_copy4)
```

### C#

```C#
using System;

class QuickSort
{
    /// <summary>
    /// Sorts an array using quick sort algorithm
    /// Time Complexity: O(n log n) average, O(n²) worst case
    /// Space Complexity: O(log n) average (recursion stack)
    /// </summary>
    /// <param name="arr">Array to be sorted</param>
    /// <param name="low">Starting index</param>
    /// <param name="high">Ending index</param>
    public static void Sort(int[] arr, int low, int high)
    {
        if (low < high)
        {
            // Partition the array and get the pivot index
            int pivotIndex = Partition(arr, low, high);
            
            // Recursively sort elements before and after partition
            Sort(arr, low, pivotIndex - 1);
            Sort(arr, pivotIndex + 1, high);
        }
    }
    
    /// <summary>
    /// Overloaded method for easier usage
    /// </summary>
    /// <param name="arr">Array to be sorted</param>
    public static void Sort(int[] arr)
    {
        Sort(arr, 0, arr.Length - 1);
    }
    
    /// <summary>
    /// Partition function using Lomuto partition scheme
    /// </summary>
    /// <param name="arr">Array to partition</param>
    /// <param name="low">Starting index</param>
    /// <param name="high">Ending index</param>
    /// <returns>Index of the pivot element</returns>
    private static int Partition(int[] arr, int low, int high)
    {
        // Choose the rightmost element as pivot
        int pivot = arr[high];
        
        // Index of smaller element
        int i = low - 1;
        
        for (int j = low; j < high; j++)
        {
            // If current element is smaller than or equal to pivot
            if (arr[j] <= pivot)
            {
                i++;
                Swap(arr, i, j);
            }
        }
        
        // Place pivot at correct position
        Swap(arr, i + 1, high);
        return i + 1;
    }
    
    /// <summary>
    /// Quick sort with Hoare partition scheme
    /// </summary>
    /// <param name="arr">Array to be sorted</param>
    /// <param name="low">Starting index</param>
    /// <param name="high">Ending index</param>
    public static void SortHoare(int[] arr, int low, int high)
    {
        if (low < high)
        {
            int pivotIndex = HoarePartition(arr, low, high);
            SortHoare(arr, low, pivotIndex);
            SortHoare(arr, pivotIndex + 1, high);
        }
    }
    
    /// <summary>
    /// Hoare partition scheme
    /// </summary>
    /// <param name="arr">Array to partition</param>
    /// <param name="low">Starting index</param>
    /// <param name="high">Ending index</param>
    /// <returns>Index for partitioning</returns>
    private static int HoarePartition(int[] arr, int low, int high)
    {
        int pivot = arr[low];
        int i = low - 1;
        int j = high + 1;
        
        while (true)
        {
            // Find element on left that should be on right
            do
            {
                i++;
            } while (arr[i] < pivot);
            
            // Find element on right that should be on left
            do
            {
                j--;
            } while (arr[j] > pivot);
            
            // If elements crossed, partitioning is done
            if (i >= j)
                return j;
            
            Swap(arr, i, j);
        }
    }
    
    /// <summary>
    /// Quick sort with random pivot selection
    /// </summary>
    /// <param name="arr">Array to be sorted</param>
    /// <param name="low">Starting index</param>
    /// <param name="high">Ending index</param>
    public static void SortRandomPivot(int[] arr, int low, int high)
    {
        if (low < high)
        {
            // Choose random pivot and swap with last element
            Random random = new Random();
            int randomIndex = random.Next(low, high + 1);
            Swap(arr, randomIndex, high);
            
            int pivotIndex = Partition(arr, low, high);
            SortRandomPivot(arr, low, pivotIndex - 1);
            SortRandomPivot(arr, pivotIndex + 1, high);
        }
    }
    
    /// <summary>
    /// Helper method to swap two elements
    /// </summary>
    /// <param name="arr">Array</param>
    /// <param name="i">First index</param>
    /// <param name="j">Second index</param>
    private static void Swap(int[] arr, int i, int j)
    {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
    
    /// <summary>
    /// Helper method to print array
    /// </summary>
    /// <param name="arr">Array to print</param>
    public static void PrintArray(int[] arr)
    {
        Console.WriteLine(string.Join(" ", arr));
    }
    
    static void Main(string[] args)
    {
        // Test array
        int[] numbers = { 64, 34, 25, 12, 22, 11, 90, 5, 77, 30 };
        
        Console.WriteLine("Original array:");
        PrintArray(numbers);
        
        // Test standard quick sort
        int[] numbersCopy1 = (int[])numbers.Clone();
        Sort(numbersCopy1);
        Console.WriteLine("Sorted array (Lomuto partition):");
        PrintArray(numbersCopy1);
        
        // Test Hoare partition
        int[] numbersCopy2 = (int[])numbers.Clone();
        SortHoare(numbersCopy2, 0, numbersCopy2.Length - 1);
        Console.WriteLine("Sorted array (Hoare partition):");
        PrintArray(numbersCopy2);
        
        // Test random pivot
        int[] numbersCopy3 = (int[])numbers.Clone();
        SortRandomPivot(numbersCopy3, 0, numbersCopy3.Length - 1);
        Console.WriteLine("Sorted array (random pivot):");
        PrintArray(numbersCopy3);
        
        Console.ReadLine(); // Keep console open
    }
}
```

### C++

```C++
\#include <iostream>
\#include <vector>
\#include <random>
\#include <algorithm>

/**
 * Partition function using Lomuto partition scheme
 * Time Complexity: O(n)
 */
int partition(std::vector<int>& arr, int low, int high) {
    // Choose the rightmost element as pivot
    int pivot = arr[high];
    
    // Index of smaller element
    int i = low - 1;
    
    for (int j = low; j < high; j++) {
        // If current element is smaller than or equal to pivot
        if (arr[j] <= pivot) {
            i++;
            std::swap(arr[i], arr[j]);
        }
    }
    
    // Place pivot at correct position
    std::swap(arr[i + 1], arr[high]);
    return i + 1;
}

/**
 * Quick sort implementation
 * Time Complexity: O(n log n) average, O(n²) worst case
 * Space Complexity: O(log n) average (recursion stack)
 */
void quickSort(std::vector<int>& arr, int low, int high) {
    if (low < high) {
        // Partition the array and get the pivot index
        int pivotIndex = partition(arr, low, high);
        
        // Recursively sort elements before and after partition
        quickSort(arr, low, pivotIndex - 1);
        quickSort(arr, pivotIndex + 1, high);
    }
}

/**
 * Overloaded function for easier usage
 */
void quickSort(std::vector<int>& arr) {
    quickSort(arr, 0, arr.size() - 1);
}

/**
 * Hoare partition scheme (alternative partitioning method)
 */
int hoarePartition(std::vector<int>& arr, int low, int high) {
    int pivot = arr[low];  // Choose first element as pivot
    int i = low - 1;
    int j = high + 1;
    
    while (true) {
        // Find element on left that should be on right
        do {
            i++;
        } while (arr[i] < pivot);
        
        // Find element on right that should be on left
        do {
            j--;
        } while (arr[j] > pivot);
        
        // If elements crossed, partitioning is done
        if (i >= j)
            return j;
        
        std::swap(arr[i], arr[j]);
    }
}

/**
 * Quick sort using Hoare partition scheme
 */
void quickSortHoare(std::vector<int>& arr, int low, int high) {
    if (low < high) {
        int pivotIndex = hoarePartition(arr, low, high);
        quickSortHoare(arr, low, pivotIndex);
        quickSortHoare(arr, pivotIndex + 1, high);
    }
}

/**
 * Quick sort with random pivot selection
 */
void quickSortRandomPivot(std::vector<int>& arr, int low, int high) {
    if (low < high) {
        // Choose random pivot and swap with last element
        std::random_device rd;
        std::mt19937 gen(rd());
        std::uniform_int_distribution<> dis(low, high);
        int randomIndex = dis(gen);
        std::swap(arr[randomIndex], arr[high]);
        
        int pivotIndex = partition(arr, low, high);
        quickSortRandomPivot(arr, low, pivotIndex - 1);
        quickSortRandomPivot(arr, pivotIndex + 1, high);
    }
}

/**
 * C-style array implementations
 */
int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;
    
    for (int j = low; j < high; j++) {
        if (arr[j] <= pivot) {
            i++;
            std::swap(arr[i], arr[j]);
        }
    }
    
    std::swap(arr[i + 1], arr[high]);
    return i + 1;
}

void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pivotIndex = partition(arr, low, high);
        quickSort(arr, low, pivotIndex - 1);
        quickSort(arr, pivotIndex + 1, high);
    }
}

/**
 * Iterative quick sort (avoids recursion stack overflow for large arrays)
 */
void quickSortIterative(std::vector<int>& arr) {
    std::vector<int> stack;
    stack.push_back(0);
    stack.push_back(arr.size() - 1);
    
    while (!stack.empty()) {
        int high = stack.back(); stack.pop_back();
        int low = stack.back(); stack.pop_back();
        
        if (low < high) {
            int pivotIndex = partition(arr, low, high);
            
            // Push left subarray bounds
            stack.push_back(low);
            stack.push_back(pivotIndex - 1);
            
            // Push right subarray bounds
            stack.push_back(pivotIndex + 1);
            stack.push_back(high);
        }
    }
}

/**
 * Helper function to print array
 */
void printArray(const std::vector<int>& arr) {
    for (int i = 0; i < arr.size(); i++) {
        std::cout << arr[i];
        if (i < arr.size() - 1) std::cout << " ";
    }
    std::cout << std::endl;
}

int main() {
    // Test with vector
    std::vector<int> numbers = {64, 34, 25, 12, 22, 11, 90, 5, 77, 30};
    
    std::cout << "Original array:" << std::endl;
    printArray(numbers);
    
    // Test standard quick sort
    std::vector<int> numbersCopy1 = numbers;
    quickSort(numbersCopy1);
    std::cout << "Sorted array (Lomuto partition):" << std::endl;
    printArray(numbersCopy1);
    
    // Test Hoare partition
    std::vector<int> numbersCopy2 = numbers;
    quickSortHoare(numbersCopy2, 0, numbersCopy2.size() - 1);
    std::cout << "Sorted array (Hoare partition):" << std::endl;
    printArray(numbersCopy2);
    
    // Test random pivot
    std::vector<int> numbersCopy3 = numbers;
    quickSortRandomPivot(numbersCopy3, 0, numbersCopy3.size() - 1);
    std::cout << "Sorted array (random pivot):" << std::endl;
    printArray(numbersCopy3);
    
    // Test iterative approach
    std::vector<int> numbersCopy4 = numbers;
    quickSortIterative(numbersCopy4);
    std::cout << "Sorted array (iterative):" << std::endl;
    printArray(numbersCopy4);
    
    return 0;
}
```

---