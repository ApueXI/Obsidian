---
Created: 2025-08-07T13:49
tags:
  - William-Fiset
---
# ==Discussion & Examples==

---

  

## 🤝 ==What is a Union Find?==

**Union Find** (also called **Disjoint Set Union, DSU**) is a data structure that keeps track of elements grouped into disjoint sets (non-overlapping groups). It supports two key operations:

- **Find** 🔍: Identify which group/set an element belongs to.
- **Union** ➕: Merge two groups into one.

## 🎯 Why use Union Find?

Perfect for problems dealing with grouping and connectivity, such as:

- Detecting cycles in graphs 🚫🔄
- Finding connected components 🌐
- Building Minimum Spanning Trees (Kruskal’s algorithm) 🏗️
- Network connectivity queries 📡

## ⚙️ How does it work?

- Each set is represented by a **tree**, where each node points to its parent.
- The **root** of the tree is the representative of that set.
- **Find** climbs the tree to find the root.
- **Union** merges two trees by connecting one root to the other.

**Optimizations:**

- **Path Compression** 🛤️: During Find, make every visited node point directly to the root to flatten the tree.
- **Union by Rank/Size** 📏: Always attach the smaller tree under the bigger to keep trees shallow.

## ⏱️ Time Complexity

Almost **O(1)** per operation (amortized), thanks to path compression and union by rank.

# 💻 Code Examples

### Python 🐍

```Python
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0] * n

    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])  # Path compression 🛤️
        return self.parent[x]

    def union(self, x, y):
        rootX = self.find(x)
        rootY = self.find(y)
        if rootX != rootY:
            if self.rank[rootX] < self.rank[rootY]:
                self.parent[rootX] = rootY
            elif self.rank[rootX] > self.rank[rootY]:
                self.parent[rootY] = rootX
            else:
                self.parent[rootY] = rootX
                self.rank[rootX] += 1
```

---

  

## 🤝 ==Union Find — Magnets Example 🧲🧲==

Imagine you have a bunch of **magnets** scattered on a table. Each magnet represents an element. Initially, **each magnet is separate** — it forms its own group (set).

- When you **bring two magnets close**, they **stick together** and form a bigger magnet cluster (union of two sets).
- You can easily check if two magnets are stuck together by seeing if they belong to the same cluster (find operation).

### How it matches the Union Find structure:

- **Each magnet cluster** is like a **disjoint set**.
- The **representative magnet** in the cluster is like the **root** in the Union Find tree.
- When two clusters join, one cluster’s representative becomes attached to the other — like sticking magnets together.
- **Find** operation is like tracing which cluster a magnet belongs to by following connections to the main magnet in the cluster.
- **Union** is like joining two clusters by making the representative magnets connect.

### Why path compression and union by rank?

- **Path Compression** 🛤️: Imagine every magnet you pass along to get to the main cluster becomes directly attached to the representative magnet, so next time you check, it’s super fast.
- **Union by Rank** 📏: When combining clusters, attach the smaller cluster’s representative magnet under the bigger cluster’s representative magnet to keep the cluster neat and easy to manage.

### Summary in Magnets terms:

|Union Find Term|Magnet Analogy|
|---|---|
|Element|A single magnet|
|Set/Cluster|A group of stuck-together magnets|
|Representative|The main magnet holding the cluster|
|Union|Sticking two clusters together|
|Find|Finding the main magnet of your cluster|

---

  

## ⏰ ==When is Union Find used?==

Use **Union Find** when you need to:

- **Quickly group elements** into disjoint sets and check if two elements belong to the same group.
- **Manage dynamic connectivity** — when connections (unions) are added over time and you need fast queries.
- **Detect cycles** in undirected graphs.
- **Efficiently merge sets** and query their representatives.

## 🌍 Where is Union Find used?

Here are some common **real-world** and **algorithmic** applications:

### 1. **Graph Algorithms** 🌐

- **Detect cycles** in undirected graphs (e.g., in Kruskal’s MST algorithm).
- **Find connected components** — groups of nodes connected by paths.

### 2. **Minimum Spanning Tree (MST)** 🏗️

- **Kruskal’s algorithm** uses Union Find to efficiently check if adding an edge will create a cycle and to merge components.

### 3. **Network Connectivity** 📡

- Checking if two computers or routers are in the same network cluster.
- Managing social networks — checking if two people belong to the same friend group.

### 4. **Image Processing** 🖼️

- Finding connected regions in pixel grids.

### 5. **Dynamic Equivalence Problems** ⚖️

- Problems where equivalence relations change over time and need quick updates.

### 6. **Percolation Theory and Physics** 🔬

