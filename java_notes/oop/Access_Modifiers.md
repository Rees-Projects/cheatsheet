# OOP — Access Levels & Access Modifiers

Access modifiers control **where fields and methods can be accessed from**.

Java has four levels of access control:

| Modifier | Same Class | Same Package | Subclass | Everywhere |
|---|---|---|---|---|
| `private` | Yes | No | No | No |
| default (no keyword) | Yes | Yes | No | No |
| `protected` | Yes | Yes | Yes | No |
| `public` | Yes | Yes | Yes | Yes |

## The Big Idea

Think of access levels like doors with different locks:

- `private` → **Only this class**
- default → **Anyone in the same package**
- `protected` → **Same package + subclasses**
- `public` → **Anyone**

### Example

```java
public class BankAccount {
    private double balance;      // Only this class
    String accountType;          // Default: same package only
    protected String owner;      // Same package + subclasses
    public String bankName;      // Accessible everywhere
}
```

## `private`

`private` is the **most restrictive** access level.

Use it for internal data that should not be accessed directly by other classes.

```java
public class BankAccount {
    private double balance;
}
```

Another class cannot do this:

```java
account.balance = 1000000;
```

Instead, you control access through methods:

```java
public void deposit(double amount) {
    balance += amount;
}

public double getBalance() {
    return balance;
}
```

This is an important part of **encapsulation**.

## Default (Package-Private)

When you don't specify an access modifier, Java uses **default access**, also called **package-private**.

It allows access only from classes in the **same package**.

```java
class Helper {
    void assist() {
    }
}
```

Both the class and method above have default access.

## `protected`

`protected` allows access from:

- The same class
- Classes in the same package
- Subclasses

```java
public class BankAccount {
    protected String owner;
}
```

## `public`

`public` is the **most open** access level.

A public field or method can be accessed from anywhere the class itself is accessible.

```java
public class BankAccount {
    public String bankName;
}
```

Methods that other classes need to call are commonly `public`.

## Access Modifiers & Encapsulation

Access modifiers are closely connected to **encapsulation**, one of the four pillars of OOP.

Encapsulation means keeping an object's internal data protected and controlling how other code interacts with it.

For example:

```java
public class BankAccount {

    private double balance;

    public void deposit(double amount) {
        balance += amount;
    }

    public double getBalance() {
        return balance;
    }
}
```

Instead of allowing other classes to directly change `balance`, the class controls how it is changed.

```java
account.deposit(100);
```

This is safer than giving everyone direct access to the field.

## Quick Memory Trick

Think:

```text
private    → ME
default    → MY PACKAGE
protected  → MY PACKAGE + MY CHILDREN
public     → EVERYONE
```

Or remember the progression:

```text
private → default → protected → public
  🔒        🏠          🛡️          🌎
```

## Best Practice

> **Choose the most restrictive access level that still allows your code to work.**

This helps:

- Protect your data
- Prevent accidental changes
- Make your code easier to understand
- Make your code easier to maintain
- Support encapsulation

### Common Pattern

A very common Java pattern is:

```java
private field
public method
```

For example:

```java
public class Person {

    private String name;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

The field is protected from direct access, while public methods provide controlled access.

---

# OOP Connection

Access modifiers → **Encapsulation**

Encapsulation → **Protect the object's data and control how it is accessed**

A useful way to think about it:

```text
Object
│
├── private data
│     └── protected from direct outside access
│
└── public methods
      └── controlled way to interact with the data
```

## Four Access Levels at a Glance

| Access Level | Who Can Access It? |
|---|---|
| `private` | Same class |
| default | Same class + same package |
| `protected` | Same class + same package + subclasses |
| `public` | Everywhere |
