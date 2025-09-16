---
Created: 2025-06-24T07:49
---
## **DOM (Document Object Model)**

### 🧠 **Definition**

- The **DOM** is a **programming interface** for web documents.
- It represents the **structure of an HTML or XML document** as a **tree of objects**.
- You can **create, read, update, and delete (CRUD)** elements using JavaScript.

  

### **DOM Tree Structure**

- The DOM turns HTML into a **tree of nodes**:
    
    ```Plain
    Document
     └── <html>
          ├── <head>
          └── <body>
               ├── <h1>
               └── <p>
    ```
    
- Types of **nodes**:
    - **Element node** – e.g., `<div>`, `<p>`, `<a>`
    - **Text node** – text inside an element
    - **Attribute node** – e.g., `id="title"`

  

### **Accessing the DOM**

Common JavaScript methods:

```JavaScript
document.getElementById("id")
document.getElementsByClassName("class")
document.getElementsByTagName("div")
document.querySelector("selector")
document.querySelectorAll("selector")
```

  

### **Modifying the DOM**

- **Change content**
    
    ```JavaScript
    element.textContent = "Hello";
    element.innerHTML = "<strong>Bold</strong>";
    ```
    
- **Change styles**
    
    ```JavaScript
    element.style.color = "red";
    ```
    
- **Change attributes**
    
    ```JavaScript
    element.setAttribute("href", "https://...");
    ```
    
- **Add/Remove elements**
    
    ```JavaScript
    parent.appendChild(newElement);
    parent.removeChild(childElement);
    ```
    

  

### **DOM Events**

- Handle user actions (clicks, input, etc.)
    
    ```JavaScript
    element.addEventListener("click", function() {
      alert("Clicked!");
    });
    ```
    

  

### **Why DOM is Important**

- Makes HTML **interactive** with JavaScript
- Enables **dynamic changes** (SPAs, animations, validations)
- Used in **front-end frameworks** (React, Vue, etc.)

  

### **Related Concepts**

- **BOM (Browser Object Model)** – interacts with browser (e.g., `window`, `navigator`)
- **Virtual DOM** – used in React to optimize performance
- **DOM Manipulation Libraries** – like jQuery, simplify interaction

  

```JavaScript
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Document</title>
    </head>
    <body>
        <h1 id="welcome">Welcome</h1>
        <script src="../DOM.js">
                        document.body.style.backgroundColor = "green";

            const username = "Bro Code";
            const welcomeMessage = document.getElementById("welcome");

            welcomeMessage.textContent += username === "" ? "Guest" : username;
        </script>
    </body>
</html>
```