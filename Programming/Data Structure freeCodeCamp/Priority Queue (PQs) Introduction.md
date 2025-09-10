---
Created: 2025-08-06T10:19
tags:
  - William-Fiset
---
# ==Discussion & Example of PQs==

---

## 🧠 ==What Is a Priority Queue?==

A **Priority Queue** is a special type of queue where **each element has a priority**, and elements are dequeued **based on priority**, not just arrival time.

- Elements with **higher priority are served first**.
- If two elements have the same priority, they follow **FIFO**.

📌 It is usually implemented using a **heap (binary heap)** for efficient access to the highest (or lowest) priority.

  

## 🎯 Real-Life Examples

- **Operating Systems**: CPU job scheduling (urgent tasks first)
- **Networking**: Packets with higher priority are sent first
- **AI Algorithms**: Like A* pathfinding using cost-based priorities
- **Emergency Room**: Patients are treated based on urgency, not arrival

  

## ✅ Python (using `heapq` - min-heap)

```Python
import heapq

# By default, heapq is a min-heap
pq = []

# Push with (priority, value)
heapq.heappush(pq, (2, 'Low priority'))
heapq.heappush(pq, (1, 'High priority'))
heapq.heappush(pq, (3, 'Very low priority'))

# Pop returns smallest priority
while pq:
    priority, task = heapq.heappop(pq)
    print(f"Priority: {priority}, Task: {task}")
```

🟢 Output:

```Plain
Priority: 1, Task: High priority
Priority: 2, Task: Low priority
Priority: 3, Task: Very low priority
```

📝 To make a **max-heap**, use negative priorities: `(-priority, value)`

  

## ✅ C# (using `SortedDictionary` or `PriorityQueue<TElement, TPriority>` in .NET 6+)

```C#
using System;
using System.Collections.Generic;

class Program {
    static void Main() {
        var pq = new PriorityQueue<string, int>();

        pq.Enqueue("Low priority", 2);
        pq.Enqueue("High priority", 1);
        pq.Enqueue("Very low priority", 3);

        while (pq.Count > 0) {
            Console.WriteLine(pq.Dequeue());
        }
    }
}
```

🟢 Output:

```Plain
High priority
Low priority
Very low priority
```

> Requires .NET 6+. In older versions, you can use SortedList or custom heap classes.

  

## ✅ C++ (using `std::priority_queue`)

```C++
\#include <iostream>
\#include <queue>
\#include <vector>

using namespace std;

int main() {
    // Max-heap by default
    priority_queue<pair<int, string>> pq;

    pq.push({2, "Low priority"});
    pq.push({1, "High priority"});
    pq.push({3, "Very low priority"});

    while (!pq.empty()) {
        auto [priority, task] = pq.top();
        cout << "Priority: " << priority << ", Task: " << task << endl;
        pq.pop();
    }
}
```

🟢 Output:

```Plain
Priority: 3, Task: Very low priority
Priority: 2, Task: Low priority
Priority: 1, Task: High priority
```

📝 To make a **min-heap**, use `greater<>` or invert priority: `pq.push({-priority, value})`

  

## ⏱️ Time Complexity

|Operation|Time Complexity|
|---|---|
|Insert (enqueue)|O(log n)|
|Remove (dequeue)|O(log n)|
|Peek|O(1)|

> Heap-based implementation makes it fast.

## 📌 Summary

|Feature|Queue|Priority Queue|
|---|---|---|
|Order|FIFO|Based on priority|
|Insertion Time|O(1)|O(log n)|
|Deletion Time|O(1) (from front)|O(log n) (from highest/lowest priority)|
|Backed By|List / Linked List|Binary Heap (Min/Max)|

---

  

## 🧠 ==What is a Heap?==

A **Heap** is a special **tree-based** data structure that satisfies the **heap property**:

- **Max-Heap**: The value of each node is **greater than or equal** to its children.
    
    → Largest value is at the root.
    
- **Min-Heap**: The value of each node is **less than or equal** to its children.
    
    → Smallest value is at the root.
    

> Heaps are usually implemented using arrays for efficiency.

## 🌲 Heap as a Complete Binary Tree

- **Complete Binary Tree**: Every level is fully filled except possibly the last, and all nodes are as far left as possible.
- You can store the heap in an array, and for any index `i`:
    - **Left child**: `2i + 1`
    - **Right child**: `2i + 2`
    - **Parent**: `(i - 1) // 2`

## 🎯 Where is Heap Used?

- **Priority Queues**
- **Heap Sort**
- **Dijkstra’s Algorithm** (shortest path)
- _A Pathfinding_
- **Median in a Stream**

## ⏱️ Time Complexity

|Operation|Time Complexity|
|---|---|
|Insertion|O(log n)|
|Deletion (root)|O(log n)|
|Peek (get root)|O(1)|
|Build Heap (n items)|O(n)|

## ✅ Python – Min-Heap using `heapq`