- Modeling connected clusters in materials.

# Quick Summary Table 📌

|Use Case|Why Union Find?|
|---|---|
|Cycle detection in graphs|Fast union and find to detect loops|
|Kruskal’s MST|Efficiently merge sets and avoid cycles|
|Network clusters|Check connectivity between nodes|
|Social networks|Track friend groups|
|Image connected components|Group adjacent pixels|

---

  

## 🏗️ ==Kruskal’s Minimum Spanning Tree Algorithm==

**Kruskal’s algorithm** finds a **Minimum Spanning Tree (MST)** for a connected, weighted, undirected graph. The MST is a subset of edges that connects all vertices with the **minimum possible total edge weight** and **no cycles**.

## 🎯 How Kruskal’s Algorithm Works

1. **Sort all edges** in the graph by increasing weight.
2. Initialize an empty MST set to store edges.
3. Use a **Union Find** data structure to keep track of connected components (sets of vertices).
4. For each edge in sorted order:
    - If the edge connects two different sets (i.e., doesn’t create a cycle), **add it to MST** and **union** their sets.
    - Otherwise, **skip** the edge (it would create a cycle).
5. Stop when MST contains exactly `V-1` edges (`V` = number of vertices).

## ⚙️ Why Union Find?

- Efficiently **check if two vertices are in the same connected component** (Find operation).
- Efficiently **merge components** when adding edges (Union operation).
- Helps detect cycles by preventing edges that connect vertices already in the same set.

## ⏱️ Time Complexity

- Sorting edges: **O(E log E)** (E = number of edges)
- Union Find operations: nearly **O(E α(V))**, α = inverse Ackermann function, practically constant
- Overall complexity: **O(E log E)**

# 📌 Summary

|Step|Description|
|---|---|
|Sort edges|Sort all edges by weight|
|Union Find|Use DSU to avoid cycles|
|Iterate edges|Add edges that connect different sets|
|Stop condition|MST contains `V-1` edges|
|Result|MST with minimum total weight|

## 💻 Code Example (Python)

```Python
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0] * n

    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])  # Path compression
        return self.parent[x]

    def union(self, x, y):
        rootX = self.find(x)
        rootY = self.find(y)
        if rootX != rootY:
            if self.rank[rootX] < self.rank[rootY]:
                self.parent[rootX] = rootY
            elif self.rank[rootX] > self.rank[rootY]:
                self.parent[rootY] = rootX
            else:
                self.parent[rootY] = rootX
                self.rank[rootX] += 1
            return True
        return False

def kruskal(n, edges):
    # n = number of vertices
    # edges = list of tuples (weight, u, v)
    edges.sort(key=lambda x: x[0])  # Sort by weight
    uf = UnionFind(n)
    mst_weight = 0
    mst_edges = []

    for weight, u, v in edges:
        if uf.union(u, v):
            mst_weight += weight
            mst_edges.append((u, v, weight))

    return mst_weight, mst_edges

# Example usage:
edges = [
    (1, 0, 1),
    (4, 0, 2),
    (3, 1, 2),
    (2, 1, 3),
    (5, 2, 3),
]
n = 4  # vertices 0,1,2,3

weight, mst = kruskal(n, edges)
print("MST weight:", weight)
print("Edges in MST:", mst)
```

---

  

## ⏱️ ==Complexity Analysis of Union Find==

Union Find supports two main operations:

- **Find(x)** 🔍 — Find the representative (root) of the set containing element x.
- **Union(x, y)** ➕ — Merge the sets containing elements x and y.

### Without Optimizations (Naive Approach)

- Both **Find** and **Union** can take up to **O(n)** in the worst case because trees can become tall and skewed.

### With Optimizations

1. **Path Compression** 🛤️
    - During **Find**, make every node on the path point directly to the root.
    - Flattens the tree, speeding up future **Find** operations.
2. **Union by Rank/Size** 📏
    - Always attach the smaller tree under the root of the larger tree.
    - Keeps trees balanced and shallow.

### Time Complexity with Optimizations

- Each **Find** or **Union** operation runs in **amortized O(α(n))** time, where:
    - **α(n)** is the **inverse Ackermann function**, a very slowly growing function.
    - For all practical input sizes, **α(n) ≤ 4**, so it's almost constant time!

### Explanation

- Even though a single operation might take longer in rare cases, the **amortized cost** (averaged over many operations) is extremely efficient.
- This makes Union Find perfect for handling large numbers of union/find operations efficiently.

### Space Complexity

- Requires **O(n)** space to store parent and rank arrays (or size arrays).

# Summary Table 📌

