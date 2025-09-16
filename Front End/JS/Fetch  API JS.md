---
Created: 2025-06-25T17:24
---
### **What is** `**fetch()**`**?**

- `fetch()` is a built-in JavaScript method to **make HTTP requests** (like Ajax but modern).
- Returns a **Promise** that resolves to a `Response` object.

  

### **Basic GET Request**

```JavaScript
fetch("https://api.example.com/data")
  .then(res => res.json())      // Convert response to JSON
  .then(data => console.log(data))
  .catch(err => console.error("Fetch error:", err));
```

  

### **Using** `**async/await**` **with** `**fetch**`

```JavaScript
async function loadData() {
  try {
    const res = await fetch("https://api.example.com/data");
    const data = await res.json();
    console.log(data);
  } catch (err) {
    console.error("Error:", err);
  }
}
```

  

### **POST Request (Send Data)**

```JavaScript
fetch("https://api.example.com/users", {
  method: "POST",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({ name: "Alice", age: 25 })
})
  .then(res => res.json())
  .then(data => console.log("Created:", data));
```

  

### **PUT or PATCH (Update Data)**

```JavaScript
fetch("https://api.example.com/users/1", {
  method: "PUT",
  headers: {
    "Content-Type": "application/json"
  },
  body: JSON.stringify({ age: 26 })
})
  .then(res => res.json())
  .then(data => console.log("Updated:", data));
```

  

### **DELETE Request**

```JavaScript
fetch("https://api.example.com/users/1", {
  method: "DELETE"
})
  .then(res => {
    if (res.ok) console.log("Deleted!");
    else throw new Error("Failed to delete");
  })
  .catch(console.error);
```

  

### **Check for HTTP Errors**

```JavaScript
fetch("https://api.example.com/data")
  .then(res => {
    if (!res.ok) throw new Error("HTTP error " + res.status);
    return res.json();
  })
  .then(data => console.log(data))
  .catch(err => console.error("Fetch failed:", err));
```

  

### Summary Table

|   |   |
|---|---|
|Task|Example Code|
|GET|`fetch(url)`|
|POST|`{ method: "POST", body: JSON.stringify() }`|
|PUT / PATCH|`{ method: "PUT", body: JSON.stringify() }`|
|DELETE|`{ method: "DELETE" }`|
|Headers|`{ headers: { "Content-Type": "application/json" } }`|
|Handle response|`.then(res => res.json())` or `await res.json()`|

  

```JavaScript
fetch("https://pokeapi.co/api/v2/pokemon/pikachu")
    .then((response) => {
        console.log(`Status Code: ${response.status}`);
        if (!response.ok) {
            throw new Error(`Could not fetch resource`);
        } else {
            return response.json();
        }
    })
    .then((data) => {
        console.log(data);
        console.log(data.name);
    })
    .catch((error) => console.log(`Error: ${error}`));
```

  

```JavaScript
async function fetchData() {
    try {
        const response = await fetch(
            "https://pokeapi.co/api/v2/pokemon/arceus"
        );
        if (!response.ok) {
            throw new Error(`Could not fetch resource`);
        }
        const data = await response.json();
        console.log(data);
    } catch (error) {
        console.error(`Error: ${error}`);
    }
}
fetchData();
```

  

```HTML
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>JSON File</title>
    </head>
    <body>
        <input
            type="text"
            name=""
            id="pokemonName"
            placeholder="Enter pokemon Name"
            value="pikachu"
        />
        <button onclick="fetchData()">Fetch Pokemon</button><br />

        <img
            src=""
            alt="Pokemon Sprite"
            id="pokemonSprite"
            style="display: none"
        />

        <script src="../FetchAPI.js">
                        async function fetchData() {
                try {
                    const pokemonName = document
                        .getElementById("pokemonName")
                        .value.toLowerCase();

                    const response = await fetch(
                        `https://pokeapi.co/api/v2/pokemon/${pokemonName}`
                    );
                    if (!response.ok) {
                        throw new Error(`Could not fetch resource`);
                    }

                    const data = await response.json();
                    console.log(data);
                    const pokemonSprite = data.sprites.front_default;
                    const imgElement = document.getElementById("pokemonSprite");
                    imgElement.src = pokemonSprite;
                    imgElement.style.display = "block";
                } catch (error) {
                    console.error(`Error: ${error}`);
                }
            }
            fetchData();
        </script>
    </body>
</html>
```

  

```Python
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/')
def index():
    # Serve a simple HTML page with JS (for demo purposes)
    return HTML_File

@app.route('/api/receive_bool', methods=['POST'])
def receive_bool():
    data = request.get_json()
    flag = data.get('flag')
    if isinstance(flag, bool):
        return jsonify({'message': f'Received boolean: {flag}'})
    else:
        return jsonify({'message': 'Error: Expected a boolean value'}), 400

if __name__ == '__main__':
    app.run(debug=True)
```

  

```HTML
<!DOCTYPE html>
    <html>
    <head><title>Send Boolean Example</title></head>
    <body>
      <button onclick="sendBool(true)">Send TRUE</button>
      <button onclick="sendBool(false)">Send FALSE</button>
      <p id="response"></p>

      <script>
      function sendBool(value) {
        fetch('/api/receive_bool', {
          method: 'POST',
          headers: {'Content-Type': 'application/json'},
          body: JSON.stringify({flag: value})
        })
        .then(res => res.json())
        .then(data => {
          document.getElementById('response').textContent = data.message;
        })
        .catch(err => {
          console.error(err);
          document.getElementById('response').textContent = 'Error sending data.';
        });
      }
      </script>
    </body>
    </html>
```

  

```HTML
<!DOCTYPE html>
<html>
<head>
  <title>Inventory</title>
</head>
<body>
  <h1>Inventory Products</h1>
  <div id="product-list"></div>

  <script>
    // Fetch products from your Flask API
    fetch('/api/products')
      .then(response => response.json())
      .then(data => {
        const container = document.getElementById('product-list');
        data.forEach(product => {
          const div = document.createElement('div');
          div.innerHTML = `
            <h3>${product.name}</h3>
            <p>Price: $${product.price.toFixed(2)}</p>
          `;
          container.appendChild(div);
        });
      })
      .catch(error => {
        console.error('Error fetching products:', error);
      });
  </script>
</body>
</html>
```