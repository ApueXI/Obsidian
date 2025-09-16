---
Created: 2025-06-22T17:47
---
### **What is a Closure?**

A **closure** is when a function **remembers** and **accesses variables** from its outer scope **even after the outer function has finished running**.

  

### **Basic Closure Example**

```JavaScript
function outer() {
  let count = 0;

  function inner() {
    count++;
    return count;
  }

  return inner;
}

const counter = outer(); // outer() runs once
console.log(counter()); // 1
console.log(counter()); // 2
```

✅ `inner()` still has access to `count` — even though `outer()` has finished.

  

### **Why Use Closures?**

- **Encapsulation** (hide private variables)
- **Data persistence** between function calls
- **Function factories**

  

### **Closure for Private Variables**

```JavaScript
function createSecret() {
  let secret = "🔒";

  return {
    getSecret: () => secret,
    setSecret: (s) => { secret = s; }
  };
}

const safe = createSecret();
console.log(safe.getSecret()); // "🔒"
safe.setSecret("🗝️");
console.log(safe.getSecret()); // "🗝️"
```

- `secret` is **private** — not accessible outside directly.

  

### **Closure in Loops (with** `**let**`**)**

```JavaScript
for (let i = 1; i <= 3; i++) {
  setTimeout(() => console.log(i), 100 * i); // 1, 2, 3
}
```

- `let` creates a new binding for each loop → closures work as expected.

  

### **Closure Factory Function**

```JavaScript
function multiplyBy(x) {
  return function(y) {
    return x * y;
  };
}

const double = multiplyBy(2);
console.log(double(5)); // 10
```

- Closure “remembers” `x = 2`.

  

### **Closures with Event Listeners**

```JavaScript
function setupButton() {
  let clicks = 0;

  document.getElementById("myBtn").onclick = function () {
    clicks++;
    console.log(`Clicked ${clicks} times`);
  };
}
```

- The inner function keeps access to `clicks`.

  

### Summary Table

|   |   |   |
|---|---|---|
|Concept|Example|Purpose|
|Basic closure|Function inside function|Remembers outer scope|
|Data privacy|Return inner functions|Hide variables|
|Persistent state|Counter or config|Keeps values across calls|
|Factory functions|`return function(...)`|Custom reusable logic|
|Loop safety|Use `let`|Block-scoped variable per loop|

  

```JavaScript
function createCounter() {
    let count = 0;

    function increment() {
        count++;
        console.log(`Count has increase to ${count}`);
    }
    function decrememt() {
        count--;
        console.log(`Count has increase to ${count}`);
    }
    function reset() {
        count = 0;
        console.log(`Count has increase to ${count}`);
    }

    function getCount() {
        return count;
    }

    return { increment: increment, decrememt, reset: reset, getCount };
}

const counter = createCounter();

counter.increment();
counter.reset();
counter.increment();
counter.increment();
counter.increment();
counter.decrememt();
counter.decrememt();
console.log(counter.getCount());
```

  

```JavaScript
// wrong way to do this
const score = function () {
    let score = 0;

    function increaseScore(pts) {
        score += pts;
        console.log(`Add ${pts}`);
    }

    function decreaseScore(pts) {
        score -= pts;
        console.log(`Minus ${pts}`);
    }

    function getScore() {
        console.log(`Current Score is ${score}`);
    }

    return { increaseScore, decreaseScore, getScore };
};

// correct way to do this
const scores = (function() {
    let score = 0;

    function increaseScore(pts) {
        score += pts;
        console.log(`Add ${pts}`);
    }

    function decreaseScore(pts) {
        score -= pts;
        console.log(`Minus ${pts}`);
    }

    function getScore() {
        console.log(`Current Score is ${score}`);
    }

    return { increaseScore, decreaseScore, getScore };
})(); 

scores.increaseScore(1);
scores.increaseScore(1);
scores.increaseScore(1);
scores.increaseScore(1);
scores.decreaseScore(1);
scores.getScore();
```

  

```JavaScript
function createWallet(initialBalance = 0) {
    let balance = initialBalance; // private variable

    function deposit(amount) {
        if (amount > 0) {
            balance += amount;
            console.log(`Deposited ${amount}. New balance: ${balance}`);
        }
    }

    function withdraw(amount) {
        if (amount <= balance) {
            balance -= amount;
            console.log(`Withdrew ${amount}. New balance: ${balance}`);
        } else {
            console.log("Insufficient funds.");
        }
    }

    function getBalance() {
        return balance;
    }

    return {
        deposit,
        withdraw,
        getBalance
    };
}

const myWallet = createWallet(100);
myWallet.deposit(50);         // Deposited 50. New balance: 150
myWallet.withdraw(20);        // Withdrew 20. New balance: 130
console.log(myWallet.balance); // ❌ undefined
console.log(myWallet.getBalance()); // ✅ 130
```