```Python
import heapq

heap = []
heapq.heappush(heap, 5)
heapq.heappush(heap, 2)
heapq.heappush(heap, 8)

print(heapq.heappop(heap))  # 2
print(heap[0])              # 5 (min element)
```

📝 Python `heapq` is a min-heap. Use negative values for max-heap.

  

## ✅ C# – Min-Heap with `PriorityQueue<TElement, TPriority>` (.NET 6+)

```C#
using System;
using System.Collections.Generic;

class Program {
    static void Main() {
        var heap = new PriorityQueue<string, int>();
        heap.Enqueue("Five", 5);
        heap.Enqueue("Two", 2);
        heap.Enqueue("Eight", 8);

        Console.WriteLine(heap.Dequeue());  // "Two"
    }
}
```

📝 The second parameter is the **priority**, not the value.

  

## ✅ C++ – Max-Heap using `priority_queue`

```C++
\#include <iostream>
\#include <queue>

int main() {
    std::priority_queue<int> maxHeap;

    maxHeap.push(5);
    maxHeap.push(2);
    maxHeap.push(8);

    std::cout << maxHeap.top() << std::endl;  // 8
    maxHeap.pop();
    std::cout << maxHeap.top() << std::endl;  // 5

    return 0;
}
```

📝 For a **min-heap**, use:

```C++
std::priority_queue<int, std::vector<int>, std::greater<int>> minHeap;
```

  

## 📌 Summary Table

|Feature|Max-Heap|Min-Heap|
|---|---|---|
|Root Value|Maximum|Minimum|
|Used in|Heap Sort, Priority Queue|Dijkstra, Task Scheduling|
|Backed By|Complete Binary Tree|Complete Binary Tree|

---

  

## 🧠 ==When and Where Is a Priority Queue Used?==

A **Priority Queue** is used **whenever elements must be processed based on priority** instead of the order they arrive (FIFO). It allows efficient insertion and removal of elements based on their assigned priorities.

## 📍 Real-World Use Cases

|Scenario|Why Priority Queue?|
|---|---|
|**Operating Systems**|Task/process scheduling: higher-priority processes are executed first|
|**Network Routing**|Packets with higher priority are sent before others (QoS systems)|
|**Emergency Rooms**|Patients treated based on urgency, not arrival time|
|**Print Queue**|Urgent print jobs jump ahead of low-priority ones|
|**Event Simulation**|Events with the earliest timestamp (highest priority) are processed first|
|**Stock Market Matching Engine**|Buy/sell orders prioritized by price or time|
|_AI Algorithms (e.g., A)_*|Nodes with lowest estimated cost are explored first|
|**Real-time systems**|Sensor alerts or interrupts that need immediate action|

## 💻 Programming/Algorithmic Use Cases

|Algorithm/Problem|How PQ Helps|
|---|---|
|**Dijkstra’s Shortest Path**|Always pick the node with the lowest cost (min-priority)|
|**Prim’s Minimum Spanning Tree**|Select edge with minimum weight|
|_A Search Algorithm_*|Expands nodes based on `f(n) = g(n) + h(n)`|
|**Huffman Coding**|Combines lowest-frequency nodes first|
|**Task Scheduling**|Select next task with the highest priority|
|**K Largest/Smallest Elements**|Maintain top K using a min/max heap|
|**Streaming Median**|Two heaps used to balance numbers efficiently|

## ⏱️ Why Use PQ Instead of Sorting?

|Operation|With PQ|With Sorting|
|---|---|---|
|Insert an element|`O(log n)`|`O(n)` (shift)|
|Remove highest/lowest|`O(log n)`|`O(1)` or `O(n)`|
|Repeated removals|Efficient|Re-sorting needed|

A priority queue **avoids the overhead of sorting** after each insertion and is much faster for dynamic scenarios.

## 📌 Summary

- **Use PQ when order of processing depends on priority**, not insertion order.
- Ideal for real-time decisions, optimization algorithms, and simulations.
- Backed by **heaps** (min-heap or max-heap) for efficient performance.

  

---

  

## 🧠 ==What’s the difference (Min PQ and Max PQ)?==

- **Min Priority Queue**: Removes the element with the **smallest priority** first.
    
    - **Max Priority Queue**: Removes the element with the **largest priority** first.
    
    Most built-in priority queues (like Python’s `heapq` and C++’s `std::priority_queue`) default to either min or max, but sometimes you only have one and need to invert behavior.
    
      
    

## 🔄 How to convert Min PQ → Max PQ?

### The trick: **Invert the priorities**

- When inserting, **store the negative of the priority**.
- When extracting, invert back (negate again).

This effectively reverses the ordering.

## ✅ Python Example (`heapq` is a Min-Heap by default)

```Python
import heapq

max_pq = []

# Insert with negative priority to simulate max heap
heapq.heappush(max_pq, -10)
heapq.heappush(max_pq, -5)
heapq.heappush(max_pq, -20)

# Extract elements (invert sign back)
print(-heapq.heappop(max_pq))  # 20
print(-heapq.heappop(max_pq))  # 10
print(-heapq.heappop(max_pq))  # 5
```

  

