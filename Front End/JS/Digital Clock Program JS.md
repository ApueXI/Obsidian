---
Created: 2025-06-23T09:39
---
```HTML
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Digital Clock</title>
        <style>
            body {
                margin: 0;
            }
            \#clock-container {
                display: flex;
                justify-content: center;
                align-items: center;
                border: 2px solid;
                height: 100vh;
            }
            \#clock {
                font-size: 10em;
                font-weight: bold;
                text-align: center;
                backdrop-filter: blur(5px);
            }
        </style>
    </head>
    <body>
        <div id="clock-container">
            <div id="clock">00:00:00</div>
        </div>

        <script>
            function updateClock() {
                const now = new Date();

                let hours = now.getHours();
                const meridiem = hours >= 12 ? "PM" : "Am";
                hours = hours % 12 || 12;
                hours = hours.toString().padStart(2, 0);
                const minutes = now.getMinutes().toString().padStart(2, 0);
                const seconds = now.getSeconds().toString().padStart(2, 0);

                const timestring = `${hours}:${minutes}:${seconds} ${meridiem}`;
                document.getElementById("clock").textContent = timestring;
            }

            updateClock();
            setInterval(updateClock, 1000);
        </script>
    </body>
</html>
```