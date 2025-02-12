# Introduction
- What is Python?

    Object oriented, Open-source
- Why python?

    Easy to learn, easy to use and understand, open-source, flexible, good community.
- Interpreter/ Compiler
    - Interpreter: 

# Installing Python
- [python.org](https://www.python.org/)
- App Stores (MS store)

# Code editors
- Python Shell
- IDLE
    - Shell vs. IDLE
- [VS code](https://code.visualstudio.com/download)
- Online editors ([Google Colab](https://colab.google/))
- etc.

# Python files
- .py

    Basic Python file type. Will run line by line, start to finish (if no exceptions).
- .ipynb

    Better suited for interactive programming, such as Data Science and ML.

# Basic data types
- int

    Whole numbers. `x = 5`
- float 

    Decimal numbers. `y = -2.04`
- string

    A string of characters. `s = 'Hello World!'`
- bool

    A variable representing True or False. `b = False`

# Basic syntax
## Basic I/O
- `print()`
- `input()`
    - type casting
    `int(input())`

- Comments
    `# This is a comment`
    `### This is a multi-line comment`
    `"""This is also a multi-line comment"""`

# Strings
- F-strings
- String methods
    - `upper()`
    - `lower()`
    - `isalnum()`
    - `isalpha()`
    - `isdigit()`
    - `islower()`
    - `isupper()`
    - etc.

```python
print(f"Hello, {name.upper()}!")
```

# Conditionals & Logical Operators
- `if`
- `elif`
- `else`

```python
if grade > 17:
    g = "A"
elif grade > 15:
    g = "B"
elif grade > 10:
    g = "C"
else:
    f = "F"
```

# loops
- for
- while
- break
- continue

```python
j = 0
while j <= 10:
    for i in range(j):
        print(j*"*")
    if j == 7:
        break
    elif j == 5:
        continue

    j += 1

```

# Built-in packages
- math
- random
- time
```python
import math, random, time
```

---
# Examples
- Calculator
- Oddity
- Prime numbers
- Inflation calculating
- factorial

# Homeworks
- Expected value of dice