---
Created: 2025-08-05T08:24
tags:
  - William-Fiset
---
# ==Discussion about Stacks==

---

## ==🧠 What is a Stack?==

A **stack** is a **linear data structure** that follows the **LIFO (Last-In, First-Out)** principle.

This means the **last** element added is the **first** one to be removed.

### 📌 Key Concepts

- Think of a **stack of plates**: you add and remove from the top only.
- Two main operations:
    - `push`: Add an element to the top
    - `pop`: Remove the top element
- Additional operations:
    
    - `peek` or `top`: View the top element without removing it
    - `isEmpty`: Check if the stack is empty
    
      
    

### 🧮 Common Uses

- Function call stack in programming languages
- Undo/Redo operations
- Expression evaluation (e.g., postfix, infix)
- Balanced parentheses checking
- Depth-First Search (DFS)

## 🕓 Time & Space Complexity

|Operation|Time Complexity|Space Complexity|
|---|---|---|
|`push`|O(1)|O(n)|
|`pop`|O(1)|O(n)|
|`peek`|O(1)|O(n)|

## ✅ Python Implementation (Using List)

  

```Python
class Stack:
    def __init__(self):
        self.stack = []

    def push(self, data):
        self.stack.append(data)

    def pop(self):
        if not self.is_empty():
            return self.stack.pop()

    def peek(self):
        if not self.is_empty():
            return self.stack[-1]

    def is_empty(self):
        return len(self.stack) == 0
```

## ✅ C# Implementation

```C#
using System;
using System.Collections.Generic;

class StackExample {
    Stack<int> stack = new Stack<int>();

    public void Push(int data) {
        stack.Push(data);
    }

    public int? Pop() {
        return stack.Count > 0 ? stack.Pop() : (int?)null;
    }

    public int? Peek() {
        return stack.Count > 0 ? stack.Peek() : (int?)null;
    }

    public bool IsEmpty() {
        return stack.Count == 0;
    }
}
```

> Note: C# provides System.Collections.Generic.Stack<T> out of the box.

  

## ✅ C++ Implementation (with manual memory logic)

```C++
\#include <iostream>
using namespace std;

class Node {
public:
    int data;
    Node* next;

    Node(int value) {
        data = value;
        next = nullptr;
    }
};

class Stack {
private:
    Node* top;

public:
    Stack() {
        top = nullptr;
    }

    void push(int value) {
        Node* newNode = new Node(value);
        newNode->next = top;
        top = newNode;
    }

    void pop() {
        if (top != nullptr) {
            Node* temp = top;
            top = top->next;
            delete temp;  // 🔥 manual memory cleanup
        }
    }

    int peek() {
        if (top != nullptr)
            return top->data;
        throw runtime_error("Stack is empty");
    }

    bool isEmpty() {
        return top == nullptr;
    }

    ~Stack() {
        while (!isEmpty()) pop(); // clean up memory
    }
};
```

## 📝 Summary

|Feature|Python|C#|C++|
|---|---|---|---|
|Built-in stack|`list` or `Stack`|`Stack<T>`|Needs manual implementation|
|Memory mgmt|Automatic|Automatic|Manual (`new` / `delete`)|
|Use case|Quick prototyping|Production-grade|Systems-level understanding|

---

  

## ==🧠 When and Where Is a Stack Used?==

A **stack** is used when **data must be stored and retrieved in reverse order**—that is, **Last In, First Out (LIFO)**. It is ideal when the **most recently added item** needs to be accessed or removed **first**.

### ✅ Real-World and Programming Use Cases

|**Use Case**|**Description**|
|---|---|
|**1. Function Call Stack**|Stores function calls; the most recent call is completed before earlier ones.|
|**2. Undo/Redo in Applications**|Each action is pushed onto a stack; popping undoes it in reverse order.|
|**3. Expression Evaluation**|Used in evaluating or converting infix/postfix/prefix expressions.|
|**4. Backtracking Algorithms**|DFS (Depth-First Search), maze solvers use stacks to remember previous steps.|
|**5. Syntax Parsing / Compilers**|Helps parse nested expressions like `{[()]}` or match HTML/XML tags.|
|**6. Browser History**|Pages are stacked; going "Back" pops the last visited page.|
|**7. Reversing Data**|Reversing strings, arrays, or data structures can be done using a stack.|

### 🧪 Example Scenarios (Python, C#, C++)

### 1. **Function Call Stack Example**

```Python
def A():
    B()

def B():
    C()

def C():
    print("Inside C")

A()
```

- Function `A` calls `B`, which calls `C`.
- Call Stack: `A → B → C` → returns in reverse: `C → B → A`.

