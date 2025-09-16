---
Created: 2025-07-11T13:42
---
```JavaScript
import React, { useState, useEffect } from "react";

function DigitalClock() {
  const [time, setTime] = useState(new Date());

  useEffect(() => {
    const intervalID = setInterval(() => {
      setTime(new Date());
    }, 1000);

    return () => {
      clearInterval(intervalID);
    };
  }, []);

  function formatTime() {
    let hours = time.getHours();
    const minutes = time.getMinutes();
    const seconds = time.getSeconds();
    const meridiem = hours >= 12 ? "PM" : "AM";

    hours = hours % 12 || 12;

    return `${paddZero(hours)}:${paddZero(minutes)}:${paddZero(
      seconds
    )} ${meridiem}`;
  }

  function paddZero(number) {
    return (number < 10 ? "0" : "") + number;
  }

  return (
    <div className="clock-container">
      <div className="clock">
        <span>{formatTime()}</span>
      </div>
    </div>
  );
}

export default DigitalClock;
```

```CSS
body {
  background-image: url(assets/huashi_moon.jpg);
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
  background-attachment: fixed;
  margin: 0;
  /*  */

  display: flex;
  justify-content: center;
  min-height: 100vh;
  align-items: center;
}
.clock-container {
  backdrop-filter: blur(10px);
  width: 100vw;
  padding: 10px 0;
}
.clock {
  color: white;
  font-size: 6rem;
  font-weight: bold;
  font-family: Arial, Helvetica, sans-serif;
  text-shadow: 3px 3px 5px hsl(0, 0%, 0%, 0.75);
  text-align: center;
}
```