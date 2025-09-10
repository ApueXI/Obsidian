---
Created: 2025-08-25T19:32
tags:
  - Control-Flow
---
## 1. Full Explanation

### 🔹 Traditional `switch` Statement (Java < 14)

- Used when you want to compare a variable against multiple values.
- Works with: `byte`, `short`, `char`, `int`, `String`, and enums.

```Java
int day = 3;
switch (day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    case 3:
        System.out.println("Wednesday");
        break;
    default:
        System.out.println("Invalid day");
}

```

- `break` → prevents fall-through (execution continuing into the next case).
- `default` → executes if no match is found (like `else`).

---

### 🔹 Java 14+ Enhanced Switch (Switch Expressions)

### ✅ Arrow Syntax (Concise, no `break` needed)

```Java
int day = 3;
switch (day) {
    case 1 -> System.out.println("Monday");
    case 2 -> System.out.println("Tuesday");
    case 3 -> System.out.println("Wednesday");
    default -> System.out.println("Invalid day");
}

```

---

### ✅ Switch as an Expression (returns a value)

```Java
int day = 2;

String dayName = switch (day) {
    case 1 -> "Monday";
    case 2 -> "Tuesday";
    case 3 -> "Wednesday";
    case 4, 5, 6 -> "Weekday";  // multiple labels
    case 7 -> "Sunday";
    default -> "Invalid day";
};

System.out.println(dayName);

```

- ✅ No `break` required.
- ✅ Can return a value → assign directly to variable.
- ✅ Multiple labels (`case 4, 5, 6 ->`).

---

### ✅ Yield Keyword (for multi-line logic)

If you need multiple statements:

```Java
int score = 85;

String grade = switch (score / 10) {
    case 10, 9 -> "A";
    case 8 -> "B";
    case 7 -> "C";
    case 6 -> {
        System.out.println("Borderline pass");
        yield "D";   // use yield instead of return
    }
    default -> "F";
};

System.out.println("Grade: " + grade);

```

---

### 🔹 Gotchas

- Traditional `switch` requires `break`; Java 14+ arrow switch removes this need.
- `null` in switch → throws `NullPointerException` (unless you explicitly handle).
- Old `switch` was statement-only; new `switch` can be **expression** (returns value).

---

## 2. 📊 Summary Table

|Version|Syntax|Example|Notes|
|---|---|---|---|
|Traditional switch|`switch(var){ case X: break; }`|`switch(day){...}`|Needs `break`|
|Arrow switch (14+)|`case X ->`|`case 1 -> "One"`|No fall-through|
|Switch expression (14+)|`var = switch(x){...};`|`String d = switch(day){...};`|Can return values|
|Multiple labels|`case A, B ->`|`case 4, 5, 6 -> "Weekday"`|Combine cases|
|Yield (14+)|`yield value;`|`case 6 -> { yield "D"; }`|For multi-line blocks|

---

## 3. 🌍 Real-World Example

Imagine a **Restaurant Menu Ordering System**:

```Java
import java.util.Scanner;

public class MenuOrder {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.println("Choose a meal: 1=Pizza, 2=Burger, 3=Pasta, 4=Exit");
        int choice = sc.nextInt();

        String order = switch (choice) {
            case 1 -> "Pizza 🍕";
            case 2 -> "Burger 🍔";
            case 3 -> "Pasta 🍝";
            case 4 -> {
                System.out.println("Exiting system...");
                yield "No order";
            }
            default -> "Invalid choice ❌";
        };

        System.out.println("You ordered: " + order);

        sc.close();
    }
}

```

✅ Example Run:

```Plain
Choose a meal: 1=Pizza, 2=Burger, 3=Pasta, 4=Exit
2
You ordered: Burger 🍔
```