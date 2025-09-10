---
Created: 2025-08-04T10:22
tags:
  - William-Fiset
---
# ==Discussion About Singly & Doubly Linked List==

---

## ==What is a Linked List?==

A **Linked List** is a **linear data structure** where elements (called **nodes**) are stored in **separate memory locations** and are connected using **pointers** or **links**.

Each node contains two parts:

1. **Data** – The actual value.
2. **Next** – A reference (or pointer) to the **next node** in the sequence.

Unlike arrays, linked lists do **not store elements in contiguous memory**, and their size can **grow or shrink dynamically**.

### ✅ Types of Linked Lists

|Type|Description|
|---|---|
|**Singly Linked List**|Each node points to the next node only.|
|**Doubly Linked List**|Each node points to both the next and previous nodes.|
|**Circular Linked List**|The last node points back to the first node.|

### 📌 Singly Linked List Example (Visual)

```Plain
[10 | • ] → [20 | • ] → [30 | NULL]
```

Each box is a node: `[data | pointer]`.

The last node’s pointer is `NULL` (no next node).

### 🧠 Why Use Linked Lists?

- **Dynamic size**: Easy to grow and shrink at runtime.
- **Efficient insertions/deletions**: Especially at the start or middle.
- **No wasted memory**: Unlike arrays, no need to pre-allocate space.

### ⚠️ When Not Ideal

- **Slow access by index**: Need to traverse from the head → O(n).
- **Extra memory**: Each node stores a pointer.
- **Cache-unfriendly**: Because nodes are not stored contiguously.

### ⏱️ Time Complexity (Singly Linked List)

|Operation|Time Complexity|
|---|---|
|Access|O(n)|
|Search|O(n)|
|Insert (head)|O(1)|
|Insert (middle/end)|O(n)|
|Delete (head)|O(1)|
|Delete (middle/end)|O(n)|

### 📝 Summary

- A linked list is a chain of nodes connected by pointers.
- Great for **flexible size** and **frequent insert/delete**.
- Not suitable for **random access** or **index-heavy operations**.

---

  

## ==Where Are Linked Lists Used?==

**Linked lists** are used in programming and system design where **dynamic memory management**, **frequent insertions/deletions**, and **non-contiguous storage** are needed.

They’re especially useful in **situations where arrays fall short**, such as:

- Unknown or changing data sizes
- Frequent additions/removals not just at the end

### ✅ Common Use Cases of Linked Lists

|Use Case|Description|
|---|---|
|**Dynamic Memory Allocation**|Used by operating systems and memory managers to track free/used memory.|
|**Implementing Stacks/Queues**|Linked lists make it easy to add/remove from head/tail.|
|**Undo/Redo Functionality**|Doubly linked lists help navigate backward and forward in history.|
|**Browser History**|Each page is a node; you can move forward or back (like doubly linked list).|
|**Music/Playlist Navigation**|Songs are nodes; you can go next/previous easily.|
|**Polynomial Arithmetic**|Each term (coefficient and exponent) is a node in a linked list.|
|**Graphs and Adjacency Lists**|Each vertex holds a linked list of its neighbors.|
|**Symbol Tables (Compilers)**|Used in scopes and parsing trees.|
|**Hash Table Buckets**|Handle collisions using separate chaining (linked lists in each bucket).|
|**Sparse Matrices**|Store only non-zero values as nodes to save space.|

### 🧠 Why Not Just Use Arrays?

|Need/Scenario|Why Linked List is Better|
|---|---|
|Unknown size in advance|Lists grow/shrink dynamically|
|Insert/delete in the middle|O(1) (with pointer), vs O(n) for arrays|
|No need for random access|Linked lists don’t need indexing|
|Memory fragmentation is a concern|Nodes can live in non-contiguous memory|

### 📝 Summary

Use **linked lists** when:

- You want a **flexible, dynamic-size** structure.
- You need **frequent inserts/deletes**.
- You don’t need fast **random access** by index.

---

  

## ==Linked List Terminology==

To work with linked lists effectively, it's important to understand the basic **terms and components** used to describe them.

  

### ✅ Key Terms in a Linked List

