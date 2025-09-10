---
Created: 2025-08-16T09:50
tags:
  - BroCode
---
## ==What is Interpolation Search==

## **Definition**

  

**Interpolation Search** is an improved searching algorithm for **sorted arrays**, especially when the elements are **uniformly distributed** (e.g., numbers spaced evenly).

It works like **Binary Search**, but instead of always checking the **middle element**, it estimates the position of the target using the **formula of proportionality**, similar to how you’d look up a word in a dictionary by guessing where it might be.

## **How it Works**

Instead of picking the middle index:

```Plain
mid = left + (right - left) / 2      # Binary Search
```

Interpolation Search estimates the position as:

```Plain
pos = left + ((target - arr[left]) * (right - left))
              / (arr[right] - arr[left])
```

This formula assumes values are **evenly distributed**, so it can "jump closer" to the target.

## **Example**

```Plain
Array: [10, 20, 30, 40, 50, 60, 70, 80]
Target: 60

Step 1: left = 0, right = 7
pos = 0 + ((60 - 10) * (7 - 0)) / (80 - 10)
pos = 5  → arr[5] = 60 → found
```

## **Complexity**

- **Best Case:** O(1) (if found on first try)
- **Average Case:** O(log log n) (faster than Binary Search on uniform data)
- **Worst Case:** O(n) (if data is not uniform, e.g., skewed values)
- **Space Complexity:** O(1)

## **When to Use**

- Data must be **sorted**.
- Works best when data is **uniformly distributed** (like IDs, timestamps, or evenly increasing values).
- Not efficient for **non-uniform datasets**.

---

  

## ==Where to use Interpolation Search==

**Interpolation Search** is an efficient search algorithm that works best under specific conditions. Use it in the following scenarios:

## **1. Sorted Data**

- The array **must be sorted**.
- Example: Searching for a number in a sorted list of IDs.

## **2. Uniformly Distributed Data**

- Works best when elements are **evenly spaced or uniformly distributed**.
- Example: Searching in a list of ages from 1 to 100 or evenly spaced timestamps.

## **3. Large Datasets**

- For large datasets, Interpolation Search can be **faster than Binary Search** when data is uniform.
- Average time complexity: O(log log n), better than O(log n) of Binary Search.

  

## **4. Static or Rarely Changing Data**

- Ideal for datasets that **don’t change frequently**, since sorting and uniformity can be maintained.

## **5. Numeric Data**

- Best suited for **numerical data** where position estimation using the formula makes sense.
- Example: Searching for a value in a sorted salary list.

## **Summary Table**

|Condition|Interpolation Search Suitable?|
|---|---|
|Sorted dataset|✅|
|Uniformly distributed data|✅|
|Large datasets|✅|
|Frequently changing data|❌|
|Non-numeric or unevenly spaced values|❌|

---

  

## ==Complexity Analysis==

**Interpolation Search** estimates the position of the target element based on its value relative to the low and high values of the sorted array.

## **Time Complexity**

|Case|Description|Complexity|
|---|---|---|
|**Best Case**|Target is found on the **first estimated position**|O(1)|
|**Average Case**|Data is **uniformly distributed**, efficient halving|O(log log n)|
|**Worst Case**|Data is **non-uniformly distributed** or skewed|O(n)|

- `n` = number of elements in the array.
- Unlike Binary Search, the search location is estimated, which makes it faster on **uniform datasets**.

## **Space Complexity**

- **Iterative version:** O(1) → uses no extra space
- **Recursive version:** O(log n) → due to recursive call stack

## **Summary**

- Extremely efficient for **large, sorted, uniformly distributed datasets**.
- Can degrade to **O(n)** if the data is skewed or non-uniform.
- Requires **numeric or comparable data** to estimate positions.

---

  

## ==Code==

### Python

