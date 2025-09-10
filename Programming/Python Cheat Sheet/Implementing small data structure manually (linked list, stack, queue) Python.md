---
Created: 2025-08-21T19:29
tags:
  - Extra
---
## ✅ **1. Singly Linked List**

A **Linked List** is a sequence of nodes, each holding:

- `data` → value
- `next` → reference to next node

---

### 🏗 **Node Class**

```Python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None
```

---

### 🏗 **Linked List Class**

```Python
class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if not self.head:
            self.head = new_node
            return
        curr = self.head
        while curr.next:
            curr = curr.next
        curr.next = new_node

    def display(self):
        curr = self.head
        while curr:
            print(curr.data, end=" -> ")
            curr = curr.next
        print("None")
```

Usage:

```Python
ll = LinkedList()
ll.append(10)
ll.append(20)
ll.append(30)
ll.display()  # 10 -> 20 -> 30 -> None
```

---

✅ **Pros & Cons**

✔ Dynamic size

✔ Easy insert/delete at head

❌ Slower random access (`O(n)`)

---

## ✅ **2. Stack (LIFO)**

**Stack** → Last-In-First-Out

---

### 🏗 **Stack Implementation**

```Python
class Stack:
    def __init__(self):
        self.items = []

    def push(self, item):
        self.items.append(item)

    def pop(self):
        return self.items.pop() if not self.is_empty() else None

    def peek(self):
        return self.items[-1] if not self.is_empty() else None

    def is_empty(self):
        return len(self.items) == 0
```

Usage:

```Python
s = Stack()
s.push(1)
s.push(2)
print(s.peek())  # 2
print(s.pop())   # 2
print(s.pop())   # 1
```

✅ **Time complexity:** `O(1)` for push/pop

---

## ✅ **3. Queue (FIFO)**

**Queue** → First-In-First-Out

---

### 🏗 **Queue Implementation**

```Python
class Queue:
    def __init__(self):
        self.items = []

    def enqueue(self, item):
        self.items.append(item)

    def dequeue(self):
        return self.items.pop(0) if not self.is_empty() else None

    def is_empty(self):
        return len(self.items) == 0
```

Usage:

```Python
q = Queue()
q.enqueue("A")
q.enqueue("B")
print(q.dequeue())  # A
print(q.dequeue())  # B
```

⚠️ `pop(0)` is `O(n)`. For better performance, use `collections.deque`.

---

## 📌 **Summary Table**

|Structure|Access Order|Implementation|Pros|Cons|
|---|---|---|---|---|
|Linked List|Sequential|Node objects|Dynamic size, easy insert|Slow access|
|Stack|LIFO|List `.append()`/`.pop()`|Fast push/pop|No random access|
|Queue|FIFO|List or deque|Simple|`pop(0)` is slow with list|

---

## 🌍 **Real-World Example: Undo Feature with Stack**

```Python
class UndoManager:
    def __init__(self):
        self.history = Stack()

    def do(self, action):
        print("Doing:", action)
        self.history.push(action)

    def undo(self):
        last = self.history.pop()
        if last:
            print("Undoing:", last)
        else:
            print("Nothing to undo!")

undo = UndoManager()
undo.do("Type Hello")
undo.do("Delete line")
undo.undo()  # Undoing Delete line
undo.undo()  # Undoing Type Hello
undo.undo()  # Nothing to undo!
```

👉 **Why?**

- Stack perfectly models **undo/redo** operations.

---

✅ **TL;DR:**

- **Linked List** → good for dynamic insertion/deletion
- **Stack** → LIFO (undo, backtracking)
- **Queue** → FIFO (task scheduling, buffering)