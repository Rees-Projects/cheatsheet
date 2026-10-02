# StringBuilder

## Package
```java
StringBuilder sb = new StringBuilder();   // no import needed
```

## What is it?
Strings in Java can't be changed — `+` makes a whole new String every time.
`StringBuilder` is the version you **can** change. Use it when building text in
a loop.

## The Problem It Solves
```java
String text = "";
for (int i = 0; i < 10000; i++) {
    text += i;          // 10000 new Strings created ❌ slow
}

StringBuilder sb = new StringBuilder();
for (int i = 0; i < 10000; i++) {
    sb.append(i);       // same buffer, reused ✅ fast
}
```

## Adding to the End
```java
StringBuilder sb = new StringBuilder();

sb.append("Total");        // "Total"
sb.append(19.99);          // "Total19.99"   — appends any type
sb.append(" items");       // "Total19.99 items"
```

## Adding Anywhere
```java
sb.insert(0, ">> ");       // ">> Total19.99 items"  — at index
sb.reverse();              // "stemi 99.91latoT >>"
sb.deleteCharAt(0);        // removes one char at index
```

## Reading
```java
String s = "Hello";
StringBuilder sb = new StringBuilder(s);

sb.length();              // 5
sb.charAt(0);             // 'H'
sb.substring(1, 3);       // "el"
sb.toString();            // "Hello"  ← needed to get a real String
```

## Changing / Removing
```java
sb.setCharAt(0, 'J');     // "Jello"
sb.replace(0, 1, "How");  // "Howllo"
sb.delete(1, 3);          // removes chars 1-2
```

## Starting Value & Capacity
```java
new StringBuilder("hello");      // starts with "hello"
new StringBuilder(100);          // room for 100 chars — avoids resizing
```

## Quick Reference
| Method | Does |
|---|---|
| `append(x)` | add to the end — the one you use most |
| `insert(i, x)` | add at an index |
| `length()` | how many characters |
| `charAt(i)` | one character |
| `substring(a,b)` | part of it |
| `setCharAt(i, c)` | swap one character |
| `delete(a,b)` | remove a range |
| `deleteCharAt(i)` | remove one character |
| `reverse()` | flip it |
| `toString()` | convert to `String` |

## Things I Want to Remember
- Only use it in loops or when building text — for a single `"a" + b`, plain `+` is fine.
- You need `toString()` to get a `String` back out.
- `append()` works on any type, so `append(19.99)` just works.
- `delete(a, b)` excludes `b`, same as `substring`.
