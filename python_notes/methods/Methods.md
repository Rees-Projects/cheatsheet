# Python Functions & Methods - Cheat Sheet

## Defining Functions
```python
def greet(name):
    return f"Hello {name}"

def add(a, b):
    return a + b

# Default arguments
def greet(name="World"):
    print(f"Hello {name}")

greet()        # Hello World
greet("Alice") # Hello Alice
```

## Arguments (Positional, Keyword, *args, **kwargs)
```python
def func(a, b, c=3):  # a,b required, c optional
    return a+b+c

func(1,2)      # 6
func(1,2,4)    # 7
func(a=1,b=2)  # 6
func(b=2,a=1)  # 6 (keyword order doesn't matter)

# Variable args
def sum_all(*args):
    total = 0
    for num in args:
        total += num
    return total

sum_all(1,2,3)  # 6

# Keyword variable args
def print_info(**kwargs):
    for k,v in kwargs.items():
        print(f"{k}: {v}")

print_info(name="Alice", age=30)
# name: Alice
# age: 30
```

## Return Values
```python
def get_values():
    return 1, 2, 3  # returns tuple

a,b,c = get_values()  # unpacking
```

## Lambda (Anonymous Functions)
```python
add = lambda x,y: x+y
add(2,3)  # 5

nums = [1,2,3,4]
squared = list(map(lambda x: x*x, nums))  # [1,4,9,16]
filtered = list(filter(lambda x: x>2, nums))  # [3,4]
```

## Docstrings & Type Hints
```python
def add(a: int, b: int) -> int:
    """Add two integers and return the sum."""
    return a + b
```

## Scope (LEGB)
Local → Enclosing → Global → Built-in

```python
x = "global"

def outer():
    x = "enclosing"
    def inner():
        x = "local"
        print(x)  # local
    inner()
    print(x)  # enclosing

outer()
print(x)  # global

# Modify global
def change():
    global x
    x = "changed"
```

## First-Class Functions / Closures
```python
def multiplier(n):
    def multiply(x):
        return x * n
    return multiply

times_two = multiplier(2)
times_two(5)  # 10
```

## Decorators (Quick)
```python
def decorator(func):
    def wrapper():
        print("Before")
        func()
        print("After")
    return wrapper

@decorator
def say_hello():
    print("Hello")

say_hello()
# Before
# Hello
# After
```

## Recursion
```python
def factorial(n):
    if n <= 1:
        return 1  # base case
    return n * factorial(n-1)  # recursive case

# For deep recursion (if needed)
# import sys
# sys.setrecursionlimit(10**7)
```

## Built-in Useful Functions
```python
len([1,2,3])      # 3
range(5)          # range object
enumerate(iterable) # (index, value)
map(func, iter)   # map object
filter(func, iter)# filter object
zip(a,b)          # pairs
sorted([3,1,2])   # [1,2,3]
reversed([1,2,3]) # iterator
any([False,True]) # True
all([True,True])  # True
isinstance(x,int) # True
type(x)           # <class 'int'>
help(func)        # docs
dir(obj)          # attributes
```
