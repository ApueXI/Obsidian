---
Created: 2025-08-25T19:29
tags:
  - Control-Flow
---
## 1. Full Explanation

### 🔹 Conditional Statements in Java

- Used to **make decisions** in code.
- Executes code blocks based on **true/false conditions**.

---

### 🔹 `if` Statement

Executes block only if condition is true.

```Java
int age = 20;

if (age >= 18) {
    System.out.println("You are an adult.");
}

```

---

### 🔹 `if – else` Statement

Adds an alternative block if condition is false.

```Java
int age = 16;

if (age >= 18) {
    System.out.println("Adult");
} else {
    System.out.println("Minor");
}

```

---

### 🔹 `if – else if – else` Statement

Checks multiple conditions in sequence.

```Java
int score = 75;

if (score >= 90) {
    System.out.println("Grade A");
} else if (score >= 75) {
    System.out.println("Grade B");
} else if (score >= 60) {
    System.out.println("Grade C");
} else {
    System.out.println("Fail");
}

```

---

### 🔹 Nested `if`

You can put an `if` inside another `if`.

```Java
int age = 25;
boolean hasLicense = true;

if (age >= 18) {
    if (hasLicense) {
        System.out.println("You can drive.");
    } else {
        System.out.println("You need a license.");
    }
}

```

---

### 🔹 Gotchas

- Conditions must evaluate to **boolean** (`true` / `false`).
- Avoid **deep nesting** → use `else if` or `switch` instead for readability.
- `=` (assignment) vs `==` (comparison) → common bug!

---

## 2. 📊 Summary Table

|Statement|Syntax|Example|Purpose|
|---|---|---|---|
|`if`|`if(condition){}`|`if(x>0){}`|Runs block if true|
|`if-else`|`if(condition){} else {}`|`if(age>=18){}`|Choose between 2 paths|
|`if-else if-else`|`if(){} else if(){} else{}`|Grading system|Multiple conditions|
|Nested `if`|`if(){ if(){} }`|`if(age>=18){ if(hasID){} }`|Conditional inside another|

---

## 3. 🌍 Real-World Example

Imagine an **ATM System**:

```Java
import java.util.Scanner;

public class ATM {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter PIN: ");
        int pin = sc.nextInt();

        if (pin == 1234) {
            System.out.println("PIN accepted. Choose option:");
            System.out.println("1. Withdraw\n2. Deposit\n3. Balance");
            int choice = sc.nextInt();

            if (choice == 1) {
                System.out.println("Withdraw selected.");
            } else if (choice == 2) {
                System.out.println("Deposit selected.");
            } else if (choice == 3) {
                System.out.println("Balance selected.");
            } else {
                System.out.println("Invalid choice.");
            }
        } else {
            System.out.println("Wrong PIN. Access denied.");
        }

        sc.close();
    }
}

```

✅ Example Outputs:

```Plain
Enter PIN: 1234
PIN accepted. Choose option:
1. Withdraw
2. Deposit
3. Balance
2
Deposit selected.

```

OR

```Plain
Enter PIN: 1111
Wrong PIN. Access denied.

```

Here we used:

- `if` → check PIN.
- `else if` → multiple menu choices.
- `else` → invalid input.