|Operation|Time Complexity (Amortized)|Notes|
|---|---|---|
|**Find(x)** 🔍|O(α(n)) ≈ O(1)|Thanks to path compression|
|**Union(x, y)** ➕|O(α(n)) ≈ O(1)|Uses union by rank/size|
|Space|O(n)|Stores parent and rank/size arrays|

---

  

## ⏱️ ==Complexity Analysis of Kruskal’s MST Algorithm==

### 1. **Sorting the Edges**

- You start by sorting all the edges based on their weights.
- If there are **E** edges, sorting takes:
    
    **O(E log E)** time.
    

### 2. **Union Find Operations**

- For each edge, you perform:
    - A **Find** operation to check which set each vertex belongs to.
    - A **Union** operation to merge sets if the vertices are in different sets.
- Using **Union Find with path compression and union by rank/size**, each operation (Find or Union) runs in nearly:
    
    **O(α(V))**, where **α** is the inverse Ackermann function — practically constant and ≤ 4 for all reasonable V.
    
- Since you process each edge once, total Union Find cost is:
    
    **O(E α(V)) ≈ O(E)**
    
      
    

### 3. **Overall Time Complexity**

Combining both steps:

O(Elog⁡E)+O(Eα(V))≈O(Elog⁡E)\boxed{  
O(E \log E) + O(E \alpha(V)) \approx O(E \log E)  
}

O(ElogE)+O(Eα(V))≈O(ElogE)

- Usually, Elog⁡EE \log EElogE dominates Eα(V)E \alpha(V)Eα(V).
- For a connected graph with VVV vertices and EEE edges, since E≤V2E \leq V^2E≤V2, sorting is the bottleneck.

### 4. **Space Complexity**

- Storing the graph edges: **O(E)**
- Union Find parent and rank arrays: **O(V)**

# Summary Table 📌

|Operation|Time Complexity|Explanation|
|---|---|---|
|Sorting edges|O(E log E)|Sorting edges by weight|
|Union Find (Find/Union)|O(E α(V)) ≈ O(E)|Nearly constant time per operation|
|**Total**|**O(E log E)**|Sorting dominates overall time|

---

## ⏳ ==What is Amortized Analysis?==

**Amortized analysis** studies the **average running time per operation** over a **sequence** of operations, rather than the worst case for a single operation.

- It **smooths out costly operations** by spreading their cost over many cheap operations.
- Helps explain why some data structures perform very efficiently in practice, despite occasional expensive steps.

## 🤝 Amortized Analysis in Union Find

- **Union Find** operations (`find` and `union`) may sometimes do expensive work (like traversing a long chain of parents).
- But with **path compression** and **union by rank/size**, these expensive steps become rare.
- Over **many operations**, the **average cost per operation** becomes very low.

## 🔢 What’s the Time Complexity?

- Each `find` or `union` operation runs in **amortized O(α(n))** time.
- **α(n)** = inverse Ackermann function — grows **so slowly** that for all practical inputs it’s ≤ 4!
- So, you can think of Union Find operations as essentially **constant time on average**.

## 🎯 Intuition: How Amortized Analysis Works Here

- The **first few finds** might take longer, walking up trees.
- But path compression flattens the tree, so **later finds are much faster**.
- The cost of these expensive finds is "paid forward" and spread out.

# Summary 📌

|Concept|Explanation|
|---|---|
|Amortized Analysis ⏳|Average cost per operation over many operations|
|Union Find|Amortized cost is O(α(n)) — almost constant|
|Practical Impact|Even with millions of operations, it stays very fast|

---

# ==Implementation Details==

---

  

## 🔍 ==Find Operation==

**Purpose:**

Find the **representative (root)** of the set that an element belongs to.

**How it works:**

- Start at the element.
- Follow the chain of parent pointers until you reach a node that is its own parent (the root).
- The root is the representative of the entire set.

**Optimization:**

- **Path Compression** 🛤️ — While finding the root, update each visited node’s parent to point directly to the root. This flattens the tree and speeds up future finds.

## ➕ ==Union Operation==

**Purpose:**

Merge two sets containing different elements into a single set.

**How it works:**

- Find the roots of both elements using **Find**.
- If roots are different, attach one root as the child of the other. This merges the sets.

**Optimization:**

- **Union by Rank/Size** 📏 — Attach the root of the smaller tree to the root of the larger tree to keep trees shallow.

## Visual Summary

