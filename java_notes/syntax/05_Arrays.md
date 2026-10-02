# Java Syntax — Arrays

A fixed-size, ordered block of same-typed values. The building block behind
`ArrayList`.

---

## Declaring

```java
int[] scores = new int[3];              // 3 zeros: {0, 0, 0}
String[] names = {"Alice", "Bob"};      // fill it in directly
double[] rates = new double[5];         // 5 zeros
```

Two syntaxes, same thing:

```java
int[] a = new int[3];       // ✅ preferred
int b[] = new int[3];       // legal, C-style — don't use it
```

### Every array is initialised to zero/null

```java
int[] counts = new int[3];       // {0, 0, 0}
String[] names = new String[3];  // {null, null, null}
boolean[] flags = new boolean[2];// {false, false}
```

```text
⚠️ A new String array is null, NOT "". You have to set every slot or you'll
   get a NullPointerException the moment you use one.
```

---

## Accessing

`.length` — **not a method**, no parentheses. It works on every array.

```java
String[] names = {"Alice", "Bob", "Carol"};

names[0];        // "Alice"   ← indexes start at 0
names[1];        // "Bob"
names[2];        // "Carol"
names.length;    // 3
```

```text
⚠️ Last valid index is length - 1.
   names[3]   ❌ ArrayIndexOutOfBoundsException
   names.length()   ❌ compile error — length is a field, not a method
```

That `<= length` mistake is the #1 array bug — see
[04_Loops.md](04_Loops.md).

---

## Writing

```java
int[] scores = new int[3];

scores[0] = 95;
scores[1] = 88;
scores[2] = 72;
```

And reading + updating in a loop:

```java
int total = 0;
for (int i = 0; i < scores.length; i++) {
    total += scores[i];
}
System.out.println(total);        // 255
```

Or with for-each, when the index doesn't matter:

```java
for (int score : scores) {
    System.out.println(score);
}
```

---

## Length Is Fixed Forever

```java
int[] a = new int[3];
a[3] = 10;              // ❌ ArrayIndexOutOfBoundsException
a = new int[5];          // the only way to "resize" — and you lose the data
```

An array can never grow. If you don't know the size upfront, use `ArrayList`.

```java
int[] a = {1, 2, 3};
int[] bigger = new int[5];         // new, empty
System.arraycopy(a, 0, bigger, 0, 3);   // the manual way to copy
```

---

## Array vs ArrayList

The distinction worth internalising:

| | Array `int[]` | ArrayList `<Integer>` |
|---|---|---|
| Size | **fixed** at creation | grows and shrinks |
| Type | primitives **and** objects | **objects only** |
| Get item | `a[0]` — instant | `.get(0)` — a hair slower |
| Add item | impossible | `.add(x)` |
| Length | `a.length` | `.size()` |
| Sorting | `Arrays.sort(a)` | `Collections.sort(list)` |

```java
import java.util.ArrayList;

ArrayList<String> names = new ArrayList<>();
names.add("Alice");       // add as many as you like
names.add("Bob");
names.size();             // 2
```

**When to use an array:** the size is known and fixed, or you're dealing with
raw bytes/characters.
**When to use an ArrayList:** anything user-facing — input lists, collections
that grow, anything you'll `add()` to. This is the right default.

Full `ArrayList` method list: [../Libraries/ArrayList.md](../Libraries/ArrayList.md).

---

## Multi-Dimensional Arrays

An array of arrays. Useful for grids, matrices, tables.

```java
int[][] grid = new int[3][4];       // 3 rows, 4 columns

grid[0][0] = 1;                     // row 0, column 0
grid[2][3] = 99;                    // row 2, column 3
grid.length;                        // 3   ← rows
grid[0].length;                     // 4   ← columns
```

Filling one in:

```java
int[][] matrix = {
    {1, 2, 3},
    {4, 5, 6}
};

for (int row = 0; row < matrix.length; row++) {
    for (int col = 0; col < matrix[row].length; col++) {
        System.out.print(matrix[row][col] + " ");
    }
    System.out.println();
}
```

```text
Output:
1 2 3
4 5 6
```

### Jagged Arrays

Rows of different lengths — leave out the second size:

```java
int[][] jagged = new int[3][];
jagged[0] = new int[2];
jagged[1] = new int[5];
jagged[2] = new int[1];
```

---

## The `Arrays` Utility Class

`java.util.Arrays` has the helpers you always end up needing.

```java
import java.util.Arrays;

int[] nums = {5, 3, 9, 1};

Arrays.toString(nums);      // "[5, 3, 9, 1]"  ← printing an array
Arrays.sort(nums);          // {1, 3, 5, 9}    ← in place, ascending
Arrays.fill(nums, 0);       // every element set to 0
int[] copy = nums.clone();  // shallow copy
```

**`Arrays.toString()` is how you print an array.** A bare
`System.out.println(nums)` gives you something useless like
`[I@1b6d3586` — the object's memory address, not the contents.

```java
int[] nums = {1, 2, 3};

System.out.println(nums);               // [I@1b6d3586   ← useless
System.out.println(Arrays.toString(nums));   // [1, 2, 3]  ✅
```

Sorting:

```java
String[] names = {"Carol", "Alice", "Bob"};
Arrays.sort(names);
// {Alice, Bob, Carol}
```

Note `Arrays.sort()` changes the array itself. For a sorted copy, use
`Arrays.copyOfRange` or an `ArrayList` — the Python-style
`sorted(x)` / `x.sort()` split doesn't exist here.

---

## Arrays as Method Parameters and Return Values

```java
// pass an array in
static double average(int[] numbers) {
    double sum = 0;
    for (int n : numbers) {
        sum += n;
    }
    return sum / numbers.length;
}

average(new int[]{1, 2, 3});       // 2.0
```

```java
// return an array
static int[] firstThree(int[] input) {
    return Arrays.copyOfRange(input, 0, 3);
}
```

Arrays are objects, so this is just object passing — no copying happens unless
you explicitly copy.

---

## Common Mistakes

| Mistake | Result |
|---|---|
| `nums.length()` | compile error — it's a field |
| `for (i <= arr.length)` | index out of bounds |
| `String[] s = new String[3];` then `s[0].length()` | `NullPointerException` |
| `int[] a = {1,2}; a[5] = 9;` | index out of bounds |
| Sorting with `=` vs `Arrays.sort` | `nums = nums.sort()` doesn't compile |
| Expecting an array to grow | impossible — use `ArrayList` |

---

## Quick Reference

| Need | Write |
|---|---|
| Declare, empty | `int[] a = new int[5];` |
| Declare, filled | `int[] a = {1, 2, 3};` |
| Length | `a.length` |
| First / last item | `a[0]` / `a[a.length - 1]` |
| Loop with index | `for (int i = 0; i < a.length; i++) { }` |
| Loop over values | `for (int x : a) { }` |
| Print contents | `Arrays.toString(a)` |
| Sort | `Arrays.sort(a)` |
| Fill with a value | `Arrays.fill(a, 0)` |
| Copy | `int[] b = a.clone();` |

---

## Key Takeaway

> **An array is a fixed-size block of same-typed values, indexed from 0, sized
> with `.length` (no parentheses).** Print one with `Arrays.toString()`, and
> if you need to `add()` to it, you're using an `ArrayList` instead.

---

Related: [04_Loops.md](04_Loops.md) · [08_Collections.md](08_Collections.md) ·
[../Libraries/ArrayList.md](../Libraries/ArrayList.md)
