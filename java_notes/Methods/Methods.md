# Java Methods — Personal Reference

## What is a Method?

A method is a block of code designed to perform a specific task.

```java
public double calculateTotal(double amount) {
    return amount;
}
```

---

## Parentheses `()`

The parentheses tell me what information a method receives.

### Method needs input

```java
public double add(double num1, double num2) {
    return num1 + num2;
}
```

Calling it:

```java
add(5, 10);
```

### Method does not need input

```java
public double getPrincipal() {
    return principal;
}
```

Calling it:

```java
loan.getPrincipal();
```

### Memory trick

```text
() = What information does this method need?
```

---

# Parameters vs Arguments

### Parameter

A parameter is the variable defined by the method.

```java
public double add(double num1, double num2)
```

`num1` and `num2` are parameters.

### Argument

An argument is the actual value passed when calling the method.

```java
add(5, 10);
```

`5` and `10` are arguments.

```text
Parameters = variables the method receives
Arguments  = actual values given to a method
```

---

# Return

`return` sends a value back to whatever called the method.

```java
public double calculateTotal() {
    double total = 100;
    return total;
}
```

Then:

```java
double result = calculateTotal();
```

The returned value can be stored, printed, or used in another calculation.

---

# `void`

Use `void` when a method performs an action but does not return a value.

```java
public void printLoan() {
    System.out.println("Mortgage");
}
```

Think:

```text
calculatePayment() → returns data
printLoan()        → performs an action
```

---

# Passing Objects to Methods

A method can receive an entire object.

```java
public static double calculateMonthlyPayment(Loan loan) {
    double principal = loan.getPrincipal();
    int months = loan.getNumMonths();

    // calculations...
}
```

The `Loan` object contains the information needed by the calculator.

---

# Variable Scope

A variable only exists within its scope.

```java
public static void runMenu() {
    int userId = 1;
}
```

`userId` exists inside `runMenu()`. Another method cannot automatically use it.

Pass it as a parameter when needed:

```java
addExpense(transactions, input, userId);
```

And receive it:

```java
public static void addExpense(
        ArrayList<Transaction> transactions,
        Scanner input,
        int userId) {
}
```

---

# Things I Want to Remember

- `()` contains method parameters when defining a method.
- `()` contains arguments when calling a method.
- A getter usually has empty `()`.
- Pass information into a method when the method needs it.
- `return` sends data back.
- `void` means the method does not return a value.
- A method cannot automatically see local variables from another method.
- Objects can be passed into methods as parameters.
