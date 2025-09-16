---
Created: 2025-07-08T10:05
---
### Basic Card Component (Reusable)

```JavaScript
// Card.jsx
function Card({ title, content }) {
  return (
    <div style={styles.card}>
      <h2>{title}</h2>
      <p>{content}</p>
    </div>
  );
}

const styles = {
  card: {
    border: '1px solid \#ddd',
    padding: '16px',
    borderRadius: '8px',
    marginBottom: '12px',
    backgroundColor: '\#fff',
    boxShadow: '0 2px 5px rgba(0,0,0,0.1)',
  },
};

export default Card;
```

```JavaScript
// App.jsx
import Card from './Card';

function App() {
  return (
    <div>
      <Card title="React" content="A JavaScript library for building UIs." />
      <Card title="Vue" content="The Progressive JavaScript Framework." />
    </div>
  );
}
```

  

### Styled with Tailwind (if you're using it)

```JavaScript
function Card({ title, content }) {
  return (
    <div className="bg-white p-4 rounded-2xl shadow-md border max-w-sm">
      <h2 className="text-xl font-bold mb-2">{title}</h2>
      <p className="text-gray-600">{content}</p>
    </div>
  );
}
```

  

### Card with Image and Button

```JavaScript
function ImageCard({ imageUrl, title, description }) {
  return (
    <div style={styles.card}>
      <img src={imageUrl} alt={title} style={styles.img} />
      <h2>{title}</h2>
      <p>{description}</p>
      <button style={styles.btn}>Learn More</button>
    </div>
  );
}

const styles = {
  card: {
    border: '1px solid \#eee',
    borderRadius: '10px',
    overflow: 'hidden',
    maxWidth: '300px',
    padding: '16px',
    textAlign: 'center',
  },
  img: {
    width: '100%',
    borderRadius: '8px',
    marginBottom: '8px',
  },
  btn: {
    backgroundColor: '\#007BFF',
    color: 'white',
    padding: '8px 16px',
    border: 'none',
    borderRadius: '5px',
    cursor: 'pointer',
  },
};
```

  

### Mapping Multiple Cards

```JavaScript
const cardsData = [
  { title: 'HTML', content: 'Markup language for web pages.' },
  { title: 'CSS', content: 'Style sheet language for designing.' },
];

function App() {
  return (
    <div>
      {cardsData.map((card, i) => (
        <Card key={i} title={card.title} content={card.content} />
      ))}
    </div>
  );
}
```

  

### Tips

|Tip|Description|
|---|---|
|**Use props**|Pass dynamic content|
|**Extract to components**|Keep code DRY and reusable|
|**Use CSS or Tailwind**|Style cards consistently|
|**Use keys in lists**|Always add `key` when mapping card lists|
|**Add interaction**|Add buttons, hover effects, or modal triggers|

  

### App.jsx

```JavaScript
import Card from "./Card.jsx";

function App() {
  return (
    <>
      <Card></Card>
      <Card></Card>
      <Card></Card>
      <Card></Card>
      <Card></Card>
      <Card></Card>
      <Card></Card>
      <Card></Card>
      <Card></Card>
      <Card></Card>
      <Card></Card>
      <Card></Card>
    </>
  );
}

export default App;
```

### Card.jsx

```JavaScript
import profilePic from "./assets/Stelle.png";

function card() {
  return (
    <div className="card">
      <img src={profilePic} alt="An Image" className="card_img" />
      <h2 className="card-title">Stelle</h2>
      <p className="card-text">I am stil a student and i study at LSPU</p>
    </div>
  );
}

export default card;
```

### main.jsx

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

  

### index.css

```CSS
.card {
  border: 1px solid hsl(0, 0%, 80%);
  border-radius: 10px;
  box-shadow: 5px 5px 5px hsl(0, 0%, 0%, 0.1);
  padding: 20px;
  margin: 10px;
  text-align: center;
  max-width: 250px;
  display: inline-block;
}
.card .card_img {
  max-width: 60%;
  height: 150px;
  border-radius: 50%;
  margin-bottom: 10px;
}
.card-title {
  font-family: Arial, Helvetica, sans-serif;
  margin: 0;
  color: hsl(0, 0%, 20%);
}
.card-text {
  font-family: Arial, Helvetica, sans-serif;
  color: hsl(0, 0%, 30%);
}
```