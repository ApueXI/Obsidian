---
Created: 2025-08-16T09:51
tags:
  - BroCode
---
## ==What is Merge Sort==

## **Definition**

**Merge Sort** is a **divide-and-conquer sorting algorithm**.

It works by **recursively splitting** the array into smaller halves, sorting each half, and then **merging them back together** in order.

## **How it Works**

1. **Divide** → Split the array into two halves until each subarray has only one element.
2. **Conquer** → Recursively sort the two halves.
3. **Combine** → Merge the two sorted halves into one sorted array.

## **Complexity**

- **Best Case:** O(n log n)
- **Worst Case:** O(n log n)
- **Average Case:** O(n log n)
- **Space Complexity:** O(n) (needs temporary arrays during merge)

## **When to Use**

- Large datasets.
- When stable sorting is required (maintains the relative order of equal elements).
- Useful in external sorting (sorting data that doesn’t fit in memory).

## **Example**

```Plain
Array: [38, 27, 43, 3, 9, 82, 10]

Step 1: Divide
[38, 27, 43, 3] and [9, 82, 10]

Step 2: Divide further
[38, 27] [43, 3] [9, 82] [10]

Step 3: Sort small pieces
[27, 38] [3, 43] [9, 82] [10]

Step 4: Merge
[3, 27, 38, 43] and [9, 10, 82]

Step 5: Final Merge
[3, 9, 10, 27, 38, 43, 82]
```

---

  

## ==Where to use Merge Sort==

**Merge Sort** is a **divide-and-conquer sorting algorithm** that is efficient for **large datasets** and guarantees **stable sorting**. Use it in the following scenarios:

## **1. Large Datasets**

- Performs consistently in **O(n log n) time**, making it ideal for large arrays or lists.
- Example: Sorting millions of records in a database.

## **2. Linked Lists**

- Works efficiently with **linked lists** because merging does not require random access.
- Example: Sorting a linked list of student records.

## **3. Stable Sorting Required**

- Merge Sort **preserves the relative order** of equal elements.
- Example: Sorting employees by salary while maintaining original order for ties.

## **4. External Sorting**

- Ideal for **sorting data that does not fit in memory** (external storage).
- Can process chunks of data and merge them efficiently.

## **5. Divide and Conquer Problems**

- Useful when you need a **reliable recursive sorting method** for complex datasets.
- Example: Preprocessing data for algorithms that require sorted input.

## **Summary Table**

|Condition|Merge Sort Suitable?|
|---|---|
|Large datasets|✅|
|Linked lists|✅|
|Stable sorting required|✅|
|Small datasets|❌ (overhead may be higher than simpler sorts)|
|In-place memory constraints|❌ (requires O(n) extra space)|

---

  

## ==Complexity Analysis==

**Merge Sort** is a **divide-and-conquer sorting algorithm** that splits the array, sorts the halves, and merges them.

## **Time Complexity**

|Case|Description|Complexity|
|---|---|---|
|**Best Case**|Array is already sorted|O(n log n)|
|**Worst Case**|Array is in reverse order|O(n log n)|
|**Average Case**|Array is in random order|O(n log n)|

- `n` = number of elements in the array.
- Each level of recursion processes all `n` elements during merging.
- Number of levels = log₂ n → total comparisons = O(n log n).

## **Space Complexity**

- Merge Sort requires **extra memory** for merging arrays.
- **Space Complexity:** O(n)

## **Summary**

- Efficient and predictable for **large datasets**.
- **Stable sort**, preserving relative order of equal elements.
- Requires **additional memory** compared to in-place sorts like Insertion or Selection Sort.

---

  

## ==Code==

### Python

