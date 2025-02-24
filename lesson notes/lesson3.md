# Introduction to Functions

Think of functions as reusable recipes in a cookbook. Just as a recipe provides steps to create a dish, a function provides instructions to perform a specific task. Functions help us:

- Avoid repeating code
- Organize our programs
- Break down complex problems into smaller parts
- Share and reuse solutions

# Your First Function

Let's start with the simplest possible function:

```python
def say_hello():
    print("Hello, World!")

# Using the function
say_hello()    # Output: Hello, World!
```

Every function has these parts:
1. `def` keyword - tells Python we're creating a function
2. Function name - what we call our function
3. Parentheses `()` - can hold inputs
4. Colon `:` - marks the start of function body
5. Indented code - the actual instructions

# Making Functions More Useful with Parameters

Parameters make our functions flexible by accepting different inputs:

```python
def greet(name):
    print(f"Hello, {name}!")

# Try it with different names
greet("Alice")     # Output: Hello, Alice!
greet("Bob")       # Output: Hello, Bob!
```

## Multiple Parameters

Functions can take several inputs:

```python
def calculate_total(price, tax_rate):
    tax = price * tax_rate
    total = price + tax
    print(f"Price: ${price}")
    print(f"Tax: ${tax:.2f}")
    print(f"Total: ${total:.2f}")

# Calculate total with different values
calculate_total(100, 0.08)    # 8% tax on $100
calculate_total(50, 0.05)     # 5% tax on $50
```

<details>
<summary>Add later:</summary>

arguments and keyword arguments:
```python
def func1(*args, **kwargs):
    print(args)
    print(kwargs)

func1(12, 13, 14, kw1=1, kw2=2, kw3=3)

# Output:
# (12, 13, 14)
# {"kw1" : 1, "kw2" : 2, "kw3" : 3}
```
</details>

# Returning Values

Functions can give back results using `return`:

```python
def double(number):
    return number * 2

# Using the returned value
result = double(5)    # result = 10
print(result)         # Output: 10

# Chain the result into another calculation
final = double(result)   # final = 20
```

## Functions with Multiple Returns

```python
def get_user_info(name, age):
    greeting = f"Hello {name}"
    can_vote = age >= 18
    years_until_vote = 18 - age if age < 18 else 0
    return greeting, can_vote, years_until_vote

# Using multiple returns
message, voting_status, years = get_user_info("Tom", 15)
print(message)              # Output: Hello Tom
print(voting_status)        # Output: False
print(years)               # Output: 3
```

# Default Parameters

Make parameters optional by providing default values:

```python
def make_sandwich(main="cheese", bread="white"):
    return f"A {main} sandwich on {bread} bread"

print(make_sandwich())                    # Output: A cheese sandwich on white bread
print(make_sandwich("turkey"))            # Output: A turkey sandwich on white bread
print(make_sandwich("tuna", "wheat"))     # Output: A tuna sandwich on wheat bread
```
# Lambda Functions
Lambda functions are concise, anonymous functions useful for simple operations. For example:

```python
# A lambda function to square a number
square = lambda x: x * x
print(square(5))  # Output: 25
```
# Functions Working Together

Functions can work like a team, each doing a specific job:

```python
def get_temperature():
    """Get temperature from user"""
    return float(input("Enter temperature in Celsius: "))

def convert_to_fahrenheit(celsius):
    """Convert Celsius to Fahrenheit"""
    return (celsius * 9/5) + 32

def describe_temperature(fahrenheit):
    """Describe the temperature"""
    if fahrenheit > 90:
        return "It's very hot!"
    elif fahrenheit > 70:
        return "It's warm."
    elif fahrenheit > 50:
        return "It's cool."
    else:
        return "It's cold!"

def weather_report():
    """Complete weather report using all functions"""
    celsius = get_temperature()
    fahrenheit = convert_to_fahrenheit(celsius)
    description = describe_temperature(fahrenheit)
    print(f"{celsius}°C is {fahrenheit}°F - {description}")

# Run the complete program
weather_report()
```

# Introduction to Recursion

Recursion is when a function calls itself. It's like a Russian nesting doll - each doll contains a smaller version of itself.

## Simple Countdown Example

```python
def countdown(n):
    """Count down from n to 1"""
    # Base case - when to stop
    if n <= 0:
        print("Blastoff!")
        return
    
    # Current step
    print(n)
    
    # Recursive call - countdown with a smaller number
    countdown(n - 1)

# Try it
countdown(5)
# Output:
# 5
# 4
# 3
# 2
# 1
# Blastoff!
```

## Factorial Calculator

Calculates n! (n × (n-1) × (n-2) × ... × 1):

```python
def factorial(n):
    """Calculate n factorial"""
    # Base cases
    if n < 0:
        return "Cannot calculate factorial of negative number"
    if n == 0 or n == 1:
        return 1
    
    # Recursive case
    return n * factorial(n - 1)

# How factorial(4) works:
# factorial(4)
# → 4 * factorial(3)
#     → 3 * factorial(2)
#         → 2 * factorial(1)
#             → 1
# Then calculates back:
# 1 → 2 * 1 = 2 → 3 * 2 = 6 → 4 * 6 = 24
```

