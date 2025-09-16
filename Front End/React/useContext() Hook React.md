---
Created: 2025-07-11T10:07
tags:
  - Hooks
---
### What is `useContext()`?

The `useContext()` hook lets you **read values from a React Context** inside a functional component.

It works with the `Context API`, which allows you to **share state** or data across deeply nested components **without passing props** manually.

  

## Creating a Context

```JavaScript
import { createContext } from 'react';

const ThemeContext = createContext('light'); // Default value
```

  

## Providing a Context Value

Wrap a part of your component tree with the **Provider** and pass a value:

```JavaScript
function App() {
  return (
    <ThemeContext.Provider value="dark">
      <Toolbar />
    </ThemeContext.Provider>
  );
}
```

  

## Consuming Context with `useContext()`

```JavaScript
import { useContext } from 'react';

function Toolbar() {
  const theme = useContext(ThemeContext); // Get context value
  return <div className={`toolbar ${theme}`}>Theme: {theme}</div>;
}
```

✅ You can use `useContext()` in **any child** of the Provider

✅ No need to pass props through intermediate components

  

## Custom Context Example

```JavaScript
// context.js
export const UserContext = createContext();

// App.jsx
<UserContext.Provider value={{ name: "Nein", loggedIn: true }}>
  <Dashboard />
</UserContext.Provider>

// Dashboard.jsx
const user = useContext(UserContext);
<p>Welcome, {user.name}</p>
```

  

## Dynamic Context Value with State

```JavaScript
const ThemeContext = createContext();

function App() {
  const [theme, setTheme] = useState("light");

  return (
    <ThemeContext.Provider value={{ theme, setTheme }}>
      <Toolbar />
    </ThemeContext.Provider>
  );
}
```

```JavaScript
function ThemeToggle() {
  const { theme, setTheme } = useContext(ThemeContext);

  return (
    <button onClick={() => setTheme(theme === "light" ? "dark" : "light")}>
      Switch to {theme === "light" ? "dark" : "light"} mode
    </button>
  );
}
```

✅ You can share state + update functions via context

  

## Common Mistakes

|Mistake|Solution|
|---|---|
|Using `useContext` outside Provider|Wrap your components in the Provider|
|Forgetting to export/import Context|Export `createContext()` from a file|
|Changing context without `useState`|Use `useState` to manage shared state|

  

## Summary Table

|Hook/API|Use|
|---|---|
|`createContext()`|Create a context|
|`.Provider`|Supply the value|
|`useContext()`|Access context value inside a component|

  

## Perfect For:

- ✅ Auth/User data
- ✅ Theme switching
- ✅ App-wide settings
- ✅ Language/locale selection