```Python
def interpolation_search(arr, target):
    """
    Performs interpolation search on a sorted array.
    
    Args:
        arr: Sorted list of numbers
        target: Value to search for
    
    Returns:
        Index of target if found, -1 otherwise
    """
    low = 0
    high = len(arr) - 1
    
    while low <= high and target >= arr[low] and target <= arr[high]:
        # If array has only one element
        if low == high:
            if arr[low] == target:
                return low
            return -1
        
        # Calculate probe position using interpolation formula
        pos = low + int(((target - arr[low]) / (arr[high] - arr[low])) * (high - low))
        
        # Ensure pos is within bounds
        pos = max(low, min(high, pos))
        
        if arr[pos] == target:
            return pos
        elif arr[pos] < target:
            low = pos + 1
        else:
            high = pos - 1
    
    return -1

def interpolation_search_recursive(arr, target, low=0, high=None):
    """
    Recursive implementation of interpolation search.
    
    Args:
        arr: Sorted list of numbers
        target: Value to search for
        low: Starting index
        high: Ending index
    
    Returns:
        Index of target if found, -1 otherwise
    """
    if high is None:
        high = len(arr) - 1
    
    # Base cases
    if low > high or target < arr[low] or target > arr[high]:
        return -1
    
    if low == high:
        return low if arr[low] == target else -1
    
    # Calculate probe position
    pos = low + int(((target - arr[low]) / (arr[high] - arr[low])) * (high - low))
    pos = max(low, min(high, pos))
    
    if arr[pos] == target:
        return pos
    elif arr[pos] < target:
        return interpolation_search_recursive(arr, target, pos + 1, high)
    else:
        return interpolation_search_recursive(arr, target, low, pos - 1)

# Example usage and testing
if __name__ == "__main__":
    # Test array
    test_array = [1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25]
    
    print("Array:", test_array)
    print("\nTesting Iterative Implementation:")
    
    # Test cases
    test_values = [1, 7, 15, 25, 4, 30]
    
    for val in test_values:
        result = interpolation_search(test_array, val)
        if result != -1:
            print(f"Value {val} found at index {result}")
        else:
            print(f"Value {val} not found")
    
    print("\nTesting Recursive Implementation:")
    
    for val in test_values:
        result = interpolation_search_recursive(test_array, val)
        if result != -1:
            print(f"Value {val} found at index {result}")
        else:
            print(f"Value {val} not found")
```

### C#

