---
Created: 2025-08-07T20:10
tags:
  - Array-&-Collections
---
## ✅ Concept

- **Unordered collection** of **unique values**.
- No duplicates allowed.
- Fast lookup, insertion, and deletion.

## 🧠 Syntax

```C#
HashSet<int> numbers = new HashSet<int> { 1, 2, 3 };
numbers.Add(4);
```

## 📦 Common Methods

|Method|Description|
|---|---|
|`.Add(item)`|Adds if not already present|
|`.Remove(item)`|Removes item|
|`.Contains(item)`|Checks if item exists|
|`.Clear()`|Removes all items|
|`.Count`|Gets item count|
|`.UnionWith(set)`|Combines two sets|
|`.IntersectWith(set)`|Keeps only common items|
|`.ExceptWith(set)`|Removes items found in another set|

## ⚠️ Gotchas

- No index-based access.
- Unordered — don’t rely on order of elements.

## 🔥 Use Case

- Filtering duplicates: `new HashSet<T>(myList);`
- Fast membership checks.

---

# 🧰 2. `Queue<T>` Cheat Sheet

## ✅ Concept

- **FIFO** (First-In-First-Out) data structure.
- Use when order matters, like processing tasks.

## 🧠 Syntax

```C#
Queue<string> tasks = new Queue<string>();
tasks.Enqueue("Task1");
string next = tasks.Dequeue();
```

## 📦 Common Methods

|Method|Description|
|---|---|
|`.Enqueue(item)`|Adds to the end|
|`.Dequeue()`|Removes and returns first item|
|`.Peek()`|Returns first item without removing|
|`.Contains()`|Checks if item exists|
|`.Clear()`|Removes all items|
|`.Count`|Number of items|

## ⚠️ Gotchas

- Calling `.Dequeue()` or `.Peek()` on empty queue = **exception**.
- No random access.

## 🔥 Use Case

- Task scheduling
- Order processing (e.g., print queue)

---

# 🧱 3. `Stack<T>` Cheat Sheet

## ✅ Concept

- **LIFO** (Last-In-First-Out) data structure.
- Last added = first removed.

## 🧠 Syntax

```C#
Stack<int> stack = new Stack<int>();
stack.Push(1);
int top = stack.Pop();
```

## 📦 Common Methods

|Method|Description|
|---|---|
|`.Push(item)`|Adds item to the top|
|`.Pop()`|Removes and returns top item|
|`.Peek()`|Views top item without removing|
|`.Contains()`|Checks if item exists|
|`.Clear()`|Clears all items|
|`.Count`|Number of items|

## ⚠️ Gotchas

- `.Pop()` and `.Peek()` throw exceptions on empty stack.

## 🔥 Use Case

- Undo functionality
- Backtracking (e.g., DFS algorithms)

---

# 🔄 Comparison Table

|Feature|`HashSet<T>`|`Queue<T>`|`Stack<T>`|
|---|---|---|---|
|Order Maintained?|❌ No|✅ FIFO|✅ LIFO|
|Allows Duplicates?|❌ No|✅ Yes|✅ Yes|
|Indexed Access|❌ No|❌ No|❌ No|
|Fast Lookup|✅ Yes|⚠️ Not ideal|⚠️ Not ideal|
|Use Case|Unique items|Processing in order|Reverse-order tasks|

---

# 🧪 Real-world Use Cases

### ✅ `HashSet<T>`

```C#
HashSet<string> emails = new HashSet<string>();
emails.Add("a@email.com");
emails.Add("a@email.com"); // Won’t add again
```

### ✅ `Queue<T>`

```C#
Queue<string> helpDesk = new Queue<string>();
helpDesk.Enqueue("Customer1");
helpDesk.Enqueue("Customer2");
Console.WriteLine(helpDesk.Dequeue()); // Customer1
```

### ✅ `Stack<T>`

```C#
Stack<string> actions = new Stack<string>();
actions.Push("Draw Line");
actions.Push("Erase Line");
Console.WriteLine(actions.Pop()); // Erase Line
```