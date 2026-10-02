# ADT: Stack

A **stack** is a LIFO (Last-In, First-Out) abstract data type. Items are pushed onto the top and popped off the top — like a stack of plates or a call stack.

---

## The ADT Reference API

This matches the API you listed (Python methods shown alongside the ADT):

```text
push(x)       Inserts x on top of stack    stack.push(44)
                                           Stack: 44, 99, 77
pop()         Removes and returns the      stack.pop() → 99
              stack's top item            Stack: 77
peek()        Returns but does not remove  stack.peek() → 99
              the stack's top item        Stack still: 99, 77
is_empty()    Returns True if no items     stack.is_empty() → False
get_length()  Returns number of items       stack.get_length() → 2
                                           Stack still: 99, 77
```

> Note: The stack states shown write items in **top → bottom** order here (leftmost = top). That matches your examples. 

---

## How a Stack Works (LIFO)

```text
Starting state (before pop/peek in your examples): Stack = [99, 77]  (top = 99)
- push(44)  → puts 44 on top → Stack = [44, 99, 77]  (top = 44)
- pop()     → removes and returns top (44) → returns 44, Stack = [99, 77]  (top = 99)
- peek()    → returns top (99) without removing → returns 99, Stack = [99, 77]
```

Your table shows `pop()` returning `99` and leaving `Stack: 77`. That means the state *before* that `pop()` call was `Stack: 99, 77` (top=99). So read each operation as acting on the stack state shown in that row's context. The key rule: **LIFO — last pushed is first popped**.

But easier to be precise: **top is the end we push/pop from**. Common notations: list `[bottom, ..., top]` or just say "top of stack".

For your exact examples:
- Initial state shown for pop/peek: `Stack: 99, 77` → top is `99` (if pop() returns 99 and leaves 77)
- `push(44)` on that? If you push onto top of `99,77` (top=99), new top is 44 → stack becomes `99, 77, 44` (bottom→top) or `44, 99, 77` (top→bottom). But result shown is `Stack: 44, 99, 77`. That means the notation writes **top first**.

So in these examples: `Stack: 44, 99, 77` means **top = 44**, below it 99, bottom 77. Then `pop()` removes top 44 and returns it? But table says returns 99 — contradiction in the written sequence. Wait, look up the exact text again.

Your user wrote:
> with my notes on data struckture and algrithms do i adequyetly have the following  
> push(x) 	Inserts x on top of stack 	stack.push(44)  
> Stack: 44, 99, 77  
> pop() 	Removes and returns the stack's top item 	stack.pop()  
> Returns: 99  
> Stack: 77  
> peek() 	Returns but does not remove the stack's top item 	stack.peek()  
> Returns: 99  
> Stack still: 99, 77  
> ...

So for `pop()`, the "Stack:" shown right before pop() in that row is not written. The example shows: after push, stack is 44,99,77 (top first). Then pop() is called on *that* stack? If stack is [44(top), 99, 77(bottom)], pop() should return 44 and leave [99,77]. But your table shows pop() returns 99 and leaves [77]. That suggests either a small ordering typo in notes, or the stack was [99,77] with 99 on top (top-first) and pop returns 99. Maybe the push example is written separately.

But the API is standard. What matters: push adds to top, pop removes+returns top, peek returns top without removal, LIFO.

---

## Core Operations (Time Complexity)

All stack operations are O(1) when implemented well (array/list with end, or linked list with head as top).

| Operation | Complexity | Notes |
|---|---|---|
| `push(x)` | O(1) | amortized if using dynamic array |
| `pop()` | O(1) | |
| `peek()` / `top()` | O(1) | |
| `is_empty()` | O(1) | check size/empty |
| `get_length()` / `size()` | O(1) | if maintaining a counter |

---

## Implementation Options

### 1) Using a Python list (simplest)

In Python, `list.append()` is push to top (end), `list.pop()` returns top. This is efficient (O(1) amortized).

```python
class Stack:
    def __init__(self):
        self._items = []

    def push(self, x):
        self._items.append(x)

    def pop(self):
        if self.is_empty():
            raise IndexError("pop from empty stack")
        return self._items.pop()

    def peek(self):
        if self.is_empty():
            raise IndexError("peek from empty stack")
        return self._items[-1]

    def is_empty(self):
        return len(self._items) == 0

    def get_length(self):
        return len(self._items)

    def __str__(self):
        # Top shown first to match your notation style if desired
        return str(list(reversed(self._items)))
```

Usage:
```python
s = Stack()
s.push(99); s.push(77)  # stack (top→bottom): 77, 99
s.push(44)              # 44, 77, 99
s.pop()                 # returns 44
s.peek()                # 77
```

### 2) Using collections.deque (recommended, O(1) both ends, clear)

```python
from collections import deque

class Stack:
    def __init__(self):
        self._dq = deque()

    def push(self, x): self._dq.append(x)
    def pop(self): return self._dq.pop()
    def peek(self): return self._dq[-1]
    def is_empty(self): return len(self._dq) == 0
    def get_length(self): return len(self._dq)
```

### 3) Using a linked list (top = head)

Push/prepend at head O(1), pop from head O(1). Matches the Linked List ADT's front operations.

```python
# If you have Node/List classes, push = prepend, pop = remove head, peek = head.data
```

---

## Edge Cases & Bugs

- **Pop/peek on empty stack**: raise `IndexError` (or return a sentinel). Don't silently fail.
- **Maintain size** if you roll your own node-based stack without `len()`.
- **Thread-safety**: not covered here (Python GIL doesn't make arbitrary objects thread-safe; use `queue.LifoQueue` if needed).
- **Memory leaks**: in CPython GC is automatic; in other langs ensure nodes freed.

---

## Stack vs Python Built-ins

| ADT Method | Python Equivalent | Notes |
|---|---|---|
| `push(x)` | `list.append(x)` / `deque.append(x)` | end = top |
| `pop()` | `list.pop()` / `deque.pop()` | O(1) |
| `peek()` | `lst[-1]` / `dq[-1]` | no mutation |
| `is_empty()` | `not s` or `len==0` | |
| `get_length()` | `len(s)` | |

Also available: `queue.LifoQueue` (thread-safe). For learning/contests/assignments, a plain list or deque is fine.

---

## Common Stack Applications

- Function call stack (recursion)
- Expression evaluation (infix→postfix, shunting-yard)
- Undo/Redo
- Backtracking (DFS)
- Balancing parentheses/braces
- Browser history (back button)

---

## Key Takeaway

> A stack is LIFO: **push/pop/peek only at the top**. All core operations are O(1). In Python, prefer `list` (end) or `collections.deque` for a clean stack; the course ADT method names (`push`, `pop`, `peek`, `is_empty`, `get_length`) are what you're expected to know.