## ✅ C# Example

In .NET 6+, `PriorityQueue<TElement, TPriority>` is a Min-PQ by default. To simulate Max-PQ, you can invert priority similarly:

```C#
using System;
using System.Collections.Generic;

class Program {
    static void Main() {
        var maxPQ = new PriorityQueue<string, int>();

        // Insert with negative priority to simulate max heap
        maxPQ.Enqueue("Task A", -10);
        maxPQ.Enqueue("Task B", -5);
        maxPQ.Enqueue("Task C", -20);

        while (maxPQ.Count > 0) {
            string task = maxPQ.Dequeue();
            Console.WriteLine(task);
        }
        // Output order: Task C, Task A, Task B
    }
}
```

  

## ✅ C++ Example

C++ `std::priority_queue` is a Max-PQ by default. To create a Min-PQ, you’d invert or use custom comparator.

So for Max-PQ, just use it directly:

```C++
\#include <iostream>
\#include <queue>

int main() {
    std::priority_queue<int> maxPQ;  // max-heap by default

    maxPQ.push(10);
    maxPQ.push(5);
    maxPQ.push(20);

    while (!maxPQ.empty()) {
        std::cout << maxPQ.top() << " ";  // Output: 20 10 5
        maxPQ.pop();
    }
}
```

If you had a Min-PQ using `greater<>`, to revert to Max-PQ just use default `priority_queue` as above.

  

## 📌 Summary

|Language|Default PQ Type|How to Make Max PQ from Min PQ|
|---|---|---|
|Python|Min-Heap|Store negative priorities|
|C#|Min-PQ|Store negative priorities|
|C++|Max-PQ|Default is max PQ; no changes needed|

---

  

## 🧠 Priority Queue: Overview

A **Priority Queue** is an abstract data type where each element has a **priority**. Elements with **higher priority are dequeued before lower ones**, regardless of the order they were added.

Under the hood, a **binary heap** is typically used for performance.

## ⏱️ Time Complexity Table

|Operation|Time Complexity|Notes|
|---|---|---|
|**Insertion (enqueue)**|`O(log n)`|Percolates up in the heap|
|**Deletion (dequeue)**|`O(log n)`|Removes highest or lowest priority|
|**Peek (get max/min)**|`O(1)`|Root element in the heap|
|**Build from n items**|`O(n)`|Done using "heapify" operation|
|**Search**|`O(n)`|Must scan entire structure|
|**Update Priority**|`O(n)` worst|May need to reheapify manually|

## 🔧 Data Structures Used Behind the Scenes

|Implementation Type|Insert|Remove|Peek|Notes|
|---|---|---|---|---|
|**Binary Heap**|O(log n)|O(log n)|O(1)|Most common (e.g., `heapq`, `std::priority_queue`)|
|**Unordered Array**|O(1)|O(n)|O(n)|Fast insert, slow removal|
|**Ordered Array**|O(n)|O(1)|O(1)|Fast removal, slow insert|
|**Balanced BST**|O(log n)|O(log n)|O(1)–O(log n)|Less common, more flexible|
|**Fibonacci Heap**|O(1)*|O(log n)*|O(1)|Used in theoretical analysis (e.g., Dijkstra), not in practice|

  

## ✅ Language-Specific Notes

### 🐍 Python (`heapq`)

- Backed by a binary min-heap
- `heappush()` → `O(log n)`
- `heappop()` → `O(log n)`
- Custom objects require you to use tuples: `(priority, item)`
- Use `priority` for max-heap behavior

### 💠 C# (`PriorityQueue<TElement, TPriority>` – .NET 6+)

- Backed by a min-heap
- `Enqueue()` and `Dequeue()` both `O(log n)`
- Priorities can be negative to simulate max behavior
- Doesn’t support updating priority directly (reinsert instead)

### ➕ C++ (`std::priority_queue`)

- Backed by a max-heap (default)
- `push()` → `O(log n)`
- `pop()` → `O(log n)`
- Use `std::greater<T>` to make it min-heap
- Doesn't support direct priority updates; must rebuild or reinsert

## 📌 Summary Table

|Operation|Binary Heap|Ordered Array|Unordered Array|BST|
|---|---|---|---|---|
|Insert|`O(log n)`|`O(n)`|`O(1)`|`O(log n)`|
|Delete Max/Min|`O(log n)`|`O(1)`|`O(n)`|`O(log n)`|
|Peek|`O(1)`|`O(1)`|`O(n)`|`O(1)` to `O(log n)`|

---

# ==Binary Heap PQ Implementation Details==

---

  

## 🧠 ==What are Sinking and Swimming?==

In **binary heaps** (min or max), these operations maintain the **heap property** after inserting or removing elements:

|Operation|Also Called|Purpose|
|---|---|---|
|**Swim**|Bubble Up / Sift Up|Fix heap after **inserting** an element|
|**Sink**|Bubble Down / Sift Down|Fix heap after **removing** root (top element)|

## 🎯 Example Scenarios

- **Insert →** Use **swim** to push the new item _up_ if it violates the heap condition.
- **Remove top →** Use **sink** to push the swapped element _down_ if it's too big (max-heap) or too small (min-heap).

## 🧮 Swim (Sift Up)

**Idea**: Compare child with parent; if it violates the heap rule, **swap with parent** and keep going.

### For Max-Heap:

```Plain
if (heap[i] > heap[parent(i)]) → swap and keep swimming
```

## ⛓️ Sink (Sift Down)

**Idea**: After removing the root, move the last element to root and **push it down** if needed.

### For Max-Heap:

```Plain
if (heap[i] < heap[larger_child]) → swap and keep sinking
```

  

## ✅ Python (Manual Max-Heap)

```Python
def swim(heap, i):
    while i > 0:
        parent = (i - 1) // 2
        if heap[i] > heap[parent]:
            heap[i], heap[parent] = heap[parent], heap[i]
            i = parent
        else:
            break

def sink(heap, i):
    n = len(heap)
    while 2 * i + 1 < n:
        j = 2 * i + 1  # left child
        if j + 1 < n and heap[j + 1] > heap[j]:
            j += 1  # right child is larger
        if heap[i] >= heap[j]:
            break
        heap[i], heap[j] = heap[j], heap[i]
        i = j
```

  

## ✅ C# (Manual Max-Heap)

```C#
void Swim(List<int> heap, int i) {
    while (i > 0) {
        int parent = (i - 1) / 2;
        if (heap[i] > heap[parent]) {
            (heap[i], heap[parent]) = (heap[parent], heap[i]);
            i = parent;
        } else break;
    }
}

void Sink(List<int> heap, int i) {
    int n = heap.Count;
    while (2 * i + 1 < n) {
        int j = 2 * i + 1;
        if (j + 1 < n && heap[j + 1] > heap[j]) j++;
        if (heap[i] >= heap[j]) break;
        (heap[i], heap[j]) = (heap[j], heap[i]);
        i = j;
    }
}
```

  

## ✅ C++ (Manual Max-Heap)

```C++
\#include <vector>
\#include <algorithm>
using namespace std;

void swim(vector<int>& heap, int i) {
    while (i > 0) {
        int parent = (i - 1) / 2;
        if (heap[i] > heap[parent]) {
            swap(heap[i], heap[parent]);
            i = parent;
        } else break;
    }
}

void sink(vector<int>& heap, int i) {
    int n = heap.size();
    while (2 * i + 1 < n) {
        int j = 2 * i + 1;
        if (j + 1 < n && heap[j + 1] > heap[j]) j++;
        if (heap[i] >= heap[j]) break;
        swap(heap[i], heap[j]);
        i = j;
    }
}
```

  

## 📌 Summary Table

|Action|Operation|When It Happens|Time Complexity|
|---|---|---|---|
|**Swim**|Sift Up|After insert|O(log n)|
|**Sink**|Sift Down|After removing root|O(log n)|

---

  

## 🧠 ==What Does “Adding Elements to a PQ” Mean?==

When you add an element to a **priority queue**, you must not only store the element, but **also maintain the priority order**. Most efficient priority queues are implemented using a **binary heap**, which uses the **swim (sift-up)** operation to keep the heap property intact.

> 🎯 In a Max-Priority Queue, higher values have higher priority.
> 
> 🎯 In a **Min-Priority Queue**, lower values have higher priority.

  

## 🔄 Algorithm: Inserting (aka Enqueue)

**Steps**:

1. Add the new element to the end of the heap.
2. Use **swim (sift-up)** to move the element up until the heap property is restored.

⏱️ **Time Complexity:** `O(log n)`

📦 **Space Complexity:** `O(1)` (in-place)

## ✅ Python Implementation (Manual Max-Heap)

```Python
def insert(heap, value):
    heap.append(value)
    swim(heap, len(heap) - 1)

def swim(heap, i):
    while i > 0:
        parent = (i - 1) // 2
        if heap[i] > heap[parent]:
            heap[i], heap[parent] = heap[parent], heap[i]
            i = parent
        else:
            break

# Example
heap = []
insert(heap, 10)
insert(heap, 5)
insert(heap, 20)
print(heap)  # Output: [20, 5, 10]
```

## ✅ C# Implementation (Manual Max-Heap)

```C#
void Insert(List<int> heap, int value) {
    heap.Add(value);
    Swim(heap, heap.Count - 1);
}

void Swim(List<int> heap, int i) {
    while (i > 0) {
        int parent = (i - 1) / 2;
        if (heap[i] > heap[parent]) {
            (heap[i], heap[parent]) = (heap[parent], heap[i]);
            i = parent;
        } else break;
    }
}

// Example usage
var heap = new List<int>();
Insert(heap, 10);
Insert(heap, 5);
Insert(heap, 20);
// heap now: [20, 5, 10]
```

