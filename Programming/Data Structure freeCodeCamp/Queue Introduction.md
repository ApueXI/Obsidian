---
Created: 2025-08-05T20:56
tags:
  - William-Fiset
---
# ==Discussion About Queue==

---

## ==📌 What is a Queue?==

A **Queue** is a **linear data structure** that follows the **FIFO (First-In, First-Out)** principle:

- The first element added is the first one removed.
- Think of a **real-life queue** (like a line at a ticket counter).

## 🧠 Characteristics

|Feature|Description|
|---|---|
|Order|FIFO – First In, First Out|
|Insertion|At the **rear** (enqueue)|
|Deletion|From the **front** (dequeue)|
|Usage|Scheduling, buffering, resource sharing|
|Variants|Circular Queue, Deque, Priority Queue|

## ✅ Operations

|Operation|Description|Time Complexity|
|---|---|---|
|`enqueue(x)`|Add item to the rear|O(1)|
|`dequeue()`|Remove item from the front|O(1)|
|`peek()`|View the front item without removing|O(1)|
|`is_empty()`|Check if the queue is empty|O(1)|

## 🔤 Python Example

```Python
from collections import deque

queue = deque()

queue.append(10)     # enqueue
queue.append(20)
print(queue.popleft())  # dequeue → 10
print(queue[0])         # peek → 20
```

  

## 💠 C# Example

```C#
using System;
using System.Collections.Generic;

class Program {
    static void Main() {
        Queue<int> queue = new Queue<int>();

        queue.Enqueue(10);
        queue.Enqueue(20);

        Console.WriteLine(queue.Dequeue()); // Output: 10
        Console.WriteLine(queue.Peek());    // Output: 20
    }
}
```

  

## 🧠 C++ Example

```C++
\#include <iostream>
\#include <queue>
using namespace std;

int main() {
    queue<int> q;

    q.push(10);  // enqueue
    q.push(20);

    cout << q.front() << endl; // peek → 10
    q.pop();                   // dequeue
    cout << q.front() << endl; // now front is 20

    return 0;
}
```

  

## 🧰 Where Are Queues Used?

- **CPU scheduling**
- **Printer queues**
- **IO buffers**
- **Task queues**
- **BFS (Breadth-First Search)** in graphs

---

  

## 📘 ==Queue Terminology==

|Term|Definition|
|---|---|
|**Queue**|A linear data structure that follows **FIFO (First In, First Out)** order.|
|**Enqueue**|The operation of **adding** an element to the **rear** (or back) of the queue.|
|**Dequeue**|The operation of **removing** an element from the **front** of the queue.|
|**Front**|The **first element** in the queue — this is the element to be dequeued next.|
|**Rear / Back**|The **last element** in the queue — this is where new elements are enqueued.|
|**Peek / Front()**|To look at the **front element** without removing it from the queue.|
|**Overflow**|Happens when the queue is **full** and you try to enqueue an element (in fixed-size queues).|
|**Underflow**|Happens when the queue is **empty** and you try to dequeue.|
|**Circular Queue**|A type of queue where the end connects back to the front to utilize space efficiently.|
|**Priority Queue**|A special type of queue where elements are dequeued based on priority, not order.|
|**Deque**|Double-Ended Queue: elements can be added/removed from both ends.|

## 🧠 Summary Table

|Action|Affects|Example in Python|C#|C++|
|---|---|---|---|---|
|Enqueue|Rear|`queue.append(x)`|`queue.Enqueue(x)`|`queue.push(x)`|
|Dequeue|Front|`queue.popleft()`|`queue.Dequeue()`|`queue.pop()`|
|Peek|Front|`queue[0]`|`queue.Peek()`|`queue.front()`|

## 📝 Example (Illustration)

After enqueueing 10, 20, 30:

```Plain
Front → [10, 20, 30] ← Rear
```

After one dequeue:

```Plain
Front → [20, 30] ← Rear
```

  

---

  

## 📌 ==When and Where Is a Queue Used?==

A **Queue** is used when:

- **Order matters** — elements must be processed in the same order they arrive.
- You need to **buffer tasks or data** before processing.
- The system must ensure **fairness** or **scheduling**.

