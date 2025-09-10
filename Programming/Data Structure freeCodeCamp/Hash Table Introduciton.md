---
Created: 2025-08-11T11:58
tags:
  - William-Fiset
---
# ==Discussion==

---

## ==Hash Table 🗂️==

## Definition

A **hash table** is a data structure that stores key-value pairs and allows for fast data retrieval based on keys. It uses a **hash function** to convert keys into indices of an underlying array, enabling efficient insertions, deletions, and lookups.

## Key Concepts

- **Key-value storage:** Data is stored as pairs, where each unique key maps to a value.
- **Hash function:** A function that takes a key and returns an integer index (hash code) to locate where the value is stored in the array.
- **Collision:** Occurs when two keys produce the same hash code or index.
- **Collision resolution:** Techniques like chaining or open addressing handle collisions to avoid data loss.

## How It Works

1. When inserting a key-value pair, the key is processed by the hash function.
2. The hash function returns an index in the array.
3. The value is stored at that index.
4. When retrieving a value by key, the same hash function is applied to the key to find the index, then the value is returned.
5. If a collision occurs, the hash table uses a collision resolution method to store or find the correct value.

## Properties / Characteristics

- **Average case complexity:**
    - Insertion: O(1)
    - Lookup: O(1)
    - Deletion: O(1)
- **Worst case complexity:** O(n), happens if many collisions occur and resolution degenerates.
- **Space efficient:** Uses an array and requires enough space to keep collisions low.
- **Depends on hash function quality:** A good hash function distributes keys uniformly.

## Common Collision Resolution Methods

- **Chaining:** Store collided elements in a linked list at the array index.
- **Open addressing:** Find another open slot in the array by probing (linear, quadratic, or double hashing).

## Use Cases

- Implementing dictionaries or maps in programming languages.
- Caching data for quick access.
- Database indexing.
- Sets to quickly check for element existence.

---

  

## ==What is a Hash Function==

## Definition

A **hash function** is a function that takes an input (key) and returns a fixed-size integer, called the **hash code** or **hash value**.

This hash value determines the index where the key–value pair will be stored in a **hash table**.

## Key Concepts

- **Deterministic**: Same input always produces the same output.
- **Fixed Range**: Hash values are mapped within the range of table indices (0 to table_size-1).
- **Uniform Distribution**: Good hash functions spread keys evenly across the table to minimize collisions.
- **Efficiency**: Should compute hash values quickly, even for large inputs.

## How It Works

1. The key (e.g., number, string) is processed by a hash function.
2. The hash function outputs an integer (hash code).
3. The hash code is reduced using modulus (`% table_size`) to find the **table index**.
4. The data is stored at that index in the hash table.

Example:

```Plain
hash(25) = 25 % 7 = 4 → Store at index 4
```

## Properties of a Good Hash Function

- **Minimizes Collisions**: Different keys rarely map to the same index.
- **Fast to Compute**: Should be O(1) time complexity.
- **Uniform Output**: Keys should be evenly distributed.
- **Stable**: Small changes in input can change the hash value significantly (helps spread keys).

## Use Cases

- **Hash Tables / Hash Maps** (fast lookups)
- **Cryptography** (password storage, digital signatures)
- **Data Integrity** (checksums)
- **Caching** (quick retrieval)

## Summary Table

|Property|Purpose|
|---|---|
|Deterministic|Same key → same hash value|
|Uniformity|Spread keys evenly|
|Efficiency|O(1) computation time|
|Low collisions|Improves performance of hash table|

---

  

## ==Properties of a Hash Function 🔑==

## Definition

A **hash function** is a function that takes an input (or "key") and returns a fixed-size string of bytes, typically an integer called the **hash code** or **hash value**, which is used as an index in a hash table.

## Key Properties

To be effective in a hash table, a hash function should have the following properties:

### 1. Deterministic

- The same input key must always produce the **same hash value**.
- This ensures consistent storage and retrieval.

