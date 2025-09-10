---
Created: 2025-08-16T09:52
tags:
  - BroCode
---
## ==What is a Graph==

## **Definition**

A **graph** is a **non-linear data structure** that consists of:

1. **Vertices (Nodes):** Fundamental units representing entities.
2. **Edges (Links):** Connections between pairs of vertices representing relationships.

Graphs are used to model relationships between objects in many real-world problems.

## **Types of Graphs**

### **1. Directed Graph (Digraph)**

- Edges have a **direction** (from one vertex to another).
- Example: Twitter follower relationships, where “A follows B” is not the same as “B follows A”.

### **2. Undirected Graph**

- Edges have **no direction**.
- Example: Facebook friendship, where friendship is mutual.

### **3. Weighted Graph**

- Edges carry a **weight or cost**.
- Example: Distance between cities in a map.

### **4. Unweighted Graph**

- Edges **do not have weights**.
- Example: Social network connections without any measure of closeness.

## **Graph Representations**

1. **Adjacency Matrix**
    - A 2D array where `matrix[i][j] = 1` (or weight) if there is an edge between vertex `i` and `j`.
    - Pros: Fast edge lookup
    - Cons: Takes O(V²) space
2. **Adjacency List**
    - Each vertex stores a list of adjacent vertices.
    - Pros: Space efficient for sparse graphs
    - Cons: Slower edge lookup

## **Applications of Graphs**

- Social networks (friends/followers)
- Maps and navigation (shortest path, distances)
- Web page linking (PageRank algorithm)
- Network routing (Internet, telephone networks)
- Task scheduling (dependency graphs)

## **Summary Table**

|Feature|Description|
|---|---|
|Vertices (Nodes)|Fundamental units|
|Edges (Links)|Connections between nodes|
|Types|Directed, Undirected, Weighted, Unweighted|
|Representations|Adjacency Matrix, Adjacency List|
|Applications|Social networks, navigation, scheduling, networking|

---

  

## ==Where do you use a Graph==

Graphs are widely used to represent **relationships between entities** in various domains.

## **1. Social Networks**

- Represent **users as vertices** and **friendships/follows as edges**.
- Example: Facebook friends, Twitter followers.

## **2. Maps and Navigation**

- Cities or locations as **vertices**, roads or paths as **edges** with weights (distance, time).
- Used in **shortest path algorithms** like Dijkstra or A*.

## **3. Network Routing**

- Computers, routers, or servers as **vertices**, network connections as **edges**.
- Used for **optimizing data flow** and avoiding congestion.

## **4. Web Page Linking**

- Web pages as **vertices**, hyperlinks as **edges**.
- Example: **Google PageRank** algorithm for ranking pages.
    
    ## **5. Dependency Management**
    
    - Tasks or projects as **vertices**, dependencies as **edges**.
    - Example: **Task scheduling**, course prerequisites, build systems.

## **6. AI and Games**

- Graphs represent **game states** or **search spaces**.
- Example: Chess moves, puzzle solving, shortest path in game maps.

## **7. Resource Allocation**

- Vertices represent **resources or jobs**, edges represent **assignments**.
- Example: Matching algorithms, flow networks.

## **Summary Table**

|Domain|Graph Usage|
|---|---|
|Social Networks|Users & connections|
|Maps & Navigation|Locations & routes|
|Network Routing|Computers/routers & connections|
|Web Linking|Pages & hyperlinks|
|Dependency Management|Tasks & prerequisites|
|AI & Games|States & moves|
|Resource Allocation|Jobs & resources|

---