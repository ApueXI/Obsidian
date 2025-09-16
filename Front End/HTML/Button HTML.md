---
Created: 2025-06-06T18:39
---
## **Basic Form Structure**

```HTML
<form action="/submit" method="post">
  <input type="text" name="username">
  <button type="submit">Submit</button>
</form>
```

|   |   |
|---|---|
|Tag / Attribute|Purpose|
|`<form>`|Container for input controls|
|`action`|Where to send the form data|
|`method`|HTTP method (`get` or `post`)|

  

## **Input Types**

```HTML
<input type="text">
<input type="password">
<input type="email">
<input type="number">
<input type="checkbox">
<input type="radio">
<input type="submit">
```

|   |   |
|---|---|
|Type|Purpose|
|`text`|Single-line text|
|`password`|Hidden input|
|`email`|Email format validation|
|`number`|Only numbers|
|`checkbox`|On/off toggle|
|`radio`|Single choice from group|
|`submit`|Submit form|

  

## **Common Form Elements**

```HTML
<label for="username">Username</label>
<input id="username" type="text">

<select>
  <option>Option 1</option>
  <option>Option 2</option>
</select>

<textarea rows="4" cols="50"></textarea>
```

|   |   |
|---|---|
|Element|Purpose|
|`<label>`|Clickable text tied to an input|
|`<input>`|General input|
|`<select>` + `<option>`|Drop-down menu|
|`<textarea>`|Multiline input|

  

## **Form Attributes**

|   |   |
|---|---|
|Attribute|Description|
|`name`|Key sent with the form data|
|`value`|Default data in the field|
|`placeholder`|Hint inside the input|
|`required`|Field must be filled out|
|`disabled`|Grays out the field|
|`readonly`|User can’t edit|

  

## **Example Login Form**

```HTML
<form action="/login" method="post">
  <label>Email</label>
  <input type="email" name="email" required>
  
  <label>Password</label>
  <input type="password" name="password" required>
  
  <button type="submit">Log In</button>
</form>
```

  

## **Styling with CSS**

```CSS
input, select, textarea {
  padding: 8px;
  margin-bottom: 10px;
  width: 100%;
  box-sizing: border-box;
}
```

  

## Summary Table

|   |   |
|---|---|
|Tag/Element|Description|
|`<form>`|Starts the form|
|`<input>`|Text, password, email, etc.|
|`<textarea>`|Multi-line input|
|`<select>` + `<option>`|Drop-down menus|
|`<button>`|Clickable button|
|`required`|Makes a field mandatory|
|`placeholder`|Shows hint text|
|`method="get"`|Appends data to URL|
|`method="post"`|Sends data securely|

  

```HTML
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Button</title>
</head>
<body>
    <a href="basics.html">
        <button style="font-size:25px;">Click me</button>
    </a>
</body>
</html>
```