---
Created: 2025-08-16T09:52
tags:
  - BroCode
---
## ==What is Adjacency Matrix==

## **Definition**

An **Adjacency Matrix** is a way to **represent a graph** using a **2D array (matrix)**.

- Each **row and column** represents a **vertex** in the graph.
- The **cell value** indicates whether an **edge exists** between two vertices:
    - `1` (or weight) → edge exists
    - `0` → no edge

## **Features**

1. **Size:** V × V, where V = number of vertices
2. **Edge Lookup:** O(1) → fast to check if an edge exists
3. **Space Complexity:** O(V²) → inefficient for sparse graphs

## **Directed vs Undirected Graph**

|Type|Matrix Representation|
|---|---|
|**Undirected**|Symmetric across the diagonal|
|**Directed**|Not necessarily symmetric; direction matters|

## **Weighted vs Unweighted Graph**

|Type|Matrix Values|
|---|---|
|**Unweighted**|1 for edge, 0 for no edge|
|**Weighted**|Weight of edge, 0 (or ∞) for no edge|

## **Example**

**Undirected, unweighted graph:**

```Plain
Vertices: A, B, C
Edges: A-B, B-C
Adjacency Matrix:

    A B C
A [ 0 1 0 ]
B [ 1 0 1 ]
C [ 0 1 0 ]
```

**Explanation:**

- `A-B = 1` → edge exists
- `A-C = 0` → no edge

## **Pros and Cons**

|Pros|Cons|
|---|---|
|Fast edge lookup O(1)|Takes O(V²) space|
|Easy to implement|Inefficient for sparse graphs|
|Good for dense graphs|Not memory-friendly for large graphs|

  

---

  

## ==Where is Adjacency Matrix used==

An **Adjacency Matrix** is suitable when you need **fast edge lookup** or are working with **dense graphs**.

## **1. Dense Graphs**

- When a graph has **many edges** (close to V² edges), adjacency matrix is efficient.
- Example: Network of flights between major airports.

## **2. Fast Edge Lookup**

- Checking if an **edge exists** between two vertices is **O(1)**.
- Example: Determining if two users are connected in a social network with many connections.

## **3. Weighted Graphs**

- Easy to store **weights** of edges directly in the matrix.
- Example: Storing distances between cities for shortest path algorithms.

## **4. Graph Algorithms**

- Useful in algorithms that need **frequent edge existence checks**, like:
    - Floyd-Warshall (All-Pairs Shortest Path)
    - Prim’s and Kruskal’s algorithm (for dense graphs)

## **5. Memory-Intensive but Simple Representation**

- Works well for graphs with a **manageable number of vertices**, where space is not a concern.
- Example: Small board games or finite state machines.

## **Summary Table**

|Use Case|Why Adjacency Matrix?|
|---|---|
|Dense graphs|Efficient storage and access|
|Edge existence queries|O(1) lookup|
|Weighted graphs|Stores weights directly|
|Algorithms with frequent checks|Supports Floyd-Warshall, Prim’s, etc.|
|Small/medium graphs|Simplicity outweighs space cost|

---

  

## ==Complexity Analysis==

An **Adjacency Matrix** represents a graph using a **V × V matrix**, where `V` = number of vertices.

## **Space Complexity**

- **O(V²)** → stores information for every possible vertex pair, regardless of actual edges.
- **Efficient for dense graphs**, but wasteful for sparse graphs.

## **Time Complexity**

|Operation|Complexity|
|---|---|
|**Check if edge exists (u, v)**|O(1)|
|**Add an edge**|O(1)|
|**Remove an edge**|O(1)|
|**Iterate over all neighbors of a vertex**|O(V)|
|**Iterate over all edges**|O(V²)|

## **Pros**

- **Fast edge lookup**
- Simple to implement
- Works well with **dense graphs**

## **Cons**

- **High memory usage** for sparse graphs
- Iterating through all neighbors is slower compared to adjacency list for sparse graphs

## **Summary Table**

|Feature|Complexity / Notes|
|---|---|
|Space|O(V²)|
|Edge existence check|O(1)|
|Add/Remove edge|O(1)|
|Iterate neighbors|O(V)|
|Iterate all edges|O(V²)|

---

  

## ==Code==

### Python

