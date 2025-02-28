# API Calls: Connecting to the Web

APIs (Application Programming Interfaces) enable your program to communicate with external services by exchanging data over the web. In this lesson, you'll learn not only how to call APIs with Python's `requests` library but also how to handle errors and understand the basics behind HTTP communication.

## Overview of API Calls

- What is an API?  
  A set of protocols that allows software to communicate over a network.
- HTTP Methods:  
  GET, POST, PUT, DELETE are used for different operations.
- Endpoints and URLs:  
  Specific addresses to access data.
- Status Codes:  
  E.g., 200 (OK), 404 (Not Found), and 500 (Server Error).
- Headers and Parameters:  
  Used to pass additional information with requests.
- Libraries:  
  The `requests` package simplifies sending HTTP requests.

## Example 1: Free Weather API

Fetch current weather data using a free API ([WeatherAPI](https://www.weatherapi.com/docs/)).

```python
import requests

API_KEY = 'YOUR_API_KEY '
def get_weather(city):
    url = f"http://api.weatherapi.com/v1/current.json?key={API_KEY}&q={city}&aqi=no"
    
    response = requests.get(url)
    data = response.json()
    
    if 'error' in data:
        return f"Error: {data['error']['message']}"
    
    location = data['location']['name']
    region = data['location']['region']
    country = data['location']['country']
    temp_c = data['current']['temp_c']
    condition = data['current']['condition']['text']
    humidity = data['current']['humidity']
    wind_kph = data['current']['wind_kph']
    feelslike_c = data['current']['feelslike_c']
    
    return (
        f"Weather in {location}, {region}, {country}:\n"
        f"Condition: {condition}\n"
        f"Temperature: {temp_c}°C (Feels like {feelslike_c}°C)\n"
        f"Humidity: {humidity}%\n"
        f"Wind Speed: {wind_kph} km/h"
    )

# Example usage
city = input("Enter city name: ").strip()
print(get_weather(city))
```

### Explanation:
- The API endpoint uses WeatherAPI.
- The function get_weather does all the logic for fetching and processing the data.

## Example 2: Free Books API

Retrieve book information from a free API (e.g., [Open Library](https://openlibrary.org/dev/docs/api/books)). This example demonstrates similar error handling and JSON processing.

```python
import requests

isbn = '0451526538'
url = f"https://openlibrary.org/api/books?bibkeys=ISBN:{isbn}&format=json&jscmd=data"

try:
    response = requests.get(url)
    response.raise_for_status()
    book_data = response.json()
    print("Book Data:", book_data)
except requests.exceptions.HTTPError as http_err:
    print(f"HTTP error occurred: {http_err}")
except Exception as err:
    print(f"Unexpected error: {err}")
```

### Explanation:
- The API call uses a query parameter (ISBN) to retrieve book data.
- Error handling is applied similarly to ensure robust communication.
- The returned JSON data is processed and outputted.

# JSON: A Lightweight Data Format

JSON (JavaScript Object Notation) is a simple, human-readable data format widely used for data exchange in APIs.

## Key Concepts:
- Represents data as key-value pairs.
- Uses arrays and nested structures.
- Easy to serialize (convert from Python objects) and deserialize (convert to Python objects).

## Using JSON in Python

```python
import json

# Serialization: Convert a Python dictionary to a JSON string.
data = {"name": "Alice", "age": 30, "active": True}
json_string = json.dumps(data, indent=4)  # 'indent' is used for pretty printing.
print("Serialized JSON:")
print(json_string)

# Deserialization: Convert a JSON string back into a Python dictionary.
data_back = json.loads(json_string)
print("Deserialized Python dict:")
print(data_back)
```

### Explanation:
- Serialization transforms Python objects into JSON.
- Deserialization converts JSON back to Python data types.
- Pretty-printing (with `indent=4`) improves readability.

# Try/Except: Handling Errors Gracefully

Python's try/except blocks allow you to handle exceptions without causing your program to crash. This section explains the syntax and common use cases.

## Basic Syntax

```python
try:
    # ...attempt code...
    result = 10 / 0  # This will trigger a ZeroDivisionError.
except ZeroDivisionError:
    print("Error: Cannot divide by zero.")
```

### Detailed Explanation:
- The "try" block includes code that might raise an exception.
- Specific exceptions (like ZeroDivisionError) are caught in the "except" block.
- This mechanism prevents the program from crashing and allows for alternative actions.

## Common Use Cases:
- Validating user input.
- Managing network failures.
- Handling file I/O errors.
- Safely making API calls.

## Detailed Example: Combining API Call with Error Handling

```python
import requests

try:
    response = requests.get("https://api.example.com/data")
    response.raise_for_status()  # Validates the HTTP response.
    data = response.json()
except requests.exceptions.HTTPError as http_err:
    print(f"HTTP error occurred: {http_err}")
except requests.exceptions.ConnectionError:
    print("Error: Could not connect to the API.")
except ValueError:
    print("Error: Failed to decode JSON.")
except Exception as err:
    print(f"An unexpected error occurred: {err}")
else:
    print("Successfully fetched data:", data)
finally:
    print("API request attempt finished.")
```

### Explanation:
- The try block attempts a network request.
- Multiple except blocks handle specific errors, ensuring clarity in error reporting.
- The final block runs regardless of exceptions, making it ideal for cleanup actions.
