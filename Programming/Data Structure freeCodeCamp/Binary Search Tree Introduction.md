---
Created: 2025-08-09T19:48
tags:
  - William-Fiset
---
# ==Discussion & Examples==

---

  

## 🌳 ==**What is a Tree in Data Structures?**==

A **Tree** is a **hierarchical data structure** that consists of **nodes** connected by **edges**, resembling an inverted tree in nature 🌲 (root at the top, leaves at the bottom).

It is **non-linear**, meaning data is not stored sequentially but in a parent–child relationship.

### 📌 **Key Features of a Tree**

- **Root** → The topmost node of the tree.
- **Parent Node** → A node that has one or more children.
- **Child Node** → A node that descends from another node.
- **Leaf Node** → A node with no children.
- **Edge** → The connection between two nodes.
- **Height of Tree** → The longest path from the root to any leaf.
- **Depth of Node** → Distance from the root to that node.

### 📍 **Example**

```Plain
        A  ← Root
       / \
      B   C
     / \    \
    D   E    F
```

- **Root**: `A`
- **Parent**: `A` (parent of B & C), `B` (parent of D & E), `C` (parent of F)
- **Children**: `B, C` are children of `A`
- **Leaf Nodes**: `D, E, F`
- **Height**: 2 (A → B → D)

### ⚡ **Why Use Trees?**

- To represent **hierarchical data** (file systems, organization charts).
- For **efficient searching & sorting** (Binary Search Tree, AVL Tree).
- To store data in a **structured, non-linear way**.

### 📦 **Where Trees Are Used**

- **Databases** (B-trees, B+ trees for indexing)
- **File Systems** (folders & subfolders)
- **XML/HTML parsing**
- **AI** (decision trees, game trees)
- **Networking** (routing tables)
- **Compilers** (syntax trees)

### 📊 **Tree Complexity Overview**

|Operation|Balanced Tree|Unbalanced Tree|
|---|---|---|
|Search|O(log n)|O(n)|
|Insert|O(log n)|O(n)|
|Delete|O(log n)|O(n)|

---

  

## 🌳 ==What is a Binary Tree (BT)?==

A **Binary Tree** is a hierarchical data structure in which:

- Each node has **at most two children** — called the **left child** and the **right child**.
- The tree starts with a **root node** at the top.
- Each child is itself the root of a subtree.

## 🎯 Key Properties

- **Nodes:** Each element in the tree.
- **Root:** The top node with no parent.
- **Parent & Child:** Nodes are connected in parent-child relationships.
- **Leaf Nodes:** Nodes with **no children**.
- **Height:** The longest path from the root to a leaf.
- **Depth:** Distance of a node from the root.

## 🔍 Why use Binary Trees?

- Efficient for searching, sorting, and hierarchical data representation.
- Basis for other trees like **Binary Search Trees (BST)**, **Heaps**, **Expression Trees**, etc.

## 🌿 Example Structure

```Plain
       1          <-- root
      / \
     2   3       <-- children of 1
    / \
   4   5         <-- children of 2
```

## Summary Table 📌

|Term|Meaning|
|---|---|
|Binary Tree|Tree where each node has ≤ 2 children|
|Root|Topmost node|
|Leaf|Node with no children|
|Height|Max distance from root to leaf|
|Depth|Distance from root to a node|

---

  

## 🌳 ==What is a Binary Search Tree (BST)?==

A **Binary Search Tree (BST)** is a **special kind of binary tree** with the following properties:

- Each node has **at most two children** (left and right).
- The **left subtree** of a node contains only nodes with values **less than** the node’s value.
- The **right subtree** contains only nodes with values **greater than** the node’s value.
- Both left and right subtrees are also BSTs (recursive property).

## 🎯 Why use a BST?

- Allows **fast searching, insertion, and deletion** of values.
- Average time complexity of these operations is **O(log n)** if the tree is balanced.
- Used in databases, dictionaries, and many algorithms needing sorted data.

## 🔍 How BST works

- To **search** for a value, start at the root:
    - If the value equals the current node, you’re done.
    - If smaller, go to the left child.
    - If larger, go to the right child.
- Repeat until you find the value or reach a leaf.

## 🌿 Example BST

```Plain
        8
       / \
      3   10
     / \    \
    1   6    14
       / \   /
      4   7 13
```

## Summary Table 📌

|Property|Description|
|---|---|
|Binary Tree|Each node has ≤ 2 children|
|BST Property|Left child < parent < right child|
|Search Time (avg)|O(log n)|
|Search Time (worst)|O(n) (unbalanced tree)|

---

## 📚 ==BST Terminology==