```Python
class AdjacencyMatrix:
    def __init__(self, num_vertices):
        """Initialize adjacency matrix with given number of vertices"""
        self.num_vertices = num_vertices
        self.matrix = [[0 for _ in range(num_vertices)] for _ in range(num_vertices)]
    
    def add_edge(self, src, dest, weight=1):
        """Add an edge from src to dest with optional weight"""
        if 0 <= src < self.num_vertices and 0 <= dest < self.num_vertices:
            self.matrix[src][dest] = weight
        else:
            print("Invalid vertex index")
    
    def add_undirected_edge(self, src, dest, weight=1):
        """Add an undirected edge between src and dest"""
        self.add_edge(src, dest, weight)
        self.add_edge(dest, src, weight)
    
    def remove_edge(self, src, dest):
        """Remove edge from src to dest"""
        if 0 <= src < self.num_vertices and 0 <= dest < self.num_vertices:
            self.matrix[src][dest] = 0
        else:
            print("Invalid vertex index")
    
    def has_edge(self, src, dest):
        """Check if edge exists from src to dest"""
        if 0 <= src < self.num_vertices and 0 <= dest < self.num_vertices:
            return self.matrix[src][dest] != 0
        return False
    
    def get_neighbors(self, vertex):
        """Get all neighbors of a vertex"""
        if 0 <= vertex < self.num_vertices:
            neighbors = []
            for i in range(self.num_vertices):
                if self.matrix[vertex][i] != 0:
                    neighbors.append(i)
            return neighbors
        return []
    
    def display(self):
        """Display the adjacency matrix"""
        print("Adjacency Matrix:")
        for row in self.matrix:
            print(" ".join(f"{val:3}" for val in row))
    
    def get_matrix(self):
        """Return the matrix as a 2D list"""
        return self.matrix

# Example usage
if __name__ == "__main__":
    # Create a graph with 5 vertices
    graph = AdjacencyMatrix(5)
    
    # Add some edges
    graph.add_edge(0, 1, 2)
    graph.add_edge(0, 2, 3)
    graph.add_edge(1, 3, 4)
    graph.add_undirected_edge(2, 4, 5)
    
    # Display the matrix
    graph.display()
    
    # Check for edges
    print(f"\nEdge from 0 to 1: {graph.has_edge(0, 1)}")
    print(f"Edge from 1 to 0: {graph.has_edge(1, 0)}")
    
    # Get neighbors
    print(f"Neighbors of vertex 0: {graph.get_neighbors(0)}")
    print(f"Neighbors of vertex 2: {graph.get_neighbors(2)}")
```

### C#

```C#
using System;
using System.Collections.Generic;

public class AdjacencyMatrix
{
    private int[,] matrix;
    private int numVertices;

    public AdjacencyMatrix(int numVertices)
    {
        this.numVertices = numVertices;
        this.matrix = new int[numVertices, numVertices];
        
        // Initialize all values to 0
        for (int i = 0; i < numVertices; i++)
        {
            for (int j = 0; j < numVertices; j++)
            {
                matrix[i, j] = 0;
            }
        }
    }

    public void AddEdge(int src, int dest, int weight = 1)
    {
        if (IsValidVertex(src) && IsValidVertex(dest))
        {
            matrix[src, dest] = weight;
        }
        else
        {
            Console.WriteLine("Invalid vertex index");
        }
    }

    public void AddUndirectedEdge(int src, int dest, int weight = 1)
    {
        AddEdge(src, dest, weight);
        AddEdge(dest, src, weight);
    }

    public void RemoveEdge(int src, int dest)
    {
        if (IsValidVertex(src) && IsValidVertex(dest))
        {
            matrix[src, dest] = 0;
        }
        else
        {
            Console.WriteLine("Invalid vertex index");
        }
    }

    public bool HasEdge(int src, int dest)
    {
        if (IsValidVertex(src) && IsValidVertex(dest))
        {
            return matrix[src, dest] != 0;
        }
        return false;
    }

    public List<int> GetNeighbors(int vertex)
    {
        List<int> neighbors = new List<int>();
        if (IsValidVertex(vertex))
        {
            for (int i = 0; i < numVertices; i++)
            {
                if (matrix[vertex, i] != 0)
                {
                    neighbors.Add(i);
                }
            }
        }
        return neighbors;
    }

    public void Display()
    {
        Console.WriteLine("Adjacency Matrix:");
        for (int i = 0; i < numVertices; i++)
        {
            for (int j = 0; j < numVertices; j++)
            {
                Console.Write($"{matrix[i, j],3} ");
            }
            Console.WriteLine();
        }
    }

    public int[,] GetMatrix()
    {
        return (int[,])matrix.Clone();
    }

    private bool IsValidVertex(int vertex)
    {
        return vertex >= 0 && vertex < numVertices;
    }

    public int NumVertices => numVertices;
}

// Example usage
class Program
{
    static void Main(string[] args)
    {
        // Create a graph with 5 vertices
        AdjacencyMatrix graph = new AdjacencyMatrix(5);
        
        // Add some edges
        graph.AddEdge(0, 1, 2);
        graph.AddEdge(0, 2, 3);
        graph.AddEdge(1, 3, 4);
        graph.AddUndirectedEdge(2, 4, 5);
        
        // Display the matrix
        graph.Display();
        
        // Check for edges
        Console.WriteLine($"\nEdge from 0 to 1: {graph.HasEdge(0, 1)}");
        Console.WriteLine($"Edge from 1 to 0: {graph.HasEdge(1, 0)}");
        
        // Get neighbors
        var neighbors0 = graph.GetNeighbors(0);
        var neighbors2 = graph.GetNeighbors(2);
        
        Console.WriteLine($"Neighbors of vertex 0: [{string.Join(", ", neighbors0)}]");
        Console.WriteLine($"Neighbors of vertex 2: [{string.Join(", ", neighbors2)}]");
    }
}
```

