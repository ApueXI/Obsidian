---
Created: 2025-08-25T20:05
tags:
  - Special-Types
---
## 1. Full Explanation

### 🔹 What are Wrapper Classes?

- **Wrapper classes** provide **object representation of primitive types** in Java.
- Useful when primitives need to be **stored in objects** (e.g., in **Collections**, like `ArrayList`).
- Java automatically converts between primitives and wrappers:
    - **Autoboxing** → primitive → wrapper object
    - **Unboxing** → wrapper object → primitive

---

### 🔹 Primitive → Wrapper Mapping

|Primitive|Wrapper Class|
|---|---|
|`int`|`Integer`|
|`double`|`Double`|
|`char`|`Character`|
|`boolean`|`Boolean`|
|`byte`|`Byte`|
|`short`|`Short`|
|`long`|`Long`|
|`float`|`Float`|

---

### 🔹 Creating Wrapper Objects

```Java
Integer i1 = new Integer(10);      // deprecated in modern Java
Integer i2 = Integer.valueOf(20);  // preferred
Double d1 = Double.valueOf(3.14);
Character c = Character.valueOf('A');

```

- **Autoboxing example:**

```Java
Integer i = 100; // primitive int 100 automatically boxed into Integer
int x = i;       // unboxing: Integer → int

```

---

### 🔹 Useful Methods

**Integer / Double / Boolean Examples**

```Java
int num = Integer.parseInt("123");       // String → int
String str = Integer.toString(456);      // int → String
int max = Integer.max(10, 20);           // max value
int min = Integer.min(10, 20);           // min value

Double d = Double.parseDouble("3.14");   // String → double
String s = Double.toString(2.718);       // double → String

```

- **Character class**

```Java
Character.isDigit('5');    // true
Character.isLetter('a');   // true
Character.isUpperCase('A');// true
Character.isLowerCase('b');// true

```

- **Boolean class**

```Java
Boolean b1 = Boolean.valueOf(true);
Boolean b2 = Boolean.parseBoolean("true");

```

---

### 🔹 Key Points

1. Wrapper classes **wrap primitives in objects**.
2. Needed for **collections** (`ArrayList<Integer>`).
3. Supports **utility methods**: parse, min, max, isDigit, etc.
4. **Autoboxing/unboxing** makes conversion automatic.

---

### 🔹 Gotchas / Notes

- `**new Integer(10)**` is deprecated → use `Integer.valueOf(10)` or autoboxing.
- **Null handling**: unboxing a `null` wrapper throws `NullPointerException`.
- Wrapper objects are **immutable**.

---

## 2. 📊 Summary Table

|Primitive|Wrapper|Autoboxing Example|Utility Methods|
|---|---|---|---|
|`int`|`Integer`|`Integer i = 10;`|`parseInt()`, `toString()`, `max()`, `min()`|
|`double`|`Double`|`Double d = 3.14;`|`parseDouble()`, `toString()`|
|`char`|`Character`|`Character c = 'A';`|`isLetter()`, `isDigit()`, `isUpperCase()`|
|`boolean`|`Boolean`|`Boolean b = true;`|`parseBoolean()`, `valueOf()`|

---

### 🔹 Real-World Example

**Storing Integers in ArrayList**

```Java
import java.util.ArrayList;

public class Main {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<>();
        numbers.add(10); // autoboxed to Integer
        numbers.add(20);

        int sum = 0;
        for(Integer n : numbers) { // unboxing Integer → int
            sum += n;
        }
        System.out.println("Sum: " + sum); // Sum: 30
    }
}

```

- Demonstrates **autoboxing/unboxing** and **wrapper objects in collections**.