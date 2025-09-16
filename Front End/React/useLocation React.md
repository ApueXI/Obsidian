---
Created: 2025-07-15T12:13
---
## What is `useLocation()`?

`useLocation()` is a **React Router hook** that returns the current **location object**, which contains info about the URL.

✅ Useful for:

- Getting current **pathname**
- Reading **query strings / search params**
- Knowing when the route has changed

---

## ✅ 1. Basic Usage

```JavaScript
import { useLocation } from "react-router-dom";

function CurrentPage() {
  const location = useLocation();

  return (
    <><p>Pathname: {location.pathname}</p>
      <p>Search Query: {location.search}</p>
      <p>Hash: {location.hash}</p>
      <p>Key: {location.key}</p>
    </>
  );
}
```

---

## 📦 2. Location Object Properties

|Property|Example Value|Description|
|---|---|---|
|`pathname`|`/about`|Current URL path|
|`search`|`?sort=price`|Query string including `?`|
|`hash`|`#section1`|Hash fragment in the URL|
|`state`|`{ from: "/home" }`|Extra state passed during nav|
|`key`|`"default"`|Unique key for location change|

---

## 🧭 3. Detect Route Changes

```JavaScript
const location = useLocation();

useEffect(() => {
  console.log("Route changed to:", location.pathname);
}, [location]);
```

✅ Runs effect whenever the URL changes

---

## 🧩 4. Reading Query Params

```JavaScript
import { useLocation } from "react-router-dom";

function Products() {
  const { search } = useLocation();
  const params = new URLSearchParams(search);
  const sort = params.get("sort"); // e.g. ?sort=price

  return <p>Sorting by: {sort}</p>;
}
```

✅ Combine with `URLSearchParams` for easy query parsing

---

## 🔄 5. With `navigate()` + State

When you navigate with state:

```JavaScript
navigate("/profile", { state: { from: "login" } });
```

You can read it via `useLocation()`:

```JavaScript
const location = useLocation();
console.log(location.state?.from); // "login"
```

---

## 📚 Summary Table

|Hook|Purpose|
|---|---|
|`useLocation()`|Get URL info (`pathname`, `search`)|
|`useParams()`|Get route params (`:id`)|
|`useNavigate()`|Programmatic navigation|
|`useSearchParams()`|Easier query param handling|

---

## ⚠️ Common Mistakes

|Mistake|Fix|
|---|---|
|Trying `useLocation()` outside Router|✅ Must be inside `<BrowserRouter>`|
|Mutating `location` directly|❌ It’s read-only|
|Forgetting to parse `search`|✅ Use `URLSearchParams`|