---
Created: 2025-07-09T13:16
---
### What is a Rendered List?

A **rendered list** in React is when you **display multiple elements** by looping over an array (usually using `.map()`).

  

### Basic List Rendering

```JavaScript
const fruits = ["Apple", "Banana", "Cherry"];

function FruitList() {
  return (
    <ul>
      {fruits.map((fruit, index) => (
        <li key={index}>{fruit}</li>
      ))}
    </ul>
  );
}
```

> 🔑 Always include a key prop when rendering lists.

  

### Rendering List of Objects

```JavaScript
const users = [
  { id: 1, name: "Alice" },
  { id: 2, name: "Bob" }
];

function UserList() {
  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
```

✅ **Use a unique and stable key**, preferably `id`.

  

### Render List in a Component

```JavaScript
function UserCard({ user }) {
  return <div>{user.name}</div>;
}

function UserList({ users }) {
  return (
    <div>
      {users.map(user => (
        <UserCard key={user.id} user={user} />
      ))}
    </div>
  );
}
```

✅ Reuse components to keep code clean.

  

### Avoid Index as Key (when possible)

```JavaScript
// ❌ Not recommended if the list can change
items.map((item, index) => <li key={index}>{item}</li>);
```

Use `index` **only when**:

- The list is static
- Items don't have unique IDs
- Performance or reordering isn't critical

  

### Conditional Rendering Inside a List

```JavaScript
tasks.map(task =>
  task.done ? <li key={task.id}>{task.title}</li> : null
)
```

Or:

```JavaScript
tasks
  .filter(task => task.done)
  .map(task => <li key={task.id}>{task.title}</li>);
```

✅ Filter, map, or conditionally render as needed.

  

### Nested Lists

```JavaScript
const categories = [
  {
    name: "Fruits",
    items: ["Apple", "Banana"]
  },
  {
    name: "Vegetables",
    items: ["Carrot", "Lettuce"]
  }
];

function CategoryList() {
  return (
    <div>
      {categories.map(cat => (
        <div key={cat.name}>
          <h3>{cat.name}</h3>
          <ul>
            {cat.items.map((item, index) => (
              <li key={index}>{item}</li>
            ))}
          </ul>
        </div>
      ))}
    </div>
  );
}
```

  

### Summary Table

|Feature|Pattern|
|---|---|
|Array of strings|`array.map((item, i) => <li key={i}>{item}</li>)`|
|Array of objects|`array.map(obj => <Component key={obj.id} ... />)`|
|Conditional rendering|`.filter()` or inline ternary|
|Nested lists|`.map()` inside `.map()`|
|Key best practice|Always use a stable and unique value (like `id`)|

  

```JavaScript
function List() {
  const fruits = ["orange", "banana", "coconut", "pineapple"];

  fruits.sort()

  const listItems = fruits.map((fruit) => <li>{fruit}</li>);

  return <ol>{listItems}</ol>;
}

export default List;
```

  

```JavaScript
function List() {
  const fruits = [
    { id: 1, name: "orange", calories: 45 },
    { id: 2, name: "banana", calories: 105 },
    { id: 3, name: "apple", calories: 95 },
    { id: 4, name: "coconut", calories: 159 },
    { id: 5, name: "pineapple", calories: 37 },
    { id: 6, name: "potato", calories: 120 },
  ];

  //   sort alphabetically
  //   fruits.sort((a, b) => a.name.localeCompare(b.name));
  //   if want reverse, just swap a and b

  //   fruits.sort((a, b) => a.calories - b.calories);

  const lowCalFruits = fruits.filter((fruit) => fruit.calories < 100);

  const highCal = fruits.filter((fruit) => fruit.calories >= 100);

  const listItems = fruits.map((fruit) => (
    <li key={fruit.id}>
      {fruit.name}: &nbsp; <b>{fruit.calories}</b>
    </li>
  ));

  return <ol>{listItems}</ol>;
}

export default List;
```

  

```JavaScript
import List from "./List";

function App() {
  const fruits = [
    { id: 1, name: "orange", calories: 45 },
    { id: 2, name: "banana", calories: 105 },
    { id: 3, name: "apple", calories: 95 },
    { id: 4, name: "coconut", calories: 159 },
    { id: 5, name: "pineapple", calories: 37 },
    { id: 6, name: "lemon", calories: 120 },
  ];

  const vegetables = [
    { id: 7, name: "potatoes", calories: 10 },
    { id: 8, name: "celery", calories: 15 },
    { id: 9, name: "carrots", calories: 25 },
    { id: 10, name: "corn", calories: 63 },
    { id: 11, name: "brocolli", calories: 50 },
    { id: 12, name: "tomato", calories: 13 },
  ];

  return (
    <>
      {fruits.length > 0 && <List items={fruits} category="Fruits"></List>}

      {vegetables.length > 0 ? (
        <List items={vegetables} category="Vegetables"></List>
      ) : null}
    </>
  );
}

export default App;
```

  

  

```JavaScript
import List from "./List";

function App() {
  const fruits = [
    { id: 1, name: "orange", calories: 45 },
    { id: 2, name: "banana", calories: 105 },
    { id: 3, name: "apple", calories: 95 },
    { id: 4, name: "coconut", calories: 159 },
    { id: 5, name: "pineapple", calories: 37 },
    { id: 6, name: "lemon", calories: 120 },
  ];

  const vegetables = [
    { id: 7, name: "potatoes", calories: 10 },
    { id: 8, name: "celery", calories: 15 },
    { id: 9, name: "carrots", calories: 25 },
    { id: 10, name: "corn", calories: 63 },
    { id: 11, name: "brocolli", calories: 50 },
    { id: 12, name: "tomato", calories: 13 },
  ];

  return (
    <>
      {fruits.length > 0 && <List items={fruits} category="Fruits"></List>}

      {vegetables.length > 0 ? (
        <List items={vegetables} category="Vegetables"></List>
      ) : null}
    </>
  );
}

export default App;
```

```JavaScript
import PropTypes from "prop-types";

function List({ category = "Category", items = [] }) {
  const itemList = items;
  const Category = category;

  const listItems = itemList.map((item) => (
    <li key={item.id}>
      {item.name}: &nbsp; <b>{item.calories}</b>
    </li>
  ));

  return (
    <>
      <h3 className="list-category">{Category}</h3>
      <ol className="list-items">{listItems}</ol>
    </>
  );
}

List.propTypes = {
  category: PropTypes.string.isRequired,
  items: PropTypes.arrayOf(
    PropTypes.shape({
      id: PropTypes.number.isRequired,
      name: PropTypes.string.isRequired,
      calories: PropTypes.number.isRequired,
    })
  ).isRequired,
};

export default List;
```