## 🧰 Real-World Analogies

|Example|Description|
|---|---|
|**Waiting in line**|First person to line up gets served first.|
|**Printer jobs**|Print requests are queued; the first one gets printed first.|
|**Call center**|Customers are queued and served in order of arrival.|

## 💻 Common Use Cases in Programming

|Use Case|How Queues Are Used|
|---|---|
|**CPU scheduling**|Processes wait in a queue to be executed by the CPU.|
|**I/O buffering**|Keyboard/mouse/network inputs are queued before reading.|
|**Breadth-First Search (BFS)**|In graph/tree traversal, nodes are explored in order.|
|**Task/Job scheduling**|Jobs are added to a queue and executed one-by-one.|
|**Message Queues (MQ)**|Background tasks or services communicate via queues.|
|**Level-order traversal (trees)**|Queue is used to visit nodes level by level.|

## 📍 Situations Where FIFO Is Needed

|Situation|Queue Role|
|---|---|
|**Round-robin algorithms**|Each task takes turns in a cyclic order.|
|**Data stream processing**|Incoming data is processed in order.|
|**Multithreading/task queues**|Worker threads dequeue and process tasks.|

## 🧠 Summary

A **Queue is best used when**:

- You need **order-preserving** data handling.
- Tasks should be processed in **first-come, first-served** manner.
- You want to manage **resources or execution flows** efficiently.

  

---

  

## 📊 ==Queue Complexity Analysis==

Queues can be implemented using:

- Arrays (Static Queue)
- Linked Lists (Dynamic Queue)
- Built-in libraries (e.g., `deque`, `Queue<T>`, `std::queue`)

### ✅ Basic Operations and Their Time Complexity

|Operation|Description|Array-based|Linked List-based|Language Library|
|---|---|---|---|---|
|`enqueue(x)`|Add element at the rear|O(1)*|O(1)|O(1)|
|`dequeue()`|Remove element from the front|O(n)*|O(1)|O(1)|
|`peek()`|Access the front element|O(1)|O(1)|O(1)|
|`isEmpty()`|Check if queue is empty|O(1)|O(1)|O(1)|

> 🔹 *In a regular array-based queue without circular handling, dequeue is O(n) because it requires shifting elements.

> 🔹 Circular arrays solve this by using front and rear pointers to make dequeue O(1).

### ✅ Space Complexity

|Implementation|Space Complexity|
|---|---|
|Array (fixed)|O(n)|
|Linked List|O(n)|
|Dynamic container|O(n)|

> Where n is the number of elements in the queue.

  

### 🧠 Summary

- **Array-based queues** are easy to implement but may suffer from O(n) dequeue unless made circular.
- **Linked list-based queues** offer consistent O(1) enqueue/dequeue by keeping head and tail pointers.
- **Library queues** (e.g., `deque`, `Queue<T>`, `std::queue`) are optimized and recommended for practical use.

### 📌 Example: C++ Linked List Queue

```C++
struct Node {
    int data;
    Node* next;
    Node(int val) : data(val), next(nullptr) {}
};

class Queue {
    Node* front;
    Node* rear;
public:
    Queue() : front(nullptr), rear(nullptr) {}

    void enqueue(int x) {
        Node* node = new Node(x);
        if (!rear) front = rear = node;
        else {
            rear->next = node;
            rear = node;
        }
    }

    void dequeue() {
        if (!front) return;
        Node* temp = front;
        front = front->next;
        if (!front) rear = nullptr;
        delete temp;
    }

    int peek() { return front ? front->data : -1; }
    bool isEmpty() { return front == nullptr; }
};
```

---

## 📘 ==What Is BFS?==

**Breadth-First Search (BFS)** is a graph traversal algorithm that visits nodes **level by level**, starting from a source node.

🔁 It uses a **queue** to keep track of the next nodes to visit in **FIFO** order.

## 📊 Complexity

|Measure|Value|
|---|---|
|Time|O(V + E) _(V: vertices, E: edges)_|
|Space|O(V) _(for queue + visited set)_|

## 🧠 Steps of BFS

