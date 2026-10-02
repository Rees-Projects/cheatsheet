# Java Syntax — Operators

The symbols that do things to values. Learn the first four tables properly and
skim the rest.

---

## Arithmetic

```java
int a = 10, b = 3;

a + b;      // 13   add
a - b;      // 7    subtract
a * b;      // 30   multiply
a / b;      // 3    divide  ← int division truncates!
a % b;      // 1    remainder (modulus)
```

### Modulus `%` — what it's actually for

Remainder after division. Two classic uses:

```text
even or odd?        number % 2 == 0
every 10th time?    count % 10 == 0
```

```java
if (amount % 2 == 0) {
    System.out.println("even");
}
```

### Integer Division

`int / int` throws away the decimals **before** anything else happens.

```java
System.out.println(7 / 2);            // 3
System.out.println(7.0 / 2);          // 3.5
System.out.println((double) 7 / 2);   // 3.5
```

Cast one side to `double` whenever you want a fractional answer. This is the
single most common Java bug — see [01_Basics.md](01_Basics.md).

---

## Compound Assignment

Shorthand for "do the operation, then put it back in the same variable".

```java
int total = 100;

total += 50;    // same as total = total + 50;    → 150
total -= 20;    // same as total = total - 20;    → 130
total *= 2;     // same as total = total * 2;     → 260
total /= 4;     // same as total = total / 4;     → 65
total %= 10;    // same as total = total % 10;
```

**When to use:** whenever you're updating a running total. It's shorter and
you can't forget to write the variable name twice.

---

## Increment / Decrement

```java
count++;          // add 1
count--;          // subtract 1
++count;          // identical
```

Pre- vs post- only matters when you use the value in the same expression:

```java
int a = 5;
System.out.println(a++);    // prints 5, then a becomes 6
System.out.println(++a);    // a becomes 7 first, then prints 7
```

```text
⚠️ Don't do this. It's confusing and interview bait.
   count++;                  ✅ just use this
   int b = count++;          ⚠️ legal but skip it
```

**When to use:** `count++` on its own line, as a standalone statement. That's
it. Everything else is harder to read than the alternative.

---

## Comparison

Produces a `boolean` — `true` or `false`.

```java
a == b;      // equal to
a != b;      // not equal
a > b;       // greater than
a < b;       // less than
a >= b;      // greater than or equal
a <= b;      // less than or equal
```

### `==` vs `.equals()` for Strings

This one matters. `==` compares **references** (are these the same object in
memory), `.equals()` compares **content**.

```java
String a = "hello";
String b = "hello";

a == b;              // ⚠️ may be true OR false — don't rely on it
a.equals(b);         // ✅ true — compares the actual characters
```

**Rule: use `.equals()` to compare Strings, `==` for numbers and chars.**
There's more in [06_Strings.md](06_Strings.md).

---

## Logical

Combine conditions. Used in `if` statements.

```java
age >= 18 && hasId;      // AND — both must be true
score < 50 || retake;   // OR  — at least one true
!isLate;                 // NOT — flips true/false
```

| Operator | Meaning |
|---|---|
| `&&` | AND |
| `\|\|` | OR |
| `!` | NOT |

### Short-Circuit Evaluation

Java stops as soon as it knows the answer — this matters when one side would
crash:

```java
if (index < list.size() && list.get(index) == null) {
    //                                ↑ only runs if index is in range
}
```

```text
⚠️ Wrong order = crash.
   if (list.get(i) == null && i < list.size())   ❌ index error first
   if (i < list.size() && list.get(i) == null)   ✅ checks size first
```

**When to use:** always put the cheap/safe check on the left of `&&`.

---

## The `+` Operator Does Two Jobs

With numbers it adds. With Strings it **joins**.

```java
System.out.println(2 + 3);          // 5
System.out.println("Total: " + 2 + 3);   // "Total: 23"  ← left to right!
```

The trap: once a String appears, everything after it is glued together.

```java
System.out.println("Total: " + (2 + 3));   // "Total: 5"  ✅
System.out.println("Sum: " + 2 + 3);       // "Sum: 23"   ⚠️
```

**Fix:** wrap arithmetic in `( )` when mixing it into a String.

---

## Ternary Operator `? :`

A compact `if / else` that produces a value.

```java
int max = (a > b) ? a : b;         // "if a > b then a, otherwise b"

String status = (paid) ? "PAID" : "DUE";
```

**When to use:** choosing one of two values for a variable. It reads as
"which of these two should it be?".

**When not to:** if the two branches are several lines long, or if there's no
value being produced — use a real `if / else` statement instead. A nested
ternary chain is a sign you should switch to `switch`.

---

## Bitwise & Shifts

Rarely needed unless you're doing low-level work. Skim so you recognise them.

```java
a & b;      // AND  (non-short-circuit)
a | b;      // OR   (non-short-circuit)
a ^ b;      // XOR  (true when they differ)
~a;         // NOT
a << 2;     // shift left  = multiply by 4
a >> 2;     // shift right = divide by 4
a >>> 2;    // unsigned shift right
```

```text
⚠️ Use && and ||, not & and |, in conditions.
   & and | evaluate both sides — no short-circuit, so no null-safety.
```

---

## Operator Precedence

Order of evaluation. Highest first:

```text
Highest → lowest

 1.  a[i]        .   ++ --   (postfix)
 2.  ++ --  + -  !   (type cast)
 3.  *   /   %
 4.  +   -
 5.  <   <=   >   >=
 6.  ==   !=
 7.  &
 8.  ^
 9.  |
10.  &&
11.  ||
12.  ?:           ternary
13.  =  +=  -=     assignment (right to left)
```

### Precedence Traps

```java
// Subtraction happens before the comparison
int count = 5;
if (count - 1 > 0) { }               // ✅ intended

// Always parenthesise mixed operators — it's free
int a = 3, b = 9;
boolean ok = (a > 0) && (b < 10);

double x = 1.5, y = 2.5;
int result = (int) ((x + y) * 2);    // without parens: x + (y * 2) ← different!
```

```text
⚠️ Note the (int) cast in the last line. Assigning a double result into an int
   variable is a compile error — Java won't silently truncate for you.
   Use the cast, or declare the variable as double.
```

**Rule:** if an expression mixes operator types, add `( )`. Nobody will ever
complain about a redundant paren.

---

## Quick Reference

| Need | Write |
|---|---|
| Add / subtract / multiply | `a + b` |
| Divide, keep decimals | `(double) a / b` |
| Remainder | `a % b` |
| Update a total | `total += amount;` |
| Go up by one | `count++;` |
| Compare | `a == b`, `a != b`, `a > b` |
| Compare text | `a.equals(b)` |
| Both / either must be true | `&&` / `\|\|` |
| Flip a boolean | `!flag` |
| Pick one of two values | `x > y ? x : y` |

---

## Key Takeaway

> **Know arithmetic, comparison, `&&`/`||`/`!`, and `+=`.** The three that
> cost you marks: cast to `double` before dividing, use `.equals()` not `==`
> for Strings, and put `( )` around arithmetic you drop into a String.

---

Related: [01_Basics.md](01_Basics.md) · [03_Conditionals.md](03_Conditionals.md) ·
[06_Strings.md](06_Strings.md)
