# HashMap

## Package
```java
import java.util.HashMap;
import java.util.Map;
```

## What is it?
Key → value pairs. Look something up by a key instead of scanning a list. Fast.

## Creating
```java
Map<String, Double> balances = new HashMap<>();
Map<String, Double> balances = new HashMap<>(10);   // initial size hint
```

## Adding & Updating
```java
Map<String, Double> balances = new HashMap<>();

balances.put("Alice", 250.00);    // add
balances.put("Alice", 300.00);    // update — same key, replaced

// The "get or create" pattern
balances.putIfAbsent("Bob", 0.0);
```

## Getting Values
```java
balances.get("Alice");            // 300.0   null if missing
balances.getOrDefault("Zoe", 0.0); // 0.0     safe default
balances.containsKey("Alice");    // true
balances.get("Zoe");              // ⚠️ null — not an error, just null
```

## The Null Trap
```java
Map<String, Double> balances = new HashMap<>();
balances.put("Alice", 250.00);

// double d = balances.get("Alice");        // ✅ found
// double d = balances.get("Zoe");          // ❌ unboxing null → crash
double d = balances.getOrDefault("Zoe", 0.0);  // ✅ 0.0
```

## Removing
```java
balances.remove("Alice");         // removes that key
balances.remove("Alice", 250.00); // removes only if value matches
balances.clear();                 // empties everything
```

## Size & Empty
```java
balances.size();            // number of entries
balances.isEmpty();         // true if nothing in it
balances.isEmpty();         // differs from size() == 0, but same idea
```

## Looping
```java
// by key
for (String key : balances.keySet()) {
    System.out.println(key);
}

// by value
for (Double value : balances.values()) {
    System.out.println(value);
}

// key and value together — the one you want most
for (Map.Entry<String, Double> entry : balances.entrySet()) {
    System.out.println(entry.getKey() + " -> " + entry.getValue());
}
```

```java
// shorter form with var (Java 10+)
for (var entry : balances.entrySet()) {
    System.out.println(entry);
}
```

## Quick Reference
| Method | Does |
|---|---|
| `put(k, v)` | add, or replace if key exists |
| `get(k)` | value for a key, `null` if missing |
| `getOrDefault(k, d)` | value, or `d` if missing |
| `containsKey(k)` | is the key there |
| `remove(k)` | delete a key |
| `size()` | how many entries |
| `isEmpty()` | any entries at all |
| `keySet()` | just the keys |
| `values()` | just the values |
| `entrySet()` | keys + values together |

## Things I Want to Remember
- `get()` on a missing key returns `null`, it doesn't crash — but unboxing `null` into a `double` does.
- `put()` with an existing key **replaces**, it doesn't add a second.
- Keys are unique; values can repeat.
- Use `entrySet()` to get key and value in one loop.

## Example From My Finance Simulator
```java
Map<String, Double> balances = new HashMap<>();

balances.put("Alice", 250.00);
balances.put("Bob", 100.50);

double total = 0;
for (Map.Entry<String, Double> entry : balances.entrySet()) {
    total += entry.getValue();
}

System.out.println("Total: " + total);
```
