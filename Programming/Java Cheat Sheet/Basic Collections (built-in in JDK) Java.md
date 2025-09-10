---
Created: 2025-08-25T20:07
tags:
  - Arrays-&-Collections-(Core)
---
# ArrayList

## 1. Full Explanation

### 🔹 What is ArrayList?

- **ArrayList** is a **resizable array** provided in `**java.util**` **package**.
- Can **grow or shrink dynamically** as elements are added or removed.
- Implements **List interface** → ordered collection, allows duplicates, maintains insertion order.
- Stores **objects only** (use wrapper classes for primitives).

---

### 🔹 Import Statement

```Java
import java.util.ArrayList;

```

---

### 🔹 Creating an ArrayList

```Java
// Without specifying type (raw type, not recommended)
ArrayList list = new ArrayList();

// With Generics (preferred)
ArrayList<Integer> numbers = new ArrayList<>();
ArrayList<String> names = new ArrayList<>();

```

- **Generics** enforce type safety → only allowed type can be added.

---

### 🔹 Adding Elements

```Java
ArrayList<String> fruits = new ArrayList<>();
fruits.add("Apple");
fruits.add("Banana");
fruits.add("Cherry");
System.out.println(fruits); // [Apple, Banana, Cherry]

// Add at specific index
fruits.add(1, "Mango");
System.out.println(fruits); // [Apple, Mango, Banana, Cherry]

```

---

### 🔹 Accessing Elements

```Java
String firstFruit = fruits.get(0); // Apple
System.out.println(firstFruit);

// Modify element
fruits.set(2, "Orange"); // replaces Banana
System.out.println(fruits); // [Apple, Mango, Orange, Cherry]

```

---

### 🔹 Removing Elements

```Java
fruits.remove("Mango");   // remove by value
fruits.remove(1);         // remove by index
System.out.println(fruits); // [Apple, Cherry]

```

---

### 🔹 Looping through ArrayList

```Java
// Using for loop
for(int i = 0; i < fruits.size(); i++) {
    System.out.println(fruits.get(i));
}

// Using enhanced for loop
for(String fruit : fruits) {
    System.out.println(fruit);
}

// Using lambda (Java 8+)
fruits.forEach(fruit -> System.out.println(fruit));

```

---

### 🔹 Other Useful Methods

|Method|Description|
|---|---|
|`size()`|Returns number of elements|
|`isEmpty()`|Checks if list is empty|
|`contains(Object o)`|Checks if element exists|
|`clear()`|Removes all elements|
|`indexOf(Object o)`|Returns first occurrence index|
|`lastIndexOf(Object o)`|Returns last occurrence index|
|`toArray()`|Converts list to array|

---

### 🔹 Key Points

1. **Dynamic size**, unlike arrays.
2. Maintains **insertion order**.
3. Allows **duplicate elements**.
4. **Random access** supported (`get(index)` is O(1)).
5. Use **Generics** for type safety.

---

### 🔹 Gotchas / Notes

- Adding/removing elements in **middle** can be **costly (O(n))** due to shifting.
- Not synchronized → use `Collections.synchronizedList()` if thread-safe access is needed.
- For **primitive types**, use wrapper classes (`Integer`, `Double`, etc.).

---

## 2. 📊 Summary Table

|Operation|Syntax / Example|Notes|
|---|---|---|
|Create|`ArrayList<Type> list = new ArrayList<>();`|Use generics|
|Add|`list.add(element)`|Adds to end|
|Add at index|`list.add(index, element)`|Shifts subsequent elements|
|Get|`list.get(index)`|Random access|
|Set|`list.set(index, element)`|Replace element|
|Remove|`list.remove(index or object)`|By index or value|
|Size|`list.size()`|Number of elements|
|Loop|`for(Type t : list)`|Enhanced for / lambda|

---

### 🔹 Real-World Example

**Managing Student Names**

```Java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<String> students = new ArrayList<>();

        // Add students
        students.add("Alice");
        students.add("Bob");
        students.add("Charlie");

        // Print all students
        students.forEach(System.out::println);

        // Modify student
        students.set(1, "David");

        // Remove student
        students.remove("Charlie");

        System.out.println("Updated list: " + students); // [Alice, David]
    }
}

```

- Demonstrates **adding, modifying, removing, looping** over `ArrayList`.

---

# LinkedList

## 1. Full Explanation

### 🔹 What is LinkedList?

- **LinkedList** is a **doubly-linked list implementation** in `**java.util**` **package**.
- Implements **List, Deque, Queue** interfaces → can be used as **list, stack, or queue**.
- Maintains **insertion order** and allows **duplicate elements**.
- Each element (node) contains **data** and **pointers to previous and next nodes**.

---

### 🔹 Import Statement

```Java
import java.util.LinkedList;

```

