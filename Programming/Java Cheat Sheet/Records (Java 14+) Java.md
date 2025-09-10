---
Created: 2025-08-25T20:04
tags:
  - Special-Types
---
## 1. Full Explanation

### 🔹 What is a Record?

- **Record** is a **special type of class** in Java introduced in **Java 14** to **model immutable data**.
- Automatically provides:
    - **Private final fields**
    - **Constructor**
    - **Getters** (no `get` prefix, just field name)
    - `**equals()**`, `**hashCode()**`, `**toString()**`
- Declared using the `record` keyword.

---

### 🔹 Basic Syntax

```Java
record Person(String name, int age) { }

```

- Automatically generates:
    
    ```Java
    private final String name;
    private final int age;
    
    public Person(String name, int age) { ... }
    
    public String name() { return name; }
    public int age() { return age; }
    
    public boolean equals(Object o) { ... }
    public int hashCode() { ... }
    public String toString() { ... }
    
    ```
    

---

### 🔹 Using Records

```Java
public class Main {
    public static void main(String[] args) {
        Person p = new Person("Alice", 25);

        System.out.println(p.name()); // Alice
        System.out.println(p.age());  // 25
        System.out.println(p);        // Person[name=Alice, age=25]
    }
}

```

- **Immutable by default** → fields are `final`.
- **Concise syntax** for data carriers.

---

### 🔹 Customizing Records

- Can **add methods**, **static fields**, or **static methods**.
- Cannot extend another class (records implicitly extend `java.lang.Record`).
- Can implement interfaces.

```Java
record Person(String name, int age) {
    // Custom method
    public String greet() {
        return "Hello, " + name;
    }

    // Compact constructor for validation
    public Person {
        if (age < 0) throw new IllegalArgumentException("Age cannot be negative");
    }
}

public class Main {
    public static void main(String[] args) {
        Person p = new Person("Bob", 30);
        System.out.println(p.greet()); // Hello, Bob
    }
}

```

---

### 🔹 Key Points

1. **Immutable data** by default.
2. Automatically generates **constructor, accessors, equals, hashCode, toString**.
3. Cannot **extend other classes**.
4. Can **implement interfaces**.
5. Supports **compact constructors** for validation or preprocessing.

---

### 🔹 Gotchas / Notes

- Fields are implicitly `**private final**`, cannot be reassigned.
- Cannot have **instance initializers** or extend classes.
- Suitable for **DTOs, value objects, simple data containers**.
- Methods can be **added** if additional behavior is needed.

---

## 2. 📊 Summary Table

|Feature|Syntax / Example|Notes|
|---|---|---|
|Record declaration|`record Person(String name, int age) { }`|Immutable data carrier|
|Accessor methods|`p.name()`, `p.age()`|No `get` prefix|
|Auto-generated|`equals()`, `hashCode()`, `toString()`|Default implementations|
|Custom methods|`public String greet() { ... }`|Add behavior|
|Compact constructor|`public Person { if(age<0) ... }`|Validation logic|
|Implements interface|`record Person(...) implements Comparable<Person>`|Records can implement interfaces|

---

### 🔹 Real-World Example

**Address Record for API Response**

```Java
record Address(String street, String city, String zip) {
    public String fullAddress() {
        return street + ", " + city + " " + zip;
    }
}

public class Main {
    public static void main(String[] args) {
        Address addr = new Address("123 Main St", "Springfield", "12345");
        System.out.println(addr.fullAddress()); // 123 Main St, Springfield 12345
        System.out.println(addr); // Address[street=123 Main St, city=Springfield, zip=12345]
    }
}

```

- Demonstrates **concise immutable data class** with additional method.