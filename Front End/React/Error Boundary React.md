---
Created: 2025-07-18T16:37
---
## **What is an Error Boundary?**

- A **React component** that **catches JavaScript errors** in its child component tree.
- Prevents the entire app from crashing by showing a **fallback UI**.
- Works for **rendering errors**, **lifecycle methods**, and **constructors** of child components.

---

## 🛠 **When Does an Error Boundary Catch Errors?**

✔️ Catches:

- During rendering
- Inside lifecycle methods
- Inside constructors of child components

❌ Does **NOT** catch:

- Event handlers (you must try/catch manually)
- Asynchronous code (e.g., `setTimeout`, Promises)
- Server-side rendering
- Errors thrown in the error boundary itself

---

## 🏗 **How to Create an Error Boundary**

You must use a **class component** with either `static getDerivedStateFromError()` or `componentDidCatch()`.

```JavaScript
import React from "react";

class ErrorBoundary extends React.Component {
  constructor(props) {
    super(props);
    this.state = { hasError: false };
  }

  static getDerivedStateFromError(error) {
    // Update state so next render shows fallback UI
    return { hasError: true };
  }

  componentDidCatch(error, info) {
    // Log the error to a monitoring service
    console.error("Error caught by boundary:", error, info);
  }

  render() {
    if (this.state.hasError) {
      return <h2>Something went wrong!</h2>;
    }
    return this.props.children;
  }
}

export default ErrorBoundary;
```

---

## 🔗 **How to Use It**

Wrap any component that might fail:

```JavaScript
<ErrorBoundary>
  <MyComponent />
</ErrorBoundary>
```

Or for the whole app:

```JavaScript
<ErrorBoundary>
  <App />
</ErrorBoundary>
```

---

## 🧩 **Key Lifecycle Methods**

|Method|Purpose|
|---|---|
|`static getDerivedStateFromError(error)`|Updates state when an error is caught|
|`componentDidCatch(error, info)`|Logs error details (stack trace, etc.)|

---

## 🎭 **Custom Fallback UI**

You can create a **custom fallback**:

```JavaScript
class ErrorBoundary extends React.Component {
  ...
  render() {
    if (this.state.hasError) {
      return (
        <div>
          <h1>Oops! Something broke.</h1>
          <button onClick={() => window.location.reload()}>Reload</button>
        </div>
      );
    }
    return this.props.children;
  }
}
```

Or make a **reusable fallback component**:

```JavaScript
const FallbackUI = () => <h1>We hit a snag. Try again later.</h1>;

<ErrorBoundary fallback={<FallbackUI />}>
  <RiskyComponent />
</ErrorBoundary>
```

---

## 🧪 **Functional Alternative**

React doesn’t have a hook-based error boundary, but you can use **3rd-party libraries** like:

- `react-error-boundary` (by Kent C. Dodds)

Example:

```JavaScript
import { ErrorBoundary } from "react-error-boundary";

function FallbackComponent({ error, resetErrorBoundary }) {
  return (
    <div>
      <p>Something went wrong: {error.message}</p>
      <button onClick={resetErrorBoundary}>Try again</button>
    </div>
  );
}

<ErrorBoundary
  FallbackComponent={FallbackComponent}
  onError={(error, info) => console.log(error, info)}
>
  <MyComponent />
</ErrorBoundary>
```

---

## ✅ **Best Practices**

- Place **multiple small error boundaries** rather than one big one.
- Use it around **UI sections** (not the whole app) for better UX.
- Log errors to a monitoring service like **Sentry**, **LogRocket**, etc.
- Combine with **lazy loading** & `React.Suspense` for robust error handling.
- Don’t overuse; catch only where needed.

---

## 📝 **Quick Reference**

- ✅ **Class Component Required**
- ✅ **Catches render/lifecycle/constructor errors**
- ❌ **Doesn’t catch event handlers or async errors**
- ✅ **Two main methods:**
    - `getDerivedStateFromError`
    - `componentDidCatch`
- ✅ **Fallback UI can be custom**
- ✅ **3rd-party library for functional components**