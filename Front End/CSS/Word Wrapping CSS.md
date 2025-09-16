---
Created: 2025-06-29T13:11
---
## `white-space`

Controls whether and how white space is collapsed, and if text wraps to the next line.

```CSS
white-space: normal;       /* Default: text wraps, collapses spaces */
white-space: nowrap;       /* Prevents line breaks (no wrapping) */
white-space: pre;          /* Keeps white space + line breaks like <pre> tag */
white-space: pre-wrap;     /* Keeps white space + wraps if needed */
white-space: pre-line;     /* Collapses spaces, but keeps line breaks */
```

✅ **Common use:** Prevent wrapping with `white-space: nowrap;`

✅ Allow preserving formatting but still wrap with `white-space: pre-wrap;`.

  

## `word-wrap` / `overflow-wrap`

Controls if long words should be broken to prevent overflow.

```CSS
overflow-wrap: normal;     /* Default: words stick out if too long */
overflow-wrap: break-word; /* Break long words onto next line */

word-wrap: break-word;     /* Older synonym for overflow-wrap */
```

✅ **Tip:** Use `overflow-wrap: break-word;` to prevent horizontal scrolling on long words/URLs.

  

## `word-break`

Defines how words break when reaching the end of a line.

```CSS
word-break: normal;       /* Break only at allowed break points (spaces, hyphens) */
word-break: break-all;    /* Break anywhere if needed (even inside words) */
word-break: keep-all;     /* Keep words intact (common for languages like Korean/Chinese) */
```

✅ **Tip:** `word-break: break-all;` is helpful if you need to force breaks on long continuous strings.

  

## `text-overflow`

Used with `overflow: hidden;` and `white-space: nowrap;` to show an ellipsis (`...`) when text overflows its container.

```CSS
overflow: hidden;
white-space: nowrap;
text-overflow: ellipsis;  /* Adds ... at the end of clipped text */
```

✅ **Tip:** Great for truncating text in buttons, table cells, or UI cards.  
  

## Key combos

**Prevent wrapping with ellipsis:**

```CSS
overflow: hidden;
white-space: nowrap;
text-overflow: ellipsis;
```

**Wrap with preserved white space:**

```CSS
white-space: pre-wrap;
```

**Break long words but don’t force breaks mid-word:**

```CSS
overflow-wrap: break-word;
word-break: normal;
```

  

## Example snippet

```CSS
.text-wrap-example {
  width: 200px;
  border: 1px solid \#ccc;
  white-space: normal;        /* Allow wrapping */
  overflow-wrap: break-word;  /* Break long words */
  word-break: normal;         /* Don't break words unnecessarily */
}
```