> This exact behavior is implemented by the runtime call stack in C#, Python, and C++.

### 2. **Backtracking (e.g., DFS Traversal)**

- In **graph/tree traversal**, stack helps explore one path fully before backtracking.

**C++ DFS Example (Using Stack):**

```C++
\#include <iostream>
\#include <stack>
\#include <vector>

void DFS(int start, std::vector<std::vector<int>>& graph) {
    std::vector<bool> visited(graph.size(), false);
    std::stack<int> s;

    s.push(start);

    while (!s.empty()) {
        int node = s.top(); s.pop();
        if (!visited[node]) {
            visited[node] = true;
            std::cout << node << " ";
            for (int neighbor : graph[node]) {
                if (!visited[neighbor])
                    s.push(neighbor);
            }
        }
    }
}
```

### 🎯 When to Use a Stack?

Use a stack when:

- You need **LIFO ordering**.
- You’re dealing with **nested scopes** or **recursive behavior**.
- The **latest operation or state must be reversed** first.
- You want to **track state changes** in order (like undo/redo).

  

---

  

## ==📊 Stack Complexity Analysis==

### 🧠 Key Operations and Their Complexity

|**Operation**|**Time Complexity**|**Space Complexity**|**Explanation**|
|---|---|---|---|
|`push`|O(1)|O(n)|Add to top; constant time|
|`pop`|O(1)|O(n)|Remove top element|
|`peek/top`|O(1)|O(n)|Look at top element|
|`isEmpty`|O(1)|O(1)|Check if stack has elements|

> All operations are constant time because stacks operate only at the top.

## 🧠 Space Complexity Details

- A stack storing **n elements** will use:
    - **O(n)** space for the elements.
    - In **Python/C#**, memory management is automatic.
    - In **C++**, you manually `new`/`delete` nodes or use STL which handles it.

### ✅ Static Array-Based Stack vs Linked List-Based Stack

|**Implementation**|**Push/Pop**|**Memory Use**|**Flexibility**|
|---|---|---|---|
|Array (fixed size)|O(1)|Fixed O(n) space|Size must be pre-defined|
|Dynamic Array (list)|Amortized O(1)|Dynamically grows|Efficient, common in Python|
|Linked List|O(1)|Extra pointer per node|True dynamic size|

## 🔁 Comparison in Languages

|**Language**|**Common Stack Type**|**Time Complexity**|
|---|---|---|
|**Python**|`list` or `collections.deque`|O(1) for append/pop|
|**C#**|`Stack<T>` from `System.Collections.Generic`|O(1) push/pop|
|**C++**|`std::stack<T>` (underlying container usually `deque`)|O(1)|

## ✅ Code Summary of O(1) Behavior

### Python

```Python
s = []
s.append(10)  # O(1)
s.pop()       # O(1)
```

### C#

```C#
Stack<int> s = new Stack<int>();
s.Push(10);  // O(1)
s.Pop();     // O(1)
```

### C++

```C++
\#include <stack>
std::stack<int> s;
s.push(10);  // O(1)
s.pop();     // O(1)
```

## 🧠 Summary Table

|**Operation**|**Best**|**Average**|**Worst**|
|---|---|---|---|
|`push`|O(1)|O(1)|O(1)|
|`pop`|O(1)|O(1)|O(1)|
|`peek`|O(1)|O(1)|O(1)|

---

  

## ==📚 Real-World Example:== ==**Balanced Parentheses Checker**==

### ✅ Problem:

Check if the parentheses in a given string are **balanced**.

Examples:

- `"()"`, `"(())"`, `"(()())"` → ✅ Balanced
- `"(()"`, `"())("`, `"(()))"` → ❌ Not Balanced

## 🧠 Why Use a Stack?

We need to keep track of **open brackets** and remove them when we see the corresponding **closing bracket**.

A stack is ideal because we always need to match the **most recent open bracket** — which is **LIFO** behavior.

  

## ✅ Python Implementation

```Python
def is_balanced(expression):
    stack = []
    for char in expression:
        if char == '(':
            stack.append(char)
        elif char == ')':
            if not stack:
                return False
            stack.pop()
    return len(stack) == 0

# Test
print(is_balanced("(())"))      # True
print(is_balanced("(()"))       # False
print(is_balanced("())(()"))    # False
```

  

## ✅ C# Implementation

