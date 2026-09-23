# Python Cheat Sheet - Dynamic Method Calls (`getattr`)

## What is Dynamic Method Calling?
Sometimes you need to call a method on an object, but the method name is given as a string (user input, test cases, config, etc.). Python lets you do this using `getattr()` instead of using if/elif chains.

## Syntax
```python
getattr(object, name, default)
```
- `object` - Instance to call method on
- `name` - Attribute/method name as string
- `default` (optional) - Returned if attribute doesn't exist (prevents AttributeError)

## Example (From Lab)

```python
from LabPrinter import LabPrinter

def call_method_named(printer, method_name):
    method = getattr(printer, method_name, None)
    
    if method is not None:
        method()
    else:
        print("Unknown method:", method_name)

# Main program
printer = LabPrinter("abc")

call_method_named(printer, "print_2_plus_2")  # Calls printer.print_2_plus_2()
call_method_named(printer, "print_plus_2")     # Doesn't exist -> "Unknown method: print_plus_2"
call_method_named(printer, "print_secret")     # Calls printer.print_secret()
```

## Breakdown
1. `getattr(printer, "print_2_plus_2", None)` looks for `printer.print_2_plus_2`
2. Returns the bound method if it exists (not the result yet)
3. `method()` executes it
4. If not found, returns `None` (default) so we can handle gracefully

## Safer: Check if Callable
```python
def call_method_named(printer, method_name):
    method = getattr(printer, method_name, None)
    if callable(method):
        method()
    else:
        print("Unknown method:", method_name)
```

## Related Built-Ins
| Function | Purpose |
|---|---|
| `getattr(obj, name, default)` | Get attribute/method by string name |
| `hasattr(obj, name)` | Check if attribute exists |
| `setattr(obj, name, value)` | Set attribute by string name |
| `delattr(obj, name)` | Delete attribute by string name |

## getattr() vs If/Elif
**If/Elif (hard to scale):**
```python
if method_name == "print_2_plus_2":
    printer.print_2_plus_2()
elif method_name == "print_secret":
    printer.print_secret()
else:
    print("Unknown method:", method_name)
```

**getattr() (scalable):**
```python
method = getattr(printer, method_name, None)
if callable(method): method()
else: print("Unknown method:", method_name)
```

## Key Reminders
- `getattr()` returns the method object - you must call it with `()`
- Always provide a default (`None`) to avoid `AttributeError`
- Use `callable()` to only call methods/functions
- Define the function **before** using it
