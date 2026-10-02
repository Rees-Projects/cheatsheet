# ADT: Deque

A **deque** (pronounced "deck", short for *double-ended queue*) lets you add
and remove items from **both ends**. That's the whole idea — a queue on one
end, a stack on the other.

```text
  FRONT                                          BACK
  ┌────┬────┬────┐                              ┌────┐
  │ 41 │ 59 │ 63 │────────── ... ──────────────► │ 19 │
  └────┴────┴────┘                              └────┘

  push_front / pop_front / peek_front  ←  work here
  push_back  / pop_back  / peek_back   ←  and here
```

**Why it exists:** a `list` makes `insert(0, x)` and `pop(0)` O(n) because
everything after it has to be shifted. A deque does both in O(1).

---

## The ADT Reference API

```text
push_front(x)      Inserts x at the front        deque.push_front(41)
                                                Deque: 41, 59, 63, 19
push_back(x)       Inserts x at the back         deque.push_back(41)
                                                Deque: 59, 63, 19, 41
pop_front()        Returns and removes the       deque.pop_front()
                  item at the front             Returns: 59
                                                Deque: 63, 19
pop_back()         Returns and removes the       deque.pop_back()
                  item at the back              Returns: 19
                                                Deque: 59, 63
peek_front()       Returns but does not remove   deque.peek_front()
                  the deque's front item        Returns: 59
                                                Deque is still: 59, 63, 19
peek_back()        Returns but does not remove   deque.peek_back()
                  the deque's back item         Returns: 19
                                                Deque is still: 59, 63, 19
is_empty()         Returns True if the deque is  deque.is_empty()
                  empty, False if not           Returns: False
                                                Deque is still: 59, 63, 19
get_length()       Returns the number of items   deque.get_length()
                  in the deque                  Returns: 3
                                                Deque is still: 59, 63, 19
```

Each example starts from the same baseline: **59, 63, 19** — front is `59`, back
is `19`.

### Read the table carefully

Note that `pop_front()` and `pop_back()` each show the deque *as it was before
the call* minus one item — they're not sequential. After `pop_front()` removes
`59`, the deque is `63, 19`, not `59, 63`. If you run the operations in the
order listed, `pop_back()` would return `19` from `63, 19` and leave `63`.

The point of the table is that **front and back are independent operations**,
not a sequence to follow.

---

## Time Complexity

The entire point of the structure. Both ends are O(1).

| Operation | Complexity | Why |
|---|---|---|
| `push_front(x)` | **O(1)** | link the new node onto the front |
| `push_back(x)` | **O(1)** | link onto the back |
| `pop_front()` | **O(1)** | move `_front` to the next node |
| `pop_back()` | **O(1)** | move `_back` to the previous node |
| `peek_front()` | **O(1)** | read `_front._data` |
| `peek_back()` | **O(1)** | read `_back._data` |
| `is_empty()` | **O(1)** | check `_front is None` |
| `get_length()` | **O(1)** | *if* a `_size` counter is maintained — O(n) if you must walk |

### The catch: `pop_back()` needs a `_prev` link

A **singly** linked list can't walk backwards — there's no `_prev` pointer. So:

```text
  pop_front()  ✅ O(1)   head moves forward — easy
  pop_back()   ✅ O(1)   tail moves backward — needs _prev to exist
```

This is why a deque implementation is effectively a **doubly** linked list:

```text
  Front                          Back
   ┌────┐    ┌────┐    ┌────┐
   │ 59 │───▶│ 63 │───▶│ 19 │
   └─▲──┘    └────┘    └────┘
     └──────────────────┘
        each node also links back to the previous one
```

```text
⚠️ This is the single biggest gotcha. If your course's Deque is implemented
   with only _next pointers, pop_back() CANNOT be O(1) — it has to walk
   from the front to find the node before the back. Check the implementation
   before you quote a complexity.
```

### The one thing that *is* O(n)

There's no random access. `get(i)` doesn't exist as an O(1) operation —
finding the i-th item means walking `i` nodes.

---

## Full Implementation

Doubly linked list, so both ends are O(1).

