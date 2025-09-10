---
Created: 2025-08-12T08:52
---
# ==Double Hashing==

---

  

## ==Double Hashing 🎯==

## Definition

**Double hashing** is a collision resolution technique used in open addressing hash tables. When a collision occurs, it uses **two different hash functions** to calculate probe sequences, reducing clustering and improving distribution.

## How It Works

1. Compute the primary hash index:

$$h_1(key)=hash_1(key)modTableSize$$

1. Compute the secondary hash (step size):

$$h_2(key)=hash_2(key)modTableSize$$

1. If collision occurs at h1(key) probe indices are calculated as:

$$index_i=(h_1(key)+i×h_2(key))modTableSize$$

where i=0, 1, 2, …

## Important Notes

- The second hash h2(key)h_2(key)h2(key) **must never be zero** and is typically chosen to be relatively prime to the table size to ensure the probe sequence visits every slot.
- Double hashing avoids **primary clustering** better than linear and quadratic probing.
- It generates a **wider and more uniform probe sequence**.

## Advantages

- Minimizes clustering significantly.
- Better probe distribution leads to fewer collisions and faster lookups.
- Suitable for hash tables with open addressing.

## Disadvantages

- Requires two hash functions.
- Slightly more complex than linear or quadratic probing.

## Time Complexity

|Operation|Average Case|Worst Case|
|---|---|---|
|Search|O(1)|O(n)|
|Insert|O(1)|O(n)|
|Delete|O(1)|O(n)|

## Use Cases

- Hash tables that need efficient collision handling and minimal clustering.
- Situations where hash function quality can be controlled to produce good secondary hashes.

---

  

## ==How does it work - Step-by-Step Process==

1. **Compute the first hash h1L**
    
    $$h_1(key)=hash_1(key)modTableSize$$
    
2. **Check the slot at h1(key)**
    - If empty, insert the key-value pair here.
    - If occupied by the same key, update its value.
    - If occupied by a different key (collision), proceed to step 3.
3. **Compute the second hash h2**: (key)=hash2(key)modtable_size
    
    This determines the **step size** for probing.
    
    $$h_2(key)=hash_2(key)modTableSize$$
    
    **Important:** h2(key) should never be zero and should be relatively prime to the table size to ensure the entire table can be probed.
    
4. **Probe using the sequence:**indexi=(h1(key)+i×h2(key))modtable_size
    
    When a collision occurs, check slots using:
    
    $$index_i=(h_1(key)+i×h_2(key))modTableSize$$
    
    where i=1, 2, 3, … increments on each collision.
    
5. **Find an empty slot or the key:**
    
    Continue probing until an empty slot (for insertion) or the key (for search/update) is found.
    

## Why It Works Well

- The **second hash function spreads out probes** to avoid clustering seen in linear or quadratic probing.
- Because the step size h2(key) varies with the key, different keys follow different probe sequences.
- If h2(key) and table size are coprime, all slots can be eventually probed, avoiding infinite loops or cycles.

## Example

Suppose:

- Table size = 11

$$h_1(key)=keymod11$$

$$h_2(key)=7−(Keymod7)$$

- (a common choice ensuring step size ≠ 0)

Insert key = 27:

$$h_1(27)=27mod11=5$$

- Slot 5 empty → insert at 5.

Insert key = 38:

$$h_1(38)=38mod11=5 → collision$$

$$h_2(38)=7−(38mod7)=7−3=4$$

- Probes:

$$i=1:(5+1×4)mod  11=9 → empty → insert at 9.$$

---

  

## ==Chaos Cycles - What Is It?==

In **double hashing**, the probe sequence depends on two hash functions:

$$index_i=(h_1(key)+i×h_2(key))modTableSize$$

Cycles occur when the probing sequence repeats slots before covering the entire table, causing infinite loops or failure to find free slots even if available.

## Why Do Cycles Happen?

- If the **step size h2(key)** and **table size** share a common factor (i.e., not coprime), the probe sequence only cycles through a subset of slots instead of the full table.
- This partial coverage leads to repeated visits to the same slots, missing others entirely.