|Term|Description|Emoji|
|---|---|---|
|**Node**|A basic unit containing a value and links to children|🟢|
|**Root**|The topmost node of the tree with no parent|🌳|
|**Leaf**|A node with **no children** (end node)|🍂|
|**Parent**|A node that has one or more child nodes|👪|
|**Child**|A node directly connected below another node (parent)|👶|
|**Subtree**|A tree formed by a node and all its descendants|🌿|
|**Height**|Length of the longest path from a node down to a leaf|📏|

|Term|Description|Emoji|
|---|---|---|
|**Depth**|Number of edges from the root to a node|📐|
|**Balanced BST**|A BST where the height difference between left and right subtrees is minimal|⚖️|
|**Traversal**|The process of visiting all nodes in some order (inorder, preorder, postorder)|🚶‍♂️|
|**Inorder Traversal**|Visit left subtree → node → right subtree (sorted order in BST)|↩️➡️|
|**Preorder Traversal**|Visit node → left subtree → right subtree|▶️|
|**Postorder Traversal**|Visit left subtree → right subtree → node|🔄|

---

  

## 🌍 ==Where are Binary Trees (BT) Used?==

### 1. **Hierarchical Data Representation** 📂

- Organizing file systems and folder structures
- Representing organizational charts

### 2. **Expression Trees** 🧮

- Representing arithmetic expressions where internal nodes are operators and leaves are operands
- Used in compilers and calculators for parsing and evaluation

### 3. **Binary Search Trees (BST)** 🔍

- Efficient searching, insertion, and deletion of data

### 4. **Heaps** 🏗️

- Implementing priority queues
- Scheduling algorithms (like CPU task scheduling)

### 5. **Decision Trees** 🤖

- Machine learning models that use binary trees for classification and regression

### 6. **Routing Tables and Network Algorithms** 📡

- Efficient data routing and network packet processing

### 7. **Data Compression** 🗜️

- Huffman coding tree for lossless compression algorithms

## Summary Table 📌

|Use Case|Description|
|---|---|
|File Systems|Organize files and directories|
|Expression Evaluation|Arithmetic parsing and calculation|
|Data Searching|BST for fast search|
|Priority Scheduling|Heaps for managing tasks|
|Machine Learning|Decision trees for predictions|
|Networking|Routing and packet processing|
|Compression|Huffman trees for encoding|

---

  

## 🌍 ==Where are Binary Search Trees (BST) Used?==

### 1. **Efficient Searching & Sorting** 🔎

- Quickly find, insert, or delete data in **O(log n)** time on average.
- Used in databases, file systems, and indexes.

### 2. **Symbol Tables & Dictionaries** 📚

- Implement key-value stores where keys need to be kept sorted and searchable.

### 3. **Autocomplete & Spell Check** 💬

- Store dictionary words to efficiently retrieve matches or suggestions.

### 4. **Priority Queues & Event Simulation** ⏳

- Manage elements with priorities, though heaps are often preferred.

### 5. **In-Memory Database Indexes** 💾

- Organize data for quick retrieval without disk I/O.

### 6. **Computational Geometry** 📐

- Range searching, nearest neighbor search, and other geometric queries.

### 7. **Networking & Routing** 🌐

- Used in IP routing tables for prefix matching (with some BST variants).

## Summary Table 📌

|Use Case|Description|
|---|---|
|Searching & Sorting|Fast lookup and updates|
|Symbol Tables|Store sorted key-value pairs|
|Autocomplete Systems|Efficient prefix matching|
|Databases|Indexing and query optimization|
|Computational Geometry|Range queries and spatial data|
|Networking|Efficient routing decisions|

---

  

## ⏱️ ==Binary Tree Complexity Analysis==

### 1. **Traversal (Inorder, Preorder, Postorder)** 🚶‍♂️

- Visits **every node exactly once**.
- Time Complexity: **O(n)**, where n = number of nodes.
- Space Complexity:
    - Recursive call stack can go as deep as the height of the tree.
    - Worst-case (skewed tree): **O(n)**
    - Average case (balanced tree): **O(log n)**

### 2. **Search Operation** 🔍

- No specific ordering in a **general** binary tree, so you may need to check all nodes.
- Time Complexity: **O(n)** in worst and average cases.

### 3. **Insertion and Deletion** ➕

- For a **general** binary tree, these operations don’t have a standard efficient approach like BSTs.
- Usually require traversing to find the insertion point or node to delete.
- Time Complexity: **O(n)** in worst case.

### 4. **Height Calculation** 📏

- Height is found by traversing the tree.
- Time Complexity: **O(n)** because you need to visit every node.

## Summary Table 📌

|Operation|Time Complexity|Space Complexity|Notes|
|---|---|---|---|
|Traversal|O(n)|O(h) (h = tree height)|Recursive stack space varies|
|Search|O(n)|O(h)|No ordering; must check all nodes|
|Insertion|O(n)|O(h)|No fixed position in general BT|
|Deletion|O(n)|O(h)|Requires node search + restructure|
|Height|O(n)|O(h)|Traversal to find max depth|

