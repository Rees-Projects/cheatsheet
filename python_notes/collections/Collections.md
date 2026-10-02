# Python Collections - Cheat Sheet

## Lists (Dynamic Arrays) - Ordered, Mutable, Duplicates OK
```python
nums = [1,2,3,4,5]
nums = list((1,2,3))  # from tuple

# Access
nums[0]      # 1
nums[-1]     # 5
nums[1:3]    # [2,3] (slice)
nums[::-1]   # reverse

# Modify
nums.append(6)        # end O(1) amortized
nums.insert(2, 99)    # middle O(n)
nums.extend([7,8])    # append multiple
nums[0] = 10
nums.remove(99)       # first match O(n)
nums.pop()            # remove end O(1)
nums.pop(0)           # remove front O(n) - avoid for large; use deque
del nums[1:3]
nums.clear()

# Search/Info
len(nums)
3 in nums             # O(n)
nums.index(3)         # first index
nums.count(3)
sorted(nums)          # new sorted list
nums.sort()           # in-place
nums.sort(reverse=True)
min(nums), max(nums), sum(nums)
```

## Tuples - Ordered, Immutable, Duplicates OK
```python
t = (1,2,3)
t = 1,2,3  # tuple packing
a,b,c = t  # unpacking
t[0]       # 1
# t[0]=5   # TypeError (immutable)
# Good for keys in dict if hashable, fixed data
```

## Sets - Unordered, Unique, No Duplicates
```python
s = {1,2,3}
s = set([1,2,2,3])  # {1,2,3}
s.add(4)
s.update({5,6})
s.remove(1)        # raises if missing
s.discard(99)      # no error
s.pop()            # arbitrary
s.clear()

# Set operations
a = {1,2,3}
b = {3,4,5}
a | b  # union {1,2,3,4,5}
a & b  # intersection {3}
a - b  # difference {1,2}
a ^ b  # symmetric diff {1,2,4,5}
1 in a  # O(1) avg
```

## Dictionaries (Hash Tables) - Key-Value, Unordered (insertion ordered from 3.7+), Keys Unique
```python
d = {"name":"Alice", "age":30}
d = dict(name="Alice", age=30)

# Access
d["name"]           # "Alice" (KeyError if missing)
d.get("city", "NYC")# safe with default
d.setdefault("role","user") # get or set

# Modify
d["city"] = "Boston"
d.update({"age":31, "city":"SF"})
del d["age"]
d.pop("city", None)
d.popitem()  # remove last inserted (3.7+)
d.clear()

# Iterate
for k in d: pass
for k,v in d.items(): pass
for k in d.keys(): pass
for v in d.values(): pass

# Comprehensions
{ k:v for k,v in [("a",1),("b",2)] }
```

## collections Module (Useful)
```python
from collections import deque, Counter, defaultdict, namedtuple

# deque - O(1) both ends (good for queue/stack/deque ADT)
dq = deque([1,2,3])
dq.append(4)        # right (stack top if using append/pop)
dq.appendleft(0)    # left
dq.pop()            # right (stack pop)
dq.popleft()        # left O(1) vs list.pop(0) O(n)
dq.extend([5,6])
dq.extendleft([-1,0])  # reverses order

# Counter - frequency counts
c = Counter("hello")
# Counter({'l':2,'o':1,'h':1,'e':1})
c.most_common(2)  # [('l',2),('o',1)]
c['l'] += 1
c.total() if hasattr(c,'total') else sum(c.values())  # Python 3.10+

# defaultdict - default value for missing keys
dd = defaultdict(int)
dd["a"] += 1  # no KeyError, starts at 0
dd = defaultdict(list)
dd["keys"].append(1)

# namedtuple - lightweight classes
Point = namedtuple("Point", ["x","y"])
p = Point(1,2)
p.x, p.y  # 1,2
```

## List/Dict/Set Comprehensions
```python
nums = [1,2,3,4,5]
[x*x for x in nums]                # [1,4,9,16,25]
[x for x in nums if x % 2 == 0]    # [2,4]

# Dict comp
{k:v*v for k,v in zip(['a','b'], [1,2])}  # {'a':1,'b':4}

# Set comp
{v for v in "hello"}  # unique chars
```

## Unpacking
```python
a,b = [1,2]
a,*b,c = [1,2,3,4,5]  # a=1, b=[2,3,4], c=5
first, *rest = nums
```