### 2. Uniform Distribution

- The hash function should distribute keys **uniformly** across the hash table to minimize collisions.
- A good hash function spreads keys evenly to avoid clustering in certain indices.

### 3. Fast Computation

- The function should be **computationally efficient** to compute the hash value quickly, keeping insertions and lookups fast.

### 4. Minimize Collisions

- Different keys should ideally produce **different hash values** to avoid collisions.
- While collisions are sometimes unavoidable, a good hash function minimizes their occurrence.

### 5. Avalanche Effect

- A small change in the input key should produce a significant and unpredictable change in the output hash value.
- This reduces patterns that cause clustering.

### 6. Preimage Resistance (more important in cryptographic hash functions)

- Given a hash value, it should be **difficult to reverse-engineer** the original input key.

## Summary Table

|Property|Description|
|---|---|
|Deterministic|Same input → same output|
|Uniform Distribution|Evenly spreads keys across indices|
|Fast Computation|Quickly computes hash values|
|Minimize Collisions|Reduces chances of different keys sharing the same hash|
|Avalanche Effect|Small input changes cause large output changes|
|Preimage Resistance|Hard to find original key from hash (cryptography)|

---

  

## ==Collision Resolution Methods ⚡==

## Definition

**Collision resolution methods** are techniques used in a hash table to handle cases when two or more keys produce the same hash index (collision). Since collisions are inevitable in most hash table implementations, these methods ensure that all elements can still be stored and retrieved correctly.

## Types of Collision Resolution

### **1. Separate Chaining (Closed Addressing)**

- **How it works:** Each array index holds a linked list (or another secondary structure) of key-value pairs that share the same hash index.
- **Process:** When a collision occurs, the new key-value pair is simply appended to the list at that index.
- **Pros:**
    - Easy to implement.
    - Table can store more elements than its array size.
- **Cons:**
    - Requires extra memory for linked lists.
    - Performance degrades to O(n) if many collisions happen at the same index.

### **2. Open Addressing (Closed Hashing)**

- **How it works:** All elements are stored directly in the hash table array. If a collision happens, the algorithm searches for the next available slot.
- **Common probing techniques:**

### a) **Linear Probing**

- Move sequentially (index + 1, +2, ...) until an empty slot is found.
- **Pros:** Simple to implement.
- **Cons:** Can cause **primary clustering** (large blocks of filled slots).

### b) **Quadratic Probing**

- Probe at intervals of `i²` (e.g., +1, +4, +9, ...) from the original index.
- **Pros:** Reduces primary clustering.
- **Cons:** Can still suffer from **secondary clustering** (collisions among keys with same initial index).

### c) **Double Hashing**

- Use a second hash function to determine the probing step size.
- **Pros:** Best at avoiding clustering.
- **Cons:** Slightly more complex to implement.

### **3. Cuckoo Hashing**

- **How it works:** Uses two hash functions and two tables. If the desired spot is occupied, the existing element is moved to its alternative position, potentially causing a chain reaction.
- **Pros:** O(1) lookups, no clustering.
- **Cons:** Can require rehashing if loops form.

## Summary Table

|Method|Idea|Pros|Cons|
|---|---|---|---|
|Separate Chaining|Linked list at each index|Simple, dynamic storage|Extra memory, possible O(n) time|
|Linear Probing|Search next sequential slot|Easy to implement|Primary clustering|
|Quadratic Probing|Search using square offsets|Less clustering than linear|Secondary clustering possible|
|Double Hashing|Second hash determines step size|Minimizes clustering|More complex, needs good hash fn|
|Cuckoo Hashing|Two hash tables, displacement method|Constant-time lookups|May require rehashing|

---

  

## ==Collision Resolution Method: Separate Chaining ⛓️==

## Definition

**Separate Chaining** (also called **Closed Addressing**) is a collision resolution method in which each index of the hash table stores a **linked list** (or another secondary data structure) containing all key-value pairs that hash to the same index.

