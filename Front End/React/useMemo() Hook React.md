---
Created: 2025-07-11T10:07
tags:
  - Hooks
---
### What is `useMemo()`?

`useMemo()` lets you **cache the result of a calculation** so it’s **only recomputed when dependencies change**, instead of on every render.

> Use it to prevent unnecessary recalculations in performance-sensitive apps.

  

## Basic Syntax

```JavaScript
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
```

- `computeExpensiveValue` only runs again when `a` or `b` changes.
- `memoizedValue` stores the result.

  

## Practical Example

```JavaScript
function ExpensiveComponent({ num }) {
  const double = useMemo(() => {
    console.log("Computing...");
    return num * 2;
  }, [num]);

  return <p>Double: {double}</p>;
}
```

✅ Only recalculates `double` when `num` changes.

  

## Avoiding Re-renders in Child Components

```JavaScript
const list = useMemo(() => generateList(data), [data]);

<ListComponent items={list} />
```

✅ Prevents unnecessary re-renders of `ListComponent` by ensuring `items` is only recreated when `data` changes.

  

## Common Mistakes

|Mistake|Fix|
|---|---|
|Using `useMemo` for trivial values|Only use it for **expensive** calculations|
|Missing dependencies|Always list **every variable** used inside|
|Overusing `useMemo`|Adds complexity; only use when measurable|

  

## `useMemo()` vs `useCallback()`

|Hook|Returns|Use for|
|---|---|---|
|`useMemo()`|A **value**|Expensive **calculations**|
|`useCallback()`|A **function**|Memoized **function**|

  

## Summary Table

|Concept|Description|
|---|---|
|`useMemo(() => fn, [deps])`|Caches return value of `fn` unless deps change|
|Prevents recomputing|Only if dependencies didn’t change|
|Used for|Heavy computations, derived data, memo props|

  

## Good Use Cases

✅ Use `useMemo()` when:

- Rendering large lists
- Doing heavy math (e.g., filtering, sorting)
- Avoiding unnecessary renders of children
- Preventing re-creation of the same object/array across renders

  

### Example: Expensive List Filtering

```JavaScript
const filteredUsers = useMemo(() => {
  return users.filter(user => user.active);
}, [users]);
```

✅ Prevents re-filtering on every render if `users` hasn’t changed.