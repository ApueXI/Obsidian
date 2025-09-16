---
Created: 2025-07-15T12:13
---
## What is `useParams()`?

`useParams()` is a React Router hook that returns an **object of URL parameters** from the current route.

✅ Useful for **dynamic routes** like:

```Ruby
/users/:id
/posts/:postId/comments/:commentId
```

---

## ✅ 1. Basic Usage

### Route Definition

```JavaScript
<Route path="/user/:id" element={<User />} />
```

### Inside `User.jsx`

```JavaScript
import { useParams } from "react-router-dom";

function User() {
  const { id } = useParams();
  return <h1>User ID: {id}</h1>;
}
```

**URL:** `/user/123` → `id = "123"` ✅

---

## 🧩 2. Multiple Parameters

### Route

```JavaScript
<Route path="/post/:postId/comment/:commentId" element={<Comment />} />
```

### Inside `Comment.jsx`

```JavaScript
const { postId, commentId } = useParams();
console.log(postId, commentId);
```

**URL:** `/post/42/comment/7`

✅ `postId = "42"`, `commentId = "7"`

---

## 🧭 3. Combine with `fetch` (Load Data)

```JavaScript
function UserProfile() {
  const { id } = useParams();

  useEffect(() => {
    fetch(`/api/users/${id}`)
      .then(res => res.json())
      .then(data => console.log(data));
  }, [id]);

  return <p>Loading user {id}...</p>;
}
```

✅ Dynamic API calls based on route param

---

## 🔄 4. Nested Routes

```JavaScript
<Route path="/dashboard/*" element={<Dashboard />}>
  <Route path="settings/:tab" element={<Settings />} />
</Route>
```

```JavaScript
function Settings() {
  const { tab } = useParams();
  return <p>Currently on {tab} tab</p>;
}
```

✅ Supports nested dynamic params

---

## 📚 Summary Table

|What You Want|Example Route Path|Example useParams Output|
|---|---|---|
|Single param|`/user/:id`|`{ id: "123" }`|
|Multiple params|`/post/:pid/comment/:cid`|`{ pid: "42", cid: "7" }`|
|Optional param (v6.4+)|`/search/:query?`|`{ query: undefined }` if missing|

---

## ⚠️ Common Mistakes

|Mistake|Fix|
|---|---|
|Trying `useParams()` outside Router|✅ Must be inside `<BrowserRouter>`|
|Forgetting param names must match|✅ Use same names as in route|
|Expecting numbers automatically|✅ Params are always **strings**|

---

## ✅ Combine with Others

- `useParams()` → Get dynamic route ID
- `useLocation()` → Get query strings
- `useNavigate()` → Redirect after fetching data