## ✅ C++ Implementation (Manual Max-Heap)

```C++
\#include <iostream>
\#include <vector>
\#include <algorithm>
using namespace std;

void swim(vector<int>& heap, int i) {
    while (i > 0) {
        int parent = (i - 1) / 2;
        if (heap[i] > heap[parent]) {
            swap(heap[i], heap[parent]);
            i = parent;
        } else break;
    }
}

void insert(vector<int>& heap, int value) {
    heap.push_back(value);
    swim(heap, heap.size() - 1);
}

int main() {
    vector<int> heap;
    insert(heap, 10);
    insert(heap, 5);
    insert(heap, 20);
    for (int val : heap)
        cout << val << " "; // Output may be: 20 5 10
}
```

## 📌 Summary Table

|Operation|Action|Time Complexity|
|---|---|---|
|`Insert()`|Add new element|`O(log n)`|
|`Swim()`|Restore heap property (bottom-up)|`O(log n)`|

---

  

## 🧠 ==What Does "Polling from a PQ" Mean?==

Polling = **Removing the element with the highest (or lowest) priority**, depending on the type of PQ:

- **Max-Priority Queue** → Remove the **maximum** element (usually at index `0`)
- **Min-Priority Queue** → Remove the **minimum** element (also at index `0`)

Since PQs are usually implemented as **binary heaps**, we must:

1. Remove the root (element at index 0)
2. Replace it with the last element
3. Use **sink (sift-down)** to restore the heap property

## 🔄 Algorithm: Removing (Polling)

**Steps**:

1. Save the root (top priority) value.
2. Move the last element to root.
3. Pop the last element.
4. **Sink** the new root down if needed.

⏱️ **Time Complexity:** `O(log n)`

📦 **Space Complexity:** `O(1)` (in-place)

## ✅ Python (Manual Max-Heap)

```Python
python
CopyEdit
def poll(heap):
    if not heap:
        return None
    top = heap[0]
    heap[0] = heap[-1]
    heap.pop()
    sink(heap, 0)
    return top

def sink(heap, i):
    n = len(heap)
    while 2 * i + 1 < n:
        j = 2 * i + 1
        if j + 1 < n and heap[j + 1] > heap[j]:
            j += 1
        if heap[i] >= heap[j]:
            break
        heap[i], heap[j] = heap[j], heap[i]
        i = j

# Example usage:
heap = [20, 5, 10]
print(poll(heap))  # 20
print(heap)        # [10, 5]

```

## ✅ C# (Manual Max-Heap)

```C#
csharp
CopyEdit
int Poll(List<int> heap) {
    if (heap.Count == 0) return -1;
    int top = heap[0];
    heap[0] = heap[^1];
    heap.RemoveAt(heap.Count - 1);
    Sink(heap, 0);
    return top;
}

void Sink(List<int> heap, int i) {
    int n = heap.Count;
    while (2 * i + 1 < n) {
        int j = 2 * i + 1;
        if (j + 1 < n && heap[j + 1] > heap[j]) j++;
        if (heap[i] >= heap[j]) break;
        (heap[i], heap[j]) = (heap[j], heap[i]);
        i = j;
    }
}

// Example usage:
var heap = new List<int> { 20, 5, 10 };
Console.WriteLine(Poll(heap)); // 20

```

## ✅ C++ (Manual Max-Heap)

```C++
cpp
CopyEdit
\#include <iostream>
\#include <vector>
\#include <algorithm>
using namespace std;

void sink(vector<int>& heap, int i) {
    int n = heap.size();
    while (2 * i + 1 < n) {
        int j = 2 * i + 1;
        if (j + 1 < n && heap[j + 1] > heap[j]) j++;
        if (heap[i] >= heap[j]) break;
        swap(heap[i], heap[j]);
        i = j;
    }
}

int poll(vector<int>& heap) {
    if (heap.empty()) return -1;
    int top = heap[0];
    heap[0] = heap.back();
    heap.pop_back();
    sink(heap, 0);
    return top;
}

int main() {
    vector<int> heap = { 20, 5, 10 };
    cout << poll(heap) << endl; // 20
}

```

## 📌 Summary Table

|Operation|Description|Time Complexity|
|---|---|---|
|`Poll()`|Remove top priority element|`O(log n)`|
|`Sink()`|Restore heap property (top-down)|`O(log n)`|

---

# ==Code Implementation==

---

## ==Max heap==

- Uses a binary heap internally to implement a max priority queue
- Starts with a fixed capacity (expandable if needed)
- Inserts elements while maintaining heap order

- Retrieves the maximum element in **O(1)**
- Removes the maximum element in **O(log n)**
- Supports getting current size

## **Python – Max Heap Priority Queue**