```C#
using System;
using System.Collections.Generic;

class StackExample {
    public static bool IsBalanced(string expression) {
        Stack<char> stack = new Stack<char>();

        foreach (char ch in expression) {
            if (ch == '(')
                stack.Push(ch);
            else if (ch == ')') {
                if (stack.Count == 0)
                    return false;
                stack.Pop();
            }
        }

        return stack.Count == 0;
    }

    // Test
    static void Main() {
        Console.WriteLine(IsBalanced("(())"));     // True
        Console.WriteLine(IsBalanced("(()"));      // False
        Console.WriteLine(IsBalanced("())(()"));   // False
    }
}
```

## ✅ C++ Implementation

```C++
\#include <iostream>
\#include <stack>
\#include <string>

bool isBalanced(const std::string& expr) {
    std::stack<char> s;

    for (char ch : expr) {
        if (ch == '(') {
            s.push(ch);
        } else if (ch == ')') {
            if (s.empty()) return false;
            s.pop();
        }
    }

    return s.empty();
}

int main() {
    std::cout << std::boolalpha;
    std::cout << isBalanced("(())") << std::endl;     // true
    std::cout << isBalanced("(()") << std::endl;      // false
    std::cout << isBalanced("())(()") << std::endl;   // false
}
```

## 🧠 Summary

This example shows:

- **How stacks manage nested structures**
- Their usefulness in **backtracking and matching pairs**
- A classic real-world application: used in **compilers, syntax checkers, and code editors**

---

  

# ==Implementation Details==

---

## 📌 ==What is "Push" in Stack?==

**Push** means adding an element to the **top** of the stack.

  

- Follows **LIFO (Last In, First Out)** order.
- The newly pushed element is now the **top** of the stack.

## 📊 Complexity

|Operation|Time Complexity|Space Complexity|
|---|---|---|
|`push`|O(1)|O(1) (plus element size)|

## ✅ Python Example

```Python
stack = []

# Push elements
stack.append(10)
stack.append(20)
stack.append(30)

print(stack)  # Output: [10, 20, 30]
```

- `append()` adds to the end of the list (top of stack).

  

## ✅ C# Example

```C#
using System;
using System.Collections.Generic;

class Program {
    static void Main() {
        Stack<int> stack = new Stack<int>();

        stack.Push(10);
        stack.Push(20);
        stack.Push(30);

        foreach (int item in stack)
            Console.WriteLine(item);  // Output: 30 20 10
    }
}
```

- `Push()` adds to the top of the `Stack<T>`.

## ✅ C++ Example

```C++
\#include <iostream>
\#include <stack>

int main() {
    std::stack<int> stack;

    stack.push(10);
    stack.push(20);
    stack.push(30);

    while (!stack.empty()) {
        std::cout << stack.top() << " ";  // Output: 30 20 10
        stack.pop();
    }

    return 0;
}
```

- `push()` adds to top.
- `top()` accesses the top.
- `pop()` removes the top.

  

## 🧠 Key Notes

- Stack grows upward: new items go on **top**.
- After `push`, the most recently added element becomes `top`.

---

  

## 📌 ==What is "Pop" in a Stack?==

**Pop** means **removing** the **top element** of the stack.

- It’s the opposite of `push`.
- Follows **LIFO (Last In, First Out)** — the most recently added element is removed first.
- You can usually `pop` only if the stack is **not empty**.

## 📊 Complexity

|Operation|Time Complexity|Space Complexity|
|---|---|---|
|`pop`|O(1)|O(1)|

## ✅ Python Example

```Python
stack = [10, 20, 30]

# Pop the top element (30)
top = stack.pop()

print("Popped:", top)   # Output: 30
print("Stack now:", stack)  # Output: [10, 20]
```

- `pop()` removes and returns the last element.

## ✅ C# Example

```C#
using System;
using System.Collections.Generic;

class Program {
    static void Main() {
        Stack<int> stack = new Stack<int>();
        stack.Push(10);
        stack.Push(20);
        stack.Push(30);

        int top = stack.Pop();  // Removes 30
        Console.WriteLine("Popped: " + top);       // Output: 30
        Console.WriteLine("Top now: " + stack.Peek());  // Output: 20
    }
}
```

- `Pop()` removes and returns the top.
- `Peek()` looks at the current top without removing.

## ✅ C++ Example

```C++
\#include <iostream>
\#include <stack>

int main() {
    std::stack<int> stack;
    stack.push(10);
    stack.push(20);
    stack.push(30);

    int top = stack.top();  // Access top (30)
    stack.pop();            // Remove top

    std::cout << "Popped: " << top << std::endl;  // Output: 30
    std::cout << "Top now: " << stack.top() << std::endl;  // Output: 20
}
```

- `top()` gets the top element.
- `pop()` removes the top element but **does not return it** — you must call `top()` first.

  

## ⚠️ Common Gotchas

