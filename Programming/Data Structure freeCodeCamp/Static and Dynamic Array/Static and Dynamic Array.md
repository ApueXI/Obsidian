---
Created: 2025-08-04T09:17
tags:
  - William-Fiset
---
## ==What is an Array?==

An **array** is a **linear data structure** that stores a **fixed-size** sequence of elements of the **same data type**, placed in **contiguous memory locations**. Arrays allow quick access to elements using an **index**, starting from 0.

### ✅ Key Characteristics:

- **Indexed**: Each element has a unique index (starting at 0).
- **Fixed Size**: The size is defined when the array is created and cannot be changed.
- **Same Data Type**: All elements must be of the same type (e.g., all integers).
- **Efficient Access**: Direct access to any element using its index → O(1) time.

### 🧠 Why Use Arrays?

- Simple and fast to access elements.
- Useful for storing ordered data.
- Can be used as the base for more complex data structures like lists, stacks, and queues.

### 📌 Example in Python:

```Python
# Creating an array (list in Python)
arr = [10, 20, 30, 40]

# Accessing elements
print(arr[0])  # Output: 10

# Modifying elements
arr[2] = 35

# Traversing
for value in arr:
    print(value)
```

### 📊 Real-World Analogy:

Think of an array like a **row of mailboxes**:

- Each mailbox has a number (index).
- You can go directly to a mailbox (access by index).
- You can store and retrieve one item per box.

### Advantages:

- Fast element access (O(1)).
- Simple to implement and use.

### Disadvantages:

- Fixed size (not dynamic unless using resizable structures like Python lists).
- Inserting/deleting in the middle is costly (O(n)).

  

  

---

  

## ==When and Where is an Array Used?==

Arrays are used **when you need to store multiple values of the same type** in a single, organized collection that allows **quick access by index**. They are best suited for situations where the **number of elements is known in advance** and **random access** is required.

### ✅ When to Use an Array

1. **You know the number of elements in advance**
    - Arrays are **fixed in size**, so they’re great for problems where the size doesn’t change.
2. **You need fast access by index**
    - Accessing elements is done in constant time: **O(1)**.
3. **You want to store elements of the same data type**
    - Arrays enforce type consistency, especially in languages like C, C++, and Java.
4. **Memory layout matters**
    - Arrays are stored in **contiguous memory**, which improves performance in low-level operations.
5. **You don’t need frequent insertion or deletion**
    - These operations are **expensive** in arrays because they may require shifting elements.

### 🧠 Where Arrays Are Used (Real Applications)

|Use Case|Description|
|---|---|
|**Storing sensor readings**|Fixed-size arrays are perfect for collecting data points.|
|**Image and video processing**|Pixel data is often stored in 2D or 3D arrays.|
|**Game development**|Arrays track player stats, enemies, level maps, etc.|
|**Data tables / matrices**|2D arrays store rows and columns of data.|
|**Compiler symbol tables**|Used to manage variables during parsing.|
|**Sorting and searching**|Arrays are commonly used with algorithms like bubble sort, binary search, etc.|
|**Static data lookup**|Example: days of the week, month names, etc.|

### ⚠️ When NOT to Use an Array

- When the **number of items can change often** → use a list or dynamic array (like `ArrayList` in Java or `List` in Python).
- When you frequently **insert/delete elements in the middle**.
- When elements are **not all the same type** (use objects or dictionaries instead).

### 📝 Summary

Use arrays when:

- You need **fast access** to elements using an index.
- You have a **known, fixed size** collection.
- You want **simple, efficient memory usage**.

  

  

---

  

## ==Array Complexity==

Arrays are efficient data structures, but different operations have different time and space complexities depending on the context. Here’s a breakdown of **Time and Space Complexity** for common array operations:

### ⏱️ Time Complexity (1D Array)

|Operation|Time Complexity|Explanation|
|---|---|---|
|**Access by index**|O(1)|Direct access using index is constant time.|
|**Search**|O(n)|Must check each element until found (linear search).|
|**Insert at end**|O(1) _(if space)_|Direct insert if space is available.|
|**Insert at middle/start**|O(n)|Requires shifting elements to make space.|
|**Delete at end**|O(1)|Just remove the last element.|
|**Delete at middle/start**|O(n)|Must shift elements to fill the gap.|

### 🧠 Example:

```Python
arr = [1, 2, 3, 4, 5]

# Access → O(1)
print(arr[2])  # 3

# Search → O(n)
for i in arr:
    if i == 4:
        break

# Insert at index 1 → O(n)
arr.insert(1, 10)  # [1, 10, 2, 3, 4, 5]

# Delete from index 2 → O(n)
arr.pop(2)  # [1, 10, 3, 4, 5]
```

