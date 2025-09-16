---
Created: 2025-07-11T10:07
tags:
  - Hooks
---
## `useCallback()` Cheat Sheet

### 🧠 What is `useCallback()`?

`useCallback()` returns a **memoized version of a function**, preventing it from being re-created on every render unless its dependencies change.

> Use it to avoid re-rendering child components or re-running effects when a function hasn't changed.

  

## Basic Syntax

```JavaScript
const memoizedFn = useCallback(() => {
  // Your logic here
}, [dependencies]);
```

- Returns the **same function reference** unless a dependency changes.
- Use when passing functions to components that rely on **reference equality** (like `React.memo()` or `useEffect()`).

  

## Example: Stable Event Handler

```JavaScript
const handleClick = useCallback(() => {
  console.log("Clicked");
}, []);
```

✅ Prevents this function from being recreated on each render.

  

## Passing to Memoized Child

```JavaScript
const handleSelect = useCallback((id) => {
  setSelectedId(id);
}, [setSelectedId]);

return <ItemList onSelect={handleSelect} />;
```

✅ Prevents `ItemList` from re-rendering if `handleSelect` doesn’t change

✅ Works best with `React.memo()`:

```JavaScript
\const ItemList = React.memo(({ onSelect }) => {
  // ...
});
```

  

## `useCallback()` vs `useMemo()`

|Hook|Returns|Use For|
|---|---|---|
|`useCallback`|A **function**|Memoize a callback function|
|`useMemo`|A **value**|Memoize an expensive result|

  

## With `useEffect()`

```JavaScript
const fetchData = useCallback(() => {
  // fetch logic
}, [userId]);

useEffect(() => {
  fetchData();
}, [fetchData]); // ✅ No infinite loop
```

✅ `useCallback` keeps function identity stable

✅ Avoids re-triggering `useEffect`

  

## Summary Table

|Feature|Use When...|
|---|---|
|Function passed to children|Use `useCallback` to avoid unnecessary re-renders|
|Dependency-heavy logic|Avoid function recreation on every render|
|Memoize async or handlers|Keep function references stable|

  

## Good Use Cases

✅ `useCallback()` is great when:

- Passing props to `React.memo()` children
- Re-using a function in `useEffect()`
- Preventing stale closures in event handlers
- Memoizing expensive functions that get re-declared

  

### Bonus: Simple Full Example

```JavaScript
function Counter() {
  const [count, setCount] = useState(0);

  const increment = useCallback(() => {
    setCount(c => c + 1); // ✅ safer
  }, []);

  return <button onClick={increment}>Count: {count}</button>;
}
```