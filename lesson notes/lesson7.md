# File Handling: Reading/Writing Files and Storing API Data (CSV, JSON)

In this lesson, we'll cover how to handle files in Python. We'll learn how to read and write plain text files, as well as how to store API data in CSV and JSON formats. This guide follows the style of previous lessons.

## 1. Reading and Writing Text Files

Working with text files is a common task in Python. Use built-in functions to open, read, and write files.

```python
# Reading a file
with open("example.txt", "r") as file:
    content = file.read()
    print(content)

# Writing to a file
with open("output.txt", "w") as file:
    file.write("Hello, World!")
```

### Explanation:
- Use the built-in open() function with modes "r" for reading and "w" for writing.
- Reading loads the entire content at once, while writing replaces the existing content.

## 2. Storing API Data in CSV Format

CSV (Comma-Separated Values) is a common format for tabular data. The csv module in Python can help you write and read CSV files.

```python
import csv

# Example API data as a list of dictionaries
api_data = [
    {"city": "New York", "temp": 22, "condition": "Sunny"},
    {"city": "London", "temp": 16, "condition": "Cloudy"}
]

# Writing API data to a CSV file
with open("api_data.csv", "w", newline="") as csvfile:
    fieldnames = ["city", "temp", "condition"]
    writer = csv.DictWriter(csvfile, fieldnames=fieldnames)
    
    writer.writeheader()
    for row in api_data:
        writer.writerow(row)
```

### Explanation:
- Use csv.DictWriter for writing dictionaries to CSV files.
- Writing a header ensures the CSV file is self-describing.

## 3. Storing API Data in JSON Format

JSON is a widely-used format for data exchange. The json module allows you to serialize Python objects to JSON strings and write them directly to files.

```python
import json

# Example API response data
api_data = {
    "location": "New York",
    "weather": {
        "temp": 22,
        "condition": "Sunny",
        "humidity": 65
    }
}

# Writing API data to a JSON file
with open("api_data.json", "w") as jsonfile:
    json.dump(api_data, jsonfile, indent=4)
    
# Reading the JSON data back
with open("api_data.json", "r") as jsonfile:
    data = json.load(jsonfile)
    print(data)
```

### Explanation:
- json.dump writes the Python dictionary to a file with pretty-printing using the indent parameter.
- json.load reads the JSON file and converts it back into a Python dictionary.

## Summary

- We learned how to read and write text files using Python's built-in functions.
- We explained how to store API data in both CSV and JSON formats.
- Code examples illustrate simple, practical usages for file handling.

Feel free to extend these examples based on your project requirements.
