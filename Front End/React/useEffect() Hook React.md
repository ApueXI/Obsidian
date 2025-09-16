---
Created: 2025-07-11T10:07
tags:
  - Hooks
---
### What is `useEffect()`?

`useEffect()` is a hook that runs **side effects** in functional components.

Side effects are operations that:

- Reach **outside** React (e.g., fetch data, modify the DOM)
- Should happen **after render**
- Might require **cleanup**

  

### Basic Syntax

```JavaScript
import { useEffect } from 'react';

useEffect(() => {
  // Code runs after the component renders
});
```

🧠 Think of it like `componentDidMount`, `componentDidUpdate`, and `componentWillUnmount` in one.

  

### Run Once on Mount (Empty Dependency Array)

```JavaScript
useEffect(() => {
  console.log("Component mounted");
}, []);
```

✅ Good for:

- Fetching data on load
- Subscribing to services
- Setting up timers

  

### Run When a Value Changes

```JavaScript
useEffect(() => {
  console.log("Count changed:", count);
}, [count]);
```

✅ Only re-runs when `count` changes

⚠️ Be careful: every value used inside the effect should be in the array.

  

### Cleanup Function

```JavaScript
useEffect(() => {
  const timer = setInterval(() => {
    console.log("Tick");
  }, 1000);

  return () => {
    clearInterval(timer); // Cleanup
  };
}, []);
```

✅ Cleanup runs:

- When the component unmounts
- Before running the effect again (if dependencies changed)

  

### Data Fetching Example

```JavaScript
useEffect(() => {
  async function fetchData() {
    const res = await fetch('https://api.example.com');
    const data = await res.json();
    setData(data);
  }
  fetchData();
}, []);
```

  

### Common Gotchas

|Mistake|Fix|
|---|---|
|Missing dependencies|Add them to the `[]` dependency array|
|Infinite loop|Avoid updating state unconditionally in effect|
|Re-declaring functions|Use `useCallback` or `useMemo` to memoize them|

  

### Summary Table

|Pattern|When to Use|
|---|---|
|`useEffect(() => { ... }, [])`|Run once on mount|
|`useEffect(() => { ... }, [x])`|Run when `x` changes|
|`return () => { ... }`|Cleanup logic (unsubscribe, clear timer)|

  

### Related Hooks

|Hook|Purpose|
|---|---|
|`useState`|Store values between renders|
|`useRef`|Keep mutable values without re-rendering|
|`useLayoutEffect`|Like `useEffect`, but fires **before paint**|