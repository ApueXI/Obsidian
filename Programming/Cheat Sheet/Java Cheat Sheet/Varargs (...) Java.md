---
Created: 2025-08-25T19:43
tags:
  - Methods-(Funciton)
---
## 1. Full Explanation

### 🔹 What is Varargs?

- **Varargs** (variable-length arguments) allows a method to accept **0 or more arguments** of the same type.
- Introduced in **Java 5**.
- Syntax uses `**...**` after the type.

```Java
modifier returnType methodName(Type... varName) {
    // method body
}

```

- Internally, **varargs are treated as an array**.

---

### 🔹 Syntax Example

```Java
public class Calculator {

    // Sum of any number of integers
    public static int sum(int... numbers) {
        int total = 0;
        for (int num : numbers) {
            total += num;
        }
        return total;
    }

    public static void main(String[] args) {
        System.out.println(sum());          // 0
        System.out.println(sum(1, 2, 3));   // 6
        System.out.println(sum(5, 10, 15)); // 30
    }
}

```

✅ Output:

```Plain
0
6
30

```

---

### 🔹 Rules / Notes

1. **Only one varargs parameter** is allowed per method.
2. Varargs must be **last parameter** in method signature.

```Java
public void example(String name, int... scores) { } // ✅ valid
public void example(int... scores, String name) { } // ❌ invalid

```

1. Can combine with **normal parameters**:

```Java
public static void greet(String greeting, String... names) {
    for (String name : names) {
        System.out.println(greeting + ", " + name);
    }
}

```

```Java
greet("Hello", "Alice", "Bob", "Charlie");

```

Output:

```Plain
Hello, Alice
Hello, Bob
Hello, Charlie

```

1. Internally treated as **array**, so you can do:

```Java
int[] arr = numbers;

```

---

### 🔹 Gotchas

- Cannot overload a method **only by varargs** if it conflicts with a method taking an array.
- Using varargs with too many recursive calls can **increase stack usage**.
- Works well with **helper/util methods** like `printf`, `Math.max`, logging methods.

---

## 2. 📊 Summary Table

|Feature|Syntax / Example|Notes|
|---|---|---|
|Varargs|`Type... name`|Accepts 0 or more values|
|Call|`method(1,2,3)`|Passed as an array internally|
|Multiple params|Only last param can be varargs|`int x, String... names` ✅|
|Array access|`for(Type t : name)`|Loop through values easily|

---

### 🔹 Real-World Example

**Logging Helper Method**:

```Java
public class Logger {
    public static void log(String level, String... messages) {
        for (String msg : messages) {
            System.out.println("[" + level + "] " + msg);
        }
    }

    public static void main(String[] args) {
        log("INFO", "Server started", "Listening on port 8080");
        log("ERROR", "Null pointer exception", "Invalid input");
    }
}

```

✅ Output:

```Plain
[INFO] Server started
[INFO] Listening on port 8080
[ERROR] Null pointer exception
[ERROR] Invalid input

```

- Demonstrates **flexible number of arguments** with `varargs`.