```Plain
Find(x):
  if parent[x] != x:
    parent[x] = Find(parent[x])  # Path Compression 🛤️
  return parent[x]

Union(x, y):
  rootX = Find(x)
  rootY = Find(y)
  if rootX != rootY:
    if rank[rootX] < rank[rootY]:
      parent[rootX] = rootY
    else if rank[rootX] > rank[rootY]:
      parent[rootY] = rootX
    else:
      parent[rootY] = rootX
      rank[rootX] += 1
```

## Why are these operations efficient?

- Path compression during **Find** keeps the tree flat, so future operations are faster.
- Union by rank/size avoids tall trees, keeping operations close to constant time.

---

  

## 🛤️ ==What is Path Compression?==

**Path Compression** is an optimization technique used in the **Find** operation of the Union Find (Disjoint Set Union) data structure.

## 🎯 Purpose

- To **flatten the structure of the tree** representing each set.
- This speeds up future **Find** operations by making nodes point **directly to the root** (representative).

## 🔍 How it works

- When you call `Find(x)`, you recursively travel up the parent chain to find the root.
- On the way back down, update the `parent` of each visited node directly to the root.
- This means next time you call `Find` on those nodes, you reach the root in **one step**.

## Example (Before and After Path Compression)

Imagine a chain like this (parent pointers):

```Plain
x -> a -> b -> root
```

Without path compression, **Find(x)** walks through `a` and `b` each time.

With path compression, after `Find(x)`, the parent of `x` and `a` is set directly to `root`:

```Plain
x -> root
a -> root
b -> root
```

## Code snippet (Python)

```Python
def find(x):
    if parent[x] != x:
        parent[x] = find(parent[x])  # Path compression here 🛤️
    return parent[x]
```

## ⏱️ Impact on Complexity

- Without path compression, **Find** can be O(n) in worst cases.
- With path compression (plus union by rank), amortized complexity per operation is almost **O(1)** — specifically **O(α(n))**, where α is the inverse Ackermann function.

## Summary 📌

|Concept|Description|
|---|---|
|Path Compression 🛤️|Flattens trees by pointing nodes directly to root during Find|
|Benefit|Speeds up repeated Find operations drastically|
|Result|Nearly constant amortized time per operation|

  

---

# ==Code Implementation==

---

- **Initialize** `n` separate sets
- **Find** with **path compression** for efficiency
- **Union** with **union by rank** to keep tree height small

- **Track component sizes** (e.g., size of the set containing a given element)
- **Nearly O(1)** amortized time complexity for each operation

### **Python – Union-Find with Size Tracking**

```Python
class UnionFind:
    def __init__(self, n):
        """
        Initialize Union Find data structure with n elements (0 to n-1)
        """
        self.parent = list(range(n))  # Each element is its own parent initially
        self.rank = [0] * n           # Rank for union by rank optimization
        self.size = [1] * n           # Size of each component
        self.components = n           # Total number of components
    
    def find(self, x):
        """
        Find the root of element x with path compression
        """
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])  # Path compression
        return self.parent[x]
    
    def union(self, x, y):
        """
        Union two elements x and y
        Returns True if union was performed, False if already in same set
        """
        root_x = self.find(x)
        root_y = self.find(y)
        
        if root_x == root_y:
            return False  # Already in same component
        
        # Union by rank optimization
        if self.rank[root_x] < self.rank[root_y]:
            root_x, root_y = root_y, root_x
        
        self.parent[root_y] = root_x
        self.size[root_x] += self.size[root_y]
        
        if self.rank[root_x] == self.rank[root_y]:
            self.rank[root_x] += 1
        
        self.components -= 1
        return True
    
    def connected(self, x, y):
        """
        Check if two elements are in the same component
        """
        return self.find(x) == self.find(y)
    
    def get_size(self, x):
        """
        Get the size of the component containing element x
        """
        return self.size[self.find(x)]
    
    def get_components(self):
        """
        Get the number of connected components
        """
        return self.components

# Example usage
if __name__ == "__main__":
    uf = UnionFind(10)
    
    # Union some elements
    uf.union(0, 1)
    uf.union(2, 3)
    uf.union(1, 3)
    
    print(f"0 and 3 connected: {uf.connected(0, 3)}")  # True
    print(f"0 and 4 connected: {uf.connected(0, 4)}")  # False
    print(f"Size of component containing 0: {uf.get_size(0)}")  # 4
    print(f"Total components: {uf.get_components()}")  # 7
```

### **C# – Union-Find with Size Tracking**

