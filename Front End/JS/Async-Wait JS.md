---
Created: 2025-06-25T17:21
---
### **What is** `**async/await**`**?**

- `async` and `await` make **asynchronous code look like synchronous code**.
- Built on top of **Promises**.
- Cleaner alternative to `.then()` and `.catch()` chains.

  

### **Declaring an** `**async**` **Function**

```JavaScript
async function getData() {
  return "Hello";
}

getData().then(console.log); // "Hello"
```

- An `async` function **always returns a Promise**.

  

### **Using** `**await**`

```JavaScript
async function showData() {
  const data = await fetchData(); // wait until fetchData() resolves
  console.log(data);
}
```

- `await` pauses execution **until the promise resolves**.
- Can only be used **inside** `**async**` **functions**.

  

### **Error Handling with** `**try...catch**`

```JavaScript
async function loadData() {
  try {
    const res = await fetch("https://api.example.com/data");
    const json = await res.json();
    console.log(json);
  } catch (err) {
    console.error("Fetch failed:", err);
  }
}
```

✅ Clean error handling

✅ Easier to debug

  

### **Sequential vs Parallel** `**await**`

### ❗ Sequential (slower)

```JavaScript
const a = await task1();
const b = await task2();
```

### ✅ Parallel (faster)

```JavaScript
const [a, b] = await Promise.all([task1(), task2()]);
```

  

### **Using** `**await**` **in Arrow Functions**

```JavaScript
const run = async () => {
  const data = await fetchData();
  console.log(data);
};
```

  

### **Custom Async Delay**

```JavaScript
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function waitThenSay() {
  await delay(1000);
  console.log("Waited 1 second!");
}
```

  

### **Common Mistake:** `**await**` **Outside** `**async**`

```JavaScript
// ❌ Invalid:
const data = await fetch("..."); // SyntaxError

// ✅ Fix:
(async () => {
  const data = await fetch("...");
})();
```

  

### Summary Table

|   |   |
|---|---|
|Keyword|Purpose|
|`async`|Declares a function that returns a Promise|
|`await`|Pauses inside an async function until resolved|
|`try/catch`|Handles errors in async/await code|
|`Promise.all`|Run multiple async tasks in parallel|

  

### Example: Full Workflow

```JavaScript
async function fetchUser() {
  try {
    const res = await fetch("https://api.example.com/user");
    const user = await res.json();
    console.log("User:", user);
  } catch (err) {
    console.error("Failed to fetch user:", err);
  }
}
```

  

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
            const isEat = true;
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

async function doChores() {
    try {
        const eatResult = await eat();
        console.log(eatResult);
        const sleepResult = await sleep();
        console.log(sleepResult);
        const wokeResult = await woke();
        console.log(wokeResult);
    } catch (error) {
        console.error(`Error: ${error}`);
    }
}
doChores();
```