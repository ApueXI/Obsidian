---
Created: 2025-08-16T09:38
tags:
  - BroCode
---
## ==Linear Search==

## **Definition**

**Linear Search** (also called **sequential search**) is the simplest searching algorithm.

It checks each element in a list or array **one by one** until:

- the target element is found, or
- the entire list has been searched.

## **Steps**

1. Start from the first element of the list.
2. Compare the current element with the target.
3. If they match → return the index (or the element).
4. If not, move to the next element.
5. If the end of the list is reached without a match → the element does not exist.

## **Example**

```Plain
Array: [4, 2, 7, 9, 1]
Target: 9

Step 1: Compare 4 with 9 → not equal
Step 2: Compare 2 with 9 → not equal
Step 3: Compare 7 with 9 → not equal
Step 4: Compare 9 with 9 → found at index 3
```

## **Complexity**

- **Best Case:** O(1) → target is the first element.
- **Worst Case:** O(n) → target is the last element or not present.
- **Average Case:** O(n).
- **Space Complexity:** O(1) (no extra space needed).

## **When to Use**

- Small datasets.
- Unsorted or unordered data (since Binary Search requires sorted data).
- Quick/simple search needs where performance is not critical.

---

  

### ==Where to use Linear Search==

**Linear Search** is simple and intuitive but **not very efficient** for large datasets. It’s most suitable in the following scenarios:

## **1. Small Datasets**

- When the number of elements is small, the overhead of more complex algorithms (like Binary Search) is unnecessary.
- Example: Searching for a student in a class list of 20 names.

## **2. Unsorted Data**

- Linear Search **does not require sorted data**, unlike Binary Search.
- Useful when sorting is costly or impossible.
- Example: Searching for a specific item in an unordered inventory list.

## **3. Simple, Quick Lookups**

- When you need a quick search and performance is **not critical**.
- Example: Finding a character in a short string or a key in a small array.

## **4. Checking All Elements**

- When you need to **process or check every element** regardless of the target.
- Example: Counting occurrences of a value in an array.

## **5. Dynamic or Frequently Changing Lists**

- If the data changes frequently, maintaining a sorted order for Binary Search may be inefficient.
- Linear Search works **directly on the current list** without preprocessing.

**Summary:**

|Condition|Linear Search Suitable?|
|---|---|
|Small dataset|✅|
|Unsorted data|✅|
|Large dataset|❌|
|Frequent searches with sorted data|❌|
|Quick one-time search|✅|

---

  

## ==Complexity Analysis==

**Linear Search** checks each element in a list one by one until the target is found or the list ends.

## **Time Complexity**

|Case|Description|Complexity|
|---|---|---|
|**Best Case**|Target is the **first element** in the array|O(1)|
|**Worst Case**|Target is the **last element** or **not present** in the array|O(n)|
|**Average Case**|Target is somewhere in the middle of the array (or random)|O(n)|

- `n` = number of elements in the array.
- Linear Search **scales linearly** with the size of the dataset.

## **Space Complexity**

- Linear Search **does not require extra space**.
- **Space Complexity:** O(1)

## **Summary**

- Simple, no preprocessing required.
- Efficient only for **small or unsorted datasets**.
- Performance **degrades linearly** as dataset size increases.

---

  

## ==Code==

### **What the code does**

- Searches for a target element in an array/list
- Returns the index if found
- Returns -1 if not found

### **Python**

```Python
def linear_search(arr, target):
    for i in range(len(arr)):
        if arr[i] == target:
            return i
    return -1

# Example usage
arr = [4, 2, 7, 9, 1]
target = 9
index = linear_search(arr, target)

if index != -1:
    print(f"Element found at index {index}")
else:
    print("Element not found")

```

### **C#**

```C#
using System;

class Program
{
    static int LinearSearch(int[] arr, int target)
    {
        for (int i = 0; i < arr.Length; i++)
        {
            if (arr[i] == target)
                return i;
        }
        return -1;
    }

    static void Main()
    {
        int[] arr = {4, 2, 7, 9, 1};
        int target = 9;
        int index = LinearSearch(arr, target);

        if (index != -1)
            Console.WriteLine($"Element found at index {index}");
        else
            Console.WriteLine("Element not found");
    }
}

```

### **C++**

```C++
\#include <iostream>
using namespace std;

int linearSearch(int arr[], int n, int target)
{
    for (int i = 0; i < n; i++)
    {
        if (arr[i] == target)
            return i;
    }
    return -1;
}

int main()
{
    int arr[] = {4, 2, 7, 9, 1};
    int n = sizeof(arr) / sizeof(arr[0]);
    int target = 9;

    int index = linearSearch(arr, n, target);
    if (index != -1)
        cout << "Element found at index " << index << endl;
    else
        cout << "Element not found" << endl;

    return 0;
}
```

---