|Mistake|Why it's wrong|
|---|---|
|Popping from empty stack|Causes errors (underflow)|
|Expecting `pop()` in C++ to return a value|It doesn't — use `top()` first|

## 🧠 Summary

|Action|Description|
|---|---|
|`pop()`|Removes the top element (O(1))|
|`top()`/`peek()`|Accesses top without removing|

---

  

# ==Code Implementation==

---

- Implements a stack data structure (LIFO)
- Supports push (add element)
- Supports pop (remove and return top element)

- Supports peek (view top element without removing)
- Supports checking if the stack is empty
- Supports getting current size

### Python — Stack.py

```Python
class Stack:
    def __init__(self):
        self.items = []
    
    def push(self, item):
        """Add an item to the top of the stack"""
        self.items.append(item)
    
    def pop(self):
        """Remove and return the top item from the stack"""
        if self.is_empty():
            raise IndexError("pop from empty stack")
        return self.items.pop()
    
    def peek(self):
        """Return the top item without removing it"""
        if self.is_empty():
            raise IndexError("peek from empty stack")
        return self.items[-1]
    
    def is_empty(self):
        """Check if the stack is empty"""
        return len(self.items) == 0
    
    def size(self):
        """Return the number of items in the stack"""
        return len(self.items)
    
    def __str__(self):
        return f"Stack({self.items})"

# Example usage
if __name__ == "__main__":
    stack = Stack()
    stack.push(1)
    stack.push(2)
    stack.push(3)
    print(f"Stack: {stack}")
    print(f"Top element: {stack.peek()}")
    print(f"Popped: {stack.pop()}")
    print(f"Size: {stack.size()}")
```

### C# — Stack.cs

```C#
using System;
using System.Collections.Generic;

public class Stack<T>
{
    private List<T> items;
    
    public Stack()
    {
        items = new List<T>();
    }
    
    public void Push(T item)
    {
        items.Add(item);
    }
    
    public T Pop()
    {
        if (IsEmpty())
            throw new InvalidOperationException("Stack is empty");
            
        T item = items[items.Count - 1];
        items.RemoveAt(items.Count - 1);
        return item;
    }
    
    public T Peek()
    {
        if (IsEmpty())
            throw new InvalidOperationException("Stack is empty");
            
        return items[items.Count - 1];
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
        return $"Stack([{string.Join(", ", items)}])";
    }
}

// Example usage
class Program
{
    static void Main()
    {
        Stack<int> stack = new Stack<int>();
        stack.Push(1);
        stack.Push(2);
        stack.Push(3);
        
        Console.WriteLine($"Stack: {stack}");
        Console.WriteLine($"Top element: {stack.Peek()}");
        Console.WriteLine($"Popped: {stack.Pop()}");
        Console.WriteLine($"Size: {stack.Size()}");
    }
}
```

### C++ — Stack.cpp

```C++
\#include <iostream>
\#include <vector>
\#include <stdexcept>

template<typename T>
class Stack {
private:
    std::vector<T> items;

public:
    // Add an item to the top of the stack
    void push(const T& item) {
        items.push_back(item);
    }
    
    // Remove and return the top item from the stack
    T pop() {
        if (isEmpty()) {
            throw std::runtime_error("pop from empty stack");
        }
        T item = items.back();
        items.pop_back();
        return item;
    }
    
    // Return the top item without removing it
    T peek() const {
        if (isEmpty()) {
            throw std::runtime_error("peek from empty stack");
        }
        return items.back();
    }
    
    // Check if the stack is empty
    bool isEmpty() const {
        return items.empty();
    }
    
    // Return the number of items in the stack
    size_t size() const {
        return items.size();
    }
    
    // Print the stack contents
    void print() const {
        std::cout << "Stack([";
        for (size_t i = 0; i < items.size(); ++i) {
            std::cout << items[i];
            if (i < items.size() - 1) std::cout << ", ";
        }
        std::cout << "])" << std::endl;
    }
};

// Example usage
int main() {
    Stack<int> stack;
    stack.push(1);
    stack.push(2);
    stack.push(3);
    
    std::cout << "Stack: ";
    stack.print();
    std::cout << "Top element: " << stack.peek() << std::endl;
    std::cout << "Popped: " << stack.pop() << std::endl;
    std::cout << "Size: " << stack.size() << std::endl;
    
    return 0;
}
```

## 🧠 Key Takeaways

- Manual stack implementations help you understand underlying memory control.
- C++ requires explicit memory deallocation (`delete[]`).
- In C#, arrays are fixed in size unless using `List<T>`.
- Python lists grow dynamically, but we're limiting them here like arrays.

---