```C#
using System;

public class InterpolationSearch
{
    /// <summary>
    /// Performs interpolation search on a sorted array.
    /// </summary>
    /// <param name="arr">Sorted array of integers</param>
    /// <param name="target">Value to search for</param>
    /// <returns>Index of target if found, -1 otherwise</returns>
    public static int Search(int[] arr, int target)
    {
        int low = 0;
        int high = arr.Length - 1;
        
        while (low <= high && target >= arr[low] && target <= arr[high])
        {
            // If array has only one element
            if (low == high)
            {
                return arr[low] == target ? low : -1;
            }
            
            // Calculate probe position using interpolation formula
            int pos = low + (int)(((double)(target - arr[low]) / (arr[high] - arr[low])) * (high - low));
            
            // Ensure pos is within bounds
            pos = Math.Max(low, Math.Min(high, pos));
            
            if (arr[pos] == target)
                return pos;
            else if (arr[pos] < target)
                low = pos + 1;
            else
                high = pos - 1;
        }
        
        return -1;
    }
    
    /// <summary>
    /// Recursive implementation of interpolation search.
    /// </summary>
    /// <param name="arr">Sorted array of integers</param>
    /// <param name="target">Value to search for</param>
    /// <param name="low">Starting index</param>
    /// <param name="high">Ending index</param>
    /// <returns>Index of target if found, -1 otherwise</returns>
    public static int SearchRecursive(int[] arr, int target, int low, int high)
    {
        // Base cases
        if (low > high || target < arr[low] || target > arr[high])
            return -1;
        
        if (low == high)
            return arr[low] == target ? low : -1;
        
        // Calculate probe position
        int pos = low + (int)(((double)(target - arr[low]) / (arr[high] - arr[low])) * (high - low));
        pos = Math.Max(low, Math.Min(high, pos));
        
        if (arr[pos] == target)
            return pos;
        else if (arr[pos] < target)
            return SearchRecursive(arr, target, pos + 1, high);
        else
            return SearchRecursive(arr, target, low, pos - 1);
    }
    
    /// <summary>
    /// Generic version for any comparable type.
    /// </summary>
    /// <typeparam name="T">Type that implements IComparable</typeparam>
    /// <param name="arr">Sorted array</param>
    /// <param name="target">Value to search for</param>
    /// <returns>Index of target if found, -1 otherwise</returns>
    public static int SearchGeneric<T>(T[] arr, T target) where T : IComparable<T>, IConvertible
    {
        int low = 0;
        int high = arr.Length - 1;
        
        while (low <= high && target.CompareTo(arr[low]) >= 0 && target.CompareTo(arr[high]) <= 0)
        {
            if (low == high)
                return arr[low].CompareTo(target) == 0 ? low : -1;
            
            // For generic types, we need to convert to double for calculation
            double targetVal = target.ToDouble(null);
            double lowVal = arr[low].ToDouble(null);
            double highVal = arr[high].ToDouble(null);
            
            int pos = low + (int)(((targetVal - lowVal) / (highVal - lowVal)) * (high - low));
            pos = Math.Max(low, Math.Min(high, pos));
            
            int comparison = arr[pos].CompareTo(target);
            if (comparison == 0)
                return pos;
            else if (comparison < 0)
                low = pos + 1;
            else
                high = pos - 1;
        }
        
        return -1;
    }
}

// Example usage
class Program
{
    static void Main(string[] args)
    {
        // Test array
        int[] testArray = { 1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25 };
        
        Console.WriteLine("Array: [" + string.Join(", ", testArray) + "]");
        Console.WriteLine("\nTesting Iterative Implementation:");
        
        // Test cases
        int[] testValues = { 1, 7, 15, 25, 4, 30 };
        
        foreach (int val in testValues)
        {
            int result = InterpolationSearch.Search(testArray, val);
            if (result != -1)
                Console.WriteLine($"Value {val} found at index {result}");
            else
                Console.WriteLine($"Value {val} not found");
        }
        
        Console.WriteLine("\nTesting Recursive Implementation:");
        
        foreach (int val in testValues)
        {
            int result = InterpolationSearch.SearchRecursive(testArray, val, 0, testArray.Length - 1);
            if (result != -1)
                Console.WriteLine($"Value {val} found at index {result}");
            else
                Console.WriteLine($"Value {val} not found");
        }
        
        // Test generic version with doubles
        double[] doubleArray = { 1.1, 3.3, 5.5, 7.7, 9.9 };
        Console.WriteLine("\nTesting Generic Implementation with doubles:");
        Console.WriteLine("Array: [" + string.Join(", ", doubleArray) + "]");
        
        int doubleResult = InterpolationSearch.SearchGeneric(doubleArray, 5.5);
        Console.WriteLine($"Value 5.5 found at index: {doubleResult}");
    }
}
```

### C++