```Python
class MaxHeap:
    def __init__(self):
        self.heap = []
    
    def parent(self, i):
        return (i - 1) // 2
    
    def left_child(self, i):
        return 2 * i + 1
    
    def right_child(self, i):
        return 2 * i + 2
    
    def swap(self, i, j):
        self.heap[i], self.heap[j] = self.heap[j], self.heap[i]
    
    def insert(self, key):
        """Insert a new key into the max heap"""
        self.heap.append(key)
        self._heapify_up(len(self.heap) - 1)
    
    def _heapify_up(self, i):
        """Maintain heap property by moving element up"""
        while i != 0 and self.heap[self.parent(i)] < self.heap[i]:
            self.swap(i, self.parent(i))
            i = self.parent(i)
    
    def extract_max(self):
        """Remove and return the maximum element"""
        if len(self.heap) == 0:
            raise IndexError("Heap is empty")
        
        if len(self.heap) == 1:
            return self.heap.pop()
        
        root = self.heap[0]
        self.heap[0] = self.heap.pop()
        self._heapify_down(0)
        return root
    
    def _heapify_down(self, i):
        """Maintain heap property by moving element down"""
        largest = i
        left = self.left_child(i)
        right = self.right_child(i)
        
        if left < len(self.heap) and self.heap[left] > self.heap[largest]:
            largest = left
        
        if right < len(self.heap) and self.heap[right] > self.heap[largest]:
            largest = right
        
        if largest != i:
            self.swap(i, largest)
            self._heapify_down(largest)
    
    def peek(self):
        """Return the maximum element without removing it"""
        if len(self.heap) == 0:
            raise IndexError("Heap is empty")
        return self.heap[0]
    
    def size(self):
        """Return the number of elements in the heap"""
        return len(self.heap)
    
    def is_empty(self):
        """Check if the heap is empty"""
        return len(self.heap) == 0
    
    def build_heap(self, arr):
        """Build heap from an array"""
        self.heap = arr[:]
        for i in range(len(arr) // 2 - 1, -1, -1):
            self._heapify_down(i)


# Example usage and test
if __name__ == "__main__":
    max_heap = MaxHeap()
    
    # Insert elements
    elements = [10, 20, 15, 30, 40]
    print("Inserting:", elements)
    for elem in elements:
        max_heap.insert(elem)
    
    print("Heap after insertions:", max_heap.heap)
    print("Max element:", max_heap.peek())
    
    # Extract elements
    print("\nExtracting elements:")
    while not max_heap.is_empty():
        print("Extracted:", max_heap.extract_max())
    
    # Build heap from array
    arr = [1, 3, 6, 5, 2, 4]
    print(f"\nBuilding heap from array: {arr}")
    max_heap.build_heap(arr)
    print("Built heap:", max_heap.heap)
```

## **C# – Max Heap Priority Queue**

```C#
using System;
using System.Collections.Generic;

public class MaxHeap<T> where T : IComparable<T>
{
    private List<T> heap;
    
    public MaxHeap()
    {
        heap = new List<T>();
    }
    
    private int Parent(int i) => (i - 1) / 2;
    private int LeftChild(int i) => 2 * i + 1;
    private int RightChild(int i) => 2 * i + 2;
    
    private void Swap(int i, int j)
    {
        T temp = heap[i];
        heap[i] = heap[j];
        heap[j] = temp;
    }
    
    public void Insert(T key)
    {
        heap.Add(key);
        HeapifyUp(heap.Count - 1);
    }
    
    private void HeapifyUp(int i)
    {
        while (i != 0 && heap[Parent(i)].CompareTo(heap[i]) < 0)
        {
            Swap(i, Parent(i));
            i = Parent(i);
        }
    }
    
    public T ExtractMax()
    {
        if (heap.Count == 0)
            throw new InvalidOperationException("Heap is empty");
        
        if (heap.Count == 1)
        {
            T result = heap[0];
            heap.RemoveAt(0);
            return result;
        }
        
        T root = heap[0];
        heap[0] = heap[heap.Count - 1];
        heap.RemoveAt(heap.Count - 1);
        HeapifyDown(0);
        return root;
    }
    
    private void HeapifyDown(int i)
    {
        int largest = i;
        int left = LeftChild(i);
        int right = RightChild(i);
        
        if (left < heap.Count && heap[left].CompareTo(heap[largest]) > 0)
            largest = left;
        
        if (right < heap.Count && heap[right].CompareTo(heap[largest]) > 0)
            largest = right;
        
        if (largest != i)
        {
            Swap(i, largest);
            HeapifyDown(largest);
        }
    }
    
    public T Peek()
    {
        if (heap.Count == 0)
            throw new InvalidOperationException("Heap is empty");
        return heap[0];
    }
    
    public int Size => heap.Count;
    public bool IsEmpty => heap.Count == 0;
    
    public void BuildHeap(T[] arr)
    {
        heap = new List<T>(arr);
        for (int i = heap.Count / 2 - 1; i >= 0; i--)
        {
            HeapifyDown(i);
        }
    }
    
    public void PrintHeap()
    {
        Console.WriteLine($"Heap: [{string.Join(", ", heap)}]");
    }
}

// Example usage
class Program
{
    static void Main()
    {
        MaxHeap<int> maxHeap = new MaxHeap<int>();
        
        // Insert elements
        int[] elements = {10, 20, 15, 30, 40};
        Console.WriteLine($"Inserting: [{string.Join(", ", elements)}]");
        foreach (int elem in elements)
        {
            maxHeap.Insert(elem);
        }
        
        maxHeap.PrintHeap();
        Console.WriteLine($"Max element: {maxHeap.Peek()}");
        
        // Extract elements
        Console.WriteLine("\nExtracting elements:");
        while (!maxHeap.IsEmpty)
        {
            Console.WriteLine($"Extracted: {maxHeap.ExtractMax()}");
        }
        
        // Build heap from array
        int[] arr = {1, 3, 6, 5, 2, 4};
        Console.WriteLine($"\nBuilding heap from array: [{string.Join(", ", arr)}]");
        maxHeap.BuildHeap(arr);
        maxHeap.PrintHeap();
        
        Console.ReadLine();
    }
}
```

