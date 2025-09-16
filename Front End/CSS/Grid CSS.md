---
Created: 2025-06-29T11:18
---
## Basic Grid Container Properties

```CSS
.container {
  display: grid;                   /* Enable grid layout */
  grid-template-columns: 200px 1fr;/* Column sizes */
  grid-template-rows: 100px auto;  /* Row sizes */
  gap: 20px;                       /* Space between rows & columns */
  row-gap: 10px;                   /* Only row gap */
  column-gap: 15px;                /* Only column gap */
}
```

  

## Defining Grid Tracks

```CSS
.container {
  grid-template-columns: repeat(3, 1fr);    /* 3 equal columns */
  grid-template-rows: 50px auto 50px;       /* 3 rows with specific heights */
  grid-auto-rows: 100px;                    /* Height for rows created implicitly */
  grid-auto-columns: 200px;                 /* Width for columns created implicitly */
}
```

  

## Placing Grid Items

```CSS
.item1 {
  grid-column-start: 1;        /* Start at column line 1 */
  grid-column-end: 3;          /* End before column line 3 */
  grid-row: 1 / 3;             /* Span from row line 1 to 3 */
}

/* shorthand placement */
.item2 {
  grid-area: 2 / 1 / 3 / 3;    /* row-start / column-start / row-end / column-end */
}
```

  

## Named Grid Areas

```CSS
.container {
  grid-template-areas:
    "header header"
    "sidebar content"
    "footer footer";
}

.header  { grid-area: header; }
.sidebar { grid-area: sidebar; }
.content { grid-area: content; }
.footer  { grid-area: footer; }
```

  

## Aligning Items

```CSS
.container {
  justify-items: start | end | center | stretch;   /* align items horizontally */
  align-items: start | end | center | stretch;     /* align items vertically */
  justify-content: start | end | center | space-between | space-around | space-evenly; /* align entire grid horizontally */
  align-content: start | end | center | space-between | space-around | space-evenly;   /* align entire grid vertically */
}

.item {
  justify-self: start | end | center | stretch;    /* align individual item horizontally */
  align-self: start | end | center | stretch;      /* align individual item vertically */
}
```

  

## Auto-placement & Order

```CSS
.container {
  grid-auto-flow: row | column | row dense | column dense; /* direction & dense packing */
}

.item {
  order: 1; /* controls item order (less common in grid but supported) */
}
```

  

## Min/Max & Auto-fit

```CSS
.container {
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  /* auto-fit: fill space with as many columns as possible */
  /* minmax(): size between min and max limits */
}
```

  

## Helpful Shorthands

- `grid-template`: combine rows, columns, and areas in one property.
- `gap`: shorthand for `row-gap` & `column-gap`.

  

### Quick Example

```CSS
.container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: 60px auto 60px;
  gap: 15px;
  grid-template-areas:
    "header header header header"
    "sidebar content content content"
    "footer footer footer footer";
}

.header  { grid-area: header; }
.sidebar { grid-area: sidebar; }
.content { grid-area: content; }
.footer  { grid-area: footer; }
```