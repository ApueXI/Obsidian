## **1. Concept**

`unittest` is Python’s built-in framework for **unit testing**. It helps you test individual functions, methods, or classes in isolation to ensure they behave correctly.

- Part of Python standard library: no external installation needed.
    
- Inspired by Java’s JUnit.
    
- Supports test discovery, setup/teardown routines, and assertions.
    

**When to use:**
- Testing functions, classes, or modules.
- Automating regression checks.
- Verifying edge cases and exceptions.

---

## **2. Basic Syntax**
```python
import unittest

# Function to test 
def add(a, b):
	return a + b  
	
# Test class 
class TestMath(unittest.TestCase):
	def test_add_positive(self):
		self.assertEqual(add(2, 3), 5)  

if __name__ == "__main__":
	unittest.main()
```
**Notes:**

- Test classes **must inherit** from `unittest.TestCase`.
- Test method names **must start with** `test_`.
- Run tests with `python test_file.py` or `python -m unittest discover`.
---

## **3. Common Assertions**

|Assertion|Meaning|
|---|---|
|`assertEqual(a, b)`|a == b|
|`assertNotEqual(a, b)`|a != b|
|`assertTrue(x)`|x is True|
|`assertFalse(x)`|x is False|
|`assertIs(a, b)`|a is b|
|`assertIsNone(x)`|x is None|
|`assertIn(a, b)`|a in b|
|`assertNotIn(a, b)`|a not in b|
|`assertRaises(Exception, func)`|func raises Exception|

---

## **4. Setup and Teardown**

Use `setUp` and `tearDown` to prepare resources for each test:

```python
class TestExample(unittest.TestCase):
	def setUp(self):
		self.data = [1, 2, 3]
	def tearDown(self):
		self.data = None
	def test_length(self):
		self.assertEqual(len(self.data), 3)
```
- `setUp()`: runs **before each test method**.
- `tearDown()`: runs **after each test method**.

For class-level setup/teardown:
```python
@classmethod
def setUpClass(cls):
	# runs once before all tests  

@classmethod def tearDownClass(cls):
	# runs once after all tests
```

---

## **5. Testing Exceptions**

```python
def divide(a, b):
	if b == 0:
	raise ValueError("Cannot divide by zero")
	return a / b  class TestDivide(unittest.TestCase):
	
def test_divide_by_zero(self):
	with self.assertRaises(ValueError):
	divide(10, 0)
```
---

## **6. Test Discovery**

- Run all tests in a folder:
```bash
python -m unittest discover
```

- Run specific file:
```bash
python -m unittest test_file.py
```

- Run specific test class or method:
```bash
python -m unittest test_file.TestClass.test_method
```

---

## **7. Real-World Example**

Suppose you have a small calculator module:
```python
# calculator.py 
def add(a, b):
	return a + b  
	
def divide(a, b):
	if b == 0:
	raise ZeroDivisionError("Cannot divide by zero")
	return a / b
```


Unit tests:
```python
import unittest 
from calculator import add, divide  
class TestCalculator(unittest.TestCase):
	def test_add(self):
		self.assertEqual(add(5, 7), 12)
	def test_divide_normal(self):
		self.assertEqual(divide(10, 2), 5)
	def test_divide_by_zero(self):
		with self.assertRaises(ZeroDivisionError):
			divide(10, 0)
			
if __name__ == "__main__":     unittest.main()

```

**Highlights:**

- Checks **normal functionality**.
- Checks **edge case** (division by zero).
- Independent, automated, and readable.

---

## **8. Tips & Gotchas**

- Always **name test methods starting with `test_`**; otherwise, they won't be discovered.
- Use `setUp` to reduce **duplicate code**.
- Combine `assert` methods for **clear error messages**.
- Avoid relying on **test order**; each test should be independent.