---
Created: 2025-06-22T20:32
---
### **What is** `**setTimeout**`**?**

- `setTimeout` schedules a function to run **once** after a specified delay (in milliseconds).

```JavaScript
setTimeout(function() {
  console.log("Hello after 2 seconds");
}, 2000);
```

  

### **Basic Syntax**

```JavaScript
setTimeout(callbackFunction, delayInMilliseconds, arg1, arg2, ...);
```

- `callbackFunction`: function to run after delay.
- `delayInMilliseconds`: time to wait before running function.
- Additional arguments can be passed to callback.

  

### **Using Arrow Function**

```JavaScript
setTimeout(() => {
  console.log("Delayed message");
}, 1000);
```

  

### **Passing Arguments**

```JavaScript
function greet(name) {
  console.log(`Hello, ${name}!`);
}

setTimeout(greet, 1500, "Alice");
```

- Arguments after delay are passed to the callback.

  

### **Canceling a Timeout**

```JavaScript
const timeoutId = setTimeout(() => {
  console.log("This won't run");
}, 3000);

clearTimeout(timeoutId);
```

- Use `clearTimeout(timeoutId)` to cancel scheduled timeout.

  

### **Timeout with Named Function**

```JavaScript
function sayHi() {
  console.log("Hi!");
}

const id = setTimeout(sayHi, 2000);
```

  

### **Common Uses**

- Delaying UI updates
- Polling or retries
- Creating simple animations or effects

  

### Summary Table

|   |   |   |
|---|---|---|
|Feature|Example|Notes|
|Basic delay|`setTimeout(() => {}, 1000)`|Run once after delay|
|Passing arguments|`setTimeout(func, 1000, arg1, arg2)`|Arguments passed to callback|
|Cancel timeout|`clearTimeout(timeoutId)`|Stop scheduled function|
|Named function usage|`setTimeout(funcName, 1000)`|Cleaner and reusable|

  

```HTML
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Set Time Out</title>
    </head>
    <body>
        <button
            onclick="startTimer()"
            style="height: 3em; width: 7em; margin-top: 20px"
        >
            START</button
        ><br />

        <button
            onclick="clearTimer()"
            style="height: 3em; width: 7em; margin-top: 20px"
        >
            CLEAR
        </button>

        <script>
            let timeoutid;

            function startTimer() {
                timeoutid = setTimeout(() => {
                    window.alert(`Hello world`);
                }, 3000);
                console.log(`Started`);
            }

            function clearTimer() {
                clearTimeout(timeoutid);
                console.log(`Cleared`);
            }
        </script>
    </body>
</html>
```