```Python
def merge_sort(arr):
    """
    Sorts an array using merge sort algorithm
    Time Complexity: O(n log n)
    Space Complexity: O(n)
    """
    # Base case: arrays with 0 or 1 element are already sorted
    if len(arr) <= 1:
        return arr
    
    # Divide the array into two halves
    mid = len(arr) // 2
    left = arr[:mid]
    right = arr[mid:]
    
    # Recursively sort both halves
    left_sorted = merge_sort(left)
    right_sorted = merge_sort(right)
    
    # Merge the sorted halves
    return merge(left_sorted, right_sorted)

def merge(left, right):
    """
    Merge two sorted arrays into one sorted array
    """
    result = []
    i = j = 0
    
    # Compare elements from both arrays and merge in sorted order
    while i < len(left) and j < len(right):
        if left[i] <= right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
    
    # Add remaining elements from left array
    while i < len(left):
        result.append(left[i])
        i += 1
    
    # Add remaining elements from right array
    while j < len(right):
        result.append(right[j])
        j += 1
    
    return result

def merge_sort_inplace(arr, left=0, right=None):
    """
    In-place merge sort implementation
    """
    if right is None:
        right = len(arr) - 1
    
    if left < right:
        mid = (left + right) // 2
        
        # Recursively sort both halves
        merge_sort_inplace(arr, left, mid)
        merge_sort_inplace(arr, mid + 1, right)
        
        # Merge the sorted halves
        merge_inplace(arr, left, mid, right)

def merge_inplace(arr, left, mid, right):
    """
    Merge function for in-place merge sort
    """
    # Create temporary arrays for left and right subarrays
    left_arr = arr[left:mid + 1]
    right_arr = arr[mid + 1:right + 1]
    
    i = j = 0
    k = left
    
    # Merge the temporary arrays back into arr[left..right]
    while i < len(left_arr) and j < len(right_arr):
        if left_arr[i] <= right_arr[j]:
            arr[k] = left_arr[i]
            i += 1
        else:
            arr[k] = right_arr[j]
            j += 1
        k += 1
    
    # Copy remaining elements
    while i < len(left_arr):
        arr[k] = left_arr[i]
        i += 1
        k += 1
    
    while j < len(right_arr):
        arr[k] = right_arr[j]
        j += 1
        k += 1

def print_array(arr):
    """Helper function to print array"""
    print(" ".join(map(str, arr)))

# Example usage
if __name__ == "__main__":
    # Test array
    numbers = [64, 34, 25, 12, 22, 11, 90, 5]
    
    print("Original array:")
    print_array(numbers)
    
    # Test regular merge sort
    sorted_numbers = merge_sort(numbers.copy())
    print("Sorted array (merge sort):")
    print_array(sorted_numbers)
    
    # Test in-place merge sort
    numbers_copy = numbers.copy()
    merge_sort_inplace(numbers_copy)
    print("Sorted array (in-place merge sort):")
    print_array(numbers_copy)
```

### C#

```C#
using System;

class MergeSort
{
    /// <summary>
    /// Sorts an array using merge sort algorithm
    /// Time Complexity: O(n log n)
    /// Space Complexity: O(n)
    /// </summary>
    /// <param name="arr">Array to be sorted</param>
    /// <param name="left">Left index</param>
    /// <param name="right">Right index</param>
    public static void Sort(int[] arr, int left, int right)
    {
        if (left < right)
        {
            // Find the middle point
            int mid = left + (right - left) / 2;
            
            // Recursively sort both halves
            Sort(arr, left, mid);
            Sort(arr, mid + 1, right);
            
            // Merge the sorted halves
            Merge(arr, left, mid, right);
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
    /// Merge two sorted subarrays
    /// </summary>
    /// <param name="arr">Main array</param>
    /// <param name="left">Left index</param>
    /// <param name="mid">Middle index</param>
    /// <param name="right">Right index</param>
    private static void Merge(int[] arr, int left, int mid, int right)
    {
        // Calculate sizes of the two subarrays
        int n1 = mid - left + 1;
        int n2 = right - mid;
        
        // Create temporary arrays
        int[] leftArray = new int[n1];
        int[] rightArray = new int[n2];
        
        // Copy data to temporary arrays
        Array.Copy(arr, left, leftArray, 0, n1);
        Array.Copy(arr, mid + 1, rightArray, 0, n2);
        
        // Merge the temporary arrays back into arr[left..right]
        int i = 0, j = 0, k = left;
        
        while (i < n1 && j < n2)
        {
            if (leftArray[i] <= rightArray[j])
            {
                arr[k] = leftArray[i];
                i++;
            }
            else
            {
                arr[k] = rightArray[j];
                j++;
            }
            k++;
        }
        
        // Copy remaining elements of leftArray[]
        while (i < n1)
        {
            arr[k] = leftArray[i];
            i++;
            k++;
        }
        
        // Copy remaining elements of rightArray[]
        while (j < n2)
        {
            arr[k] = rightArray[j];
            j++;
            k++;
        }
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
        int[] numbers = { 64, 34, 25, 12, 22, 11, 90, 5 };
        
        Console.WriteLine("Original array:");
        PrintArray(numbers);
        
        // Sort the array
        Sort(numbers);
        
        Console.WriteLine("Sorted array:");
        PrintArray(numbers);
        
        Console.ReadLine(); // Keep console open
    }
}
```

