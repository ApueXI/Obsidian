---
Created: 2025-06-06T15:59
---
## **Basic Table Structure**

```HTML
<table>
  <tr>
    <th>Header 1</th>
    <th>Header 2</th>
  </tr>
  <tr>
    <td>Row 1, Col 1</td>
    <td>Row 1, Col 2</td>
  </tr>
</table>
```

|   |   |
|---|---|
|Tag|Description|
|`<table>`|Table container|
|`<tr>`|Table row|
|`<th>`|Table header cell (bold + centered)|
|`<td>`|Table data cell|

  

## **Adding a Caption**

```HTML
<table>
  <caption>Student Grades</caption>
  <!-- ... -->
</table>
```

- `<caption>` adds a title to the table (displayed above by default).

  

## **Column and Row Span**

### Column span (`colspan`)

```HTML
<td colspan="2">Merged cell</td>
```

### Row span (`rowspan`)

```HTML
<td rowspan="2">Merged rows</td>
```

  

## **Semantic Grouping Tags**

|   |   |
|---|---|
|Tag|Use|
|`<thead>`|Groups header rows|
|`<tbody>`|Groups body rows|
|`<tfoot>`|Groups footer rows|

```HTML
<table>
  <thead>
    <tr><th>Name</th><th>Score</th></tr>
  </thead>
  <tbody>
    <tr><td>Anna</td><td>95</td></tr>
  </tbody>
  <tfoot>
    <tr><td>Average</td><td>90</td></tr>
  </tfoot>
</table>
```

  

## **Styling with CSS**

```CSS
table {
  width: 100%;
  border-collapse: collapse;
}

th, td {
  border: 1px solid black;
  padding: 8px;
  text-align: left;
}

thead {
  background-color: \#f2f2f2;
}
```

  

## Summary Table

|   |   |
|---|---|
|Element|Description|
|`<table>`|Defines a table|
|`<tr>`|Table row|
|`<th>`|Header cell|
|`<td>`|Data cell|
|`<caption>`|Table title|
|`<thead>`|Header group|
|`<tbody>`|Body group|
|`<tfoot>`|Footer group|
|`colspan`|Span across columns|
|`rowspan`|Span across rows|

  

```HTML
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=Edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>tables</title>
</head>

<body>
    <h3>Hours</h3>
    <table border="1">
        <tr>
            <th>Monday</th>
            <th>Tuesday</th>
            <th>Wednesday</th>
            <th>Thursday</th>
            <th>Fridau</th>
            <th>Saturday</th>
            <th>Sunday</th>
        </tr>
        <tr align="center">
            <td>Closed</td>
            <td>Open</td>
            <td>Closed</td>
            <td>Open</td>
            <td>Closed</td>
            <td>Open</td>
            <td>Closed</td>
        </tr>
    </table>
</body>

</html>
```