### 💾 Space Complexity

|Scenario|Space Complexity|
|---|---|
|**Storing n elements**|O(n)|
|**Temporary variables**|O(1) (if constant) or O(n) (if copied)|

- Arrays use **contiguous memory**: good for cache performance.
- Dynamic arrays (like Python `list`) may use **extra space** internally for resizing.

### 📌 Summary Table

|Operation|Time (Average/Worst)|Space|
|---|---|---|
|Access|O(1) / O(1)|O(1)|
|Search|O(n) / O(n)|O(1)|
|Insert (end)|O(1)* / O(n)|O(1)|
|Insert (middle)|O(n) / O(n)|O(1)|
|Delete (end)|O(1) / O(1)|O(1)|
|Delete (middle)|O(n) / O(n)|O(1)|

> *Amortized O(1) for dynamic arrays when resizing is not needed.

![[image.png]]

---

  

## ==Static Array – Usage Example==

A **static array** is an array with a **fixed size** defined at the time of declaration. It cannot grow or shrink during runtime. Static arrays are commonly used in low-level languages like **C** or **Java** where memory management is more manual.

### ✅ When to Use a Static Array

- You **know the number of elements** ahead of time.
- You want **fast, predictable performance**.
- You don’t need to insert or delete elements dynamically.
- Memory usage must remain **constant and controlled**.

### 🧱 Real-World Example:

**Store and display the scores of 5 students**

### ✅ In C:

```C
\#include <stdio.h>

int main() {
    int scores[5] = {85, 90, 78, 92, 88};  // Static array

    printf("Student Scores:\n");
    for (int i = 0; i < 5; i++) {
        printf("Student %d: %d\n", i + 1, scores[i]);
    }

    return 0;
}
```

### ✅ In Java:

```Java
public class StaticArrayExample {
    public static void main(String[] args) {
        int[] scores = {85, 90, 78, 92, 88};  // Static array

        System.out.println("Student Scores:");
        for (int i = 0; i < scores.length; i++) {
            System.out.println("Student " + (i + 1) + ": " + scores[i]);
        }
    }
}
```

### 🔍 Key Takeaways:

- Memory is **allocated at compile-time**.
- Index-based access is **fast (O(1))**.
- Cannot resize after creation.
- Suitable for **fixed-size datasets**.

---

---

  

## ==Dynamic Array – Implementation Details==

A **dynamic array** is a resizable array that can grow or shrink in size during runtime. Unlike static arrays, it does **not require knowing the size in advance**. When the current capacity is full, it **automatically allocates a larger array**, copies the old data, and adds new elements.

Dynamic arrays are used in many programming languages:

- **C++**: `std::vector`
- **Java**: `ArrayList`
- **Python**: `list`
- **C**: Manual implementation using `malloc()` and `realloc()`

### ✅ Key Concepts of Dynamic Array

### 1. **Internal Structure**

A dynamic array usually keeps:

- A **pointer to the array in memory**
- A **current size** (number of elements stored)
- A **capacity** (total allocated space)

### 2. **Resizing Strategy**

- When `size == capacity`, allocate a new array with **2× capacity**.
- Copy old elements to the new array.
- Free the old memory (if applicable).

### 🔧 Pseudo Implementation (in C-like style)

```C
struct DynamicArray {
    int *data;      // pointer to array
    int size;       // number of elements
    int capacity;   // total capacity
};

void init(struct DynamicArray *arr) {
    arr->capacity = 2;
    arr->size = 0;
    arr->data = malloc(sizeof(int) * arr->capacity);
}

void add(struct DynamicArray *arr, int value) {
    if (arr->size == arr->capacity) {
        // Double the capacity
        arr->capacity *= 2;
        arr->data = realloc(arr->data, sizeof(int) * arr->capacity);
    }
    arr->data[arr->size++] = value;
}
```

### ✅ Real Example in Python (already dynamic)

```Python
arr = []

# Adding elements dynamically
arr.append(10)
arr.append(20)
arr.append(30)

print(arr)  # Output: [10, 20, 30]
```

> Python’s list resizes automatically behind the scenes using a strategy similar to doubling the size.

### ⚙️ Time Complexity (Amortized)

|Operation|Time Complexity|Explanation|
|---|---|---|
|Access by index|O(1)|Like static arrays|
|Append (average)|O(1)|Fast unless resizing is triggered|
|Append (worst)|O(n)|Happens when resizing is needed|
|Insert/delete at middle|O(n)|Requires shifting elements|

