---
Created: 2025-08-25T19:24
tags:
  - Basics-&-Foundations
---
## 1. Full Explanation

### 🔹 Basic Java File Structure

Every Java program follows a strict structure:

```Java
// File: MyProgram.java
public class MyProgram {
    // Entry point (main method)
    public static void main(String[] args) {
        System.out.println("Java File Structure Example");
    }
}

```

### 🔹 Key Rules

1. **File Name = Public Class Name**
    - If your class is `MyProgram`, the file **must** be `MyProgram.java`.
    - Java is case-sensitive → `MyProgram` ≠ `myprogram`.
2. **Class Declaration**
    - Everything in Java **lives inside a class**.
    - Syntax:
        
        ```Java
        public class ClassName {
            // fields (variables)
            // methods
        }
        
        ```
        
3. **Main Method (Program Entry Point)**
    - The method that runs when you execute a Java program.
    - Must always have the exact signature:
        
        ```Java
        public static void main(String[] args)
        
        ```
        
    - **Keywords meaning**:
        - `public` → accessible everywhere.
        - `static` → can be run without creating an object.
        - `void` → does not return any value.
        - `String[] args` → accepts command-line arguments.
4. **Multiple Classes in One File**
    - Only **one public class** is allowed per file.
    - Other classes can be defined but must not be `public`.
    - Example:
        
        ```Java
        public class MainClass {
            public static void main(String[] args) {
                Helper.sayHello();
            }
        }
        
        class Helper {
            static void sayHello() {
                System.out.println("Hello from Helper!");
            }
        }
        
        ```
        
5. **Packages (Optional at First)**
    - Classes can be grouped in **packages**.
    - If declared, the package must match the folder structure:
        
        ```Java
        package com.example;
        
        public class App {
            public static void main(String[] args) {
                System.out.println("With package!");
            }
        }
        
        ```
        
    - File must be stored at `/com/example/App.java`.

---

## 2. 📊 Summary Table

|Component|Example|Purpose|
|---|---|---|
|**Class**|`public class MyClass {}`|Defines a blueprint (all code must be inside a class)|
|**Main Method**|`public static void main(String[] args)`|Entry point of program|
|**File Name**|`MyClass.java`|Must match public class name|
|**Other Classes**|`class Helper {}`|Allowed, but not `public`|
|**Package**|`package com.example;`|Groups related classes|

---

## 3. 🌍 Real-World Example

Imagine you’re writing a **Student Management System**.

- File: `StudentApp.java`

```Java
public class StudentApp {
    public static void main(String[] args) {
        Student s = new Student("Alice", 20);
        s.printInfo();
    }
}

class Student {
    String name;
    int age;

    Student(String n, int a) {
        name = n;
        age = a;
    }

    void printInfo() {
        System.out.println(name + " is " + age + " years old.");
    }
}

```

- ✅ Shows: one `public class`, one `main method`, and another helper class.
- This structure mirrors **real projects** where you keep one main entry point and multiple helper classes.