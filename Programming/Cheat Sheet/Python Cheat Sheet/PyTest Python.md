## **1. Installation**
```bash
pip install pytest
```

Run tests:
```python
pytest                # discover and run all tests 
pytest test_file.py   # run specific file 
pytest -v             # verbose mode 
pytest -k "keyword"   # run tests matching keyword
```

---

## **2. Writing Tests**

- Test **functions** starting with `test_`
- Optional: **class-based** tests (must inherit from `object` or nothing)
- Assertions use **plain `assert`**

```python
def add(a, b):
	return a + b
	
def test_add_positive():
	assert add(2, 3) == 5
	
class TestMath:
	def test_add_negative(self):
	assert add(-1, -2) == -3
```

---

## **3. Fixtures (Setup/Teardown)**
```python
import pytest  
@pytest.fixture 
def sample_data():
	return [1, 2, 3]
	
def test_length(sample_data):
	assert len(sample_data) == 3
```

- Fixtures can be **injected** into any test function.
- Can have `scope`:
    - `function` (default) – runs before each test
    - `class` – runs once per test class
    - `module` – runs once per module
    - `session` – runs once per pytest session

```python
@pytest.fixture(scope="module")
	def db_connection():
		return create_db_connection()
```

---

## **4. Parametrized Tests**
```python
import pytest
@pytest.mark.parametrize("a,b,expected", [
	(1,2,3),
	(2,3,5),
	(0,0,0)
])
def test_add(a, b, expected):
	assert a + b == expected
```

---

## **5. Testing Exceptions**

```python
import pytest
def divide(a, b):
	if b == 0:
	raise ValueError("Cannot divide by zero")
	return a / b
def test_divide_by_zero():
	with pytest.raises(ValueError):
		divide(10, 0)
```
``

---

## **6. Skipping & Marking Tests**

```python
import pytest

@pytest.mark.skip(reason="Not implemented yet")
def test_future_feature():
	pass  
	
@pytest.mark.skipif(True, reason="Condition met, skip this")
def test_conditional_skip():
	pass
```
``

---

## **7. Assertions & Comparison**

- Use **plain `assert`**
- Works for equality, truthiness, exceptions, collections:
```python
assert x == y 
assert x != y 
assert x is None 
assert x in collection 
assert x not in collection 
assert condition
```

---

## **8. Running Specific Tests**

```python
pytest test_file.py::test_function 
pytest test_file.py::TestClass::test_method
```
- `-v` for verbose output
- `-q` for quiet mode
- `-k "keyword"` runs tests matching the keyword
- `--maxfail=2` stops after 2 failures

---

## **9. Test Discovery**

- By default, pytest discovers files matching:
    - `test_*.py` or `*_test.py`
- Test functions must start with `test_`
- Test classes should **start with `Test`** (no `__init__`)

---

## **10. Real-World Example**

```python
import pytest  
# Code to test 
def multiply(a, b):
	return a * b
def divide(a, b):
	if b == 0:
		raise ValueError("Cannot divide by zero")
	return a / b  
	
# Tests 
@pytest.mark.parametrize("a,b,expected", [(2,3,6), (5,0,0)])
def test_multiply(a, b, expected):
	assert multiply(a, b) == expected
	
def test_divide_normal():
	assert divide(10,2) == 5
	
def test_divide_by_zero():
	with pytest.raises(ValueError):
		divide(10,0)
```

---

✅ **Tips**

- Use **fixtures** instead of `setUp`/`tearDown` (more flexible)
- Use **parametrize** for multiple input combinations
- Keep tests **independent**
- Avoid `print()`; use `assert` for results
- Combine with plugins like `pytest-cov` for coverage