### 📌 Summary

- Dynamic arrays **grow automatically** when needed.
- Useful when the **number of elements is unknown**.
- Internally use **resizing + copying strategy**.
- Resizing takes time, but **amortized cost** is still efficient.

---

  

## ==✅ Dynamic Array – Code Implementation in== ==**C**==

```C
\#include <stdio.h>
\#include <stdlib.h>

typedef struct {
    int *data;
    int size;
    int capacity;
} DynamicArray;

void init(DynamicArray *arr) {
    arr->capacity = 2;
    arr->size = 0;
    arr->data = (int *)malloc(sizeof(int) * arr->capacity);
}

void resize(DynamicArray *arr) {
    arr->capacity *= 2;
    arr->data = (int *)realloc(arr->data, sizeof(int) * arr->capacity);
}

void add(DynamicArray *arr, int value) {
    if (arr->size == arr->capacity) {
        resize(arr);
    }
    arr->data[arr->size++] = value;
}

void print(DynamicArray *arr) {
    for (int i = 0; i < arr->size; i++) {
        printf("%d ", arr->data[i]);
    }
    printf("\n");
}

void freeArray(DynamicArray *arr) {
    free(arr->data);
    arr->data = NULL;
    arr->size = arr->capacity = 0;
}

int main() {
    DynamicArray arr;
    init(&arr);

    add(&arr, 10);
    add(&arr, 20);
    add(&arr, 30);
    add(&arr, 40); // triggers resize

    print(&arr);   // Output: 10 20 30 40

    freeArray(&arr);
    return 0;
}
```

## ==✅ Dynamic Array – Code Implementation in== ==**Java (ArrayList-style)**==

```Java
public class DynamicArray {
    private int[] data;
    private int size;
    private int capacity;

    public DynamicArray() {
        capacity = 2;
        size = 0;
        data = new int[capacity];
    }

    private void resize() {
        capacity *= 2;
        int[] newData = new int[capacity];
        for (int i = 0; i < size; i++)
            newData[i] = data[i];
        data = newData;
    }

    public void add(int value) {
        if (size == capacity) {
            resize();
        }
        data[size++] = value;
    }

    public void print() {
        for (int i = 0; i < size; i++)
            System.out.print(data[i] + " ");
        System.out.println();
    }

    public static void main(String[] args) {
        DynamicArray arr = new DynamicArray();
        arr.add(10);
        arr.add(20);
        arr.add(30);
        arr.add(40); // triggers resize

        arr.print(); // Output: 10 20 30 40
    }
}
```

---

  

## ==🛠️ Operations on Dynamic Array==

A **dynamic array** supports various operations similar to a static array, but with added flexibility to **grow or shrink in size** at runtime. Below are the most common operations and their typical complexities:

### ✅ 1. **Access (Indexing)**

- **Description**: Get an element at a specific index.
- **Syntax** (Python/Java/C++): `arr[i]`
- **Time Complexity**: `O(1)` – direct memory access.

### ✅ 2. **Append / Add (at End)**

- **Description**: Adds a new element at the end of the array.
- **Time Complexity**:
    - **Amortized O(1)** – Fast most of the time.
    - **Worst-case O(n)** – Only when resizing is triggered.

### ✅ 3. **Insert (at Index)**

- **Description**: Insert an element at a specific position.
- **Action**: Shift elements rightward to make space.
- **Time Complexity**: `O(n)` – due to shifting.

### ✅ 4. **Delete (at Index)**

- **Description**: Remove element at a given index.
- **Action**: Shift elements leftward to fill the gap.
- **Time Complexity**: `O(n)` – shifting required.

  

### ✅ 5. **Search**

- **Description**: Find the position of an element.
- **Approach**: Linear search unless sorted.
- **Time Complexity**: `O(n)` – need to check each item.

### ✅ 6. **Resize**

- **Description**: Internal process when adding exceeds current capacity.
- **Action**: Allocate new array (usually 2× size), copy all elements.
- **Cost**: `O(n)` for that moment, but amortized `O(1)` per addition over time.

### 🧮 Summary Table

|Operation|Description|Time Complexity|
|---|---|---|
|Access|Get element by index|O(1)|
|Append (End)|Add element at the end|O(1) (amortized)|
|Insert (Middle)|Insert at any position|O(n)|
|Delete (Middle)|Remove element at index|O(n)|
|Search (Linear)|Find element in array|O(n)|
|Resize (internal)|Expand capacity when full|O(n)|

### 📝 Note:

