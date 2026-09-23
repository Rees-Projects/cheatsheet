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

## Quick Reference

| Method | Purpose |
|---|---|
| `nextInt()` | Reads an `int` |
| `nextDouble()` | Reads a `double` |
| `next()` | Reads the next token/word |
| `nextLine()` | Reads an entire line |

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
- `next()` and `nextLine()` behave differently.
- `nextInt()` reads an integer.
- `nextDouble()` reads a decimal number.
