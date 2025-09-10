---
Created: 2025-08-25T19:36
tags:
  - Methods-(Funciton)
---
## 1. Full Explanation

### 🔹 What is a Static Method?

- A **static method** belongs to the **class**, not an object.
- Can be called **without creating an instance** of the class.
- Declared using the `static` keyword.

---

### 🔹 Syntax

```Java
modifier static returnType methodName(parameters) {
    // method body
}

```

- **modifier** → `public`, `private`, etc.
- **static** → keyword to make method belong to class.
- **returnType** → type of value returned (`void` if none).
- **parameters** → optional input values.

---

### 🔹 Calling a Static Method

- Call using **ClassName.methodName()**

```Java
public class Utils {
    public static int square(int n) {
        return n * n;
    }

    public static void main(String[] args) {
        int result = Utils.square(5); // no object needed
        System.out.println("Square: " + result);
    }
}

```

✅ Output:

```Plain
Square: 25

```

---

### 🔹 Static vs Non-Static Methods

|Feature|Static|Non-Static|
|---|---|---|
|Belongs to|Class|Object|
|Call|`ClassName.method()`|`object.method()`|
|Can access|Only static members|Both static & instance members|
|Example|`Math.max()`|`myObject.greet()`|

---

### 🔹 Static Members Inside a Static Method

- Can access **other static methods** or **static variables**.
- Cannot access **instance variables or methods directly**.

```Java
public class Counter {
    static int count = 0;

    public static void increment() {
        count++;
    }

    public static void main(String[] args) {
        Counter.increment();
        Counter.increment();
        System.out.println("Count: " + Counter.count); // 2
    }
}

```

---

### 🔹 Gotchas / Notes

- Overuse of static methods → reduces **OOP benefits** (encapsulation, polymorphism).
- `main` method in Java is **always static** → entry point of the program.
- Static methods **cannot use** `**this**` keyword.

---

## 2. 📊 Summary Table

|Feature|Syntax / Example|Notes|
|---|---|---|
|Declaration|`static returnType name(params)`|Belongs to class|
|Call|`ClassName.method()`|No object needed|
|Access|Only static members directly|Cannot access instance members|
|Usage|Utility/helper methods|e.g., `Math`, `Collections`|
|Main Method|`public static void main(String[] args)`|Program entry point|

---

### 🔹 Real-World Example

Imagine a **Utility Class for Math Operations**:

```Java
public class MathUtils {
    public static int add(int a, int b) {
        return a + b;
    }

    public static int multiply(int a, int b) {
        return a * b;
    }

    public static void main(String[] args) {
        System.out.println("Add: " + MathUtils.add(5, 10));
        System.out.println("Multiply: " + MathUtils.multiply(4, 6));
    }
}

```

✅ Output:

```Plain
Add: 15
Multiply: 24

```

- Methods are **called without creating an object**.