```python
class Node:
    def __init__(self, data):
        self._data = data
        self._next = None      # towards the back
        self._prev = None      # towards the front

    def __repr__(self):
        return f"Node({self._data})"


class Deque:
    def __init__(self):
        self._front = None
        self._back = None
        self._size = 0

    def __str__(self):
        if self._front is None:
            return "()"
        items = []
        cur = self._front
        while cur is not None:
            items.append(str(cur._data))
            cur = cur._next
        return "(" + ", ".join(items) + ")"

    def is_empty(self):
        return self._front is None

    def get_length(self):
        return self._size

    # ---------- back ----------

    def push_back(self, x):
        new = Node(x)
        new._prev = self._back
        if self._back is None:
            self._front = new            # empty deque — both ends are the new node
        else:
            self._back._next = new
        self._back = new
        self._size += 1

    def pop_back(self):
        if self.is_empty():
            return None
        cur = self._back
        self._back = cur._prev          # thanks to _prev this is O(1)
        if self._back is None:
            self._front = None          # that was the only node
        else:
            self._back._next = None     # don't leave a dangling link
        cur._prev = None                # cut the removed node loose
        cur._next = None
        self._size -= 1
        return cur._data

    def peek_back(self):
        return None if self._back is None else self._back._data

    # ---------- front ----------

    def push_front(self, x):
        new = Node(x)
        new._next = self._front
        if self._front is None:
            self._back = new            # empty deque
        else:
            self._front._prev = new
        self._front = new
        self._size += 1

    def pop_front(self):
        if self.is_empty():
            return None
        cur = self._front
        self._front = cur._next
        if self._front is None:
            self._back = None           # that was the only node
        else:
            self._front._prev = None
        cur._next = None                 # cut the removed node loose
        cur._prev = None
        self._size -= 1
        return cur._data

    def peek_front(self):
        return None if self._front is None else self._front._data
```

### The two mirror-image branches

Every pop has the same shape, and the first branch is the one people forget:

```text
  pop_front() on a one-item deque (59):
     _front = 59, _back = 59

    self._front = cur._next      → None
    if self._front is None: self._back = None   ← must clear BOTH
    else: self._front._prev = None

  Result: front and back both None, size 0. ✅
```

Skip the `else` on `_back` and the deque looks empty from the front but still
has a `_back` pointing at an unreachable node. Then `push_back()` links onto
it and the list falls apart.

---

## Try It

```python
dq = Deque()
dq.push_back(59)
dq.push_back(63)
dq.push_back(19)
print(dq)                 # (59, 63, 19)

dq.push_front(41)
print(dq)                 # (41, 59, 63, 19)
print(dq.pop_front())     # 41
print(dq)                 # (59, 63, 19)

dq.push_back(41)
print(dq)                 # (59, 63, 19, 41)
print(dq.pop_back())      # 41
print(dq)                 # (59, 63, 19)

print(dq.peek_front())    # 59
print(dq.peek_back())     # 19
print(dq.get_length())    # 3
print(dq.is_empty())      # False

print(dq.pop_front())     # 59
print(dq)                 # (63, 19)

print(dq.pop_back())      # 19
print(dq)                 # (63)

print(dq.pop_back())      # 63   ← now it's empty
print(dq.is_empty())      # True
print(dq)                 # ()
```

---

## The Bugs That Cost Marks

### 1. Forgetting to update the *other* pointer

```text
  Single-item deque, (99), front and back both point here

  pop_front():
    _front = None          ← updated
    _back  = 99            ← ❌ still set, and unreachable

  Now push_back(5):
    new._prev = _back  (99)
    _back._next = new      ← 99 is no longer in the list
    _back = new

  Result: front is None, so the deque prints as () — but it has two items.
  FIX: if self._front is None: self._back = None
```

The reverse happens on `pop_back()`. Both pops, both ends, all four cases.

### 2. Forgetting the new node's inward-facing link

```text
  push_back(5) onto (59, 63):

  new = Node(5)
  new._prev = self._back   ✅ needed for pop_back to work later
  self._back._next = new   ✅
  self._back = new         ✅

  Forget new._prev and: pop_back() returns 5, then tries to read 5._prev
  which is None → the deque claims to be empty while 63 and 59 are still
  there. Silent data loss.
```