---

### 🔹 Creating a LinkedList

```Java
// Without generics (not recommended)
LinkedList list = new LinkedList();

// With generics (preferred)
LinkedList<Integer> numbers = new LinkedList<>();
LinkedList<String> names = new LinkedList<>();

```

---

### 🔹 Adding Elements

```Java
LinkedList<String> fruits = new LinkedList<>();

// Add at end
fruits.add("Apple");
fruits.add("Banana");

// Add at specific index
fruits.add(1, "Mango"); // [Apple, Mango, Banana]

// Add first / last
fruits.addFirst("Strawberry"); // [Strawberry, Apple, Mango, Banana]
fruits.addLast("Cherry");      // [Strawberry, Apple, Mango, Banana, Cherry]

```

---

### 🔹 Accessing Elements

```Java
System.out.println(fruits.get(0));    // Strawberry
System.out.println(fruits.getFirst()); // Strawberry
System.out.println(fruits.getLast());  // Cherry

// Modify element
fruits.set(2, "Orange"); // replaces Mango
System.out.println(fruits); // [Strawberry, Apple, Orange, Banana, Cherry]

```

---

### 🔹 Removing Elements

```Java
fruits.remove("Apple");    // remove by value
fruits.remove(1);          // remove by index
fruits.removeFirst();      // remove first element
fruits.removeLast();       // remove last element
System.out.println(fruits); // [Orange, Banana]

```

---

### 🔹 Looping through LinkedList

```Java
// Using for loop
for(int i = 0; i < fruits.size(); i++) {
    System.out.println(fruits.get(i));
}

// Using enhanced for loop
for(String fruit : fruits) {
    System.out.println(fruit);
}

// Using lambda (Java 8+)
fruits.forEach(fruit -> System.out.println(fruit));

```

---

### 🔹 Other Useful Methods

|Method|Description|
|---|---|
|`size()`|Returns number of elements|
|`isEmpty()`|Checks if list is empty|
|`contains(Object o)`|Checks if element exists|
|`clear()`|Removes all elements|
|`indexOf(Object o)`|Returns first occurrence index|
|`lastIndexOf(Object o)`|Returns last occurrence index|
|`peek()`, `peekFirst()`, `peekLast()`|Returns element without removing (queue)|
|`poll()`, `pollFirst()`, `pollLast()`|Removes and returns element (queue)|
|`push()`, `pop()`|Stack operations|

---

### 🔹 Key Points

1. **Dynamic size**, grows/shrinks as needed.
2. **Maintains insertion order** and allows duplicates.
3. **Faster insertions/deletions** at head/tail or middle compared to `ArrayList` (no shifting).
4. **Slower random access** (`get(index)` is O(n)) compared to `ArrayList`.
5. Implements **List, Deque, Queue** → versatile data structure.

---

### 🔹 Gotchas / Notes

- Use **LinkedList** when **frequent insertions/deletions** are needed.
- Use **ArrayList** when **frequent random access** is needed.
- Iterating with **for loop and get(index)** is **less efficient**; use **iterator/enhanced for loop**.

---

## 2. 📊 Summary Table

|Operation|Syntax / Example|Notes|
|---|---|---|
|Create|`LinkedList<Type> list = new LinkedList<>();`|Use generics|
|Add end|`list.add(element)`|Adds at tail|
|Add first/last|`addFirst() / addLast()`|Deque operations|
|Add at index|`list.add(index, element)`|Inserts at index|
|Get element|`get(index) / getFirst() / getLast()`|Access element|
|Set element|`set(index, element)`|Replace element|
|Remove|`remove(index/object) / removeFirst()/removeLast()`|Remove element|
|Size|`size()`|Number of elements|
|Loop|`for(Type t : list)`|Enhanced for / lambda|

---

### 🔹 Real-World Example

**Task Management Queue**

```Java
import java.util.LinkedList;

public class Main {
    public static void main(String[] args) {
        LinkedList<String> tasks = new LinkedList<>();

        // Add tasks
        tasks.add("Write report");
        tasks.add("Email client");
        tasks.addFirst("Check emails"); // priority task

        // Process tasks
        while(!tasks.isEmpty()) {
            String task = tasks.poll(); // removes from front
            System.out.println("Processing: " + task);
        }
    }
}

```

✅ Output:

```Plain
Processing: Check emails
Processing: Write report
Processing: Email client

```

- Demonstrates **LinkedList as a queue** with **addFirst, addLast, poll**.

# HashSet

## 1. Full Explanation

### 🔹 What is HashSet?

- **HashSet** is a **collection that implements the Set interface**.
- **Stores unique elements only** → no duplicates.
- **Unordered** → does **not maintain insertion order**.
- Backed by a **hash table** → **fast add, remove, contains** operations (average O(1)).
- Null element is allowed (only **one null**).

