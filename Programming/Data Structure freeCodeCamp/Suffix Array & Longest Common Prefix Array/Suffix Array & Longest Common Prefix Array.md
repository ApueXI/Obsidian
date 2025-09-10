---
Created: 2025-08-15T20:59
tags:
  - William-Fiset
---
# ==What is a Suffix==

---

## 1. Definition of a Suffix

A **suffix** of a string is a **substring that starts at any position in the string and extends to the end**.

Formally, for a string SSS of length n: suffix Array[i]=starting Index Of The i-th Smallest Suffix Of S

Where 0≤i<n.

---

## 2. Examples

String: `"banana"`

|Start Index iii|Suffix|
|---|---|
|0|"banana"|
|1|"anana"|
|2|"nana"|
|3|"ana"|
|4|"na"|
|5|"a"|

## 3. Key Points

- **Number of suffixes** = Length of the string nnn
- Every suffix **ends at the last character** of the string
- Suffixes can **overlap**
- Fundamental for building a **suffix array** or **suffix tree**

## 4. Visual Representation

```Plain
String:   b  a  n  a  n  a
Suffixes:
0: banana
1: anana
2: nana
3: ana
4: na
5: a
```

## 5. Summary

|Term|Meaning|
|---|---|
|Suffix|Substring from index `i` to end of string|
|Total|Number of suffixes = string length `n`|
|Use|Core building block for **suffix arrays** and **string processing algorithms**|

---

  

## ==What is a Suffix Array==

## 1. Definition

A **suffix array** of a string SSS is an **array of integers representing the starting indices of all suffixes of SSS sorted in lexicographical (alphabetical) order**.

Formally: suffix Array[i]= starting Index Of The i-th Smallest Suffix Of S

$$suffixArray[i]=starting Index Of The ith Smallest Suffix Of S$$

## 2. Example

String: `"banana"`

1. List all suffixes with their starting indices:

|Index|Suffix|
|---|---|
|0|banana|
|1|anana|
|2|nana|
|3|ana|
|4|na|
|5|a|

1. Sort the suffixes lexicographically:

|Sorted Order|Suffix|Starting Index|
|---|---|---|
|1|a|5|
|2|ana|3|
|3|anana|1|
|4|banana|0|
|5|na|4|
|6|nana|2|

1. **Suffix Array**:

$$suffixArray=[5,3,1,0,4,2]$$

## 3. Key Points

- **Length**: Same as the string length nnn
- **Elements**: Starting indices of suffixes
- **Sorting**: Lexicographical order
- Useful for **pattern searching**, **longest repeated substring**, **LCP array construction**, and many string algorithms

## 4. Visual Representation

```Plain
String: "banana"
Suffixes (sorted):
a      -> index 5
ana    -> index 3
anana  -> index 1
banana -> index 0
na     -> index 4
nana   -> index 2
Suffix Array: [5, 3, 1, 0, 4, 2]
```

## 5. Summary

|Term|Meaning|
|---|---|
|Suffix Array|Array of starting indices of all suffixes sorted lexicographically|
|Length|n (string length)|
|Purpose|Efficient string search, pattern matching, repeated substring detection|

---

  

## ==What is LCP Array==

---

## 1. Definition

The **LCP (Longest Common Prefix) array** stores the lengths of the **longest common prefix between consecutive suffixes in a suffix array**.

Formally, for a string SSS with suffix array `SA`:

LCP[i]= length of longest common prefix of S[SA[i]] and S[SA[i−1]]

- LCP array is of length n (or sometimes n−1)
- LCP[0] is usually set to 0 (no previous suffix to compare with)

## 2. Example

String: `"banana"`

1. Suffix Array: `[5, 3, 1, 0, 4, 2]`

|Sorted Suffix|Index|LCP with previous|
|---|---|---|
|a|5|0|
|ana|3|1 (prefix: "a")|
|anana|1|3 (prefix: "ana")|
|banana|0|0|
|na|4|0|
|nana|2|2 (prefix: "na")|

**LCP Array:** `[0, 1, 3, 0, 0, 2]`

## 3. Key Points

- LCP array **speeds up string pattern matching** and other suffix-array-based algorithms.
- Helps efficiently find **longest repeated substring**, **common substrings between strings**, and **string similarity measures**.
- Constructed **after building the suffix array**, often in **O(n)** using Kasai’s algorithm.

## 4. Summary Table

|Term|Meaning|
|---|---|
|LCP[i]|Length of longest common prefix between `SA[i]` and `SA[i-1]`|
|Length|n (or n-1 depending on implementation)|
|Usage|Pattern matching, substring queries, repeated substring detection|

---

  

## ==Using SA/LCP Array to find unique substring==

## 1. Problem

We want to find **all unique substrings** of a string SSS.

- A substring is **unique** if it appears **exactly once** in the string.
- Using **Suffix Array (SA)** and **LCP Array**, we can efficiently count or list unique substrings.

## 2. Key Idea

1. **All substrings** of SSS are prefixes of some suffix of SSS.
2. **Suffix Array** sorts all suffixes lexicographically.
3. **LCP Array** tells us the **length of common prefix** between consecutive suffixes.
4. **Unique substrings starting at SA[i]** are the prefixes of the suffix `S[SA[i]..n-1]` **that are longer than LCP[i]**.

Number of unique substrings starting at SA[i]=(n−SA[i])−LCP[i] n

  

- `n - SA[i]` = total length of suffix starting at `SA[i]`
- Subtract `LCP[i]` → removes substrings already counted in previous suffix

## 3. Example

String: `"banana"`

Suffix Array (SA): `[5, 3, 1, 0, 4, 2]`

LCP Array: `[0, 1, 3, 0, 0, 2]`

|i|SA[i]|Suffix|LCP[i]|Unique substrings from this suffix|
|---|---|---|---|---|
|0|5|a|0|a (length = 1)|
|1|3|ana|1|an, ana (lengths > LCP=1 → lengths 2,3)|
|2|1|anana|3|anan, anana (lengths > LCP=3 → lengths 4,5)|
|3|0|banana|0|b, ba, ban, bana, banan, banana|
|4|4|na|0|n, na|
|5|2|nana|2|nan, nana|

- **Total unique substrings** can be calculated by summing `(n - SA[i]) - LCP[i]` over all `i`.

## 4. Formula

![[88eebc2a-7ab4-45de-bd2f-cd581cf9cbcf.jpg]]

- Efficient: Can compute in **O(n)** if SA and LCP are precomputed.

## 5. Advantages

- Avoids generating all substrings explicitly.
- Works efficiently even for **large strings**.
- Useful for problems like:
    - Counting distinct substrings
    - Finding longest unique substring
    - Text analysis and compression

## 6. Summary Table

|Concept|Explanation|
|---|---|
|Suffix Array (SA)|Sorted list of all suffix starting indices|
|LCP Array|Length of longest common prefix between consecutive suffixes|
|Unique Substrings at SA[i]|`(n - SA[i]) - LCP[i]`|
|Total Unique Substrings|Sum over all SA[i]|

  

---

  

## ==The longest Common Substring==

---

  

## ==LCS Algorithm==

---

  

## ==Longest Repeated Substring==

---