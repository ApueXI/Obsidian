---
Created: 2025-07-10T13:37
---
## Updating Objects in `useState`

### 🧠 Why be careful?

React state is **immutable**, meaning you should **not mutate** the object directly.

Always create a **new copy** of the object and update that.

  

## Basic Object State Example

```JavaScript
const [user, setUser] = useState({
  name: 'Nein',
  age: 18,
});
```

  

## Updating One Field

```JavaScript
setUser(prev => ({
  ...prev,
  age: prev.age + 1,
}));
```

✅ This creates a **new object** using the spread operator (`...prev`)

✅ Only updates the field you specify (e.g., `age`)

❌ Don’t mutate directly: `user.age = 19` is **wrong**

  

## Updating Nested Objects

```JavaScript
const [profile, setProfile] = useState({
  name: 'Nein',
  address: {
    city: 'Manila',
    zip: '1000',
  },
});

// Update `city` only
setProfile(prev => ({
  ...prev,
  address: {
    ...prev.address,
    city: 'Quezon City',
  },
}));
```

✅ Always spread **each level** to keep other values intact

  

## With Input `onChange`

```JavaScript
function handleChange(e) {
  const { name, value } = e.target;

  setUser(prev => ({
    ...prev,
    [name]: value,
  }));
}

// <input name="name" onChange={handleChange} />
// <input name="age" onChange={handleChange} />
```

✅ This makes the handler **dynamic** for any field

  

## Summary Table

|Task|Code Example|
|---|---|
|Update one field|`setX(prev => ({ ...prev, field: newVal }))`|
|Update nested field|`setX(prev => ({ ...prev, nested: { ...prev.nested, key: val } }))`|
|Dynamic key from input|`setX(prev => ({ ...prev, [name]: value }))`|

## Don't Do This

```JavaScript
user.name = "New Name";     // ❌ Mutates directly
setUser(user);              // ❌ Still same object reference
```

> 🛑 This won’t trigger a re-render!