---

### 🔹 Import Statement

```Java
import java.util.HashSet;

```

---

### 🔹 Creating a HashSet

```Java
// Without generics (not recommended)
HashSet set = new HashSet();

// With generics (preferred)
HashSet<Integer> numbers = new HashSet<>();
HashSet<String> names = new HashSet<>();

```

---

### 🔹 Adding Elements

```Java
HashSet<String> fruits = new HashSet<>();
fruits.add("Apple");
fruits.add("Banana");
fruits.add("Cherry");
fruits.add("Apple"); // duplicate, ignored
System.out.println(fruits); // [Banana, Apple, Cherry] - unordered

```

- **Duplicates are ignored** automatically.

---

### 🔹 Removing Elements

```Java
fruits.remove("Banana");   // remove by value
System.out.println(fruits); // [Apple, Cherry]

fruits.clear();            // removes all elements
System.out.println(fruits); // []

```

---

### 🔹 Checking Elements

```Java
fruits.add("Apple");
fruits.add("Mango");

System.out.println(fruits.contains("Apple")); // true
System.out.println(fruits.contains("Banana")); // false
System.out.println(fruits.isEmpty()); // false

```

---

### 🔹 Looping through HashSet

```Java
HashSet<String> fruits = new HashSet<>();
fruits.add("Apple");
fruits.add("Banana");
fruits.add("Cherry");

// Using enhanced for loop
for(String fruit : fruits) {
    System.out.println(fruit);
}

// Using lambda (Java 8+)
fruits.forEach(System.out::println);

// Using iterator
Iterator<String> it = fruits.iterator();
while(it.hasNext()) {
    System.out.println(it.next());
}

```

> Note: Order of elements is not guaranteed.

---

### 🔹 Other Useful Methods

|Method|Description|
|---|---|
|`size()`|Returns number of elements|
|`isEmpty()`|Checks if set is empty|
|`contains(Object o)`|Checks if element exists|
|`clear()`|Removes all elements|
|`addAll(Collection c)`|Adds all elements from another collection|
|`removeAll(Collection c)`|Removes all elements present in another collection|
|`retainAll(Collection c)`|Keeps only elements present in another collection|

---

### 🔹 Key Points

1. **No duplicates allowed**.
2. **Unordered** collection.
3. Backed by a **hash table** → fast operations.
4. Null allowed (only once).
5. Implements **Set interface** → does **not support indexed access**.

---

### 🔹 Gotchas / Notes

- Iteration order is **not predictable**.
- Use **LinkedHashSet** if **insertion order** must be preserved.
- Use **TreeSet** if **sorted order** is required.

---

## 2. 📊 Summary Table

|Operation|Syntax / Example|Notes|
|---|---|---|
|Create|`HashSet<Type> set = new HashSet<>();`|Use generics|
|Add|`set.add(element)`|Ignores duplicates|
|Remove|`set.remove(element)`|Removes specified element|
|Contains|`set.contains(element)`|Check if element exists|
|Size|`set.size()`|Number of elements|
|Clear|`set.clear()`|Removes all elements|
|Loop|`for(Type t : set)`|Enhanced for / lambda / iterator|

---

### 🔹 Real-World Example

**Unique Usernames**

```Java
import java.util.HashSet;

public class Main {
    public static void main(String[] args) {
        HashSet<String> usernames = new HashSet<>();

        usernames.add("Alice");
        usernames.add("Bob");
        usernames.add("Charlie");
        usernames.add("Alice"); // duplicate ignored

        System.out.println("All usernames:");
        usernames.forEach(System.out::println); // order not guaranteed

        System.out.println("Contains 'Bob'? " + usernames.contains("Bob")); // true

        usernames.remove("Charlie");
        System.out.println("After removal: " + usernames); // [Alice, Bob]
    }
}

```

- Demonstrates **HashSet storing unique elements**, **checking existence**, and **removing elements**.

# TreeSet

## 1. Full Explanation

### 🔹 What is TreeSet?

- **TreeSet** is a **collection that implements the Set interface**.
- **Stores unique elements only** → no duplicates.
- **Sorted order** → elements are stored in **natural ascending order** (or using a custom comparator).
- Backed by a **Red-Black tree** → operations like add, remove, search are **O(log n)**.
- Does **not allow null elements**.

---

### 🔹 Import Statement

```Java
import java.util.TreeSet;

```

---

### 🔹 Creating a TreeSet

```Java
// Without generics (not recommended)
TreeSet set = new TreeSet();

// With generics (preferred)
TreeSet<Integer> numbers = new TreeSet<>();
TreeSet<String> names = new TreeSet<>();

```

- Can also provide a **custom comparator** for custom sorting:

```Java
TreeSet<String> namesDesc = new TreeSet<>((a, b) -> b.compareTo(a)); // descending order

```

