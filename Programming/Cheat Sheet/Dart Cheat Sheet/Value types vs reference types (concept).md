---
Created: 2025-09-16T20:23
tags:
  - Memory-&-Performance
---
# 🎯 Dart Value Types vs Reference Types Cheat Sheet

## 1. Full Explanation

In programming, **types of data are categorized** based on how variables store and access them:

### **1. Value Types (Primitive types / Immutable types)**

- **Stored directly** in the variable’s memory.
- **Assignment copies the value**. Changing one variable **does not affect** the other.
- Typically **immutable**.

**Examples in Dart:**

- `int`, `double`, `bool`, `String` (immutable), `enum`

### **2. Reference Types (Objects / Classes / Collections)**

- **Stored as a reference (pointer)** to the memory location of the object.
- **Assignment copies the reference**, not the object itself. Changing the object **affects all references**.
- Typically **mutable** unless explicitly immutable (`final` or `const`).

**Examples in Dart:**

- `List`, `Map`, `Set`, custom `class` objects

---

## 2. Examples

### **Value Type Example**

```Dart
void main() {
  int a = 5;
  int b = a; // copy of value

  b = 10;

  print(a); // 5
  print(b); // 10
}

```

✅ `a` remains unchanged because **b has its own copy**.

---

### **Reference Type Example**

```Dart
void main() {
  List<int> list1 = [1, 2, 3];
  List<int> list2 = list1; // reference copied

  list2[0] = 99;

  print(list1); // [99, 2, 3]
  print(list2); // [99, 2, 3]
}

```

✅ Changing `list2` **affects** `**list1**`, because they **point to the same object**.

---

### **Immutable Reference Example**

```Dart
void main() {
  final list = [1, 2, 3];
  // list = [4, 5, 6]; // ❌ Cannot reassign final
  list[0] = 99; // ✅ Can still mutate contents
  print(list); // [99, 2, 3]
}

```

- `final` prevents **reassignment of the reference**, not mutation.
- `const` makes **both reference and contents immutable**.

---

## 3. Summary Table

|Feature|Value Type|Reference Type|
|---|---|---|
|Storage|Direct in variable|Memory address / reference|
|Assignment|Copies value|Copies reference|
|Mutation|Immutable|Usually mutable|
|Examples|`int`, `double`, `bool`, `String`, `enum`|`List`, `Map`, `Set`, `class` objects|
|Effect of change|Does not affect other variable|Affects all references pointing to the object|

---

## 4. Real-World Analogy

- **Value Type:** Like writing a number on a paper. Copying the paper gives **independent numbers**.
- **Reference Type:** Like giving someone a **shared key to a locker**. Everyone accessing the key sees **the same contents**.