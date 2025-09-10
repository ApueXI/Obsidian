---
Created: 2025-08-25T19:27
tags:
  - Basics-&-Foundations
---
## 1. Full Explanation

### 🔹 What is Type Casting?

- **Type casting** = converting one data type into another.
- Two types in Java:
    1. **Implicit Casting (Widening)** → smaller type → larger type (safe, automatic).
    2. **Explicit Casting (Narrowing)** → larger type → smaller type (possible data loss, must be forced).

---

### 🔹 1. Implicit Casting (Widening)

- Performed **automatically** by Java.
- Safe → no data loss.
- Example:

```Java
int num = 100;
double d = num;   // int → double
System.out.println(d); // 100.0

```

**Conversion order (smaller → larger):**

```Plain
byte → short → int → long → float → double
          char → int

```

---

### 🔹 2. Explicit Casting (Narrowing)

- Performed **manually** by programmer.
- Risky → possible data loss or overflow.
- Syntax: `(targetType) value`
- Example:

```Java
double pi = 3.14159;
int approx = (int) pi; // double → int (fraction lost)
System.out.println(approx); // 3

```

Another example with overflow:

```Java
int big = 130;
byte small = (byte) big;  // narrowing
System.out.println(small); // -126 (overflowed)

```

---

### 🔹 Type Casting with Reference Types

- Java also allows **casting objects** (when they are related via inheritance).

```Java
Animal a = new Dog();   // Upcasting (implicit)
Dog d = (Dog) a;        // Downcasting (explicit, must be safe)

```

---

### 🔹 Gotchas

- Implicit → always safe.
- Explicit → may cause **loss of precision** or **unexpected values**.
- Casting **reference types** requires `instanceof` check to avoid `ClassCastException`.

---

## 2. 📊 Summary Table

|Casting Type|Syntax|Example|Safe?|
|---|---|---|---|
|**Implicit (Widening)**|automatic|`int x = 10; double y = x;`|✅ Safe|
|**Explicit (Narrowing)**|`(type) value`|`double d = 5.7; int i = (int) d;`|⚠️ Data loss possible|
|**Object Upcasting**|automatic|`Animal a = new Dog();`|✅ Safe|
|**Object Downcasting**|`(Child)obj`|`Dog d = (Dog)a;`|⚠️ Risk of `ClassCastException`|

---

## 3. 🌍 Real-World Example

Imagine a **Banking App** where you need both precise and approximate values:

```Java
public class BankApp {
    public static void main(String[] args) {
        double balance = 1050.75;

        // Implicit casting (safe)
        double updatedBalance = balance + 100; // int → double
        System.out.println("Updated Balance: " + updatedBalance);

        // Explicit casting (narrowing)
        int wholeDollars = (int) balance; // drops cents
        System.out.println("Whole Dollars: " + wholeDollars);

        // Risky overflow example
        int largeAmount = 1000;
        byte smallAccount = (byte) largeAmount;
        System.out.println("Overflowed Value: " + smallAccount);
    }
}

```

✅ Output:

```Plain
Updated Balance: 1150.75
Whole Dollars: 1050
Overflowed Value: -24

```

- Shows **implicit widening (int → double)**,
- **explicit narrowing (double → int)**,
- and **overflow in narrowing (int → byte)**.