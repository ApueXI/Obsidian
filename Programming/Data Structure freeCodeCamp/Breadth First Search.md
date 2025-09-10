---
Created: 2025-08-16T09:52
tags:
  - BroCode
---
## ==What is Breadth First Search==

**Breadth First Search (BFS)** is a graph traversal algorithm that explores nodes **level by level** (or breadth-wise). It starts from a **source node**, visits all its neighbors first, then moves on to the next level of neighbors.

## 🔹 **How BFS Works**

1. Start from a **source node**.
2. Visit all its **immediate neighbors**.
3. Use a **queue** to keep track of nodes to visit next.
4. Continue until all reachable nodes are visited.

## 🔹 **Key Properties**

- **Explores shortest path first** (in unweighted graphs).
- Uses **Queue (FIFO)** for traversal.
- Guarantees visiting nodes in **increasing distance** from the start node.

## 🔹 **Applications of BFS**

- Finding **shortest path** in unweighted graphs.
- **Web crawling** (finding all reachable websites).
- **Social networks** (friend suggestions).
- **Network broadcasting** (sending data across all nodes).
- **AI & games** (finding the shortest sequence of moves).

## 📊 **Summary**

- **Data structure used:** Queue (FIFO)
- **Traversal style:** Level-order (breadth-first)
- **Best for:** Shortest path in unweighted graphs & exploring layers

## 🔹 **Example (Graph Traversal)**

For graph:

```Plain
A — B — C
|   |
D — E

```

Starting BFS at **A**:

**Order → A → B → D → C → E**

---

  

## ==Where is Breadth First Search Used==

Breadth First Search is widely used in computer science, networking, and real-world applications because it explores nodes **level by level** and guarantees the **shortest path in unweighted graphs**.

## 🔹 **1. Shortest Path in Unweighted Graphs**

- BFS always finds the shortest number of edges between two nodes.
- Example: Finding the **minimum number of moves** in a board game like Snakes and Ladders.

## 🔹 **2. Social Networks**

- To find **degrees of separation** (e.g., “friends of friends”).
- Example: Facebook suggesting “People You May Know” uses BFS.

## 🔹 **3. Web Crawling**

- Search engines like Google use BFS-like traversal to explore websites **layer by layer** from a seed URL.

## 🔹 **4. Network Broadcasting**

- BFS ensures data packets reach all nodes with **minimum hops**.
- Example: Sending a message to all computers in a LAN.

## 🔹 **5. Artificial Intelligence & Games**

- Used in puzzles (e.g., 8-puzzle, Rubik’s Cube) to find the **shortest solution sequence**.
- Example: Finding the shortest path in a maze.

## 🔹 **6. Peer-to-Peer (P2P) Networks**

- BFS is used to find nearby peers efficiently.
- Example: BitTorrent peer discovery.

## 🔹 **7. Garbage Collection (Mark-and-Sweep)**

- BFS is used in **mark phase** to traverse all reachable objects in memory.

✅ **In short:** BFS is the go-to algorithm when we need to **explore in layers** or guarantee the **shortest path in an unweighted scenario**.

---

  

## ==Complexity Analysis==

BFS explores a graph level by level using a **queue (FIFO)**. The complexity depends on the number of **vertices (V)** and **edges (E)** in the graph.

## ⏱ **Time Complexity**

- Each **vertex** is enqueued and dequeued once → O(V)
- Each **edge** is explored once → O(E)
- **Total Time Complexity:**

O(V+E)O(V + E)

O(V+E)

- **Adjacency List Representation:** O(V + E) ✅ (efficient)
- **Adjacency Matrix Representation:** O(V²) ❌ (less efficient)

## 💾 **Space Complexity**

- **Visited array:** O(V)
- **Queue storage:** O(V) in the worst case (if all vertices are in the queue).
- **Graph storage:**
    - Adjacency List → O(V + E)
    - Adjacency Matrix → O(V²)
- **Total Space Complexity:**

O(V+E)(with adjacency list)O(V + E) \quad \text{(with adjacency list)}

O(V+E)(with adjacency list)

## 🔍 **Summary Table**

