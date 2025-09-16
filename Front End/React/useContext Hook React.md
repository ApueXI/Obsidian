---
Created: 2025-07-11T17:01
tags:
  - Hooks
---
### Component A

```JavaScript
import ComponentB from "./ComponentB";
import React, { useState, createContext } from "react";

export const UserContext = createContext();

function ComponentA() {
  const [user, setUser] = useState("Bro Code");

  return (
    <div className="box">
      <h1>Component A</h1>
      <h2>{`Hello ${user}`}</h2>
      <UserContext.Provider value={user}>
        <ComponentB />
      </UserContext.Provider>
    </div>
  );
}

export default ComponentA;
```

### Component B

```JavaScript
import ComponentC from "./ComponentC";
import React, { useContext } from "react";
import { UserContext } from "./ComponentA";

function ComponentB() {
  const user = useContext(UserContext);

  return (
    <div className="box">
      <h1>Component B</h1>
      <h2>{`Hello Again ${user}`}</h2>
      <ComponentC />
    </div>
  );
}

export default ComponentB;
```

  

  

### Component C

```JavaScript
import ComponentD from "./ComponentD";
import React, { useContext } from "react";
import { UserContext } from "./ComponentA";

function ComponentC() {
  const user = useContext(UserContext);

  return (
    <div className="box">
      <h1>Component C</h1>
      <h2>{`Hello from B ${user}`}</h2>
      <ComponentD />
    </div>
  );
}

export default ComponentC;
```

### Component D

```JavaScript
import React, { useContext } from "react";
import { UserContext } from "./ComponentA";

function ComponentD() {

    const user = useContext(UserContext)

  return (
    <div className="box">
      <h1>Component D</h1>
      <h2>{`Bye ${user}`}</h2>
    </div>
  );
}

export default ComponentD;
```