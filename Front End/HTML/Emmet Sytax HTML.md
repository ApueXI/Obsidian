---
Created: 2025-06-11T19:22
---
## Emmet Syntax Cheat Sheet (HTML-focused)

Emmet uses abbreviations that expand into full HTML code when you hit `Tab`.

  

### **Basic Structure**

|   |   |
|---|---|
|Syntax|Expands To|
|`html:5`|Basic HTML5 boilerplate|
|`!`|Same as `html:5`|

```HTML
html:5 → 
<!DOCTYPE html>
         <html lang="en">
         <head>...</head>
         <body>...</body>
         </html>
```

  

### **Elements & Nesting**

|   |   |
|---|---|
|Abbreviation|Result|
|`div`|`<div></div>`|
|`ul>li`|`<ul><li></li></ul>`|
|`div>ul>li`|Nested tags|
|`section>h2+p`|`<section><h2></h2><p></p></section>`|

  

### **Multiplication**

|   |   |
|---|---|
|Abbreviation|Result|
|`ul>li*3`|3 `<li>` tags inside `<ul>`|

```HTML
<ul>
  <li></li>
  <li></li>
  <li></li>
</ul>
```

  

### **Classes and IDs**

|   |   |
|---|---|
|Syntax|Output|
|`.box`|`<div class="box"></div>`|
|`#header`|`<div id="header"></div>`|
|`div.container`|`<div class="container"></div>`|
|`div#main.content`|`<div id="main" class="content"></div>`|

  

### **Text & Attributes**

|   |   |
|---|---|
|Syntax|Output|
|`a{Click here}`|`<a>Click here</a>`|
|`img[src="img.jpg"]`|`<img src="img.jpg">`|
|`input:checkbox`|`<input type="checkbox">`|
|`button[type=submit]{Send}`|`<button type="submit">Send</button>`|

  

### **Siblings & Climbing**

|   |   |   |
|---|---|---|
|Syntax|Meaning|Result|
|`h1+p`|Sibling|`<h1></h1><p></p>`|
|`div>ul>li^^p`|Go up|`<div><ul><li></li></ul></div><p></p>`|

  

### **Grouping**

|   |   |
|---|---|
|Syntax|Result|
|`(header>h1)+section+footer`|Groups header with nested h1|

```HTML
<header>
  <h1></h1>
</header>
<section></section>
<footer></footer>
```

  

### **Form Example**

```HTML
form>label+input:email+br+label+input:password+br+button{Login}

<form>
  <label></label>
  <input type="email">
  <br>
  <label></label>
  <input type="password">
  <br>
  <button>Login</button>
</form>
```

  

### Bonus: CSS Emmet Snippets

|   |   |
|---|---|
|Syntax|Expands To|
|`m10`|`margin: 10px;`|
|`p20-10`|`padding: 20px 10px;`|
|`w100p`|`width: 100%;`|
|`bgc`|`background-color:`|
|`pos:a`|`position: absolute;`|
|`d:f`|`display: flex;`|

  

### Pro Tip

Most editors expand Emmet by pressing `Tab` **after typing an abbreviation**. You can also use it inside existing elements (like in JSX or inline).