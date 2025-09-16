---
Created: 2025-09-16T20:30
tags:
  - Dart-Core-Library-(no-external-imports)
---
# 🎯 Dart `Comparable`, `Iterable`, `Iterator` Cheat Sheet

## 1. Comparable

### **Purpose**

- Interface used to **define natural ordering** of objects.
- Enables **sorting** with `.sort()` or comparison operators.

### **Implementation**

```Dart
class Person implements Comparable<Person> {
  String name;
  int age;

  Person(this.name, this.age);

  @override
  int compareTo(Person other) {
    return age.compareTo(other.age); // sort by age
  }

  @override
  String toString() => "$name ($age)";
}

void main() {
  var people = [
    Person("Alice", 30),
    Person("Bob", 25),
    Person("Charlie", 35)
  ];

  people.sort(); // uses compareTo
  print(people); // [Bob (25), Alice (30), Charlie (35)]
}

```

✅ `Comparable` is useful for **custom object sorting**.

---

## 2. Iterable

### **Purpose**

- Base interface for **collections that can be iterated** (e.g., `List`, `Set`).
- Provides **read-only iteration** methods.

### **Common Methods**

|Method|Description|
|---|---|
|`.map()`|Transform each element|
|`.where()`|Filter elements|
|`.reduce()`|Reduce to single value|
|`.forEach()`|Apply function to each element|
|`.toList()`|Convert iterable to list|
|`.contains()`|Check if element exists|

### **Example**

```Dart
void main() {
  Iterable<int> numbers = [1, 2, 3, 4, 5];

  var even = numbers.where((n) => n % 2 == 0);
  even.forEach(print); // 2, 4

  var sum = numbers.reduce((a, b) => a + b);
  print(sum); // 15
}

```

✅ Most collections implement **Iterable**, so these methods work on `List`, `Set`, etc.

---

## 3. Iterator

### **Purpose**

- Provides **low-level iteration** over an Iterable.
- Every Iterable has an `.iterator` property.

### **Basic Usage**

```Dart
void main() {
  List<String> fruits = ["apple", "banana", "orange"];
  Iterator<String> it = fruits.iterator;

  while (it.moveNext()) {
    print(it.current); // apple, banana, orange
  }
}

```

- `.moveNext()` → moves to next element, returns `false` if end reached
- `.current` → current element

✅ Useful for **manual iteration** when you don’t want `for`/`forEach`.

---

## 4. Summary Table

|Interface|Purpose|Key Methods|
|---|---|---|
|`Comparable`|Defines natural order for objects|`compareTo()`|
|`Iterable`|Base interface for iterables|`map()`, `where()`, `reduce()`, `forEach()`, `toList()`|
|`Iterator`|Iterates over an iterable|`moveNext()`, `current`|

---

## 5. Real-World Example

💡 **Sort and Filter Custom Objects**

```Dart
class Task implements Comparable<Task> {
  String name;
  int priority;

  Task(this.name, this.priority);

  @override
  int compareTo(Task other) => priority.compareTo(other.priority);

  @override
  String toString() => "$name (Priority $priority)";
}

void main() {
  var tasks = [
    Task("Clean", 3),
    Task("Code", 1),
    Task("Cook", 2)
  ];

  tasks.sort();                     // sort by priority
  tasks.where((t) => t.priority < 3)
       .forEach(print);             // Code (Priority 1), Cook (Priority 2)
}

```

✅ Combines **Comparable + Iterable + Iterator** concepts.