---
Created: 2025-08-25T20:03
tags:
  - Special-Types
---
## 1. Full Explanation

### 🔹 What is an Enum?

- An **enum (enumeration)** is a **special data type** that defines a **set of named constants**.
- Introduced to **replace integer constants** with readable names.
- Declared using the `**enum**` keyword.

```Java
enum Day {
    MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY
}

```

- Enums are **type-safe** → cannot assign invalid values.

---

### 🔹 Using Enums

```Java
public class Main {
    public static void main(String[] args) {
        Day today = Day.MONDAY;

        if(today == Day.MONDAY) {
            System.out.println("Start of the week");
        }

        // Loop through all enum constants
        for(Day d : Day.values()) {
            System.out.println(d);
        }
    }
}

```

✅ Output:

```Plain
Start of the week
MONDAY
TUESDAY
WEDNESDAY
THURSDAY
FRIDAY
SATURDAY
SUNDAY

```

---

### 🔹 Enums with Fields, Constructor, and Methods

- Enums can have **fields**, **constructors**, and **methods**.

```Java
enum Planet {
    MERCURY(3.3e23, 2.4e6),
    VENUS(4.8e24, 6.1e6),
    EARTH(5.97e24, 6.37e6);

    private double mass;   // in kg
    private double radius; // in meters

    Planet(double mass, double radius) { // constructor
        this.mass = mass;
        this.radius = radius;
    }

    double surfaceGravity() { // method
        final double G = 6.67430e-11;
        return G * mass / (radius * radius);
    }
}

public class Main {
    public static void main(String[] args) {
        for(Planet p : Planet.values()) {
            System.out.println(p + " gravity: " + p.surfaceGravity());
        }
    }
}

```

- Enum constants behave like **objects** with their own properties and behavior.

---

### 🔹 Key Points

1. Enums are **classes internally** (`extends java.lang.Enum`).
2. Can have **fields, constructors, and methods**.
3. Enum constructors are **private by default**.
4. Provides **type safety** instead of using integer/string constants.
5. Can use `**values()**`, `**ordinal()**`, and `**valueOf()**` methods.

---

### 🔹 Gotchas / Notes

- Enum constructors **cannot be public or protected**.
- Enum constants are **implicitly** `**public static final**`.
- Enum can implement **interfaces**, but cannot extend another class.

```Java
enum Status implements Printable {
    NEW, IN_PROGRESS, DONE;

    public void print() {
        System.out.println(this);
    }
}

```

---

## 2. 📊 Summary Table

|Feature|Syntax / Example|Notes|
|---|---|---|
|Enum declaration|`enum Day {MON, TUE}`|Type-safe constant values|
|Enum field|`private double mass;`|Add properties to enum|
|Enum constructor|`Planet(double mass){ this.mass = mass; }`|Implicitly private|
|Enum method|`double surfaceGravity(){}`|Behaves like class methods|
|Enum utility|`values()`, `ordinal()`, `valueOf()`|Iterate, get index, or parse string|

---

### 🔹 Real-World Example

**Order Status Enum**

```Java
enum OrderStatus {
    PENDING, PROCESSING, SHIPPED, DELIVERED, CANCELLED
}

public class Order {
    OrderStatus status;

    Order() {
        status = OrderStatus.PENDING;
    }

    void updateStatus(OrderStatus newStatus) {
        status = newStatus;
        System.out.println("Order status updated to " + status);
    }

    public static void main(String[] args) {
        Order order = new Order();
        order.updateStatus(OrderStatus.SHIPPED);    // Order status updated to SHIPPED
        order.updateStatus(OrderStatus.DELIVERED);  // Order status updated to DELIVERED
    }
}

```

- Demonstrates **enum as type-safe order status** with clear readable values.