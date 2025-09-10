## Set up proxy and .env for fetching in React

### ==🧠 1.== ==**Set up the Proxy (for Local Development)**==

In your **React app folder** (where `package.json` is), add this line:

```JSON
// package.json
{
  ...
  "proxy": "http://localhost:5000"
}
```

✅ This tells React's dev server (`npm start`) to forward any unknown API requests (like `/api/data`) to Flask.

---

### ==🧠 2.== ==**Create**== ==`**.env**`== ==**File in React**==

In the **root** of your React project (same level as `package.json`), create a file:

```Shell
touch .env
```

Inside `.env`, you can leave the API base empty for dev:

```Plain
REACT_APP_API_BASE=
```

Or omit it completely — `""` will default to using the proxy.

---

### ==🧠 3.== ==**Use the Env Variable in Code**==

In your React components or services:

```JavaScript
const API_BASE = process.env.REACT_APP_API_BASE || "";  // fallback to proxy

fetch(`${API_BASE}/api/data`)
  .then(res => res.json())
  .then(data => console.log(data));
```

✅ In dev, `API_BASE` is empty, so it fetches `/api/data`, which goes to Flask via the `proxy`.

---

  

### ==🧠 4.== ==**Set Up Flask to Run Locally**==

Make sure Flask is running on `http://localhost:5000`.

Example Flask app:

```Python
from flask import Flask, jsonify
from flask_cors import CORS

app = Flask(__name__)
CORS(app)  # Allow React (port 3000) to access

@app.route("/api/data")
def get_data():
    return jsonify({"message": "Hello from Flask!"})

if __name__ == "__main__":
    app.run(port=5000)
```

---

### ==🧠 5.== ==**Set Up Production**== `**.env.production**`

For deployment, create this:

```Bash
touch .env.production
```

Inside:

```Plain
REACT_APP_API_BASE=https://your-flask-backend.com
```

Then build the React app:

```Bash
npm run build
```

✅ Your build will use the hosted Flask API URL.

---

## 🧪 Test the Flow

|Environment|`.env`|URL Called by Code|Result|
|---|---|---|---|
|Dev|`REACT_APP_API_BASE=`|`/api/data`|Proxied to `localhost:5000`|
|Prod|`REACT_APP_API_BASE=https://...`|Full API URL|Calls hosted Flask server|
