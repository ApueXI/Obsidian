---
Created: 2025-08-16T09:52
tags:
  - BroCode
---
## ==What is Depth First Search==

**Definition:**

Depth First Search is a graph traversal algorithm that explores **as far as possible along one branch (deep into the graph) before backtracking**.

It’s like exploring a maze: you pick a path, go deep until you can’t, then backtrack and try another path.

## 📊 DFS Complexity Analysis

Let:

- VVV = number of vertices
- EEE = number of edges
- **Time Complexity:**
    - `O(V + E)` → visit every vertex and edge once.
- **Space Complexity:**
    - `O(V)` for recursion stack (or explicit stack).
    - `O(V)` for visited set/array.

## 🔑 Key Properties

- **Traversal style:** Goes deep first, then backtracks.
- **Data structure:** Uses a **stack** (can be explicit or via recursion call stack).
- **Works for:** Directed, undirected, weighted (for traversal, not for shortest paths).
- **Applications:** Detecting cycles, topological sorting, connected components, solving puzzles, path finding.

## ⚡ Real-World Uses

- Finding **connected components** in a graph.
- **Cycle detection** (in directed/undirected graphs).
- **Topological sort** (for DAGs).
- **Path finding** in mazes/puzzles (not guaranteed shortest).
- **Artificial Intelligence**: Game tree exploration (chess, tic-tac-toe).
- **Compilers**: Checking dependencies between modules.

  

---

  

## ==Where is Depth First Search Used==

Depth First Search (DFS) is widely used in **graphs, trees, and problem-solving algorithms**. Its ability to go deep and backtrack makes it suitable for many real-world and computer science applications.

## 🔹 **1. Graph Traversal**

- Visit all vertices and edges in a **systematic way**.
- Example: Exploring **social networks** or **web page links**.

## 🔹 **2. Path Finding in Puzzles & Mazes**

- DFS explores paths deeply before backtracking.
- Example: Solving **mazes**, **Sudoku**, or **puzzle games**.

## 🔹 **3. Cycle Detection**

- Check if a **graph contains a cycle** (directed/undirected).
- Example: Detecting **deadlocks** in operating systems.

## 🔹 **4. Topological Sorting**

- DFS helps order tasks with dependencies.
- Example: **Course prerequisite checking**, **build systems** (make, compilers).

## 🔹 **5. Connected Components**

- Identify clusters in a graph.
- Example: **Friend groups in social networks**, **network connectivity**.

## 🔹 **6. Artificial Intelligence & Games**

- Explore **game trees** for decision-making.
- Example: **Tic-tac-toe**, **chess move generation**.

## 🔹 **7. Compilers & Parsing**

- Used for **dependency analysis** and **syntax tree traversal**.
- Example: **Expression evaluation**, **program analysis**.

## 📊 **Summary Table**

|Use Case|Why DFS?|Example Application|
|---|---|---|
|Graph traversal|Visit all vertices systematically|Social networks, web crawling|
|Path finding|Explore deep paths|Mazes, puzzles|
|Cycle detection|Detect loops in graphs|Deadlocks in OS|
|Topological sorting|Handle task dependencies|Course scheduling|
|Connected components|Find clusters|Social groups|
|AI & games|Explore decision trees|Chess, tic-tac-toe|
|Compilers & parsing|Analyze syntax trees|Expression parsing|

---

  

## ==Complexity Analysis==

DFS explores a graph by going deep along one path before backtracking. The complexity depends on the number of **vertices (V)** and **edges (E)** in the graph.

## ⏱ **Time Complexity**

- Each **vertex** is visited once → O(V)
- Each **edge** is explored once → O(E)
- **Total Time Complexity:** O(V+E)
- **Adjacency List Representation:** O(V + E) ✅ (efficient)
- **Adjacency Matrix Representation:** O(V²) ❌ (less efficient)

## 💾 **Space Complexity**

- **Visited array:** O(V)
- **Recursion stack (or explicit stack):** O(V) in the worst case (a deep path).
- **Total Space Complexity:** O(V)

## 🔍 **Summary Table**

|Factor|Complexity|
|---|---|
|Best Case (tree-like graph)|O(V + E)|
|Worst Case (dense graph)|O(V + E)|
|Average Case|O(V + E)|
|Space Complexity|O(V)|

✅ **DFS is efficient** when implemented with an adjacency list.

⚠️ With adjacency matrix, it becomes **slower (O(V²))** for sparse graphs.

---

  

## ==Code==

### Python

