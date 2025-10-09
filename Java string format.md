## 🔹 Common Format Specifiers in Java

|Specifier|Meaning|Example Output|
|---|---|---|
|`%s`|String|`"Hello"`|
|`%d`|Integer (decimal)|`42`|
|`%f`|Floating-point (decimal notation)|`3.141593`|
|`%.2f`|Floating-point with 2 decimal places|`3.14`|
|`%e`|Floating-point in scientific notation|`3.141593e+00`|
|`%c`|Character|`A`|
|`%b`|Boolean|`true`|
|`%o`|Octal integer|`52` (for `42`)|
|`%x`|Hex integer (lowercase)|`2a` (for `42`)|
|`%X`|Hex integer (uppercase)|`2A` (for `42`)|
|`%n`|Platform-independent newline|_(like `\n` but safer)_|

---

## 🔹 Flags and Width Modifiers

You can also control **width, alignment, and padding**:

| Example | Meaning                    | Output (for `42`) |
| ------- | -------------------------- | ----------------- |
| `%5d`   | Right-align in 5 spaces    | `" 42"`           |
| `%-5d`  | Left-align in 5 spaces     | `"42 "`           |
| `%05d`  | Pad with zeros to 5 digits | `"00042"`         |
| `%+d`   | Always show sign           | `+42`             |
| `%,d`   | Use grouping separator     | `1,000,000`       |

---
## 🔹 Examples
```java
public class Main {
    public static void main(String[] args) {
        String name = "Alice";
        int age = 30;
        double pi = Math.PI;

        System.out.printf("Name: %s%n", name);        // String
        System.out.printf("Age: %d%n", age);          // Integer
        System.out.printf("Pi: %.2f%n", pi);          // Floating point, 2 decimals
        System.out.printf("Hex: %x%n", age);          // Hexadecimal
        System.out.printf("Zero-padded: %05d%n", age);// Padding
    }
}

```
**Output:**
```java
Name: Alice
Age: 30
Pi: 3.14
Hex: 1e
Zero-padded: 00030
```

---

⚡ So the most common ones you’ll use:

- `%s` → string
- `%d` → int
- `%f` / `%.2f` → floating-point
- `%n` → newline