---

### 🔹 Adding Elements

```Java
TreeSet<String> fruits = new TreeSet<>();
fruits.add("Apple");
fruits.add("Banana");
fruits.add("Cherry");
fruits.add("Apple"); // duplicate ignored

System.out.println(fruits); // [Apple, Banana, Cherry] - sorted order

```

---

### 🔹 Removing Elements

```Java
fruits.remove("Banana");
System.out.println(fruits); // [Apple, Cherry]

fruits.clear(); // removes all elements
System.out.println(fruits); // []

```

---

### 🔹 Checking Elements

```Java
fruits.add("Apple");
fruits.add("Mango");

System.out.println(fruits.contains("Apple")); // true
System.out.println(fruits.contains("Banana")); // false
System.out.println(fruits.isEmpty()); // false

```

---

### 🔹 Looping through TreeSet

```Java
TreeSet<String> fruits = new TreeSet<>();
fruits.add("Apple");
fruits.add("Banana");
fruits.add("Cherry");

// Using enhanced for loop
for(String fruit : fruits) {
    System.out.println(fruit);
}

// Using lambda (Java 8+)
fruits.forEach(System.out::println);

// Using iterator
Iterator<String> it = fruits.iterator();
while(it.hasNext()) {
    System.out.println(it.next());
}

```

> Note: Elements are always in sorted order.

---

### 🔹 Other Useful Methods

|Method|Description|
|---|---|
|`size()`|Returns number of elements|
|`isEmpty()`|Checks if set is empty|
|`contains(Object o)`|Checks if element exists|
|`clear()`|Removes all elements|
|`first()`|Returns first (lowest) element|
|`last()`|Returns last (highest) element|
|`headSet(toElement)`|Returns elements less than `toElement`|
|`tailSet(fromElement)`|Returns elements greater than or equal to `fromElement`|
|`subSet(from, to)`|Returns elements in range `[from, to)`|

---

### 🔹 Key Points

1. **No duplicates allowed**.
2. **Sorted order** → natural or custom comparator.
3. Backed by **Red-Black tree** → O(log n) operations.
4. **Does not allow null** (throws `NullPointerException`).
5. Implements **Set interface** → no indexed access.

---

### 🔹 Gotchas / Notes

- For **null-safe sorted sets**, use **TreeSet with Comparator** that handles null.
- If **insertion order** is needed, use **LinkedHashSet** instead.
- Use **HashSet** if **sorting not required** → faster O(1) operations.

---

## 2. 📊 Summary Table

|Operation|Syntax / Example|Notes|
|---|---|---|
|Create|`TreeSet<Type> set = new TreeSet<>();`|Use generics|
|Add|`set.add(element)`|Ignores duplicates, sorted|
|Remove|`set.remove(element)`|Removes specified element|
|Contains|`set.contains(element)`|Check existence|
|Size|`set.size()`|Number of elements|
|Clear|`set.clear()`|Removes all elements|
|Loop|`for(Type t : set)`|Enhanced for / lambda / iterator|
|First / Last|`set.first() / set.last()`|Lowest / highest element|
|Subsets|`headSet(), tailSet(), subSet()`|Returns part of set|

---

### 🔹 Real-World Example

**Sorted Unique Product Names**

```Java
import java.util.TreeSet;

public class Main {
    public static void main(String[] args) {
        TreeSet<String> products = new TreeSet<>();

        products.add("Laptop");
        products.add("Phone");
        products.add("Tablet");
        products.add("Laptop"); // duplicate ignored

        System.out.println("All products (sorted): " + products); // [Laptop, Phone, Tablet]

        System.out.println("First product: " + products.first()); // Laptop
        System.out.println("Last product: " + products.last());   // Tablet

        // Products before "Phone"
        System.out.println("HeadSet: " + products.headSet("Phone")); // [Laptop]

        // Products from "Phone"
        System.out.println("TailSet: " + products.tailSet("Phone")); // [Phone, Tablet]
    }
}

```

- Demonstrates **TreeSet storing unique elements in sorted order**, **first/last access**, and **subset operations**.

# HashMap

## 1. Full Explanation

### 🔹 What is HashMap?

- **HashMap** is a **key-value pair collection** in `**java.util**` **package**.
- Implements **Map interface** → stores data as **(key, value) pairs**.
- **Keys are unique**, **values can be duplicate**.
- **Unordered** → does **not maintain insertion order**.
- **Allows one null key** and multiple null values.
- Backed by a **hash table** → **fast retrieval, insertion, and deletion** (average O(1)).

---

### 🔹 Import Statement

```Java
import java.util.HashMap;

```

---

### 🔹 Creating a HashMap

