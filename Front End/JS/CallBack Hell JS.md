---
Created: 2025-06-25T16:50
---
### **What Is Callback Hell?**

**Callback hell** happens when callbacks are nested **too deeply**, making code:

- Hard to read 😵
- Hard to debug 🔧
- Hard to maintain 🧱

### 😨 Example:

```JavaScript
doTask1(function(result1) {
  doTask2(result1, function(result2) {
    doTask3(result2, function(result3) {
      doTask4(result3, function(result4) {
        console.log("All done!");
      });
    });
  });
});
```

This is often called:

- "Pyramid of Doom" 🏔️
- "Spaghetti Code" 🍝

  

### **Why Callback Hell Happens**

- You use **asynchronous functions** (like loading data or waiting for timers).
- Each async function needs to wait for the **previous one** to finish.
- So you **nest** the next function inside the callback of the previous one.

  

### **How to Fix It**

### ✅ **Solution 1: Use Named Functions**

```JavaScript
function step1(result1) {
  doTask2(result1, step2);
}
function step2(result2) {
  doTask3(result2, step3);
}
function step3(result3) {
  doTask4(result3, finalStep);
}
function finalStep(result4) {
  console.log("Done!");
}

doTask1(step1);
```

✅ Cleaner, but still uses callbacks.

  

### **Solution 2: Use Promises**

```JavaScript
doTask1()
  .then(result1 => doTask2(result1))
  .then(result2 => doTask3(result2))
  .then(result3 => doTask4(result3))
  .then(result4 => console.log("All done!"))
  .catch(error => console.error("Error:", error));
```

✅ Flattened structure

✅ Built-in error handling

  

### **Solution 3: Use** `**async**` **/** `**await**`

```JavaScript
async function runTasks() {
  try {
    const result1 = await doTask1();
    const result2 = await doTask2(result1);
    const result3 = await doTask3(result2);
    const result4 = await doTask4(result3);
    console.log("All done!");
  } catch (err) {
    console.error("Error:", err);
  }
}

runTasks();
```

✅ Looks like synchronous code

✅ Easiest to read

✅ Easy to debug

  

### Summary Table

|   |   |   |   |
|---|---|---|---|
|Approach|Readability|Error Handling|Best For|
|Nested Callbacks|😵 Bad|❌ Manual|Simple or one-time async work|
|Named Functions|😐 Medium|❌ Manual|Breaking complex logic|
|Promises|🙂 Good|✅ Built-in|Chained async operations|
|async/await|😀 Best|✅ Built-in|Clean and readable workflows|

  

```JavaScript
function say1(params) {
    setTimeout(() => {
        console.log(`Task 1 is complete`);
        params();
    }, 1000);
}
function say2(params) {
    setTimeout(() => {
        console.log(`Task 2 is complete`);
        params();
    }, 1000);
}
function say3(params) {
    setTimeout(() => {
        console.log(`Task 3 is complete`);
        params();
    }, 1000);
}
function say4(params) {
    setTimeout(() => {
        console.log(`Task 4 is complete`);
        params();
    }, 1000);
}

say1(() => {
    say2(() => {
        say3(() => {
            say4(() => {
                console.log(`Task is completE`);
            });
        });
    });
});
```