## How It Works

1. The key is passed through a **hash function** to get the index.
2. If the index is empty, insert the key-value pair directly.
3. If the index already has one or more elements, append the new key-value pair to the linked list at that index.
4. To search for a key, go to the index from the hash function and traverse the linked list.

## Example

Suppose we have a hash table of size 5 and hash function:

`hash(key) = key % 5`

|Key|Hash|Index|Stored in List at Index|
|---|---|---|---|
|12|2|2|[12]|
|22|2|2|[12, 22]|
|32|2|2|[12, 22, 32]|

Here, all keys produce the same hash index (2), so they are stored in the linked list at index 2.

## Advantages

- Simple to implement.
- Can store more elements than the hash table’s array size.
- Easy to handle **dynamic growth** (linked lists grow as needed).

## Disadvantages

- Requires extra memory for storing pointers in the linked list.
- If too many collisions occur, search time can degrade to **O(n)**.
- Cache performance is worse compared to open addressing because linked list nodes may be scattered in memory.

## Time Complexity

|Operation|Average Case|Worst Case|
|---|---|---|
|Search|O(1)|O(n)|
|Insert|O(1)|O(n)|
|Delete|O(1)|O(n)|

---

  

## ==Collision Resolution Method: Open Addressing 🔍==

## Definition

**Open Addressing** (also called **Closed Hashing**) is a collision resolution method where **all elements are stored directly in the hash table array itself**. When a collision occurs, the algorithm searches for the **next available slot** in the array using a probing sequence until an empty spot is found.

## How It Works

1. The key is passed through a **hash function** to get the index.
2. If the index is empty, store the key-value pair there.
3. If the index is already occupied (collision), search for the next empty slot based on a **probing strategy**.
4. To search for a key, follow the same probing sequence until the key is found or an empty slot is encountered.

## Common Probing Strategies

### **1. Linear Probing**

- **Idea:** Move sequentially (`+1, +2, +3, ...`) until an empty slot is found.
- **Formula:**
    
    ```Plain
    index = (hash(key) + i) % table_size
    ```
    
- **Pros:** Easy to implement.
- **Cons:** Suffers from **primary clustering** (groups of filled slots form, causing longer searches).

### **2. Quadratic Probing**

- **Idea:** Check slots at intervals of perfect squares (`+1², +2², +3², ...`) from the original index.
- **Formula:**
    
    ```Plain
    index = (hash(key) + i²) % table_size
    ```
    
- **Pros:** Reduces primary clustering compared to linear probing.
- **Cons:** Still susceptible to **secondary clustering** (keys with same starting index follow same sequence).

### **3. Double Hashing**

- **Idea:** Use a second hash function to determine the probing step size.
- **Formula:**
    
    ```Plain
    index = (hash1(key) + i * hash2(key)) % table_size
    ```
    
- **Pros:** Minimizes clustering and distributes keys more evenly.
- **Cons:** Requires two good hash functions; slightly more complex.

## Advantages

- No extra memory for linked lists or secondary structures.
- Cache-friendly since data is stored in a contiguous array.

## Disadvantages

- Table must have enough empty space to avoid excessive probing.
- Performance degrades when **load factor** (elements/table size) is high.
- Deletion can be tricky (often requires marking deleted slots as "tombstones").

## Time Complexity

|Operation|Average Case|Worst Case|
|---|---|---|
|Search|O(1)|O(n)|
|Insert|O(1)|O(n)|
|Delete|O(1)|O(n)|

---

  

## ==Hash Table – Complexity Analysis 📊==

## Definition

A **hash table** is a key-value data structure that provides average constant-time performance for insertion, deletion, and search by using a **hash function** to map keys to indices in an array.

The complexity depends on factors like **hash function quality**, **collision resolution method**, and **load factor**.

## Key Terms for Complexity Analysis