## Consequences

- **Insertion failures** even with free slots available.
- **Search misses** for existing keys.
- Poor performance and correctness issues.

## How to Avoid Cycles in Double Hashing

|Strategy|Explanation|
|---|---|
|Choose **table size as a prime number**|Ensures better distribution and full probing.|
|Design h2(key so it's **coprime to table size**|Guarantees all slots are eventually probed.|
|Use carefully designed hash functions|Prevents step size of zero or repeated cycles.|

## Example

- Table size = 10 (not prime)
- h2(key)=keymod  5h
- For key with h2(key)=5h , probe indices cycle through only two positions:
    
    $$index_i=(h_1(key)+i×5)mod  10 → cycles between 0 and 5 only$$
    

## Summary

|Problem|Cause|Impact|Solution|
|---|---|---|---|
|Cycles in probe|Step size not coprime with table size|Infinite loops, missed slots|Prime table size & coprime step size|

  

---

  

## ==Constructing a new Hash Function - Purpose of the Second Hash Function h2(key)==

- Provides the **step size** used for probing on collisions.
- Must produce a value **never equal to zero** to ensure progress.
- Should be **relatively prime** to the table size to guarantee that the probe sequence visits all slots.

## Guidelines for Designing h2(key)

|Guideline|Explanation|
|---|---|
|**Non-zero output**|h2(key)≠0 for any key to avoid infinite loop on same slot.|
|**Relatively prime to table size**|Ensures the entire table can be probed (full cycle).|
|**Simple and fast to compute**|Hashing should remain efficient (O(1) time).|
|**Dependent on key**|Output should vary significantly with different keys.|

## Common Construction Techniques

### 1. Using Modulus with a Smaller Prime

$$h_2(key)=R−(keymodR)$$

- Where R is a prime number smaller than the table size.
- Guarantees h2(key)≠0 as long as R < table_size.
- Example: If table size = 11, choose R=7.

### 2. Using Multiplicative Hashing

$$h2(key)=1+(key×A)mod(TableSize−1)$$

- Where 𝐴 A is a constant multiplier
- Adding 1 ensures non-zero output.

### 3. Using Bitwise Operations

- Combine shifts, XORs, and masks on the key to create variability.
- Then apply modulus with a prime smaller than table size.

## Example

For table size 13:

$$h_2(key)=7−(keymod7)$$

- Since 7 is prime and less than 13, h2(key) is always between 1 and 7 (never zero).
- Step size will vary for different keys, helping spread probe indices.

## Summary

|Property|Importance|
|---|---|
|Non-zero|Avoid infinite loop on same slot|
|Relatively prime to table|Full table coverage|
|Efficient computation|Maintains overall performance|
|Key-dependent variation|Better probe distribution|

  

---

  

## ==What is a Universal Hash Function?==

A **universal hash function family** is a set of hash functions designed so that the probability of collision between any two distinct keys is minimized when a function is chosen at random from the family.

Using universal hashing in double hashing improves randomness and reduces clustering.

## Why Use Universal Hashing in Double Hashing?

- Reduces **worst-case collisions** caused by adversarial inputs.
- Provides **provable guarantees** on collision probability.
- Ensures better distribution of both primary and secondary hashes, leading to efficient probing.

## Structure in Double Hashing

- Primary hash function h1and secondary hash function h2are selected randomly from universal hash families.
- This randomness improves probe sequence diversity.

## Common Universal Hash Function Form

For keys in universe U={0,1,…,m−1}:

$$^ha,b(key)=((a×key+b)modP)modTableSize$$

Where:

- p is a large prime number greater than m (key space size).
- a and b are random integers where 1 ≤ 𝑎 < p, 0 ≤ 𝑏 < 𝑝.

## Using Universal Hashing in Double Hashing

- Choose

$$h_1(key)=^ha1,b1(key)$$

- from universal family.
- Choose

$$h_1(key)=^ha1,b1(key)$$

- and relatively prime to table size.

## Benefits

|Benefit|Explanation|
|---|---|
|Minimizes collisions|Randomization spreads keys better|
|Provable performance|Guarantees expected O(1) operations|
|Security advantages|Resists adversarial input causing collisions|

## Summary Table

|Term|Meaning|
|---|---|
|Universal hashing|Randomly selects hash functions to minimize collision probability|
|a,b,p|Parameters defining universal hash functions|
|Double hashing|Uses two universal hash functions for primary and step size hashes|

---

  

## ==Double Hashing - Inserting/Resizing Examples==

## Setup

- Initial table size = 11 (prime number recommended)
- Load factor threshold = 0.7 (resize when table > 70% full)
- Primary hash function:

$$h_1(key)=keymod11$$

- Secondary hash function:

$$h_2(key)=7−(keymod7)$$

- (non-zero, coprime with table size)

## Step 1: Insert Keys 10, 22, 31, 4

|Key|h₁(key)|h₂(key)|Probing Sequence|Action/Result|
|---|---|---|---|---|
|10|10|4|10|Slot 10 empty → Insert|
|22|0|2|0|Slot 0 empty → Insert|
|31|9|3|9|Slot 9 empty → Insert|
|4|4|3|4|Slot 4 empty → Insert|

- Load factor = 4/11 ≈ 0.36 → No resize yet.

## Step 2: Insert Key 15

- h₁(15) = 15 % 11 = 4 → collision (4 occupied by 4)
- h₂(15) = 7 - (15 % 7) = 7 - 1 = 6
- Probe sequence:
    - i=1: (4 + 1×6) % 11 = 10 → occupied by 10
    - i=2: (4 + 2×6) % 11 = 5 → empty → insert at 5
- Load factor = 5/11 ≈ 0.45 → still under threshold

## Step 3: Insert Key 28

- h₁(28) = 28 % 11 = 6 → empty → insert at 6
- Load factor = 6/11 ≈ 0.55 → still under threshold

## Step 4: Insert Key 33 (Trigger Resize)

- h₁(33) = 33 % 11 = 0 → occupied by 22
- h₂(33) = 7 - (33 % 7) = 7 - 5 = 2
- Probe sequence:
    - i=1: (0 + 1×2) % 11 = 2 → empty → insert at 2
- Load factor = 7/11 ≈ 0.64 → still under 0.7, but next insert may trigger resize

Insert Key 44 → Load factor exceeds 0.7 → Resize table

## Step 5: Resize Table

- New table size: 23 (next prime ≥ 2×11)
- Re-insert all keys using new hash functions modulo 23:
    - h₁(key) = key % 23
    - h₂(key) = 17 - (key % 17) (prime < 23)

Re-inserting keys:

|Key|h₁(key)|h₂(key)|Final Index|
|---|---|---|---|
|10|10|7|10|
|22|22|12|22|
|31|8|3|8|
|4|4|13|4|
|15|15|2|15|
|28|5|6|5|
|33|10|14|11 (collision at 10) → insert at 11|

  

## Final Table (Size 23)

|Index|Value|
|---|---|
|0|-|
|1|-|
|2|-|
|3|-|
|4|4|
|5|28|
|6|-|
|7|-|
|8|31|
|9|-|
|10|10|
|11|33|
|12|-|
|13|-|
|14|-|
|15|15|
|16|-|
|17|-|
|18|-|
|19|-|
|20|-|
|21|-|
|22|22|

## Summary

|Step|Action|
|---|---|
|Insertion|Use formula indexi=(h1(key)+i×h2(key))mod  table_sizeindex_i = (h_1(key) + i \times h_2(key)) \mod table\_sizeindexi=(h1(key)+i×h2(key))modtable_size to resolve collisions|
|Load Factor|Track table fullness (n / table_size)|
|Resize|When load factor exceeds threshold, double table size and rehash keys|
|Rehash|Recompute h₁ and h₂ for all keys in the new table|

---