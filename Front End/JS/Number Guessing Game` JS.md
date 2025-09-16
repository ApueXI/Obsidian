---
Created: 2025-06-18T12:59
---
```JavaScript
const min = 50;
const max = 100;
const answer = Math.floor(Math.random() * (max - min + 1) + min);

let attempts = 0;
let guess;
let isRunnig = true;

while (isRunnig) {
  guess = window.prompt(`Guess a number between ${min} - ${max}`);
  guess = Number(guess);

  if (isNaN(guess) || guess <= min || guess >= max) {
    window.alert(`Please enter a valid number`);
  } else {
    attempts++;
    if (guess < answer) {
      window.alert(`Too low`);
    } else if (guess > answer) {
      window.alert(`Too high`);
    } else {
      window.alert(`Correct the answer is ${answer}. it took you ${attempts} attempts to get it right`);
      isRunnig = false;
    }
  }
}
```