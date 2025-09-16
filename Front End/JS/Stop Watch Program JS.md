---
Created: 2025-06-23T12:11
---
```JavaScript
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Stop Watch Program</title>
        <style>
            body {
                display: flex;
                flex-direction: column;
                align-items: center;
                background-color: hsl(0, 0%, 90%);
            }
            \#h1 {
                font-size: 4rem;
                font-family: Arial, sans-serif, sans-serif;
                color: hsl(0, 0%, 25%);
            }
            \#container {
                display: flex;
                flex-direction: column;
                align-items: center;
                border: 5px solid;
                border-radius: 50px;
                padding: 30px;
                background-color: white;
            }
            \#display {
                font-size: 5rem;
                font-family: monospace, sans-serif;
                font-weight: bold;
                color: hsl(0, 0%, 30%);
                text-shadow: 4px 4px 5px hsl(0, 0%, 0%), 0.75;
                margin-bottom: 25px;
            }
            \#controls button {
                font-size: 1.5rem;
                font-weight: bold;
                padding: 10px 20px;
                margin: 5px;
                min-width: 125px;
                border: none;
                border-radius: 10px;
                cursor: pointer;
                color: white;
                transition: background-color 0.3s ease;
            }
            \#startbtn {
                background-color: hsl(120, 100%, 35%);
            }
            \#startbtn:hover {
                background-color: hsl(120, 100%, 25%);
            }
            \#stopbtn {
                background-color: hsl(0, 100%, 60%);
            }
            \#stopbtn:hover {
                background-color: hsl(0, 100%, 40%);
            }
            \#resetbtn {
                background-color: hsl(240, 100%, 60%);
            }
            \#resetbtn:hover {
                background-color: hsl(240, 100%, 40%);
            }
        </style>
    </head>
    <body>
        <h1 id="h1">Stop Watch</h1>

        <div id="container">
            <div id="display">00:00:00:00</div>
            <div id="controls">
                <button id="startbtn" onclick="start()">Start</button>
                <button id="stopbtn" onclick="stop()">Stop</button>
                <button id="resetbtn" onclick="reset()">Reset</button>
            </div>
        </div>

        <script>
            const display = document.getElementById("display");
            let timer = null;
            let startTime = 0;
            let elapsedTime = 0;
            let isRunnig = false;

            function start() {
                if (!isRunnig) {
                    startTime = Date.now() - elapsedTime;
                    timer = setInterval(update, 10);
                    isRunnig = true;
                }
            }
            function stop() {
                if (isRunnig) {
                    clearInterval(timer);
                    elapsedTime = Date.now() - startTime;
                    isRunnig = false;
                }
            }
            function reset() {
                clearInterval(timer);
                startTime = 0;
                elapsedTime = 0;
                isRunnig = false;
                display.textContent = "00:00:00:00";
            }
            function update() {
                const currentTime = Date.now();
                elapsedTime = currentTime - startTime;
                let hours = Math.floor(elapsedTime / (1000 * 60 * 60));
                let minute = Math.floor((elapsedTime / (1000 * 60)) % 60);
                let seconds = Math.floor((elapsedTime / 1000) % 60);
                let miliseconds = Math.floor((elapsedTime % 1000) / 10);

                hours = String(hours).padStart(2, "0");
                minute = String(minute).padStart(2, "0");
                seconds = String(seconds).padStart(2, "0");
                miliseconds = String(miliseconds).padStart(2, "0");

                display.textContent = `${hours}:${minute}:${seconds}:${miliseconds}`;
            }
        </script>
    </body>
</html>
```