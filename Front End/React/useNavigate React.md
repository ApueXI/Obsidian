---
Created: 2025-07-15T12:15
---
## What is `useNavigate()`?

`useNavigate()` is a hook from **react-router-dom** that lets you **navigate to a different route using JavaScript**, instead of `<Link>`.

✅ Useful for:

- Redirecting after a form submit
- Conditional navigation (auth checks)
- Going **back/forward** in history

---

## ✅ 1. Basic Usage

```JavaScript
import { useNavigate } from "react-router-dom";

function HomeButton() {
  const navigate = useNavigate();

  return (
    <button onClick={() => navigate("/")}>
      Go Home
    </button>
  );
}
```

✅ Works like clicking a `<Link to="/">`

---

## 🧭 2. Navigate Back / Forward

```JavaScript
navigate(-1); // Go back 1 step
navigate(1);  // Go forward 1 step
```

✅ Similar to browser back/forward buttons

---

## 🔄 3. Replace Instead of Push

```JavaScript
navigate("/login", { replace: true });
```

✅ Replaces the current history entry (won’t add a new one)

---

## 📦 4. Pass State with Navigation

```JavaScript
navigate("/profile", { state: { from: "dashboard" } });
```

You can read it in the target page with `useLocation()`:

```JavaScript
const location = useLocation();
console.log(location.state?.from); // "dashboard"
```

---

## 🧩 5. Conditional Redirect Example

```JavaScript
function ProtectedPage() {
  const navigate = useNavigate();
  const isLoggedIn = false;

  useEffect(() => {
    if (!isLoggedIn) {
      navigate("/login");
    }
  }, [isLoggedIn, navigate]);

  return <div>Protected Content</div>;
}
```

✅ Auto-redirect if not logged in

---

## 📚 Summary Table

|Action|Code Example|
|---|---|
|Go to route|`navigate("/about")`|
|Go back|`navigate(-1)`|
|Go forward|`navigate(1)`|
|Replace history|`navigate("/home", { replace: true })`|
|Pass extra state|`navigate("/page", { state: { foo: "bar" }})`|

---

## ⚠️ Common Mistakes

|Mistake|Fix|
|---|---|
|Calling `useNavigate()` outside Router|✅ Must be inside `<BrowserRouter>`|
|Forgetting `{ replace: true }` when needed|✅ Add option if you don’t want history stack|
|Expecting query params automatically parsed|✅ Use `useSearchParams` or `URLSearchParams`|