---
Created: 2025-09-16T20:23
tags:
  - Memory-&-Performance
---
# 🎯 Dart Garbage Collection Cheat Sheet

## 1. Full Explanation

- **Garbage Collection (GC)** is a **memory management mechanism** that **automatically frees memory** occupied by objects that are **no longer accessible**.
- Dart **does not require manual memory management** (like `free` in C/C++).
- Works for both **Dart VM (server/CLI)** and **Flutter (mobile/web)**.
- GC is essential to **prevent memory leaks** and **optimize performance**.

---

## 2. How Dart GC Works

1. **Allocation:**
    - Memory is allocated on the **heap** when objects are created (e.g., `List`, `Map`, custom classes).
2. **Reachability:**
    - An object is considered **reachable** if it can be accessed via **active variables, global references, or call stack**.
3. **Garbage:**
    - Objects that are **no longer referenced** are **eligible for garbage collection**.
4. **Collection:**
    - The GC **automatically frees memory** of unreachable objects.

---

## 3. Example Concept

```Dart
void main() {
  var list1 = [1, 2, 3]; // allocated on heap
  var list2 = list1;      // another reference

  list1 = null;           // list1 reference removed
  // list2 still references the object → not garbage yet

  list2 = null;           // no references left → object is garbage
}

```

✅ When no references exist, the **object becomes eligible for GC**.

---

## 4. GC in Flutter

- Dart uses **generational garbage collection**:
    1. **Young Generation:** short-lived objects, collected frequently
    2. **Old Generation:** long-lived objects, collected less often
- Helps **reduce pause times** and improve **UI smoothness**.
- Best practices to avoid memory issues:
    - Dispose of controllers, streams, and animations (`TextEditingController`, `StreamController`)
    - Avoid unnecessary global/static references
    - Use `final`/`const` where possible

---

## 5. Key Points

|Feature|Notes|
|---|---|
|Automatic|No manual `delete` needed|
|Heap allocation|All objects allocated on heap|
|Reachable vs Garbage|Only unreachable objects are collected|
|Generational GC|Young/Old object optimization in Dart VM|
|Best practices|Dispose controllers, avoid memory leaks, use final/const|

---

## 6. Real-World Analogy

- **Value type:** Like a number on paper; GC not needed.
- **Reference type:** Like a locker key; GC cleans lockers that **no one can access anymore**.