|Term|Description|
|---|---|
|**Node**|The basic unit of a linked list. Stores **data** and a **pointer/link** to the next node.|
|**Data**|The actual **value** stored in a node (e.g., number, string, object).|
|**Pointer / Link**|A reference to the **next** node (in singly linked lists) or both **next and previous** (in doubly linked lists).|
|**Head**|The **first node** in a linked list. All traversal starts from here.|
|**Tail**|The **last node**, usually has a pointer/link of `NULL` or points to `head` in circular lists.|
|**Next**|A reference to the **next node** (in singly or doubly linked lists).|
|**Previous**|A reference to the **previous node** (only in doubly linked lists).|
|**Null**|Indicates the **end** of the list (no next node).|
|**Linked List**|A sequence of nodes connected via pointers, forming a **chain**.|

  

### 📌 Visual Example (Singly Linked List):

```Plain
Head → [10 | • ] → [20 | • ] → [30 | NULL]
         data   next     data   next     data   next
```

- Each `[data | pointer]` is a **node**.
- The pointer in the last node is **NULL**, marking the end of the list.
- The first node is the **head**.

### 🧠 Extra Terms (Advanced)

|Term|Description|
|---|---|
|**Traversal**|Visiting each node in order (usually starting from head).|
|**Insertion**|Adding a new node at head, tail, or middle.|
|**Deletion**|Removing a node and updating adjacent pointers.|
|**Circular List**|A linked list where the last node points to the head (forms a loop).|
|**Doubly Linked List**|Each node points to both next and previous nodes.|

### 📝 Summary

- A **node** is the building block.
- **Head** starts the list; **tail** ends it.
- **Next** and **Previous** pointers connect the nodes.
- Understanding this vocabulary is essential for **building and modifying** linked lists.

---

  

## ==🔗 Singly Linked List vs Doubly Linked List==

|Feature|**Singly Linked List (SLL)**|**Doubly Linked List (DLL)**|
|---|---|---|
|**Node Structure**|`[data|next]`|
|**Direction**|One-way (forward only)|Two-way (forward and backward)|
|**Memory Usage**|Less (only one pointer per node)|More (stores two pointers per node)|
|**Insert at Head**|Easy, O(1)|Easy, O(1)|
|**Insert at Tail**|O(n) (need to traverse to end)|O(1) if tail is tracked|
|**Delete Node**|O(n), must track previous node|O(1) if node pointer is given|
|**Reverse Traversal**|Not possible|Possible|
|**Extra Memory Needed**|No extra memory for back links|Needs extra memory for `prev` pointers|
|**Implementation Simplicity**|Simple|Slightly complex (more pointer handling)|

### ✅ Singly Linked List – Pros & Cons

- ✅ Simpler and uses **less memory**.
- ❌ Can only move **forward**, so deleting a node or reverse traversal is **harder**.

### ✅ Doubly Linked List – Pros & Cons

- ✅ Supports **two-way traversal** (forward and backward).
- ✅ **Easy deletion** when you have a reference to any node.
- ❌ Takes **more memory** and has **more pointer management** (higher complexity).

### 📌 Visual Difference

### Singly Linked List:

```CSS
[10 | • ] → [20 | • ] → [30 | NULL]
```

### Doubly Linked List:

```CSS
NULL ← [10 | • | • ] ⇄ [20 | • | • ] ⇄ [30 | • | NULL]
```

### 📝 Summary

- Use **SLL** when you need **simplicity** and **forward-only** operations.
- Use **DLL** when you need **reverse traversal** or **frequent deletions** from both ends or middle.

---

# ==Implementation Details==

---

## ==🛠️ Inserting New Elements in a Singly Linked List==

To insert a new node, we create a new node with data and update the `next` pointers to link it into the list.

### ✅ 3 Common Insertion Methods

|Insertion Type|Description|Time Complexity|
|---|---|---|
|**At the Beginning**|Insert before the head|O(1)|
|**At the End**|Insert after the last node|O(n)|
|**In the Middle**|Insert after a specific node/index|O(n)|

### 📌 1. Insert at the Beginning (Head)

**Steps**:

1. Create a new node.
2. Set its `next` to the current `head`.
3. Update `head` to point to the new node.

**Code Example (Python)**:

```Python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

def insert_at_head(head, data):
    new_node = Node(data)
    new_node.next = head
    return new_node  # new head
```

### 📌 2. Insert at the End (Tail)

**Steps**:

1. Traverse to the last node.
2. Set its `next` to the new node.

**Code Example (Python)**:

```Python
def insert_at_tail(head, data):
    new_node = Node(data)
    if head is None:
        return new_node  # list was empty
    current = head
    while current.next:
        current = current.next
    current.next = new_node
    return head
```

