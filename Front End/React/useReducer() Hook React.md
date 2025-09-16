---
Created: 2025-07-11T10:07
tags:
  - Hooks
---
### What is `useReducer()`?

`useReducer()` is a React Hook used to manage **complex state** or **multiple related state values**, similar to Redux-style reducers.

> It’s an alternative to useState() — especially useful for state that depends on previous state or involves multiple updates.

  

## Basic Syntax

```JavaScript
const [state, dispatch] = useReducer(reducer, initialState);
```

- `state` — the current state
- `dispatch(action)` — sends actions to the reducer
- `reducer(state, action)` — function that decides how to update the state

  

## Simple Example

```JavaScript
function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      return state;
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  return (
    <div>
      <button onClick={() => dispatch({ type: 'decrement' })}>-</button>
      <span>{state.count}</span>
      <button onClick={() => dispatch({ type: 'increment' })}>+</button>
    </div>
  );
}
```

  

## Initial State from Function (Lazy Initialization)

```JavaScript
const init = (initialCount) => ({ count: initialCount });

const [state, dispatch] = useReducer(reducer, 10, init);
```

✅ Use when the initial state is **expensive to calculate**.

  

## Action with Payload

```JavaScript
dispatch({ type: 'add', value: 5 });

function reducer(state, action) {
  switch (action.type) {
    case 'add':
      return { count: state.count + action.value };
    default:
      return state;
  }
}
```

✅ `action` can carry extra data with custom properties like `value`, `id`, `payload`, etc.

  

## `useReducer()` vs `useState()`

|Feature|`useState`|`useReducer`|
|---|---|---|
|Simple state|✅ Yes|✅ Yes|
|Complex state logic|😐 Verbose|✅ Cleaner logic with reducer|
|Multiple related states|😐 Separate `useState()` calls|✅ Combine in one reducer|
|Externalized logic|❌ Inline only|✅ Extract reducer to another file|

  

## When to Use

✅ Good for:

- Complex components with multiple pieces of state
- State transitions that depend on **previous state**
- Centralizing state update logic
- Avoiding prop drilling when paired with `useContext`

  

## Summary Table

|Term|Description|
|---|---|
|`reducer`|Function that returns new state|
|`dispatch()`|Sends an action to the reducer|
|`state`|The current state object|
|`action`|Object that describes how to update state|

  

## Custom Example: Todo List

```JavaScript
function reducer(state, action) {
  switch (action.type) {
    case 'add':
      return [...state, { id: Date.now(), text: action.text }];
    case 'remove':
      return state.filter(todo => todo.id !== action.id);
    default:
      return state;
  }
}

function TodoApp() {
  const [todos, dispatch] = useReducer(reducer, []);

  return (
    <div>
      <button onClick={() => dispatch({ type: 'add', text: 'Learn React' })}>
        Add Todo
      </button>
      <ul>
        {todos.map(todo => (
          <li key={todo.id}>
            {todo.text}
            <button onClick={() => dispatch({ type: 'remove', id: todo.id })}>❌</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
```