# Java Syntax — Loops

Repeat code without copy-pasting. Four forms, and each one has a job.

---

## The Classic `for` Loop

The one you'll use most. Three parts separated by semicolons:

```text
for (initialisation; condition; update) {
    body
}
```

```java
for (int i = 0; i < 5; i++) {
    System.out.println(i);
}
```

```text
Output:
0
1
2
3
4
```

Breaking the header down:

```java
int i = 0     // start — runs once before anything
i < 5        // check — loop keeps going while this is true
i++          // update — runs after every pass
```

**Think:** *declare → check → run → update → check → run → update...*

### Variations

```java
// start at 1
for (int i = 1; i <= 5; i++) { }

// count down
for (int i = 5; i > 0; i--) { }

// step by 10
for (int i = 0; i < 100; i += 10) { }

// the variable outlives the loop if you declare it before
int i;
for (i = 0; i < 3; i++) { }
```

### Off-By-One

The classic beginner bug. `<` vs `<=` decides whether the last value runs:

```java
for (int i = 0; i < 5; i++)   // 0,1,2,3,4   five times
for (int i = 0; i <= 5; i++)  // 0,1,2,3,4,5 six times  ⚠️ one too many
```

```text
⚠️ With an array of length 5, index 5 doesn't exist.
   for (int i = 0; i <= arr.length; i++)   ❌ ArrayIndexOutOfBoundsException
   for (int i = 0; i <  arr.length; i++)   ✅
```

---

## `while` — Repeat While a Condition Holds

```java
int balance = 500;

while (balance > 0) {
    balance -= 100;
}
System.out.println(balance);     // 0
```

No counter built in — you manage it yourself.

```text
Think: while there are cookies left, eat one.

   check balance > 0?  → yes → subtract → check again → ... → check → stop
```

### Infinite Loops

```java
while (true) {
    System.out.println("forever");
}
```

```text
⚠️ The condition must eventually become false, or the loop never stops.
   A for loop with a counter can't get stuck this way; a while can.
   Ctrl+C is the escape hatch while testing.
```

**When to use:** the number of repeats isn't known in advance — reading input
until the user quits, processing a file until it's empty, retrying a connection.

---

## `do...while` — Run Once, Then Maybe Again

```java
int attempts = 0;

do {
    System.out.println("Attempt " + (attempts + 1));
    attempts++;
} while (attempts < 3);
```

```text
Output:
Attempt 1
Attempt 2
Attempt 3
```

The body runs **before** the first check, so it always executes at least once
— even if the condition is already false.

```java
int x = 0;
do {
    x++;                    // still runs
} while (x < 0);
```

**When to use:** menus and input validation — "keep asking until the answer is
valid". Using `while` there requires a duplicated first attempt or an awkward
`if` around it.

---

## For-Each (Enhanced `for`) — Loop Over a Collection

When you don't need the index, this is the one to use.

```java
String[] names = {"Alice", "Bob", "Carol"};

for (String name : names) {
    System.out.println(name);
}
```

Read it as *"for each `name` **in** `names`"*. Works on arrays and any
collection.

```java
ArrayList<String> names = new ArrayList<>();
names.add("Alice");

for (String name : names) {
    System.out.println(name);
}
```

**When to use:** any time you're just visiting every element. It's shorter, has
no index variable to get wrong, and can't go out of bounds.

**When not to:** you need the index, or you want to skip items — those need
the classic `for`. See [08_Collections.md](08_Collections.md).

### Classic `for` Equivalent

```java
for (int i = 0; i < names.length; i++) {
    System.out.println(names[i]);
}
```

---

## `break` and `continue`

```java
for (int i = 1; i <= 10; i++) {
    if (i == 5) {
        break;              // LEAVE the loop entirely
    }
    System.out.println(i);
}
```

```text
Output:
1
2
3
4
```

```java
for (int i = 1; i <= 5; i++) {
    if (i == 3) {
        continue;           // SKIP to the next iteration
    }
    System.out.println(i);
}
```

```text
Output:
1
2
4
5
```

```text
break    → exits the loop
continue → skips the rest of this pass, keeps looping
```

**When to use:** both are signs a loop is doing too much. Often the fix is
splitting it into two loops or a method — but `continue` for "skip invalid
input" is perfectly normal.

---

## Nested Loops

A loop inside a loop. Inner loop must finish before the outer one advances.

```java
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        System.out.print(i * j + " ");
    }
    System.out.println();
}
```

```text
Output:
1 2 3
2 4 6
3 6 9
```

**The counting rule:** a loop that runs `n` times inside a loop that runs `m`
times runs `n × m` times total. Nested loops are how you get slow code fast —
be careful with them.

### `break` Only Escapes One Loop

```java
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        if (i * j == 6) {
            break;          // exits the INNER loop only
        }
    }
}
```

To leave both, use a labelled `break`:

```java
outer:
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        if (i * j == 6) {
            break outer;    // exits both
        }
    }
}
```

Labels are rare — usually a sign the logic wants to be a method.

---

## Which Loop Do I Use?

| Situation | Use |
|---|---|
| Count from 0 to n | `for` |
| Iterate over a collection, index unused | for-each |
| Repeat until some condition changes | `while` |
| Run once minimum, then repeat | `do...while` |
| Loop until a number is entered | `do...while` (menu/input) |
| Index needed inside the body | `for` |

```text
Default answer: for. Reach for for-each when you don't need the index,
and while when the repeat count isn't known in advance.
```

---

## Common Mistakes

| Mistake | Result |
|---|---|
| `for (i = 0; ...)` with `i` never declared | compile error — declare it |
| `<= arr.length` | index out of bounds |
| Mutating an `ArrayList` while for-each looping | `ConcurrentModificationException` |
| `while (i = 5)` — one `=` | infinite loop; comparing needs `==` |
| Nested loops over the same size data | O(n²) — often an algorithm, not a loop, problem |

```java
// for-each is read-only over the collection it's looping
for (String s : list) {
    list.remove(s);            // ❌ ConcurrentModificationException
}
```

---

## Quick Reference

| Need | Write |
|---|---|
| Count N times | `for (int i = 0; i < n; i++) { }` |
| Count down | `for (int i = n; i > 0; i--) { }` |
| Loop over a collection | `for (String s : list) { }` |
| Until a condition changes | `while (cond) { }` |
| At least one pass | `do { } while (cond);` |
| Stop early | `break;` |
| Skip this one | `continue;` |
| Leave two loops | `break label;` |

---

## Key Takeaway

> **`for` for counting, for-each for collections, `while` for unknown counts,
> `do...while` when it must run once.** Watch the `<` vs `<=` off-by-one, and
> remember two nested `n`-loops do `n × n` work.

---

Related: [03_Conditionals.md](03_Conditionals.md) ·
[05_Arrays.md](05_Arrays.md) · [08_Collections.md](08_Collections.md) ·
[../Libraries/ArrayList.md](../Libraries/ArrayList.md) (for-each over ArrayList)