```C++
\#include <iostream>
\#include <vector>
\#include <algorithm>

class InterpolationSearch {
public:
    /**
     * Performs interpolation search on a sorted array.
     * @param arr Sorted vector of integers
     * @param target Value to search for
     * @return Index of target if found, -1 otherwise
     */
    static int search(const std::vector<int>& arr, int target) {
        int low = 0;
        int high = arr.size() - 1;
        
        while (low <= high && target >= arr[low] && target <= arr[high]) {
            // If array has only one element
            if (low == high) {
                return arr[low] == target ? low : -1;
            }
            
            // Calculate probe position using interpolation formula
            int pos = low + static_cast<int>(
                (static_cast<double>(target - arr[low]) / (arr[high] - arr[low])) * (high - low)
            );
            
            // Ensure pos is within bounds
            pos = std::max(low, std::min(high, pos));
            
            if (arr[pos] == target) {
                return pos;
            } else if (arr[pos] < target) {
                low = pos + 1;
            } else {
                high = pos - 1;
            }
        }
        
        return -1;
    }
    
    /**
     * Recursive implementation of interpolation search.
     * @param arr Sorted vector of integers
     * @param target Value to search for
     * @param low Starting index
     * @param high Ending index
     * @return Index of target if found, -1 otherwise
     */
    static int searchRecursive(const std::vector<int>& arr, int target, int low, int high) {
        // Base cases
        if (low > high || target < arr[low] || target > arr[high]) {
            return -1;
        }
        
        if (low == high) {
            return arr[low] == target ? low : -1;
        }
        
        // Calculate probe position
        int pos = low + static_cast<int>(
            (static_cast<double>(target - arr[low]) / (arr[high] - arr[low])) * (high - low)
        );
        pos = std::max(low, std::min(high, pos));
        
        if (arr[pos] == target) {
            return pos;
        } else if (arr[pos] < target) {
            return searchRecursive(arr, target, pos + 1, high);
        } else {
            return searchRecursive(arr, target, low, pos - 1);
        }
    }
    
    /**
     * Template version for any comparable type.
     * @param arr Sorted vector of type T
     * @param target Value to search for
     * @return Index of target if found, -1 otherwise
     */
    template<typename T>
    static int searchTemplate(const std::vector<T>& arr, T target) {
        int low = 0;
        int high = arr.size() - 1;
        
        while (low <= high && target >= arr[low] && target <= arr[high]) {
            if (low == high) {
                return arr[low] == target ? low : -1;
            }
            
            // Calculate probe position
            int pos = low + static_cast<int>(
                (static_cast<double>(target - arr[low]) / (arr[high] - arr[low])) * (high - low)
            );
            pos = std::max(low, std::min(high, pos));
            
            if (arr[pos] == target) {
                return pos;
            } else if (arr[pos] < target) {
                low = pos + 1;
            } else {
                high = pos - 1;
            }
        }
        
        return -1;
    }
};

// Utility function to print vector
template<typename T>
void printVector(const std::vector<T>& vec) {
    std::cout << "[";
    for (size_t i = 0; i < vec.size(); ++i) {
        std::cout << vec[i];
        if (i < vec.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
}

int main() {
    // Test array
    std::vector<int> testArray = {1, 3, 5, 7, 9, 11, 13, 15, 17, 19, 21, 23, 25};
    
    std::cout << "Array: ";
    printVector(testArray);
    std::cout << "\nTesting Iterative Implementation:" << std::endl;
    
    // Test cases
    std::vector<int> testValues = {1, 7, 15, 25, 4, 30};
    
    for (int val : testValues) {
        int result = InterpolationSearch::search(testArray, val);
        if (result != -1) {
            std::cout << "Value " << val << " found at index " << result << std::endl;
        } else {
            std::cout << "Value " << val << " not found" << std::endl;
        }
    }
    
    std::cout << "\nTesting Recursive Implementation:" << std::endl;
    
    for (int val : testValues) {
        int result = InterpolationSearch::searchRecursive(testArray, val, 0, testArray.size() - 1);
        if (result != -1) {
            std::cout << "Value " << val << " found at index " << result << std::endl;
        } else {
            std::cout << "Value " << val << " not found" << std::endl;
        }
    }
    
    // Test template version with doubles
    std::vector<double> doubleArray = {1.1, 3.3, 5.5, 7.7, 9.9};
    std::cout << "\nTesting Template Implementation with doubles:" << std::endl;
    std::cout << "Array: ";
    printVector(doubleArray);
    
    int doubleResult = InterpolationSearch::searchTemplate(doubleArray, 5.5);
    std::cout << "Value 5.5 found at index: " << doubleResult << std::endl;
    
    // Performance comparison demonstration
    std::cout << "\n--- Performance Note ---" << std::endl;
    std::cout << "Interpolation search works best with uniformly distributed data." << std::endl;
    std::cout << "Time complexity: O(log log n) for uniform data, O(n) worst case." << std::endl;
    std::cout << "Space complexity: O(1) iterative, O(log log n) recursive." << std::endl;
    
    return 0;
}
```

---