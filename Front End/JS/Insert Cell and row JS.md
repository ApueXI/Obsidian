---
Created: 2025-07-01T12:41
---
## Selecting the Table

First, get a reference to your table element:

```JavaScript
const table = document.getElementById("myTable");
```

---

## ✅ Insert a Row at the End

```JavaScript
const newRow = table.insertRow(); // Adds at the end of the table
```

---

## ✅ Insert a Row at a Specific Index

```JavaScript
const index = 2; // e.g., insert at 3rd row (0-based)
const newRow = table.insertRow(index);
```

---

## ✅ Insert Cells into a Row

```JavaScript
const cell1 = newRow.insertCell(0); // Insert first cell
const cell2 = newRow.insertCell(1); // Insert second cell
```

---

## ✅ Set Text or HTML in a Cell

```JavaScript
cell1.textContent = "Hello";
cell2.innerHTML = "<strong>World</strong>";
```

---

## ✅ Insert Row with Loop (Dynamic Columns)

```JavaScript
const data = ["Apple", "Banana", "Cherry"];
const newRow = table.insertRow();

data.forEach((text, i) => {
  const cell = newRow.insertCell(i);
  cell.textContent = text;
});
```

---

## ✅ Insert Headers Dynamically

If you want to insert into a `<thead>` or create one dynamically:

```JavaScript
let thead = table.createTHead();
let headerRow = thead.insertRow();

["ID", "Name", "Age"].forEach((title, i) => {
  let th = document.createElement("th");
  th.textContent = title;
  headerRow.appendChild(th);
});
```

---

## ✅ Remove a Row

```JavaScript
const rowIndex = 1; // remove second row
table.deleteRow(rowIndex);
```

---

## 📎 Complete Example

```HTML
<table id="myTable" border="1">
  <tr>
    <th>Name</th>
    <th>Age</th>
  </tr>
</table>

<script>
  const table = document.getElementById("myTable");
  const newRow = table.insertRow();
  const nameCell = newRow.insertCell(0);
  const ageCell = newRow.insertCell(1);

  nameCell.textContent = "Alice";
  ageCell.textContent = "30";
</script>
```

---

✅ **Tip:** `insertRow()` and `insertCell()` both return the new element immediately, so you can chain setting their contents.