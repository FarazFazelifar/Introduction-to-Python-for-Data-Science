# Python Data Structures: Lists, Tuples, Dictionaries, and Sets

## Introduction

Python provides several built-in data structures that help us organize and manage data efficiently. In this lesson, we'll explore four fundamental data structures: lists, tuples, dictionaries, and sets. Each structure has its unique characteristics and use cases, making them suitable for different scenarios in programming.

## Lists

Lists are ordered collections of items that can be modified. Think of a list as a container that can hold multiple items, similar to a shopping list or a to-do list.

### Creating Lists

We can create lists using square brackets `[]`:

```python
# A simple list of numbers
numbers = [1, 2, 3, 4, 5]

# A list of strings
fruits = ["apple", "banana", "orange"]

# A mixed list containing different types
mixed = [1, "hello", 3.14, True]

# An empty list
empty_list = []
```

### Working with Lists

Lists support various operations:

```python
# Accessing elements (indexing starts at 0)
first_fruit = fruits[0]      # "apple"
last_fruit = fruits[-1]      # "orange"

# Slicing lists
some_fruits = fruits[0:2]    # ["apple", "banana"]

# Modifying elements
fruits[1] = "grape"          # Changes "banana" to "grape"

# Adding elements
fruits.append("mango")       # Adds to the end
fruits.insert(1, "kiwi")     # Adds at specific position

# Removing elements
fruits.remove("apple")       # Removes first occurrence
last = fruits.pop()          # Removes and returns last element

# Finding length
length = len(fruits)         # Number of items in the list

# Checking membership
has_apple = "apple" in fruits  # Returns True or False
```

## Tuples

Tuples are similar to lists but are immutable, meaning they cannot be changed after creation. They're perfect for representing fixed collections of items, like coordinates or RGB colors.

### Creating and Using Tuples

```python
# Creating tuples
coordinates = (10, 20)
rgb_color = (255, 128, 0)

# Accessing elements
x = coordinates[0]           # 10
y = coordinates[1]           # 20

# Trying to modify will cause an error
# coordinates[0] = 30       # This would raise an error

# Multiple assignment using tuples
x, y = coordinates          # Unpacking the tuple
```

## Dictionaries

Dictionaries store key-value pairs, similar to a real dictionary where each word (key) has a definition (value). They're perfect for mapping relationships between items.

### Working with Dictionaries

```python
# Creating a dictionary
student = {
    "name": "Alice",
    "age": 20,
    "grades": [85, 92, 78]
}

# Accessing values
name = student["name"]       # "Alice"
age = student["age"]        # 20

# Adding or modifying entries
student["city"] = "New York"  # Adding new key-value pair
student["age"] = 21          # Modifying existing value

# Checking for keys
has_name = "name" in student  # True

# Getting values safely
grade = student.get("grade", "Not found")  # Returns "Not found" if key doesn't exist
```

## Sets

Sets are unordered collections of unique elements. They're useful for removing duplicates and testing membership.

### Using Sets

```python
# Creating sets
numbers = {1, 2, 3, 4, 5}
more_numbers = {4, 5, 6, 7, 8}

# Adding and removing elements
numbers.add(6)              # Add single element
numbers.remove(2)           # Remove element (raises error if not found)
numbers.discard(10)         # Remove if present (no error if not found)

# Set operations
union = numbers | more_numbers          # All numbers from both sets
intersection = numbers & more_numbers   # Numbers common to both sets
difference = numbers - more_numbers     # Numbers in first set but not in second
```

## Practical Exercises

Let's practice using these data structures with increasingly challenging exercises.

### Exercise 1: List Operations
Create a program that manages a shopping list.

Problem:
1. Create an empty shopping list
2. Add five items to the list
3. Remove the second item
4. Print the total number of items
5. Check if "milk" is in the list

Solution with explanation:
```python
# Initialize empty shopping list
shopping_list = []

# Add items one by one
shopping_list.append("milk")
shopping_list.append("bread")
shopping_list.append("eggs")
shopping_list.append("cheese")
shopping_list.append("fruit")
print("After adding items:", shopping_list)

# Remove second item (bread)
shopping_list.pop(1)    # Index 1 is the second item
print("After removing bread:", shopping_list)

# Print total number of items
print("Total items:", len(shopping_list))

# Check for milk
if "milk" in shopping_list:
    print("Milk is in the list")
else:
    print("Milk is not in the list")
```

### Exercise 2: Dictionary Word Counter
Create a program that counts how many times each word appears in a sentence.

Problem:
1. Take a sentence as input
2. Convert it to lowercase and split into words
3. Count occurrences of each word
4. Print the results

Solution with explanation:
```python
# Our sample sentence
sentence = "the quick brown fox jumps over the lazy fox"

# Convert to lowercase and split into words
words = sentence.lower().split()

# Create empty dictionary for counting
word_count = {}

# Count each word
for word in words:
    # If word exists in dictionary, increment count
    # If not, add it with count of 1
    if word in word_count:
        word_count[word] += 1
    else:
        word_count[word] = 1

# Print results
for word, count in word_count.items():
    print(f"'{word}' appears {count} times")
```

### Exercise 3: Set Operations
Find common elements between two lists without duplicates.

Problem:
1. Create two lists with some overlapping numbers
2. Convert them to sets
3. Find common elements
4. Find elements unique to each list

Solution with explanation:
```python
# Create two lists with some overlapping numbers
list1 = [1, 2, 2, 3, 4, 5, 5, 6]
list2 = [4, 5, 5, 6, 7, 7, 8, 9]

# Convert lists to sets to remove duplicates
set1 = set(list1)
set2 = set(list2)

# Find common elements (intersection)
common = set1 & set2
print("Common elements:", common)

# Find unique elements in first list
unique_to_list1 = set1 - set2
print("Elements only in first list:", unique_to_list1)

# Find unique elements in second list
unique_to_list2 = set2 - set1
print("Elements only in second list:", unique_to_list2)
```

### Exercise 4: Combined Data Structures
Create a program to manage a simple classroom roster using multiple data structures.

Problem:
Create a system that:
1. Stores student information (name and grades) in a dictionary
2. Calculates average grades
3. Identifies unique grade values
4. Lists students with grades above average

Solution with explanation:
```python
# Create dictionary of students and their grades
students = {
    "Alice": [85, 90, 92],
    "Bob": [78, 85, 80],
    "Charlie": [90, 92, 85],
    "David": [75, 68, 75]
}

# Calculate average grade for each student
averages = {}
for student, grades in students.items():
    # Calculate average and round to 2 decimal places
    average = round(sum(grades) / len(grades), 2)
    averages[student] = average

# Find unique grades using a set
all_grades = set()
for grades in students.values():
    # Add each grade to the set
    # Duplicates will automatically be ignored
    for grade in grades:
        all_grades.add(grade)

# Calculate class average
class_average = sum(averages.values()) / len(averages)

# Find students above average
above_average = []
for student, average in averages.items():
    if average > class_average:
        above_average.append(student)

# Print results
print("Student Averages:", averages)
print("Unique Grades:", sorted(all_grades))
print("Class Average:", round(class_average, 2))
print("Students Above Average:", above_average)
```

Each exercise builds upon the previous ones and demonstrates practical applications of Python's data structures. Try modifying these exercises by:
- Adding more features (like sorting, filtering)
- Combining different data structures
- Working with different types of data
- Adding input validation
- Creating more complex calculations