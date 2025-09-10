---
Created: 2025-08-25T19:26
tags:
  - Basics-&-Foundations
---
## 1. Full Explanation

### 🔹 Variables in Java

- A **variable** is a **container for data**.
- Must have:
    1. **Type** → defines kind of data stored.
    2. **Name** → identifier.
    3. **Value** → assigned data.

Example:

```Java
int age = 25;
String name = "Alice";

```

---

### 🔹 Data Types in Java

### 1. **Primitive Types** (8 total, stored directly in memory stack)

|Type|Size (bits)|Example Value|Notes|
|---|---|---|---|
|`byte`|8|`127`|Small integers (-128 to 127)|
|`short`|16|`32000`|Larger integers (-32,768 to 32,767)|
|`int`|32|`100000`|Most common integer type|
|`long`|64|`10000000000L`|Big integers (suffix `L`)|
|`float`|32|`3.14f`|Decimal, single precision (suffix `f`)|
|`double`|64|`3.14159`|Decimal, double precision|
|`char`|16|`'A'`|Single Unicode character|
|`boolean`|1|`true` / `false`|Logical values|

---

### 2. **Reference Types** (store memory address of objects)

- Created using **classes, arrays, interfaces, enums**.
- Always initialized with `new` (except `String`, which has special treatment).

Examples:

```Java
String message = "Hello";    // String (special reference type)
int[] numbers = {1, 2, 3};   // Array
Student s = new Student();   // Custom object

```

---

### 🔹 Differences: Primitive vs Reference

- **Primitive** → stores actual value.
- **Reference** → stores memory address (reference to object).

Example:

```Java
int x = 5;          // primitive → stores value 5 directly
String y = "Hi";    // reference → points to "Hi" object in heap

```

---

### 🔹 Variable Declaration Styles

```Java
int a;            // declaration
a = 10;           // initialization
int b = 20;       // declaration + initialization
final int PI = 3; // constant (cannot change)

```

---

## 2. 📊 Summary Table

|Category|Type(s)|Example|Stored As|
|---|---|---|---|
|**Primitive**|`byte, short, int, long, float, double, char, boolean`|`int n = 42;`|Direct value|
|**Reference**|`String, Arrays, Classes, Objects, Interfaces`|`String s = "Hi";`|Memory address|
|**Constant**|`final` keyword|`final double PI = 3.14;`|Immutable value|

---

## 3. 🌍 Real-World Example

Imagine a **Student Management System**:

```Java
public class Student {
    String name;       // Reference type
    int age;           // Primitive type
    double gpa;        // Primitive type

    Student(String n, int a, double g) {
        name = n;
        age = a;
        gpa = g;
    }

    void printInfo() {
        System.out.println(name + " (" + age + ") has GPA: " + gpa);
    }

    public static void main(String[] args) {
        Student s1 = new Student("Alice", 20, 3.8);
        Student s2 = new Student("Bob", 22, 3.5);

        s1.printInfo();
        s2.printInfo();
    }
}

```

✅ Output:

```Plain
Alice (20) has GPA: 3.8
Bob (22) has GPA: 3.5

```

Here:

- `age` and `gpa` → **primitives**.
- `name` and `Student` object → **reference types**.