# ADT: Queue

A **queue** is FIFO — *First In, First Out*. Items join at the **back** and
leave from the **front**, like a line of people or a queue at a till.

```text
   FRONT                                          BACK
   ┌───────────┬───────────┬───────────┐        ┌───────────┐
   │ Boil water│Add noodles│Cook 5 mins│ ─────► │ Add sauce │
   └───────────┴───────────┴───────────┘        └───────────┘
   ↑ leaves first                               ↑ joins here

   get() / remove()  ← at the front
   put() / add()     → at the back
```

**FIFO in one line:** first thing in, first thing out. A queue is the opposite
of a [stack](ADT_Stack.md) — same structure, opposite ends.

---

## The ADT Reference API

```text
put()          Enqueues an item into the queue      ex_queue.put("Add sauce")

front: "Boil water",
       "Add noodles",
       "Cook 5 minutes",
end:   "Add sauce"

get()          Removes and returns the queue's     ex_queue.get()
               front item                         # Returns "Boil water"
                                                   instruction = ex_queue.get()

front: "Add noodles",
end:   "Cook 5 minutes"

qsize()        Returns the number of items         ex_queue.qsize()
               in the queue                        queue_size = ex_queue.qsize()
                                                    # Returns 3
```

Note the method names: **`put`/`get`, not `add`/`remove`.** That's Python's
`queue.Queue` convention, and it differs from almost everything else in the
standard library.

### Track the counts carefully

Starting queue has 3 items. The rows show:

```text
  initial        3 items   Boil water, Add noodles, Cook 5 minutes
  after put()    4 items   ... plus "Add sauce" at the end
  after get()    3 items   "Boil water" gone
  qsize()   →    3         ✅ consistent — it runs on the 3-item queue
```

`qsize()` returning `3` makes sense only if it runs *after* the `get()`. The
rows are independent examples, not a sequence.

---

## Time Complexity

| Operation | Complexity | Why |
|---|---|---|
| `put(x)` | **O(1)** | link the new node onto the back |
| `get()` | **O(1)** | move `_front` to the next node |
| `peek()` | **O(1)** | read `_front._data` — not always in the ADT |
| `qsize()` | **O(1)** | *if* a `_size` counter is maintained — O(n) if you must walk |
| `is_empty()` | **O(1)** | check `_front is None` |

### A queue only needs `_next`

Everything happens at the two ends, but `get()` only ever moves **forward**:

```text
  put()  →  add at the back     ┌────┐ ← _back
                             ┌────┐──▶... no reverse link needed
                             └────┘

  get()  →  remove from front  ┌────┐ ← _front
             moves _front ──▶  next node

  Never walk backwards ⇒ a SINGLY linked list is enough ✅
```

That's the key contrast with a [deque](ADT_Deque.md): a deque's `pop_back()`
walks backwards, so it needs `_prev` on every node. A queue doesn't.

**But** `put()` is only O(1) with a `_back` pointer. Without one, every insert
walks the whole queue to reach the end — O(n), and you'd feel it.

---

## Full Implementation

Singly linked list with `_front`, `_back`, and `_size`.

```python
class Node:
    def __init__(self, data):
        self._data = data
        self._next = None

    def __repr__(self):
        return f"Node({self._data})"


class Queue:
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

    def qsize(self):
        return self._size

    def put(self, x):
        new = Node(x)
        if self._back is None:
            self._front = new            # empty queue — both ends are the new node
        else:
            self._back._next = new
        self._back = new
        self._size += 1

    def get(self):
        if self.is_empty():
            return None
        cur = self._front
        self._front = cur._next
        if self._front is None:
            self._back = None           # that was the only node
        cur._next = None                 # cut the removed node loose
        self._size -= 1
        return cur._data

    def peek(self):
        return None if self._front is None else self._front._data
```

### The empty-queue branch, again

Same trap as every list-backed structure — one item means both pointers land on
the same node:

```text
  queue = (Boil water), _front and _back both point here

  get():
    self._front = cur._next   → None
    if self._front is None:
        self._back = None     ← MUST clear both
    cur._next = None

  Miss the _back reset and put() links onto an unreachable node.
  The queue then reports empty while holding items. Silent corruption.
```

---

## Try It

```python
q = Queue()

q.put("Boil water")
q.put("Add noodles")
q.put("Cook 5 minutes")
print(q)                      # (Boil water, Add noodles, Cook 5 minutes)
print(q.qsize())              # 3

q.put("Add sauce")
print(q)                      # (Boil water, Add noodles, Cook 5 minutes, Add sauce)
print(q.qsize())              # 4

instruction = q.get()
print(instruction)            # Boil water
print(q)                      # (Add noodles, Cook 5 minutes, Add sauce)
print(q.qsize())              # 3

print(q.peek())               # Add noodles
print(q.is_empty())           # False

print(q.get())                # Add noodles
print(q.get())                # Cook 5 minutes
print(q.get())                # Add sauce
print(q.is_empty())           # True
print(q)                      # ()
```

