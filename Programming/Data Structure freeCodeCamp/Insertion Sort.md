---
Created: 2025-08-16T09:51
tags:
  - BroCode
---
## ==What is Insertion Sort==

## **Definition**

**Insertion Sort** is a simple **comparison-based sorting algorithm**.

It builds the sorted array **one element at a time**, by repeatedly **picking the next element** from the unsorted part and **inserting it into its correct position** in the sorted part.

It works similarly to how people **sort playing cards in their hand**.

## **How it Works**

1. Assume the first element is already sorted.
2. Pick the next element.
3. Compare it with elements in the sorted portion.
4. Shift all larger elements one step to the right.
5. Insert the picked element into its correct position.
6. Repeat until the array is sorted.

  

## **Complexity**

- **Best Case:** O(n) → already sorted array (no shifting needed).
- **Worst Case:** O(n²) → reverse sorted array.
- **Average Case:** O(n²).
- **Space Complexity:** O(1) (in-place sorting).

## **When to Use**

- Small datasets.
- Nearly sorted datasets (performs well).
- Useful when the dataset is **continuously receiving new elements** (since insertion is efficient).

## **Example**

```Plain
Array: [5, 3, 4, 1, 2]

Step 1: [5] | [3, 4, 1, 2]
Insert 3 → [3, 5] | [4, 1, 2]

Step 2: [3, 5] | [4, 1, 2]
Insert 4 → [3, 4, 5] | [1, 2]

Step 3: [3, 4, 5] | [1, 2]
Insert 1 → [1, 3, 4, 5] | [2]

Step 4: [1, 3, 4, 5] | [2]
Insert 2 → [1, 2, 3, 4, 5]

Sorted Array: [1, 2, 3, 4, 5]
```

---

  

## ==Where to use Insertion Sort==

**Insertion Sort** is simple and efficient for certain types of datasets. It’s best suited for:

## **1. Small Datasets**

- Works well on **small arrays or lists** because the overhead of complex algorithms isn’t necessary.
- Example: Sorting a handful of scores or short lists of names.

## **2. Nearly Sorted Data**

- Performs very efficiently on **almost sorted arrays**, achieving **O(n) time complexity** in the best case.
- Example: Adding a few new records to an already sorted list.

## **3. Online or Incremental Sorting**

- Useful when data **arrives one element at a time** and you want to keep it sorted.
- Example: Maintaining a sorted leaderboard while new scores come in.

## **4. Stable Sorting Required**

- Insertion Sort is **stable**: it preserves the relative order of equal elements.
- Useful when the original order matters.

## **5. Simple Implementation Needed**

- Easy to implement and understand.
- Useful in **scripts or educational purposes**.

## **Summary Table**

|Condition|Insertion Sort Suitable?|
|---|---|
|Small dataset|✅|
|Nearly sorted data|✅|
|Online/incremental sorting|✅|
|Large dataset|❌|
|Stable sorting required|✅|

---

  

## ==Complexity Analysis==

**Insertion Sort** builds the sorted array one element at a time by inserting each element into its correct position in the sorted portion.

## **Time Complexity**

|Case|Description|Complexity|
|---|---|---|
|**Best Case**|Array is **already sorted** (no shifting needed)|O(n)|
|**Worst Case**|Array is **reverse sorted**|O(n²)|
|**Average Case**|Array is in **random order**|O(n²)|

- `n` = number of elements in the array.
- Best case occurs when minimal comparisons and shifts are required.
- Worst case occurs when each element needs to be compared and shifted through the entire sorted portion.

## **Space Complexity**

- **In-place sorting algorithm** → requires no extra array.
- **Space Complexity:** O(1)

## **Summary**

- Very efficient for **small or nearly sorted datasets**.
- Stable sorting algorithm.
- Not suitable for **large random datasets** due to O(n²) performance.

---

  

## ==Code==

### Python

```Python
def insertion_sort(arr):
    """
    Sorts an array using insertion sort algorithm
    Time Complexity: O(n²)
    Space Complexity: O(1)
    """
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        
        # Move elements greater than key one position ahead
        while j >= 0 and arr[j] > key:
            arr[j + 1] = arr[j]
            j -= 1
        
        arr[j + 1] = key
    
    return arr

def print_array(arr):
    """Helper function to print array"""
    print(" ".join(map(str, arr)))

# Example usage
if __name__ == "__main__":
    # Test array
    numbers = [64, 34, 25, 12, 22, 11, 90]
    
    print("Original array:")
    print_array(numbers)
    
    # Sort the array
    sorted_numbers = insertion_sort(numbers.copy())
    
    print("Sorted array:")
    print_array(sorted_numbers)
```

### C#

```C#
using System;

class InsertionSort
{
    /// <summary>
    /// Sorts an array using insertion sort algorithm
    /// Time Complexity: O(n²)
    /// Space Complexity: O(1)
    /// </summary>
    /// <param name="arr">Array to be sorted</param>
    public static void Sort(int[] arr)
    {
        int n = arr.Length;
        
        for (int i = 1; i < n; i++)
        {
            int key = arr[i];
            int j = i - 1;
            
            // Move elements greater than key one position ahead
            while (j >= 0 && arr[j] > key)
            {
                arr[j + 1] = arr[j];
                j--;
            }
            
            arr[j + 1] = key;
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
        int[] numbers = { 64, 34, 25, 12, 22, 11, 90 };
        
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
 * Sorts an array using insertion sort algorithm
 * Time Complexity: O(n²)
 * Space Complexity: O(1)
 */
void insertionSort(std::vector<int>& arr) {
    int n = arr.size();
    
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        
        // Move elements greater than key one position ahead
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        
        arr[j + 1] = key;
    }
}

/**
 * Alternative implementation using C-style arrays
 */
void insertionSort(int arr[], int n) {
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        
        arr[j + 1] = key;
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
    std::vector<int> numbers = {64, 34, 25, 12, 22, 11, 90};
    
    std::cout << "Original array:" << std::endl;
    printArray(numbers);
    
    // Sort the array
    insertionSort(numbers);
    
    std::cout << "Sorted array:" << std::endl;
    printArray(numbers);
    
    return 0;
}
```

---