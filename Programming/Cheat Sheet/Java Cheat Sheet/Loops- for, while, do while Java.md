---
Created: 2025-08-25T19:33
tags:
  - Control-Flow
---
## 1. Full Explanation

### 🔹 `for` Loop

- Best when the **number of iterations is known**.
- Syntax:

```Java
for (initialization; condition; update) {
    // loop body
}

```

✅ Example:

```Java
for (int i = 0; i < 5; i++) {
    System.out.println("i = " + i);
}

```

---

### 🔹 `while` Loop

- Best when the **number of iterations is not known in advance**.
- Condition checked **before** loop body executes.

```Java
int i = 0;
while (i < 5) {
    System.out.println("i = " + i);
    i++;
}

```

---

### 🔹 `do-while` Loop

- Executes the loop body **at least once**, condition checked **after** execution.

```Java
int i = 0;
do {
    System.out.println("i = " + i);
    i++;
} while (i < 5);

```

---

### 🔹 Loop Control Statements

- `break;` → exits loop immediately.
- `continue;` → skips current iteration, moves to next.

Example:

```Java
for (int i = 1; i <= 5; i++) {
    if (i == 3) continue;  // skip 3
    if (i == 5) break;     // stop at 5
    System.out.println(i);
}

```

---

## 2. 📊 Summary Table

|Loop Type|When to Use|Syntax|Executes At Least Once?|
|---|---|---|---|
|`for`|Known iterations|`for(init; cond; update){}`|❌|
|`while`|Unknown iterations (condition first)|`while(cond){}`|❌|
|`do-while`|Must run at least once|`do{} while(cond);`|✅|

---

## 3. 🌍 Real-World Example

### ✅ ATM PIN Verification (while & do-while)

```Java
import java.util.Scanner;

public class ATMPinCheck {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int correctPin = 1234;
        int attempts = 0;
        boolean access = false;

        // User has 3 tries
        while (attempts < 3) {
            System.out.print("Enter PIN: ");
            int pin = sc.nextInt();
            attempts++;

            if (pin == correctPin) {
                access = true;
                break; // exit loop when correct
            } else {
                System.out.println("Incorrect PIN. Try again.");
            }
        }

        if (access) {
            System.out.println("✅ Access granted.");
        } else {
            System.out.println("❌ Account locked. Too many attempts.");
        }

        sc.close();
    }
}

```

**Sample Run:**

```Plain
Enter PIN: 1111
Incorrect PIN. Try again.
Enter PIN: 2222
Incorrect PIN. Try again.
Enter PIN: 1234
✅ Access granted.

```