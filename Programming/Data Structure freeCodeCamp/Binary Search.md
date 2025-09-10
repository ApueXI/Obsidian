---
Created: 2025-08-16T09:41
tags:
  - BroCode
---
## ==What is Binary Search==

## **Definition**

**Binary Search** is an efficient algorithm for finding a target element in a **sorted array or list**.

It works by repeatedly **dividing the search interval in half**:

1. Compare the target with the middle element.
2. If it matches → element found.
3. If the target is smaller → search the **left half**.
4. If the target is larger → search the **right half**.
5. Repeat until the element is found or the interval is empty.

> Important: Binary Search only works on sorted data.

## **Example**

```Plain
Array: [1, 3, 5, 7, 9, 11]
Target: 7

Step 1: Middle element = 5 → 7 > 5 → search right half
Step 2: Middle element = 9 → 7 < 9 → search left half
Step 3: Middle element = 7 → found at index 3
```

## **Complexity**

- **Best Case:** O(1) → target is the middle element.
- **Worst Case:** O(log n) → repeatedly halve until found or empty.
- **Average Case:** O(log n).
- **Space Complexity:** O(1) for iterative, O(log n) for recursive implementation.

## **When to Use**

- Large datasets.
- Sorted data only.
- When fast search performance is important.

---

  

## ==Where to use Binary Search==

**Binary Search** is efficient but has specific requirements. Use it in the following scenarios:

## **1. Sorted Data**

- Binary Search **requires the array/list to be sorted**.
- Example: Searching in a list of sorted student IDs or timestamps.

## **2. Large Datasets**

- For large datasets, Binary Search is **much faster than Linear Search**.
- Time complexity is O(log n), so it scales well with millions of elements.

## **3. Static or Rarely Changing Data**

- Ideal when the dataset **does not change frequently**, so sorting is either already done or infrequent.
- Example: Searching in a database of books sorted by ISBN.

  

## **4. Random Access Data Structures**

- Works best on **arrays or data structures with O(1) random access**.
- Binary Search is **inefficient on linked lists**, because accessing the middle element takes O(n).

## **5. Multiple Searches on the Same Dataset**

- If you need to **search repeatedly**, sorting once and using Binary Search repeatedly saves time.
- Example: Searching for multiple usernames in a sorted list.

## **Summary Table**

|Condition|Binary Search Suitable?|
|---|---|
|Sorted dataset|✅|
|Large dataset|✅|
|Frequently changing data|❌|
|Random access structure (array)|✅|
|Sequential access structure (list)|❌|

---

  

## ==Complexity Analysis==

**Binary Search** works by repeatedly dividing a **sorted array** in half until the target element is found or the search interval is empty.

## **Time Complexity**

|Case|Description|Complexity|
|---|---|---|
|**Best Case**|Target is the **middle element** on the first check|O(1)|
|**Worst Case**|Target is at one end or not present; all halves checked|O(log n)|
|**Average Case**|Element is somewhere in the middle|O(log n)|

- `n` = number of elements in the array.
- Each step **halves the search space**, so the number of comparisons grows logarithmically.

## **Space Complexity**

- **Iterative version:** O(1) → uses no extra space
- **Recursive version:** O(log n) → due to recursive call stack

## **Summary**

- Extremely efficient for **large, sorted datasets**.
- Significantly faster than Linear Search for big arrays.
- Works only on **sorted data** and requires **random access** (like arrays).

---

  

## ==Code==

### **What the code does**

- Searches for a target element in a **sorted array/list**
- Returns the index if found
- Returns -1 if not found

### **Python (Iterative)**

```Python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = left + (right - left) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

# Example usage
arr = [1, 3, 5, 7, 9, 11]
target = 7
index = binary_search(arr, target)

if index != -1:
    print(f"Element found at index {index}")
else:
    print("Element not found")

```

### **C# (Iterative)**

```C#
using System;

class Program
{
    static int BinarySearch(int[] arr, int target)
    {
        int left = 0, right = arr.Length - 1;
        while (left <= right)
        {
            int mid = left + (right - left) / 2;
            if (arr[mid] == target)
                return mid;
            else if (arr[mid] < target)
                left = mid + 1;
            else
                right = mid - 1;
        }
        return -1;
    }

    static void Main()
    {
        int[] arr = {1, 3, 5, 7, 9, 11};
        int target = 7;
        int index = BinarySearch(arr, target);

        if (index != -1)
            Console.WriteLine($"Element found at index {index}");
        else
            Console.WriteLine("Element not found");
    }
}

```

### **C++ (Iterative)**

```C++
\#include <iostream>
using namespace std;

int binarySearch(int arr[], int n, int target)
{
    int left = 0, right = n - 1;
    while (left <= right)
    {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target)
            return mid;
        else if (arr[mid] < target)
            left = mid + 1;
        else
            right = mid - 1;
    }
    return -1;
}

int main()
{
    int arr[] = {1, 3, 5, 7, 9, 11};
    int n = sizeof(arr) / sizeof(arr[0]);
    int target = 7;

    int index = binarySearch(arr, n, target);
    if (index != -1)
        cout << "Element found at index " << index << endl;
    else
        cout << "Element not found" << endl;

    return 0;
}
```

---