```Java
// Without generics (not recommended)
HashMap map = new HashMap();

// With generics (preferred)
HashMap<Integer, String> idNameMap = new HashMap<>();
HashMap<String, Integer> nameScoreMap = new HashMap<>();

```

---

### 🔹 Adding Elements

```Java
HashMap<String, Integer> scores = new HashMap<>();

scores.put("Alice", 90);
scores.put("Bob", 85);
scores.put("Charlie", 95);
scores.put("Alice", 100); // key "Alice" updated

System.out.println(scores); // {Alice=100, Bob=85, Charlie=95}

```

---

### 🔹 Accessing Elements

```Java
int aliceScore = scores.get("Alice");   // 100
System.out.println(aliceScore);

// Using getOrDefault to avoid null
int daveScore = scores.getOrDefault("Dave", 0); // 0
System.out.println(daveScore);

```

---

### 🔹 Removing Elements

```Java
scores.remove("Bob");          // removes key "Bob"
System.out.println(scores);    // {Alice=100, Charlie=95}

scores.clear();                // removes all entries
System.out.println(scores);    // {}

```

---

### 🔹 Checking Elements

```Java
scores.put("Alice", 90);
scores.put("Bob", 85);

System.out.println(scores.containsKey("Alice"));   // true
System.out.println(scores.containsValue(85));      // true
System.out.println(scores.isEmpty());              // false

```

---

### 🔹 Looping through HashMap

```Java
HashMap<String, Integer> scores = new HashMap<>();
scores.put("Alice", 90);
scores.put("Bob", 85);
scores.put("Charlie", 95);

// Using entrySet
for(Map.Entry<String, Integer> entry : scores.entrySet()) {
    System.out.println(entry.getKey() + " : " + entry.getValue());
}

// Using keySet
for(String key : scores.keySet()) {
    System.out.println(key + " : " + scores.get(key));
}

// Using lambda (Java 8+)
scores.forEach((key, value) -> System.out.println(key + " : " + value));

```

> Note: Iteration order is not guaranteed.

---

### 🔹 Other Useful Methods

|Method|Description|
|---|---|
|`size()`|Returns number of key-value pairs|
|`isEmpty()`|Checks if map is empty|
|`containsKey(key)`|Checks if key exists|
|`containsValue(value)`|Checks if value exists|
|`putAll(Map m)`|Adds all entries from another map|
|`replace(key, value)`|Replaces value for a given key|
|`keySet()`|Returns a Set of keys|
|`values()`|Returns a Collection of values|
|`entrySet()`|Returns a Set of Map.Entry objects|

---

### 🔹 Key Points

1. Stores data as **key-value pairs**.
2. **Keys unique**, **values can be duplicate**.
3. **Unordered** collection → use `LinkedHashMap` for insertion order.
4. **Null key allowed (only one)**, multiple null values allowed.
5. **Fast lookup** → average O(1).

---

### 🔹 Gotchas / Notes

- HashMap is **not thread-safe** → use `ConcurrentHashMap` for multi-threaded access.
- Keys must **implement** `**hashCode()**` **and** `**equals()**` properly.
- Iteration order is **not guaranteed**; for **sorted order** use `TreeMap`.

---

## 2. 📊 Summary Table

|Operation|Syntax / Example|Notes|
|---|---|---|
|Create|`HashMap<K,V> map = new HashMap<>();`|Use generics|
|Add / Update|`map.put(key, value)`|Adds or updates key-value pair|
|Get|`map.get(key)`|Returns value for key|
|Get with default|`map.getOrDefault(key, defaultValue)`|Avoids null|
|Remove|`map.remove(key)`|Removes entry by key|
|Contains Key/Value|`map.containsKey(k)/containsValue(v)`|Check existence|
|Size|`map.size()`|Number of entries|
|Clear|`map.clear()`|Removes all entries|
|Loop|`for(Map.Entry<K,V> e : map.entrySet())`|Iteration|

---

### 🔹 Real-World Example

**Student Scores Mapping**

```Java
import java.util.HashMap;
import java.util.Map;

public class Main {
    public static void main(String[] args) {
        HashMap<String, Integer> studentScores = new HashMap<>();

        // Add students
        studentScores.put("Alice", 90);
        studentScores.put("Bob", 85);
        studentScores.put("Charlie", 95);

        // Print all students
        studentScores.forEach((name, score) -> System.out.println(name + ": " + score));

        // Access a specific student
        System.out.println("Alice's score: " + studentScores.get("Alice"));

        // Remove a student
        studentScores.remove("Bob");
        System.out.println("After removal: " + studentScores);
    }
}

```

- Demonstrates **adding, updating, accessing, removing, and iterating** over `HashMap`.

# TreeMap

## 1. Full Explanation

### 🔹 What is TreeMap?