```Python
class Graph:
    def __init__(self):
        self.graph = {}
    
    def add_edge(self, u, v):
        """Add an edge to the graph"""
        if u not in self.graph:
            self.graph[u] = []
        if v not in self.graph:
            self.graph[v] = []
        self.graph[u].append(v)
    
    def dfs_recursive(self, start, visited=None):
        """DFS using recursion"""
        if visited is None:
            visited = set()
        
        visited.add(start)
        print(start, end=' ')
        
        if start in self.graph:
            for neighbor in self.graph[start]:
                if neighbor not in visited:
                    self.dfs_recursive(neighbor, visited)
    
    def dfs_iterative(self, start):
        """DFS using stack (iterative)"""
        visited = set()
        stack = [start]
        
        while stack:
            vertex = stack.pop()
            if vertex not in visited:
                visited.add(vertex)
                print(vertex, end=' ')
                
                # Add neighbors to stack (in reverse order for consistent traversal)
                if vertex in self.graph:
                    for neighbor in reversed(self.graph[vertex]):
                        if neighbor not in visited:
                            stack.append(neighbor)
    
    def dfs_path(self, start, target, visited=None, path=None):
        """Find path from start to target using DFS"""
        if visited is None:
            visited = set()
        if path is None:
            path = []
        
        visited.add(start)
        path.append(start)
        
        if start == target:
            return path
        
        if start in self.graph:
            for neighbor in self.graph[start]:
                if neighbor not in visited:
                    result = self.dfs_path(neighbor, target, visited, path.copy())
                    if result:
                        return result
        
        return None

# Example usage
if __name__ == "__main__":
    g = Graph()
    g.add_edge(0, 1)
    g.add_edge(0, 2)
    g.add_edge(1, 2)
    g.add_edge(2, 0)
    g.add_edge(2, 3)
    g.add_edge(3, 3)
    
    print("DFS Recursive starting from vertex 2:")
    g.dfs_recursive(2)
    print()
    
    print("DFS Iterative starting from vertex 2:")
    g.dfs_iterative(2)
    print()
    
    print("Path from 2 to 3:")
    path = g.dfs_path(2, 3)
    if path:
        print(" -> ".join(map(str, path)))
    else:
        print("No path found")
```

### C#

```C#
using System;
using System.Collections.Generic;
using System.Linq;

public class Graph
{
    private Dictionary<int, List<int>> graph;
    
    public Graph()
    {
        graph = new Dictionary<int, List<int>>();
    }
    
    public void AddEdge(int u, int v)
    {
        if (!graph.ContainsKey(u))
            graph[u] = new List<int>();
        if (!graph.ContainsKey(v))
            graph[v] = new List<int>();
        
        graph[u].Add(v);
    }
    
    public void DFSRecursive(int start, HashSet<int> visited = null)
    {
        if (visited == null)
            visited = new HashSet<int>();
        
        visited.Add(start);
        Console.Write(start + " ");
        
        if (graph.ContainsKey(start))
        {
            foreach (int neighbor in graph[start])
            {
                if (!visited.Contains(neighbor))
                {
                    DFSRecursive(neighbor, visited);
                }
            }
        }
    }
    
    public void DFSIterative(int start)
    {
        HashSet<int> visited = new HashSet<int>();
        Stack<int> stack = new Stack<int>();
        
        stack.Push(start);
        
        while (stack.Count > 0)
        {
            int vertex = stack.Pop();
            
            if (!visited.Contains(vertex))
            {
                visited.Add(vertex);
                Console.Write(vertex + " ");
                
                if (graph.ContainsKey(vertex))
                {
                    // Add neighbors in reverse order for consistent traversal
                    var neighbors = graph[vertex].ToList();
                    neighbors.Reverse();
                    
                    foreach (int neighbor in neighbors)
                    {
                        if (!visited.Contains(neighbor))
                        {
                            stack.Push(neighbor);
                        }
                    }
                }
            }
        }
    }
    
    public List<int> DFSPath(int start, int target, HashSet<int> visited = null, List<int> path = null)
    {
        if (visited == null)
            visited = new HashSet<int>();
        if (path == null)
            path = new List<int>();
        
        visited.Add(start);
        path.Add(start);
        
        if (start == target)
        {
            return path;
        }
        
        if (graph.ContainsKey(start))
        {
            foreach (int neighbor in graph[start])
            {
                if (!visited.Contains(neighbor))
                {
                    var result = DFSPath(neighbor, target, visited, new List<int>(path));
                    if (result != null)
                    {
                        return result;
                    }
                }
            }
        }
        
        return null;
    }
}

class Program
{
    static void Main()
    {
        Graph g = new Graph();
        g.AddEdge(0, 1);
        g.AddEdge(0, 2);
        g.AddEdge(1, 2);
        g.AddEdge(2, 0);
        g.AddEdge(2, 3);
        g.AddEdge(3, 3);
        
        Console.WriteLine("DFS Recursive starting from vertex 2:");
        g.DFSRecursive(2);
        Console.WriteLine();
        
        Console.WriteLine("DFS Iterative starting from vertex 2:");
        g.DFSIterative(2);
        Console.WriteLine();
        
        Console.WriteLine("Path from 2 to 3:");
        var path = g.DFSPath(2, 3);
        if (path != null)
        {
            Console.WriteLine(string.Join(" -> ", path));
        }
        else
        {
            Console.WriteLine("No path found");
        }
    }
}
```

