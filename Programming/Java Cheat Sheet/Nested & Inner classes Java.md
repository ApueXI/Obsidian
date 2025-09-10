---
Created: 2025-08-25T20:02
tags:
  - Object-Oriented-Programming-(OOP)
---
## 1. Full Explanation

### 🔹 What are Nested & Inner Classes?

- **Nested class** = a class defined **inside another class**.
- Helps **group classes logically**, increases **encapsulation**, and allows **access to outer class members**.
- **Types of nested classes in Java:**
    1. **Static Nested Class** – declared `static`, cannot access non-static outer members directly.
    2. **Non-static Inner Class** – also called **Member Inner Class**, can access outer class members.
    3. **Local Inner Class** – declared inside a **method**, local to that method.
    4. **Anonymous Inner Class** – no name, usually used for **implementing interfaces or extending classes on the fly**.

---

### 🔹 1. Static Nested Class

- Declared `static` inside a class.
- **Can access only static members of outer class**.

```Java
class Outer {
    static int data = 10;

    static class StaticNested {
        void display() {
            System.out.println("Data: " + data); // access static member
        }
    }

    public static void main(String[] args) {
        Outer.StaticNested nested = new Outer.StaticNested();
        nested.display(); // Data: 10
    }
}

```

---

### 🔹 2. Member Inner Class (Non-static)

- Can access **all members of outer class**, including private fields.
- Must **instantiate using outer class object**.

```Java
class Outer {
    private int data = 30;

    class Inner {
        void display() {
            System.out.println("Data: " + data); // access outer class field
        }
    }

    public static void main(String[] args) {
        Outer outer = new Outer();
        Outer.Inner inner = outer.new Inner();
        inner.display(); // Data: 30
    }
}

```

---

### 🔹 3. Local Inner Class

- Declared **inside a method**.
- Can access **final or effectively final local variables** of the method.

```Java
class Outer {
    void show() {
        int num = 100;
        class LocalInner {
            void display() {
                System.out.println("Num: " + num);
            }
        }
        LocalInner li = new LocalInner();
        li.display();
    }

    public static void main(String[] args) {
        Outer o = new Outer();
        o.show(); // Num: 100
    }
}

```

---

### 🔹 4. Anonymous Inner Class

- **No class name**, usually for **implementing an interface or extending a class**.
- **One-time use**.

```Java
interface Greeting {
    void sayHello();
}

public class Main {
    public static void main(String[] args) {
        Greeting g = new Greeting() {
            @Override
            public void sayHello() {
                System.out.println("Hello from anonymous class");
            }
        };
        g.sayHello(); // Hello from anonymous class
    }
}

```

---

### 🔹 Key Points

1. **Static nested class** → cannot access non-static outer members directly.
2. **Non-static inner class** → can access all outer members.
3. **Local inner class** → limited to method scope, accesses final/effectively final variables.
4. **Anonymous class** → convenient for one-time use (e.g., listeners, callbacks).

---

### 🔹 Gotchas / Notes

- Inner classes hold a **reference to outer class object**, which may increase **memory usage**.
- Anonymous inner classes can implement **interfaces** or extend a class **inline**.
- Useful in GUI programming, callbacks, and event handling.

---

## 2. 📊 Summary Table

|Type|Declaration|Access|Instantiation|
|---|---|---|---|
|Static Nested Class|`static class Nested {}`|Only static outer members|`Outer.Nested obj = new Outer.Nested();`|
|Member Inner Class|`class Inner {}`|All outer members|`Outer.Inner obj = outer.new Inner();`|
|Local Inner Class|inside method|Final or effectively final locals + outer members|Instantiate inside method|
|Anonymous Inner Class|`new Interface/Class() {}`|Depends on outer scope|Inline, no object name|

---

### 🔹 Real-World Example

**GUI Button Listener (Anonymous Inner Class)**

```Java
import javax.swing.*;
import java.awt.event.*;

public class Main {
    public static void main(String[] args) {
        JButton button = new JButton("Click Me");

        button.addActionListener(new ActionListener() { // anonymous inner class
            @Override
            public void actionPerformed(ActionEvent e) {
                System.out.println("Button clicked!");
            }
        });

        JFrame frame = new JFrame();
        frame.add(button);
        frame.setSize(200, 200);
        frame.setVisible(true);
    }
}

```

- Demonstrates **anonymous inner class** for **event handling**.