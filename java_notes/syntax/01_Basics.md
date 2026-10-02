# Java Syntax — Basics, Variables & Types

How to declare things in Java and when to reach for each type. Terse reference —
the goal is "can I write this without looking it up", not a full spec.

---

## Program Structure

Every Java file has at least one **class**. Code runs from `main`.

```java
public class Main {              // file name must match the class name
    public static void main(String[] args) {
        System.out.println("Hello");
    }
}
```

```text
javac Main.java     →  compiles to Main.class
java Main           →  runs it
```

### Comments

```java
// one line

/* many
   lines */

/** Javadoc — shows up as documentation on hover in an IDE */
```

### Imports

```java
import java.util.Scanner;        // one class
import java.util.*;              // everything in a package
```

---

## Variables

A variable is `type name = value;`. Declare it, then use it. The `;` is
required on every statement.

```java
int age = 30;                   // declare + assign
String name = "Alice";          // String is capital S — it's a class
double balance = 1250.75;
boolean isActive = true;
```

You can also declare without a value, then assign later:

```java
int total;                      // defaults to 0
total = 10;
```

### Naming Rules (these are conventions, not compile errors)

| Thing | Convention | Example |
|---|---|---|
| Variables, methods | `camelCase` | `monthlyPayment` |
| Classes | `PascalCase` | `LoanCalculator` |
| Constants | `UPPER_SNAKE_CASE` | `MAX_LOAN_AMOUNT` |
| Packages | all lowercase | `com.mybank.loans` |

```java
final int MAX_LOAN_AMOUNT = 50000;    // final = can't be reassigned
```

> Full detail on `final` lives in [../oop/java_final_keyword_guide.md](../oop/java_final_keyword_guide.md).

---

## The 8 Primitive Types

Primitives are the built-in basics — no object, no methods, just a value.

| Type | Size | Holds | Default | Example |
|---|---|---|---|---|
| `int` | 32-bit | whole numbers | `0` | `int count = 5;` |
| `double` | 64-bit | decimals | `0.0` | `double rate = 4.5;` |
| `boolean` | — | `true` / `false` | `false` | `boolean paid = false;` |
| `char` | 16-bit | **one** character | `'\0'` | `char grade = 'A';` |
| `long` | 64-bit | huge whole numbers | `0` | `long id = 9_000_000_000L;` |
| `float` | 32-bit | small decimals | `0.0f` | `float ratio = 0.5f;` |
| `short` | 16-bit | small whole numbers | `0` | `short year = 2026;` |
| `byte` | 8-bit | tiny whole numbers | `0` | `byte level = 3;` |

**When to use which — the short version:**

```text
counting things          →  int
money, interest, anything
  with decimals          →  double
yes/no flags             →  boolean
a single letter or
  keyboard key           →  char
IDs, timestamps          →  long
```

**99% of the time you only need `int`, `double`, `boolean`, and `String`.**
Reach for `long`/`float`/`short`/`byte` only when a range forces you to.

```text
⚠️ char is ONE character. Use double quotes for String, single for char.

   char grade = 'A';        ✅
   char grade = "A";        ❌ COMPILER ERROR
   char grade = 'AB';       ❌ COMPILER ERROR
```

### Strings Aren't Primitives

`String` is a **class** — that's why it's capitalised and why you can call
methods on it (`"hi".length()`).

```java
String name = "Alice";        // object reference, not a primitive
String nothing = null;        // null = "no object yet"
```

---

## `var` — Let Java Guess the Type

```java
var count = 5;                // int
var rate = 4.5;               // double
var name = "Alice";           // String
var items = new ArrayList<String>();   // ArrayList<String>
```

**When to use:** locals where the type is obvious from the right-hand side.
**When not to:** fields, or when the right side is vague (`var x = getIt();`).
It is still static typing — the type is fixed at compile time.

---

## Printing

```java
System.out.println("Balance: " + balance);   // adds a newline
System.out.print("Loading");                 // no newline
System.out.println();                        // blank line

System.out.printf("Total: %.2f%n", 12.5);    // formatted output
```

`printf` format specifiers:

| Specifier | Use |
|---|---|
| `%s` | String / any object |
| `%d` | whole number (`int`, `long`) |
| `%f` | decimal (`%.2f` = 2 decimal places) |
| `%n` | new line (portable) |
| `%,.2f` | thousands separator + 2 decimals |

**When to use which:** `println` for everyday output, `printf` when the
format matters (money, aligned columns, fixed decimals).

---

## Casting — Changing Type on Purpose

