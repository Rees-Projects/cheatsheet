# Python Common Patterns & Tricks - Cheat Sheet

## F-Strings (Formatted Strings) - Recommended
```python
name, age = "Alice", 30
f"{name} is {age}"                # Alice is 30
f"{name.upper()} is {age:03d}"    # ALICE is 030
f"Price: ${19.99:.2f}"            # Price: $19.99
f"{2**3=}"                        # 2**3=8 (debug)
```

## String Methods
```python
s = "  Hello World  "
s.strip()           # "Hello World"
s.lower()           # "  hello world  "
s.upper()           # "  HELLO WORLD  "
s.title()           # "  Hello World  "
s.replace("o","x")  # "  Hellx Wxrld  "
s.split()           # ['Hello','World']
" ".join(['a','b']) # "a b"
s.startswith("He")  # False (spaces)
s.strip().startswith("He")  # True
s.endswith("ld")
"123".isdigit()     # True
"abc123".isalnum()  # True
"abc".isalpha()     # True
```

## File I/O (With Context Manager)
```python
# Read
with open("file.txt", "r") as f:
    content = f.read()        # all
    # lines = f.readlines()   # list
    # for line in f: pass     # line by line

# Write
with open("file.txt", "w") as f:  # overwrite
    f.write("Hello\n")

with open("file.txt", "a") as f:  # append
    f.write("World\n")

# Read binary
with open("img.png", "rb") as f:
    data = f.read()
```

## Error Handling (Try/Except/Else/Finally)
```python
try:
    x = int(input("Num: "))
    result = 10 / x
except ValueError:
    print("Not a number")
except ZeroDivisionError:
    print("Can't divide by zero")
except (ValueError, ZeroDivisionError):
    print("Input error")
else:
    print("Success:", result)  # runs if no exception
finally:
    print("Always runs")
```

## Custom Exceptions
```python
class MyError(Exception):
    pass

def do_something():
    raise MyError("Something went wrong")

try:
    do_something()
except MyError as e:
    print(e)
```

## Iteration Patterns
```python
# Iterate with index
items = ['a','b','c']
for i, v in enumerate(items, start=1):  # start at 1
    print(i,v)

# Zip two lists
names = ['Alice','Bob']
ages = [30,25]
for n,a in zip(names, ages):
    print(f"{n}:{a}")

# Zip longest? (Python 3.10+ has zip(..., strict=True))
from itertools import zip_longest
for n,a in zip_longest(names, [30], fillvalue='N/A'):
    print(n,a)

# Reverse
for v in reversed(items): pass
```

## Swapping Variables
```python
a,b = 1,2
a,b = b,a  # swap (Pythonic)
```

## List Slicing Tricks
```python
arr = [0,1,2,3,4,5]
arr[::2]      # every other: [0,2,4]
arr[1::2]     # odd: [1,3,5]
arr[::-1]     # reverse: [5,4,3,2,1,0]
arr[-3:]      # last 3: [3,4,5]
arr[:3]       # first 3: [0,1,2]
arr[2:5]      # [2,3,4]
```

## Truthiness & Short-Circuiting
```python
name = None
print(name or "Unknown")  # "Unknown"
print(name and name.upper())  # None
name = "alice"
print(name and name.upper())  # "ALICE"
```

## Walrus Operator (:=) - Python 3.8+
```python
# Assign and use in condition
if (n := len(items)) > 10:
    print(f"Large list ({n} items)")

# In while loops
while (line := input("> ")) != "quit":
    print(line)
```

## Generator Expressions (Memory Efficient)
```python
# List comp (creates list in memory)
squares = [x*x for x in range(10**6)]

# Generator (lazy, iterator)
squares_gen = (x*x for x in range(10**6))
sum(squares_gen)  # computes on-the-fly
```

## `any()` / `all()`
```python
nums = [1,2,3,4]
any(x > 3 for x in nums)  # True (uses generator, short-circuits)
all(x > 0 for x in nums)  # True
```

## Unpacking with * and **
```python
# * for iterables
print(*[1,2,3])  # 1 2 3
first, *middle, last = [1,2,3,4,5]

# ** for dicts
def f(a,b,c): print(a,b,c)
d = {'a':1,'b':2,'c':3}
f(**d)  # 1 2 3
```

## Check if Empty
```python
lst = []
if not lst:  # Pythonic (truthy/falsy)
    print("Empty")

if len(lst) == 0:
    print("Empty")
```

## Chaining Comparisons
```python
x = 5
1 < x < 10  # True (same as 1 < x and x < 10)
```

## Ternary & One-Liners
```python
"even" if x%2==0 else "odd"
result = [i*i for i in range(5) if i%2==0]
```

## Debugging Quick Tips
```python
# Print debugging
print(f"{var=}")  # Python 3.8+

# Check types
type(obj)
isinstance(obj, int)

# See attributes
dir(obj)
help(obj)
```
