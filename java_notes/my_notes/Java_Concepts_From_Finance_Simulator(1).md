# Java Concepts Learned — Finance Simulator

This note collects the Java concepts I practiced while building my finance simulator.

---

## 1. Methods and `()`

The parentheses `()` are used for a method's **parameters** when defining a method and **arguments** when calling it.

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

The method needs information from outside, so values go inside `()`.

### Method does not need input

```java
public double getPrincipal() {
    return this.principal;
}
```

Calling it:

```java
loan.getPrincipal();
```

Nothing needs to be supplied because the object already contains the information.

### Memory trick

```text
() = What information does this method need?
```

---

## 2. Parameters vs Arguments

These are related but different terms.

### Parameter

A **parameter** is the variable defined by the method.

```java
public double add(double num1, double num2)
```

`num1` and `num2` are parameters.

### Argument

An **argument** is the actual value passed when calling the method.

```java
add(5, 10);
```

`5` and `10` are arguments.

```text
Parameters = variables the method receives
Arguments  = actual values given to the method
```

---

## 3. Class vs Object

A **class** is the blueprint.

An **object** is an instance created from that blueprint.

```java
Loan mortgage = new Loan("Mortgage", 300000, 360, 6.5);
```

Breakdown:

```text
Loan       → class/type
mortgage   → variable referring to the object
new        → creates the object
Loan(...)  → calls the constructor
```

The important distinction is:

```java
Loan
```

refers to the type/class.

```java
mortgage
```

refers to a specific object.

So when a method receives:

```java
public static double calculateMonthlyPayment(Loan loan)
```

`loan` is the actual `Loan` object being worked with.

---

## 4. Call Methods on the Object, Not the Class

When working with an instance method, use the object:

```java
loan.getPrincipal();
loan.getNumMonths();
loan.getAnnualInterestRate();
```

Not:

```java
Loan.getPrincipal(); // Usually incorrect for an instance method
```

Think:

```text
Loan = blueprint/type
loan = actual object
```

The object contains the specific data.

---

## 5. Constructors

A constructor initializes an object when it is created.

```java
public Loan(
        String name,
        double principal,
        int numMonths,
        double annualInterestRate) {

    this.name = name;
    this.principal = principal;
    this.numMonths = numMonths;
    this.annualInterestRate = annualInterestRate;
}
```

Then:

```java
Loan mortgage = new Loan(
    "Mortgage",
    300000,
    360,
    6.5
);
```

The constructor receives the arguments and stores them in the new object.

---

## 6. `this`

`this` refers to the **current object**.

```java
this.name = name;
```

Here:

```text
this.name → field belonging to the object
name      → parameter being passed into the constructor
```

Example:

```java
public Loan(String name) {
    this.name = name;
}
```

---

## 7. Getters

A getter retrieves data from a private field.

```java
private double principal;

public double getPrincipal() {
    return this.principal;
}
```

Call it with:

```java
loan.getPrincipal();
```

### Important

A getter normally does **not** need the value as a parameter.

Incorrect:

```java
public double getPrincipal(double principal)
```

Correct:

```java
public double getPrincipal()
```

The object already knows its principal.

---

## 8. Setters

A setter changes a private field.

```java
public void setPrincipal(double principal) {
    this.principal = principal;
}
```

A setter can also validate data before changing it.

```java
public void setPrincipal(double principal) {
    if (principal > 0) {
        this.principal = principal;
    }
}
```

### Memory trick

```text
Getter → GET data
Setter → SET/change data
```

You do not always need both. A field can be read-only by providing a getter without a setter.

---

## 9. Encapsulation

Encapsulation means protecting an object's internal data and controlling how other code accesses it.

Common pattern:

```java
private double principal;

public double getPrincipal() {
    return principal;
}
```

Instead of:

```java
public double principal;
```

Think:

```text
private field
     ↓
public method
     ↓
controlled access
```

This is why the `Loan` class can keep its data private while `AmortizationSchedule` can still read it.

---

## 10. Variable Scope

A variable only exists within the scope where it was declared.

For example:

```java
public static void runMenu() {
    int userId = 1;
}
```

`userId` belongs to `runMenu()`.

It is not automatically available inside another method:

```java
public static void addExpense(...) {
    // userId is not automatically available here
}
```

If another method needs it, pass it as a parameter:

```java
addExpense(transactions, input, userId);
```

and receive it:

```java
public static void addExpense(
        ArrayList<Transaction> transactions,
        Scanner input,
        int userId) {
}
```

### Mental model

```text
runMenu()
   │
   │ userId
   ↓
addExpense(..., userId)
   │
   ↓
method can now use userId
```

---

## 11. Passing Objects to Methods

A method can receive an entire object as a parameter.

```java
public static double calculateMonthlyPayment(Loan loan) {
    double principal = loan.getPrincipal();
    int months = loan.getNumMonths();

    // calculations...
}
```

The method doesn't need separate parameters for every loan value because it receives the `Loan` object.