1. Start at a source node.
2. Mark it as visited and enqueue it.
3. While queue is not empty:
    - Dequeue node `n`
    - Visit all **unvisited neighbors** of `n`
    - Mark each as visited and enqueue them

## ✅ Python BFS Using Queue

```Python
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])

    while queue:
        node = queue.popleft()
        if node not in visited:
            print(node, end=' ')
            visited.add(node)
            queue.extend(graph[node])

# Sample graph (adjacency list)
graph = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': ['F'],
    'F': []
}

bfs(graph, 'A')
# Output: A B C D E F
```

  

## ✅ C# BFS Using Queue

```C#
using System;
using System.Collections.Generic;

class Program {
    static void BFS(Dictionary<string, List<string>> graph, string start) {
        var visited = new HashSet<string>();
        var queue = new Queue<string>();
        queue.Enqueue(start);

        while (queue.Count > 0) {
            string node = queue.Dequeue();
            if (!visited.Contains(node)) {
                Console.Write(node + " ");
                visited.Add(node);
                foreach (var neighbor in graph[node])
                    queue.Enqueue(neighbor);
            }
        }
    }

    static void Main() {
        var graph = new Dictionary<string, List<string>> {
            {"A", new List<string>{"B", "C"}},
            {"B", new List<string>{"D", "E"}},
            {"C", new List<string>{"F"}},
            {"D", new List<string>()},
            {"E", new List<string>{"F"}},
            {"F", new List<string>()}
        };

        BFS(graph, "A");
        // Output: A B C D E F
    }
}
```

  

## ✅ C++ BFS Using Queue

```C++
\#include <iostream>
\#include <queue>
\#include <unordered_map>
\#include <vector>
\#include <unordered_set>

void bfs(std::unordered_map<char, std::vector<char>>& graph, char start) {
    std::unordered_set<char> visited;
    std::queue<char> q;

    q.push(start);

    while (!q.empty()) {
        char node = q.front(); q.pop();
        if (visited.count(node) == 0) {
            std::cout << node << " ";
            visited.insert(node);
            for (char neighbor : graph[node]) {
                q.push(neighbor);
            }
        }
    }
}

int main() {
    std::unordered_map<char, std::vector<char>> graph = {
        {'A', {'B', 'C'}},
        {'B', {'D', 'E'}},
        {'C', {'F'}},
        {'D', {}},
        {'E', {'F'}},
        {'F', {}}
    };

    bfs(graph, 'A');  // Output: A B C D E F
}
```

  

## 📌 Summary

- **Queue is essential** in BFS to track traversal order.
- Nodes are explored **level by level**, not depth-first.
- Great for **finding shortest paths** in unweighted graphs.

---

# ==Implementation Details==

---

  

## 🧠 ==What Is Enqueue?==

**Enqueue** means **adding an element to the rear (end)** of the queue.

It follows **FIFO** (First In, First Out) ordering.

## 🔧 General Steps

1. Check if the queue has space (in static implementations).
2. Add the element to the **rear**.
3. Update the `rear` pointer/index if needed.

## ✅ Python (using `deque`)

```Python
from collections import deque

queue = deque()

# Enqueue elements
queue.append('A')
queue.append('B')
queue.append('C')

print(queue)  # Output: deque(['A', 'B', 'C'])
```

📌 Python’s `deque.append()` adds to the **right (rear)** of the queue.

  

## ✅ C# (using `Queue<T>`)

```C#
using System;
using System.Collections.Generic;

class Program {
    static void Main() {
        Queue<string> queue = new Queue<string>();

        // Enqueue elements
        queue.Enqueue("A");
        queue.Enqueue("B");
        queue.Enqueue("C");

        foreach (var item in queue)
            Console.Write(item + " ");  // Output: A B C
    }
}
```

📌 `Queue<T>.Enqueue()` adds to the **end** of the queue.

  

## ✅ C++ (using `std::queue`)

```C++
\#include <iostream>
\#include <queue>

int main() {
    std::queue<char> queue;

    // Enqueue elements
    queue.push('A');
    queue.push('B');
    queue.push('C');

    while (!queue.empty()) {
        std::cout << queue.front() << " ";
        queue.pop();
    }
    // Output: A B C
}
```

