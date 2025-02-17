# Introduction to Python Programming

## What is Python?

Python is a high-level programming language designed with a philosophy that emphasizes code readability. Think of Python as a versatile tool that helps you communicate with computers in a way that both humans and machines can understand easily.

Python stands out because it is:
- Object-oriented: It organizes code into reusable pieces called objects
- Open-source: Free to use and modify, supported by a global community
- High-level: Takes care of many complex details automatically
- Interpreted: Executes code line by line, making it easier to test and debug

## Why Choose Python?

Python has become one of the most popular programming languages, especially for beginners and data scientists, because:

1. Easy to Learn: Its syntax resembles natural English, making it intuitive to read and write
2. Versatile: Used in web development, data science, artificial intelligence, and more
3. Rich Ecosystem: Has thousands of pre-built packages for various tasks
4. Strong Community: Large community providing support and resources
5. Industry Demand: Highly sought after in job markets

## Getting Started with Python

### Installation

You can install Python in several ways:

1. Official Website (python.org):
   - Visit python.org/downloads
   - Download the latest stable version
   - Run the installer with "Add Python to PATH" checked

2. Microsoft Store (Windows):
   - Search for "Python"
   - Install the official Python package
   - Automatically handles PATH settings

3. Package Managers:
   - Windows: Use Chocolatey
   - macOS: Use Homebrew
   - Linux: Usually pre-installed

### Development Environments

Choose the environment that best suits your needs:

1. Python Shell:
   - Basic interactive environment
   - Good for quick testing and learning
   - Opens by typing `python` in terminal

2. IDLE:
   - Comes with Python installation
   - Simple interface with basic features
   - Good for beginners

3. Visual Studio Code:
   - Feature-rich editor
   - Excellent Python support
   - Debugging capabilities
   - Git integration

4. Online Editors:
   - Google Colab
   - Replit
   - JupyterLab

## Python Files

Python uses two main types of files:

1. .py files:
   - Standard Python script files
   - Execute from start to finish
   - Used for most Python programs
   Example:
   ```python
   # hello.py
   print("Hello, World!")
   ```

2. .ipynb files:
   - Jupyter Notebook files
   - Mix code and documentation
   - Great for data science
   - Run code in cells

## Basic Data Types

Python has several fundamental data types that help us work with different kinds of information:

### Numbers

1. Integers (int):
   ```python
   age = 25
   temperature = -10
   population = 1000000
   ```

2. Floating-point numbers (float):
   ```python
   price = 19.99
   pi = 3.14159
   temperature = -3.8
   ```

### Text

Strings (str) store text:
```python
name = "Alice"
message = 'Hello, World!'
address = """123 Main Street
New York, NY 10001"""
```

### Boolean

Boolean (bool) represents True or False:
```python
is_student = True
has_license = False
is_valid = 5 > 3  # True
```

## Basic Input/Output

### Printing Output

The `print()` function displays information:
```python
name = "Alice"
age = 25

# Simple printing
print("Hello, World!")

# Printing variables
print(name)

# Printing multiple items
print("Name:", name, "Age:", age)

# Using f-strings (formatted strings)
print(f"{name} is {age} years old")
```

### Getting Input

The `input()` function reads user input:
```python
# Basic input
name = input("Enter your name: ")

# Converting input to numbers
age = int(input("Enter your age: "))
height = float(input("Enter your height in meters: "))
```

## Operators

### Arithmetic Operators

```python
a = 10
b = 3

addition = a + b        # 13
subtraction = a - b     # 7
multiplication = a * b  # 30
division = a / b        # 3.3333...
floor_division = a // b # 3: calculate a / b without considering decimal points
modulus = a % b        # 1: the remainder of a // b
exponent = a ** b      # 1000
```

### Assignment Operators

```python
x = 5      # Basic assignment
x += 3     # Same as: x = x + 3
x -= 2     # Same as: x = x - 2
x *= 4     # Same as: x = x * 4
x /= 2     # Same as: x = x / 2
x %= 3     # Same as: x = x % 3
x **= 2    # Same as: x = x ** 2
```

## Practice Exercises

### Exercise 1: Temperature Converter
Create a program that converts Celsius to Fahrenheit.

```python
# Get temperature in Celsius
celsius = float(input("Enter temperature in Celsius: "))

# Convert to Fahrenheit
# Formula: (C × 9/5) + 32 = F
fahrenheit = (celsius * 9/5) + 32

# Print result
print(f"{celsius}°C is equal to {fahrenheit}°F")
```

### Exercise 2: Circle Calculator
Calculate the area and circumference of a circle.

```python
# Import pi from math module
from math import pi

# Get radius from user
radius = float(input("Enter the radius of the circle: "))

# Calculate area and circumference
area = pi * radius ** 2
circumference = 2 * pi * radius

# Print results (rounded to 2 decimal places)
print(f"Area: {round(area, 2)} square units")
print(f"Circumference: {round(circumference, 2)} units")
```

### Exercise 3: Simple Interest Calculator
Calculate simple interest given principal, rate, and time.

```python
# Get input from user
principal = float(input("Enter principal amount: "))
rate = float(input("Enter annual interest rate (%): "))
time = float(input("Enter time in years: "))

# Calculate simple interest
# Formula: Simple Interest = (P × R × T) / 100
interest = (principal * rate * time) / 100

# Calculate total amount
total = principal + interest

# Print results
print(f"Principal Amount: ${principal}")
print(f"Interest Rate: {rate}%")
print(f"Time Period: {time} years")
print(f"Interest Earned: ${round(interest, 2)}")
print(f"Total Amount: ${round(total, 2)}")
```

### Exercise 4: Grade Calculator
Calculate the average grade and determine the letter grade.

```python
# Get three test scores
test1 = float(input("Enter score for test 1: "))
test2 = float(input("Enter score for test 2: "))
test3 = float(input("Enter score for test 3: "))

# Calculate average
average = (test1 + test2 + test3) / 3

# Determine letter grade
if average >= 90:
    grade = 'A'
elif average >= 80:
    grade = 'B'
elif average >= 70:
    grade = 'C'
elif average >= 60:
    grade = 'D'
else:
    grade = 'F'

# Print results
print(f"Average Score: {round(average, 2)}")
print(f"Letter Grade: {grade}")
```

## Practice Problems

Try solving these problems to test your understanding:

1. **Tip Calculator**
   - Get the bill amount and tip percentage
   - Calculate the tip and total amount
   - Print both the tip and final total

2. **Triangle Area Calculator**
   - Get the base and height of a triangle
   - Calculate its area
   - Print the result

3. **Time Converter**
   - Get number of minutes
   - Convert to hours and minutes
   - Print in format "X hours and Y minutes"

4. **BMI Calculator**
   - Get weight (in kg) and height (in meters)
   - Calculate BMI (weight / height²)
   - Print BMI with appropriate category

Remember:
- Test your code with different inputs
- Handle decimal numbers appropriately
- Use clear variable names
- Add comments to explain your logic
- Format output to be user-friendly

## Additional Resources

1. Online Learning:
   - Python.org Tutorial
   - W3Schools Python Tutorial
   - Codecademy Python Course

2. Practice Platforms:
   - HackerRank
   - LeetCode
   - Python Challenge

3. Documentation:
   - Official Python Documentation
   - Python Quick Reference Guide