- **n:** Number of elements stored in the hash table.
- **m:** Number of slots (size of the hash table array).
- **Load Factor (a)**
    
    $$α=m / n$$
    
    Measures how full the table is; higher values mean more collisions.
    

## Time Complexity

|Operation|Average Case|Worst Case|Notes|
|---|---|---|---|
|**Search**|O(1)|O(n)|Worst case happens when all elements end up in the same slot (poor hash function or high load factor).|
|**Insert**|O(1)|O(n)|In worst case, finding a place for new data may require checking all slots (open addressing) or traversing a long chain (separate chaining).|
|**Delete**|O(1)|O(n)|Deletion may require searching first; worst case occurs with excessive collisions.|

## Space Complexity

|Case|Complexity|Notes|
|---|---|---|
|**Overall**|O(m + n)|Needs space for the table array (m) and possibly extra structures (e.g., linked lists in separate chaining).|

## Factors Affecting Performance

1. **Hash Function Quality**
    - Good hash function → uniform distribution → minimal collisions → near O(1) performance.
    - Poor hash function → clustering → more collisions → degraded performance.
2. **Collision Resolution Method**
    - Separate chaining → performance depends on chain length.
    - Open addressing → performance drops as load factor approaches 1.
3. **Load Factor (α)**
    - Keep **α ≤ 0.75** for good performance (common in many implementations like Java’s `HashMap`).
    - If α gets too high, **rehashing** (resizing and reinserting elements) is often used.

## Complexity Summary Table

|Operation|Average Case|Worst Case|Space Complexity|
|---|---|---|---|
|Search|O(1)|O(n)|O(m + n)|
|Insert|O(1)|O(n)|O(m + n)|
|Delete|O(1)|O(n)|O(m + n)|

---

# ==Separate Chaining Implementation Details==

---

  

## ==Separate Chaining – Linked List Approach Overview ⛓️==

## Definition

In **Separate Chaining** using a **Linked List**, each index of the hash table contains a pointer to a linked list that holds **all key-value pairs** that hash to the same index. This approach is the most common way to implement separate chaining because linked lists allow **dynamic growth** and efficient insertion at the head or tail.

## How It Works

1. **Hashing the Key**
    - Use a hash function to compute the index
        
        $$index=hash(key)modTableSize$$
        
2. **Insertion**
    - If the index is empty, create a new linked list and insert the key-value pair.
    - If the index already contains a linked list, append or prepend the new node to it.
3. **Search**
    - Compute the index using the hash function.
    - Traverse the linked list at that index until the key is found or the list ends.
4. **Deletion**
    - Compute the index using the hash function.
    - Search the linked list and remove the node containing the key.
    - If the linked list becomes empty, free it or mark it as null.

## Advantages

- **Dynamic growth:** Linked lists can grow as needed without resizing the hash table.
- **Simple collision handling:** No probing logic required.
- **Easy deletion:** Removing a node from a linked list is straightforward.

## Disadvantages

- Requires **extra memory** for node pointers.
- Poor cache performance since linked list nodes may be scattered in memory.
- Worst-case search time is **O(n)** if many keys hash to the same index.

## Example Structure (Node)

### **Pseudocode**

```Plain
Node:
    key
    value
    next  // pointer to the next node in the list
```

### **Table Representation**

```Plain
Index 0: NULL
Index 1: (key1, val1) → (key2, val2) → NULL
Index 2: NULL
Index 3: (key3, val3) → NULL
...
```

## Time Complexity

|Operation|Average Case|Worst Case|
|---|---|---|
|Search|O(1)|O(n)|
|Insert|O(1)|O(n)|
|Delete|O(1)|O(n)|

---

  

## ==Separate Chaining FAQs ❓⛓️==

### 1. **What is separate chaining in hash tables?**

