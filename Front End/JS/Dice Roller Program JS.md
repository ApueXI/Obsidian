---
Created: 2025-06-19T13:59
---
```JavaScript
function rollDice() {
    const numOfDice = document.getElementById("numOfDice").value;
    const diceResult = document.getElementById("diceResult");
    const diceImage = document.getElementById("diceimages");
    const values = [];
    const images = [];

    for (let index = 0; index < numOfDice; index++) {
        const value = Math.floor(Math.random() * 6 + 1);
        values.push(value);
        images.push(`<img src="images/${value}.svg"/>`);
    }

    diceResult.textContent = `Dice: ${values.join(", ")}`;
    diceImage.innerHTML = images.join("");
}
```

  

```HTML
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Dice Roller Program</title>
        <style>
            \#container {
                font-family: sans-serif;
                text-align: center;
                font-size: 2rem;
                font-weight: bold;
            }
            \#h1 {
                background-color: red;
                display: inline-block;
                padding: 10px 15px;
                border-radius: 25px;
            }
            button {
                font-size: 1.5rem;
                padding: 10px 15px;
                border-radius: 15px;
                border: none;
                background-color: hsl(240, 100%, 70%);
                color: white;
                font-weight: bold;
                cursor: pointer;
            }
            button:hover {
                background-color: hsl(240, 100%, 50%);
            }
            button:active {
                background-color: hsl(0, 100%, 50%);
            }
            \#numOfDice {
                width: 150px;
                font-size: 2rem;
                text-align: center;
                font-weight: bold;
            }
            \#diceResult {
                margin: 25px;
            }
            \#diceimages {
                min-height: 25vh;
                width: 100vh;
                border: 5px solid black;
            }
            \#diceimages img {
                width: 150px;
                margin: 10px;   
            }
            \#containers {
                display: flex;
                justify-content: center;
            }
        </style>
    </head>
    <body>
        <div id="container">
            <h1 id="h1">Dice Roller</h1>
            <br />
            <label for="numOfDice">Number of Dice</label>
            <input
                type="number"
                name=""
                id="numOfDice"
                value="1"
                min="1"
                max="6"
            />
            <button onclick="rollDice()">Roll Dice</button>
            <div id="diceResult"></div>
            <div id="containers">
                <div id="diceimages"></div>
            </div>
        </div>
        <script src="../DiceRollerProgram.js"></script>
    </body>
</html>
```