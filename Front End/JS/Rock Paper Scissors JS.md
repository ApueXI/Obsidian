---
Created: 2025-06-25T16:50
---
```HTML
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Rock Paper Scissors</title>
        <style>
            body {
                font-family: Arial, Helvetica, sans-serif;
                font-weight: bold;
                margin: 0;
                display: flex;
                flex-direction: column;
                align-items: center;
            }
            h1 {
                font-size: 3.5rem;
                color: hsl(0, 0%, 20%);
            }
            .choices {
                margin-bottom: 30px;
            }
            .choices button {
                font-size: 7.5rem;
                min-width: 160px;
                margin: 0px 10px;
                border-radius: 250px;
                background-color: hsl(200, 100%, 50%);
                cursor: pointer;
                transition: background-color 0.5s ease;
            }
            .choices button:hover {
                background-color: hsl(200, 100%, 70%);
            }
            \#playerDisplay,
            \#computerDisplay {
                font-size: 2.5rem;
            }
            \#resultDisplay {
                font-size: 5rem;
                margin: 30px 0px;
            }
            .greenText,
            \#playerScoreDisplay {
                color: green;
            }
            .redText,
            \#computerScoreDisplay {
                color: red;
            }
            .blueText,
            \#tieScoreDisplay {
                color: blue;
            }
            .scoreDisplay {
                font-size: 2rem;
            }
        </style>
    </head>
    <body>
        <h1>Rock - Paper - Scissors</h1>

        <div class="choices">
            <button onclick="playGame('rock')">👊</button>
            <button onclick="playGame('paper')">🖐️</button>
            <button onclick="playGame('scissor')">✌️</button>
        </div>

        <div id="playerDisplay">PLAYER:</div>
        <div id="computerDisplay">COMPUTER:</div>
        <div id="resultDisplay"></div>

        <div class="scoreDisplay">
            Player Score:
            <span id="playerScoreDisplay">0</span>
        </div>
        <div class="scoreDisplay">
            Computer Score:
            <span id="computerScoreDisplay">0</span>
        </div>
        <div class="scoreDisplay">
            Tie:
            <span id="tieScoreDisplay">0</span>
        </div>

        <script src="../RockPaperScissors.js">
                        const choices = ["rock", "paper", "scissor"];
            const playerDisplay = document.getElementById("playerDisplay");
            const computerDisplay = document.getElementById("computerDisplay");
            const resultDisplay = document.getElementById("resultDisplay");
            const playerScoreDisplay = document.getElementById("playerScoreDisplay");
            const computerScoreDisplay = document.getElementById("computerScoreDisplay");
            const tieScoreDisplay = document.getElementById("tieScoreDisplay");
            let playerScore = 0;
            let computerScore = 0;
            let tieScore = 0;

            function playGame(playerChoice) {
                const computerChoice = choices[Math.floor(Math.random() * 3)];

                let result = "";
                if (playerChoice === computerChoice) {
                    result = "It's a TIE!";
                } else {
                    switch (playerChoice) {
                        case "rock":
                            result =
                                computerChoice === "scissor" ? "You Win!" : "You Lose!";
                            break;
                        case "paper":
                            result = computerChoice === "rock" ? "You Win!" : "You Lose!";
                            break;
                        case "scissor":
                            result = computerChoice === "paper" ? "You Win!" : "You Lose!";
                            break;
                        default:
                            break;
                    }
                }
                playerDisplay.textContent = `PLAYER: ${playerChoice}`;
                computerDisplay.textContent = `COMPUTER: ${computerChoice}`;
                resultDisplay.textContent = result;

                resultDisplay.classList.remove("greenText", "redText", "blueText");

                switch (result) {
                    case "You Win!":
                        resultDisplay.classList.add("greenText");
                        playerScore++;
                        playerScoreDisplay.textContent = playerScore;
                        break;
                    case "You Lose!":
                        resultDisplay.classList.add("redText");
                        computerScore++;
                        computerScoreDisplay.textContent = computerScore;
                        break;
                        case "It's a TIE!":
                            resultDisplay.classList.add("blueText");
                            tieScore++;
                            tieScoreDisplay.textContent = tieScore;
                        break;

                    default:
                        break;
                }
            }
        </script>
    </body>
</html>
```