## Directory Tree Explorer

A practical example of recursion - exploring files and folders:

```python
def explore_directory(path, level=0):
    """Print all files and folders in a directory"""
    import os
    
    # Print current location
    indent = "  " * level
    print(f"{indent}📂 {os.path.basename(path)}")
    
    # Try to list directory contents
    try:
        # Get all items in directory
        items = os.listdir(path)
        
        # Process each item
        for item in items:
            item_path = os.path.join(path, item)
            
            # If it's a file, print it
            if os.path.isfile(item_path):
                print(f"{indent}  📄 {item}")
            # If it's a directory, explore it (recursion!)
            elif os.path.isdir(item_path):
                explore_directory(item_path, level + 1)
                
    except PermissionError:
        print(f"{indent}  ⚠️ Permission denied")
    except Exception as e:
        print(f"{indent}  ❌ Error: {e}")

# Example usage:
# explore_directory("C:/Users/Documents")
```

# Practical Exercises

## Exercise 1: Temperature Converter

```python
def convert_temperature():
    """Convert between Celsius and Fahrenheit"""
    # Get temperature and unit
    temp = float(input("Enter temperature: "))
    unit = input("Enter unit (C/F): ").upper()
    
    # Convert and return result
    if unit == "C":
        result = (temp * 9/5) + 32
        return f"{temp}°C = {result}°F"
    elif unit == "F":
        result = (temp - 32) * 5/9
        return f"{temp}°F = {result}°C"
    else:
        return "Invalid unit (use C or F)"

# Test the converter
print(convert_temperature())
```

## Exercise 2: Password Validator

```python
def check_length(password):
    """Check if password is at least 8 characters"""
    return len(password) >= 8

def has_number(password):
    """Check if password contains a number"""
    return any(char.isdigit() for char in password)

def has_uppercase(password):
    """Check if password has an uppercase letter"""
    return any(char.isupper() for char in password)

def validate_password(password):
    """Check if password meets all criteria"""
    checks = {
        "Length": check_length(password),
        "Number": has_number(password),
        "Uppercase": has_uppercase(password)
    }
    
    # Print detailed results
    print("\nPassword Check Results:")
    for check, passed in checks.items():
        print(f"{check}: {'✅' if passed else '❌'}")
    
    # Return True only if all checks pass
    return all(checks.values())

# Test the validator
test_password = input("Enter a password: ")
if validate_password(test_password):
    print("\n✨ Password is valid!")
else:
    print("\n⚠️ Password does not meet all requirements")
```

## Exercise 3: Recursive Number Guesser

```python
def guess_number(low, high, attempts=1):
    """Guess a number using binary search"""
    # Calculate middle point
    guess = (low + high) // 2
    
    # Ask user about guess
    print(f"\nAttempt {attempts}: Is your number {guess}?")
    response = input("Enter 'h' for higher, 'l' for lower, 'c' for correct: ").lower()
    
    # Check response
    if response == 'c':
        print(f"\n🎉 Found your number in {attempts} attempts!")
        return attempts
    elif response == 'h':
        return guess_number(guess + 1, high, attempts + 1)
    elif response == 'l':
        return guess_number(low, guess - 1, attempts + 1)
    else:
        print("Please enter 'h', 'l', or 'c'")
        return guess_number(low, high, attempts)

# Play the game
print("Think of a number between 1 and 100")
guess_number(1, 100)
```

# Best Practices

1. **Naming**
   - Use descriptive names
   - Use lowercase with underscores
   - Avoid single-letter names (except in simple loops)

2. **Documentation**
   - Add docstrings to explain what functions do
   - Comment complex logic
   - Update comments when code changes

3. **Structure**
   - One task per function
   - Keep functions short (< 20 lines ideally)
   - Use parameters instead of global variables

4. **Error Handling**
   - Check input validity
   - Use try/except for risky operations
   - Return meaningful error messages

# Common Pitfalls to Avoid

1. **Forgetting Return Values**
   ```python
   # Bad
   def add(a, b):
       c = a + b
   
   # Good
   def add(a, b):
       return a + b
   ```

2. **Using Global Variables**
   ```python
   # Bad
   total = 0
   def add_to_total(n):
       global total
       total += n
   
   # Good
   def add_to_total(current_total, n):
       return current_total + n
   ```

3. **Too Many Parameters**
   ```python
   # Bad
   def create_user(name, age, email, address, phone, job, salary):
       # Too many parameters
   
   # Good
   def create_user(user_data):
       # Pass a dictionary with user information
   ```

Remember:
- Start simple and build complexity gradually
- Test functions with different inputs
- Use print statements to debug
- Keep your code organized and readable
- Practice regularly with new challenges