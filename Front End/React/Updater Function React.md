---
Created: 2025-07-10T12:24
tags:
  - Hooks
---
### What is an Updater Function?

An **updater function** is a version of `setState()` or `setCount()` (when using `useState`) where you **pass a function** instead of a value.

```JavaScript
setState(prevState => {
  // return the new state based on prevState
});
```

> ✅ Use it when the new state depends on the previous state to avoid stale state issues.

  

## Basic Example

```JavaScript
const [count, setCount] = useState(0);

// ❌ Incorrect: might use stale `count` if batched
setCount(count + 1);

// ✅ Correct: uses the latest state value
setCount(prev => prev + 1);
```

  

## Complex State Example

```JavaScript
const [state, setState] = useState({ clicks: 0, views: 0 });

setState(prev => ({
  ...prev,
  clicks: prev.clicks + 1
}));
```

✅ Always **spread the previous state** when updating objects to avoid losing other fields.

  

## Why Use It?

|Situation|Why Updater Function Is Best|
|---|---|
|Multiple rapid state updates|Prevents overwriting with stale values|
|Based on previous state or props|Ensures logic is based on latest known value|
|Inside async functions or effects|Keeps things reliable in closures|

  

## With `useReducer` (similar pattern)

```JavaScript
dispatch(prev => prev + 1); // not valid syntax in reducer, just conceptually similar
```

Updaters are conceptually like Redux/reducer functions — they give **state transformation logic**.

  

## Summary

|Pattern|Use When...|
|---|---|
|`setX(newValue)`|You have a static or independent new value|
|`setX(prev => prev + 1)`|The new value depends on the current/previous one|
|`setX(prev => ({ ...prev, ... }))`|You're updating a piece of an object/array state|

  

## Common Mistakes

|Mistake|Correct Approach|
|---|---|
|`setCount(count + 1)` (in loop)|`setCount(prev => prev + 1)`|
|Overwriting objects|Use `...prev` to copy existing keys|

  

### Example: Add to Array

```JavaScript
setList(prev => [...prev, newItem]);
```

  

  

```CSS
import React, { useState } from "react";

function MyComponent() {
  const [count, setCount] = useState(0);

  // takes the PENDING state to calculate next state
  // react puts your updater funnction in a queue
  // During the next render, it wil call them in the same order
  const increment = () => {
    setCount((prevCount) => prevCount + 1);
    setCount((prevCount) => prevCount + 1);
    setCount((prevCount) => prevCount + 1);
  };
  const decrement = () => {
    setCount((prevCount) => prevCount - 1);
    setCount((prevCount) => prevCount - 1);
    setCount((prevCount) => prevCount - 1);
  };
  const reset = () => {
    setCount((prevCount) => (prevCount = 0));
  };

  return (
    <div className="counter-container">
      <p className="count-display">{count}</p>
      <button className="counter-button" onClick={decrement}>
        Decrement
      </button>
      <button className="counter-button" onClick={reset}>
        Reset
      </button>
      <button className="counter-button" onClick={increment}>
        Increment
      </button>
    </div>
  );
}

export default MyComponent;
```