---

  

## ⏱️ ==BST Complexity Analysis==

### 1. **Search** 🔍

- Average Case: **O(log n)** — Because each comparison cuts the search space roughly in half.
- Worst Case: **O(n)** — When the tree is **unbalanced** and resembles a linked list (all nodes in a single chain).

### 2. **Insertion** ➕

- Average Case: **O(log n)** — Inserting into a balanced BST.
- Worst Case: **O(n)** — If the tree is skewed (like a linked list).

### 3. **Deletion** ❌

- Average Case: **O(log n)** — Similar reasoning as insertion and search.
- Worst Case: **O(n)** — If tree is skewed.

### 4. **Traversal (Inorder, Preorder, Postorder)** 🚶‍♂️

- Visits every node exactly once.
- Time Complexity: **O(n)**
- Space Complexity:
    - Call stack up to height of tree: **O(h)**
    - Worst case skewed tree: **O(n)**
    - Balanced tree: **O(log n)**

### 5. **Height of BST** 📏

- Average height: **O(log n)**
- Worst case height: **O(n)** (unbalanced tree)

## Summary Table 📌

|Operation|Average Time Complexity|Worst Time Complexity|Notes|
|---|---|---|---|
|Search|O(log n)|O(n)|Balanced vs skewed|
|Insertion|O(log n)|O(n)|Worst case when tree is skewed|
|Deletion|O(log n)|O(n)|Removing node may require re-linking|
|Traversal|O(n)|O(n)|Visits all nodes|
|Height|O(log n)|O(n)|Affects search, insertion|

---

# ==Implementation Details==

---

  

## ➕ ==How to Insert a Node into a BST==

### Step 1: Start at the Root 🔍

- Compare the value to insert with the current node’s value.

### Step 2: Decide Direction ➡️⬅️

- If the value is **less than** the current node, go to the **left child**.
- If the value is **greater than** the current node, go to the **right child**.

### Step 3: Repeat Until Leaf 🏁

- Keep moving left or right until you reach a spot where the child is **null** (no node).

### Step 4: Insert Node 🌱

- Insert the new node at the null spot found.

## 🌿 Example

Insert **5** into this BST:

```Plain
     8
    / \
   3   10
  / \
 1   6
```

- 5 < 8 → go left to 3
- 5 > 3 → go right to 6
- 5 < 6 → go left → left child is null → insert here

Result:

```Plain
     8
    / \
   3   10
  / \
 1   6
     /
    5
```

## 💻 Code Example (Python)

```Python
class Node:
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None

def insert(root, val):
    if root is None:
        return Node(val)
    if val < root.val:
        root.left = insert(root.left, val)
    else:
        root.right = insert(root.right, val)
    return root
```

# Summary 📌

|Step|Description|
|---|---|
|Compare with node|Move left if smaller, right if bigger|
|Find null spot|Traverse until leaf/null|
|Insert new node|Place node in the null child position|

---

  

## ❌ ==How to Remove a Node from a BST==

Removing a node depends on **how many children** it has:

### 1. **Node with No Children (Leaf Node)** 🍂

- Just remove the node by setting its parent’s pointer to `null`.

### 2. **Node with One Child** 🌿

- Replace the node with its **single child**.

### 3. **Node with Two Children** 🌳

- Find the node’s **inorder successor** (smallest node in the right subtree) or **inorder predecessor** (largest node in the left subtree).
- Replace the node’s value with the successor/predecessor’s value.
- Recursively delete the successor/predecessor node (which will be in case 1 or 2).

## 🌿 Visual Example

Delete **3** from:

```Plain
      8
     / \
    3   10
   / \
  1   6
```

- Node 3 has two children.
- Find its inorder successor: **6** (smallest in right subtree).
- Replace 3 with 6.
- Delete node 6 (which is a leaf).

Result:

```Plain
      8
     / \
    6   10
   /
  1
```

## 💻 Code Example (Python)

```Python
def find_min(node):
    while node.left:
        node = node.left
    return node

def delete_node(root, val):
    if root is None:
        return root

    if val < root.val:
        root.left = delete_node(root.left, val)
    elif val > root.val:
        root.right = delete_node(root.right, val)
    else:
        # Node found
        if root.left is None:
            return root.right
        elif root.right is None:
            return root.left

        # Node with two children
        temp = find_min(root.right)      # Inorder successor
        root.val = temp.val
        root.right = delete_node(root.right, temp.val)

    return root
```

## Summary 📌

|Case|Action|
|---|---|
|No children|Remove node|
|One child|Replace node with child|
|Two children|Replace with inorder successor/predecessor and delete that node|

---

# ==Binary Tree Traversals==

