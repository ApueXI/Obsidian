---
Created: 2025-08-12T08:51
---
# ==Quadratic Probing==

---

## ==What is a Quadratic Probing==

## Definition

**Quadratic probing** is a collision resolution technique used in open addressing hash tables. When a collision occurs, instead of checking the next slot sequentially (like linear probing), it probes slots at increasing quadratic intervals based on the number of attempts.

## How It Works

1. Compute the hash index of the key.
2. If the slot is occupied (collision), check slots at intervals of i2i^2i2 from the original index, where iii is the attempt number (starting from 1).
3. Continue probing using the sequence until an empty slot is found.

## Formula

For the _i_th probe, the index checked is:

$$index=(hash(key)+i^2)modTableSize$$

Where:

- i=0,1,2,3,...i = 0, 1, 2, 3, ...i=0,1,2,3,... (number of probes so far)

## Advantages

- Reduces **primary clustering** compared to linear probing.
- Simple to implement.

## Disadvantages

- Can still suffer from **secondary clustering** (keys with the same initial hash follow the same probe sequence).
- Table size and load factor need careful management to ensure that a free slot is found.
- May not guarantee that all slots are probed depending on the table size.

## Time Complexity

|Operation|Average Case|Worst Case|
|---|---|---|
|Search|O(1)|O(n)|
|Insert|O(1)|O(n)|
|Delete|O(1)|O(n)|

## Use Cases

- Open addressing hash tables where better distribution is desired than linear probing provides.

---

  

## ==Problems with Probing Sequence Cycles==

In open addressing hash tables using probing (like linear, quadratic, or double hashing), the **probing sequence** is the order of slots checked when resolving collisions. Sometimes, the sequence can **cycle back** to previously visited slots without covering all table slots, causing **infinite loops** or failure to find empty slots—even if free space exists.

## Why Do Cycles Happen?

- The **probe function** may not generate a full permutation of indices over the table size.
- Especially in **quadratic probing** and **double hashing**, if table size and probe steps are not chosen carefully, the probing sequence can get stuck cycling over a subset of slots.
- This means some empty slots remain unreachable during insertion or search.

## Consequences

- **Insertion fails** prematurely despite free slots being available.
- **Search fails** to find keys even if they exist.
- Degrades hash table performance or breaks correctness.

## Example

- Suppose the table size is 10 (not prime), and quadratic probing uses increments i2i^2i2.
- The probe sequence might check indices: 3, 4, 7, 4, 7, ... cycling endlessly between 4 and 7 without visiting other slots.

## How to Prevent Cycles

|Strategy|Explanation|
|---|---|
|Choose table size as a **prime number**|Ensures probe sequences cover more slots fully.|
|Use **proper hash functions**|Functions designed to avoid short cycles.|
|Limit load factor (e.g., ≤ 0.5)|Reduces collisions and likelihood of cycles.|
|Use **double hashing** with coprime step sizes|Produces better probe coverage than quadratic or linear.|
|Table size must be the power of 2|P(x) = `(x^2 + x) / 2`  <br>Table Size = `2^k`|

  

$$P(i)=(h+c_1i+c_2i^2) mod m$$

## Summary Table

|Problem|Cause|Impact|Mitigation|
|---|---|---|---|
|Probing sequence cycles|Poor choice of table size/hash|Infinite loops, insertion/search failure|Prime table size, double hashing, load factor control|

---

  

## ==Different ways to Quadratically Probe==

Quadratic probing is a method to resolve collisions by checking slots at increasing quadratic intervals from the original hash index. However, the exact formula and implementation details can vary, affecting performance and cycle avoidance.

## Common Quadratic Probing Formulas

|Method|Formula|Description|
|---|---|---|
|**Basic Quadratic Probing**|index=(hash(key)+i^2)mod table_size|Checks slots at perfect square intervals: 1², 2², 3²...|
|**Generalized Form**|index=(hash(key)+c1⋅i+c2⋅i2)mod table_size|Combines linear and quadratic terms with constants c1,c2c_1, c_2c1,c2. Useful for better distribution.|
|**Symmetric Probing**|Probe sequence includes both + 𝑖 2 +i 2 and − 𝑖 2 −i 2 offsets|Checks slots in both directions from the original index, reducing clustering.|

