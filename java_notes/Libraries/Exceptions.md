# Exceptions

## Throwing and Catching
```java
try {
    int age = Integer.parseInt(text);   // risky line
} catch (NumberFormatException e) {
    System.out.println("That wasn't a number.");
}
```
```text
try      → run it, it might break
catch    → what to do if it does
finally  → always runs, error or not
```

## finally
```java
try {
    System.out.println("working");
} catch (Exception e) {
    System.out.println("failed");
} finally {
    System.out.println("always runs");
}
```

## The Common Ones
```java
Integer.parseInt("abc");    // NumberFormatException
list.get(99);                // IndexOutOfBoundsException
array[99];                   // ArrayIndexOutOfBoundsException
null.length();               // NullPointerException
10 / zero;                   // ArithmeticException
(Integer)"str";              // ClassCastException
```
```java
try { int age = Integer.parseInt(text); }
catch (NumberFormatException e) { /* wasn't a number */ }

try { String n = list.get(i); }
catch (IndexOutOfBoundsException e) { /* index too big */ }
```

## Catch Anything
```java
try { risky(); }
catch (Exception e) {
    System.out.println(e.getMessage());   // why it happened
}
```
```text
⚠️ Catch the specific type when you can. Catching Exception hides real bugs.
```

## Throwing Your Own
```java
if (age < 0) {
    throw new IllegalArgumentException("Age cannot be negative");
}
```
```java
public void withdraw(double amount) throws InsufficientFundsException {
    if (amount > balance) {
        throw new InsufficientFundsException("Not enough money");
    }
    balance -= amount;
}
```

## try-with-resources (closes for you)
```java
try (Scanner input = new Scanner(System.in)) {
    System.out.println(input.nextLine());
}   // closed automatically here

try (BufferedReader br = new BufferedReader(new FileReader("data.txt"))) {
    System.out.println(br.readLine());
} catch (IOException e) {
    System.out.println("Couldn't read the file.");
}
```

```text
⚠️ FileReader throws a checked exception (IOException), so you must catch it
   or declare throws. Scanner doesn't need this.
```

## Quick Reference
| Keyword | Does |
|---|---|
| `try` | risky code |
| `catch (Type e)` | handle that problem |
| `catch (Exception e)` | handle anything |
| `finally` | always runs |
| `throw new X()` | cause an exception |
| `throws X` | this method might throw X |
| `e.getMessage()` | the error text |
| `e.printStackTrace()` | print the whole error |

## Things I Want to Remember
- `catch` only runs if something actually went wrong.
- `finally` always runs — good for cleanup.
- Catch the specific type, not `Exception`.
- `Scanner` and files should use try-with-resources.

Full detail: [../syntax/07_Exceptions.md](../syntax/07_Exceptions.md)
