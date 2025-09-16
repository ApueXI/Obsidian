---
Created: 2025-06-23T16:04
---
### **What is an Error?**

An **error** is a problem that stops code from running correctly. JavaScript has built-in error handling using `try...catch`.

  

### **Basic** `**try...catch**`

```Plain
js
CopyEdit
try {
  // Code that may throw an error
  const result = riskyFunction();
  console.log(result);
} catch (error) {
  console.error("Something went wrong:", error.message);
}

```

- Code inside `try` runs first.
- If it **throws** an error, `catch` runs.
- `error` contains details like `.message`, `.name`, and `.stack`.

  

### **Using** `**finally**`

```Plain
js
CopyEdit
try {
  runProcess();
} catch (e) {
  console.error("Error:", e.message);
} finally {
  console.log("Always runs — success or fail");
}

```

- `finally` always runs, **even if there's an error**.

  

### **Throwing Custom Errors**

```Plain
js
CopyEdit
function divide(a, b) {
  if (b === 0) {
    throw new Error("Cannot divide by zero");
  }
  return a / b;
}

try {
  divide(10, 0);
} catch (e) {
  console.error(e.message); // "Cannot divide by zero"
}

```

  

### **Creating Custom Error Classes**

```JavaScript
class ValidationError extends Error {
  constructor(message) {
    super(message);
    this.name = "ValidationError";
  }
}

throw new ValidationError("Invalid input");
```

  

### **Error Handling in Promises**

```JavaScript
fetch("invalid-url")
  .then(response => response.json())
  .catch(error => console.error("Fetch failed:", error));
```

- Use `.catch()` to handle errors in promises.

  

### **Error Handling in async/await**

```JavaScript
async function loadData() {
  try {
    const response = await fetch("invalid-url");
    const data = await response.json();
    console.log(data);
  } catch (err) {
    console.error("Async error:", err.message);
  }
}
```

- `try...catch` works with `async/await` like synchronous code.

  

### **Silent Fail (⚠️ Not Recommended)**

```JavaScript
try {
  doSomethingRisky();
} catch (e) {
  // empty catch — avoids crash, but hides problem!
}
```

- Avoid this unless you intentionally suppress specific errors.

  

To catch a **specific error** in JavaScript, you can use a `try...catch` block and check the error inside the `catch` clause using an `if` or `instanceof` statement. Here's a breakdown:

  

### Basic Syntax

```JavaScript
try {
  // code that may throw
} catch (error) {
  if (error instanceof TypeError) {
    console.error("Caught a TypeError:", error.message);
  } else if (error instanceof ReferenceError) {
    console.error("Caught a ReferenceError:", error.message);
  } else {
    console.error("Caught an unknown error:", error.message);
  }
}
```

  

### Custom Errors

You can also define and catch custom errors:

```JavaScript
class CustomError extends Error {
  constructor(message) {
    super(message);
    this.name = "CustomError";
  }
}

try {
  throw new CustomError("Something went wrong!");
} catch (error) {
  if (error instanceof CustomError) {
    console.log("Caught a custom error:", error.message);
  } else {
    console.error("Other error:", error);
  }
}
```

  

### Check Using `error.name`

If you don’t want to use `instanceof`, you can also check the `error.name`:

```JavaScript
try {
  null.f(); // Will throw a TypeError
} catch (error) {
  if (error.name === "TypeError") {
    console.log("Type error occurred");
  }
}
```

  

### With Async/Await (Promises)

```JavaScript
async function fetchData() {
  try {
    const res = await fetch("invalid-url");
  } catch (error) {
    if (error instanceof TypeError) {
      console.log("Network error or bad URL");
    }
  }
}
```

  

### Summary Table

|   |   |   |
|---|---|---|
|Feature|Example|Notes|
|Try/catch|`try { ... } catch (e) { ... }`|Handle synchronous errors|
|Finally|`finally { ... }`|Always runs|
|Throw custom error|`throw new Error("message")`|Manually trigger an error|
|Custom error class|`class MyError extends Error {}`|Your own error types|
|Promise error|`.catch(error => ...)`|Handles rejected Promises|
|async/await error|`try { await } catch {}`|Clean async error handling|

  

```JavaScript
try {
    console.leg(`Hello world`);
} catch (error) {
    console.error(`Errpr has occured ${error}`);
} finally {
    console.log(`Database has been closed`);
}

console.log(`End Program`);
```

```JavaScript
try {
    const dividend = Number(window.prompt(`Enter a dividend: `));
    const divisor = Number(window.prompt(`Enter a divosor: `));

    if (divisor == 0) {
        window.alert("You cant diide by zero")
        throw new Error("You cant diide by zero");
    }
    if (isNaN(dividend) || isNaN(divisor)) {
        window.alert("Value must be a number")
        throw new Error("Value must be a number");
    }

    const result = dividend / divisor;

    console.log(result);
} catch (error) {
    console.error(error);
}

console.log(`Program End`);
```