### 3. Not clearing the dangling `_next` / `_prev`

```text
  pop_front() removes 59 but leaves 59._next pointing at 63.

  Two different things are going on:

  1. The NEW front must forget the old one:
       self._front._prev = None       ✅
     Otherwise walking backwards from the front hits the removed node.

  2. The REMOVED node must forget the deque:
       cur._next = None               ✅
       cur._prev = None               ✅
     Otherwise the popped node still holds references to live nodes.
```

`#2` is optional for correctness in Python — the GC collects the detached node
and its links — but do it anyway. In a language without a GC it's a memory
leak, and it keeps the structure honest when you inspect nodes in a debugger.

### 4. Forgetting `_size`

Same as the linked list. Miss an increment and `get_length()` is O(1) **and
wrong**. All four mutators must update the counter.

### 5. Empty-deque edge cases

Every operation needs an `_front is None` check first:

```text
  pop_front() / pop_back()   on empty  →  None (this ADT) or raise
                                  IndexError (Python's deque)
  peek_front() / peek_back() on empty  →  None here

  push_front(1) / push_back(1) on empty → must set BOTH pointers
```

---

## This ADT vs Python's `collections.deque`

| Operation | Course ADT | Python `deque` |
|---|---|---|
| add at front | `push_front(x)` | `appendleft(x)` |
| add at back | `push_back(x)` | `append(x)` |
| remove from front | `pop_front()` | `popleft()` |
| remove from back | `pop_back()` | `pop()` |
| read front | `peek_front()` | `dq[0]` or `dq.peekLeft()` |
| read back | `peek_back()` | `dq[-1]` or `dq.peek()` |
| emptiness | `is_empty()` | `if not dq:` or `len(dq) == 0` |
| length | `get_length()` | `len(dq)` |
| rotate | not in the ADT | `dq.rotate(1)` |
| remove by value | not in the ADT | `dq.remove(x)` |

**Note the naming trap:** Python's `dq.pop()` removes from the **back**, not the
front. The ADT's `pop_front()` is `popleft()`. Read the method name carefully.

Python's `deque` is already a doubly linked list, so both ends are O(1) —
exactly what the ADT is teaching.

---

## Deque vs List vs Stack vs Queue

| Structure | Add | Remove | Order | Use it for |
|---|---|---|---|---|
| `list` | end O(1) | end O(1), front **O(n)** | — | general purpose, indexing |
| **deque** | both ends O(1) | both ends O(1) | — | sliding windows, work queues |
| stack | top O(1) | top O(1) | LIFO | undo, recursion, backtracking |
| queue | back O(1) | front O(1) | FIFO | processing in arrival order |

### The `list.pop(0)` problem this fixes

```python
items = [1, 2, 3]
items.pop(0)          # O(n) — every remaining element shifts left
```

```python
from collections import deque
dq = deque([1, 2, 3])
dq.popleft()          # O(1)
```

If you ever need to take items off the front of a growing collection, a deque
is the answer. That's the single most practical reason to know this structure.

### When each actually wins

| Use | Because |
|---|---|
| Sliding window / last N items | remove from the front, add to the back, both O(1) |
| Breadth-first search | queue behaviour — FIFO, `popleft()` |
| Undo / redo | deque of states, used as a stack |
| Task scheduling with priorities at either end | both ends reachable |
| Almost everything in Python | `list` — it's the default, and indexing wins |

---

## Key Takeaway

> **A deque adds and removes at both ends, all O(1).** That means a **doubly**
> linked list — each node needs `_next` *and* `_prev`, because `pop_back()`
> can't walk backwards without the reverse link. The two easy mistakes are
> forgetting to clear the *opposite* pointer after a pop, and forgetting the new
> node's inward-facing link on a push.

```text
  O(1)                                O(n)
  ─────                               ────
  push_front / push_back              anything needing to reach the middle
  pop_front  / pop_back               get(i) — no random access
  peek_front / peek_back              (walk from the nearest end)
  is_empty
  get_length (with a counter)
```

Related: [ADT_Stack.md](ADT_Stack.md) · [ADT_Linked_List.md](ADT_Linked_List.md) ·
[Collections.md](Collections.md)