Java won't let you mix types freely. Two directions:

```java
// Widening — always allowed, safe (small → big)
int count = 5;
long big = count;             // ✅ int fits in long
double precise = count;       // ✅ int → double

// Narrowing — needs an explicit cast (big → small, loses data)
double price = 19.99;
int whole = (int) price;      // 19  ← decimals thrown away
```

```text
byte → short → int → long → float → double     ✅ widening, implicit
                ← ← ← ← ← ← ← ← ← ← ← ← ← ← ←   ❌ narrowing, needs (cast)
```

### The Integer Division Trap

This one bites everybody:

```java
int a = 7, b = 2;
System.out.println(a / b);          // 3   ← int / int = int
System.out.println((double) a / b);  // 3.5 ✅ cast one side
```

**When to cast:** when dividing and you want the fractional answer. Cast
*one* side to `double` — that's the whole trick.

---

## Text ↔ Number Conversion

```java
// String → number
int age = Integer.parseInt("30");
double rate = Double.parseDouble("4.5");

// number → String
String text = String.valueOf(30);
String alsoText = "" + 30;             // works, but String.valueOf is clearer

// String → char
char first = "Alice".charAt(0);        // 'A'
```

```text
⚠️ Integer.parseInt("abc")  →  throws NumberFormatException
   Parse user input inside a try/catch, or use a safe helper.
   See 07_Exceptions.md
```

---

## Boxing — Primitives vs Wrapper Classes

Every primitive has a matching object "wrapper":

| Primitive | Wrapper |
|---|---|
| `int` | `Integer` |
| `double` | `Double` |
| `boolean` | `Boolean` |
| `char` | `Character` |
| `long` | `Long` |

You rarely write the wrapper yourself, but you see it constantly, because
**collections only accept objects**:

```java
ArrayList<Integer> scores = new ArrayList<>();
scores.add(95);                  // ✅ autoboxed to Integer for you
```

That automatic conversion is called **autoboxing**.

```java
int a = 5;
Integer b = a;                   // boxing:   primitive → object
int c = b;                       // unboxing: object → primitive
```

**Rule of thumb:** use primitives (`int`, `double`) for normal variables.
You'll only touch wrappers when dealing with `ArrayList`, `HashMap`, or
generic types.

---

## Scope

A variable only exists inside the block `{ }` it was declared in.

```java
public static void main(String[] args) {
    int userId = 7;              // declared here

    if (true) {
        int temp = 99;           // only exists inside this if
        System.out.println(temp);
    }

    System.out.println(userId);  // ✅ fine, declared in the outer block
    // System.out.println(temp); ❌ temp is out of scope
}
```

**The rule:** a variable is visible from where it's declared to the end of
its enclosing `{ }`. If you need a variable somewhere else, pass it in as a
parameter.

---

## Common Mistakes

| Mistake | Problem | Fix |
|---|---|---|
| `String s = 'hi';` | single quotes are for `char` only | `"hi"` |
| `char c = 'hello';` | `char` holds one character | use `String` |
| Missing `;` | compile error on that line | add it |
| Using a variable before declaring it | compile error | declare first |
| `int x = "5";` | type mismatch | `Integer.parseInt("5")` |
| `a = b = 5;` | valid but confusing | write two lines |
| Case mismatch (`String` vs `string`) | compile error | Java is case-sensitive |

---

## Quick Reference

| Need | Write |
|---|---|
| Whole number | `int count = 5;` |
| Decimal / money | `double total = 19.99;` |
| Text | `String name = "Alice";` |
| Yes / no | `boolean paid = false;` |
| One character | `char grade = 'A';` |
| Can't change | `final double RATE = 0.045;` |
| Let Java pick the type | `var items = 5;` |
| Print | `System.out.println(x);` |
| Formatted print | `System.out.printf("%.2f", x);` |
| String → int | `Integer.parseInt(s);` |
| int → String | `String.valueOf(i);` |
| Fractional division | `(double) a / b;` |

---

## Key Takeaway

> **Declare with `type name = value;`, end every statement with `;`.**
> In practice you need four types: `int`, `double`, `boolean`, `String`.
> Two things to memorise: `String` is capitalised because it's a class, and
> `(double)` cast before dividing if you don't want the answer truncated.

---

Related: [02_Operators.md](02_Operators.md) · [03_Conditionals.md](03_Conditionals.md) ·
[../Libraries/Scanner.md](../Libraries/Scanner.md) (reading input) ·
[../oop/java_final_keyword_guide.md](../oop/java_final_keyword_guide.md) (`final`)