|Factor|Complexity|
|---|---|
|Best Case (tree-like graph)|O(V + E)|
|Worst Case (dense graph)|O(V + E)|
|Average Case|O(V + E)|
|Space Complexity|O(V + E)|

✅ BFS is efficient for **shortest paths in unweighted graphs**.

⚠️ Using an adjacency matrix makes BFS slower for **sparse graphs**.

---

  

## ==Code==

### Python

```Python
from collections import deque

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
    
    def bfs(self, start):
        """Basic BFS traversal"""
        visited = set()
        queue = deque([start])
        visited.add(start)
        
        while queue:
            vertex = queue.popleft()
            print(vertex, end=' ')
            
            if vertex in self.graph:
                for neighbor in self.graph[vertex]:
                    if neighbor not in visited:
                        visited.add(neighbor)
                        queue.append(neighbor)
    
    def bfs_shortest_path(self, start, target):
        """Find shortest path from start to target using BFS"""
        if start == target:
            return [start]
        
        visited = set()
        queue = deque([(start, [start])])
        visited.add(start)
        
        while queue:
            vertex, path = queue.popleft()
            
            if vertex in self.graph:
                for neighbor in self.graph[vertex]:
                    if neighbor == target:
                        return path + [neighbor]
                    
                    if neighbor not in visited:
                        visited.add(neighbor)
                        queue.append((neighbor, path + [neighbor]))
        
        return None  # No path found
    
    def bfs_levels(self, start):
        """BFS that tracks levels/distances from start"""
        visited = set()
        queue = deque([(start, 0)])
        visited.add(start)
        levels = {}
        
        while queue:
            vertex, level = queue.popleft()
            levels[vertex] = level
            print(f"Level {level}: {vertex}")
            
            if vertex in self.graph:
                for neighbor in self.graph[vertex]:
                    if neighbor not in visited:
                        visited.add(neighbor)
                        queue.append((neighbor, level + 1))
        
        return levels
    
    def bfs_all_paths(self, start, target, max_depth=10):
        """Find all paths from start to target using BFS (with depth limit)"""
        if start == target:
            return [[start]]
        
        paths = []
        queue = deque([(start, [start])])
        
        while queue:
            vertex, path = queue.popleft()
            
            if len(path) > max_depth:
                continue
            
            if vertex in self.graph:
                for neighbor in self.graph[vertex]:
                    if neighbor == target:
                        paths.append(path + [neighbor])
                    elif neighbor not in path:  # Avoid cycles
                        queue.append((neighbor, path + [neighbor]))
        
        return paths

# Example usage
if __name__ == "__main__":
    g = Graph()
    g.add_edge(0, 1)
    g.add_edge(0, 2)
    g.add_edge(1, 2)
    g.add_edge(2, 0)
    g.add_edge(2, 3)
    g.add_edge(3, 3)
    g.add_edge(1, 4)
    g.add_edge(4, 5)
    
    print("BFS traversal starting from vertex 0:")
    g.bfs(0)
    print("\n")
    
    print("BFS levels starting from vertex 0:")
    levels = g.bfs_levels(0)
    print()
    
    print("Shortest path from 0 to 5:")
    path = g.bfs_shortest_path(0, 5)
    if path:
        print(" -> ".join(map(str, path)))
    else:
        print("No path found")
    print()
    
    print("All paths from 0 to 3 (max depth 5):")
    all_paths = g.bfs_all_paths(0, 3, 5)
    for i, path in enumerate(all_paths, 1):
        print(f"Path {i}: {' -> '.join(map(str, path))}")
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
    
    public void BFS(int start)
    {
        HashSet<int> visited = new HashSet<int>();
        Queue<int> queue = new Queue<int>();
        
        queue.Enqueue(start);
        visited.Add(start);
        
        while (queue.Count > 0)
        {
            int vertex = queue.Dequeue();
            Console.Write(vertex + " ");
            
            if (graph.ContainsKey(vertex))
            {
                foreach (int neighbor in graph[vertex])
                {
                    if (!visited.Contains(neighbor))
                    {
                        visited.Add(neighbor);
                        queue.Enqueue(neighbor);
                    }
                }
            }
        }
    }
    
    public List<int> BFSShortestPath(int start, int target)
    {
        if (start == target)
            return new List<int> { start };
        
        HashSet<int> visited = new HashSet<int>();
        Queue<(int vertex, List<int> path)> queue = new Queue<(int, List<int>)>();
        
        queue.Enqueue((start, new List<int> { start }));
        visited.Add(start);
        
        while (queue.Count > 0)
        {
            var (vertex, path) = queue.Dequeue();
            
            if (graph.ContainsKey(vertex))
            {
                foreach (int neighbor in graph[vertex])
                {
                    if (neighbor == target)
                    {
                        var resultPath = new List<int>(path);
                        resultPath.Add(neighbor);
                        return resultPath;
                    }
                    
                    if (!visited.Contains(neighbor))
                    {
                        visited.Add(neighbor);
                        var newPath = new List<int>(path);
                        newPath.Add(neighbor);
                        queue.Enqueue((neighbor, newPath));
                    }
                }
            }
        }
        
        return null; // No path found
    }
    
    public Dictionary<int, int> BFSLevels(int start)
    {
        HashSet<int> visited = new HashSet<int>();
        Queue<(int vertex, int level)> queue = new Queue<(int, int)>();
        Dictionary<int, int> levels = new Dictionary<int, int>();
        
        queue.Enqueue((start, 0));
        visited.Add(start);
        
        while (queue.Count > 0)
        {
            var (vertex, level) = queue.Dequeue();
            levels[vertex] = level;
            Console.WriteLine($"Level {level}: {vertex}");
            
            if (graph.ContainsKey(vertex))
            {
                foreach (int neighbor in graph[vertex])
                {
                    if (!visited.Contains(neighbor))
                    {
                        visited.Add(neighbor);
                        queue.Enqueue((neighbor, level + 1));
                    }
                }
            }
        }
        
        return levels;
    }
    
    public List<List<int>> BFSAllPaths(int start, int target, int maxDepth = 10)
    {
        if (start == target)
            return new List<List<int>> { new List<int> { start } };
        
        List<List<int>> paths = new List<List<int>>();
        Queue<(int vertex, List<int> path)> queue = new Queue<(int, List<int>)>();
        
        queue.Enqueue((start, new List<int> { start }));
        
        while (queue.Count > 0)
        {
            var (vertex, path) = queue.Dequeue();
            
            if (path.Count > maxDepth)
                continue;
            
            if (graph.ContainsKey(vertex))
            {
                foreach (int neighbor in graph[vertex])
                {
                    if (neighbor == target)
                    {
                        var resultPath = new List<int>(path);
                        resultPath.Add(neighbor);
                        paths.Add(resultPath);
                    }
                    else if (!path.Contains(neighbor)) // Avoid cycles
                    {
                        var newPath = new List<int>(path);
                        newPath.Add(neighbor);
                        queue.Enqueue((neighbor, newPath));
                    }
                }
            }
        }
        
        return paths;
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
        g.AddEdge(1, 4);
        g.AddEdge(4, 5);
        
        Console.WriteLine("BFS traversal starting from vertex 0:");
        g.BFS(0);
        Console.WriteLine("\n");
        
        Console.WriteLine("BFS levels starting from vertex 0:");
        var levels = g.BFSLevels(0);
        Console.WriteLine();
        
        Console.WriteLine("Shortest path from 0 to 5:");
        var path = g.BFSShortestPath(0, 5);
        if (path != null)
        {
            Console.WriteLine(string.Join(" -> ", path));
        }
        else
        {
            Console.WriteLine("No path found");
        }
        Console.WriteLine();
        
        Console.WriteLine("All paths from 0 to 3 (max depth 5):");
        var allPaths = g.BFSAllPaths(0, 3, 5);
        for (int i = 0; i < allPaths.Count; i++)
        {
            Console.WriteLine($"Path {i + 1}: {string.Join(" -> ", allPaths[i])}");
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
\#include <queue>
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
    
    void bfs(int start) {
        std::unordered_set<int> visited;
        std::queue<int> queue;
        
        queue.push(start);
        visited.insert(start);
        
        while (!queue.empty()) {
            int vertex = queue.front();
            queue.pop();
            std::cout << vertex << " ";
            
            if (graph.find(vertex) != graph.end()) {
                for (int neighbor : graph[vertex]) {
                    if (visited.find(neighbor) == visited.end()) {
                        visited.insert(neighbor);
                        queue.push(neighbor);
                    }
                }
            }
        }
    }
    
    std::vector<int> bfsShortestPath(int start, int target) {
        if (start == target) {
            return {start};
        }
        
        std::unordered_set<int> visited;
        std::queue<std::pair<int, std::vector<int>>> queue;
        
        queue.push({start, {start}});
        visited.insert(start);
        
        while (!queue.empty()) {
            auto [vertex, path] = queue.front();
            queue.pop();
            
            if (graph.find(vertex) != graph.end()) {
                for (int neighbor : graph[vertex]) {
                    if (neighbor == target) {
                        std::vector<int> resultPath = path;
                        resultPath.push_back(neighbor);
                        return resultPath;
                    }
                    
                    if (visited.find(neighbor) == visited.end()) {
                        visited.insert(neighbor);
                        std::vector<int> newPath = path;
                        newPath.push_back(neighbor);
                        queue.push({neighbor, newPath});
                    }
                }
            }
        }
        
        return {}; // Return empty vector if no path found
    }
    
    std::unordered_map<int, int> bfsLevels(int start) {
        std::unordered_set<int> visited;
        std::queue<std::pair<int, int>> queue;
        std::unordered_map<int, int> levels;
        
        queue.push({start, 0});
        visited.insert(start);
        
        while (!queue.empty()) {
            auto [vertex, level] = queue.front();
            queue.pop();
            
            levels[vertex] = level;
            std::cout << "Level " << level << ": " << vertex << std::endl;
            
            if (graph.find(vertex) != graph.end()) {
                for (int neighbor : graph[vertex]) {
                    if (visited.find(neighbor) == visited.end()) {
                        visited.insert(neighbor);
                        queue.push({neighbor, level + 1});
                    }
                }
            }
        }
        
        return levels;
    }
    
    std::vector<std::vector<int>> bfsAllPaths(int start, int target, int maxDepth = 10) {
        if (start == target) {
            return {{start}};
        }
        
        std::vector<std::vector<int>> paths;
        std::queue<std::pair<int, std::vector<int>>> queue;
        
        queue.push({start, {start}});
        
        while (!queue.empty()) {
            auto [vertex, path] = queue.front();
            queue.pop();
            
            if (static_cast<int>(path.size()) > maxDepth) {
                continue;
            }
            
            if (graph.find(vertex) != graph.end()) {
                for (int neighbor : graph[vertex]) {
                    if (neighbor == target) {
                        std::vector<int> resultPath = path;
                        resultPath.push_back(neighbor);
                        paths.push_back(resultPath);
                    }
                    else if (std::find(path.begin(), path.end(), neighbor) == path.end()) {
                        // Avoid cycles
                        std::vector<int> newPath = path;
                        newPath.push_back(neighbor);
                        queue.push({neighbor, newPath});
                    }
                }
            }
        }
        
        return paths;
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
    g.addEdge(1, 4);
    g.addEdge(4, 5);
    
    std::cout << "BFS traversal starting from vertex 0:" << std::endl;
    g.bfs(0);
    std::cout << "\n" << std::endl;
    
    std::cout << "BFS levels starting from vertex 0:" << std::endl;
    auto levels = g.bfsLevels(0);
    std::cout << std::endl;
    
    std::cout << "Shortest path from 0 to 5:" << std::endl;
    auto path = g.bfsShortestPath(0, 5);
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
    std::cout << std::endl;
    
    std::cout << "All paths from 0 to 3 (max depth 5):" << std::endl;
    auto allPaths = g.bfsAllPaths(0, 3, 5);
    for (size_t i = 0; i < allPaths.size(); ++i) {
        std::cout << "Path " << (i + 1) << ": ";
        for (size_t j = 0; j < allPaths[i].size(); ++j) {
            std::cout << allPaths[i][j];
            if (j < allPaths[i].size() - 1) {
                std::cout << " -> ";
            }
        }
        std::cout << std::endl;
    }
    
    return 0;
}
```

---