---

## The Bugs That Cost Marks

### 1. `put()` not setting `_back` on an empty queue

```text
  put("Boil water") into an empty queue:

  if self._back is None:
      self._front = new        ✅ needed
      self._back  = new        ✅ ALSO needed — miss this and...
```

Without `self._back = new`, `_back` stays `None`. The next `put()` sees
`_back is None` again and overwrites `_front`, so **the first item is lost** and
`get()` returns the second one.

### 2. `get()` not clearing `_back` on the last item

```text
  Queue holds one item, (99):

  get():
    self._front = None        ← updated
    self._back  = 99          ← ❌ still set

  Then put(5):  _back._next = 5 links onto the ghost node.
  Queue reports is_empty() == True but qsize() == 1.
```

### 3. No `_back` pointer at all

```text
  put(x) without _back:

  while self._back is not None:     ← have to walk to the end
      self._back = self._back._next
  self._back._next = new

  Every put is O(n). Correct, but the whole point of the structure is that
  both ends are O(1). Check for _back before you quote O(1).
```

### 4. Forgetting `_size`

Same as the linked list. `qsize()` is O(1) **and wrong**. Both `put()` and
`get()` must update the counter.

### 5. Returning the node instead of the data

```text
  return cur                  ❌ you get Node(Boil water)
  return cur._data            ✅ you get "Boil water"
```

---

## This ADT vs Python's `queue.Queue`

| Operation | Course ADT | Python `queue.Queue` |
|---|---|---|
| add at back | `put(x)` | `put(x)` or `add(x)` |
| remove from front | `get()` | `get()` or `get_nowait()` |
| read front | `peek()` | `.queue[0]` (accesses internals) |
| size | `qsize()` | `qsize()` or `unfinished_tasks` |
| emptiness | `is_empty()` | `empty()` |
| blocking put | — | `put(x, block=True)` waits if full |
| timed get | — | `get(timeout=2)` |

Note the direction of the naming difference: `empty()` in Python, `is_empty()`
in the ADT.

### Three classes, three purposes

```python
from queue import Queue, LifoQueue, PriorityQueue

Queue()          # FIFO — first in, first out
LifoQueue()      # LIFO — that's a STACK, same API
PriorityQueue()  # lowest priority value first, ignores insertion order
```

All three are thread-safe — they're built on a lock, so `put`/`get` are atomic
across threads. That safety comes with a small cost: the lock makes them slower
than a plain `deque` for single-threaded work.

```python
# blocking behaviour — put waits for space, get waits for an item
q.put(x)                 # blocks if the queue is full (unbounded: never)
q.get(timeout=2)         # raises Empty if nothing arrives within 2 seconds
```

---

## Queue vs Stack vs Deque

| Structure | Order | Add | Remove | Use it for |
|---|---|---|---|---|
| **queue** | FIFO | back | front | process in arrival order |
| stack | LIFO | top | top | undo, recursion, backtracking |
| deque | — | both ends | both ends | sliding windows, work queues |

| Use | Because |
|---|---|
| Print jobs, task processing | FIFO is the point |
| Breadth-first search | queue behaviour — expand in levels |
| Buffering between producer and consumer | queue decouples timing |
| Order of arrival matters | a `list.pop(0)` is O(n) — use a queue |

**A queue is a stack turned around.** `put` at the back / `get` at the front is
the same structure as a stack's `push`/`pop` at the top, with the working end
moved.

---

## Key Takeaway

> **A queue is FIFO: `put` adds at the back, `get` removes from the front.**
> It needs a singly linked list — nothing ever walks backwards — but it does
> need a `_back` pointer, without which `put()` is O(n). Track `_size` for an
> O(1) `qsize()`, and clear both pointers when the queue empties.

```text
  O(1)                              O(n)
  ─────                             ────
  put (needs _back)                 anything requiring a walk from the back
  get                               get(i) — no random access
  peek
  is_empty
  qsize (with a counter)
```

Related: [ADT_Stack.md](ADT_Stack.md) (the same structure, LIFO) ·
[ADT_Deque.md](ADT_Deque.md) (both ends) ·
[ADT_Linked_List.md](ADT_Linked_List.md) (the underlying structure) ·
[Collections.md](Collections.md)
