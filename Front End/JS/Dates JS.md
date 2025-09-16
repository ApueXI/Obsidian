---
Created: 2025-06-22T15:36
---
### **Create a Date**

```JavaScript
const now = new Date(); // Current date & time
const birthday = new Date("1995-06-20"); // ISO string
const custom = new Date(2025, 5, 20); // YYYY, MM (0-indexed), DD
```

- Months are **0-based**: `0 = January`, `5 = June`.

  

### **Get Date Components**

```JavaScript
now.getFullYear();  // 2025
now.getMonth();     // 5 (June)
now.getDate();      // 20
now.getDay();       // 5 (Friday, 0 = Sunday)
now.getHours();     // 14
now.getMinutes();   // 30
now.getSeconds();   // 0
now.getMilliseconds(); // 123
```

  

### **Set Date Components**

```JavaScript
now.setFullYear(2030);
now.setMonth(0);         // January
now.setDate(1);          // Day of month
now.setHours(9, 30, 0);  // Set time (hour, min, sec)
```

  

### **Date to String**

```JavaScript
now.toString();        // Full date string
now.toDateString();    // "Tue Jun 20 2025"
now.toTimeString();    // "14:30:00 GMT+0800"
now.toISOString();     // "2025-06-20T06:30:00.000Z"
now.toLocaleString();  // Locale formatted (e.g., "6/20/2025, 2:30 PM")
```

  

### **Date Arithmetic (Add/Subtract)**

```JavaScript
const tomorrow = new Date();
tomorrow.setDate(tomorrow.getDate() + 1);

const oneWeekLater = new Date();
oneWeekLater.setDate(oneWeekLater.getDate() + 7);
```

- You can modify any unit using `setX(getX() ± value)`.

  

### **Compare Dates**

```JavaScript
const d1 = new Date("2025-06-20");
const d2 = new Date("2025-06-21");

console.log(d1 < d2); // true
console.log(d1.getTime() === d2.getTime()); // false
```

- Use `.getTime()` to compare exact timestamps (ms).

  

### **Time Difference Between Two Dates**

```JavaScript
const msDiff = d2 - d1;
const daysDiff = msDiff / (1000 * 60 * 60 * 24); // Convert ms to days
console.log(daysDiff); // 1
```

  

### **Unix Timestamp (Milliseconds since Jan 1, 1970)**

```JavaScript
Date.now(); // current timestamp
new Date().getTime(); // same as Date.now()
```

  

### **Parse Strings to Dates**

```JavaScript
new Date("2025-06-20T12:00:00Z"); // ISO string
Date.parse("2025-06-20"); // Returns timestamp (ms)
```

  

### Summary Table

|   |   |   |
|---|---|---|
|Task|Example|Output / Notes|
|Create date|`new Date()`|Current time|
|From string|`new Date("YYYY-MM-DD")`|Parse date|
|Get year/month/day|`.getFullYear()`, `.getMonth()`|Year / 0-based month / day|
|Set date values|`.setDate(1)`|Changes specific part|
|Format date|`.toLocaleString()`|Locale-formatted|
|Add/subtract days|`.setDate(date.getDate() + X)`|Basic date math|
|Compare dates|`d1 < d2` or `d1.getTime()`|Check order or exact match|
|Time difference|`(d2 - d1) / msPerDay`|In days|

  

```JavaScript
// Date(year, month, day, hour, minute, second, ms)
const date1 = new Date(2024, 1, 26, 2, 3, 4, 5);
const date2 = new Date("2024-01-02T12:22:29Z");
const date3 = new Date(0);
const date4 = new Date();

const time = date4.getDay();

console.log(date1); //Mon Feb 26 2024 02:03:04 GMT+0800 (Philippine Standard Time)
console.log(date2); //Tue Jan 02 2024 20:22:29 GMT+0800 (Philippine Standard Time)
console.log(date3); //Thu Jan 01 1970 08:00:00 GMT+0800 (Philippine Standard Time)

console.log(time);
```

  

```JavaScript
const date = new Date();

date.setFullYear(2024);
date.setMonth(3);

console.log(date);
```