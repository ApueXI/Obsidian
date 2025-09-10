---
Created: 2025-08-25T19:27
tags:
  - Basics-&-Foundations
---
## 1. Full Explanation

Operators in Java are **symbols** that perform operations on variables and values.

---

### 🔹 1. Arithmetic Operators

Used for basic math.

```Java
int a = 10, b = 3;
System.out.println(a + b);  // 13
System.out.println(a - b);  // 7
System.out.println(a * b);  // 30
System.out.println(a / b);  // 3 (integer division)
System.out.println(a % b);  // 1 (remainder)

```

- `/` → integer division truncates decimals.
- `%` → modulo gives remainder.

---

### 🔹 2. Relational (Comparison) Operators

Used to compare values. Returns **boolean** (`true` / `false`).

```Java
int x = 5, y = 10;
System.out.println(x == y);  // false
System.out.println(x != y);  // true
System.out.println(x > y);   // false
System.out.println(x < y);   // true
System.out.println(x >= 5);  // true
System.out.println(y <= 10); // true

```

---

### 🔹 3. Logical Operators

Used with **boolean expressions**.

```Java
boolean a = true, b = false;
System.out.println(a && b); // false (AND)
System.out.println(a || b); // true  (OR)
System.out.println(!a);     // false (NOT)

```

- `&&` → true if **both** are true.
- `||` → true if **at least one** is true.
- `!` → negation.

---

### 🔹 4. Bitwise Operators

Work at **bit level**.

```Java
int p = 5;   // 0101
int q = 3;   // 0011

System.out.println(p & q); // 1 (0001)
System.out.println(p | q); // 7 (0111)
System.out.println(p ^ q); // 6 (0110)
System.out.println(~p);    // -6 (inverts bits)
System.out.println(p << 1);// 10 (shift left)
System.out.println(p >> 1);// 2  (shift right)

```

- `&` (AND), `|` (OR), `^` (XOR), `~` (NOT).
- `<<` left shift (multiply by 2).
- `>>` right shift (divide by 2).

---

### 🔹 5. Assignment Operators

Used to assign or update values.

```Java
int z = 10;
z += 5;  // z = z + 5 → 15
z -= 3;  // z = z - 3 → 12
z *= 2;  // z = z * 2 → 24
z /= 4;  // z = z / 4 → 6
z %= 5;  // z = z % 5 → 1

```

---

### 🔹 Unary Operators

- `++` Increment
- `-` Decrement

```Java
int m = 5;
System.out.println(++m); // 6 (pre-increment)
System.out.println(m++); // 6 (post-increment, then m=7)
System.out.println(--m); // 6 (pre-decrement)
System.out.println(m--); // 6 (post-decrement, then m=5)

```

---

### 🔹 Ternary Operator

Shortcut for `if-else`.

```Java
int num = 10;
String result = (num % 2 == 0) ? "Even" : "Odd";
System.out.println(result); // Even

```

---

## 2. 📊 Summary Table

|Category|Operator(s)|Example|Notes|
|---|---|---|---|
|Arithmetic|`+ - * / %`|`a + b`|Basic math|
|Relational|`== != > < >= <=`|`x == y`|Returns boolean|
|Logical|`&&||!`|
|Bitwise|`&|^ ~ << >>`|`p & q`|
|Assignment|`= += -= *= /= %=`|`x += 5`|Updates variable|
|Unary|`++ --`|`++i, i--`|Increment/decrement|
|Ternary|`? :`|`(x>0 ? "Pos":"Neg")`|Conditional|

---

## 3. 🌍 Real-World Example

Imagine an **Employee Payroll System**:

```Java
public class Payroll {
    public static void main(String[] args) {
        int hoursWorked = 45;
        double hourlyRate = 20.0;
        boolean isOvertime = hoursWorked > 40;

        // Arithmetic
        double basePay = 40 * hourlyRate;
        double overtimePay = (hoursWorked - 40) * hourlyRate * 1.5;

        // Logical + Relational
        double totalPay = basePay + (isOvertime ? overtimePay : 0);

        // Assignment
        totalPay += 100; // bonus

        // Bitwise example: check if employee ID is odd/even
        int employeeId = 101;
        String type = (employeeId & 1) == 0 ? "Even ID" : "Odd ID";

        System.out.println("Total Pay: $" + totalPay);
        System.out.println("Employee Type: " + type);
    }
}

```

✅ Output:

```Plain
Total Pay: $1050.0
Employee Type: Odd ID

```

Here we used:

- **Arithmetic** (pay calculations).
- **Relational & Logical** (overtime check).
- **Assignment** (bonus).
- **Bitwise** (ID check).
- **Ternary** (odd/even).