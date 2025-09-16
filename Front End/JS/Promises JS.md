---
Created: 2025-06-25T17:19
---
### **What Is a Promise?**

A **Promise** is an object representing the **future result** of an asynchronous operation.

It has 3 states:

- 🕒 `pending` – waiting for a result
- ✅ `fulfilled` – operation succeeded
- ❌ `rejected` – operation failed

  

### **Creating a Promise**

```JavaScript
const myPromise = new Promise((resolve, reject) => {
  const success = true;

  setTimeout(() => {
    if (success) {
      resolve("It worked!");
    } else {
      reject("It failed.");
    }
  }, 1000);
});
```

  

### **Consuming a Promise with** `**.then()**` **and** `**.catch()**`

```JavaScript
myPromise
  .then(result => console.log("Success:", result))
  .catch(error => console.error("Error:", error));
```

- `.then()` handles success
- `.catch()` handles errors

  

### **Chaining** `**.then()**` **Calls**

```JavaScript
Promise.resolve(2)
  .then(x => x + 2)
  .then(x => x * 3)
  .then(result => console.log("Result:", result)); // 12
 
```

- Each `.then()` returns a new Promise.

  

### **Promise Error Handling**

```JavaScript
somePromise()
  .then(doSomething)
  .then(doNext)
  .catch(err => console.error("Caught:", err));
```

- One `.catch()` can handle errors in the whole chain.

  

### **Using** `**Promise.all()**` **– Run in Parallel**

```JavaScript
Promise.all([
  Promise.resolve("A"),
  Promise.resolve("B"),
  Promise.resolve("C"),
]).then(values => {
  console.log(values); // ["A", "B", "C"]
});
```

- ✅ Waits for all to succeed
- ❌ Fails if **any** fails

  

### **Using** `**Promise.race()**` **– First to Finish**

```JavaScript
Promise.race([
  new Promise(res => setTimeout(() => res("Fast"), 500)),
  new Promise(res => setTimeout(() => res("Slow"), 1000)),
]).then(console.log); // "Fast"
```

  

### **Convert a Callback to a Promise**

```JavaScript
function asyncAdd(a, b) {
  return new Promise((resolve) => {
    setTimeout(() => resolve(a + b), 1000);
  });
}

asyncAdd(2, 3).then(result => console.log(result)); // 5
```

  

### **Promise with** `**async/await**` **(Modern Usage)**

```JavaScript
async function run() {
  try {
    const result = await asyncAdd(5, 10);
    console.log("Result:", result);
  } catch (err) {
    console.error("Error:", err);
  }
}
```

- `await` works **only inside** `async` functions.

  

### Summary Table

|   |   |
|---|---|
|Method|Purpose|
|`new Promise()`|Create a new promise manually|
|`.then()`|Handle success|
|`.catch()`|Handle errors|
|`.finally()`|Run code after success/failure|
|`Promise.all()`|Wait for all to finish|
|`Promise.race()`|Take first result (win or fail)|
|`Promise.resolve()`|Create a fulfilled promise immediately|
|`Promise.reject()`|Create a rejected promise immediately|

  

```JavaScript
function eat() {
    return new Promise((resolve) => {
        setTimeout(() => {
            resolve(`I ate`);
        }, 1000);
    });
}

function sleep() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const isEat = false;
            if (isEat) {
                resolve(`I slept`);
            } else {
                reject(`i Woke`);
            }
        }, 1000);
    });
}

function woke() {
    return new Promise((resolve, reject) => {
        setTimeout(() => {
            const isWoke = true;
            if (isWoke) {
                resolve(`I wake `);
            } else {
                reject(`I slept`);
            }
        }, 1000);
    });
}

eat()
    .then((value) => {
        console.log(value);
        return sleep();
    })
    .then((value) => {
        console.log(value);
        return woke();
    })
    .then((value) => console.log(value))
    .catch((errors) => console.error(`Error: ${errors}`));
```