## **C++ – Max Heap Priority Queue**

```C++
\#include <iostream>
\#include <vector>
\#include <stdexcept>

template<typename T>
class MaxHeap {
private:
    std::vector<T> heap;
    
    int parent(int i) { return (i - 1) / 2; }
    int leftChild(int i) { return 2 * i + 1; }
    int rightChild(int i) { return 2 * i + 2; }
    
    void swap(int i, int j) {
        T temp = heap[i];
        heap[i] = heap[j];
        heap[j] = temp;
    }
    
    void heapifyUp(int i) {
        while (i != 0 && heap[parent(i)] < heap[i]) {
            swap(i, parent(i));
            i = parent(i);
        }
    }
    
    void heapifyDown(int i) {
        int largest = i;
        int left = leftChild(i);
        int right = rightChild(i);
        
        if (left < heap.size() && heap[left] > heap[largest])
            largest = left;
        
        if (right < heap.size() && heap[right] > heap[largest])
            largest = right;
        
        if (largest != i) {
            swap(i, largest);
            heapifyDown(largest);
        }
    }
    
public:
    MaxHeap() {}
    
    void insert(T key) {
        heap.push_back(key);
        heapifyUp(heap.size() - 1);
    }
    
    T extractMax() {
        if (heap.empty())
            throw std::runtime_error("Heap is empty");
        
        if (heap.size() == 1) {
            T result = heap[0];
            heap.pop_back();
            return result;
        }
        
        T root = heap[0];
        heap[0] = heap.back();
        heap.pop_back();
        heapifyDown(0);
        return root;
    }
    
    T peek() const {
        if (heap.empty())
            throw std::runtime_error("Heap is empty");
        return heap[0];
    }
    
    int size() const {
        return heap.size();
    }
    
    bool isEmpty() const {
        return heap.empty();
    }
    
    void buildHeap(const std::vector<T>& arr) {
        heap = arr;
        for (int i = heap.size() / 2 - 1; i >= 0; i--) {
            heapifyDown(i);
        }
    }
    
    void printHeap() const {
        std::cout << "Heap: [";
        for (int i = 0; i < heap.size(); i++) {
            std::cout << heap[i];
            if (i < heap.size() - 1) std::cout << ", ";
        }
        std::cout << "]" << std::endl;
    }
};

// Example usage
int main() {
    MaxHeap<int> maxHeap;
    
    // Insert elements
    std::vector<int> elements = {10, 20, 15, 30, 40};
    std::cout << "Inserting: [";
    for (int i = 0; i < elements.size(); i++) {
        std::cout << elements[i];
        if (i < elements.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
    
    for (int elem : elements) {
        maxHeap.insert(elem);
    }
    
    maxHeap.printHeap();
    std::cout << "Max element: " << maxHeap.peek() << std::endl;
    
    // Extract elements
    std::cout << "\nExtracting elements:" << std::endl;
    while (!maxHeap.isEmpty()) {
        std::cout << "Extracted: " << maxHeap.extractMax() << std::endl;
    }
    
    // Build heap from array
    std::vector<int> arr = {1, 3, 6, 5, 2, 4};
    std::cout << "\nBuilding heap from array: [";
    for (int i = 0; i < arr.size(); i++) {
        std::cout << arr[i];
        if (i < arr.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
    
    maxHeap.buildHeap(arr);
    maxHeap.printHeap();
    
    return 0;
}
```

---

## ==Min heap==

- Implements a priority queue using a min-heap
- Supports inserting elements (enqueue) with priority
- Supports extracting the minimum element (dequeue)

- Supports peeking at the minimum element
- Maintains the heap property on insert and remove
- Supports getting the current size

