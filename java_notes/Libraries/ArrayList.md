# ArrayList

## Package
```java
import java.util.ArrayList;
```

## What is it?
`ArrayList` is a resizable list that stores objects. Its size can grow or shrink as items are added or removed.

## Creating an ArrayList
```java
ArrayList<Transaction> transactions = new ArrayList<>();
ArrayList<String> names = new ArrayList<>(10);   // size hint
```

## Methods I've Used

### `.add()`
Adds an object to the list.
```java
transactions.add(newTransaction);
transactions.add(0, firstItem);   // at index 0 instead of the end
```

### `.get()`
Gets an object at a specific index.
```java
Transaction transaction = transactions.get(0);
```

### `.size()`
Returns the number of items in the list.
```java
int numberOfTransactions = transactions.size();
```

### `.remove()`
Removes an item from the list.
```java
transactions.remove(0);        // by index
transactions.remove(item);     // by object
```

## The Rest of Them
```java
ArrayList<String> names = new ArrayList<>();

names.add("Alice");          // add to the end
names.get(0);                // "Alice"
names.size();                // 1
names.contains("Alice");     // true
names.indexOf("Alice");      // 0   (-1 if missing)
names.isEmpty();             // false

names.set(0, "Bob");         // replace at index
names.remove(0);             // remove by index
names.remove("Bob");         // remove by object
names.add(0, "Zoe");         // insert at index
names.clear();               // empty it
```

```java
ArrayList<Integer> nums = new ArrayList<>(List.of(1, 2, 3));   // from a List
ArrayList<Integer> copy = new ArrayList<>(nums);               // safe copy
```

## Looping Through an ArrayList
```java
for (Transaction transaction : transactions) {
    System.out.println(transaction);
}
```
```java
for (int i = 0; i < transactions.size(); i++) {
    System.out.println(transactions.get(i));
}
```

## ⚠️ Don't Change It While Looping
```java
for (String n : names) {
    names.remove(n);      // ❌ ConcurrentModificationException
}
```

## Arrays vs ArrayLists
| | `Transaction[]` | `ArrayList<Transaction>` |
|---|---|---|
| Size | fixed | **grows** |
| Works with | primitives + objects | objects only |
| Length | `.length` | `.size()` |
| Loop over | for / for-each | for-each |

## Quick Reference
| Method | Does |
|---|---|
| `.add(x)` | add to the end |
| `.get(i)` | item at that index |
| `.size()` | how many items |
| `.remove(i)` | remove by index |
| `.remove(x)` | remove by object |
| `.contains(x)` | is it in there |
| `.indexOf(x)` | where it is, `-1` if not |
| `.set(i, x)` | replace at index |
| `.isEmpty()` | nothing in it |
| `.clear()` | empty it |

## Example From My Finance Simulator
```java
ArrayList<Transaction> transactions = new ArrayList<>();

transactions.add(newTransaction);

for (Transaction transaction : transactions) {
    System.out.println(transaction);
}
```

## Things I Want to Remember
- `ArrayList` stores objects.
- `add()` puts something into the list.
- `get()` retrieves something by index.
- `size()` tells me how many items are in the list.
- I can loop through an `ArrayList` with a for-each loop.
- `get(i)` and `remove(i)` are O(n) — the computer shifts everything after that index.
- Never `remove()` inside a for-each loop over the same list.
