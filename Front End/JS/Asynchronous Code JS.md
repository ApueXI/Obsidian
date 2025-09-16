---
Created: 2025-06-23T15:40
---
### **What is Asynchronous Code?**

- Code that **doesn’t block** execution while waiting (e.g., for data, timers, I/O).
- Lets other code run **while waiting for something to finish**.

  

### **setTimeout (Async with Timer)**

```JavaScript
console.log("Start");

setTimeout(() => {
  console.log("Async code");
}, 1000);

console.log("End");
```

🟰 Output:

```Plain
Start
End
Async code
```

  

### **Callbacks (Old Way)**

```JavaScript
function fetchData(callback) {
  setTimeout(() => {
    callback("Data loaded");
  }, 1000);
}

fetchData(data => {
  console.log(data); // "Data loaded"
});
```

- ❗ Can lead to **callback hell** if deeply nested.

  

### **Promises (Better)**

```JavaScript
const fetchData = new Promise((resolve, reject) => {
  setTimeout(() => {
    resolve("Data from promise");
  }, 1000);
});

fetchData.then(data => console.log(data));
```

- Promises represent a **future value**.

  

### **Promise: Catching Errors**

```JavaScript
fetchData
  .then(data => console.log(data))
  .catch(error => console.error(error));
```

  

### **Promise Chain**

```JavaScript
Promise.resolve(5)
  .then(x => x * 2)
  .then(x => x + 1)
  .then(console.log); // 11
```

- Chain multiple `.then()` calls.

  

### **async / await (Modern, Cleanest)**

```JavaScript
async function getData() {
  try {
    const result = await fetchData;
    console.log(result);
  } catch (error) {
    console.error(error);
  }
}

getData();
```

- `await` pauses until the promise resolves.
- Must be inside an `async` function.

  

### **Async Functions Always Return Promises**

```JavaScript
async function greet() {
  return "Hello";
}

greet().then(console.log); // "Hello"
```

  

### **Parallel Promises with** `**Promise.all**`

```JavaScript
const p1 = Promise.resolve(1);
const p2 = Promise.resolve(2);

Promise.all([p1, p2]).then(values => {
  console.log(values); // [1, 2]
});
```

- Waits for **all** promises.

  

### **Race with** `**Promise.race**`

```JavaScript
Promise.race([
  Promise.resolve("Fast"),
  new Promise(res => setTimeout(() => res("Slow"), 1000))
]).then(console.log); // "Fast"
```

  

### Summary Table

|   |   |   |
|---|---|---|
|Feature|Syntax|Description|
|Delay|`setTimeout(fn, ms)`|Delayed async execution|
|Callback|`fn(cb)`|Basic async pattern|
|Promise|`new Promise((res, rej) => {})`|Handles async success/failure|
|Then chaining|`.then().then()`|Step-by-step async flow|
|async/await|`await promise`|Cleaner syntax for Promises|
|Try/catch|`try { await } catch {}`|Handle errors with async/await|
|`Promise.all`|Wait for all promises|Runs in parallel|
|`Promise.race`|First one to finish|Fastest result wins|

  

```JavaScript
function func1(params) {
    setTimeout(() => {
        console.log(`This is func 1`);
        params();
    }, 2000);
}

function func2() {
    console.log(`This is func 2`);
    console.log(`This is func 3`);
    console.log(`This is func 4`);
}

func1(func2);
```