# Python OOP - Cheat Sheet

## Classes & Objects
```python
class Dog:
    # Class attribute (shared)
    species = "Canis familiaris"
    
    # Constructor
    def __init__(self, name, age):
        # Instance attributes
        self.name = name
        self.age = age
    
    # Instance method
    def bark(self):
        print(f"{self.name} says woof!")
    
    def description(self):
        return f"{self.name} is {self.age} years old"

# Create objects
dog1 = Dog("Buddy", 3)
dog2 = Dog("Max", 5)

dog1.bark()  # Buddy says woof!
print(dog1.description())
print(Dog.species)  # Canis familiaris
print(dog1.species) # Canis familiaris (inherited from class)
```

## `self` Explained
- `self` refers to the **instance** of the class
- Must be the first parameter in instance methods
- Python passes it automatically when calling `obj.method()`

## Dunder (Magic) Methods
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def __str__(self):
        return f"{self.name} ({self.age})"
    
    def __repr__(self):
        return f"Person('{self.name}', {self.age})"
    
    def __eq__(self, other):
        if not isinstance(other, Person): return False
        return self.name == other.name and self.age == other.age
    
    def __len__(self):
        return len(self.name)

p = Person("Alice", 30)
print(p)        # Alice (30) - uses __str__
str(p)          # "Alice (30)"
repr(p)         # "Person('Alice', 30)"
len(p)          # 5
```

## Inheritance
```python
class Animal:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        print("Some sound")

class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name)  # call parent constructor
        self.breed = breed
    
    def speak(self):  # override
        print("Woof!")

d = Dog("Buddy", "Labrador")
d.speak()  # Woof!
```

## Multiple Inheritance (MRO)
```python
class A: pass
class B: pass
class C(A,B): pass  # Method Resolution Order: C, A, B, object
print(C.mro())  # view MRO
```

## Encapsulation (Naming Convention)
```python
class BankAccount:
    def __init__(self, balance):
        self._balance = balance      # protected (convention)
        self.__pin = "1234"          # name mangled (private-ish)
    
    def deposit(self, amt):
        if amt > 0:
            self._balance += amt
    
    def get_balance(self):
        return self._balance

# __pin becomes _BankAccount__pin (name mangling)
```

**Convention:**
- `_var` - Protected (internal use, "don't touch outside")
- `__var` - Name mangled (stronger hint of privacy)
- `var` - Public

## Properties (Getters/Setters Pythonic)
```python
class Circle:
    def __init__(self, radius):
        self._radius = radius
    
    @property
    def radius(self):
        return self._radius
    
    @radius.setter
    def radius(self, value):
        if value < 0:
            raise ValueError("Radius must be positive")
        self._radius = value
    
    @property
    def area(self):
        import math
        return math.pi * self.radius ** 2

c = Circle(5)
print(c.area)  # called like attribute, no ()
c.radius = 10  # uses setter
```

## Class Methods & Static Methods
```python
class MyClass:
    count = 0
    
    def __init__(self):
        MyClass.count += 1
    
    @classmethod  # operates on class, takes cls
    def get_count(cls):
        return cls.count
    
    @staticmethod  # utility, takes nothing related to instance/class
    def add(a,b):
        return a+b

obj = MyClass()
print(MyClass.get_count())  # 1
print(MyClass.add(2,3))     # 5
```

## Abstract Classes (Optional)
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Square(Shape):
    def __init__(self, s): self.s = s
    def area(self): return self.s*self.s
```

## Key Terms
- **Instance** - Specific object created from class
- **Attribute** - Variable on class/instance
- **Method** - Function inside class
- **Inheritance** - Child class inherits from parent
- **Polymorphism** - Same method name, different behavior
- **Encapsulation** - Hiding/internal details
- **Abstraction** - Simplify by exposing only essentials
