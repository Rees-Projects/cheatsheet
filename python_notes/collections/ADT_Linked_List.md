# ADT: Linked List

Course ADT for a **singly linked list**. Note this is a *custom* data structure
with its own method names — most of these do **not** exist in Python.

---

## The ADT Reference API

```text
append(X)             Inserts X at end of list        list.append(44)
                                                     list: (99, 77, 44)
prepend(X)            Inserts X at start of list      list.prepend(44)
                                                     list: (44, 99, 77)
insert_after(W, X)    Inserts X after W               list.insert_after(99, 44)
                                                     list: (99, 44, 77)
remove(X)             Removes X                       list.remove(77)
                                                     list: (99)
contains(X)           Returns true if X is in the     list.contains(99) → True
                      list, false otherwise           list.contains(22) → False
print()               Prints list's items in order    list.print() → 99, 77
sort()                Sorts items ascending            list.sort()
                                                     list: (77, 99)
is_empty()            Returns true if no items         list.is_empty() → False
get_length()          Returns number of items          list.get_length() → 2
```

### Spotted the format difference?

`list: (99, 77, 44)` uses **parentheses**. Python lists print as `[99, 77, 44]`.
That parenthesis format is the tell that this is the course's linked-list
class, not a Python `list`.

---

## Node Structure

Each node holds data and a link to the next node. The list object holds
pointers to the ends.

```text
List object
  _head ──▶ [99|•] ──▶ [77|•] ──▶ [44|None] ◀── _tail
  _size = 3

Node
  _data : the item
  _next : the following Node, or None at the end
```

Keeping a `_tail` pointer is what makes `append()` O(1) instead of O(n) — you
never have to walk to the end. This is the single biggest performance decision
in the whole ADT.

---

## Time Complexity

| Method | Complexity | Why |
|---|---|---|
| `append(X)` | **O(1)** | with a `_tail` pointer — link straight onto the end |
| `prepend(X)` | **O(1)** | point the new node at the old head, move head |
| `insert_after(W, X)` | **O(n)** | must find `W` first; the insert itself is then O(1) |
| `remove(X)` | **O(n)** | must find `X` first |
| `contains(X)` | **O(n)** | linear search |
| `print()` | **O(n)** | must visit every node |
| `sort()` | **O(n log n)** | with merge sort |
| `is_empty()` | **O(1)** | check `_head is None` |
| `get_length()` | **O(1)** | *if* a `_size` counter is maintained — O(n) if you must walk |

⚠️ **The `get_length()` subtlety.** If the class keeps a counter, length is
O(1). If it doesn't, you have to walk the list to count, so it's O(n). Same
answer, different cost. Check your course's implementation before you quote a
complexity.

### Singly linked list can't go backwards

This is the defining limitation. There's no `prev` pointer, so:

```text
 You can walk  head → tail   ✅
 You can walk  tail → head   ❌  (would need to restart from the head)
```

So operations anchored to the *front* are cheap, and anything needing the
previous node is not. `insert_after(W, X)` is O(n) precisely because "after W"
has no stored link to W's predecessor.

If you need backwards traversal or O(1) deletion of a known node, that's a
**doubly linked list** — add `_prev` to each node and a doubly linked list
becomes the answer. Trade-off: more memory and more pointers to keep correct.

---

## Full Implementation

