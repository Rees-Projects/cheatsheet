# Java Exceptions (Try/Catch)

## What is it?
When something goes wrong at runtime, Java **throws** an exception instead of
just stopping. `try/catch` lets you handle it and keep going.

## The Basic Shape
```java
try {
    int age = Integer.parseInt(input);   // might fail
    System.out.println(age);
} catch (NumberFormatException e) {
    System.out.println("That wasn't a number.");
}
```

```text
  try      → run this code, it might break
  catch    → here's what to do if it does
  finally  → always runs, error or not
```

## finally Runs Either Way
```java
try {
    System.out.println("working");
} catch (Exception e) {
    System.out.println("failed");
} finally {
    System.out.println("always runs");
}
```

Use it for cleanup — closing files, releasing resources.

## Catching the Ones You'll Meet
```java
try {
    int age = Integer.parseInt(text);
} catch (NumberFormatException e) {
    // text wasn't a number
}

try {
    String name = list.get(index);
} catch (IndexOutOfBoundsException e) {
    // index was too big
}

try {
    System.out.println(name.length());
} catch (NullPointerException e) {
    // name was null
}

try {
    int result = 10 / 0);
} catch (ArithmeticException e) {
    // divided by zero
}
```

## Catching Any Exception
```java
try {
    // risky code
} catch (Exception e) {
    // catches everything
    System.out.println(e.getMessage());   // why it happened
}
```

```text
⚠️ Catch the specific exception, not Exception, when you can.
   Catching everything hides real bugs.
```

## Throwing Your Own
```java
if (age < 0) {
    throw new IllegalArgumentException("Age cannot be negative");
}
```

```java
// in a method that can throw
public void withdraw(double amount) throws InsufficientFundsException {
    if (amount > balance) {
        throw new InsufficientFundsException("Not enough money");
    }
    balance -= amount;
}
```

## try-with-resources — Closes Files For You
```java
try (Scanner input = new Scanner(System.in)) {
    System.out.println(input.nextLine());
}   // input closed automatically here
```

```java
try (BufferedReader br = new BufferedReader(new FileReader("data.txt"))) {
    System.out.println(br.readLine());
} catch (IOException e) {
    System.out.println("Couldn't read the file.");
}
```

```text
⚠️ File reading throws a checked exception (IOException), so it must be
   caught or declared with throws. Scanner and most other things don't.
```

Cleaner than a manual `finally { input.close(); }`, and it closes the file even
if the code inside throws.

## Common Exceptions
| Exception | Happens when |
|---|---|
| `NumberFormatException` | parsing a bad number from text |
| `NullPointerException` | using something that's `null` |
| `ArrayIndexOutOfBoundsException` | index past the end of an array |
| `IndexOutOfBoundsException` | index past the end of a list |
| `ArithmeticException` | divide by zero |
| `IllegalArgumentException` | bad argument passed in |
| `ClassCastException` | casting to the wrong type |
| `InputMismatchException` | Scanner gets text when it wants a number |

## Quick Reference
| Keyword | Does |
|---|---|
| `try { }` | run this, it might throw |
| `catch (Type e) { }` | handle a specific problem |
| `catch (Exception e) { }` | handle anything |
| `finally { }` | always runs |
| `throw new X()` | cause an exception yourself |
| `throws X` | say a method might throw this |
| `e.getMessage()` | the error message |
| `e.printStackTrace()` | print the whole error |

## Things I Want to Remember
- `try` = risky code, `catch` = what to do about it.
- `catch` runs **only** if something went wrong. No error, no catch.
- `finally` always runs — good for cleanup.
- Catch the specific type, not `Exception`.
- `Scanner` and file reading should use try-with-resources.
