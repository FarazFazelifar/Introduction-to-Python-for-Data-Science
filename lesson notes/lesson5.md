## Inheritance
Inheritance allows you to create a new class based on an existing one, inheriting attributes and methods while adding or modifying functionality.

```python
class Animal:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        return f"{self.name} makes a sound."

class Dog(Animal):
    def speak(self):
        return f"{self.name} barks!"

# Using inheritance
dog = Dog("Buddy")
print(dog.speak())  # Output: Buddy barks!
```

## Polymorphism: One Interface, Multiple Forms

Polymorphism lets you define methods in a child class with the same name as in the parent class, enabling different behaviors for different objects.

```python
class Cat(Animal):
    def speak(self):
        return f"{self.name} meows!"

def animal_sound(animal):
    print(animal.speak())

# Testing polymorphism
cat = Cat("Whiskers")
animal_sound(dog)  # Buddy barks!
animal_sound(cat)  # Whiskers meows!
```

## Encapsulation: Hiding the Inner Workings

Encapsulation restricts direct access to some of an object's components, protecting its internal state. This is typically achieved using private variables and getter/setter methods.

```python
class Account:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.__balance = balance  # Private attribute
    
    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            return f"Deposited {amount}"
        return "Invalid deposit amount"
    
    def get_balance(self):
        return self.__balance

# Using encapsulation
acc = Account("John")
acc.deposit(300)
print(acc.get_balance())  # 300
```

## Abstraction: Focusing on Essentials

Abstraction means hiding complex reality while exposing only the necessary parts. It enables you to work with high-level concepts without considering the underlying details.
> the process of reorganizing common behavior from groups of non-abstract classes into abstract classes using inheritance and sub-classes, as seen in object-oriented programming languages.

```python
from abc import ABC, abstractmethod

class Vehicle(ABC):
    @abstractmethod
    def start(self):
        pass

class Car(Vehicle):
    def start(self):
        return "Car is starting with a key ignition."

# Using abstraction
car = Car()
print(car.start())  # Car is starting with a key ignition.
```

## Composition: Building Complex Objects from Simpler Ones

Composition involves constructing complex objects using simpler, reusable objects; it's a "has-a" relationship where one object contains other objects.

```python
class Engine:
    def start(self):
        return "Engine starting."

class Car:
    def __init__(self, model):
        self.model = model
        self.engine = Engine()  # Composition: Car has an Engine
    
    def start(self):
        return f"{self.model}: {self.engine.start()}"

# Using composition
my_car = Car("Sedan")
print(my_car.start())  # Sedan: Engine starting.
```

## Summary of Advanced OOP Concepts:
- Inheritance: Deriving new classes from existing classes.
- Polymorphism: One method name, different behaviors.
- Encapsulation: Safeguarding internal state with private attributes and methods.
- Abstraction: Exposing only essential features.
- Composition: Combining simple objects to create complex ones.
