---
Created: 2025-09-16T20:18
tags:
  - Advance-Concepts
---
# 🎯 Dart Generics Cheat Sheet

## 1. Full Explanation

- **Generics** allow you to **parameterize types**.
- Makes code **type-safe** and **reusable** without casting.
- Commonly used in **collections** like `List`, `Map`, `Set`.
- Syntax: `ClassName<T>` or `ClassName<K, V>`

---

## 2. Generic List

```Dart
void main() {
  List<int> numbers = [1, 2, 3]; // only ints allowed
  numbers.add(4);
  // numbers.add("five"); // ❌ Compile-time error

  List<String> names = ["Alice", "Bob"];
  print(numbers); // [1, 2, 3, 4]
  print(names);   // [Alice, Bob]
}

```

✅ Type-safe: prevents adding wrong types to the list.

---

## 3. Generic Map

```Dart
void main() {
  Map<String, int> scores = {
    "Alice": 90,
    "Bob": 85,
  };

  scores["Charlie"] = 92;
  // scores[100] = "John"; // ❌ Compile-time error

  print(scores); // {Alice: 90, Bob: 85, Charlie: 92}
}

```

✅ `Map<K, V>` ensures **key/value types** are consistent.

---

## 4. Generic Class Example

```Dart
class Box<T> {
  T value;
  Box(this.value);

  void show() {
    print("Value: $value");
  }
}

void main() {
  var intBox = Box<int>(123);
  var stringBox = Box<String>("Hello");

  intBox.show();     // Value: 123
  stringBox.show();  // Value: Hello
}

```

✅ `T` can represent **any type**, making the class reusable.

---

## 5. Generic Method Example

```Dart
T getFirst<T>(List<T> items) {
  return items[0];
}

void main() {
  var nums = [1, 2, 3];
  var names = ["Alice", "Bob"];

  print(getFirst(nums));   // 1
  print(getFirst(names));  // Alice
}

```

✅ Methods can also be **generic** with `<T>`.

---

## 6. Summary Table

|Feature|Syntax|Notes|
|---|---|---|
|Generic List|`List<T>`|Type-safe list|
|Generic Map|`Map<K, V>`|Type-safe key-value|
|Generic Class|`class Box<T> { ... }`|Reusable class for any type|
|Generic Method|`T getFirst<T>(List<T> list)`|Reusable method for any type|
|Benefits|Type safety, code reuse|Prevents runtime type errors|

---

## 7. Real-World Example

💡 **Repository Pattern with Generics**

```Dart
class Repository<T> {
  List<T> items = [];

  void add(T item) => items.add(item);
  T get(int index) => items[index];
  List<T> getAll() => items;
}

void main() {
  var intRepo = Repository<int>();
  intRepo.add(10);
  intRepo.add(20);

  var stringRepo = Repository<String>();
  stringRepo.add("Alice");
  stringRepo.add("Bob");

  print(intRepo.getAll());    // [10, 20]
  print(stringRepo.getAll()); // [Alice, Bob]
}

```

✅ Generics let you **reuse the same class** for **different types safely**.