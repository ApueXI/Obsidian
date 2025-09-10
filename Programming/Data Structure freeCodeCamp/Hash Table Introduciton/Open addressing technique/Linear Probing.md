---
Created: 2025-08-12T08:51
---
# ==Linear Probing==

---

  

## ==What is Linear Probing==

## Definition

**Linear probing** is a collision resolution technique used in open addressing hash tables. When a collision occurs (i.e., when a hash index is already occupied), linear probing searches for the next available slot by checking the following slots sequentially (one by one) until an empty slot is found.

## How It Works

1. Compute the hash index of the key.
2. If the slot at that index is empty, insert the key-value pair there.
3. If the slot is occupied (collision), check the next slot (index + 1).
4. Continue checking slots sequentially (wrapping around to the start if needed) until an empty slot is found.
5. Insert the key-value pair in the first available slot.

## Formula

For the _i_th probe, the index checked is:

$$index=(hash(key)+i)modTableSize$$

  

## Advantages

- Simple and easy to implement.
- Uses contiguous memory which improves cache performance.

## Disadvantages

- Can cause **primary clustering**: consecutive occupied slots form clusters, which increase the average search time.
- Performance degrades significantly at high load factors.

## Time Complexity

|Operation|Average Case|Worst Case|
|---|---|---|
|Search|O(1)|O(n)|
|Insert|O(1)|O(n)|
|Delete|O(1)|O(n)|

## Use Cases

- When implementing hash tables with open addressing and simplicity is desired.
- Situations where cache performance is important.

---

  

## ==Linear Probing Chaos with Cycles 🔄❌==

## What Is It?

In **linear probing**, when a collision occurs, the next slot is checked sequentially:

$$inde_xi=(h(key)+i)modTableSize$$

**Chaos with cycles** happens when the probe sequence **loops over the same set of slots repeatedly** without reaching an empty slot—even though free slots exist.

## Why Does This Happen?

- Table size is **not chosen carefully**, e.g., not prime.
- Certain patterns of keys and table occupancy create **cyclic probe sequences**.
- This can cause **infinite loops** during insertion or search.

## Consequences

- **Insertion fails** even when free slots exist.
- **Search fails** for existing keys.
- Performance degrades due to repeated probing of the same slots.

## Example

- Table size = 10 (not prime)
- Insert keys: 0, 10, 20, 30, 40
- Hash function:

$$h(key)=Keymod  10$$

- Probe sequence:

|Key|h(key)|Index Sequence|
|---|---|---|
|0|0|0 → insert|
|10|0|1 → insert|
|20|0|2 → insert|
|30|0|3 → insert|
|40|0|4 → insert|

- Now table is partially full. If we try keys that collide at 0 and table is highly loaded, linear probing may **cycle back through already probed slots**, missing some empty slots.

## How to Avoid Cycles in Linear Probing

|Strategy|Explanation|
|---|---|
|Use **prime table size**|Reduces chances of probe sequence cycling early.|
|Maintain **low load factor**|E.g., ≤ 0.7, to ensure more empty slots.|
|Resize table when needed|Double the size and rehash keys when table is nearly full.|

## Summary

|Problem|Cause|Impact|Solution|
|---|---|---|---|
|Chaos with probe cycles|Table size not prime, high load|Infinite loops, insertion/search fails|Prime table size, low load factor, resize when needed|

---

  

## ==Linear probing insertion examples==

## Scenario

Assume we have a hash table of size 7 and a simple hash function:

$$hash(key)=Keymod7$$

We want to insert these keys in order: **10, 20, 15, 7, 32**

## Step-by-Step Insertions

|Step|Key|Hash Index (key % 7)|Action/Result|
|---|---|---|---|
|1|10|3|Index 3 is empty → Insert at index 3|
|2|20|6|Index 6 is empty → Insert at index 6|
|3|15|1|Index 1 is empty → Insert at index 1|
|4|7|0|Index 0 is empty → Insert at index 0|
|5|32|4|Index 4 is empty → Insert at index 4|

## Example with Collision

Now insert **17**:

- Hash(17) = 17 % 7 = 3
- Index 3 is already occupied (key 10).
- Apply linear probing → check index 4 → occupied (key 32)
- Check index 5 → empty
- Insert key 17 at index 5.

## Final Table State

|Index|Stored Key|
|---|---|
|0|7|
|1|15|
|2|-|
|3|10|
|4|32|
|5|17|
|6|20|

## Summary

- Linear probing checks the next slot sequentially when a collision occurs.
- It continues probing until it finds an empty slot.
- Clusters of filled slots can form, which may degrade performance.

---

  

## ==Table Resizing and Updating Values==

---

## 1. Updating Values During Insertion

When inserting a key-value pair in a linear probing hash table:

- Compute the hash index for the key.
- If the slot is empty, insert the new key-value pair.
- If the slot contains the **same key**, update its value instead of inserting a new entry.
- If the slot contains a **different key** (collision), probe linearly (next index) until:
    - An empty slot is found (insert here), or
    - The key is found (update value).

## 2. Table Resizing (Rehashing)

### Why Resize?

- Linear probing performs poorly as the table fills up (high **load factor**).
- Typical threshold: resize when load factor α=nm\alpha = \frac{n}{m}α=mn exceeds ~0.7 or 0.75.
- Resizing involves creating a **larger table** and **re-inserting all existing elements**.

### How to Resize?

1. Choose a new table size (usually double the current size and preferably a prime number).
2. Create a new, empty hash table with the new size.
3. For each element in the old table, **recompute the hash index using the new table size** and insert it into the new table (using linear probing as usual).
4. Replace the old table with the new one.

## Why Rehash?

Because the hash function depends on the table size, the indices for keys will change when the table size changes. Thus, every element must be rehashed and inserted into the new table.

## Example (High-Level)

|Before resizing (size=7)|After resizing (size=15)|
|---|---|
|Insert key with hash modulo 7|Re-insert keys with hash modulo 15|

## Summary

|Topic|Description|
|---|---|
|Updating values|Update existing key’s value during insertion to avoid duplicates|
|Table resizing|Double size when load factor high; rehash all keys into new table|
|Rehashing necessity|Needed because hash indices depend on table size|