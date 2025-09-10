---
Created: 2025-08-16T09:53
tags:
  - BroCode
---
## ==What is a Tree==

A **Tree** is a **non-linear hierarchical data structure** that consists of **nodes** connected by **edges**. Unlike arrays or linked lists (which are linear), a tree organizes data in a **parent-child relationship**.

## 🔹 **Key Properties of a Tree**

1. **Root Node** → The topmost node (starting point).
2. **Child Node** → A node directly connected below another node.
3. **Parent Node** → A node directly above a child node.
4. **Leaf Node** → A node with **no children**.
5. **Edge** → A link connecting two nodes.
6. **Height of Tree** → Longest path from root to any leaf.
7. **Depth of Node** → Distance from the root to that node.

## 🔹 **Why Trees are Special**

- **No cycles** → Trees are **acyclic** graphs.
- For **N nodes**, a tree always has **N – 1 edges**.
- Used to represent hierarchical data.

## 🔹 **Types of Trees**

- **Binary Tree** → Each node has at most 2 children.
- **Binary Search Tree (BST)** → Left < Root < Right.
- **AVL Tree** → Self-balancing BST.
- **Heap** → Complete tree for priority queues.
- **Trie** → For storing strings/prefixes.

## 📊 **Summary**

- **Linear vs Non-linear:** Tree is **non-linear**.
- **Edges = Nodes – 1.**
- **Efficient for:** Searching, hierarchical data, expression parsing, etc.

## 🔹 **Example Structure**

```Plain
        A (Root)
       / \
      B   C
     / \   \
    D   E   F
```

- Root = A
- Parent of B = A
- Children of B = D, E
- Leaves = D, E, F

---

  

## ==Terminology==

Understanding trees requires knowing the common **terminologies** used to describe their structure.

## 🔹 **Basic Terms**

- **Node** → Fundamental unit of a tree (stores data).
- **Root** → The topmost node of the tree (starting point).
- **Parent** → A node that has one or more children.
- **Child** → A node directly connected to another node above it.
- **Leaf (External Node)** → A node with no children.
- **Internal Node** → A node that has at least one child.
- **Sibling** → Nodes with the same parent.

## 🔹 **Relationships**

- **Ancestor** → Any node along the path from the root to the current node.
- **Descendant** → Any node that lies below a given node.
- **Subtree** → A tree formed by any node and its descendants.

## 🔹 **Structural Properties**

- **Edge** → A connection between two nodes.
- **Path** → Sequence of nodes connected by edges.
- **Depth of a Node** → Distance from the root to that node.
- **Height of a Node** → Longest path from the node to a leaf.
- **Height of a Tree** → Height of the root node.
- **Level** → The depth of a node (root is level 0).
- **Degree of a Node** → Number of children a node has.
- **Degree of a Tree** → Maximum degree of any node in the tree.

## 🔹 **Special Nodes**

- **Root Node** → The first node in the tree.
- **Leaf Node** → End nodes with no children.
- **Non-Leaf Nodes** → Internal nodes having at least one child.

## 🌲 **Example Diagram**

```Plain
        A (Root, Level 0)
       / \
      B   C   (Level 1)
     / \    \
    D   E    F (Level 2)
```

- **Root:** A
- **Parent of B:** A
- **Children of B:** D, E
- **Siblings:** B and C; D and E
- **Leaves:** D, E, F
- **Height of Tree:** 2
- **Degree of Node B:** 2

✅ With this terminology, you can describe **any tree** precisely.

---