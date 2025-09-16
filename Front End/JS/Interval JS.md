---
Created: 2025-06-28T14:21
---
## `setInterval()`

**What it does:**

- Repeatedly executes a function at a fixed time interval (in milliseconds) until stopped.

**Syntax:**

```JavaScript
let intervalId = setInterval(function, delay, param1, param2, ...);
```

- **function** – the function to run repeatedly.
- **delay** – time in milliseconds between calls.
- **param1, param2, ...** – optional arguments passed to the function.

  

**Stopping the interval:**

```JavaScript
clearInterval(intervalId);
```

  

## Key Notes

✔ Runs **indefinitely** until `clearInterval()` is called.

✔ Interval timing isn’t perfectly precise – browser event loop can cause slight delays.

✔ Returns an **interval ID** you need to stop it later.

  

## Common Mistake

Using `setInterval(myFunction(), 1000)` – this **calls the function immediately**.

✅ Instead, pass the function **reference**: `setInterval(myFunction, 1000)`.

  

## Real-life example: Digital clock updating every second

```HTML
<div id="clock"></div>

<script>
function updateClock() {
  const now = new Date();
  const timeString = now.toLocaleTimeString();
  document.getElementById("clock").textContent = timeString;
}

// Start the interval to update clock every 1000ms (1 second)
let clockInterval = setInterval(updateClock, 1000);

// Optional: Stop the clock after 1 minute for demonstration
setTimeout(() => clearInterval(clockInterval), 60000);
</script>
```

🕒 **What this does:**

- Displays current time in a `<div>`
- Updates every second with `setInterval()`
- Stops updating after 1 minute with `setTimeout()` (for demonstration)

  

## Another practical example: Slideshow auto-advance

```JavaScript
let slideIndex = 0;
const slides = document.querySelectorAll(".slide");

function showNextSlide() {
  slides[slideIndex].classList.remove("active");
  slideIndex = (slideIndex + 1) % slides.length;
  slides[slideIndex].classList.add("active");
}

let slideshow = setInterval(showNextSlide, 3000); // Advance every 3 seconds

// To stop slideshow:
// clearInterval(slideshow);
```