### C++

```C++
\#include <iostream>
\#include <vector>
\#include <unordered_map>
\#include <unordered_set>
\#include <stack>
\#include <algorithm>

class Graph {
private:
    std::unordered_map<int, std::vector<int>> graph;
    
public:
    void addEdge(int u, int v) {
        graph[u].push_back(v);
        if (graph.find(v) == graph.end()) {
            graph[v] = std::vector<int>();
        }
    }
    
    void dfsRecursive(int start, std::unordered_set<int>& visited) {
        visited.insert(start);
        std::cout << start << " ";
        
        if (graph.find(start) != graph.end()) {
            for (int neighbor : graph[start]) {
                if (visited.find(neighbor) == visited.end()) {
                    dfsRecursive(neighbor, visited);
                }
            }
        }
    }
    
    void dfsRecursive(int start) {
        std::unordered_set<int> visited;
        dfsRecursive(start, visited);
    }
    
    void dfsIterative(int start) {
        std::unordered_set<int> visited;
        std::stack<int> stack;
        
        stack.push(start);
        
        while (!stack.empty()) {
            int vertex = stack.top();
            stack.pop();
            
            if (visited.find(vertex) == visited.end()) {
                visited.insert(vertex);
                std::cout << vertex << " ";
                
                if (graph.find(vertex) != graph.end()) {
                    // Add neighbors in reverse order for consistent traversal
                    std::vector<int> neighbors = graph[vertex];
                    std::reverse(neighbors.begin(), neighbors.end());
                    
                    for (int neighbor : neighbors) {
                        if (visited.find(neighbor) == visited.end()) {
                            stack.push(neighbor);
                        }
                    }
                }
            }
        }
    }
    
    std::vector<int> dfsPath(int start, int target, std::unordered_set<int>& visited, std::vector<int>& path) {
        visited.insert(start);
        path.push_back(start);
        
        if (start == target) {
            return path;
        }
        
        if (graph.find(start) != graph.end()) {
            for (int neighbor : graph[start]) {
                if (visited.find(neighbor) == visited.end()) {
                    std::vector<int> newPath = path;
                    std::unordered_set<int> newVisited = visited;
                    std::vector<int> result = dfsPath(neighbor, target, newVisited, newPath);
                    
                    if (!result.empty()) {
                        return result;
                    }
                }
            }
        }
        
        return std::vector<int>(); // Return empty vector if no path found
    }
    
    std::vector<int> dfsPath(int start, int target) {
        std::unordered_set<int> visited;
        std::vector<int> path;
        return dfsPath(start, target, visited, path);
    }
};

int main() {
    Graph g;
    g.addEdge(0, 1);
    g.addEdge(0, 2);
    g.addEdge(1, 2);
    g.addEdge(2, 0);
    g.addEdge(2, 3);
    g.addEdge(3, 3);
    
    std::cout << "DFS Recursive starting from vertex 2:" << std::endl;
    g.dfsRecursive(2);
    std::cout << std::endl;
    
    std::cout << "DFS Iterative starting from vertex 2:" << std::endl;
    g.dfsIterative(2);
    std::cout << std::endl;
    
    std::cout << "Path from 2 to 3:" << std::endl;
    std::vector<int> path = g.dfsPath(2, 3);
    if (!path.empty()) {
        for (size_t i = 0; i < path.size(); ++i) {
            std::cout << path[i];
            if (i < path.size() - 1) {
                std::cout << " -> ";
            }
        }
        std::cout << std::endl;
    } else {
        std::cout << "No path found" << std::endl;
    }
    
    return 0;
}
```

---