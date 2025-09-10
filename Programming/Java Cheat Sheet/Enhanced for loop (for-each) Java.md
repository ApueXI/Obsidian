---
Created: 2025-08-25T19:34
tags:
  - Control-Flow
---
## 1. Full Explanation

### 🔹 What is the Enhanced For Loop?

- Introduced in **Java 5**.
- Simplifies **iteration over arrays or collections**.
- Automatically retrieves each element **without using an index**.

### 🔹 Syntax

```Java
for (Type element : collection) {
    // use element
}

```

- `Type` → type of the elements in array or collection.
- `element` → temporary variable holding current value.
- `collection` → array or object implementing `Iterable` (e.g., `ArrayList`).

---

### 🔹 Example with Array

```Java
int[] numbers = {1, 2, 3, 4, 5};

for (int num : numbers) {
    System.out.println(num);
}

```

✅ Output:

```Plain
1
2
3
4
5

```

---

### 🔹 Example with Collection (`ArrayList`)

```Java
import java.util.ArrayList;

public class ForEachExample {
    public static void main(String[] args) {
        ArrayList<String> fruits = new ArrayList<>();
        fruits.add("Apple");
        fruits.add("Banana");
        fruits.add("Cherry");

        for (String fruit : fruits) {
            System.out.println(fruit);
        }
    }
}

```

✅ Output:

```Plain
Apple
Banana
Cherry

```

---

### 🔹 Gotchas / Notes

- **Read-only**: you cannot modify the array/collection elements using the enhanced for variable directly.
    
    ```Java
    for (int num : numbers) {
        num = num * 2; // doesn't change original array
    }
    
    ```
    
- Use **classic for loop** if you need the index or to modify elements.
- Works with **arrays,** `**ArrayList**`**,** `**LinkedList**`**,** `**HashSet**`**, etc.**

---

## 2. 📊 Summary Table

|Feature|Syntax|Example|Notes|
|---|---|---|---|
|Enhanced for loop|`for(Type var : collection){}`|`for(String f : fruits){}`|Simplifies iteration|
|Works with|Arrays, Collections|`int[] arr, ArrayList<String>`|Must be iterable|
|Modifying values|❌ Cannot modify directly|`var = ...` changes temp only|Use classic for if needed|
|Readability|✅ Very readable|Loops without index|Preferred when index not needed|

---

## 3. 🌍 Real-World Example

Imagine a **Shopping Cart System**:

```Java
import java.util.ArrayList;

public class ShoppingCart {
    public static void main(String[] args) {
        ArrayList<String> cart = new ArrayList<>();
        cart.add("Laptop");
        cart.add("Mouse");
        cart.add("Keyboard");

        System.out.println("Items in your cart:");
        for (String item : cart) {
            System.out.println("- " + item);
        }
    }
}

```

✅ Output:

```Plain
Items in your cart:
- Laptop
- Mouse
- Keyboard

```

- Cleaner and easier than using a classic `for` loop with an index.