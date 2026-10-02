# Java Syntax — Conditionals

Code that decides which branch to take. `if / else` covers 90% of real cases;
`switch` is for one variable with many fixed values.

---

## `if / else if / else`

```java
int score = 85;

if (score >= 90) {
    System.out.println("A");
} else if (score >= 80) {
    System.out.println("B");
} else if (score >= 70) {
    System.out.println("C");
} else {
    System.out.println("F");
}
```

**The chain runs top to bottom and stops at the first `true`.** That ordering is
why `score >= 90` has to come before `score >= 80` — reverse them and everything
becomes an A.

```text
Think of it as a checkpoint race:

  score = 85
  if (score >= 90)?   no  → keep going
  if (score >= 80)?   yes → print B, SKIP everything below
  if (score >= 70)?   never reached
  else?               never reached
```

### Rules

```java
if (condition) {         // condition must be boolean — no if (5)
```

```text
⚠️ COMPILER ERRORS
   if (5) { }                 ❌ Java has no truthy numbers
   if ("hello") { }           ❌ strings are not booleans
   if (count > 0) { }         ✅
   if (list.isEmpty()) { }    ✅ method returning boolean

⚠️ The braces matter.
   if (x > 0)
       doSomething();
       doSomethingElse();     ❌ only the first line is conditional
```

**When to use:** any time you need to run code only under some condition.
Braces always — even for one line.

---

## Blocks and Variable Scope

`{ }` defines a scope. Variables declared inside die at the closing brace.

```java
int balance = 500;

if (balance > 0) {
    int bonus = 100;      // only exists inside here
    balance += bonus;
}

System.out.println(balance);    // 600 ✅
// System.out.println(bonus);  ❌ bonus is out of scope
```

This also means the same name can be reused in a *different* block:

```java
if (true) { int x = 1; }
if (true) { int x = 2; }    // ✅ fine — separate scopes
```

---

## Combining Conditions

```java
if (age >= 18 && hasId) { }          // both
if (score < 50 || isRetake) { }      // either
if (!isExpired) { }                  // not
```

```java
// Complex conditions? Name them as booleans first.
boolean isEligible = (age >= 18) && (income > 20000) && !hasDefault;
if (isEligible) {
    System.out.println("Approved");
}
```

**When to use:** more than two or three combined conditions and the `if` line
stops being readable. Extracting named booleans is the fix, and it's also
easier to test.

Full detail on `&&` and short-circuiting: [02_Operators.md](02_Operators.md).

---

## Nested `if`

An `if` inside an `if` — for when there are two separate questions.

```java
if (isLoggedIn) {
    if (isAdmin) {
        System.out.println("Admin panel");
    }
}
```

Equivalently, flattened with `&&`:

```java
if (isLoggedIn && isAdmin) {
    System.out.println("Admin panel");
}
```

**Prefer the flattened version** unless the inner block is long — nesting more
than two deep is a sign the logic wants to move into a method.

---

## `switch` — One Variable, Many Fixed Values

The right tool when you're comparing **one thing** against a list of exact
values.

### Classic form

```java
int day = 3;

switch (day) {
    case 1:
        System.out.println("Monday");
        break;
    case 2:
        System.out.println("Tuesday");
        break;
    case 3:
        System.out.println("Wednesday");
        break;
    default:
        System.out.println("Unknown");
}
```

### `break` Is Required (in this form)

Without it Java keeps falling through to the next case:

```java
switch (day) {
    case 1:
        System.out.println("Special");     // no break
    case 2:
        System.out.println("Normal");      // ← ALSO runs for day == 1
        break;
}
```

```text
⚠️ Missing break is the #1 switch bug. It's legal Java, so the compiler
   won't catch it — you get the wrong output instead.

   day = 1  →  prints "Special" AND "Normal"
```

### Multiple values per case

```java
switch (day) {
    case 6:                 // Saturday
    case 7:                 // Sunday
        System.out.println("Weekend");
        break;
    default:
        System.out.println("Weekday");
}
```

The empty `case 6:` falls through into `case 7:`. That's intentional.

### Switch on Strings and enums

```java
String type = "SAVINGS";

switch (type) {
    case "SAVINGS":
        rate = 0.02;
        break;
    case "CURRENT":
        rate = 0.01;
        break;
    default:
        rate = 0.0;
}
```

### Arrow form — skips the fall-through problem (Java 14+)

```java
int day = 3;

String name = switch (day) {
    case 1 -> "Monday";
    case 2 -> "Tuesday";
    case 3 -> "Wednesday";
    default -> "Unknown";
};                        // no break needed — one line per case
```

This form **returns a value**, so it can be assigned directly. Much harder to
get wrong than the classic form.

---

## `switch` vs `if / else`

| Situation | Use |
|---|---|
| One variable, several exact values | `switch` |
| Ranges (`>= 90`, `< 50`) | `if / else` |
| Complex boolean logic | `if / else` |
| Strings or enums with fixed options | `switch` |
| More than ~5 branches, all exact | `switch` |

```text
Ranges can never use switch.
   if (score >= 90)          ✅ conditions
   switch (score)            ❌ no such thing as "case >= 90"
```

**When in doubt use `if / else`.** Reach for `switch` when you notice yourself
writing a chain of `else if (x == 1) ... else if (x == 2) ...`.

---

## Ternary as a Conditional

For picking one of two values — covered in
[02_Operators.md](02_Operators.md#ternary-operator--).

```java
int max = (a > b) ? a : b;
```

Use it for a one-line value choice, not for a whole branch of logic.

---

## Quick Reference

| Need | Write |
|---|---|
| One condition | `if (x > 0) { }` |
| Two branches | `if (x > 0) { } else { }` |
| Several conditions in order | `if / else if / else` |
| Both must hold | `a && b` |
| Either may hold | `a \|\| b` |
| One of two values | `max > min ? max : min` |
| One var, many exact values | `switch (x) { case 1: ... }` |
| Match a String | `switch (s) { case "A": ... }` |
| Group several values | stacked empty `case 1:` / `case 2:` |
| Anything unmatched | `default:` |

---

## Key Takeaway

> **`if / else` is the default. Always use `{ }`. The chain stops at the first
> `true`, so order your ranges widest-first. Use `switch` only for one variable
> compared against exact values — and in the classic form, never forget `break`.**

---

Related: [02_Operators.md](02_Operators.md) · [04_Loops.md](04_Loops.md) ·
[../oop/getter_setter_methods.md](../oop/getter_setter_methods.md)
(the `if` in a setter guard)