### C++

```C++
\#include <iostream>
\#include <vector>

/**
 * Merge two sorted subarrays into one sorted array
 * Time Complexity: O(n)
 * Space Complexity: O(n)
 */
void merge(std::vector<int>& arr, int left, int mid, int right) {
    // Calculate sizes of the two subarrays
    int n1 = mid - left + 1;
    int n2 = right - mid;
    
    // Create temporary arrays
    std::vector<int> leftArray(n1);
    std::vector<int> rightArray(n2);
    
    // Copy data to temporary arrays
    for (int i = 0; i < n1; i++)
        leftArray[i] = arr[left + i];
    for (int j = 0; j < n2; j++)
        rightArray[j] = arr[mid + 1 + j];
    
    // Merge the temporary arrays back into arr[left..right]
    int i = 0, j = 0, k = left;
    
    while (i < n1 && j < n2) {
        if (leftArray[i] <= rightArray[j]) {
            arr[k] = leftArray[i];
            i++;
        } else {
            arr[k] = rightArray[j];
            j++;
        }
        k++;
    }
    
    // Copy remaining elements of leftArray[]
    while (i < n1) {
        arr[k] = leftArray[i];
        i++;
        k++;
    }
    
    // Copy remaining elements of rightArray[]
    while (j < n2) {
        arr[k] = rightArray[j];
        j++;
        k++;
    }
}

/**
 * Merge sort implementation
 * Time Complexity: O(n log n)
 * Space Complexity: O(n)
 */
void mergeSort(std::vector<int>& arr, int left, int right) {
    if (left < right) {
        // Find the middle point to divide the array into two halves
        int mid = left + (right - left) / 2;
        
        // Recursively sort both halves
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        
        // Merge the sorted halves
        merge(arr, left, mid, right);
    }
}

/**
 * Overloaded function for easier usage
 */
void mergeSort(std::vector<int>& arr) {
    mergeSort(arr, 0, arr.size() - 1);
}

/**
 * Alternative implementation using C-style arrays
 */
void merge(int arr[], int left, int mid, int right) {
    int n1 = mid - left + 1;
    int n2 = right - mid;
    
    // Create temporary arrays
    int* leftArray = new int[n1];
    int* rightArray = new int[n2];
    
    // Copy data to temporary arrays
    for (int i = 0; i < n1; i++)
        leftArray[i] = arr[left + i];
    for (int j = 0; j < n2; j++)
        rightArray[j] = arr[mid + 1 + j];
    
    // Merge the temporary arrays back into arr[left..right]
    int i = 0, j = 0, k = left;
    
    while (i < n1 && j < n2) {
        if (leftArray[i] <= rightArray[j]) {
            arr[k] = leftArray[i];
            i++;
        } else {
            arr[k] = rightArray[j];
            j++;
        }
        k++;
    }
    
    // Copy remaining elements
    while (i < n1) {
        arr[k] = leftArray[i];
        i++;
        k++;
    }
    
    while (j < n2) {
        arr[k] = rightArray[j];
        j++;
        k++;
    }
    
    // Clean up memory
    delete[] leftArray;
    delete[] rightArray;
}

void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;
        
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        
        merge(arr, left, mid, right);
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
    std::vector<int> numbers = {64, 34, 25, 12, 22, 11, 90, 5};
    
    std::cout << "Original array:" << std::endl;
    printArray(numbers);
    
    // Sort the array
    mergeSort(numbers);
    
    std::cout << "Sorted array:" << std::endl;
    printArray(numbers);
    
    return 0;
}
```

---