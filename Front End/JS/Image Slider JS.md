---
Created: 2025-06-25T16:50
---
```HTML
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <title>Image Slider</title>
        <style>
            .slider {
                position: relative;
                width: 100%;
                margin: auto;
                overflow: hidden;
            }
            .slider img {
                width: 100%;
                display: none;
            }
            img.displaySlide {
                display: block;
                animation-name: fade;
                animation-duration: 1.5s;
            }
            .slider button {
                position: absolute;
                top: 50%;
                transform: translateY(-50%);
                font-size: 2rem;
                background-color: hsl(0, 0%, 50%);
                color: white;
                border: none;
                cursor: pointer;
                padding: 10px 15px;
            }
            .prev {
                left: 0;
            }
            .next {
                right: 0;
            }
            @keyframes fade {
                from {
                    opacity: 0.5;
                }
                to {
                    opacity: 1;
                }
            }
        </style>
    </head>
    <body>
        <div class="slider">
            <div class="slides">
                <img
                    class="slide"
                    src="images/huashi moon.jpg"
                    alt="huashi moon"
                />
                <img
                    class="slide"
                    src="images/huashi summer steps.jpg"
                    alt="huashi summer steps"
                />
                <img
                    class="slide"
                    src="images/huashi summer.jpg"
                    alt="huashi summer"
                />
                <img
                    class="slide"
                    src="images/Huashi wing.jpg"
                    alt="Huashi wing"
                />
            </div>
            <button class="prev" onclick="prevSlide()">&#10094;</button>
            <button class="next" onclick="nextSlide()">&#10095;</button>
        </div>

        <script src="../imageSlider.js">
                        const slides = document.querySelectorAll(".slides img");
            let slideIndex = 0;
            let intervalId = null;

            document.addEventListener("DOMContentLoaded", initializeSlider);

            function initializeSlider() {
                if (slides.length > 0) {
                    slides[slideIndex].classList.add("displaySlide");
                    intervalId = setInterval(nextSlide, 5000);
                }
            }
            function showSlide(index) {
                if (index >= slides.length) {
                    slideIndex = 0;
                } else if (index < 0n) {
                    slideIndex = slides.length - 1;
                }

                slides.forEach((slide) => {
                    slide.classList.remove("displaySlide");
                });
                slides[slideIndex].classList.add("displaySlide");
            }
            function prevSlide() {
                clearInterval(intervalId);
                slideIndex--;
                showSlide(slideIndex);
            }
            function nextSlide() {
                clearInterval(intervalId);
                slideIndex++;
                showSlide(slideIndex);
            }
        </script>
    </body>
</html>
```