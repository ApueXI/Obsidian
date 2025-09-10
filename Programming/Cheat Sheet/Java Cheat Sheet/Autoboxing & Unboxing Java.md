---
Created: 2025-08-25T20:05
tags:
  - Special-Types
---
## 1. Full Explanation

### 🔹 What is Autoboxing?

- **Autoboxing** is the **automatic conversion of a primitive type** to its **corresponding wrapper class**.
- Example: `int → Integer`, `double → Double`

```Java
int num = 10;
Integer obj = num; // Autoboxing: primitive → wrapper

```

- No manual object creation needed (`Integer.valueOf(num)` happens automatically).

---

### 🔹 What is Unboxing?

- **Unboxing** is the **automatic conversion of a wrapper class object** back to its **primitive type**.
- Example: `Integer → int`, `Double → double`

```Java
Integer obj = 20;
int num = obj; // Unboxing: wrapper → primitive

```

- No need to call `obj.intValue()` manually.

---

### 🔹 Examples

```Java
public class Main {
    public static void main(String[] args) {
        // Autoboxing
        int a = 10;
        Integer aObj = a; // int → Integer
        System.out.println("Autoboxed: " + aObj);

        // Unboxing
        Integer bObj = 20;
        int b = bObj; // Integer → int
        System.out.println("Unboxed: " + b);

        // Using in Collections
        ArrayList<Integer> list = new ArrayList<>();
        list.add(30);   // autoboxed
        int value = list.get(0); // unboxed
        System.out.println("Value from list: " + value);
    }
}

```

✅ Output:

```Plain
Autoboxed: 10
Unboxed: 20
Value from list: 30

```

---

### 🔹 Key Points

1. **Autoboxing**: primitive → wrapper class automatically.
2. **Unboxing**: wrapper → primitive automatically.
3. **Introduced in Java 5** to simplify coding with collections.
4. Works for all **wrapper classes**: `Integer, Double, Character, Boolean, etc.`.

---

### 🔹 Gotchas / Notes

- **Null wrapper objects**: unboxing `null` causes `**NullPointerException**`.

```Java
Integer i = null;
int num = i; // ❌ NullPointerException

```

- Autoboxing/unboxing can **slightly reduce performance** due to object creation.
- Use **primitives** in performance-critical code when possible.

---

## 2. 📊 Summary Table

|Concept|Example|Notes|
|---|---|---|
|Autoboxing|`int a = 10; Integer obj = a;`|Primitive → wrapper automatically|
|Unboxing|`Integer obj = 20; int a = obj;`|Wrapper → primitive automatically|
|Collection use|`ArrayList<Integer> list = new ArrayList<>(); list.add(5);`|Autoboxing occurs|
|Null handling|`Integer i = null; int a = i;`|❌ Causes NullPointerException|

---

### 🔹 Real-World Example

**Sum of Numbers in ArrayList**

```Java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<>();
        numbers.add(5);  // autoboxed
        numbers.add(10); // autoboxed
        numbers.add(15); // autoboxed

        int sum = 0;
        for(Integer n : numbers) { // unboxing
            sum += n;
        }
        System.out.println("Sum: " + sum); // Sum: 30
    }
}

```

- Demonstrates **autoboxing when adding to collection** and **unboxing when retrieving**.