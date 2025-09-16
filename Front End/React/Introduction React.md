---
Created: 2025-07-08T09:01
---
you need Node to use npm

  

```Bash
npm create vite@latest

cd my_React_App
npm install
npm run dev
```

ctrl+c to exit npm run

  

## React Introduction Cheat Sheet

### 📦 1. Installation & Setup

**Using Create React App (CRA):**

```Shell
npx create-react-app my-app
cd my-app
npm start
```

**Using Vite (faster, modern):**

```Shell
npm create vite@latest my-app -- --template react
cd my-app
npm install
npm run dev
```

  

### Core Concepts

|Concept|Description|
|---|---|
|JSX|JavaScript + XML syntax to define UI (`<h1>Hello</h1>`)|
|Components|Reusable UI pieces; can be function or class-based|
|Props|Inputs to components (readonly)|
|State|Local data managed in the component|
|Hooks|Special functions like `useState`, `useEffect`, etc.|
|Virtual DOM|A fast in-memory DOM used for efficient UI updates|

  

### Basic React Component

```JavaScript
function Welcome(props) {
  return <h1>Hello, {props.name}</h1>;
}

// Usage
<Welcome name="Nein" />
```

  

### Common Hooks

|Hook|Purpose|
|---|---|
|`useState`|Add state to functional components|
|`useEffect`|Side effects (like fetching data, timers)|
|`useRef`|Persist values without re-render|
|`useContext`|Access global context values|

```JavaScript
// useState Example
const [count, setCount] = useState(0);
```

```JavaScript
// useEffect Example
useEffect(() => {
  console.log("Component mounted or updated");
}, [count]); // Dependency array
```

  

### Props vs State

|Feature|Props|State|
|---|---|---|
|Data|Passed from parent|Local to the component|
|Mutable|❌ No|✅ Yes|
|Purpose|Configure component|Track changes/render|

  

### Event Handling

```JavaScript
function Clicker() {
  const handleClick = () => alert("Clicked!");
  return <button onClick={handleClick}>Click me</button>;
}
```

  

### Conditional Rendering

```JavaScript
{isLoggedIn ? <LogoutButton /> : <LoginButton />}
```

  

### Lists and Keys

```JavaScript
const items = ['Apple', 'Banana'];
items.map((item, index) => <li key={index}>{item}</li>);
```

  

### Component File Structure (Best Practice)

```CSS
src/
├── components/
│   └── Header.jsx
├── App.jsx
└── main.jsx (Vite) / index.js (CRA)
```

  

### Fetching Data (with `useEffect`)

```JavaScript
useEffect(() => {
  fetch('https://api.example.com/data')
    .then(res => res.json())
    .then(data => setData(data));
}, []);
```

  

### React Developer Tools

Install the React Developer Tools Chrome extension for debugging:

==[https://legacy.reactjs.org/blog/2019/08/15/new-react-devtools.html](https://legacy.reactjs.org/blog/2019/08/15/new-react-devtools.html)==

  

### Main.jsx

```JavaScript
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App.jsx'

createRoot(document.getElementById('root')).render(
  <StrictMode>
    <App />
  </StrictMode>,
)
```

  

### App.jsx

```JavaScript
import Header from "./Header.jsx";
import Footer from "./Footer.jsx";
import Food from "./Food.jsx";

function App() {
  return (
    <>
      <Header></Header>
      <Food />
      <Footer />
    </>
  );
}

export default App;
```

  

### Header.jsx

```JavaScript
function Header() {
  return (
    <header>
      <h1>My Website</h1>
      <nav>
        <ul>
          <li>
            <a href="">Home</a>
          </li>
          <li>
            <a href="">About</a>
          </li>
          <li>
            <a href="">Services</a>
          </li>
          <li>
            <a href="">Contact</a>
          </li>
        </ul>
      </nav>
      <hr />
    </header>
  );
}

export default Header;
```

  

### Food.jsx

```JavaScript
function Food() {
  const food1 = "Orange";
  const food2 = "Banana";

  return (
    <ul>
      <li>Apple</li>
      <li> {food1} </li>
      <li> {food2.toUpperCase()} </li>
    </ul>
  );
}

export default Food;
```

  

### Footer.jsx

```JavaScript
function Footer(param) {
  return (
    <footer>
      <p>&copy; {new Date().getFullYear()} My Website</p>
    </footer>
  );
}

export default Footer;
```