### 📌 3. Insert After a Specific Node

**Steps**:

1. Find the node after which to insert.
2. Point the new node’s `next` to that node’s `next`.
3. Set that node’s `next` to the new node.

**Code Example (Python)**:

```Python
def insert_after_node(prev_node, data):
    if prev_node is None:
        print("Previous node cannot be None")
        return
    new_node = Node(data)
    new_node.next = prev_node.next
    prev_node.next = new_node
```

### 🧠 Important Notes

- Always check for `None` to avoid runtime errors.
- When inserting at **head**, the `head` must be updated and returned.
- For inserting **in the middle**, traversal is required, costing `O(n)` time.

### 📝 Summary Table

|Operation|Steps Involved|Time Complexity|
|---|---|---|
|Insert at Head|Create node → Point to old head → Update head|O(1)|
|Insert at Tail|Traverse to end → Append new node|O(n)|
|Insert in Middle|Traverse to position → Adjust pointers|O(n)|

  

---

  

## ==❌ Removing Elements in a Singly Linked List==

To remove a node, you need to:

1. **Find the node** (or its previous node),
2. **Change the** `**next**` **pointer** to skip the node,
3. **Free/delete** the node (in languages like C/C++).

### ✅ 3 Common Deletion Types

|Deletion Type|Description|Time Complexity|
|---|---|---|
|**Delete at Head**|Remove the first node|O(1)|
|**Delete at Tail**|Remove the last node|O(n)|
|**Delete by Value**|Remove node containing specific data|O(n)|

### 📌 1. Delete at the Beginning (Head)

**Steps**:

1. Point `head` to `head.next`.
2. Delete the old head.

```Python
def delete_head(head):
    if head is None:
        return None
    return head.next  # New head
```

### 📌 2. Delete at the End (Tail)

**Steps**:

1. Traverse to second-last node.
2. Set its `next` to `None`.

```Python
def delete_tail(head):
    if head is None or head.next is None:
        return None
    current = head
    while current.next.next:
        current = current.next
    current.next = None
    return head
```

### 📌 3. Delete by Value

**Steps**:

1. Traverse and track the **previous node**.
2. If value found, update `prev.next = current.next`.

```Python
def delete_by_value(head, key):
    if head is None:
        return None
    if head.data == key:
        return head.next  # deleted head
    prev = head
    current = head.next
    while current:
        if current.data == key:
            prev.next = current.next
            return head
        prev = current
        current = current.next
    return head  # value not found
```

### 🧠 Notes

- Always check if the list is empty (`head is None`).
- For **delete by value**, only the first match is removed.
- In **C/C++**, you must `free()` the deleted node.

### 📝 Summary Table

|Operation|Time Complexity|Notes|
|---|---|---|
|Delete at Head|O(1)|Simple, just move head pointer|
|Delete at Tail|O(n)|Need to find second-last node|
|Delete by Value|O(n)|Traverse and relink nodes|

  

---

  

# ==Complexity Analysis==

---

## ==🧮 Complexity Analysis – Linked List==

Linked lists have different time and space complexities for common operations depending on the type (Singly, Doubly, Circular).

Let’s focus on **Singly Linked Lists** here:

### ✅ Time Complexity (Singly Linked List)

|Operation|Best Case|Average Case|Worst Case|Notes|
|---|---|---|---|---|
|**Access by Index**|O(1)|O(n)|O(n)|Must traverse from head to index|
|**Search (by value)**|O(1)|O(n)|O(n)|Best case if value is in head|
|**Insert at Head**|O(1)|O(1)|O(1)|No traversal needed|
|**Insert at Tail**|O(n)|O(n)|O(n)|Must traverse to end unless tail is tracked|
|**Insert in Middle**|O(n)|O(n)|O(n)|Need to find position first|
|**Delete Head**|O(1)|O(1)|O(1)|Just update `head` pointer|
|**Delete Tail**|O(n)|O(n)|O(n)|Must find second last node|
|**Delete by Value**|O(1)|O(n)|O(n)|Best if head matches, worst if last node|

### ✅ Space Complexity

|Scenario|Space Complexity|
|---|---|
|**Storing n nodes**|O(n)|
|**With no extra storage**|O(1)|
|**With recursive operations**|O(n) call stack|

### 🧠 Comparisons with Arrays

