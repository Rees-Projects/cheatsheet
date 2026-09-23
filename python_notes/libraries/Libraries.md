# Python Common Libraries - Cheat Sheet

## math - Math Functions
```python
import math

math.pi        # 3.14159...
math.e
math.sqrt(16)  # 4.0
math.ceil(3.2) # 4
math.floor(3.8)# 3
math.pow(2,3)  # 8.0
math.abs(-5)   # 5
math.sin(math.pi/2)
math.log(10)   # natural log
math.log10(100)# 2.0
```

## random - Random Numbers
```python
import random

random.randint(1,10)        # inclusive 1-10
random.randrange(0,10)      # 0-9
random.choice(['a','b','c'])
random.choices(['a','b','c'], k=2)  # with replacement
random.sample(['a','b','c'], k=2)   # without replacement
random.shuffle([1,2,3,4])           # in-place
random.random()            # 0.0-1.0
random.uniform(1.0, 5.0)   # float range
```

## datetime - Dates & Times
```python
from datetime import datetime, date, time, timedelta

# Current
now = datetime.now()
today = date.today()

# Create
d = datetime(2025, 9, 22, 14, 30, 0)
dt = date(2025,9,22)
t = time(14,30)

# Format
now.strftime("%Y-%m-%d %H:%M:%S")  # 2025-09-22 14:30:00
now.strftime("%m/%d/%Y")            # 09/22/2025

# Parse
datetime.strptime("2025-09-22", "%Y-%m-%d")

# Delta
tomorrow = now + timedelta(days=1)
week_ago = now - timedelta(weeks=1)
delta = tomorrow - now  # timedelta
```

## time - Time Functions
```python
import time

time.sleep(1)        # pause 1 second
start = time.time()  # seconds since epoch
# ... work ...
end = time.time()
print(end-start)
```

## os - Operating System
```python
import os

os.getcwd()           # current working dir
os.listdir('.')      # list files
os.mkdir("folder")
os.makedirs("a/b/c", exist_ok=True)
os.path.exists("file.txt")
os.path.join("a","b","file.txt")
os.remove("file.txt")
os.rmdir("folder")
os.rename("old","new")
os.environ.get("PATH")
```

## sys - System
```python
import sys

sys.argv        # command line args
sys.exit(0)     # exit program
sys.path        # import search paths
sys.version     # Python version
# sys.setrecursionlimit(10**7)
```

## json - JSON
```python
import json

data = {"name":"Alice", "age":30}
s = json.dumps(data)        # to JSON string
json.loads(s)               # from JSON string

# Files
with open("data.json","w") as f:
    json.dump(data, f, indent=2)

with open("data.json") as f:
    data = json.load(f)
```

## copy - Shallow/Deep Copy
```python
import copy

a = [1,[2,3]]
b = copy.copy(a)      # shallow
c = copy.deepcopy(a)  # deep
```

## typing - Type Hints (Common)
```python
from typing import List, Dict, Tuple, Optional, Union

def get_names() -> List[str]: ...
def find_user(id: int) -> Optional[Dict[str,str]]: ...
def process(x: Union[int,str]) -> str: ...
```

## re - Regular Expressions (Basics)
```python
import re

re.search(r"ab+", "abbc")      # match
re.findall(r"\d+", "a12b3")    # ['12','3']
re.sub(r"\s+", "-", "a b  c")  # 'a-b-c'
re.match(r"^abc", "abcdef")    # match from start
```

## pathlib - Modern File Paths (Python 3.4+)
```python
from pathlib import Path

p = Path("folder/file.txt")
p.exists()
p.is_file()
p.read_text()
p.write_text("hello")
p.parent
p.name
p.suffix
Path("a/b").mkdir(parents=True, exist_ok=True)
```

## pickle - Serialize Python Objects (Binary)
```python
import pickle

data = {"x":1}
with open("data.pkl","wb") as f:
    pickle.dump(data, f)

with open("data.pkl","rb") as f:
    data = pickle.load(f)
```
