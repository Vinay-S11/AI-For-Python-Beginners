## 🌈 Lesson 5: APIs to Get Data from the Web

### ✨ Overview:
In this lesson, you will learn how to fetch real-time weather data from a web service (OpenWeatherMap) using the requests library and how to display the extracted data in a human-readable format.

Content:

#### 1. Importing Libraries and Setting up API Key
Use dotenv to securely store and access your API key:
```python
import os
import requests
from aisetup import print_llm_response
from dotenv import load_dotenv
```

#### 2. Setting Coordinates for Weather Request
Specify the location using latitude and longitude:
```python
lat = 37.4419  # Palo Alto, CA
lon = -122.1430
```

#### 3. Making the API Request
Fetch the weather data using the OpenWeatherMap API:
```python
url = f"https://api.openweathermap.org/data/2.5/forecast?units=metric&cnt=1&lat={lat}&lon={lon}&appid={api_key}"
response = requests.get(url)
```

#### 4. Extracting Relevant Information
Parse the JSON response to extract specific weather details:
```python
data = response.json()
temperature = data['list'][0]['main']['temp']
description = data['list'][0]['weather'][0]['description']
wind_speed = data['list'][0]['wind']['speed']
```

#### 5. Displaying Weather Information
Display the extracted data in a clear, readable format:
```python
print(f"Temperature: {temperature}")
print(f"Weather Description: {description}")
print(f"Wind Speed: {wind_speed}")
```

#### 6. Creating a Detailed Weather Report
Combine the information into a structured weather report:
```python
weather_string = f"""The temperature is {temperature}°C.
It is currently {description},
with a wind speed of {wind_speed}m/s.
"""
print(weather_string)
```

#### 7. Using LLMs for Outfit Suggestions
Query an LLM to suggest an appropriate outfit based on the weather:
```python
prompt = f"""Based on the following weather, suggest an appropriate outdoor outfit.

Forecast: {weather_string}
"""
print_llm_response(prompt)
```

✅ Summary:
  - In this lesson, you learned how to:
  - Fetch real-time weather data from OpenWeatherMap API
  - Parse and extract useful data from the JSON response
  - Format and display the weather data
  - Use LLMs for generating outfit recommendations based on the weather