```python
class Node:
    def __init__(self, data):
        self._data = data
        self._next = None

    def __repr__(self):
        return f"Node({self._data})"


class List:
    def __init__(self):
        self._head = None
        self._tail = None
        self._size = 0

    def __str__(self):
        if self._head is None:
            return "()"
        items = []
        cur = self._head
        while cur is not None:
            items.append(str(cur._data))
            cur = cur._next
        return "(" + ", ".join(items) + ")"

    def is_empty(self):
        return self._head is None

    def get_length(self):
        return self._size

    def print(self):
        cur = self._head
        first = True
        while cur is not None:
            if not first:
                print(", ", end="")
            print(cur._data, end="")
            first = False
            cur = cur._next
        print()

    def append(self, x):
        new = Node(x)
        if self._head is None:
            self._head = self._tail = new
        else:
            self._tail._next = new
            self._tail = new
        self._size += 1

    def prepend(self, x):
        new = Node(x)
        new._next = self._head
        self._head = new
        if self._tail is None:
            self._tail = new
        self._size += 1

    def _find(self, x):
        cur = self._head
        while cur is not None:
            if cur._data == x:
                return cur
            cur = cur._next
        return None

    def contains(self, x):
        return self._find(x) is not None

    def insert_after(self, w, x):
        cur = self._find(w)
        if cur is None:
            return False
        new = Node(x)
        new._next = cur._next
        cur._next = new
        if cur is self._tail:      # don't lose the tail pointer
            self._tail = new
        self._size += 1
        return True

    def remove(self, x):
        prev = None
        cur = self._head
        while cur is not None and cur._data != x:
            prev = cur
            cur = cur._next
        if cur is None:
            return False
        if prev is None:
            self._head = cur._next
        else:
            prev._next = cur._next
        if cur is self._tail:
            self._tail = prev
        self._size -= 1
        return True
```

### `sort()` — merge sort

Naive repeated insertion gives O(n²). Merge sort gives **O(n log n)** and
suits linked lists naturally because it just relinks nodes — it never has to
shift or copy elements the way it would with an array.

```python
    def sort(self):
        self._head = self._sort(self._head)
        self._tail = self._last(self._head)

    def _last(self, node):
        while node is not None and node._next is not None:
            node = node._next
        return node

    def _sort(self, node):
        if node is None or node._next is None:
            return node
        slow, fast = node, node._next
        while fast is not None and fast._next is not None:
            slow = slow._next
            fast = fast._next._next
        mid = slow._next
        slow._next = None              # split into two lists
        return self._merge(self._sort(node), self._sort(mid))

    def _merge(self, a, b):
        dummy = Node(None)
        tail = dummy
        while a is not None and b is not None:
            if a._data <= b._data:
                tail._next = a
                a = a._next
            else:
                tail._next = b
                b = b._next
            tail = tail._next
        tail._next = a if a is not None else b
        return dummy._next
```

The **slow/fast pointer** split finds the midpoint in one pass — you can't
index into a linked list, so you can't just halve it by arithmetic.

---

## Try It

```python
lst = List()
lst.append(99)
lst.append(77)
lst.append(44)
print(lst)                 # (99, 77, 44)

lst.prepend(1)
print(lst)                 # (1, 99, 77, 44)

lst.insert_after(99, 50)
print(lst)                 # (1, 99, 50, 77, 44)

print(lst.remove(77))     # True
print(lst)                 # (1, 99, 50, 44)

lst.sort()
print(lst)                 # (1, 44, 50, 99)
print(lst.get_length())    # 4
print(lst.is_empty())      # False
print(lst.contains(50))   # True
```

---

## The Bugs That Cost Marks

Every one of these is a real bug that passes a casual read-through and fails a
test case.

### 1. Forgetting to update `_tail` on insert_after

```text
 (99) ──▶ (77)
  _tail  points here

 insert_after(99, 44)  — naive version:
   (99) ──▶ (44) ──▶ (77)
    _tail still points at 77  ✅ by luck

 insert_after(77, 55)  — naive version:
   (99) ──▶ (77) ──▶ (55)
    _tail still points at 77  ❌ 77 is no longer the last node

 Now append() does: self._tail._next = new
 → the new node is linked onto 77, and 55 gets orphaned in the middle.
 → the list silently falls apart.

 FIX: if cur is self._tail: self._tail = new
```

### 2. Removing the head without a `prev`

```text
 _head ──▶ (99) ──▶ (77)
 prev = None

 remove(99) — naive version:
   if prev is not None: prev._next = cur._next   ← prev IS None
   ...never updates _head, so 99 stays forever
   and removing it again removes the same node twice

 FIX: if prev is None: self._head = cur._next
```

### 3. Same problem in reverse on `remove`