|Operation|Array (Static)|Linked List|
|---|---|---|
|Random Access|O(1)|❌ Not supported|
|Insert/Delete at Start|O(n)|✅ O(1)|
|Insert/Delete at End|O(1) or O(n)|O(n)|
|Insert/Delete in Middle|O(n)|O(n)|
|Memory Allocation|Contiguous|Non-contiguous|

### 📝 Summary

- Use **linked lists** when you need **frequent insertion/deletion**.
- They trade **fast access (O(1))** for **flexibility and dynamic memory**.
- **Worst case** for most operations is **O(n)** due to linear traversal.

---

## ==📊 Complexity Analysis — Doubly Linked List==

|Operation|Time Complexity|Explanation|
|---|---|---|
|**Access by Index**|O(n)|Must traverse nodes sequentially, no random access|
|**Search by Value**|O(n)|Linear search through nodes|
|**Insert at Head**|O(1)|Directly update pointers without traversal|
|**Insert at Tail**|O(1) (if tail tracked) O(n) (otherwise)|If tail pointer maintained, insertion at tail is constant time; otherwise requires traversal|
|**Insert in Middle**|O(n)|Must traverse to position, then adjust pointers|
|**Delete at Head**|O(1)|Update head pointer and `prev` of next node|
|**Delete at Tail**|O(1) (if tail tracked) O(n) (otherwise)|Deletion at tail is constant time if tail pointer exists, else needs traversal|
|**Delete by Value**|O(n)|Linear traversal to find node, then pointer adjustment|
|**Traversal (forward or backward)**|O(n)|Visit each node once|

## 🧠 Space Complexity

- **O(n)** space for storing **n nodes**.
- Each node uses **extra space** for `prev` pointer besides `data` and `next`.
- So, space per node is slightly more than singly linked list.

## ⚖️ Summary

|Operation|Doubly Linked List|Singly Linked List|
|---|---|---|
|Access|O(n)|O(n)|
|Search|O(n)|O(n)|
|Insert at Head|O(1)|O(1)|
|Insert at Tail|O(1) if tail pointer used|O(n)|
|Delete at Head|O(1)|O(1)|
|Delete at Tail|O(1) if tail pointer used|O(n)|
|Delete by Value|O(n)|O(n)|
|Reverse Traversal|O(n)|Not possible without extra structure|

## ==⏱️ Time Complexity — Doubly Linked List==

|**Operation**|**Best Case**|**Average Case**|**Worst Case**|**Explanation**|
|---|---|---|---|---|
|**Access by Index**|O(1)|O(n)|O(n)|No random access; must traverse nodes|
|**Search (by value)**|O(1)|O(n)|O(n)|If found at head (best), else linear search|
|**Insert at Head**|O(1)|O(1)|O(1)|No traversal needed|
|**Insert at Tail**|O(1)*|O(n)|O(n)|O(1) if tail pointer is maintained|
|**Insert in Middle**|O(n)|O(n)|O(n)|Need to traverse to position first|
|**Delete at Head**|O(1)|O(1)|O(1)|Just update head and pointers|
|**Delete at Tail**|O(1)*|O(n)|O(n)|O(1) if tail is tracked|
|**Delete by Value**|O(1)|O(n)|O(n)|Best case if head matches|

## 🧠 Notes:

- If you **maintain a tail pointer**, both **insert/delete at tail become O(1)**.
- Traversing forward/backward takes **O(n)** either way.
- **No need to track previous node** during deletion like in singly linked list — it's already linked.
- Overhead: each node stores an **extra** `**prev**` **pointer** → slightly more **space usage**.

## 🧮 Space Complexity

|Scenario|Space Complexity|
|---|---|
|**Storing n elements**|O(n)|
|**Extra space per node**|O(1)|

## 📝 Summary Table

|Operation|Time Complexity|Description|
|---|---|---|
|Insert/Delete Head|O(1)|Instant update of head/prev|
|Insert/Delete Tail|O(1)*|Fast with tail pointer; O(n) without|
|Search by Value|O(n)|Linear search required|
|Traverse Forward/Backward|O(n)|Easy with both `next` and `prev` links|

---

  

# ==Code Implementation==

---

## ==🧾 Singly Linked List: Full Code Implementation (Python)==