- **TreeMap** is a **Map implementation** that stores **key-value pairs** in **sorted order of keys**.
- Implements **NavigableMap and SortedMap interfaces**.
- **Keys are unique**, **values can be duplicate**.
- Backed by a **Red-Black tree** → operations like add, remove, search are **O(log n)**.
- **Null keys are not allowed** (throws `NullPointerException`), but null values are allowed.

---

### 🔹 Import Statement

```Java
import java.util.TreeMap;

```

---

### 🔹 Creating a TreeMap

```Java
// Without generics (not recommended)
TreeMap map = new TreeMap();

// With generics (preferred)
TreeMap<Integer, String> idNameMap = new TreeMap<>();
TreeMap<String, Integer> nameScoreMap = new TreeMap<>();

```

- Can also provide a **custom comparator** for custom key ordering:

```Java
TreeMap<String, Integer> descMap = new TreeMap<>((a, b) -> b.compareTo(a)); // descending order keys

```

---

### 🔹 Adding Elements

```Java
TreeMap<String, Integer> scores = new TreeMap<>();
scores.put("Alice", 90);
scores.put("Bob", 85);
scores.put("Charlie", 95);
scores.put("Alice", 100); // key "Alice" updated

System.out.println(scores); // {Alice=100, Bob=85, Charlie=95} - sorted keys

```

---

### 🔹 Accessing Elements

```Java
int aliceScore = scores.get("Alice");   // 100
System.out.println(aliceScore);

// Using getOrDefault to avoid null
int daveScore = scores.getOrDefault("Dave", 0); // 0
System.out.println(daveScore);

```

---

### 🔹 Removing Elements

```Java
scores.remove("Bob");          // removes key "Bob"
System.out.println(scores);    // {Alice=100, Charlie=95}

scores.clear();                // removes all entries
System.out.println(scores);    // {}

```

---

### 🔹 Checking Elements

```Java
scores.put("Alice", 90);
scores.put("Bob", 85);

System.out.println(scores.containsKey("Alice"));   // true
System.out.println(scores.containsValue(85));      // true
System.out.println(scores.isEmpty());              // false

```

---

### 🔹 Looping through TreeMap

```Java
TreeMap<String, Integer> scores = new TreeMap<>();
scores.put("Alice", 90);
scores.put("Bob", 85);
scores.put("Charlie", 95);

// Using entrySet
for(Map.Entry<String, Integer> entry : scores.entrySet()) {
    System.out.println(entry.getKey() + " : " + entry.getValue());
}

// Using keySet
for(String key : scores.keySet()) {
    System.out.println(key + " : " + scores.get(key));
}

// Using lambda (Java 8+)
scores.forEach((key, value) -> System.out.println(key + " : " + value));

```

> Note: Iteration order is sorted by keys.

---

### 🔹 Other Useful Methods

|Method|Description|
|---|---|
|`size()`|Returns number of key-value pairs|
|`isEmpty()`|Checks if map is empty|
|`containsKey(key)`|Checks if key exists|
|`containsValue(value)`|Checks if value exists|
|`firstKey()`|Returns first (lowest) key|
|`lastKey()`|Returns last (highest) key|
|`headMap(toKey)`|Returns keys less than `toKey`|
|`tailMap(fromKey)`|Returns keys greater than or equal to `fromKey`|
|`subMap(fromKey, toKey)`|Returns keys in range `[fromKey, toKey)`|
|`putAll(Map m)`|Adds all entries from another map|
|`replace(key, value)`|Replaces value for a given key|

---

### 🔹 Key Points

1. **Sorted key order** → natural or custom comparator.
2. **No null keys** allowed.
3. **Keys unique**, **values can be duplicates**.
4. Backed by **Red-Black tree** → O(log n) operations.
5. Implements **Map interface** → no indexed access.

---

### 🔹 Gotchas / Notes

- Use **TreeMap** when **sorted key order** is required.
- Use **HashMap** when **fast lookup without ordering** is sufficient.
- Null keys **throw NullPointerException**.
- Iteration over `entrySet()` or `keySet()` gives **sorted order by keys**.

---

## 2. 📊 Summary Table

|Operation|Syntax / Example|Notes|
|---|---|---|
|Create|`TreeMap<K,V> map = new TreeMap<>();`|Use generics|
|Add / Update|`map.put(key, value)`|Adds or updates key-value pair|
|Get|`map.get(key)`|Returns value for key|
|Get with default|`map.getOrDefault(key, defaultValue)`|Avoids null|
|Remove|`map.remove(key)`|Removes entry by key|
|Contains Key/Value|`map.containsKey(k)/containsValue(v)`|Check existence|
|Size|`map.size()`|Number of entries|
|Clear|`map.clear()`|Removes all entries|
|Loop|`for(Map.Entry<K,V> e : map.entrySet())`|Iteration in sorted key order|
|First / Last Key|`map.firstKey()/map.lastKey()`|Lowest / highest key|
|Submaps|`headMap(), tailMap(), subMap()`|Return subset of map|

