---
Created: 2025-06-19T15:22
---
```JavaScript
function generatepassowrd(passlength, lowercase, uppercase, number, symbols) {
    const lowercaseChar = "abcdefghijklmnopqrstuvwxyz";
    const uppercaseChar = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    const numberChar = "0123456789";
    const symbolsChar = "!@#$%^&*()_+";

    let allowedChars = "";
    let password = "";

    allowedChars += lowercase ? lowercaseChar : "";
    allowedChars += uppercase ? uppercaseChar : "";
    allowedChars += number ? numberChar : "";
    allowedChars += symbols ? symbolsChar : "";

    if (passlength <= 0) {
        return `Password length must be at least 1`;
    }
    if (allowedChars.length === 0) {
        return `Password must have a set of characters`;
    }
    for (let index = 0; index < passlength; index++) {
        const randomIndex = Math.floor(Math.random() * allowedChars.length + 1);
        password += allowedChars[randomIndex];
    }

    return password;
}

const passlength = 12;
const lowercase = true;
const uppercase = true;
const number = true;
const symbols = true;

const passowrd = generatepassowrd(
    passlength,
    lowercase,
    uppercase,
    number,
    symbols
);
console.log(`Generated Passowrd: ${passowrd}`);
```