---

  

## ==🌳 Binary Tree Traversals==

Traversals mean **visiting all nodes** in a tree in some order. The main types are:

- **Preorder** (Node → Left → Right)
- **Inorder** (Left → Node → Right)
- **Postorder** (Left → Right → Node)

## ▶️ Preorder Traversal

**Order:**

1. Visit the **current node** first.
2. Traverse the **left subtree** recursively.
3. Traverse the **right subtree** recursively.

## 🔍 Why Preorder?

- Useful for copying the tree.
- Used in prefix expression evaluation.
- Helpful when you want to visit the root node before its children.

## 🌿 Example

Given the tree:

```Plain
      1
     / \
    2   3
   / \
  4   5
```

**Preorder traversal:**

Visit nodes in order: 1 → 2 → 4 → 5 → 3

## 💻 Code Example (Python)

```Python
def preorder(node):
    if node:
        print(node.val, end=' ')
        preorder(node.left)
        preorder(node.right)
```

## Summary 📌

|Step|Action|
|---|---|
|Visit Node|Process current node|
|Traverse Left Subtree|Recursively preorder traverse left|
|Traverse Right Subtree|Recursively preorder traverse right|

---

  

## 🔄 ==Inorder Traversal==

**Order:**

1. Traverse the **left subtree** recursively.
2. Visit the **current node**.
3. Traverse the **right subtree** recursively.

## 🎯 Why Inorder?

- For **Binary Search Trees (BSTs)**, inorder traversal visits nodes in **sorted (ascending) order**.
- Useful for tasks that require sorted data output.

## 🌿 Example

Given the tree:

```Plain
      1
     / \
    2   3
   / \
  4   5
```

**Inorder traversal:**

Visit nodes in order: 4 → 2 → 5 → 1 → 3

## 💻 Code Example (Python)

```Python
def inorder(node):
    if node:
        inorder(node.left)
        print(node.val, end=' ')
        inorder(node.right)
```

## Summary 📌

|Step|Action|
|---|---|
|Traverse Left Subtree|Recursively inorder traverse left|
|Visit Node|Process current node|
|Traverse Right Subtree|Recursively inorder traverse right|

---

  

## 🔄 ==Postorder Traversal==

**Order:**

1. Traverse the **left subtree** recursively.
2. Traverse the **right subtree** recursively.
3. Visit the **current node** last.

## 🎯 Why Postorder?

- Useful for **deleting trees** (children before parent).
- Used in **expression tree evaluation** (postfix notation).
- When you want to process child nodes before the parent.

## 🌿 Example

Given the tree:

```Plain
      1
     / \
    2   3
   / \
  4   5
```

**Postorder traversal:**

Visit nodes in order: 4 → 5 → 2 → 3 → 1

## 💻 Code Example (Python)

```Python
def postorder(node):
    if node:
        postorder(node.left)
        postorder(node.right)
        print(node.val, end=' ')
```

## Summary 📌

|Step|Action|
|---|---|
|Traverse Left Subtree|Recursively postorder traverse left|
|Traverse Right Subtree|Recursively postorder traverse right|
|Visit Node|Process current node|

---

  

## 📏 ==Level Order Traversal==

**Order:**

- Visit nodes **level by level**, from **top to bottom**, and **left to right** within each level.

## 🎯 Why Level Order?

- Useful to explore nodes in **breadth-first** manner.
- Used in shortest path problems, serialization/deserialization of trees, and in algorithms like BFS.

## 🌿 Example

Given the tree:

```Plain
      1
     / \
    2   3
   / \
  4   5
```

**Level order traversal:**

Visit nodes in order: 1 → 2 → 3 → 4 → 5

## 💻 Code Example (Python)

```Python
from collections import deque

def level_order(root):
    if not root:
        return

    queue = deque([root])

    while queue:
        node = queue.popleft()
        print(node.val, end=' ')

        if node.left:
            queue.append(node.left)
        if node.right:
            queue.append(node.right)
```

## Summary 📌

|Step|Action|
|---|---|
|Use a Queue|Store nodes level by level|
|Visit Current Node|Process node at front of the queue|
|Enqueue Children|Add left and right children to the queue|

---

# ==Code Implementation==

---

- Node structure
- BST insertion
- BST search

- Inorder traversal (to print sorted order)
- A simple example showing usage

#### Code Implementation

|Name|Created|Tags|
|---|---|---|
|[[Python BST]]|August 12, 2025 6:40 AM||
|[[C BST]]|August 12, 2025 6:40 AM||
|[[C++ BST]]|August 12, 2025 6:40 AM||

  
  

- A `Node` class to represent each node
- A `BinaryTree` class to build the tree

- Basic traversal methods: Preorder, Inorder, Postorder
- A simple example to build and traverse the tree

---