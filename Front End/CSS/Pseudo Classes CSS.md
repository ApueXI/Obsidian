---
Created: 2025-06-10T20:44
---
## ==What Are Pseudo-Classes?==

**Pseudo-classes** target elements based on their **state**, **position**, or **interaction**, without needing to add extra classes or IDs.

  

## Most Common Pseudo-Classes

|   |   |   |
|---|---|---|
|Pseudo-Class|Description|Example|
|`:hover`|When mouse is over an element|`a:hover`|
|`:active`|When element is being clicked|`button:active`|
|`:focus`|When element is focused (e.g. input)|`input:focus`|
|`:visited`|For visited links|`a:visited`|
|`:link`|For unvisited links|`a:link`|
|`:checked`|Checked inputs (checkbox/radio)|`input:checked`|
|`:disabled`|Disabled form elements|`input:disabled`|
|`:enabled`|Enabled form elements|`input:enabled`|
|`:required`|Required input fields|`input:required`|
|`:optional`|Optional input fields|`input:optional`|
|`:focus-within`|||

  

## Positional Pseudo-Classes

|   |   |   |
|---|---|---|
|Pseudo-Class|Description|Example|
|`:first-child`|First child of parent|`li:first-child`|
|`:last-child`|Last child of parent|`p:last-child`|
|`:nth-child(n)`|nth child of parent|`tr:nth-child(2)`|
|`:nth-last-child(n)`|nth from the end|`li:nth-last-child(1)`|
|`:only-child`|If it's the only child|`div:only-child`|

  

## Structural Pseudo-Classes

|   |   |   |
|---|---|---|
|Pseudo-Class|Description|Example|
|`:first-of-type`|First element of its type among siblings|`p:first-of-type`|
|`:last-of-type`|Last of its type|`h2:last-of-type`|
|`:nth-of-type(n)`|nth of its type|`li:nth-of-type(3)`|
|`:only-of-type`|If it's the only of its type|`div:only-of-type`|
|`:empty`|Element has no children (not even text)|`div:empty`|

  

## UI/State Pseudo-Classes

|   |   |   |
|---|---|---|
|Pseudo-Class|Description|Example|
|`:checked`|Input is checked|`input:checked`|
|`:focus`|Input is focused|`input:focus`|
|`:valid`|Valid form input|`input:valid`|
|`:invalid`|Invalid input|`input:invalid`|
|`:in-range`|Input in allowed range|`input:in-range`|
|`:out-of-range`|Out of allowed range|`input:out-of-range`|
|`:read-only`|Read-only input|`input:read-only`|

  

## Pseudo-Class Combinations

```CSS
a:hover,
a:focus {
  color: red;
}
```

Apply style when either hovered or focused.

  

## Special: `:not(selector)`

|   |   |   |
|---|---|---|
|Pseudo-Class|Description|Example|
|`:not(X)`|Targets everything **except** `X`|`div:not(.active)`|

  

## Quick Example

```CSS
input:focus {
  border: 2px solid blue;
}

li:nth-child(odd) {
  background: \#f0f0f0;
}

button:hover {
  background-color: green;
}
```