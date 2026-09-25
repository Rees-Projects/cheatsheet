a# Huffman Coding (Python) - Cheat Sheet

Huffman coding is a **lossless compression** algorithm. It assigns **shorter codes to frequent characters** and **longer codes to rare characters**, so the whole message takes fewer bits than fixed-length codes (like ASCII).

## Big Picture (Understand This First)

1. Count how often each character appears (a **frequency table**).
2. Turn every character into a **leaf node** holding `(character, frequency)`.
3. Repeatedly merge the **two least-frequent** nodes into a parent whose frequency is their sum.
4. When one node remains, that node is the **root** of a binary tree.
5. Walk the tree: `0` = go left, `1` = go right. The path to a leaf is that character's code.

Because frequent characters sit near the root, they get short codes. This is the **greedy** idea: always merge the two cheapest nodes (this is why we need a **min-heap / priority queue**).

```
Example text:  "abccdd"
freq:  a=1  b=1  c=2  d=2

  a(1)  b(1)     -> ab(2)
  c(2)  d(2)     -> cd(4)
  ab(2) cd(4)    -> root(6)

      (6)
      /  \
   (2)    (4)
   / \    / \
 a(1) b(1) c(2) d(2)

codes: a=00  b=01  c=10  d=11
```

---

## 1. The Node Class

```python
class HuffmanTreeNode:
    def __init__(self, left_child_node, right_child_node):
        self.left_child = left_child_node
        self.right_child = right_child_node
        self.character = '\0'

        # Internal nodes have no character; their frequency is the
        # sum of both children's frequencies.
        frequency = 0
        if left_child_node is not None:
            frequency += left_child_node.get_frequency()
        if right_child_node is not None:
            frequency += right_child_node.get_frequency()
        self.frequency = frequency

    # Builds a leaf: a node with a character but no children.
    @staticmethod
    def create_leaf(leaf_character, leaf_frequency):
        new_node = HuffmanTreeNode(None, None)
        new_node.character = leaf_character
        new_node.frequency = leaf_frequency
        return new_node

    def get_character(self):
        return self.character

    def get_left_child(self):
        return self.left_child

    def get_right_child(self):
        return self.right_child

    def get_frequency(self):
        return self.frequency

    # Lets the heap compare nodes by frequency.
    def __lt__(self, other):
        return self.frequency < other.frequency
```

### What each piece means

| Piece | Meaning |
|---|---|
| `character = '\0'` | The **null character** marks an *internal* (combined) node. Leaves overwrite it with a real character. |
| `create_leaf(...)` | A `@staticmethod` factory: builds a leaf directly without going through `__init__`'s child-sum logic. |
| `frequency` | Leaves hold a real count; internal nodes hold the **sum** of their children. |
| `__lt__` | Python's "less than" operator. `heapq` needs it to compare and order nodes by frequency. |

### Why a static factory instead of a second constructor?

`__init__` assumes two children and computes frequency by summing. A leaf has **no children** and a **known frequency**, so the standard constructor can't build it correctly — `create_leaf` sidesteps that by calling `HuffmanTreeNode(None, None)` and then setting `character` and `frequency` directly.

---

## 2. Build the Frequency Table

```python
def build_freq_table(text):
    freq = {}
    for ch in text:
        freq[ch] = freq.get(ch, 0) + 1
    return freq
```

`d.get(ch, 0)` returns `0` when the key is missing, so each character counts itself without a `KeyError`. (Or just use `collections.Counter(text)`, which does exactly this.)

---

## 3. Build the Huffman Tree (min-heap)

```python
import heapq

def build_huffman_tree(freq_table):
    heap = []

    # Turn every character into a leaf and push it onto the heap.
    for char, freq in freq_table.items():
        heapq.heappush(heap, HuffmanTreeNode.create_leaf(char, freq))

    # Merge the two smallest nodes until one tree remains.
    while len(heap) > 1:
        left = heapq.heappop(heap)   # smallest
        right = heapq.heappop(heap)  # second smallest
        parent = HuffmanTreeNode(left, right)  # frequency = left + right
        heapq.heappush(heap, parent)

    return heap[0]  # the root of the finished tree
```

### Why a heap?

The two smallest frequencies are needed at every step. A **min-heap** pops the smallest in `O(log n)`, so the whole tree build is `O(n log n)`. Sorting repeatedly or scanning the list each time would be slower.

Memory trick: **heap = "always grab the smallest"**.

---

## 4. Generate the Codes

```python
def generate_codes(root, code="", codes=None):
    if codes is None:
        codes = {}

    if root is None:
        return codes

    if root.get_character() != '\0':        # leaf reached -> save the code
        codes[root.get_character()] = code if code else "0"
    else:                                   # internal node -> keep descending
        generate_codes(root.get_left_child(), code + "0", codes)
        generate_codes(root.get_right_child(), code + "1", codes)
    return codes
```

Recursive walk: every time you go **left** append `"0"`, every time you go **right** append `"1"`. When a leaf is reached, the accumulated string is that character's code.

Edge case: if the text has **only one distinct character**, the root *is* a leaf and the path is empty — fall back to `"0"` so the code is never blank.

---

## 5. Encode Text

```python
def encode(text, codes):
    return "".join(codes[ch] for ch in text)
```

Simple lookup table: replace each character with its binary code and join. Example: `"abccdd"` → `"0001101011"` (from the tree above).

---

## 6. Decode Bits Back to Text

```python
def decode(bits, root):
    # Edge case: a single-character text makes the root a leaf.
    # There are no children to walk, so every bit is just that character.
    if root.get_character() != '\0':
        return root.get_character() * len(bits)

    result = []
    node = root
    for bit in bits:
        # 0 -> go left, 1 -> go right
        node = node.get_left_child() if bit == '0' else node.get_right_child()

        if node.get_character() != '\0':   # hit a leaf -> character found
            result.append(node.get_character())
            node = root                     # restart from the root
    return "".join(result)
```

Huffman codes are **prefix-free** (no code is the start of another), so decoding is unambiguous: just follow bits down the tree, and every time you land on a leaf you know exactly which character it was, then restart from the root.

---

## 7. Putting It All Together

```python
text = "hello world"

freq_table = build_freq_table(text)
root       = build_huffman_tree(freq_table)
codes      = generate_codes(root)

print(codes)                 # {'h': '110', 'e': '1011', 'l': '011', ...}
bits = encode(text, codes)   # compressed message
print(decode(bits, root) == text)  # True
```

---

## Complexity

| Step | Time | Space |
|---|---|---|
| Build frequency table | `O(n)` | `O(k)` |
| Build tree (heap) | `O(k log k)` | `O(k)` |
| Generate codes | `O(k)` | `O(k)` |
| Encode | `O(n)` | — |
| Decode | `O(n)` | — |

`n` = text length, `k` = number of distinct characters.

---

## Key Takeaways

- Huffman trees are built **bottom-up** by repeatedly merging the two smallest nodes using a **min-heap (priority queue)**.
- `__lt__` is what makes the node heap-comparable.
- `'\0'` is a sentinel that distinguishes **leaf** (has character) from **internal** (sum of children).
- Codes are **prefix-free**, which is what makes decoding simple and lossless.