Removing the **tail** leaves `_tail` pointing at a node that's no longer
reachable from `_head`.

```text
 FIX: if cur is self._tail: self._tail = prev
```

### 4. Empty-list edge cases

Every mutation has to handle `_head is None` first. A single-element list
breaks any code that assumes "there's always a next node".

```text
 (99) ◀── _head  and  (99) ◀── _tail   ← same node, both pointers
 remove(99)  →  _head = None, _tail = None, _size = 0
 append(1)   →  _head = _tail = new     (the first branch, not the second)
```

### 5. Forgetting `_size`

Miss an increment and `get_length()` returns O(1) and **wrong**. Every mutator
must update the counter in the same breath.

---

## This ADT vs Python's Built-in `list`

| Operation | Course ADT | Python `list` |
|---|---|---|
| add at end | `append(x)` O(1) | `append(x)` O(1) amortized |
| add at front | `prepend(x)` O(1) | `insert(0, x)` **O(n)** — `deque.appendleft` is O(1) |
| insert after item | `insert_after(w, x)` O(n) | no equivalent — must find the index first |
| remove | `remove(x)` | `remove(x)` — **raises `ValueError`** if absent |
| membership | `contains(x)` | `x in lst` |
| length | `get_length()` | `len(lst)` |
| emptiness | `is_empty()` | `len(lst) == 0` or `not lst` |
| print | `print()` | `print(lst)` → `99, 77, 44` in **square** brackets |
| sort | `sort()` | `sort()` in place, or `sorted()` for a new list |

Three behavioural differences to watch:

```text
 remove()
   ADT  : silent no-op when the item isn't there
   list : raises ValueError

 print / str()
   ADT  : your __str__ decides the format (this course uses (99, 77, 44))
   list : fixed [99, 77, 44], no override without subclassing

 sort()
   ADT  : whatever your implementation does
   list : stable, in place, O(n) temp space
```

---

## Linked List vs Array

The trade-off the ADT is teaching you:

```text
 LINKED LIST                    ARRAY / Python list
 ───────────                    ───────────────────
 O(1) insert at a known         O(n) insert (must shift)
   node pointer
 O(1) delete once you           O(n) delete (must shift)
   have the node
 no resizing ever               may reallocate + copy
 no pre-allocation              contiguous
 scattered in memory            contiguous, cache-friendly
 no random access               O(1) indexing

 Net: linked lists win when you
 INSERT/DELETE heavily at a few
 known points (queues, LRU
 caches, free lists, undo
 stacks).

 In practice in Python, prefer
 collections.deque — it gives you
 the list's benefits with none of
 the pointer bookkeeping. Linked
 lists are for learning the
 structure, and for languages
 where you manage memory.
```

### When each actually wins

| Use | Because |
|---|---|
| Queue / deque | O(1) at both ends; `deque` is the Python answer |
| LRU cache | O(1) remove of a known node — the classic real use |
| Free list / memory pool | allocation and free are both O(1) |
| Undo history | append per action, walk backwards if doubly linked |
| Priority queue | usually a heap, not a plain list |
| Almost everything in Python | `list` / `deque` — better cache locality, less code |

---

## Recursion Note

Traversal and `_sort` above are recursive. A singly linked list of 10,000 items
will hit Python's default recursion limit (~1000) in a recursive merge. If that
matters, convert the traversal to a `while` loop, or raise the limit — but
know which one you did.

---

## Key Takeaway

> **A linked list stores items in nodes chained by `_next` pointers, with the
> list holding `_head` and `_tail`. That makes inserts and appends O(1) at
> known points, but forces O(n) for anything needing a search — and crucially
> you cannot walk backwards, because there's no `_prev` link.**

```text
  O(1)                              O(n)
  ─────                             ────
  append    (needs _tail)           insert_after(w, x)   (must find w)
  prepend                          remove(x)            (must find x)
  is_empty                         contains(x)
  get_length (with a counter)       print()
                                   sort() → O(n log n)
```

Related: [Collections.md](Collections.md) · [Huffman_Coding.md](Huffman_Coding.md)
