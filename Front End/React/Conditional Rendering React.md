---
Created: 2025-07-09T12:37
---
### What is Conditional Rendering?

Conditional rendering lets you **show different JSX or nothing at all** depending on some **state, props, or logic**.

  

### `if` Statement (Classic)

```JavaScript
if (isLoggedIn) {
  return <h1>Welcome back!</h1>;
}
return <h1>Please sign in.</h1>;
```

✅ Use when rendering **completely different UI blocks**.

  

### Ternary Operator (Inline Conditions)

```JavaScript
<h1>{isLoggedIn ? "Welcome back!" : "Please sign in."}</h1>
```

✅ Best for **simple conditional text or components**.

  

  

### `&&` (Short-Circuit Rendering)

```JavaScript
{isAdmin && <button>Delete User</button>}
```

✅ Renders the element **only if the condition is true**.

  

### Prevent Rendering (`null`)

```JavaScript
if (!isVisible) {
  return null;
}
return <div>Now you see me!</div>;
```

✅ Use `null` when you want to **render nothing**.

  

### Conditional Class or Style

```JavaScript
<div className={isActive ? "active" : "inactive"}>Tab</div>
```

Or:

```JavaScript
<div style={{ display: isVisible ? "block" : "none" }}>Panel</div>
```

✅ Dynamically change **appearance** without hiding logic.

  

### Rendering Different Components

```JavaScript
function UserPanel({ isAdmin }) {
  return isAdmin ? <AdminDashboard /> : <UserDashboard />;
}
```

✅ Great for **role-based UI** or **feature toggles**.

  

### Tips

|Pattern|Use When...|
|---|---|
|`if...else`|Logic is complex or multiline|
|Ternary (`? :`)|Quick inline conditional output|
|`&&`|One-sided conditional display|
|`null`|You want to skip rendering|

  

### Full Example

```JavaScript
function Dashboard({ isLoggedIn, isAdmin }) {
  if (!isLoggedIn) {
    return <LoginForm />;
  }

  return (
    <div>
      <h1>Welcome!</h1>
      {isAdmin && <button>Admin Tools</button>}
    </div>
  );
}
```

  

---

  

```JavaScript
import UserGreeting from "./UserGreeing";

function App() {
  return (
    <>
      <UserGreeting isLoggedIn={false} />
      <UserGreeting isLoggedIn={true} username="BroCode" />
    </>
  );
}

export default App;
```

```JavaScript
function UserGreeting(props) {
  return props.isLoggedIn ? (
    <h2 className="welcome-message">Welcome {props.username}</h2>
  ) : (
    <h2 className="login-prompt">Please Log In/Sign In</h2>
  );
}
export default UserGreeting;
```

  

```JavaScript
import UserGreeting from "./UserGreeing";

function App() {
  return (
    <>
      <UserGreeting isLoggedIn={false} />
      <UserGreeting isLoggedIn={true} username="Bro Code" />
    </>
  );
}

export default App;
```

```JavaScript
import PropTypes from "prop-types";

function UserGreeting({ username = "Guest", isLoggedIn = false }) {
  const welcomeMessage = (
    <h2 className="welcome-message">Welcome {username}</h2>
  );

  const logInPrompt = <h2 className="login-prompt">Please Log In/Sign In</h2>;

  return isLoggedIn ? welcomeMessage : logInPrompt;
}

UserGreeting.propTypes = {
  isLoggedIn: PropTypes.bool,
  username: PropTypes.string,
};

export default UserGreeting;
```