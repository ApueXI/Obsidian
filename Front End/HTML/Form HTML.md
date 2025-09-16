---
Created: 2025-06-06T19:58
---
### **Form Tag Recap**

```HTML
<form action="/submit" method="post" autocomplete="on" novalidate>
  <!-- form controls go here -->
</form>
```

|   |   |
|---|---|
|Attribute|Description|
|`action`|Where data is sent|
|`method`|`get` or `post`|
|`autocomplete`|Enable/disable browser autofill|
|`novalidate`|Skip browser validation|

  

### **Advanced Input Types**

```HTML
<input type="date">
<input type="time">
<input type="range" min="0" max="100">
<input type="color">
<input type="file">
<input type="hidden" name="token" value="abc123">
```

|   |   |
|---|---|
|Type|Use|
|`date`, `time`|Pickers|
|`range`|Slider|
|`color`|Color picker|
|`file`|Upload files|
|`hidden`|Invisible data|

  

### **Radio Buttons & Checkboxes**

```HTML
<label><input type="radio" name="gender" value="male"> Male</label>
<label><input type="radio" name="gender" value="female"> Female</label>

<label><input type="checkbox" name="subscribe"> Subscribe</label>
```

- Radio = **one choice**
- Checkbox = **multiple choices**

  

### **Select Menus and Option Groups**

```HTML
<select name="car">
  <optgroup label="German Cars">
    <option value="bmw">BMW</option>
    <option value="audi">Audi</option>
  </optgroup>
</select>
```

  

### **Text Areas**

```HTML
<textarea name="message" rows="4" cols="30" placeholder="Your message..."></textarea>
```

  

### **Form Validation**

```HTML
<input type="email" required>
<input type="password" minlength="6" maxlength="12">
<input type="text" pattern="[A-Za-z]+" title="Only letters allowed">
```

|   |   |
|---|---|
|Attribute|Function|
|`required`|Cannot be empty|
|`minlength` / `maxlength`|Limits|
|`pattern`|Custom regex|
|`title`|Tooltip error message|

  

### **Form Buttons**

```HTML
<button type="submit">Send</button>
<button type="reset">Clear</button>
<button type="button" onclick="alert('Hi!')">Click Me</button>
```

  

### **Fieldsets & Legends**

```HTML
<fieldset>
  <legend>Personal Info</legend>
  <input type="text" name="name">
</fieldset>
```

- `<fieldset>` groups fields
- `<legend>` adds a title to the group

  

### **Form Styling (CSS)**

```CSS
form {
  display: flex;
  flex-direction: column;
  gap: 10px;
  max-width: 400px;
}
input, textarea, select {
  padding: 8px;
  font-size: 1rem;
}
```

  

### Summary: Key Elements

|   |   |
|---|---|
|Element|Use|
|`<form>`|Wraps the form|
|`<input>`|Field (text, email, etc.)|
|`<select>` / `<option>`|Dropdowns|
|`<textarea>`|Multiline input|
|`<button>`|Submit/reset/click|
|`required`, `pattern`, `minlength`, `maxlength`|Validation|
|`<fieldset>`, `<legend>`|Grouping|

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Form</title>
</head>

<body>
    <form action="index.php" method="POST" enctype="multipart/form-data">

        <label for="Username">Username</label>
        <input type="text" name="" id="Username" placeholder="Enter Name" required><br>

        <label for="password">Enter Pawsword</label>
        <input type="password" name="" id="password" placeholder="Enter your Password" required><br>

        <label for="email">Enter Email</label>
        <input type="email" name="" id="email" placeholder="Enter Email"><br>

        <label for="phone">Tel Number</label>
        <input type="tel" name="" id="phone" placeholder="Enter Phone Number" pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}"><br>

        <label for="bday">bday</label>
        <input type="date" name="" id="bday"><br>

        <label for="num">Qunatity</label>
        <input type="number" name="" id="num" min="0" value="1"><br>

        <label for="Mr">Mr.</label>
        <input type="radio" name="title" id="Mr" value="Mr">
        <label for="Ms">Ms.</label>
        <input type="radio" name="title" id="Ms" value="Ms">
        <label for="Dr">Dr.</label>
        <input type="radio" name="title" id="Dr" value="Dr"><br>

        <label for="pay">payment</label>
        <select name="" id="pay">
            <option value="">Visa</option>
            <option value="">Paypal</option>
            <option value="">Mastercard</option>
        </select><br>

        <label for="sub">subscribe</label>
        <input type="checkbox" name="" id="sub"><br>

        <label for="comment">Comment</label>
        <textarea name="" id="comment"></textarea><br>

        <label for="file">File</label>
        <input type="file" name="" id="file" accept="image/png, image/jpeg">

        <br>
        <input type="reset">
        <input type="submit">

    </form>
</body>

</html>
```

### **Form Tag Recap**

```Plain
html
CopyEdit
```

### **Advanced Input Types**

```Plain
html
CopyEdit
```

<input type="date">  
<input type="time">  
<input type="range" min="0" max="100">  
<input type="color">  
<input type="file">  
<input type="hidden" name="token" value="abc123">