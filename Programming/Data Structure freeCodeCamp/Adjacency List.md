---
Created: 2025-08-16T09:52
tags:
  - BroCode
---
## ==What is Adjacency List==

## **Definition**

An **Adjacency List** is a way to **represent a graph** by storing **a list of adjacent vertices for each vertex**.

- Each **vertex** maintains a **list of its neighbors**.
- Efficient for **sparse graphs** where the number of edges is much less than V².

## **Features**

1. **Space-efficient:** Uses O(V + E) memory, where V = number of vertices, E = number of edges.
2. **Edge Lookup:** Slower than adjacency matrix; finding if an edge exists takes O(k), where k = number of neighbors of the vertex.
3. **Good for sparse graphs** with fewer connections.

## **Directed vs Undirected Graph**

|Type|List Representation|
|---|---|
|**Undirected**|Each edge is listed in **both vertex lists**|
|**Directed**|Edge is listed **only in the source vertex’s list**|

## **Weighted vs Unweighted Graph**

|Type|List Values|
|---|---|
|**Unweighted**|Just store neighboring vertices|
|**Weighted**|Store pairs (neighbor, weight)|

## **Example**

**Graph:**

Vertices: A, B, C

Edges: A-B, B-C

**Adjacency List:**

```Plain
A: B
B: A, C
C: B
```

**Explanation:**

- Each vertex stores its neighbors.
- Space efficient compared to adjacency matrix for sparse graphs.

## **Pros and Cons**

|Pros|Cons|
|---|---|
|Space-efficient (O(V + E))|Edge lookup slower (O(k))|
|Ideal for sparse graphs|Slightly more complex to implement|
|Easy to iterate neighbors|Not as fast for dense graphs|

---

  

## ==Where is Adjacency List used==

An **Adjacency List** is best suited for **sparse graphs** where the number of edges is much less than the square of the number of vertices.

## **1. Sparse Graphs**

- Efficient storage for graphs with relatively **few edges**.
- Example: Road maps where not every city is connected to every other city.

## **2. Graph Traversal Algorithms**

- Ideal for **DFS (Depth-First Search)** and **BFS (Breadth-First Search)**.
- Example: Traversing social networks, maze solving, or exploring connected components.

## **3. Weighted Graphs**

- Can store **weights along with neighbors**, useful for **shortest path algorithms** like Dijkstra or Bellman-Ford.

## **4. Network Graphs**

- Represent **computer networks, communication systems, or transport networks** efficiently.

## **5. Dynamic Graphs**

- Easy to **add or remove edges** without wasting memory.
- Example: Updating friendship connections in a social network.

## **Summary Table**

|Use Case|Why Adjacency List?|
|---|---|
|Sparse graphs|Saves memory (O(V + E))|
|Graph traversal (DFS, BFS)|Efficient iteration over neighbors|
|Weighted graphs|Can store edge weights|
|Network graphs|Efficient for dynamic and sparse networks|
|Dynamic graphs|Easy to add/remove edges|

---

  

## ==Complexity Analysis==

An **Adjacency List** represents a graph using **lists of neighbors for each vertex**. Its efficiency depends on the **number of vertices (V)** and **edges (E)**.

## **Space Complexity**

- **O(V + E)** → stores a list for each vertex and each edge once (or twice for undirected graphs).
- **More efficient** than adjacency matrix for **sparse graphs**.

## **Time Complexity**

|Operation|Complexity|Notes|
|---|---|---|
|**Check if edge exists (u, v)**|O(k)|k = number of neighbors of u|
|**Add an edge**|O(1)|Append to adjacency list|
|**Remove an edge**|O(k)|Need to search in the list|
|**Iterate over all neighbors of a vertex**|O(k)|Efficient|
|**Iterate over all edges**|O(V + E)|Visit all vertices and neighbors|

## **Pros**

- Space-efficient for **sparse graphs**
- Easy to iterate neighbors → good for DFS/BFS
- Supports **dynamic graph updates**

## **Cons**

- Edge lookup is **slower than adjacency matrix** (O(k))
- Slightly more complex to implement

## **Summary Table**

|Feature|Complexity / Notes|
|---|---|
|Space|O(V + E)|
|Edge existence check|O(k)|
|Add edge|O(1)|
|Remove edge|O(k)|
|Iterate neighbors|O(k)|
|Iterate all edges|O(V + E)|

---

  

## ==Code==

### Python

