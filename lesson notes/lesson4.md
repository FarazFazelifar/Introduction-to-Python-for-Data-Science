# Classes: The Blueprint of OOP

Imagine you're an architect designing houses:
- A class is your blueprint
- The houses built from that blueprint are objects
- The rooms and features specified in the blueprint are attributes
- The functionality of each room represents methods

Here's how to create your first class:

```python
class House:
    def __init__(self, color, windows, doors):
        self.color = color
        self.windows = windows
        self.doors = doors
    
    def describe(self):
        return f"This is a {self.color} house with {self.windows} windows and {self.doors} doors."

# Creating a house object
my_house = House("blue", 6, 2)
print(my_house.describe())  # Output: This is a blue house with 6 windows and 2 doors.
```

## Key Components of a Class:
- The `class` keyword: Tells Python you're creating a blueprint
- Class name: By convention, uses CamelCase (e.g., `House`, `CarEngine`, `StudentRecord`)
- The constructor (`__init__`): Like the foundation of your house
- Instance attributes: The characteristics of your object
- Methods: The behaviors or actions your object can perform

# Understanding Objects: Bringing Classes to Life

Think of objects like cookies made from a cookie cutter:
- The cookie cutter is your class
- Each cookie is an object
- The decorations are attributes
- The way you can eat or stack them are methods

```python
class Cookie:
    def __init__(self, flavor, decorations):
        self.flavor = flavor
        self.decorations = decorations
        self.is_baked = False
    
    def bake(self):
        self.is_baked = True
        return "Your cookie is ready!"
    
    def add_decoration(self, new_decoration):
        self.decorations.append(new_decoration)

# Creating different cookie objects
chocolate_cookie = Cookie("chocolate", ["sprinkles"])
sugar_cookie = Cookie("vanilla", ["frosting"])
```

## Important Points About Objects:
- Each object is independent
- Objects have their own copy of attributes
- Objects share the same methods but can behave differently
- Objects can interact with each other

# Constructors: Building Your Objects

Think of a constructor like a factory assembly line:
- It receives raw materials (parameters)
- Sets up the initial state (attributes)
- Prepares the object for use

```python
class Robot:
    # Class attribute - shared by all robots
    manufacturer = "RobotCorp"
    
    def __init__(self, name, task):
        # Instance attributes - unique to each robot
        self.name = name
        self.task = task
        self.battery = 100
    
    def work(self):
        if self.battery > 0:
            self.battery -= 10
            return f"{self.name} is {self.task}. Battery: {self.battery}%"
        return f"{self.name} needs charging!"

# Creating robot objects
cleaner_bot = Robot("Cleaney", "cleaning")
painter_bot = Robot("Paintey", "painting")
```

## Constructor Best Practices:
- Initialize all necessary attributes
- Set default values when appropriate
- Keep it simple and focused
- Validate input data if needed

# Attributes: Giving Objects Characteristics

Think of attributes like a person's traits:
- Instance attributes are personal traits (height, weight)
- Class attributes are family traits (last name, heritage)

```python
class Student:
    # Class attribute
    school = "Python High"
    
    def __init__(self, name, grade):
        # Instance attributes
        self.name = name
        self.grade = grade
        self.subjects = []
    
    def add_subject(self, subject):
        self.subjects.append(subject)
        return f"{self.name} is now studying {subject}"

# Using the Student class
alice = Student("Alice", 10)
bob = Student("Bob", 11)

print(alice.school)  # Output: Python High
print(bob.school)    # Output: Python High
```

## Types of Attributes:
1. Instance Attributes:
   - Unique to each object
   - Defined in the constructor
   - Can be modified for each instance

2. Class Attributes:
   - Shared by all instances
   - Defined outside the constructor
   - Changes affect all instances

# Methods: Defining Object Behaviors

Methods define behaviors within a class: how objects act and interact. There are three types:
Methods define how objects behave. There are three types:

1. Instance Methods
    • Regular methods that use object data
    • Always use `self` parameter
    • Example: `add_number(self, num)`

2. Class Methods
    • Work with the class itself
    • Use `@classmethod` and `cls` parameter
    • Example: `@classmethod def create(cls)`

3. Static Methods
    • Utility functions
    • Use `@staticmethod`
    • Don't need object or class data
    • Example: `@staticmethod def validate(x)`

Here's a simple example:

```python
class Dog:
    # Class attribute
    species = "Canine"
    
    def __init__(self, name):
        self.name = name
    
    # Instance method - uses self
    def bark(self):
        return f"{self.name} says woof!"
    
    # Class method - uses cls
    @classmethod
    def get_species(cls):
        return cls.species
    
    # Static method - uses neither
    @staticmethod
    def is_adult(age):
        return age > 2

# Using the methods
dog = Dog("Max")
print(dog.bark())                # Max says woof!
print(Dog.get_species())         # Canine
print(Dog.is_adult(3))          # True
```

# Practical Example: A Complete Banking System

Let's put everything together in a real-world example:

```python
class BankAccount:
    # Class attributes
    bank_name = "PyBank"
    interest_rate = 0.02
    
    def __init__(self, owner, initial_balance=0):
        # Instance attributes
        self.owner = owner
        self.balance = initial_balance
        self.transactions = []
    
    def deposit(self, amount):
        """Instance method for deposits"""
        if amount > 0:
            self.balance += amount
            self.transactions.append(f"Deposit: ${amount}")
            return f"Deposited ${amount}. New balance: ${self.balance}"
        return "Invalid amount"
    
    def withdraw(self, amount):
        """Instance method for withdrawals"""
        if 0 < amount <= self.balance:
            self.balance -= amount
            self.transactions.append(f"Withdrawal: ${amount}")
            return f"Withdrew ${amount}. New balance: ${self.balance}"
        return "Insufficient funds"
    
    @classmethod
    def set_interest_rate(cls, rate):
        """Class method to change interest rate"""
        cls.interest_rate = rate
        return f"New interest rate: {rate*100}%"
    
    @staticmethod
    def validate_amount(amount):
        """Static method to validate amounts"""
        return amount > 0 and isinstance(amount, (int, float))
    
    def get_statement(self):
        """Generate account statement"""
        statement = f"\nAccount Statement for {self.owner}\n"
        statement += f"{'='*40}\n"
        for transaction in self.transactions:
            statement += f"{transaction}\n"
        statement += f"{'='*40}\n"
        statement += f"Current Balance: ${self.balance}"
        return statement

# Using the banking system
account = BankAccount("John Doe", 1000)
print(account.deposit(500))
print(account.withdraw(200))
print(account.get_statement())
```

# Best Practices and Common Pitfalls

## Best Practices:
- Name classes with CamelCase
- Keep methods focused on single tasks
- Use descriptive names for attributes and methods
- Include docstrings for documentation
- Validate input data
- Handle errors gracefully

## Common Pitfalls to Avoid:
- Using mutable default arguments
- Forgetting to call parent class constructor
- Accessing private attributes directly
- Creating too many responsibilities in one class
- Not using proper encapsulation

# Practice Exercises

1. Create a `Library` system with books and members
2. Build a `Restaurant` ordering system
3. Develop a `School` management system
4. Create a simple game with character classes

Remember:
- Start with simple classes
- Build complexity gradually
- Test your code frequently
- Use meaningful names
- Document your code
- Practice regularly with real-world examples