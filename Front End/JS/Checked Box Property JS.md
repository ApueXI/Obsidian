---
Created: 2025-06-15T17:04
---
### **HTML Checkbox Example**

```JavaScript
<input type="checkbox" id="subscribe" checked>
```

  

### **Access the Checkbox in JavaScript**

```JavaScript
let checkbox = document.getElementById("subscribe");
```

  

### **Common Checkbox Properties**

|   |   |   |
|---|---|---|
|Property|Description|Example|
|`checked`|`true` if checkbox is checked|`checkbox.checked` → `true/false`|
|`disabled`|`true` if checkbox is disabled|`checkbox.disabled = true;`|
|`indeterminate`|Checkbox looks "partially checked"|`checkbox.indeterminate = true;`|
|`value`|Value attribute of the checkbox|`checkbox.value`|
|`name`|Name attribute for form submission|`checkbox.name`|
|`id`|ID attribute|`checkbox.id`|

  

### **Check if a Checkbox is Checked**

```JavaScript
if (checkbox.checked) {
  console.log("User is subscribed.");
} else {
  console.log("Not subscribed.");
}
```

  

### **Toggle a Checkbox**

```JavaScript
checkbox.checked = !checkbox.checked;
```

  

### **Event Listener for Changes**

```JavaScript
checkbox.addEventListener("change", function() {
  if (this.checked) {
    console.log("Checked!");
  } else {
    console.log("Unchecked!");
  }
});
```

  

### Tip:

- `indeterminate` is **visual only** — it doesn’t affect form submission.