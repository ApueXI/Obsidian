---
Created: 2025-07-12T16:55
---
## What is `react-router-dom`?

`react-router-dom` is the routing library for React web apps. It lets you:

- Navigate between pages/components
- Use URLs to reflect app state
- Create dynamic and nested routes

  

## Install It

```Shell
npm install react-router-dom
```

  

## Setup Basic Router

```JavaScript
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import Home from './Home';
import About from './About';

function App() {
  return (
    <BrowserRouter>
      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

✅ `BrowserRouter` = wraps the app

✅ `Routes` = holds all `<Route>` components

✅ `Route` = defines a path and the component to render

  

## Navigation Links

```JavaScript
import { Link } from 'react-router-dom';

<Link to="/">Home</Link>
<Link to="/about">About</Link>
```

✅ No full-page reloads

✅ Works like SPA navigation

  

## Programmatic Navigation

```JavaScript
import { useNavigate } from 'react-router-dom';

const navigate = useNavigate();
navigate('/about');
```

✅ Use this inside a `useEffect`, button click, etc.

  

## URL Parameters

### Route:

```JavaScript
<Route path="/user/:id" element={<User />} />
```

### Inside `User.jsx`:

```JavaScript
import { useParams } from 'react-router-dom';

const { id } = useParams();
```

✅ `id` comes from the URL like `/user/123`

  

## Query Strings

```JavaScript
import { useSearchParams } from 'react-router-dom';

const [searchParams] = useSearchParams();
const sort = searchParams.get('sort');
```

Example URL: `/products?sort=price`

  

## Nested Routes

```JavaScript
<Route path="/dashboard" element={<Dashboard />}>
  <Route path="settings" element={<Settings />} />
</Route>
```

Inside `Dashboard`, render nested route with:

```JavaScript
<Outlet />
```

✅ Displays child routes inside the parent layout

  

## Navigate Back/Forward

```JavaScript
const navigate = useNavigate();

navigate(-1); // back
navigate(1);  // forward
```

  

## 404 Not Found Route

```JavaScript
<Route path="*" element={<NotFound />} />
```

✅ Catches all unmatched routes

  

## Summary Table

|Feature|Function / Component|
|---|---|
|Routing setup|`BrowserRouter` + `Routes`|
|Navigate with UI|`<Link to="..." />`|
|Navigate with JS|`useNavigate()`|
|URL parameters|`useParams()`|
|Query strings|`useSearchParams()`|
|Nested route rendering|`<Outlet />`|
|Wildcard/404|`path="*"`|

  

## Common Mistakes

|Mistake|Fix|
|---|---|
|Using `component=` in `<Route>`|✅ Use `element={<Comp />}` in v6+|
|Forgetting `<Routes>` wrapper|All routes must be inside `<Routes>`|
|Not using `<Outlet />` in nested|Required for child routes to render|