Separate chaining is a collision resolution technique where each slot in the hash table stores a linked list (or another secondary data structure) of all elements whose keys hash to that slot. It handles collisions by keeping multiple elements in the same bucket.

### 2. **Why use separate chaining instead of open addressing?**

Separate chaining allows the hash table to store more elements than its size since each bucket can grow dynamically. It is also simpler to implement deletion and avoids clustering issues common in open addressing.

### 3. **What happens if many keys hash to the same index?**

All those keys are stored in the linked list at that index. If the list becomes long, operations like search, insert, and delete degrade to O(n) time complexity in the worst case.

### 4. **How does separate chaining affect space complexity?**

It requires extra space for pointers in the linked lists. Therefore, the space complexity is O(m + n), where m is the size of the hash table array and n is the number of elements stored.

### 5. **Can separate chaining handle dynamic resizing?**

Yes. When the load factor becomes too high, the hash table can be resized by creating a larger array and rehashing all existing elements into the new table.

### 6. **Is separate chaining cache-friendly?**

No. Linked lists may be scattered in memory, which results in poor cache performance compared to open addressing where elements are stored contiguously.

### 7. **How to choose between separate chaining and open addressing?**

- Use **separate chaining** when:
    - You expect many collisions or a high load factor.
    - Easy deletion is needed.
    - Dynamic resizing without rehashing is desired.
- Use **open addressing** when:
    - Memory overhead needs to be minimal.
    - Cache performance is critical.

### 8. **Can other data structures replace linked lists in separate chaining?**

Yes. Balanced trees, dynamic arrays, or other structures can replace linked lists for better worst-case performance, but linked lists are simplest and most common.

### 9. **What is the average length of a chain in separate chaining?**

It is approximately equal to the load factor α=n/m . Keeping α\alphaα low ensures short chains and efficient operations.

### 10. **Does separate chaining guarantee O(1) time complexity?**

No. Average case is O(1) assuming a good hash function and low load factor, but worst case can degrade to O(n) if many keys collide.

### FreeCodeCamp

==Q:== How do i maintain O(1) insertion and lookup time complexity once my HT gets really full and i have a long linkedl ist chains

==A:== Once the HT contains s lot of elements you should create an HT with a larger capacity and rehash all the item inside the old HT and disperse them throughout the new HT at different locations

---

==Q:== How do i remove key-value pairs from my HT

==A:== Apply the same procedure as doing a lookup for a key, but this time instead of returning the value associated with the key remove the node in the linked list data structure

---

==Q:== Can i use another data structure to model the bucket behavior required for the separate chaining method

==A:== Of Course! Common data structure used instead of linked list include: arrays, binary tress, self balancing trees, etc… You can even go with a hybrid approach like Java’s HashMap. However, note that some of these are much more memory intensive and complex to implement than a simple linked list which is why they are less popular.

---

  

  

---

## ==Code Implementation==

#### Code

|Name|Created|Tags|
|---|---|---|
|[[Python Separate Chaining]]|August 12, 2025 8:45 AM||
|[[C Separate Chaining]]|August 12, 2025 8:45 AM||
|[[C++ Separate Chaining]]|August 12, 2025 8:45 AM||

  
  

---

# ==Open addressing technique implementation details==

---

#### Open addressing technique

|Name|Created|Tags|
|---|---|---|
|[[Linear Probing]]|August 12, 2025 8:51 AM||
|[[Quadratic Probing]]|August 12, 2025 8:51 AM||
|[[Double Hashing]]|August 12, 2025 8:52 AM||
|[[Removing Elements]]|August 12, 2025 8:52 AM||

  
  

---

# ==Code implementation==

---

#### Linear, Quadratic, Double Hash

|Name|Created|Tags|
|---|---|---|
|[[Python Open Addressing]]|August 14, 2025 3:05 PM||
|[[C Open Addressing]]|August 14, 2025 3:05 PM||
|[[C++ Open Addressing]]|August 14, 2025 3:05 PM||

  
  

---