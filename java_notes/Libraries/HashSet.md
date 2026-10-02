# HashSet

## Package
```java
import java.util.HashSet;
import java.util.Set;
```

## What is it?
A list with **no duplicates**. Adding the same thing twice changes nothing.

## Creating
```java
Set<String> categories = new HashSet<>();
Set<String> categories = new HashSet<>(10);
```

## Adding — Duplicates Vanish
```java
Set<String> categories = new HashSet<>();

categories.add("Food");       // {Food}
categories.add("Food");       // still {Food}  ← ignored
categories.add("Transport");  // {Food, Transport}

new HashSet<>(List.of("a","a","b"));   // {a, b}
```

## Checking
```java
categories.contains("Food");   // true
categories.contains("Rent");   // false
categories.size();             // 2
categories.isEmpty();          // false
```

## Removing
```java
categories.remove("Food");
categories.clear();
```

## Looping
```java
for (String category : categories) {
    System.out.println(category);
}
```

## The Duplicates Use Case
```java
// you have duplicates and don't want them
List<String> tags = List.of("food", "food", "work", "food");
Set<String> unique = new HashSet<>(tags);   // {food, work}

// count how many times something appeared
Map<String, Integer> counts = new HashMap<>();
for (String tag : tags) {
    counts.put(tag, counts.getOrDefault(tag, 0) + 1);
}
// counts: food=3, work=1
```

## Ordering
```java
new HashSet<>(List.of("c", "a", "b"));   // order NOT guaranteed
new TreeSet<>(List.of("c", "a", "b"));   // [a, b, c]  sorted

Set<String> s = new LinkedHashSet<>(List.of("c","a","b"));  // [c, a, b]  keeps order
```

```text
⚠️ HashSet does not keep insertion order. If order matters,
   use LinkedHashSet or TreeSet.
```

## Set Operations
```java
Set<String> a = new HashSet<>(List.of("x", "y", "z"));
Set<String> b = new HashSet<>(List.of("y", "z", "w"));

Set<String> both = new HashSet<>(a); both.retainAll(b);   // {y, z}
Set<String> either = new HashSet<>(a); either.addAll(b);  // {x, y, z, w}
Set<String> onlyA = new HashSet<>(a); onlyA.removeAll(b);  // {x}
```

## Set vs List vs Map
| | Type | Duplicates | Ordered | Lookup |
|---|---|---|---|---|
| `List` | values | yes | yes | by index |
| `Set` | values | **no** | no | by value |
| `Map` | key→value | keys unique | no | by key |

## Quick Reference
| Method | Does |
|---|---|
| `add(x)` | add it — ignored if already there |
| `contains(x)` | is it in the set |
| `remove(x)` | take it out |
| `size()` | how many unique items |
| `isEmpty()` | nothing in it |
| `clear()` | empty it |
| `containsAll(other)` | has all of them |

## Things I Want to Remember
- Adding a duplicate does nothing — no error, no second copy.
- No order guaranteed; use `LinkedHashSet` to keep it, `TreeSet` to sort it.
- Use a `Set` when duplicates are meaningless or unwanted.
- Use a `Map` when I need to look something up by key.
