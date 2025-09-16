---
Created: 2025-07-09T11:27
---
> According to the comments on the vid, react dropped the proptypes and default

> if you want to use default, just use the JS default

  

### What is PropTypes?

`PropTypes` is a **runtime type-checking** tool for React props. It helps ensure that components receive props of the expected type, making your app more robust.

  

### Setup

First, install the `prop-types` package (if not already):

```Shell
npm install prop-types
```

  

### Basic Usage

```JavaScript
import PropTypes from 'prop-types';

function Greeting({ name, age }) {
  return (
    <div>
      Hello, {name}. You are {age} years old.
    </div>
  );
}

Greeting.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number,
};
```

- `isRequired` means the prop **must** be provided.
- Without `isRequired`, the prop is optional.

  

### Common PropTypes Validators

|Validator|Description|Example|
|---|---|---|
|`PropTypes.string`|String prop|`name: PropTypes.string`|
|`PropTypes.number`|Number prop|`age: PropTypes.number`|
|`PropTypes.bool`|Boolean prop|`isOnline: PropTypes.bool`|
|`PropTypes.array`|Array prop|`items: PropTypes.array`|
|`PropTypes.object`|Object prop|`settings: PropTypes.object`|
|`PropTypes.func`|Function prop|`onClick: PropTypes.func`|
|`PropTypes.node`|Anything React can render|`children: PropTypes.node`|
|`PropTypes.element`|React element|`icon: PropTypes.element`|

  

### Complex Types

**Array of a specific type:**

```JavaScript
items: PropTypes.arrayOf(PropTypes.string)
```

**Object with specific shape:**

```JavaScript
user: PropTypes.shape({
  name: PropTypes.string.isRequired,
  age: PropTypes.number,
})
```

**One of a set of values:**

```JavaScript
status: PropTypes.oneOf(['loading', 'success', 'error'])
```

  

### Default Props

Use `defaultProps` to specify default values if a prop is not passed:

```JavaScript
Greeting.defaultProps = {
  age: 25,
};
```

  

### Example Putting It All Together

```JavaScript
import PropTypes from 'prop-types';

function UserProfile({ name, age, isOnline, hobbies }) {
  return (
    <div>
      <h2>{name}</h2>
      <p>Age: {age}</p>
      <p>Status: {isOnline ? 'Online' : 'Offline'}</p>
      <ul>
        {hobbies.map((hobby, i) => (
          <li key={i}>{hobby}</li>
        ))}
      </ul>
    </div>
  );
}

UserProfile.propTypes = {
  name: PropTypes.string.isRequired,
  age: PropTypes.number,
  isOnline: PropTypes.bool,
  hobbies: PropTypes.arrayOf(PropTypes.string),
};

UserProfile.defaultProps = {
  age: 18,
  isOnline: false,
  hobbies: [],
};
```

  

### Summary Table

|PropType Validator|Use Case|
|---|---|
|`string`, `number`, `bool`|Basic types|
|`func`|Functions (event handlers)|
|`arrayOf(type)`|Arrays with specific item types|
|`shape({...})`|Object with specific keys|
|`oneOf([...])`|Enum-like values|
|`node`|Anything React can render|

  

---

  

  

### What are Default Props?

**Default props** let you specify default values for props **when the parent does not provide them**. This ensures your component always has valid data to work with.

  

### Default Props in Functional Components

**With default function parameters (modern and recommended):**

```JavaScript
function Greeting({ name = "Guest" }) {
  return <h1>Hello, {name}!</h1>;
}
```

  

### Default Props with `defaultProps` (Legacy way)

```JavaScript
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}

Greeting.defaultProps = {
  name: "Guest",
};
```

  

### Default Props with Class Components

```JavaScript
class Greeting extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}

Greeting.defaultProps = {
  name: "Guest",
};
```

  

### Why Use Default Props?

- Prevents `undefined` props inside the component
- Makes components more robust and easier to use
- Avoids runtime errors from missing props

  

### Note About Default Props and `undefined`

Default props only work if the prop is `**undefined**` or **missing**. If the parent passes `null`, default props **do not** apply.

```JavaScript
<Greeting name={null} />  // name will be null, not defaulted
```

  

### Summary Table

|Method|Works For|Syntax Example|
|---|---|---|
|Default parameter value|Functional components|`function Comp({ prop = val }) {}`|
|`defaultProps` property|Functional & Class comps|`Comp.defaultProps = { prop: val }`|