---

### 🔹 Real-World Example

**Sorted Student Scores**

```Java
import java.util.TreeMap;
import java.util.Map;

public class Main {
    public static void main(String[] args) {
        TreeMap<String, Integer> studentScores = new TreeMap<>();

        studentScores.put("Alice", 90);
        studentScores.put("Bob", 85);
        studentScores.put("Charlie", 95);

        System.out.println("All scores (sorted by name):");
        studentScores.forEach((name, score) -> System.out.println(name + ": " + score));

        System.out.println("First student: " + studentScores.firstKey()); // Alice
        System.out.println("Last student: " + studentScores.lastKey());   // Charlie

        System.out.println("Students before Bob: " + studentScores.headMap("Bob")); // {Alice=90}
    }
}

```

- Demonstrates **TreeMap storing unique keys in sorted order**, **first/last key**, and **submap operations**.

# Stack

## 1. Full Explanation

### 🔹 What is Stack?

- **Stack** is a **LIFO (Last-In-First-Out)** data structure.
- In Java, `**java.util.Stack**` is a **class that extends Vector**.
- Supports typical **stack operations** like **push, pop, peek, search**.
- Useful for **undo mechanisms, expression evaluation, recursion simulation**, etc.

---

### 🔹 Import Statement

```Java
import java.util.Stack;

```

---

### 🔹 Creating a Stack

```Java
// Without generics (not recommended)
Stack stack = new Stack();

// With generics (preferred)
Stack<Integer> numbers = new Stack<>();
Stack<String> letters = new Stack<>();

```

---

### 🔹 Basic Operations

### 1️⃣ Push (Add element on top)

```Java
Stack<String> stack = new Stack<>();
stack.push("A");
stack.push("B");
stack.push("C");
System.out.println(stack); // [A, B, C]

```

### 2️⃣ Pop (Remove and return top element)

```Java
String top = stack.pop();
System.out.println("Popped: " + top); // C
System.out.println(stack); // [A, B]

```

### 3️⃣ Peek (Return top element without removing)

```Java
String topElement = stack.peek();
System.out.println("Top element: " + topElement); // B
System.out.println(stack); // [A, B]

```

### 4️⃣ Search (Return 1-based position from top)

```Java
int position = stack.search("A");
System.out.println("Position of A: " + position); // 2

```

---

### 🔹 Checking Stack

```Java
System.out.println(stack.isEmpty()); // false
System.out.println(stack.size());    // 2

```

---

### 🔹 Looping through Stack

```Java
// Using enhanced for loop
for(String s : stack) {
    System.out.println(s);
}

// Using iterator
Iterator<String> it = stack.iterator();
while(it.hasNext()) {
    System.out.println(it.next());
}

```

> Note: Iterating from bottom to top (as Vector). Pop always removes top.

---

### 🔹 Key Points

1. **LIFO (Last-In-First-Out)** → last element added is removed first.
2. Stack extends **Vector** → inherits methods from Vector.
3. Supports **push, pop, peek, search** operations.
4. Use **Generics** for type safety.
5. For **thread-safe LIFO**, Stack is synchronized; for modern alternatives, use **Deque** (`ArrayDeque`) for non-synchronized stack.

---

### 🔹 Gotchas / Notes

- **Pop on empty stack** → throws `EmptyStackException`.
- For **better performance**, use `ArrayDeque` instead of `Stack` in new applications.
- Iteration goes **bottom → top**, pop removes **top**.

---

## 2. 📊 Summary Table

|Operation|Syntax / Example|Notes|
|---|---|---|
|Create|`Stack<Type> stack = new Stack<>();`|Use generics|
|Push|`stack.push(element)`|Add to top|
|Pop|`stack.pop()`|Remove top element|
|Peek|`stack.peek()`|View top element|
|Search|`stack.search(element)`|1-based position from top|
|Is Empty|`stack.isEmpty()`|Check if empty|
|Size|`stack.size()`|Number of elements|
|Loop|`for(Type t : stack)`|Iterate bottom → top|

---

### 🔹 Real-World Example

**Undo Operation in Text Editor**

```Java
import java.util.Stack;

public class Main {
    public static void main(String[] args) {
        Stack<String> undoStack = new Stack<>();

        // User actions
        undoStack.push("Type A");
        undoStack.push("Type B");
        undoStack.push("Delete A");

        System.out.println("Current actions: " + undoStack);

        // Undo last action
        String lastAction = undoStack.pop();
        System.out.println("Undo: " + lastAction);

        System.out.println("Remaining actions: " + undoStack);
    }
}

```

✅ Output:

