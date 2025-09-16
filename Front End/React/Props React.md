---
Created: 2025-07-08T20:43
---
### What are Props?

> Props (short for "properties") are read-only inputs passed from a parent component to a child component to customize its behavior or appearance.

  

### Passing and Using Props

**Parent → Child**

```JavaScript
function Greeting(props) {
  return <h1>Hello, {props.name}!</h1>;
}

// Usage in parent
<Greeting name="Nein" />
```

🧠 `props.name` gives you the value `"Nein"` inside `Greeting`.

  

### Destructuring Props

Instead of:

```JavaScript
function Card(props) {
  return <div>{props.title}</div>;
}
```

Use:

```JavaScript
function Card({ title }) {
  return <div>{title}</div>;
}
```

✅ Cleaner and easier to read.

  

### Multiple Props

```JavaScript
function Profile({ name, age, isOnline }) {
  return (
    <div>
      <h3>{name}</h3>
      <p>Age: {age}</p>
      <p>Status: {isOnline ? 'Online' : 'Offline'}</p>
    </div>
  );
}

// Usage
<Profile name="Alex" age={30} isOnline={true} />
```

  

### Passing Functions as Props

```JavaScript
function Button({ onClick }) {
  return <button onClick={onClick}>Click me</button>;
}

function App() {
  const handleClick = () => alert("Button clicked!");
  return <Button onClick={handleClick} />;
}
```

✅ Functions are passed as props for interactivity or callback logic.

  

### Props with Children (Special Prop)

```JavaScript
function Wrapper({ children }) {
  return <div className="box">{children}</div>;
}

// Usage
<Wrapper>
  <h1>Hello inside a Wrapper</h1>
</Wrapper>
```

🧠 `children` refers to the content placed **between** the component's tags.

  

### Props Are Read-Only

```JavaScript
function Card({ title }) {
  title = "Hacked"; // 🚫 BAD! Props are immutable
  return <div>{title}</div>;
}
```

Use **state** if you need mutability, not props.

  

### Default Props (Manual)

```JavaScript
function Avatar({ name = "Guest" }) {
  return <div>Welcome, {name}</div>;
}
```

✅ Sets fallback if no prop is provided.

  

### Summary Table

|Feature|Description|
|---|---|
|`props`|Object passed to components|
|Destructuring|Clean way to extract prop values|
|`children`|Special prop for nested content|
|Read-only|Cannot modify props inside component|
|Functions|Used for event handlers/callbacks|

  

### Basic

```JavaScript
import Student from "./Students";

function App() {
  return (
    <>
      <Student name="Acob" age={15} isStudent={true} />
      <Student name="Andy" age={21} isStudent={false} />
      <Student name="Goco" age={25} isStudent={true} />
      <Student name="Zam" age={31} isStudent={false} />
    </>
  );
}

export default App;
```

```JavaScript
function Student(props) {
  return (

    <div className="student">
      <p>Name: {props.name}</p>
      <p>Age: {props.age}</p>
      <p>Student: {props.isStudent ? "Yes" : "No"}</p>
    </div>
  );
}
export default Student;
```

```CSS
.student {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 2em;
  padding: 10px;
  border: 1px solid hsl(0, 0%, 50%);
  margin: 20px 50px;
}
.student p {
  margin: 0;
}
```

  

### PropTypes (Does not work)

```JavaScript
import PropTypes from "prop-types";

function Student(props) {
  return (
    <div className="student">
      <p>Name: {props.name}</p>
      <p>Age: {props.age}</p>
      <p>Student: {props.isStudent ? "Yes" : "No"}</p>
    </div>
  );
}

Student.proptypes = {
  name: PropTypes.string,
  age: PropTypes.number,
  isStudent: PropTypes.bool,
};
export default Student;
```

  

### Default Props

```JavaScript
function Student({ name = "Guest", age = 0, isStudent = false }) {
  return (
    <div className="student">
      <p>Name: {name}</p>
      <p>Age: {age}</p>
      <p>Student: {isStudent ? "Yes" : "No"}</p>
    </div>
  );
}

export default Student;
```

  

  

```JavaScript
function Student({ name = "Guest", age = 0, isStudent = false }) {
  return (
    <div className="student">
      <p>Name: {name}</p>
      <p>Age: {age}</p>
      <p>Student: {isStudent ? "Yes" : "No"}</p>
    </div>
  );
}

export default Student;
```

```CSS
.student {
  font-family: Arial, Helvetica, sans-serif;
  font-size: 2em;
  padding: 10px;
  border: 1px solid hsl(0, 0%, 50%);
  margin: 20px 50px;
}
.student p {
  margin: 0;
}
```

```CSS
import Student from "./Students.jsx";

function App() {
  return (
    <>
      <Student name="Acob" age={15} isStudent={true} />
      <Student name="Andy" age={21} isStudent={false} />
      <Student name="Zam" age={31} isStudent={false} />
      <Student name="Goco" age={25} isStudent={true} />
      <Student></Student>
    </>
  );
}

export default App;
```