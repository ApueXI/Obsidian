---
Created: 2025-08-25T19:47
tags:
  - Object-Oriented-Programming-(OOP)
---
## 1. Full Explanation

### 🔹 What Are Fields?

- **Fields** = variables declared **inside a class** but **outside methods**.
- Represent the **state/data** of an object.
- Can be **instance variables** (each object has its own copy) or **static variables** (shared by all objects).

### Syntax Examples:

```Java
public class Person {
    // Instance fields
    String name;
    int age;

    // Static field
    static int population;
}

```

- **Instance fields** → accessed via object (`obj.name`).
- **Static fields** → accessed via class (`Person.population`).

---

### 🔹 What Are Methods?

- **Methods** = blocks of code **inside a class** that define **behavior**.
- Can access **fields** of the class.
- Can be **instance methods** (need object) or **static methods** (belong to class).

### Syntax Example:

```Java
public class Person {
    String name;
    int age;

    // Instance method
    public void greet() {
        System.out.println("Hello, my name is " + name);
    }

    // Static method
    public static void showPopulation() {
        System.out.println("Population: " + population);
    }
}

```

---

### 🔹 Accessing Fields & Methods

```Java
public class Main {
    public static void main(String[] args) {
        // Object creation
        Person person1 = new Person();
        person1.name = "Alice";
        person1.age = 25;

        // Access instance field
        System.out.println(person1.name); // Alice

        // Call instance method
        person1.greet(); // Hello, my name is Alice

        // Access static field
        Person.population = 1000;
        System.out.println(Person.population); // 1000

        // Call static method
        Person.showPopulation(); // Population: 1000
    }
}

```

---

### 🔹 Field & Method Modifiers

- **Access Modifiers:** `public`, `private`, `protected`
- **Other Modifiers:** `static`, `final`, `abstract`

|Modifier|Applies To|Notes|
|---|---|---|
|public|Fields/Methods|Accessible anywhere|
|private|Fields/Methods|Accessible only in class|
|protected|Fields/Methods|Accessible in package & subclasses|
|static|Fields/Methods|Belongs to class, shared by all objects|
|final|Fields/Methods|Field value cannot change / method cannot be overridden|
|abstract|Methods|No body, must be implemented in subclass|

---

### 🔹 Gotchas / Notes

- **Instance fields** → each object has its own copy.
- **Static fields** → shared by all instances.
- **Methods** can **access instance fields** (non-static) or **static fields**.
- **Static methods** cannot directly access **instance fields/methods**; need object.

---

## 2. 📊 Summary Table

|Concept|Syntax / Example|Notes|
|---|---|---|
|Instance Field|`String name;`|Each object has its own copy|
|Static Field|`static int population;`|Shared among all objects|
|Instance Method|`void greet(){}`|Access via object|
|Static Method|`static void show(){}`|Access via class|
|Access Modifier|`private, public, protected`|Controls visibility|

---

### 🔹 Real-World Example

**Car Class**

```Java
public class Car {
    // Fields
    String model;
    int year;
    static int totalCars;

    // Constructor
    public Car(String model, int year) {
        this.model = model;
        this.year = year;
        totalCars++;
    }

    // Instance method
    public void displayInfo() {
        System.out.println("Model: " + model + ", Year: " + year);
    }

    // Static method
    public static void showTotalCars() {
        System.out.println("Total Cars: " + totalCars);
    }

    public static void main(String[] args) {
        Car car1 = new Car("Toyota", 2020);
        Car car2 = new Car("Honda", 2021);

        car1.displayInfo(); // Model: Toyota, Year: 2020
        car2.displayInfo(); // Model: Honda, Year: 2021

        Car.showTotalCars(); // Total Cars: 2
    }
}

```

- Demonstrates **fields (instance + static)** and **methods (instance + static)** in practice.