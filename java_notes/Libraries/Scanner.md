# Scanner

## Package
```java
import java.util.Scanner;
```

## What is it?
`Scanner` lets a Java program read input. I have mainly used it to read information entered by the user in the console.

## Creating a Scanner
```java
Scanner input = new Scanner(System.in);
```

## Methods I've Used

### `.nextInt()`
Reads an integer.
```java
int choice = input.nextInt();
```

### `.nextDouble()`
Reads a decimal number.
```java
double amount = input.nextDouble();
```

### `.next()`
Reads the next token/word.
```java
String category = input.next();
```

### `.nextLine()`
Reads the rest of the current line.
```java
String category = input.nextLine();
```

## ⚠️ next() vs nextLine()
This is the one that confuses me. They read from the same line differently.

Input line: `Boil water`

```java
input.next();       // "Boil"      — stops at the space
input.nextLine();   // " water"    — rest of the line, space included
```

Both read from the **same** line — `next()` takes one word, `nextLine()` takes
everything remaining on that line. They are not two different lines of input.

```text
⚠️ Asking for more once the input runs out throws NoSuchElementException.
   hasNextLine() first if you're not sure there's more.
```

```text
⚠️ nextInt() / nextDouble() / next() all leave the newline sitting there.
   So a nextLine() after them returns "" not the next line.
```

```java
Scanner input = new Scanner(System.in);

int age = input.nextInt();        // user types "30" then Enter
String name = input.nextLine();   // ❌ returns ""
input.nextLine();                 // ✅ the leftover newline
String name = input.nextLine();   // ✅ now this gets "Alice"
```

### The Fix — Always Follow a Number With a nextLine()
```java
int age = input.nextInt();
input.nextLine();                 // clear the leftover newline
String name = input.nextLine();   // "Alice" ✅
```

Or just use `nextLine()` for everything and convert:
```java
int age = Integer.parseInt(input.nextLine());
double amount = Double.parseDouble(input.nextLine());
```

## The Rest of Them
```java
input.hasNext();        // is there more?
input.hasNextInt();     // is the next one an int?
input.hasNextDouble();  // is the next one a decimal?
input.hasNextLine();    // is there another line?
input.close();          // tidy up when done
```

## ⚠️ Wrong Input Crashes the Program
```java
System.out.print("Enter amount: ");
double amount = input.nextDouble();
```
```text
⚠️ User types "abc" → InputMismatchException, program stops.
   Use hasNextDouble() to check first, or try/catch it.
```

```java
System.out.print("Enter amount: ");
double amount;
if (input.hasNextDouble()) {
    amount = input.nextDouble();
} else {
    System.out.println("That wasn't a number.");
    amount = 0.0;
}
```

## Quick Reference
| Method | Reads |
|---|---|
| `nextInt()` | an `int` |
| `nextDouble()` | a `double` |
| `next()` | the next word |
| `nextLine()` | the whole line |
| `hasNext()` | anything at all |
| `hasNextInt()` | is the next an `int` |
| `close()` | shut the Scanner |

## Example From My Finance Simulator
```java
Scanner input = new Scanner(System.in);

System.out.print("Enter amount: ");
double amount = input.nextDouble();

System.out.print("Enter category: ");
String category = input.next();
```

## Things I Want to Remember
- `Scanner` reads input.
- `next()` and `nextLine()` behave differently — `next()` stops at spaces.
- `nextInt()` reads an integer.
- `nextDouble()` reads a decimal number.
- After `nextInt()`/`nextDouble()`/`next()`, add a `nextLine()` to clear the newline.
- `hasNextInt()` / `hasNextDouble()` check the input before reading it.
