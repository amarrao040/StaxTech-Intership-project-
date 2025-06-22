# StaxTech-Intership-project-


Project 4 :Weather App/Website

A basic weather application project typically involves creating a user interface using HTML, CSS, and 

JavaScript to display weather information for a specific location.



🔧 Tech Stack

Frontend: HTML, CSS, JavaScript

API: OpenWeatherMap API (or any other free weather API)

(Optional): React.js or Bootstrap for advanced UI

(Optional Backend): Node.js/Express.js if you want to store search history or build a more complete system



---

🧱 Basic Features

1. Search by City Name


2. Display:

City name

Temperature (°C/°F)

Weather condition (e.g., Clear, Rainy, etc.)

Humidity

Wind speed

Weather icon



3. Responsive Design




---

🧑‍💻 Step-by-Step Guide

1. HTML (Structure)

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Weather App</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <div class="weather-app">
    <h1>Weather App</h1>
    <input type="text" id="cityInput" placeholder="Enter city name" />
    <button onclick="getWeather()">Get Weather</button>
    <div id="weatherResult"></div>
  </div>
  <script src="script.js"></script>
</body>
</html>

2. CSS (Style)

body {
  font-family: Arial, sans-serif;
  background: #87ceeb;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

.weather-app {
  text-align: center;
  background: white;
  padding: 30px;
  border-radius: 10px;
  box-shadow: 0 5px 15px rgba(0,0,0,0.3);
}

input {
  padding: 10px;
  margin: 10px;
  width: 200px;
}

button {
  padding: 10px 20px;
  background: #007bff;
  color: white;
  border: none;
  cursor: pointer;
}

#weatherResult {
  margin-top: 20px;
}

3. JavaScript (Functionality)

async function getWeather() {
  const city = document.getElementById('cityInput').value;
  const apiKey = 'your_openweathermap_api_key'; // Replace with your API key
  const url = `https://api.openweathermap.org/data/2.5/weather?q=${city}&appid=${apiKey}&units=metric`;

  try {
    const response = await fetch(url);
    if (!response.ok) throw new Error("City not found");

    const data = await response.json();
    document.getElementById('weatherResult').innerHTML = `
      <h2>${data.name}, ${data.sys.country}</h2>
      <p><strong>Temperature:</strong> ${data.main.temp}°C</p>
      <p><strong>Condition:</strong> ${data.weather[0].main}</p>
      <p><strong>Humidity:</strong> ${data.main.humidity}%</p>
      <p><strong>Wind Speed:</strong> ${data.wind.speed} m/s</p>
      <img src="http://openweathermap.org/img/wn/${data.weather[0].icon}@2x.png" />
    `;
  } catch (error) {
    document.getElementById('weatherResult').innerHTML = `<p>Error: ${error.message}</p>`;
  }
}


---

🌍 Where to Get API Key

Sign up at https://openweathermap.org/api

Get a free API key

Replace your_openweathermap_api_key with your actual API key in the code above



---

🌟 Optional Enhancements

Add background image based on weather

Save search history

Use localStorage to remember last search

Add dark/light mode toggle

Show 5-day forecast using a different endpoint



---






