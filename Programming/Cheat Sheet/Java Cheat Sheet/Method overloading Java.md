---
Created: 2025-08-25T19:36
tags:
  - Methods-(Funciton)
---
## 1. Full Explanation

### 🔹 What is Method Overloading?

- **Method Overloading** = multiple methods in the **same class** with the **same name** but **different parameter lists**.
- Helps **improve readability** and **reuse method names** for similar actions.

---

### 🔹 Rules for Overloading

1. Must have **same method name**.
2. Must have **different parameter list** (number or type of parameters).
3. **Return type alone is not enough** to overload.
4. Can be **static** or **non-static**.

---

### 🔹 Syntax Example

```Java
public class Calculator {

    // Add two integers
    public int add(int a, int b) {
        return a + b;
    }

    // Add three integers
    public int add(int a, int b, int c) {
        return a + b + c;
    }

    // Add two doubles
    public double add(double a, double b) {
        return a + b;
    }

    public static void main(String[] args) {
        Calculator calc = new Calculator();

        System.out.println(calc.add(5, 10));        // 15
        System.out.println(calc.add(1, 2, 3));      // 6
        System.out.println(calc.add(2.5, 3.5));     // 6.0
    }
}

```

✅ Output:

```Plain
15
6
6.0

```

---

### 🔹 Gotchas / Notes

- Cannot overload **only by return type**:

```Java
// ❌ Invalid
int add(int a, int b) { return a+b; }
double add(int a, int b) { return a+b; } // error

```

- Can combine **different types, different number of parameters, order of parameters**.
- Works with **primitive types, objects, arrays**.

---

## 2. 📊 Summary Table

|Feature|Example|Notes|
|---|---|---|
|Same method name|`add()`|Overloaded methods share name|
|Different parameters|`add(int a, int b)` vs `add(double a, double b)`|Must differ in **type or count**|
|Return type|Can be same or different|Cannot overload **by return type only**|
|Overloading usage|Improves readability|Avoids creating multiple method names for similar tasks|

---

### 🔹 Real-World Example

Imagine a **Shape Area Calculator**:

```Java
public class ShapeCalculator {

    // Area of square
    public int area(int side) {
        return side * side;
    }

    // Area of rectangle
    public int area(int length, int width) {
        return length * width;
    }

    // Area of circle
    public double area(double radius) {
        return 3.14159 * radius * radius;
    }

    public static void main(String[] args) {
        ShapeCalculator calc = new ShapeCalculator();

        System.out.println("Square area: " + calc.area(5));
        System.out.println("Rectangle area: " + calc.area(4, 6));
        System.out.println("Circle area: " + calc.area(3.0));
    }
}

```

✅ Output:

```Plain
Square area: 25
Rectangle area: 24
Circle area: 28.27431

```

- Demonstrates **same method name** `**area()**`, but **different parameters**.