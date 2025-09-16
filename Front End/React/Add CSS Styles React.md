---
Created: 2025-07-08T12:21
---
### **Regular CSS File (Vanilla CSS)**

**📁 File Structure**

```Bash
/src
├── App.jsx
└── App.css
```

**🔹 App.css**

```CSS
.card {
  background-color: white;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 6px rgba(0,0,0,0.1);
}
```

**🔹 App.jsx**

```JavaScript
import './App.css';

function App() {
  return <div className="card">Hello CSS</div>;
}
```

✅ _Best for beginners and small projects_

  

### **CSS Modules (Scoped Styles)**

**📁 File Structure**

```Plain
/src
├── Card.module.css
└── Card.jsx
```

**🔹 Card.module.css**

```CSS
.card {
  background-color: \#f0f0f0;
  padding: 16px;
  border-radius: 12px;
}
```

**🔹 Card.jsx**

```JavaScript
import styles from './Card.module.css';

function Card() {
  return <div className={styles.card}>I'm a scoped card!</div>;
}
```

✅ _Avoids global style conflicts_

⚠️ _Class names must be imported_

  

### **Styled Components (CSS-in-JS)**

Install:

```Shell
npm install styled-components
```

**🔹 Card.jsx**

```JavaScript
import styled from 'styled-components';

const Card = styled.div`
  background: \#fff;
  padding: 24px;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
`;

function App() {
  return <Card>This is styled!</Card>;
}
```

✅ _Powerful, scoped, dynamic styling_

⚠️ _Adds runtime dependency_

  

### **Inline Styles**

```JavaScript
function Card() {
  const cardStyle = {
    backgroundColor: '\#fff',
    padding: '20px',
    borderRadius: '10px',
  };

  return <div style={cardStyle}>Inline style card</div>;
}
```

✅ _Good for quick, dynamic styles_

⚠️ _No pseudo-classes (`:hover`) or media queries_

  

### **Tailwind CSS (Utility-first)**

Install:

```Shell
bash
CopyEdit
npm install -D tailwindcss
npx tailwindcss init

```

Then configure `tailwind.config.js` and import Tailwind in `index.css`.

**🔹 Card.jsx**

```JavaScript
function Card() {
  return (
    <div className="bg-white p-4 rounded-xl shadow-md">
      Tailwind Styled Card
    </div>
  );
}
```

✅ _Super fast, consistent UI_

⚠️ _Learning curve for class names_

  

### Summary Table

|Method|Scoped|Dynamic|Easy Setup|Notes|
|---|---|---|---|---|
|CSS File|❌|❌|✅|Use for global or simple styling|
|CSS Modules|✅|❌|✅|Best for component-based projects|
|Styled Components|✅|✅|⚠️|Great for dynamic and theme-based UI|
|Inline Styles|✅|✅|✅|Quick and JS-driven|
|Tailwind CSS|✅|⚠️|⚠️|Fast, scalable with utility classes|

  

  

### Inline Style

```JavaScript
function Button() {
  const styles = {
    backgroundColor: "hsl(200, 100%, 50%)",
    color: "white",
    padding: "10px 20px",
    borderRadius: "15px",
    border: "none",
    cursor: "pointer",
    fontSize: "5rem",
  };

  return <button style={styles}>Click Me</button>;
}

export default Button;
```

  

### Module Style

```JavaScript
import styles from "./Button.module.css";

function Button() {
  return <button className={styles.button}>Click Me</button>;
}

export default Button;
```

```CSS
.button {
  background-color: hsl(200, 100%, 50%);
  color: white;
  padding: 10px 20px;
  border-radius: 15px;
  border: none;
  cursor: pointer;
  font-size: 5rem;
}
.button:hover {
  background-color: hsl(200, 100%, 40%);
  font-size: 7rem;
}
```