```Python
from collections import defaultdict

class AdjacencyList:
    def __init__(self, num_vertices=0):
        """Initialize adjacency list with given number of vertices"""
        self.num_vertices = num_vertices
        self.adj_list = defaultdict(list)
        
        # Initialize empty lists for each vertex if num_vertices is specified
        if num_vertices > 0:
            for i in range(num_vertices):
                self.adj_list[i] = []
    
    def add_vertex(self, vertex):
        """Add a new vertex to the graph"""
        if vertex not in self.adj_list:
            self.adj_list[vertex] = []
            if isinstance(vertex, int) and vertex >= self.num_vertices:
                self.num_vertices = vertex + 1
    
    def add_edge(self, src, dest, weight=1):
        """Add an edge from src to dest with optional weight"""
        # Ensure both vertices exist
        self.add_vertex(src)
        self.add_vertex(dest)
        
        # Add edge (store as tuple with destination and weight)
        self.adj_list[src].append((dest, weight))
    
    def add_undirected_edge(self, src, dest, weight=1):
        """Add an undirected edge between src and dest"""
        self.add_edge(src, dest, weight)
        self.add_edge(dest, src, weight)
    
    def remove_edge(self, src, dest):
        """Remove edge from src to dest"""
        if src in self.adj_list:
            self.adj_list[src] = [(v, w) for v, w in self.adj_list[src] if v != dest]
    
    def remove_vertex(self, vertex):
        """Remove a vertex and all its edges"""
        if vertex in self.adj_list:
            # Remove all edges pointing to this vertex
            for v in self.adj_list:
                self.adj_list[v] = [(dest, weight) for dest, weight in self.adj_list[v] if dest != vertex]
            
            # Remove the vertex itself
            del self.adj_list[vertex]
    
    def has_edge(self, src, dest):
        """Check if edge exists from src to dest"""
        if src in self.adj_list:
            return any(v == dest for v, w in self.adj_list[src])
        return False
    
    def get_neighbors(self, vertex):
        """Get all neighbors of a vertex (returns list of vertices)"""
        if vertex in self.adj_list:
            return [dest for dest, weight in self.adj_list[vertex]]
        return []
    
    def get_weighted_neighbors(self, vertex):
        """Get all neighbors with weights (returns list of tuples)"""
        if vertex in self.adj_list:
            return self.adj_list[vertex].copy()
        return []
    
    def get_edge_weight(self, src, dest):
        """Get weight of edge from src to dest"""
        if src in self.adj_list:
            for v, w in self.adj_list[src]:
                if v == dest:
                    return w
        return None
    
    def get_vertices(self):
        """Get all vertices in the graph"""
        return list(self.adj_list.keys())
    
    def get_edges(self):
        """Get all edges in the graph as list of tuples (src, dest, weight)"""
        edges = []
        for src in self.adj_list:
            for dest, weight in self.adj_list[src]:
                edges.append((src, dest, weight))
        return edges
    
    def display(self):
        """Display the adjacency list"""
        print("Adjacency List:")
        for vertex in sorted(self.adj_list.keys()):
            neighbors = self.adj_list[vertex]
            if neighbors:
                neighbor_str = ", ".join(f"{dest}(w:{weight})" for dest, weight in neighbors)
                print(f"  {vertex} -> [{neighbor_str}]")
            else:
                print(f"  {vertex} -> []")
    
    def get_degree(self, vertex):
        """Get the degree (number of outgoing edges) of a vertex"""
        if vertex in self.adj_list:
            return len(self.adj_list[vertex])
        return 0

# Example usage
if __name__ == "__main__":
    # Create a graph
    graph = AdjacencyList()
    
    # Add some edges
    graph.add_edge(0, 1, 2)
    graph.add_edge(0, 2, 3)
    graph.add_edge(1, 3, 4)
    graph.add_edge(2, 1, 1)
    graph.add_undirected_edge(2, 4, 5)
    graph.add_edge(4, 0, 2)
    
    # Display the graph
    graph.display()
    
    # Check for edges
    print(f"\nEdge from 0 to 1: {graph.has_edge(0, 1)}")
    print(f"Edge from 1 to 0: {graph.has_edge(1, 0)}")
    print(f"Weight of edge 0->1: {graph.get_edge_weight(0, 1)}")
    
    # Get neighbors
    print(f"Neighbors of vertex 0: {graph.get_neighbors(0)}")
    print(f"Weighted neighbors of vertex 2: {graph.get_weighted_neighbors(2)}")
    
    # Graph statistics
    print(f"All vertices: {graph.get_vertices()}")
    print(f"All edges: {graph.get_edges()}")
    print(f"Degree of vertex 0: {graph.get_degree(0)}")
```

