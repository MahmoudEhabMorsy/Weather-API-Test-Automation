# Weather API Testing Project

Automated API testing project built using Postman and GitHub Actions for validating WeatherAPI endpoints.

## Project Overview

This project contains automated API tests for multiple weather-related endpoints provided by WeatherAPI.  
The collection validates different query methods, forecast functionality, response structures, and dynamic data handling.

The project is integrated with GitHub Actions to enable automated CI test execution on every push or pull request.

---

## Features

- Current Weather API Testing
- Forecast Weather API Testing
- Collection Runner Data-Driven Testing
- Dynamic Date Validation
- Automated Assertions
- CI/CD Integration using GitHub Actions

---

## Technologies Used

- Postman
- Newman
- GitHub Actions
- JavaScript
- CSV Data Files

---

## Test Coverage

### Current Weather Tests

Validation using:
- City Name
- Coordinates
- ZIP Code
- METAR Code
- IATA Code
- IP Address
- Country Name

### Forecast Weather Tests

Validation for:
- Forecast for specific hours
- Forecast date validation
- Forecast day count validation
- Dynamic current date handling

### Collection Runner Tests

Data-driven testing using CSV files for:
- Multiple cities
- Multiple forecast dates
- Multiple forecast hours

---

## Assertions Included

- Status code validation
- Response body validation
- Forecast existence validation
- Forecast length validation
- Timezone validation
- Dynamic date validation

---

## CI/CD Integration

GitHub Actions is configured to automatically:

- Install Newman
- Execute the Postman collection
- Generate test results
- Validate all API requests on every push

---

## Project Structure

```bash
.
├── WeatherApi.json
├── data/
│   └── Cities.csv
├── .github/
│   └── workflows/
│       └── main.yml
└── README.md
```

---

## Running Tests Locally

### Using Postman

1. Import the collection
2. Configure environment variables
3. Add your WeatherAPI key to Postman Vault
4. Run the collection

### Using Newman

Install Newman:

```bash
npm install -g newman
```

Run the collection:

```bash
newman run "WeatherApi.json"
```

Run with iteration data:

```bash
newman run "WeatherApi.json" -d Cities.csv
```

---

## Environment Variables

| Variable | Description |
|---|---|
| baseUrl | WeatherAPI base URL |
| apiKey | WeatherAPI API key |
| cityName | City used for testing |
| coords | Coordinates for testing |
| zipCode | ZIP code for testing |

---

## Example Validations

```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

const todayDate = new Date().toISOString().split('T')[0];

pm.test("Forecast date matches today", function () {
    pm.expect(pm.response.json().forecast.forecastday[0].date).to.eql(todayDate);
});
```

---

## GitHub Actions

The workflow automatically runs the Postman collection using Newman after every push.

This ensures:
- Early bug detection
- Continuous validation
- Reliable API behavior

---

## Author

Mahmoud Ehab