## Parameters Explained

- iii: Probe attempt number (starting from 0 or 1).
- c1,c2c_1, c_2c1,c2: Constants chosen (usually small integers like 1 or 2) to tune probe steps.
- table_sizetable\_sizetable_size: Size of the hash table, ideally prime or a power of two for better behavior.

## Example: Generalized Formula

$$index=(hash(key)+i+3i2)mod TableSize$$

- Here, c_1 = 1, c_2 = 3.
- This formula mixes linear and quadratic terms for more diverse probing.

## Why Vary the Formula?

- To **reduce clustering** more effectively.
- To **avoid cycles** and ensure full table coverage.
- To **balance probe distribution** between nearby and farther slots.

## Practical Tips

- Use **prime-sized tables** to reduce cycles.
- Tune c_1, c_2 constants based on table size and expected load.
- Symmetric probing can improve search by checking slots on both sides of the original index.

---

  

## ==Inserting/Resizing Example==

## Setup

- Initial table size = 7
- Load factor threshold = 0.7 (resize when table is more than 70% full)
- Hash function

$$hash(key)=KeymodTableSize$$

- Quadratic probing formula

$$index=(hash(key)+i2)modTableSize$$

- where i=0, 1, 2,...

## Step 1: Insert keys 10, 24, 31, 17

|Key|hash(key) = key % 7|Attempt iii|Calculated Index|Action/Result|
|---|---|---|---|---|
|10|3|0|3|Index 3 empty → Insert at 3|
|24|3|0|3|Collision (10 at 3) → try i=1i=1i=1|
|||1|(3 + 1²) % 7 = 4|Index 4 empty → Insert at 4|
|31|3|0|3|Collision (10 at 3) → try i=1i=1i=1|
|||1|4 (occupied by 24)|Collision → try i=2i=2i=2|
|||2|(3 + 4) % 7 = 0|Index 0 empty → Insert at 0|
|17|3|0|3|Collision → i=1i=1i=1 → 4 (occupied)|
|||1|4|Collision → i=2i=2i=2 → 0 (occupied)|
|||2|0|Collision → i=3i=3i=3 → (3 + 9) % 7 = 5|

## Table State After Step 1

|Index|Value|
|---|---|
|0|31|
|1|-|
|2|-|
|3|10|
|4|24|
|5|17|
|6|-|

- Load factor = 4/7 ≈ 0.57 → No resize yet.

## Step 2: Insert key 39

- hash(39) = 39 % 7 = 4
- Attempt 𝑖 = 0 index 4 (occupied by 24) → collision
- Attempt i=1 (4 + 1²) % 7 = 5 (occupied by 17) → collision
- Attempt i=2 (4 + 4) % 7 = 1 (empty) → insert at index 1

Table after insertion:

|Index|Value|
|---|---|
|0|31|
|1|39|
|2|-|
|3|10|
|4|24|
|5|17|
|6|-|

- Load factor = 5/7 ≈ 0.71 → **Exceeds 0.7 threshold!**

## Step 3: Resize & Rehash

- New table size: 15 (usually doubled)
- Create an empty table of size 15
- Re-insert all existing keys using new hash function: key mod  15 and quadratic probing

|Key|hash(key) = key % 15|Attempt iii|Calculated Index|Action|
|---|---|---|---|---|
|10|10|0|10|Insert at 10|
|24|9|0|9|Insert at 9|
|31|1|0|1|Insert at 1|
|17|2|0|2|Insert at 2|
|39|9|0|9 (occupied)|i=1 → 10 (occupied) i=2 → 13 (empty) Insert at 13|

## Final Table After Resizing

|Index|Value|
|---|---|
|0|-|
|1|31|
|2|17|
|3|-|
|4|-|
|5|-|
|6|-|
|7|-|
|8|-|
|9|24|
|10|10|
|11|-|
|12|-|
|13|39|
|14|-|

## Summary

|Step|Action|
|---|---|
|Insertion|If collision, probe using quadratic steps i^2|
|Load factor check|Resize when load factor exceeds threshold (0.7)|
|Resizing|Double table size, rehash all keys into new table|

---