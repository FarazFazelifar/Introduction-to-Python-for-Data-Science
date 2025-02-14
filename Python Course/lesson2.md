# Session 2: Lists, Tuples, Dictionaries, and Sets

## Introduction
In this session, we will dive deeper into some fundamental Python data structures: **lists**, **tuples**, **dictionaries**, and **sets**. Each of these data structures serves a unique purpose in Python, making data handling more convenient and efficient.

---
## Lists
A **list** in Python is an ordered, mutable collection of items. They are incredibly versatile and commonly used for storing sequences of data.

### Creating a List
```python
# Creating a simple list
fruits = ["apple", "banana", "cherry"]

# Lists can contain different data types
mixed_list = [1, "Hello", 3.14, True]
```

### Accessing and Modifying Elements
- **Indexing**: Lists are zero-indexed.
- **Slicing**: You can slice a list using `list[start:end]`.
- **Mutability**: Elements of a list can be changed.

```python
# Indexing
print(fruits[0])       # Output: apple

# Slicing
print(fruits[0:2])     # Output: ["apple", "banana"]

# Changing a value
fruits[1] = "mango"
print(fruits)          # Output: ["apple", "mango", "cherry"]
```

### Common List Methods
- **`append(x)`**: Adds `x` to the end of the list.
- **`insert(i, x)`**: Inserts `x` at index `i`.
- **`remove(x)`**: Removes the first occurrence of `x`.
- **`pop(i)`**: Removes and returns the item at index `i` (by default, the last item).
- **`extend(iterable)`**: Adds elements from an iterable (e.g., another list) to the end.
- **`sort()`**: Sorts the list in-place.
- **`reverse()`**: Reverses the list in-place.

```python
numbers = [10, 5, 8]
numbers.append(12)
print(numbers)     # [10, 5, 8, 12]

numbers.insert(1, 7)
print(numbers)     # [10, 7, 5, 8, 12]

numbers.remove(10)
print(numbers)     # [7, 5, 8, 12]

popped_value = numbers.pop()
print(popped_value) # 12
print(numbers)      # [7, 5, 8]
```

---
## Tuples
A **tuple** is an ordered, **immutable** collection of items. Once created, elements within a tuple cannot be changed.

### Creating a Tuple
```python
tuple_example = ("red", "green", "blue")

# Single-element tuple requires a trailing comma
single_tuple = ("only one", )
```

### Accessing Elements
- **Indexing**: Similar to lists, tuples are zero-indexed.
- **Slicing**: Tuples can also be sliced.

```python
print(tuple_example[0])      # Output: red
print(tuple_example[1:3])    # Output: ("green", "blue")
```

### Immutability
```python
# This will raise an error because tuples are immutable
# tuple_example[0] = "yellow"  # TypeError
```

Tuples are often used when you want data to remain unchanged or when returning multiple values from a function.

---
## Dictionaries
A **dictionary** in Python is an **unordered** collection of key-value pairs. It is extremely useful for quick lookups when you know the key.

### Creating a Dictionary
```python
student = {
    "name": "Alice",
    "age": 21,
    "major": "Computer Science"
}
```

### Accessing and Modifying Values
- Use `dict_name[key]` to access a value.
- Assign `dict_name[key] = value` to change or add entries.

```python
print(student["name"])        # Output: Alice

student["age"] = 22           # Change an existing key's value
student["graduation_year"] = 2024  # Add a new key-value pair
print(student)
```

### Common Dictionary Methods
- **`keys()`**: Returns a list-like object of all keys.
- **`values()`**: Returns a list-like object of all values.
- **`items()`**: Returns a list-like object of `(key, value)` pairs.
- **`get(key, default)`**: Returns the value for `key` if it exists; otherwise returns `default`.
- **`pop(key, default)`**: Removes the key and returns its value if it exists; otherwise returns `default`.

```python
print(student.keys())         # dict_keys(['name', 'age', 'major', 'graduation_year'])
print(student.values())       # dict_values(['Alice', 22, 'Computer Science', 2024])
print(student.items())        # dict_items([('name', 'Alice'), ('age', 22), ('major', 'Computer Science'), ('graduation_year', 2024)])

removed_value = student.pop("major", None)
print(removed_value)          # Computer Science
print(student)
```

---
## Sets
A **set** in Python is an **unordered**, **mutable** collection of **unique** elements. It is often used for membership checking and to eliminate duplicate items.

### Creating a Set
```python
my_set = {1, 2, 3, 2}
print(my_set)       # Output: {1, 2, 3}
```

### Set Operations
- **Union (`|` or `union()`)**: Combines elements from both sets.
- **Intersection (`&` or `intersection()`)**: Elements common to both sets.
- **Difference (`-` or `difference()`)**: Elements in one set but not the other.
- **Symmetric difference (`^` or `symmetric_difference()`)**: Elements in either set, but not both.

```python
set_a = {1, 2, 3}
set_b = {3, 4, 5}

print(set_a | set_b)      # {1, 2, 3, 4, 5}
print(set_a & set_b)      # {3}
print(set_a - set_b)      # {1, 2}
print(set_a ^ set_b)      # {1, 2, 4, 5}
```

### Common Set Methods
- **`add(x)`**: Adds `x` to the set.
- **`remove(x)`**: Removes `x` from the set (raises an error if `x` not found).
- **`discard(x)`**: Removes `x` from the set if present (does not raise an error if `x` not found).
- **`pop()`**: Removes and returns an arbitrary element.
- **`clear()`**: Removes all items from the set.

```python
my_set = {1, 2, 3}
my_set.add(4)
print(my_set)          # {1, 2, 3, 4}

my_set.remove(2)
print(my_set)          # {1, 3, 4}

popped = my_set.pop()
print(popped, my_set)  # Possible output: 1 {3, 4}
```

---
## Iterating Through Collections

### Iterating Over a List
```python
my_list = ["apple", "banana", "cherry"]
for item in my_list:
    print(item)
```

### Iterating Over a Tuple
```python
my_tuple = ("red", "green", "blue")
for color in my_tuple:
    print(color)
```

### Iterating Over a Dictionary
```python
# Iterating through keys
for key in student:
    print(key)

# Iterating through values
for value in student.values():
    print(value)

# Iterating through key-value pairs
for key, value in student.items():
    print(key, value)
```

### Iterating Over a Set
```python
unique_items = {"apple", "banana", "cherry"}
for item in unique_items:
    print(item)
```

---
## Additional Resources
- [Real Python - Data Structures](https://realpython.com/tutorials/data-structures/)
- [W3Schools on Python Data Structures](https://www.w3schools.com/python/python_lists.asp)

---
## Examples
1. **List Operations**: Explore list methods like `append()`, `sort()`, etc. with a real dataset.
2. **Tuple Return Values**: Create a function that returns multiple values in a tuple.
3. **Dictionary for Counting**: Use a dictionary to count occurrences of items in a list.
4. **Set for Unique Values**: Convert a list of repeated values into a set.

```python
# Dictionary for counting example
names = ["Alice", "Bob", "Alice", "Charles", "Bob", "Alice"]
count_dict = {}

for name in names:
    if name in count_dict:
        count_dict[name] += 1
    else:
        count_dict[name] = 1

print(count_dict)  # Output: {'Alice': 3, 'Bob': 2, 'Charles': 1}
```