### C#

```C#
using System;
using System.Collections.Generic;
using System.Linq;

public class Edge
{
    public int Destination { get; set; }
    public int Weight { get; set; }
    
    public Edge(int destination, int weight = 1)
    {
        Destination = destination;
        Weight = weight;
    }
    
    public override string ToString()
    {
        return $"{Destination}(w:{Weight})";
    }
}

public class AdjacencyList
{
    private Dictionary<int, List<Edge>> adjList;
    
    public AdjacencyList()
    {
        adjList = new Dictionary<int, List<Edge>>();
    }
    
    public void AddVertex(int vertex)
    {
        if (!adjList.ContainsKey(vertex))
        {
            adjList[vertex] = new List<Edge>();
        }
    }
    
    public void AddEdge(int src, int dest, int weight = 1)
    {
        // Ensure both vertices exist
        AddVertex(src);
        AddVertex(dest);
        
        // Add edge
        adjList[src].Add(new Edge(dest, weight));
    }
    
    public void AddUndirectedEdge(int src, int dest, int weight = 1)
    {
        AddEdge(src, dest, weight);
        AddEdge(dest, src, weight);
    }
    
    public void RemoveEdge(int src, int dest)
    {
        if (adjList.ContainsKey(src))
        {
            adjList[src].RemoveAll(edge => edge.Destination == dest);
        }
    }
    
    public void RemoveVertex(int vertex)
    {
        if (adjList.ContainsKey(vertex))
        {
            // Remove all edges pointing to this vertex
            foreach (var kvp in adjList)
            {
                kvp.Value.RemoveAll(edge => edge.Destination == vertex);
            }
            
            // Remove the vertex itself
            adjList.Remove(vertex);
        }
    }
    
    public bool HasEdge(int src, int dest)
    {
        if (adjList.ContainsKey(src))
        {
            return adjList[src].Any(edge => edge.Destination == dest);
        }
        return false;
    }
    
    public List<int> GetNeighbors(int vertex)
    {
        if (adjList.ContainsKey(vertex))
        {
            return adjList[vertex].Select(edge => edge.Destination).ToList();
        }
        return new List<int>();
    }
    
    public List<Edge> GetWeightedNeighbors(int vertex)
    {
        if (adjList.ContainsKey(vertex))
        {
            return new List<Edge>(adjList[vertex]);
        }
        return new List<Edge>();
    }
    
    public int? GetEdgeWeight(int src, int dest)
    {
        if (adjList.ContainsKey(src))
        {
            var edge = adjList[src].FirstOrDefault(e => e.Destination == dest);
            return edge?.Weight;
        }
        return null;
    }
    
    public List<int> GetVertices()
    {
        return adjList.Keys.OrderBy(x => x).ToList();
    }
    
    public List<(int src, int dest, int weight)> GetEdges()
    {
        var edges = new List<(int, int, int)>();
        foreach (var kvp in adjList)
        {
            foreach (var edge in kvp.Value)
            {
                edges.Add((kvp.Key, edge.Destination, edge.Weight));
            }
        }
        return edges;
    }
    
    public void Display()
    {
        Console.WriteLine("Adjacency List:");
        var sortedVertices = adjList.Keys.OrderBy(x => x);
        
        foreach (var vertex in sortedVertices)
        {
            var neighbors = adjList[vertex];
            if (neighbors.Count > 0)
            {
                var neighborStr = string.Join(", ", neighbors);
                Console.WriteLine($"  {vertex} -> [{neighborStr}]");
            }
            else
            {
                Console.WriteLine($"  {vertex} -> []");
            }
        }
    }
    
    public int GetDegree(int vertex)
    {
        if (adjList.ContainsKey(vertex))
        {
            return adjList[vertex].Count;
        }
        return 0;
    }
    
    public int VertexCount => adjList.Count;
    
    public int EdgeCount => adjList.Values.Sum(list => list.Count);
}

// Example usage
class Program
{
    static void Main(string[] args)
    {
        // Create a graph
        AdjacencyList graph = new AdjacencyList();
        
        // Add some edges
        graph.AddEdge(0, 1, 2);
        graph.AddEdge(0, 2, 3);
        graph.AddEdge(1, 3, 4);
        graph.AddEdge(2, 1, 1);
        graph.AddUndirectedEdge(2, 4, 5);
        graph.AddEdge(4, 0, 2);
        
        // Display the graph
        graph.Display();
        
        // Check for edges
        Console.WriteLine($"\nEdge from 0 to 1: {graph.HasEdge(0, 1)}");
        Console.WriteLine($"Edge from 1 to 0: {graph.HasEdge(1, 0)}");
        Console.WriteLine($"Weight of edge 0->1: {graph.GetEdgeWeight(0, 1)}");
        
        // Get neighbors
        var neighbors0 = graph.GetNeighbors(0);
        var weightedNeighbors2 = graph.GetWeightedNeighbors(2);
        
        Console.WriteLine($"Neighbors of vertex 0: [{string.Join(", ", neighbors0)}]");
        Console.WriteLine($"Weighted neighbors of vertex 2: [{string.Join(", ", weightedNeighbors2)}]");
        
        // Graph statistics
        var vertices = graph.GetVertices();
        var edges = graph.GetEdges();
        
        Console.WriteLine($"All vertices: [{string.Join(", ", vertices)}]");
        Console.WriteLine($"All edges: [{string.Join(", ", edges.Select(e => $"({e.src}->{e.dest}, w:{e.weight})"))}]");
        Console.WriteLine($"Degree of vertex 0: {graph.GetDegree(0)}");
        Console.WriteLine($"Total vertices: {graph.VertexCount}, Total edges: {graph.EdgeCount}");
    }
}
```

