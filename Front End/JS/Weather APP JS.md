---
Created: 2025-06-25T17:31
---
> [!important]
> 
> ### API Used

==[https://openweathermap.org/api/geocoding-api](https://openweathermap.org/api/geocoding-api)==

==[https://openweathermap.org/current](https://openweathermap.org/current)==

==[https://openweathermap.org/weather-conditions](https://openweathermap.org/weather-conditions)==

  

```JavaScript
const weatherForm = document.querySelector(".weatherForm");
const cityInput = document.querySelector(".cityInput");
const card = document.querySelector(".card");
const apiKey = "33b874a3a24ee87742818c29aacff823";

weatherForm.addEventListener("submit", async (event) => {
    event.preventDefault();
    const city = cityInput.value;
    if (city) {
        try {
            const weatherData = await getWeatherData(city);
            displayWeatherInfo(weatherData);
        } catch (error) {
            console.error(`Error: ${error}`);
            displayError(error);
        }
    } else {
        displayError(`Please Enter a City`);
    }
});

async function getWeatherData(city) {
    const geoCoordinateAPI = `http://api.openweathermap.org/geo/1.0/direct?q=${city}&limit=20&appid=${apiKey}`;
    const cityData = await fetch(geoCoordinateAPI);
    const parsedCityData = await cityData.json();

    if (parsedCityData.length === 0) {
        throw new Error(`Could not fetch City Data`);
    }

    const cityAPI = `https://api.openweathermap.org/data/2.5/weather?lat=${parsedCityData[0].lat}&lon=${parsedCityData[0].lon}&appid=${apiKey}`;
    const cityWeather = await fetch(cityAPI);

    return await cityWeather.json();
}
function displayWeatherInfo(data) {
    const {
        name: city,
        main: { temp, humidity },
        weather: [{ description, id }],
    } = data;

    card.textContent = "";
    card.style.display = "flex";

    const cityDisplay = document.createElement("h1");
    const tempDisplay = document.createElement("p");
    const humidityDisplay = document.createElement("p");
    const descriptionDisplay = document.createElement("p");
    const weatherEmoji = document.createElement("p");

    cityDisplay.textContent = city;
    tempDisplay.textContent = `${(temp - 273.15).toFixed(2)}°C`;
    humidityDisplay.textContent = `Humidity ${humidity}%`;
    descriptionDisplay.textContent = description;
    weatherEmoji.textContent = getWeatherEmoji(id);

    cityDisplay.classList.add("cityDisplay");
    tempDisplay.classList.add("tempDisplay");
    humidityDisplay.classList.add("humidityDisplay");
    descriptionDisplay.classList.add("descriptionDisplay");
    weatherEmoji.classList.add("weatherEmoji");

    card.appendChild(cityDisplay);
    card.appendChild(tempDisplay);
    card.appendChild(humidityDisplay);
    card.appendChild(descriptionDisplay);
    card.appendChild(weatherEmoji);
}

function getWeatherEmoji(weatherId) {
    switch (true) {
        case weatherId >= 200 && weatherId < 300:
            return "⛈️";
            break;
        case weatherId >= 300 && weatherId < 400:
            return "🌧️";
            break;
        case weatherId >= 500 && weatherId < 600:
            return "🌧️";
            break;
        case weatherId >= 600 && weatherId < 700:
            return "🌨️";
            break;
        case weatherId >= 700 && weatherId < 800:
            return "🌫️";
            break;
        case weatherId === 800:
            return "☀️";
            break;
        case weatherId >= 801 && weatherId < 810:
            return "☁️";
            break;
        default:
            return "❓";
            break;
    }
}

function displayError(message) {
    const errorDisplay = document.createElement("p");
    errorDisplay.textContent = message;
    errorDisplay.classList.add("errorDisplay");
    card.textContent = "";
    card.style.display = "flex";
    card.appendChild(errorDisplay);
}
```

  

```HTML
<!DOCTYPE html>
<html lang="en">
    <head>
        <meta charset="UTF-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0" />
        <link rel="stylesheet" href="WeatherApp.css" />
        <title>Weather App</title>
    </head>
    <body>
        <form action="" class="weatherForm">
            <input
                type="text"
                name=""
                id=""
                class="cityInput"
                placeholder="Enter City"
                value="Manila"
            />
            <button type="submit">Get Weather</button>
        </form>

        <div class="card" style="display: none">
            <!-- <h1 class="cityDisplay">Miami</h1>
            <p class="tempDisplay">90°F</p>
            <p class="humidityDisplay">Humidity: 75%</p>
            <p class="descriptionDisplay">Clear Skies</p>
            <p class="weatherEmoji">☀️</p>
            <p class="errorDisplay">Please enter a city</p> -->
        </div>

        <script src="WeatherApp.js"></script>
    </body>
</html>
```

  

```CSS
body {
    font-family: Arial, sans-serif, sans-serif;
    background-color: hsl(0, 0%, 95%);
    margin: 0;
    display: flex;
    flex-direction: column;
    align-items: center;
}
.weatherForm {
    margin: 20px;
}
.cityInput {
    padding: 10px;
    font-size: 2rem;
    font-weight: bold;
    border: 2px solid hsl(0, 0%, 20%, 0.3);
    border-radius: 15px;
    margin: 10px;
    width: 300px;
}
button[type="submit"] {
    padding: 10px 20px;
    font-weight: bold;
    font-size: 2rem;
    background-color: hsl(122, 100%, 50%);
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}
button[type="submit"]:hover {
    background-color: hsl(122, 100%, 40%);
}
.card {
    background: linear-gradient(
        180deg,
        hsl(120, 100%, 50%),
        hsl(40, 100%, 60%)
    );
    padding: 50px;
    box-shadow: 2px 2px 5px hsl(0, 0%, 50%);
    min-width: 300px;
    display: flex;
    flex-direction: column;
    align-items: center;
    border-radius: 15px;
}
h1 {
    margin-top: 0;
    margin-bottom: 25px;
}
p {
    font-size: 1.5rem;
    margin: 5px 0;
}
.cityDisplay,
.tempDisplay {
    font-size: 3.5rem;
    font-weight: bold;
    color: hsl(0, 0%, 0%, 0.75);
    margin-bottom: 25px;
}
.humidityDisplay {
    font-weight: bold;
    margin-bottom: 25px;
}
.descriptionDisplay {
    font-style: italic;
    font-weight: bold;
    font-size: 2rem;
}

.weatherEmoji {
    margin: 0;
    font-size: 7.5rem;
}
.errorDisplay {
    font-size: 2.5rem;
    font-weight: bold;
    color: hsl(0, 0%, 0%, 0.75);
}
```