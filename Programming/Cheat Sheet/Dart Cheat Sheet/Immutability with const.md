---
Created: 2025-09-16T20:24
tags:
  - Memory-&-Performance
---
# 🎯 Dart Immutability with `const` Cheat Sheet

## 1. Full Explanation

- `**const**` in Dart makes **variables, objects, and collections immutable**.
- Once assigned, a `const` object **cannot be modified** anywhere.
- **Compile-time constant:** `const` objects are created at **compile-time**, not runtime.
- Benefits:
    - **Memory efficiency:** identical `const` objects are **canonicalized** (shared instance)
    - **Safety:** prevents accidental mutation

---

## 2. Const Variables

```Dart
void main() {
  const pi = 3.14;
  // pi = 3.1415; // ❌ Compile-time error
  print(pi); // 3.14
}

```

✅ Immutable primitive value.

---

## 3. Const Collections

```Dart
void main() {
  const numbers = [1, 2, 3];
  // numbers[0] = 99; // ❌ Compile-time error
  print(numbers); // [1, 2, 3]

  const map = {"a": 1, "b": 2};
  // map["a"] = 99; // ❌ Compile-time error
}

```

✅ **Cannot change content** of `const` collections.

---

## 4. Const Constructors

```Dart
class Point {
  final int x;
  final int y;
  const Point(this.x, this.y);
}

void main() {
  const p1 = Point(1, 2);
  const p2 = Point(1, 2);

  print(identical(p1, p2)); // true → same instance
}

```

✅ `const` constructor + `const` object → **immutable object shared in memory**.

---

## 5. Const vs Final vs Late

|Feature|`const`|`final`|`late`|
|---|---|---|---|
|Assignment time|Compile-time|Runtime|Deferred (runtime)|
|Reassignment|❌ No|❌ No|✅ Yes until first assignment|
|Mutability|❌ Immutable|⚠ Can mutate object fields|⚠ Can mutate object fields|
|Shared instance|✅ Canonicalized|❌ Not shared|❌ Not shared|

---

## 6. Real-World Example

💡 **UI Colors in Flutter**

```Dart
class Colors {
  static const red = Color(255, 0, 0);
  static const blue = Color(0, 0, 255);
}

void main() {
  const c1 = Colors.red;
  const c2 = Colors.red;

  print(identical(c1, c2)); // true → memory efficient
}

```

✅ Using `const` ensures **immutable configuration objects** and **memory optimization**.