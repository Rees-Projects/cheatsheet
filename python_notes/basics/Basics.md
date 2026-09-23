# Python Basics - Cheat Sheet

## Quick Reminders
- **Indentation**: 4 spaces (Python doesn't use braces `{}`)
- **Case sensitive**: `Variable` and `variable` are different
- **Comments**: `# single line`, `""" multiline docstring """`
- **Dynamic typing**: No need to declare types (`x = 5`)

## Variables & Data Types
```python
# Numbers
x = 5        # int
y = 3.14     # float
z = 2 + 3j   # complex

# Strings
name = "Alice"
msg = 'Hello'
multiline = """Line 1
Line 2"""

# Booleans
is_true = True
is_false = False

# None
value = None
```

## Type Conversion (Casting)
```python
int("10")      # 10
float("3.14")  # 3.14
str(5)         # "5"
bool(1)        # True
bool(0)        # False
bool([])       # False
bool([1,2])    # True
```

## Input/Output
```python
name = input("Enter name: ")  # input (str)
print("Hello", name)          # space separated
print(f"Hello {name}")       # f-string (recommended)
print("Value: {}".format(x)) # format
print(r"C:\path")             # raw string
```

## Operators
```python
# Arithmetic: + - * / // % **
10 // 3  # floor division = 3
10 % 3   # modulo = 1
2 ** 3   # power = 8
5 / 2    # 2.5 (float division)

# Comparison: == != < > <= >=
# Logical: and or not
# Identity: is, is not
# Membership: in, not in
'a' in "abc"  # True
```

## Control Flow
```python
# If/Elif/Else
if x > 0:
    print("positive")
elif x < 0:
    print("negative")
else:
    print("zero")

# Ternary
result = "even" if x % 2 == 0 else "odd"
```

## Loops
```python
# For loop
for i in range(5):        # 0-4
    print(i)

for item in [1,2,3]:
    print(item)

for i, v in enumerate([10,20,30]):
    print(i, v)  # index, value

# While
count = 0
while count < 3:
    print(count)
    count += 1

# Break/Continue/Else
for i in range(5):
    if i == 2: continue
    if i == 4: break
else:
    pass  # runs if no break
```

## Range
```python
range(5)        # 0,1,2,3,4
range(1,5)      # 1,2,3,4
range(0,10,2)   # 0,2,4,6,8
```

## Truthy/Falsy
Falsy: `False`, `0`, `0.0`, `""`, `[]`, `{}`, `()`, `set()`, `None`