### C++

```C++
\#include <iostream>
\#include <vector>
\#include <iomanip>

class AdjacencyMatrix {
private:
    std::vector<std::vector<int>> matrix;
    int numVertices;

    bool isValidVertex(int vertex) const {
        return vertex >= 0 && vertex < numVertices;
    }

public:
    AdjacencyMatrix(int numVertices) : numVertices(numVertices) {
        // Initialize matrix with zeros
        matrix.resize(numVertices, std::vector<int>(numVertices, 0));
    }

    void addEdge(int src, int dest, int weight = 1) {
        if (isValidVertex(src) && isValidVertex(dest)) {
            matrix[src][dest] = weight;
        } else {
            std::cout << "Invalid vertex index" << std::endl;
        }
    }

    void addUndirectedEdge(int src, int dest, int weight = 1) {
        addEdge(src, dest, weight);
        addEdge(dest, src, weight);
    }

    void removeEdge(int src, int dest) {
        if (isValidVertex(src) && isValidVertex(dest)) {
            matrix[src][dest] = 0;
        } else {
            std::cout << "Invalid vertex index" << std::endl;
        }
    }

    bool hasEdge(int src, int dest) const {
        if (isValidVertex(src) && isValidVertex(dest)) {
            return matrix[src][dest] != 0;
        }
        return false;
    }

    std::vector<int> getNeighbors(int vertex) const {
        std::vector<int> neighbors;
        if (isValidVertex(vertex)) {
            for (int i = 0; i < numVertices; i++) {
                if (matrix[vertex][i] != 0) {
                    neighbors.push_back(i);
                }
            }
        }
        return neighbors;
    }

    void display() const {
        std::cout << "Adjacency Matrix:" << std::endl;
        for (int i = 0; i < numVertices; i++) {
            for (int j = 0; j < numVertices; j++) {
                std::cout << std::setw(3) << matrix[i][j] << " ";
            }
            std::cout << std::endl;
        }
    }

    const std::vector<std::vector<int>>& getMatrix() const {
        return matrix;
    }

    int getNumVertices() const {
        return numVertices;
    }
};

// Example usage
int main() {
    // Create a graph with 5 vertices
    AdjacencyMatrix graph(5);
    
    // Add some edges
    graph.addEdge(0, 1, 2);
    graph.addEdge(0, 2, 3);
    graph.addEdge(1, 3, 4);
    graph.addUndirectedEdge(2, 4, 5);
    
    // Display the matrix
    graph.display();
    
    // Check for edges
    std::cout << "\nEdge from 0 to 1: " << (graph.hasEdge(0, 1) ? "true" : "false") << std::endl;
    std::cout << "Edge from 1 to 0: " << (graph.hasEdge(1, 0) ? "true" : "false") << std::endl;
    
    // Get neighbors
    auto neighbors0 = graph.getNeighbors(0);
    auto neighbors2 = graph.getNeighbors(2);
    
    std::cout << "Neighbors of vertex 0: [";
    for (size_t i = 0; i < neighbors0.size(); i++) {
        std::cout << neighbors0[i];
        if (i < neighbors0.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
    
    std::cout << "Neighbors of vertex 2: [";
    for (size_t i = 0; i < neighbors2.size(); i++) {
        std::cout << neighbors2[i];
        if (i < neighbors2.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
    
    return 0;
}
```

---