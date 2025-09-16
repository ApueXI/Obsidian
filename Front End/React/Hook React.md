---
Created: 2025-07-11T10:58
tags:
  - Hooks
---
### What are Hooks?

**Hooks** let you use **state** and other **React features** inside **functional components**—without writing class components.

Hooks start with `use` (like `useState`, `useEffect`, etc.).

  

## `useState()` – Add State

```JavaScript
const [count, setCount] = useState(0);
```

- ✅ Use for local state
- 🔁 Update using `setCount(...)`
- ⚠️ Triggers re-render

  

## `useEffect()` – Side Effects

```JavaScript
useEffect(() => {
  console.log("Runs after render");

  return () => {
    console.log("Cleanup before unmount or re-run");
  };
}, [dependency]);
```

- ✅ Use for: API calls, subscriptions, timers
- 📦 Runs after render by default
- 🔁 Re-runs when dependencies change

  

## `useRef()` – Mutable References

```JavaScript
const inputRef = useRef();

<input ref={inputRef} />
<button onClick={() => inputRef.current.focus()}>Focus</button>
```

- ✅ Store **mutable values** that persist across renders
- ❌ Changing `.current` doesn't trigger re-render

  

## `useContext()` – Access Context

```JavaScript
const user = useContext(UserContext);
```

- ✅ Use to **consume global data**
- 👨‍👩‍👧‍👦 Works with `React.createContext()`

  

## `useReducer()` – Alternative to `useState`

```JavaScript
const [state, dispatch] = useReducer(reducer, initialState);
```

- ✅ Best for **complex state logic**
- Like `Redux` but local to the component

  

## `useMemo()` – Memoize Computations

```JavaScript
const total = useMemo(() => calculateTotal(items), [items]);
```

- ✅ Avoids **recalculating** expensive logic unless needed

  

## `useCallback()` – Memoize Functions

```JavaScript
const handleClick = useCallback(() => doSomething(id), [id]);
```

- ✅ Keeps same function reference unless dependencies change
- 📦 Useful when passing callbacks to child components

  

## `useLayoutEffect()` – Like `useEffect`, but fires **before paint**

```JavaScript
useLayoutEffect(() => {
  // Runs before browser paints
});
```

- ⚠️ Use **only if needed** for layout measurements or sync DOM updates

  

## `useImperativeHandle()` – Expose Methods to Parent

Used with `forwardRef` to expose functions from a child component to its parent.

  

### Summary Table

|Hook|Use Case|
|---|---|
|`useState`|Local state in a functional component|
|`useEffect`|Side effects (fetching, timers, etc.)|
|`useRef`|Referencing DOM or persistent values|
|`useContext`|Access context provider values|
|`useReducer`|Complex or grouped state management|
|`useMemo`|Expensive calculations|
|`useCallback`|Memoize event handlers/functions|
|`useLayoutEffect`|DOM reads before paint|
|`useImperativeHandle`|Custom instance methods for refs|