### C++

```C++
\#include <iostream>
\#include <vector>
\#include <unordered_map>
\#include <algorithm>
\#include <utility>

struct Edge {
    int destination;
    int weight;
    
    Edge(int dest, int w = 1) : destination(dest), weight(w) {}
    
    bool operator==(const Edge& other) const {
        return destination == other.destination;
    }
};

class AdjacencyList {
private:
    std::unordered_map<int, std::vector<Edge>> adjList;

public:
    AdjacencyList() = default;
    
    void addVertex(int vertex) {
        if (adjList.find(vertex) == adjList.end()) {
            adjList[vertex] = std::vector<Edge>();
        }
    }
    
    void addEdge(int src, int dest, int weight = 1) {
        // Ensure both vertices exist
        addVertex(src);
        addVertex(dest);
        
        // Add edge
        adjList[src].emplace_back(dest, weight);
    }
    
    void addUndirectedEdge(int src, int dest, int weight = 1) {
        addEdge(src, dest, weight);
        addEdge(dest, src, weight);
    }
    
    void removeEdge(int src, int dest) {
        auto it = adjList.find(src);
        if (it != adjList.end()) {
            auto& edges = it->second;
            edges.erase(
                std::remove_if(edges.begin(), edges.end(),
                    [dest](const Edge& edge) { return edge.destination == dest; }),
                edges.end()
            );
        }
    }
    
    void removeVertex(int vertex) {
        auto it = adjList.find(vertex);
        if (it != adjList.end()) {
            // Remove all edges pointing to this vertex
            for (auto& pair : adjList) {
                auto& edges = pair.second;
                edges.erase(
                    std::remove_if(edges.begin(), edges.end(),
                        [vertex](const Edge& edge) { return edge.destination == vertex; }),
                    edges.end()
                );
            }
            
            // Remove the vertex itself
            adjList.erase(it);
        }
    }
    
    bool hasEdge(int src, int dest) const {
        auto it = adjList.find(src);
        if (it != adjList.end()) {
            const auto& edges = it->second;
            return std::any_of(edges.begin(), edges.end(),
                [dest](const Edge& edge) { return edge.destination == dest; });
        }
        return false;
    }
    
    std::vector<int> getNeighbors(int vertex) const {
        std::vector<int> neighbors;
        auto it = adjList.find(vertex);
        if (it != adjList.end()) {
            for (const auto& edge : it->second) {
                neighbors.push_back(edge.destination);
            }
        }
        return neighbors;
    }
    
    std::vector<Edge> getWeightedNeighbors(int vertex) const {
        auto it = adjList.find(vertex);
        if (it != adjList.end()) {
            return it->second;
        }
        return std::vector<Edge>();
    }
    
    int getEdgeWeight(int src, int dest) const {
        auto it = adjList.find(src);
        if (it != adjList.end()) {
            const auto& edges = it->second;
            auto edgeIt = std::find_if(edges.begin(), edges.end(),
                [dest](const Edge& edge) { return edge.destination == dest; });
            if (edgeIt != edges.end()) {
                return edgeIt->weight;
            }
        }
        return -1; // Return -1 if edge not found
    }
    
    std::vector<int> getVertices() const {
        std::vector<int> vertices;
        for (const auto& pair : adjList) {
            vertices.push_back(pair.first);
        }
        std::sort(vertices.begin(), vertices.end());
        return vertices;
    }
    
    std::vector<std::tuple<int, int, int>> getEdges() const {
        std::vector<std::tuple<int, int, int>> edges;
        for (const auto& pair : adjList) {
            int src = pair.first;
            for (const auto& edge : pair.second) {
                edges.emplace_back(src, edge.destination, edge.weight);
            }
        }
        return edges;
    }
    
    void display() const {
        std::cout << "Adjacency List:" << std::endl;
        
        // Get sorted vertices for consistent output
        auto vertices = getVertices();
        
        for (int vertex : vertices) {
            auto it = adjList.find(vertex);
            if (it != adjList.end()) {
                const auto& neighbors = it->second;
                std::cout << "  " << vertex << " -> [";
                
                for (size_t i = 0; i < neighbors.size(); ++i) {
                    std::cout << neighbors[i].destination << "(w:" << neighbors[i].weight << ")";
                    if (i < neighbors.size() - 1) {
                        std::cout << ", ";
                    }
                }
                std::cout << "]" << std::endl;
            }
        }
    }
    
    int getDegree(int vertex) const {
        auto it = adjList.find(vertex);
        if (it != adjList.end()) {
            return static_cast<int>(it->second.size());
        }
        return 0;
    }
    
    size_t getVertexCount() const {
        return adjList.size();
    }
    
    size_t getEdgeCount() const {
        size_t count = 0;
        for (const auto& pair : adjList) {
            count += pair.second.size();
        }
        return count;
    }
};

// Example usage
int main() {
    // Create a graph
    AdjacencyList graph;
    
    // Add some edges
    graph.addEdge(0, 1, 2);
    graph.addEdge(0, 2, 3);
    graph.addEdge(1, 3, 4);
    graph.addEdge(2, 1, 1);
    graph.addUndirectedEdge(2, 4, 5);
    graph.addEdge(4, 0, 2);
    
    // Display the graph
    graph.display();
    
    // Check for edges
    std::cout << "\nEdge from 0 to 1: " << (graph.hasEdge(0, 1) ? "true" : "false") << std::endl;
    std::cout << "Edge from 1 to 0: " << (graph.hasEdge(1, 0) ? "true" : "false") << std::endl;
    std::cout << "Weight of edge 0->1: " << graph.getEdgeWeight(0, 1) << std::endl;
    
    // Get neighbors
    auto neighbors0 = graph.getNeighbors(0);
    auto weightedNeighbors2 = graph.getWeightedNeighbors(2);
    
    std::cout << "Neighbors of vertex 0: [";
    for (size_t i = 0; i < neighbors0.size(); ++i) {
        std::cout << neighbors0[i];
        if (i < neighbors0.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
    
    std::cout << "Weighted neighbors of vertex 2: [";
    for (size_t i = 0; i < weightedNeighbors2.size(); ++i) {
        std::cout << weightedNeighbors2[i].destination << "(w:" << weightedNeighbors2[i].weight << ")";
        if (i < weightedNeighbors2.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
    
    // Graph statistics
    auto vertices = graph.getVertices();
    auto edges = graph.getEdges();
    
    std::cout << "All vertices: [";
    for (size_t i = 0; i < vertices.size(); ++i) {
        std::cout << vertices[i];
        if (i < vertices.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
    
    std::cout << "All edges: [";
    for (size_t i = 0; i < edges.size(); ++i) {
        auto [src, dest, weight] = edges[i];
        std::cout << "(" << src << "->" << dest << ", w:" << weight << ")";
        if (i < edges.size() - 1) std::cout << ", ";
    }
    std::cout << "]" << std::endl;
    
    std::cout << "Degree of vertex 0: " << graph.getDegree(0) << std::endl;
    std::cout << "Total vertices: " << graph.getVertexCount() << ", Total edges: " << graph.getEdgeCount() << std::endl;
    
    return 0;
}
```

---