```text
Loan object
    ↓
calculateMonthlyPayment(loan)
    ↓
loan.getPrincipal()
loan.getNumMonths()
loan.getAnnualInterestRate()
```

This is useful because the `Loan` class owns the loan's data while the calculator uses that data.

---

## 12. Separating Responsibilities Between Classes

A class should have a clear job.

For the finance simulator:

```text
Transaction
    ↓
Stores transaction information

Loan
    ↓
Stores loan information

AmortizationSchedule
    ↓
Performs loan/amortization calculations

Projections
    ↓
Combines financial information to create projections
```

This keeps one class from becoming responsible for everything.

### Finance simulator example

```text
                 Finance Simulator
                         |
          ┌──────────────┼──────────────┐
          ↓              ↓              ↓
    Transactions       Loans       Projections
                           |
                           ↓
                 AmortizationSchedule
```

---

## 13. Model vs Calculator

A useful way to think about the classes:

### `Loan` = Model/Data

```java
Loan mortgage = new Loan(
    "Mortgage",
    300000,
    360,
    6.5
);
```

It answers:

> What information describes this loan?

### `AmortizationSchedule` = Calculations

```java
AmortizationSchedule.calculateMonthlyPayment(mortgage);
```

It answers:

> What does the math say about this loan?

This separation makes it easier to expand the program later.

---

## 14. Return vs `System.out.println()`

A calculation method should generally **return the result** rather than only print it.

Example:

```java
public static double calculateSomething() {
    double result = 100;
    return result;
}
```

Then another part of the program can use it:

```java
double result = calculateSomething();

System.out.println(result);
```

Why?

Because a returned value can be:

- printed
- stored
- used in another calculation
- sent through an API
- saved to a database

Printing only displays the value and does not give another part of the program the result to work with.

---

## 15. `void` Methods

Use `void` when a method performs an action but does not need to return a value.

```java
public void printLoan() {
    System.out.println("Mortgage");
}
```

Think:

```text
returning data:
calculatePayment() → $500

performing an action:
printLoan() → displays something
```

For your future API, returning data will often be more useful than having your calculation classes print directly to the console.

---

## 16. Amortization Mental Model

An amortizing loan is not simply:

```text
principal × interest rate
```

The balance changes every month.

The basic monthly process is:

```text
Starting Balance
       ↓
Calculate Monthly Interest
       ↓
Monthly Payment
       ↓
Payment - Interest = Principal Paid
       ↓
Starting Balance - Principal Paid
       ↓
New Balance
       ↓
Repeat
```

Example:

```text
Starting balance: $25,000
Annual interest:  6%

Monthly rate:
6% / 12 = 0.5%

Month 1 interest:
$25,000 × 0.005 = $125

If payment = $483:

Principal paid:
$483 - $125 = $358

New balance:
$25,000 - $358 = $24,642
```

Month 2 calculates interest using `$24,642`, not `$25,000`.

---

## 17. Important Naming Lessons

Java class names normally use **PascalCase**:

```java
AmortizationSchedule
Transaction
Loan
ExpenseTracker
```

Not:

```java
amortizationSchedule
```

Also watch spelling because variable names become part of your program's vocabulary.

Correct financial terms:

```text
principal
interest
```

Not:

```text
principle
intrest
```

---

# Quick Reference

| Concept | Remember |
|---|---|
| `()` | Input a method needs |
| Parameter | Variable defined by a method |
| Argument | Actual value passed to a method |
| Class | Blueprint/type |
| Object | Specific instance of a class |
| `new` | Creates an object |
| Constructor | Initializes an object |
| `this` | Current object |
| Getter | Gets data |
| Setter | Changes data |
| `private` | Restricts direct access |
| `public` | Allows access from other classes |
| Scope | Where a variable exists |
| `return` | Sends data back |
| `void` | Returns no value |
| Model class | Stores/describes data |
| Calculator/service class | Performs operations/calculations |

---

# My Finance Simulator Mental Model

The biggest lesson from today's work:

```text
OBJECTS HOLD DATA
        ↓
METHODS USE DATA
        ↓
CLASSES ORGANIZE RESPONSIBILITIES
        ↓
OBJECTS CAN BE PASSED BETWEEN METHODS
        ↓
CALCULATIONS RETURN RESULTS
        ↓
OTHER PARTS OF THE PROGRAM CAN USE THOSE RESULTS
```

That is the foundation I'm using to build my finance simulator.

---

# My Notes / Things I Want to Remember

- A class is not an object.
- `Loan` is the class; `loan` can be an object.
- If a method needs information, pass it through parameters.
- If a getter is simply retrieving an object's field, it normally needs empty `()`.
- Variables declared inside one method are not automatically available inside another method.
- Pass an object to another method when that method needs the object's data.
- Keep data classes focused on storing information and calculation classes focused on calculations.
- Prefer returning calculation results instead of printing them directly.
- `private` fields + public getters/setters are a common encapsulation pattern.
- I should build the logic first and then connect it to the database/API.