- Dynamic arrays like Python `list`, Java `ArrayList`, and C++ `vector` manage **resizing automatically**.
- You don’t need to manually allocate or free memory (unless using C).

  

---

  

# ==Code Implementation==

---

- Starts with a fixed capacity
- Doubles capacity when full
- Supports adding elements

- Supports getting elements by index
- Supports getting current size
- Supports removing elements (optional, but I'll add a basic remove at index)

### Python — DynamicArray.py

```Python
class DynamicArray:
    def __init__(self, initial_capacity=4):
        self.capacity = initial_capacity
        self.size = 0
        self.data = [None] * self.capacity
    
    def __len__(self):
        return self.size
    
    def __getitem__(self, index):
        if 0 <= index < self.size:
            return self.data[index]
        raise IndexError("Index out of range")
    
    def __setitem__(self, index, value):
        if 0 <= index < self.size:
            self.data[index] = value
        else:
            raise IndexError("Index out of range")
    
    def append(self, value):
        if self.size >= self.capacity:
            self._resize()
        self.data[self.size] = value
        self.size += 1
    
    def _resize(self):
        old_capacity = self.capacity
        self.capacity *= 2
        new_data = [None] * self.capacity
        for i in range(self.size):
            new_data[i] = self.data[i]
        self.data = new_data
        print(f"Resized from {old_capacity} to {self.capacity}")
    
    def pop(self):
        if self.size == 0:
            raise IndexError("Pop from empty array")
        self.size -= 1
        return self.data[self.size]
    
    def insert(self, index, value):
        if index < 0 or index > self.size:
            raise IndexError("Index out of range")
        
        if self.size >= self.capacity:
            self._resize()
        
        # Shift elements to the right
        for i in range(self.size, index, -1):
            self.data[i] = self.data[i-1]
        
        self.data[index] = value
        self.size += 1
    
    def remove_at(self, index):
        if index < 0 or index >= self.size:
            raise IndexError("Index out of range")
        
        # Shift elements to the left
        for i in range(index, self.size - 1):
            self.data[i] = self.data[i + 1]
        
        self.size -= 1
    
    def __str__(self):
        return f"[{', '.join(str(self.data[i]) for i in range(self.size))}]"

# Example usage
if __name__ == "__main__":
    arr = DynamicArray(2)
    print(f"Initial capacity: {arr.capacity}")
    
    # Add elements to trigger resize
    for i in range(5):
        arr.append(i * 10)
        print(f"Added {i * 10}, size: {len(arr)}, array: {arr}")
    
    # Test other operations
    arr.insert(2, 999)
    print(f"After insert at index 2: {arr}")
    
    arr.remove_at(1)
    print(f"After remove at index 1: {arr}")
```

  

### C# — DynamicArray.cs

```C#
using System;

public class DynamicArray<T>
{
    private T[] data;
    private int size;
    private int capacity;

    public DynamicArray(int initialCapacity = 4)
    {
        capacity = initialCapacity;
        size = 0;
        data = new T[capacity];
    }

    public int Count => size;
    public int Capacity => capacity;

    public T this[int index]
    {
        get
        {
            if (index < 0 || index >= size)
                throw new IndexOutOfRangeException();
            return data[index];
        }
        set
        {
            if (index < 0 || index >= size)
                throw new IndexOutOfRangeException();
            data[index] = value;
        }
    }

    public void Add(T item)
    {
        if (size >= capacity)
            Resize();
        
        data[size] = item;
        size++;
    }

    private void Resize()
    {
        int oldCapacity = capacity;
        capacity *= 2;
        T[] newData = new T[capacity];
        
        for (int i = 0; i < size; i++)
        {
            newData[i] = data[i];
        }
        
        data = newData;
        Console.WriteLine($"Resized from {oldCapacity} to {capacity}");
    }

    public T RemoveLast()
    {
        if (size == 0)
            throw new InvalidOperationException("Array is empty");
        
        size--;
        T item = data[size];
        data[size] = default(T); // Clear reference
        return item;
    }

    public void Insert(int index, T item)
    {
        if (index < 0 || index > size)
            throw new IndexOutOfRangeException();
        
        if (size >= capacity)
            Resize();
        
        // Shift elements to the right
        for (int i = size; i > index; i--)
        {
            data[i] = data[i - 1];
        }
        
        data[index] = item;
        size++;
    }

    public void RemoveAt(int index)
    {
        if (index < 0 || index >= size)
            throw new IndexOutOfRangeException();
        
        // Shift elements to the left
        for (int i = index; i < size - 1; i++)
        {
            data[i] = data[i + 1];
        }
        
        size--;
        data[size] = default(T); // Clear reference
    }

    public override string ToString()
    {
        if (size == 0) return "[]";
        
        string result = "[";
        for (int i = 0; i < size; i++)
        {
            result += data[i];
            if (i < size - 1) result += ", ";
        }
        result += "]";
        return result;
    }
}

class Program
{
    static void Main()
    {
        var arr = new DynamicArray<int>(2);
        Console.WriteLine($"Initial capacity: {arr.Capacity}");
        
        // Add elements to trigger resize
        for (int i = 0; i < 5; i++)
        {
            arr.Add(i * 10);
            Console.WriteLine($"Added {i * 10}, size: {arr.Count}, array: {arr}");
        }
        
        // Test other operations
        arr.Insert(2, 999);
        Console.WriteLine($"After insert at index 2: {arr}");
        
        arr.RemoveAt(1);
        Console.WriteLine($"After remove at index 1: {arr}");
    }
}
```

### C++ — DynamicArray.cpp

```C++
\#include <iostream>
\#include <stdexcept>

template<typename T>
class DynamicArray {
private:
    T* data;
    size_t size;
    size_t capacity;

    void resize() {
        size_t oldCapacity = capacity;
        capacity *= 2;
        T* newData = new T[capacity];
        
        // Copy existing elements
        for (size_t i = 0; i < size; ++i) {
            newData[i] = data[i];
        }
        
        delete[] data;
        data = newData;
        std::cout << "Resized from " << oldCapacity << " to " << capacity << std::endl;
    }

public:
    explicit DynamicArray(size_t initialCapacity = 4) 
        : capacity(initialCapacity), size(0) {
        data = new T[capacity];
    }
    
    // Copy constructor
    DynamicArray(const DynamicArray& other) 
        : capacity(other.capacity), size(other.size) {
        data = new T[capacity];
        for (size_t i = 0; i < size; ++i) {
            data[i] = other.data[i];
        }
    }
    
    // Assignment operator
    DynamicArray& operator=(const DynamicArray& other) {
        if (this != &other) {
            delete[] data;
            capacity = other.capacity;
            size = other.size;
            data = new T[capacity];
            for (size_t i = 0; i < size; ++i) {
                data[i] = other.data[i];
            }
        }
        return *this;
    }
    
    // Destructor
    ~DynamicArray() {
        delete[] data;
    }
    
    size_t getSize() const { return size; }
    size_t getCapacity() const { return capacity; }
    
    // Array access operators
    T& operator[](size_t index) {
        if (index >= size) {
            throw std::out_of_range("Index out of range");
        }
        return data[index];
    }
    
    const T& operator[](size_t index) const {
        if (index >= size) {
            throw std::out_of_range("Index out of range");
        }
        return data[index];
    }
    
    void push_back(const T& value) {
        if (size >= capacity) {
            resize();
        }
        data[size] = value;
        ++size;
    }
    
    T pop_back() {
        if (size == 0) {
            throw std::runtime_error("Array is empty");
        }
        --size;
        return data[size];
    }
    
    void insert(size_t index, const T& value) {
        if (index > size) {
            throw std::out_of_range("Index out of range");
        }
        
        if (size >= capacity) {
            resize();
        }
        
        // Shift elements to the right
        for (size_t i = size; i > index; --i) {
            data[i] = data[i - 1];
        }
        
        data[index] = value;
        ++size;
    }
    
    void removeAt(size_t index) {
        if (index >= size) {
            throw std::out_of_range("Index out of range");
        }
        
        // Shift elements to the left
        for (size_t i = index; i < size - 1; ++i) {
            data[i] = data[i + 1];
        }
        --size;
    }
    
    void print() const {
        std::cout << "[";
        for (size_t i = 0; i < size; ++i) {
            std::cout << data[i];
            if (i < size - 1) std::cout << ", ";
        }
        std::cout << "]" << std::endl;
    }
};

int main() {
    DynamicArray<int> arr(2);
    std::cout << "Initial capacity: " << arr.getCapacity() << std::endl;
    
    // Add elements to trigger resize
    for (int i = 0; i < 5; ++i) {
        arr.push_back(i * 10);
        std::cout << "Added " << i * 10 << ", size: " << arr.getSize() << ", array: ";
        arr.print();
    }
    
    // Test other operations
    arr.insert(2, 999);
    std::cout << "After insert at index 2: ";
    arr.print();
    
    arr.removeAt(1);
    std::cout << "After remove at index 1: ";
    arr.print();
    
    return 0;
}
```

---