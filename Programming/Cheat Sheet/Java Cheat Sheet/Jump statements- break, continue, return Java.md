---
Created: 2025-08-25T19:34
tags:
  - Control-Flow
---
## 1. Full Explanation

### 🔹 What Are Jump Statements?

- Statements that **alter normal flow** of execution.
- Three common jump statements in Java: `break`, `continue`, `return`.

---

### 🔹 1. `break`

- Exits the **nearest enclosing loop or switch** immediately.

**Example with Loop:**

```Java
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        break; // exit loop when i = 3
    }
    System.out.println(i);
}

```

✅ Output:

```Plain
1
2

```

**Example with Switch:**

```Java
int day = 3;
switch (day) {
    case 1: System.out.println("Monday"); break;
    case 2: System.out.println("Tuesday"); break;
    case 3: System.out.println("Wednesday"); break;
    default: System.out.println("Invalid");
}

```

---

### 🔹 2. `continue`

- Skips the **current iteration** and moves to the **next loop iteration**.

```Java
for (int i = 1; i <= 5; i++) {
    if (i == 3) continue; // skip printing 3
    System.out.println(i);
}

```

✅ Output:

```Plain
1
2
4
5

```

- Works with `for`, `while`, `do-while` loops.

---

### 🔹 3. `return`

- Exits from a **method immediately**, optionally returning a value.

```Java
public static int square(int n) {
    if (n < 0) return -1; // exit method early for invalid input
    return n * n;
}

public static void main(String[] args) {
    System.out.println(square(5));  // 25
    System.out.println(square(-2)); // -1
}

```

- In `void` methods, `return;` can be used to exit early.

---

### 🔹 Gotchas / Notes

- `break` in nested loops → exits **only the innermost loop**.
- `continue` in nested loops → affects **only the innermost loop**.
- Labeled `break` and `continue` can break/continue **outer loops**:

```Java
outer:
for(int i=1; i<=3; i++){
    for(int j=1; j<=3; j++){
        if(i*j > 2) break outer;
        System.out.println(i + "," + j);
    }
}

```

✅ Output:

```Plain
1,1
1,2

```

---

## 2. 📊 Summary Table

|Jump Statement|Purpose|Example|Notes|
|---|---|---|---|
|`break`|Exit loop or switch immediately|`if(i==3) break;`|Stops nearest enclosing loop/switch|
|`continue`|Skip current iteration|`if(i==3) continue;`|Moves to next iteration|
|`return`|Exit method immediately|`return n*n;`|Can return a value or exit void method|

---

## 3. 🌍 Real-World Example

Imagine a **Number Guessing Game**:

```Java
import java.util.Scanner;

public class GuessGame {
    public static void main(String[] args) {
        int secret = 7;
        Scanner sc = new Scanner(System.in);

        for (int attempts = 1; attempts <= 5; attempts++) {
            System.out.print("Guess the number (1-10): ");
            int guess = sc.nextInt();

            if (guess == secret) {
                System.out.println("✅ Correct! You win!");
                break; // exit loop when guessed correctly
            } else if (guess < 1 || guess > 10) {
                System.out.println("Invalid input, try again.");
                continue; // skip this iteration for invalid input
            }

            if (attempts == 5) {
                System.out.println("❌ Game over. The number was " + secret);
                return; // exit program early
            }

            System.out.println("Wrong! Attempts left: " + (5 - attempts));
        }

        sc.close();
    }
}

```

- Demonstrates:
    - `break` → correct guess ends loop
    - `continue` → invalid input skips iteration
    - `return` → exit method/program early