```Python
# Node class
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

# Singly Linked List class
class SinglyLinkedList:
    def __init__(self):
        self.head = None

    # Insert at head
    def insert_at_head(self, data):
        new_node = Node(data)
        new_node.next = self.head
        self.head = new_node

    # Insert at end
    def insert_at_tail(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            return
        current = self.head
        while current.next:
            current = current.next
        current.next = new_node

    # Delete node by value
    def delete_by_value(self, key):
        if self.head is None:
            return
        if self.head.data == key:
            self.head = self.head.next
            return
        prev = self.head
        current = self.head.next
        while current:
            if current.data == key:
                prev.next = current.next
                return
            prev = current
            current = current.next

    # Display all elements
    def display(self):
        current = self.head
        while current:
            print(current.data, end=" → ")
            current = current.next
        print("None")

    # Search for a value
    def search(self, key):
        current = self.head
        while current:
            if current.data == key:
                return True
            current = current.next
        return False
```

---

## 🧪 Example Usage:

```Python
ll = SinglyLinkedList()
ll.insert_at_head(30)
ll.insert_at_tail(40)
ll.insert_at_head(20)
ll.insert_at_head(10)

ll.display()  # Output: 10 → 20 → 30 → 40 → None

ll.delete_by_value(20)
ll.display()  # Output: 10 → 30 → 40 → None

print("Found 30:", ll.search(30))  # Output: True
print("Found 50:", ll.search(50))  # Output: False
```

---

## 📌 Key Concepts Used:

- **Classes** for both Node and LinkedList.
- Operations: **insert, delete, search, and display**.
- Dynamic memory: no size limit, elements added as needed.

## ==🧾 Doubly Linked List: Full Code Implementation (Python)==

```Python
# Node class for Doubly Linked List
class Node:
    def __init__(self, data):
        self.data = data
        self.prev = None
        self.next = None

# Doubly Linked List class
class DoublyLinkedList:
    def __init__(self):
        self.head = None

    # Insert at the front
    def insert_at_head(self, data):
        new_node = Node(data)
        new_node.next = self.head
        if self.head:
            self.head.prev = new_node
        self.head = new_node

    # Insert at the end
    def insert_at_tail(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            return
        current = self.head
        while current.next:
            current = current.next
        current.next = new_node
        new_node.prev = current

    # Delete a node by value
    def delete_by_value(self, key):
        if self.head is None:
            return
        current = self.head

        # If head is to be deleted
        if current.data == key:
            self.head = current.next
            if self.head:
                self.head.prev = None
            return

        while current:
            if current.data == key:
                if current.prev:
                    current.prev.next = current.next
                if current.next:
                    current.next.prev = current.prev
                return
            current = current.next

    # Display the list forward
    def display_forward(self):
        current = self.head
        while current:
            print(current.data, end=" ⇄ ")
            current = current.next
        print("None")

    # Display the list backward
    def display_backward(self):
        current = self.head
        if not current:
            print("None")
            return
        while current.next:
            current = current.next
        while current:
            print(current.data, end=" ⇄ ")
            current = current.prev
        print("None")

    # Search for a value
    def search(self, key):
        current = self.head
        while current:
            if current.data == key:
                return True
            current = current.next
        return False
```

---

## 🧪 Example Usage:

```Python
dll = DoublyLinkedList()
dll.insert_at_head(20)
dll.insert_at_head(10)
dll.insert_at_tail(30)
dll.insert_at_tail(40)

dll.display_forward()   # Output: 10 ⇄ 20 ⇄ 30 ⇄ 40 ⇄ None
dll.display_backward()  # Output: 40 ⇄ 30 ⇄ 20 ⇄ 10 ⇄ None

dll.delete_by_value(20)
dll.display_forward()   # Output: 10 ⇄ 30 ⇄ 40 ⇄ None

print("Search 30:", dll.search(30))  # Output: True
print("Search 100:", dll.search(100))  # Output: False
```

---

## 🧠 Key Notes:

- Each `Node` has two pointers: `prev` and `next`.
- Can be traversed both **forward and backward**.
- Insertion and deletion is more flexible than singly linked list.
- Slightly more memory usage due to `prev` pointer.

---

# ==Another Code Implementation==

---

- Defines a singly linked list structure
- Supports adding elements to the end (append)
- Supports removing elements by value

- Supports searching for an element (returns True/False)
- Supports printing all elements
- Supports getting the size (count) of the list

#### Code Implementation

|Name|Created|Tags|
|---|---|---|
|[[Python Linked List]]|August 12, 2025 6:46 AM||
|[[C Linked List]]|August 12, 2025 6:46 AM||
|[[C++ Linked List]]|August 12, 2025 6:46 AM||

  
  

---