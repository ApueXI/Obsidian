---
Created: 2025-07-12T08:52
---
```JavaScript
import React, { useEffect, useState, useRef } from "react";

export default function StopWatch() {
  const [isRunning, setIsRunning] = useState(false);
  const [elapsedTime, setElapsedTime] = useState(0);
  const intervalIDRef = useRef(null);
  const startTimeRef = useRef(0);

  useEffect(() => {
    if (isRunning) {
      intervalIDRef.current = setInterval(() => {
        setElapsedTime(Date.now() - startTimeRef.current);
      }, 10);
    }

    return () => {
      clearInterval(intervalIDRef.current);
    };
  }, [isRunning]);

  function start() {
    setIsRunning(true);
    startTimeRef.current = Date.now() - elapsedTime;
  }

  function stop() {
    setIsRunning(false);
  }

  function reset() {
    setElapsedTime(0);
    setIsRunning(false);
  }

  function formatTime() {
    let hours = Math.floor(elapsedTime / (1000 * 60 * 60));
    let minutes = Math.floor((elapsedTime / (1000 * 60)) % 60);
    let seconds = Math.floor((elapsedTime / 1000) % 60);
    let miliseconds = Math.floor((elapsedTime % 1000) / 10);

    hours = String(hours).padStart(2, "0");
    minutes = String(minutes).padStart(2, "0");
    seconds = String(seconds).padStart(2, "0");
    miliseconds = String(miliseconds).padStart(2, "0");

    return `${hours}:${minutes}:${seconds}:${miliseconds}`;
  }

  return (
    <div className="stop-watch">
      <div className="display-time">{formatTime()}</div>
      <div className="controls">
        <button className="button-start" onClick={start}>
          Start
        </button>
        <button className="button-stop" onClick={stop}>
          Stop
        </button>
        <button className="button-reset" onClick={reset}>
          Reset
        </button>
      </div>
    </div>
  );
}
```

```CSS
body {
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: hsl(0, 0%, 95%);
}
.stop-watch {
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 5px solid;
  border-radius: 50px;
  background-color: white;
  padding: 30px;
}
.display-time {
  font-size: 5rem;
  font-family: Arial, Helvetica, sans-serif;
  font-weight: bold;
  color: hsl(0, 0%, 30%);
  text-shadow: 2px 2px 4px hsl(0, 0%, 0%, 0.75);
  margin-bottom: 25px;
}
.controls button {
  font-size: 1.5rem;
  font-weight: bold;
  padding: 10px 20px;
  margin: 5px;
  min-width: 125px;
  border: none;
  border-radius: 15px;
  cursor: pointer;
  color: white;
  transition: background-color 0.35s ease;
}
.button-start {
  background-color: hsl(115, 100%, 40%);
}
.button-start:hover {
  background-color: hsl(115, 100%, 30%);
}
.button-stop {
  background-color: hsl(10, 90%, 50%);
}
.button-stop:hover {
  background-color: hsl(10, 90%, 40%);
}
.button-reset {
  background-color: hsl(205, 90%, 60%);
}
.button-reset:hover {
  background-color: hsl(205, 90%, 50%);
}
```