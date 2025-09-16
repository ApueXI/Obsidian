---
Created: 2025-07-11T10:07
tags:
  - Hooks
---
### What is `useState`?

`useState` is a **React Hook** that lets you add **stateful logic** to functional components.

  

### Basic Usage

```JavaScript
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0); // Declare state variable 'count' with initial value 0

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```

- `count` — current state value
- `setCount` — function to update the state
- `useState(0)` — initializes the state to `0`

  

### Using Multiple States

```JavaScript
function Form() {
  const [name, setName] = useState('');
  const [age, setAge] = useState(18);

  return (
    <div>
      <input value={name} onChange={e => setName(e.target.value)} placeholder="Name" />
      <input value={age} onChange={e => setAge(Number(e.target.value))} type="number" />
      <p>{name} is {age} years old.</p>
    </div>
  );
}
```

  

### Updating State Based on Previous State

When new state depends on old state, pass a function to `setState`:

```JavaScript
setCount(prevCount => prevCount + 1);
```

This avoids stale state issues.

  

### Initial State Can Be a Function (Lazy Initialization)

```JavaScript
const [value, setValue] = useState(() => expensiveComputation());
```

The function runs only once during initial render.

  

### State Updates Are Asynchronous

Multiple `setState` calls may batch and update asynchronously.

  

### Summary Table

|Feature|Example|Notes|
|---|---|---|
|Declare state|`const [count, setCount] = useState(0)`|`count` initial value = 0|
|Update state|`setCount(count + 1)`|Triggers component re-render|
|Update based on previous|`setCount(prev => prev + 1)`|Safer when state depends on old|
|Lazy initialization|`useState(() => computeExpensiveValue())`|Runs computation once on mount|

  

```JavaScript
import React, { useState } from "react";

function MyComponent() {
  const [name, setName] = useState("Guest");
  const [age, setAge] = useState(0);
  const [isStudent, setIsStudent] = useState(false);

  const updateName = () => {
    setName("Bro Code");
  };
  const incrementAge = () => {
    setAge(age + 1);
  };
  const toggleStudentStat = () => {
    setIsStudent(!isStudent);
  };

  return (
    <div>
      <p>Name: {name}</p>
      <button onClick={updateName}>Set Name</button>
      <br />

      <p>Age: {age}</p>
      <button onClick={incrementAge}>Increment Age</button>
      <br />

      <p>Student: {isStudent ? "Yes" : "No"}</p>
      <button onClick={toggleStudentStat}>Toggle Status</button>
    </div>
  );
}
export default MyComponent;
```

  

```JavaScript
import React, { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };
  const decrement = () => {
    setCount(count - 1);
  };
  const reset = () => {
    setCount(0);
  };

  return (
    <div className="counter-container">
      <p className="count-display">{count}</p>
      <button className="counter-button" onClick={decrement}>Decrement</button>
      <button className="counter-button" onClick={reset}>Reset</button>
      <button className="counter-button" onClick={increment}>Increment</button>
    </div>
  );
}

export default Counter;
```

```JavaScript
.counter-container {
  text-align: center;
  font-family: sans-serif, Arial, Helvetica, sans-serif;
}
.count-display {
  font-size: 10em;
  margin-top: 0;
  margin-bottom: 50px;
}
.counter-button {
  width: 150px;
  height: 50px;
  font-size: 1.5em;
  font-weight: bold;
  margin: 0px 5px;
  color: white;
  border: none;
  border-radius: 15px;
  cursor: pointer;
  background-color: hsl(197, 100%, 58%);
}
.counter-button:hover {
  background-color: hsl(197, 100%, 48%);
}
```