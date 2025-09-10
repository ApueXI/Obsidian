---
Created: 2025-08-12T08:52
---
# ==Removing elements==

---

  

## ==Issues with Removing Elements==

## The Problem

In **open addressing hash tables** (linear probing, quadratic probing, double hashing), collisions are resolved by **probing** to find an empty slot.

If you **remove an element by simply clearing its slot to empty**:

- The **probe sequence is broken**.
- Searches for some keys will incorrectly stop early.
- This leads to **failed lookups** and **data corruption**.

## Why This Happens

Open addressing relies on **continuous probe sequences**:

Example — Linear Probing:

1. Insert `10` → index 0
2. Insert `20` → index 1 (collision with 10)
3. Insert `30` → index 2 (collision chain continues)

|Index|Value|
|---|---|
|0|10|
|1|20|
|2|30|

If we delete `20` by making index 1 empty:

|Index|Value|
|---|---|
|0|10|
|1|EMPTY|
|2|30|

Searching for `30`:

- Hash(30) → 0, check index 0 (10) → not found → index 1 is empty → **stop** → **fails to find 30** (even though it exists).

## Consequences

1. **Search failures** — Keys that should be found are missed.
2. **Broken insertion logic** — New insertions may overwrite necessary probe sequence slots.
3. **Data corruption risk** — Probe sequences no longer guarantee correct search results.

## Standard Solutions

|Method|How It Works|
|---|---|
|**Tombstones**|Mark deleted slot with special value so searches keep probing past it.|
|**Lazy Deletion**|Same as tombstones; slot reused for insertion but treated as occupied during search.|
|**Relocation**|After deletion, shift subsequent keys backward to close the gap.|
|**Full Rehash**|Rebuild table without deleted element to fully restore structure.|

## Key Takeaways

- In open addressing, **you cannot simply set a deleted slot to empty**.
- Removing elements requires **special handling** to preserve probe sequences.
- Common fix: **Tombstones** (most widely used).

  

---

  

## ==Solution using Tombstone==

## Problem

In **open addressing hash tables** (linear, quadratic, or double hashing), directly deleting an element and leaving the slot empty can break probe sequences:

- Example: Searching for a key may stop at an empty slot, even if the key exists further along the probe sequence.
- This can lead to **failed searches and corrupted lookups**.

## Solution: Tombstones

- A **tombstone** is a special marker indicating that a slot was **previously occupied but is now deleted**.
- When searching:
    - Treat tombstones as **occupied** for continuing the probe sequence.
- When inserting:
    - Treat tombstones as **available slots** for new elements.

This preserves probe sequences while allowing deletions.

## How It Works

1. **Insert Key**
    - Use the usual hash + probing strategy.
2. **Remove Key**
    - Instead of setting the slot to empty, mark it as a **tombstone**.
3. **Search Key**
    - Continue probing past tombstones until the key is found or an empty slot is reached.
4. **Insert into Tombstone**
    - New keys can occupy tombstone slots, effectively recycling space.

## Example (Linear Probing)

|Index|Value|
|---|---|
|0|10|
|1|22|
|2|31|
|3|4|
|4|15|

- Remove key `22` → mark index 1 as **TOMBSTONE**

|Index|Value|
|---|---|
|0|10|
|1|TOMBSTONE|
|2|31|
|3|4|
|4|15|

- Searching for `31`:
    - Start at hash(31) → probe indices 2 → found
    - Tombstone at index 1 does not stop the probe
- Inserting `28`:
    - Hash(28) → index 0 occupied
    - Index 1 is tombstone → insert at 1

|Index|Value|
|---|---|
|0|10|
|1|28|
|2|31|
|3|4|
|4|15|

## Advantages

- Preserves **probe sequences** for search and update operations.
- Allows **recycling deleted slots** for future insertions.

## Disadvantages

- Tombstones increase **probe length** over time.
- Table may require **periodic rehashing** to clean up tombstones and reduce wasted space.

## Summary Table

|Operation|How Tombstone Helps|
|---|---|
|Search|Continue past tombstone until key found or empty slot reached|
|Insert|Tombstones treated as available slots|
|Delete|Mark slot as tombstone instead of empty|
|Rehashing|Can remove tombstones to reclaim space|

---

  

## ==Lazy Deletion/Relocation==

## Problem

In **open addressing hash tables**, simply deleting an element by marking its slot empty can break probe sequences:

- Subsequent searches for keys that collided with the deleted key may fail.
- This can corrupt lookups and make insertion/search incorrect.

## Solution: Lazy Deletion / Relocation

### **Lazy Deletion**

- Instead of immediately removing a key from the table, **mark it as deleted (tombstone)**.
- The slot is treated as **occupied during searches** but **available during insertion**.
- Preserves probe sequences without breaking searches.

### **Relocation (Optional Optimization)**

- After marking a tombstone, you may **shift subsequent keys backward** to fill the empty slot.
- Helps reduce **probe lengths** and improves future search/insertion efficiency.

## How It Works

1. **Search for the key to delete**
    - Follow the usual probing sequence until the key is found.
2. **Mark as deleted**
    - Set the slot as a **tombstone** instead of empty.
3. **Insert new key**
    - Tombstone slots are treated as **available** for insertion.
4. **Optional Relocation**
    - Shift keys that were part of the same probe sequence backward to fill the tombstone.
    - Reduces wasted slots and shortens probe sequences.

## Example (Linear Probing with Lazy Deletion)

Original table:

|Index|Value|
|---|---|
|0|10|
|1|22|
|2|31|
|3|4|
|4|15|

- Delete key `22` → mark index 1 as **TOMBSTONE**

|Index|Value|
|---|---|
|0|10|
|1|TOMBSTONE|
|2|31|
|3|4|
|4|15|

- Insert `28` → uses tombstone slot 1

|Index|Value|
|---|---|
|0|10|
|1|28|
|2|31|
|3|4|
|4|15|

**Optional Relocation:**

- Shift 31 back to tombstone if it preserves probe sequence correctness.
- Result: shorter probe sequences and more efficient future operations.

## Advantages

- Preserves probe sequences, preventing search failures.
- Recycles deleted slots for new insertions.
- Relocation reduces probe lengths and improves efficiency.

## Disadvantages

- Tombstones can accumulate, increasing average probe length.
- Relocation adds extra computation during deletion.
- Periodic **rehashing** may still be needed to clean up table.

## Summary Table

|Operation|How Lazy Deletion / Relocation Helps|
|---|---|
|Search|Continue past tombstone until key or empty slot|
|Insert|Tombstone treated as available slot|
|Delete|Mark as tombstone instead of empty; optionally relocate keys|
|Rehashing|Can remove tombstones to reclaim space|

---