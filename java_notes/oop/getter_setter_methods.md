# Getter and Setter Methods

Getters and setters are methods that provide controlled access to private fields.

- A **getter** retrieves a field's value.
- A **setter** modifies a field's value.

## Naming Convention

The standard naming convention is:

- `get` + field name with the first letter capitalized
- `set` + field name with the first letter capitalized

For example, a field named `name` uses `getName()` and `setName()`.

## Basic Example

```java
public class Product {
    private String name;
    private double price;

    // Getter for name
    public String getName() {
        return name;
    }

    // Setter for name
    public void setName(String name) {
        this.name = name;
    }

    // Getter for price
    public double getPrice() {
        return price;
    }

    // Setter with validation
    public void setPrice(double price) {
        if (price >= 0) {
            this.price = price;
        }
    }
}
```

## Why Use Getters and Setters?

Because the fields are `private`, code outside the class cannot directly access them.

Instead, external code can use the getter and setter methods:

```java
Product product = new Product();

product.setName("Laptop");
product.setPrice(999.99);

System.out.println(product.getName());
System.out.println(product.getPrice());
```

This gives the class control over how its data is accessed and changed.

## Setters Can Validate Data

One of the most useful features of setters is that they can contain validation logic.

In the example:

```java
public void setPrice(double price) {
    if (price >= 0) {
        this.price = price;
    }
}
```

The setter only accepts non-negative prices.

This helps protect the object from invalid data.

For example:

```java
product.setPrice(-50);
```

The setter will reject the value because `-50` is not valid according to the rule.

### Important Idea

Think of a setter as a **gatekeeper**:

```text
Outside Code
     |
     v
 setPrice(999.99)
     |
     v
 Validation
     |
     +---- Valid ----> Update field
     |
     +---- Invalid --> Reject value
```

## Boolean Getters

For boolean fields, getters typically use the prefix `is` instead of `get`.

```java
private boolean active;

public boolean isActive() {
    return active;
}
```

Usage:

```java
if (product.isActive()) {
    System.out.println("Product is active");
}
```

## Read-Only and Write-Only Fields

You do not have to provide both a getter and a setter.

### Read-Only

Provide only a getter:

```java
private String productId;

public String getProductId() {
    return productId;
}
```

External code can read the value but cannot change it through a setter.

### Write-Only

Provide only a setter:

```java
private String password;

public void setPassword(String password) {
    this.password = password;
}
```

External code can provide a value, but there is no getter to retrieve it.

> In real applications, write-only fields are less common, but the pattern is possible.

## Quick Cheat Sheet

| Method | Purpose | Example |
|---|---|---|
| Getter | Retrieves a value | `getName()` |
| Setter | Changes a value | `setName("Laptop")` |
| Boolean getter | Retrieves a boolean | `isActive()` |
| Read-only | Getter without setter | `getProductId()` |
| Write-only | Setter without getter | `setPassword()` |

## Key Takeaway

**Getters get data. Setters set data.**

They are especially useful with `private` fields because they give a class **controlled access** to its internal data.

A setter can also enforce rules and validation before changing the field.

```text
private field
     |
     v
Getter ---> Read the value
     |
Setter ---> Validate and change the value
```