📌 `queue.push()` enqueues elements to the **back** of the queue.

  

## ⏱️ Time Complexity

|Operation|Complexity|
|---|---|
|Enqueue|O(1)|

(Assuming dynamic or linked-list based queues. Static arrays may overflow.)

## 📌 Summary

- Enqueue means **pushing data to the back** of the queue.
- All standard libraries use `.enqueue()` or `.push()` methods.
- Complexity is **O(1)** for dynamic queues.

---

  

## 🧠 ==What Is Dequeue?==

**Dequeue** means **removing an element from the front** of the queue.

It follows the **FIFO (First In, First Out)** rule — the earliest added element is the first to be removed.

## ✅ Python (using `deque`)

```Python
from collections import deque

queue = deque(['A', 'B', 'C'])

# Dequeue element
front = queue.popleft()
print("Removed:", front)       # Output: Removed: A
print("Queue now:", queue)     # Output: deque(['B', 'C'])
```

📌 `popleft()` removes the **leftmost (front)** item in O(1) time.

  

## ✅ C# (using `Queue<T>`)

```C#
using System;
using System.Collections.Generic;

class Program {
    static void Main() {
        Queue<string> queue = new Queue<string>();
        queue.Enqueue("A");
        queue.Enqueue("B");
        queue.Enqueue("C");

        // Dequeue element
        string front = queue.Dequeue();
        Console.WriteLine("Removed: " + front);       // Output: Removed: A

        foreach (var item in queue)
            Console.Write(item + " ");                // Output: B C
    }
}
```

📌 `Dequeue()` removes and returns the **front** element.

## ✅ C++ (using `std::queue`)

```C++
\#include <iostream>
\#include <queue>

int main() {
    std::queue<char> queue;
    queue.push('A');
    queue.push('B');
    queue.push('C');

    // Dequeue element
    char front = queue.front();
    queue.pop();
    std::cout << "Removed: " << front << "\n";      // Output: Removed: A

    while (!queue.empty()) {
        std::cout << queue.front() << " ";
        queue.pop();
    }
    // Output: B C
}
```

📌 `front()` gets the front item; `pop()` removes it.

  

## ⏱️ Time Complexity

|Operation|Complexity|
|---|---|
|Dequeue|O(1)|

> For both dynamic array-based and linked list-based queues.

## ⚠️ Gotchas

- In static array implementations (non-circular), dequeue might be O(n) due to shifting.
- In languages like C++ (manual memory), be cautious with pointers if implementing yourself.

## 📌 Summary

- **Dequeue = remove from front**
- In all three languages:
    - Get the front element
    - Remove it using `.pop()` / `.Dequeue()` / `.popleft()`
- Time complexity is **O(1)**

  

---

# ==Code Implementation==

---

- Implements a queue data structure (FIFO)
- Supports enqueue (add element to back)
- Supports dequeue (remove and return front element)

- Supports peek/front (view front element without removing)
- Supports checking if queue is empty
- Supports getting current size

### Python — Queue.py

```Python
from collections import deque

class Queue:
    def __init__(self):
        self.items = deque()
    
    def enqueue(self, item):
        """Add an item to the rear of the queue"""
        self.items.append(item)
    
    def dequeue(self):
        """Remove and return the front item from the queue"""
        if self.is_empty():
            raise IndexError("dequeue from empty queue")
        return self.items.popleft()
    
    def front(self):
        """Return the front item without removing it"""
        if self.is_empty():
            raise IndexError("front from empty queue")
        return self.items[0]
    
    def rear(self):
        """Return the rear item without removing it"""
        if self.is_empty():
            raise IndexError("rear from empty queue")
        return self.items[-1]
    
    def is_empty(self):
        """Check if the queue is empty"""
        return len(self.items) == 0
    
    def size(self):
        """Return the number of items in the queue"""
        return len(self.items)
    
    def __str__(self):
        return f"Queue({list(self.items)})"

# Example usage
if __name__ == "__main__":
    queue = Queue()
    queue.enqueue(1)
    queue.enqueue(2)
    queue.enqueue(3)
    print(f"Queue: {queue}")
    print(f"Front element: {queue.front()}")
    print(f"Rear element: {queue.rear()}")
    print(f"Dequeued: {queue.dequeue()}")
    print(f"Size: {queue.size()}")
    print(f"Queue after dequeue: {queue}")
```

  

