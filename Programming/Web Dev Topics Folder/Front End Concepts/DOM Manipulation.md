---
Created: 2025-06-23T19:02
---
## What is DOM Manipulation?

- The process of **accessing and changing** HTML elements dynamically using JavaScript.
- DOM = Document Object Model — a tree-like structure representing the page.

  

## Common DOM Methods

|   |   |   |
|---|---|---|
|Method|Description|Example|
|`document.getElementById()`|Select element by ID|`const el = document.getElementById('myId');`|
|`document.querySelector()`|Select first element matching CSS selector|`const el = document.querySelector('.myClass');`|
|`document.querySelectorAll()`|Select all matching elements|`const items = document.querySelectorAll('li');`|
|`element.textContent`|Get/set text content|`el.textContent = 'Hello';`|
|`element.innerHTML`|Get/set HTML inside element|`el.innerHTML = '<strong>Hi</strong>';`|
|`element.style.property`|Change CSS style|`el.style.color = 'red';`|
|`element.classList.add()`|Add a CSS class|`el.classList.add('active');`|
|`element.classList.remove()`|Remove a CSS class|`el.classList.remove('hidden');`|
|`element.setAttribute()`|Set an attribute|`el.setAttribute('data-id', '123');`|
|`element.getAttribute()`|Get an attribute|`const id = el.getAttribute('data-id');`|
|`document.createElement()`|Create a new element|`const div = document.createElement('div');`|
|`parent.appendChild(child)`|Add child element to parent|`parent.appendChild(div);`|
|`element.remove()`|Remove element from DOM|`el.remove();`|
|`element.addEventListener()`|Attach event listener|`el.addEventListener('click', () => {});`|

  

## Example: Adding a New Item to a List

```Plain
const ul = document.querySelector('ul');
const li = document.createElement('li');
li.textContent = 'New Item';
ul.appendChild(li);
```

  

## Event Delegation (Efficient Event Handling)

Instead of adding event listeners to many elements:

```Plain
document.querySelector('ul').addEventListener('click', (e) => {
  if (e.target.tagName === 'LI') {
    console.log('Clicked:', e.target.textContent);
  }
});
```

  

## Tips

- Prefer `textContent` over `innerHTML` when inserting plain text (safer).
- Use `querySelector`/`querySelectorAll` for flexible element selection.
- Clean up event listeners to avoid memory leaks.
- Use event delegation for dynamic elements.