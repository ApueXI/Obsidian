---
Created: 2025-06-19T15:22
---
### What is a Callback?

A **callback** is a function passed as an argument to another function, which is then invoked (called back) inside the outer function to complete some action.

  

### Why Use Callbacks?

- To handle asynchronous operations (e.g., network requests, timers).
- To ensure code runs _after_ another operation finishes.
- To customize behavior inside functions.

  

### Basic Syntax

```JavaScript
function greet(name, callback) {
    console.log('Hello ' + name);
    callback();
}

function sayGoodbye() {
    console.log('Goodbye!');
}

greet('Alice', sayGoodbye);
// Output:
// Hello Alice
// Goodbye!
```

  

### Common Use Cases

### 1. **Asynchronous callbacks**

```JavaScript
setTimeout(() => {
    console.log('This runs after 2 seconds');
}, 2000);
```

### 2. **Callbacks in Array Methods**

```JavaScript
const numbers = [1, 2, 3];
numbers.forEach((num) => {
    console.log(num * 2);
});
```

  

### Callback Hell (Pyramid of Doom)

Nesting many callbacks can make code hard to read:

```JavaScript
doSomething(function(result) {
    doSomethingElse(result, function(newResult) {
        doThirdThing(newResult, function(finalResult) {
            console.log(finalResult);
        });
    });
});
```

  

### Avoiding Callback Hell

- Use **Promises** or **async/await** for better readability.
- Modularize callbacks into named functions.

  

### Example: Simple Callback with Parameters

```JavaScript
function processUserInput(callback) {
    const name = 'Bob';
    callback(name);
}

processUserInput(function(name) {
    console.log('User name is: ' + name);
});
```

  

### Summary

- Callbacks are functions passed to other functions.
- They allow code to run after some work is done.
- Used heavily in async JavaScript.
- Can cause nested “callback hell” if overused.

  

```JavaScript
function greet(callback, call) {
    setTimeout(() => {
        console.log(`Hello BroCode`);
        callback();
        call();
    }, 3000);
}
function goodbye() {
    console.log(`Goodbye BroCode`);
}
function leave() {
    console.log(`Please Leave`);
}

greet(goodbye, leave);
```

  

```JavaScript
function sum(callback, x, y) {
    let result = x + y;
    callback(result);
}

function display(result) {
    console.log(`The result is ${result}`);
}
sum(displayPage, 5, 6);

function displayPage(result) {
    document.getElementById("h1").textContent = `The Result is ${result}`;
}
```