#### Code Implementation

|Name|Created|Tags|
|---|---|---|
|[[Python PQ Min Heap]]|August 12, 2025 6:50 AM||
|[[C PQ Min Heap]]|August 12, 2025 6:50 AM||
|[[C++ PQ Min Heap]]|August 12, 2025 6:50 AM||

  
  

---

# ==Heapify==

---

## ⚙️ ==What is Heapify?==

**Heapify** is the process of converting a binary tree (usually represented as an array) into a **heap** data structure, typically a **max-heap** or a **min-heap**. A heap is a complete binary tree where every parent node follows a specific order with respect to its children:

- **Max-Heap**: Parent node is greater than or equal to its children.
- **Min-Heap**: Parent node is less than or equal to its children.

Heapify helps maintain this heap property after insertions or deletions.

# 🎯 Why Heapify?

- To **build a heap** efficiently from an unordered array.
- To **restore the heap property** after removing the root (for example, during heap sort or priority queue operations).

  

# 🔍 How Heapify Works

Starting from a node that may violate the heap property, compare the node with its children. If the node doesn’t satisfy the heap condition:

- Swap it with the appropriate child (largest for max-heap, smallest for min-heap).
- Recursively heapify the affected subtree.

This process is often called **“sift down”** or **“bubble down”**.

# ⏱️ Time Complexity

- Heapify a single node takes **O(log n)** time, where n is the number of nodes in the heap.
- Building a heap from an array of size n (by calling heapify on all non-leaf nodes) takes **O(n)** time.

# 💻 Code Examples

#### Max Heapify

|Name|Created|Tags|
|---|---|---|
|[[Python PQ Max Heap]]|August 12, 2025 6:56 AM||
|[[C PQ Max Heap]]|August 12, 2025 6:56 AM||
|[[C++ PQ Max Heap]]|August 12, 2025 6:56 AM||

  
  

---

### **Python – Min Heapify**

```Python
def heapify(arr, n, i):
    smallest = i
    left = 2 * i + 1
    right = 2 * i + 2

    if left < n and arr[left] < arr[smallest]:
        smallest = left

    if right < n and arr[right] < arr[smallest]:
        smallest = right

    if smallest != i:
        arr[i], arr[smallest] = arr[smallest], arr[i]
        heapify(arr, n, smallest)

def build_min_heap(arr):
    n = len(arr)
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, n, i)

# Example usage
arr = [3, 5, 1, 10, 2, 7]
build_min_heap(arr)
print("Min Heap:", arr)

```

### **C# – Min Heapify**

```C#
using System;

class Program
{
    static void Heapify(int[] arr, int n, int i)
    {
        int smallest = i;
        int left = 2 * i + 1;
        int right = 2 * i + 2;

        if (left < n && arr[left] < arr[smallest])
            smallest = left;

        if (right < n && arr[right] < arr[smallest])
            smallest = right;

        if (smallest != i)
        {
            (arr[i], arr[smallest]) = (arr[smallest], arr[i]);
            Heapify(arr, n, smallest);
        }
    }

    static void BuildMinHeap(int[] arr)
    {
        int n = arr.Length;
        for (int i = n / 2 - 1; i >= 0; i--)
            Heapify(arr, n, i);
    }

    static void Main()
    {
        int[] arr = { 3, 5, 1, 10, 2, 7 };
        BuildMinHeap(arr);
        Console.WriteLine("Min Heap: " + string.Join(", ", arr));
    }
}

```

### **C++ – Min Heapify**

```C++
\#include <iostream>
\#include <vector>
using namespace std;

void heapify(vector<int>& arr, int n, int i) {
    int smallest = i;
    int left = 2 * i + 1;
    int right = 2 * i + 2;

    if (left < n && arr[left] < arr[smallest])
        smallest = left;

    if (right < n && arr[right] < arr[smallest])
        smallest = right;

    if (smallest != i) {
        swap(arr[i], arr[smallest]);
        heapify(arr, n, smallest);
    }
}

void buildMinHeap(vector<int>& arr) {
    int n = arr.size();
    for (int i = n / 2 - 1; i >= 0; i--)
        heapify(arr, n, i);
}

int main() {
    vector<int> arr = {3, 5, 1, 10, 2, 7};
    buildMinHeap(arr);

    cout << "Min Heap: ";
    for (int val : arr) cout << val << " ";
    cout << endl;

    return 0;
}
```

# 📌 Summary Table

|Term|Description|Time Complexity|
|---|---|---|
|**Heapify(node)** 🔄|Restore heap property starting from node i|O(log n)|
|**Build Heap** 🏗️|Call heapify on all non-leaf nodes|O(n)|

# 🌍 Real-World Example

Heaps and heapify are used in:

- **Heap Sort** to sort arrays efficiently.
- **Priority Queues** where the highest (or lowest) priority element must be accessed quickly.
- **Scheduling algorithms** that prioritize tasks.

---