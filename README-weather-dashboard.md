# Live Weather Dashboard

## Project Overview

This project is a responsive **real-time Weather Dashboard** built using HTML, CSS, and modern JavaScript.

It demonstrates asynchronous JavaScript, RESTful API communication, JSON processing, error handling, and dynamic DOM rendering.

## Key Features

- Search weather by city name
- Fetch live weather data using the modern `fetch()` API
- Use `async/await` for asynchronous operations
- Process JSON responses
- Display temperature
- Display humidity
- Display wind speed
- Display weather condition
- Display feels-like temperature
- Display wind direction
- Handle invalid city names
- Handle failed network/API requests
- Dynamically update the dashboard
- Responsive design for desktop and mobile
- No API key required

## APIs Used

This project uses the public **Open-Meteo** REST APIs.

### 1. Geocoding API

The city name is first converted into latitude and longitude.

```text
https://geocoding-api.open-meteo.com/v1/search
```

### 2. Weather API

The latitude and longitude are then used to request current weather information.

```text
https://api.open-meteo.com/v1/forecast
```

No registration or API key is required.

## How the Application Works

### Step 1 — User enters a city

Example:

```text
Chennai
```

### Step 2 — Geocoding request

JavaScript sends the city name to the geocoding REST API.

The response contains data such as:

```json
{
  "name": "Chennai",
  "latitude": 13.0878,
  "longitude": 80.2785,
  "country": "India"
}
```

### Step 3 — Weather request

The latitude and longitude are sent to the weather API.

The API returns a nested JSON object containing the current weather.

### Step 4 — JSON processing

The application extracts:

- Temperature
- Relative humidity
- Apparent temperature
- Weather code
- Wind speed
- Wind direction

### Step 5 — Dynamic rendering

The extracted values are inserted into the HTML dashboard using DOM manipulation.

## Async/Await

The main asynchronous operation is:

```javascript
async function searchWeather(city) {
  const cityData = await getCityCoordinates(city);
  const weatherData = await getWeather(
    cityData.latitude,
    cityData.longitude
  );

  renderWeather(cityData, weatherData);
}
```

This makes the API flow easier to read and understand.

## Error Handling

The project uses `try...catch...finally`.

```javascript
try {
  // API requests
} catch (error) {
  // Display error message
} finally {
  // Stop loading state
}
```

Errors handled include:

- City not found
- API/network failure
- Empty search input
- Failed HTTP response

## Expected Outcome

The completed application provides a dynamic weather dashboard where the user can enter a city and receive current weather information.

Example:

```text
Chennai, India

Temperature: 30 °C
Humidity: 70%
Wind Speed: 12 km/h
Weather: Partly cloudy
Feels Like: 34 °C
Wind Direction: E (90°)
```

The exact values change according to the live API response.

## How to Run

1. Download `weather-dashboard.html`.
2. Open the file in a modern web browser such as Chrome, Edge, or Firefox.
3. Make sure you have an internet connection.
4. The dashboard initially loads weather for Chennai.
5. Enter another city and click **Search**.

No Node.js, server, package installation, or API key is required.

## Project Structure

```text
weather-dashboard-project/
├── weather-dashboard.html
└── README.md
```

## Technologies Used

- HTML5
- CSS3
- JavaScript ES6+
- Fetch API
- Async/Await
- REST APIs
- JSON
- DOM Manipulation
- Error Handling
- Responsive Web Design

## Learning Outcomes

After completing this task, you should understand:

1. What a REST API is.
2. How to make API requests with `fetch()`.
3. How `async/await` handles asynchronous operations.
4. How to process JSON responses.
5. How to use nested JSON data.
6. How to handle API and network errors.
7. How to dynamically update HTML using JavaScript.
8. How a city name can be converted into geographic coordinates.
9. How multiple API requests can work together in one application.

## API Attribution

Weather data is provided by Open-Meteo:

```text
https://open-meteo.com/
```