```C#
using System;

public class UnionFind
{
    private int[] parent;
    private int[] rank;
    private int[] size;
    private int components;
    
    /// <summary>
    /// Initialize Union Find data structure with n elements (0 to n-1)
    /// </summary>
    public UnionFind(int n)
    {
        parent = new int[n];
        rank = new int[n];
        size = new int[n];
        components = n;
        
        for (int i = 0; i < n; i++)
        {
            parent[i] = i;  // Each element is its own parent initially
            rank[i] = 0;
            size[i] = 1;
        }
    }
    
    /// <summary>
    /// Find the root of element x with path compression
    /// </summary>
    public int Find(int x)
    {
        if (parent[x] != x)
        {
            parent[x] = Find(parent[x]);  // Path compression
        }
        return parent[x];
    }
    
    /// <summary>
    /// Union two elements x and y
    /// Returns true if union was performed, false if already in same set
    /// </summary>
    public bool Union(int x, int y)
    {
        int rootX = Find(x);
        int rootY = Find(y);
        
        if (rootX == rootY)
        {
            return false;  // Already in same component
        }
        
        // Union by rank optimization
        if (rank[rootX] < rank[rootY])
        {
            (rootX, rootY) = (rootY, rootX);
        }
        
        parent[rootY] = rootX;
        size[rootX] += size[rootY];
        
        if (rank[rootX] == rank[rootY])
        {
            rank[rootX]++;
        }
        
        components--;
        return true;
    }
    
    /// <summary>
    /// Check if two elements are in the same component
    /// </summary>
    public bool Connected(int x, int y)
    {
        return Find(x) == Find(y);
    }
    
    /// <summary>
    /// Get the size of the component containing element x
    /// </summary>
    public int GetSize(int x)
    {
        return size[Find(x)];
    }
    
    /// <summary>
    /// Get the number of connected components
    /// </summary>
    public int GetComponents()
    {
        return components;
    }
}

// Example usage
class Program
{
    static void Main()
    {
        UnionFind uf = new UnionFind(10);
        
        // Union some elements
        uf.Union(0, 1);
        uf.Union(2, 3);
        uf.Union(1, 3);
        
        Console.WriteLine($"0 and 3 connected: {uf.Connected(0, 3)}");  // True
        Console.WriteLine($"0 and 4 connected: {uf.Connected(0, 4)}");  // False
        Console.WriteLine($"Size of component containing 0: {uf.GetSize(0)}");  // 4
        Console.WriteLine($"Total components: {uf.GetComponents()}");  // 7
    }
}
```

### **C++ – Union-Find with Size Tracking**

```C++
\#include <iostream>
\#include <vector>
\#include <numeric>

class UnionFind {
private:
    std::vector<int> parent;
    std::vector<int> rank;
    std::vector<int> size;
    int components;

public:
    /**
     * Initialize Union Find data structure with n elements (0 to n-1)
     */
    UnionFind(int n) : parent(n), rank(n, 0), size(n, 1), components(n) {
        std::iota(parent.begin(), parent.end(), 0);  // Each element is its own parent
    }
    
    /**
     * Find the root of element x with path compression
     */
    int find(int x) {
        if (parent[x] != x) {
            parent[x] = find(parent[x]);  // Path compression
        }
        return parent[x];
    }
    
    /**
     * Union two elements x and y
     * Returns true if union was performed, false if already in same set
     */
    bool unionSets(int x, int y) {
        int rootX = find(x);
        int rootY = find(y);
        
        if (rootX == rootY) {
            return false;  // Already in same component
        }
        
        // Union by rank optimization
        if (rank[rootX] < rank[rootY]) {
            std::swap(rootX, rootY);
        }
        
        parent[rootY] = rootX;
        size[rootX] += size[rootY];
        
        if (rank[rootX] == rank[rootY]) {
            rank[rootX]++;
        }
        
        components--;
        return true;
    }
    
    /**
     * Check if two elements are in the same component
     */
    bool connected(int x, int y) {
        return find(x) == find(y);
    }
    
    /**
     * Get the size of the component containing element x
     */
    int getSize(int x) {
        return size[find(x)];
    }
    
    /**
     * Get the number of connected components
     */
    int getComponents() const {
        return components;
    }
};

// Example usage
int main() {
    UnionFind uf(10);
    
    // Union some elements
    uf.unionSets(0, 1);
    uf.unionSets(2, 3);
    uf.unionSets(1, 3);
    
    std::cout << "0 and 3 connected: " << std::boolalpha << uf.connected(0, 3) << std::endl;  // true
    std::cout << "0 and 4 connected: " << std::boolalpha << uf.connected(0, 4) << std::endl;  // false
    std::cout << "Size of component containing 0: " << uf.getSize(0) << std::endl;  // 4
    std::cout << "Total components: " << uf.getComponents() << std::endl;  // 7
    
    return 0;
}
```