---
Created: 2025-08-07T20:10
tags:
  - Unit-Testing
---
## ✅ 1. Concept Overview

Instead of using test frameworks, you can **manually write tests and simulate assertions** using:

- Basic methods
- Console output
- Exceptions for failed assertions

This is useful for:

- Quick sanity checks
- Embedded systems (no framework)
- Learning how test frameworks work internally
- Building your own micro test runner

---

## 🧰 2. Assertion Helpers

Create a small **assertion utility class** like this:

```C#
public static class Assert {
    public static void AreEqual<T>(T expected, T actual, string message = "") {
        if (!EqualityComparer<T>.Default.Equals(expected, actual)) {
            throw new Exception($"Assert.AreEqual Failed: Expected={expected}, Actual={actual}. {message}");
        }
    }

    public static void IsTrue(bool condition, string message = "") {
        if (!condition) {
            throw new Exception($"Assert.IsTrue Failed. {message}");
        }
    }

    public static void IsFalse(bool condition, string message = "") {
        if (condition) {
            throw new Exception($"Assert.IsFalse Failed. {message}");
        }
    }

    public static void IsNotNull(object obj, string message = "") {
        if (obj == null) {
            throw new Exception($"Assert.IsNotNull Failed. {message}");
        }
    }

    public static void IsNull(object obj, string message = "") {
        if (obj != null) {
            throw new Exception($"Assert.IsNull Failed. {message}");
        }
    }
}
```

---

## 🧾 3. Summary Table

|Assertion Type|Method|Description|
|---|---|---|
|Equality|`AreEqual(expected, actual)`|Checks value equality|
|Boolean true|`IsTrue(condition)`|Passes if condition is true|
|Boolean false|`IsFalse(condition)`|Passes if condition is false|
|Null check|`IsNull(obj)`|Passes if object is null|
|Not null check|`IsNotNull(obj)`|Passes if object is NOT null|

---

## 💡 4. Real-World Example: Testing a Calculator

### 🔸 Class Under Test:

```C#
public class Calculator {
    public int Add(int a, int b) => a + b;
    public int Divide(int a, int b) => b == 0 ? throw new DivideByZeroException() : a / b;
}
```

### 🔸 Simulated Test Class:

```C#
public static class CalculatorTests {
    public static void RunAllTests() {
        var calc = new Calculator();

        try {
            Assert.AreEqual(5, calc.Add(2, 3), "Add failed");
            Assert.AreEqual(0, calc.Add(-1, 1), "Add with negatives failed");
            Assert.AreEqual(2, calc.Divide(4, 2), "Divide failed");
            Assert.IsTrue(calc.Divide(9, 3) == 3, "Divide should be 3");

            // Simulate failure case
            try {
                calc.Divide(1, 0);
                Console.WriteLine("Test Failed: Expected exception not thrown.");
            } catch (DivideByZeroException) {
                Console.WriteLine("Test Passed: Divide by zero exception thrown.");
            }

            Console.WriteLine("All tests passed.");
        } catch (Exception ex) {
            Console.WriteLine("Test failed: " + ex.Message);
        }
    }
}
```

### 🔸 Program Entry:

```C#
public static void Main() {
    CalculatorTests.RunAllTests();
}
```

---

## 🛠️ 5. Bonus: Minimal Test Runner Template

```C#
public class TestRunner {
    public static void Run(params Action[] tests) {
        int passed = 0, failed = 0;

        foreach (var test in tests) {
            try {
                test();
                Console.WriteLine($"[PASS] {test.Method.Name}");
                passed++;
            } catch (Exception ex) {
                Console.WriteLine($"[FAIL] {test.Method.Name}: {ex.Message}");
                failed++;
            }
        }

        Console.WriteLine($"\n✅ {passed} passed, ❌ {failed} failed.");
    }
}
```

### Use it like:

```C#
TestRunner.Run(
    () => Assert.AreEqual(4, 2 + 2),
    () => Assert.IsTrue("abc".Contains("a")),
    () => Assert.IsFalse(5 < 3)
);
```

---

## ⚠️ 6. Gotchas & Tips

|Tip|Reason|
|---|---|
|Use `try/catch` for each test|Isolates failures and continues running|
|Give descriptive messages|Helps debug when a test fails|
|Avoid global state in tests|Leads to unpredictable failures|
|Consider using `[CallerMemberName]` for names|Makes logging easier|