```Plain
Current actions: [Type A, Type B, Delete A]
Undo: Delete A
Remaining actions: [Type A, Type B]

```

- Demonstrates **push, pop, peek** operations with a **real-world use case**.

# Queue

## 1. Full Explanation

### 🔹 What is Queue?

- **Queue** is a **FIFO (First-In-First-Out)** data structure.
- In Java, `**java.util.Queue**` is an **interface**, implemented by classes like **LinkedList, ArrayDeque, PriorityQueue**.
- Elements are added at **rear (offer/add)** and removed from **front (poll/remove)**.
- Used for **task scheduling, buffering, breadth-first search**, etc.

---

### 🔹 Import Statement

```Java
import java.util.Queue;
import java.util.LinkedList;

```

---

### 🔹 Creating a Queue

```Java
// Using LinkedList (common implementation)
Queue<String> queue = new LinkedList<>();

// Using ArrayDeque (more efficient)
Queue<String> queue2 = new ArrayDeque<>();

```

---

### 🔹 Adding Elements

```Java
queue.add("A");      // throws exception if fails
queue.offer("B");    // returns false if fails
queue.offer("C");

System.out.println(queue); // [A, B, C]

```

- `add()` and `offer()` both add to **rear** of the queue.
- `offer()` is preferred for **capacity-restricted queues**.

---

### 🔹 Removing Elements

```Java
String first = queue.poll();  // removes and returns front, returns null if empty
System.out.println(first);    // A
System.out.println(queue);    // [B, C]

String removed = queue.remove(); // removes front, throws exception if empty
System.out.println(removed);    // B
System.out.println(queue);      // [C]

```

---

### 🔹 Accessing Elements

```Java
queue.add("D");
queue.add("E");

System.out.println(queue.peek());   // C (front element, returns null if empty)
System.out.println(queue.element()); // C (front element, throws exception if empty)

```

---

### 🔹 Looping through Queue

```Java
for(String item : queue) {
    System.out.println(item);
}

// Using iterator
Iterator<String> it = queue.iterator();
while(it.hasNext()) {
    System.out.println(it.next());
}

```

> Note: Iteration goes front → rear.

---

### 🔹 Other Useful Methods

|Method|Description|
|---|---|
|`size()`|Returns number of elements|
|`isEmpty()`|Checks if queue is empty|
|`contains(Object o)`|Checks if element exists|
|`clear()`|Removes all elements|
|`offer(E e)`|Adds element at rear, returns false if fails|
|`add(E e)`|Adds element at rear, throws exception if fails|
|`poll()`|Removes and returns front, returns null if empty|
|`remove()`|Removes and returns front, throws exception if empty|
|`peek()`|Returns front element, null if empty|
|`element()`|Returns front element, throws exception if empty|

---

### 🔹 Key Points

1. **FIFO (First-In-First-Out)** → first element added is removed first.
2. **Queue is an interface** → implemented by LinkedList, ArrayDeque, PriorityQueue.
3. Use **LinkedList** for **flexible size**, **ArrayDeque** for **better performance**.
4. **peek / poll** vs **element / remove** → safe vs exception-throwing methods.

---

### 🔹 Gotchas / Notes

- **PriorityQueue** implements Queue with **priority ordering**, not FIFO.
- Iterating does not remove elements; use **poll()** to dequeue.
- **Null elements** are generally **not allowed** in most queue implementations (except LinkedList).

---

## 2. 📊 Summary Table

|Operation|Syntax / Example|Notes|
|---|---|---|
|Create|`Queue<Type> queue = new LinkedList<>();`|Use LinkedList or ArrayDeque|
|Add|`queue.add(e)` / `queue.offer(e)`|Add at rear|
|Remove|`queue.remove()` / `queue.poll()`|Remove from front|
|Peek|`queue.peek()` / `queue.element()`|View front element|
|Size|`queue.size()`|Number of elements|
|Is Empty|`queue.isEmpty()`|Check if empty|
|Loop|`for(Type t : queue)`|Iterate front → rear|

---

### 🔹 Real-World Example

**Task Scheduling Queue**

```Java
import java.util.Queue;
import java.util.LinkedList;

public class Main {
    public static void main(String[] args) {
        Queue<String> tasks = new LinkedList<>();

        // Add tasks
        tasks.offer("Task 1");
        tasks.offer("Task 2");
        tasks.offer("Task 3");

        System.out.println("All tasks: " + tasks);

        // Process tasks
        while(!tasks.isEmpty()) {
            String task = tasks.poll();
            System.out.println("Processing: " + task);
        }
    }
}

```

✅ Output:

```Plain
All tasks: [Task 1, Task 2, Task 3]
Processing: Task 1
Processing: Task 2
Processing: Task 3

```

- Demonstrates **adding, polling, and iterating** in a **FIFO queue**.