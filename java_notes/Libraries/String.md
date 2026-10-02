# String

## Package
```java
String name = "Alice";   // no import needed
```

## Basic Info
```java
String s = "Hello";
s.length();            // 5
s.isEmpty();           // false
s.isBlank();           // false — whitespace counts as blank
```

## Getting Parts
```java
String s = "Hello";
s.charAt(0);           // 'H'
s.charAt(4);           // 'o'
s.substring(1);        // "ello"
s.substring(1, 3);     // "el"  — start, end (end excluded)
s.indexOf('l');        // 2   first 'l'
s.lastIndexOf('l');    // 3   last 'l'
s.charAt(s.indexOf('l')));  // 'l' — common combo
```

## Changing Case / Whitespace
```java
String s = "  Hello World  ";
s.toUpperCase();       // "  HELLO WORLD  "
s.toLowerCase();       // "  hello world  "
s.trim();              // "Hello World"  — both ends
s.strip();             // "Hello World"  — Unicode-aware, prefer this
```

## Finding Things
```java
String s = "Boil water";
s.contains("water");   // true
s.startsWith("Boil");  // true
s.endsWith("water");   // true
```

## Splitting
```java
String s = "a,b,c";
String[] parts = s.split(",");     // ["a", "b", "c"]
String[] two = s.split(",", 2);    // limit of 2 parts

"a b c".split(" ");                // ["a", "b", "c"]
```

## split Uses Regex — This Bites
```java
"a.b.c".split("\\.")     // ["a", "b", "c"]   ✅ escaped, literal dot
"a.b.c".split(".")        // []                ❌ "." matches ANY character
```
```text
⚠️ "." in a regex means "any character", so it splits everywhere at once
   and you get an empty array back. Always escape it: "\\."
   Same applies to |  *  +  ?  ( )  [ ]  and \ itself.
```

## Joining
```java
String.join(", ", "a", "b", "c");   // "a, b, c"
String.join("-", List.of("x","y")); // "x-y"
```

## Replacing
```java
String s = "a-b-c";
s.replace('-', '+');    // "a+b+c"      replaces chars
s.replace("a", "z");    // "z-b-c"      replaces the literal text
s.replaceAll("\\d", "#"); // regex, all matches
```

## Converting
```java
String.valueOf(30);            // "30"
Integer.parseInt("30");        // 30
Double.parseDouble("4.5");     // 4.5
String.join("", 1, 2, 3);      // "123"
```

## Comparing — the one to remember
```java
String a = "hello";
String b = "hello";

a.equals(b);              // true  ✅ compares content
a == b;                   // unreliable ❌ compares references
a.equalsIgnoreCase(b);    // "HELLO".equalsIgnoreCase("hello") → true

s.equals(null);           // false, safe
null.equals(s);           // ❌ NullPointerException
```

## The Big One: Strings Are Immutable
```java
String s = "hi";
s = s + " there";    // creates a NEW string

// In a loop this makes a new string every pass — slow
String result = "";
for (int i = 0; i < 10000; i++) {
    result += i;          // 10000 new strings ❌
}

// Use StringBuilder instead — mutable, fast
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 10000; i++) {
    sb.append(i);
}
String fast = sb.toString();
```

## Quick Reference
| Method | Does |
|---|---|
| `.length()` | number of characters |
| `.isEmpty()` | no characters at all |
| `.charAt(i)` | one character at index |
| `.substring(a)` / `(a,b)` | cut out part of it |
| `.indexOf(x)` | where it appears, `-1` if not |
| `.contains(x)` | is it in there |
| `.startsWith(x)` / `.endsWith(x)` | match the ends |
| `.split(",")` | cut into an array |
| `.trim()` / `.strip()` | remove whitespace |
| `.replace(a,b)` | swap something out |
| `.equals(x)` | **compare** two Strings |
| `.toUpperCase()` | SHOUT |
| `+` | joins Strings together |

## Things I Want to Remember
- Strings are capital `S` because `String` is a class.
- `equals()` compares content, `==` compares references — always use `equals()`.
- `substring(a, b)` includes `a` but NOT `b`.
- `split()` takes a regex, so `.` becomes `\\.`.
- Strings never change — `+` builds a new one. Loops need `StringBuilder`.