### C# — Queue.cs

```C#
using System;
using System.Collections.Generic;
using System.Linq;

public class Queue<T>
{
    private LinkedList<T> items;
    
    public Queue()
    {
        items = new LinkedList<T>();
    }
    
    public void Enqueue(T item)
    {
        items.AddLast(item);
    }
    
    public T Dequeue()
    {
        if (IsEmpty())
            throw new InvalidOperationException("Queue is empty");
            
        T item = items.First.Value;
        items.RemoveFirst();
        return item;
    }
    
    public T Front()
    {
        if (IsEmpty())
            throw new InvalidOperationException("Queue is empty");
            
        return items.First.Value;
    }
    
    public T Rear()
    {
        if (IsEmpty())
            throw new InvalidOperationException("Queue is empty");
            
        return items.Last.Value;
    }
    
    public bool IsEmpty()
    {
        return items.Count == 0;
    }
    
    public int Size()
    {
        return items.Count;
    }
    
    public override string ToString()
    {
        return $"Queue([{string.Join(", ", items)}])";
    }
}

// Example usage
class Program
{
    static void Main()
    {
        Queue<int> queue = new Queue<int>();
        queue.Enqueue(1);
        queue.Enqueue(2);
        queue.Enqueue(3);
        
        Console.WriteLine($"Queue: {queue}");
        Console.WriteLine($"Front element: {queue.Front()}");
        Console.WriteLine($"Rear element: {queue.Rear()}");
        Console.WriteLine($"Dequeued: {queue.Dequeue()}");
        Console.WriteLine($"Size: {queue.Size()}");
        Console.WriteLine($"Queue after dequeue: {queue}");
    }
}
```

### C++ — Queue.cpp

```C++
\#include <iostream>
\#include <deque>
\#include <stdexcept>

template<typename T>
class Queue {
private:
    std::deque<T> items;

public:
    // Add an item to the rear of the queue
    void enqueue(const T& item) {
        items.push_back(item);
    }
    
    // Remove and return the front item from the queue
    T dequeue() {
        if (isEmpty()) {
            throw std::runtime_error("dequeue from empty queue");
        }
        T item = items.front();
        items.pop_front();
        return item;
    }
    
    // Return the front item without removing it
    T front() const {
        if (isEmpty()) {
            throw std::runtime_error("front from empty queue");
        }
        return items.front();
    }
    
    // Return the rear item without removing it
    T rear() const {
        if (isEmpty()) {
            throw std::runtime_error("rear from empty queue");
        }
        return items.back();
    }
    
    // Check if the queue is empty
    bool isEmpty() const {
        return items.empty();
    }
    
    // Return the number of items in the queue
    size_t size() const {
        return items.size();
    }
    
    // Print the queue contents
    void print() const {
        std::cout << "Queue([";
        for (size_t i = 0; i < items.size(); ++i) {
            std::cout << items[i];
            if (i < items.size() - 1) std::cout << ", ";
        }
        std::cout << "])" << std::endl;
    }
};

// Example usage
int main() {
    Queue<int> queue;
    queue.enqueue(1);
    queue.enqueue(2);
    queue.enqueue(3);
    
    std::cout << "Queue: ";
    queue.print();
    std::cout << "Front element: " << queue.front() << std::endl;
    std::cout << "Rear element: " << queue.rear() << std::endl;
    std::cout << "Dequeued: " << queue.dequeue() << std::endl;
    std::cout << "Size: " << queue.size() << std::endl;
    std::cout << "Queue after dequeue: ";
    queue.print();
    
    return 0;
}
```

## 🧠 Summary

|Feature|Python|C#|C++|
|---|---|---|---|
|Enqueue|`append()`|Add node to rear|Add node to rear|
|Dequeue|`pop(0)`|Remove front node|Delete front node|
|Manual Mem|Automatic|Automatic (GC)|Manual (`new` + `delete`)|

---