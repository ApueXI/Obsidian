---
Created: 2025-08-25T19:28
tags:
  - Basics-&-Foundations
---
## 1. Full Explanation

### 🔹 Output with `System.out`

- `**System.out**` → Standard output stream (prints to console).
- Common methods:
    
    ```Java
    System.out.print("Hello");    // prints without newline
    System.out.println("World");  // prints with newline
    System.out.printf("Age: %d\n", 25); // formatted output
    
    ```
    

---

### 🔹 Input with `System.in`

- `**System.in**` → Standard input stream (reads bytes from keyboard).
- Usually wrapped with `**Scanner**` or `**BufferedReader**` for easier use.

### ✅ Using `Scanner` (most common)

```Java
import java.util.Scanner;

public class InputExample {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter your name: ");
        String name = sc.nextLine();

        System.out.print("Enter your age: ");
        int age = sc.nextInt();

        System.out.println("Hello " + name + ", you are " + age + " years old.");

        sc.close();
    }
}

```

- `nextLine()` → reads full line (string).
- `nextInt()` → reads integer.
- `nextDouble()`, `nextBoolean()` etc. available.

---

### ✅ Using `BufferedReader` (faster, but more complex)

```Java
import java.io.BufferedReader;
import java.io.InputStreamReader;

public class InputBuffered {
    public static void main(String[] args) throws Exception {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

        System.out.print("Enter your city: ");
        String city = br.readLine();

        System.out.println("You live in: " + city);
    }
}

```

- `readLine()` → reads full input as string.
- Must parse manually for numbers:
    
    ```Java
    int num = Integer.parseInt(br.readLine());
    
    ```
    

---

### 🔹 Gotchas

- `Scanner.nextLine()` after `nextInt()` may consume leftover newline → use an extra `nextLine()` if needed.
- Always **close input streams** (`sc.close()`, `br.close()`) to avoid memory leaks.
- For competitive programming / huge input, prefer `BufferedReader` (faster).

---

## 2. 📊 Summary Table

|Method|Class|Example|Notes|
|---|---|---|---|
|`System.out.print`|`System.out`|`System.out.print("Hi")`|No newline|
|`System.out.println`|`System.out`|`System.out.println("Hi")`|Adds newline|
|`System.out.printf`|`System.out`|`System.out.printf("Age: %d", age)`|Formatted output|
|`Scanner.nextLine()`|`Scanner`|`String s = sc.nextLine()`|Reads string line|
|`Scanner.nextInt()`|`Scanner`|`int n = sc.nextInt()`|Reads integer|
|`BufferedReader.readLine()`|`BufferedReader`|`String s = br.readLine()`|Reads string, needs parsing for numbers|

---

## 3. 🌍 Real-World Example

Imagine a **Login System** where we collect username & password:

```Java
import java.util.Scanner;

public class LoginSystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter username: ");
        String username = sc.nextLine();

        System.out.print("Enter password: ");
        String password = sc.nextLine();

        if(username.equals("admin") && password.equals("1234")) {
            System.out.println("Login successful!");
        } else {
            System.out.println("Invalid credentials.");
        }

        sc.close();
    }
}

```

✅ Output (user input in `<>`):

```Plain
Enter username: <admin>
Enter password: <1234>
Login successful!

```

- Used **System.out** for prompts & results.
- Used **System.in + Scanner** for input.