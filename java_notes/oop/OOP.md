# Object-Oriented Programming (OOP)

## What is OOP?

**Object-Oriented Programming (OOP)** is a way to structure code using **objects** that contain data and behavior.

Java is heavily based around OOP.

Objects can contain:

- **Data** → fields/variables
- **Behavior** → methods

OOP gives you a way to organize larger programs into objects that represent things in your program.

---

# Class

A **class** is a blueprint for creating objects.

Think:

```text
Class = Blueprint
Object = Thing created from the blueprint
```

Example:

```java
public class Animal {
    String name;

    public Animal(String name) {
        this.name = name;
    }

    public String makeSound() {
        return this.name + " makes a sound!";
    }
}
```

The class describes what an `Animal` object has and what it can do.

---

# Object

An **object** is an instance of a class.

```java
Animal dog = new Animal("Buddy");

System.out.println(dog.makeSound());
```

Output:

```text
Buddy makes a sound!
```

### Breaking it down

```java
Animal dog = new Animal("Buddy");
```

```text
Animal       → class/type
dog          → variable that refers to the object
new          → creates a new object
Animal(...)  → calls the constructor
"Buddy"      → value passed to the constructor
```

---

# Constructor

A **constructor** is used when an object is created.

```java
public Animal(String name) {
    this.name = name;
}
```

When we do:

```java
Animal dog = new Animal("Buddy");
```

Java calls the constructor and passes `"Buddy"` into it.

---

# `this`

`this` refers to the **current object**.

```java
this.name = name;
```

In this example:

```text
this.name → the object's field
name      → the constructor parameter
```

---

# The Four Pillars of OOP

The four commonly taught pillars of OOP are:

1. **Encapsulation**
2. **Inheritance**
3. **Polymorphism**
4. **Abstraction**

---

## 1. Encapsulation

**Encapsulation** means keeping an object's data and behavior together while controlling access to its internal data.

Example:

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

Here `name` is `private`, so other classes cannot directly access it.

---

## 2. Inheritance

**Inheritance** allows one class to inherit fields and methods from another class.

Example:

```java
public class Animal {

    public void eat() {
        System.out.println("Eating...");
    }
}
```

A `Dog` can inherit from `Animal`:

```java
public class Dog extends Animal {

}
```

Now a `Dog` object can use the `eat()` method because it inherited it from `Animal`.

```java
Dog dog = new Dog();

dog.eat();
```

Think:

```text
Animal
   ↑
   |
  Dog
```

`Dog` is an `Animal`.

---

## 3. Polymorphism

**Polymorphism** means that different objects can be treated through a common type while still behaving according to their actual type.

Example:

```java
Animal dog = new Dog();
Animal cat = new Cat();
```

Both objects can be treated as `Animal` objects, but they can behave differently when they use overridden methods.

Polymorphism is especially useful when different classes share a common parent class or interface.

---

## 4. Abstraction

**Abstraction** means hiding unnecessary implementation details and exposing what is important.

For example:

```java
car.start();
```

You can use the method without needing to know every internal step required to start the engine.

In Java, abstraction is commonly achieved using:

- Abstract classes
- Interfaces

Example:

```java
public interface Animal {

    void makeSound();

}
```

A class can implement the interface:

```java
public class Dog implements Animal {

    public void makeSound() {
        System.out.println("Woof!");
    }
}
```

The interface says **what must be done**, while the class determines **how it is done**.

---

# What OOP Allows Me To Do

OOP gives me a way to:

- Create my own types
- Represent things as objects
- Give objects data/state
- Give objects behavior
- Create reusable classes
- Hide internal data
- Control how data is changed
- Reuse code through inheritance
- Allow different objects to share common behavior
- Use interfaces to define common behavior
- Build larger programs from smaller pieces
- Make code easier to organize and maintain

---

# OOP Mental Model

Think about a program like a collection of objects:

```text
                PROGRAM
                   |
        ┌──────────┼──────────┐
        ↓          ↓          ↓
      Dog        Person      Car
       |           |           |
     data        data        data
       |           |           |
    methods      methods     methods
```

Each object has:

```text
STATE + BEHAVIOR
```

**State** = what the object knows

**Behavior** = what the object can do

Example:

```text
Dog

State:
- name
- age
- breed

Behavior:
- bark()
- eat()
- sleep()
```

---

# Quick Reference

| Concept | Meaning |
|---|---|
| Class | Blueprint for objects |
| Object | Instance of a class |
| Field | Data/state belonging to an object |
| Method | Behavior/action |
| Constructor | Initializes an object |
| `this` | Refers to the current object |
| Encapsulation | Protect/control access to data |
| Inheritance | One class inherits from another |
| Polymorphism | Different objects can be treated through a common type |
| Abstraction | Hide unnecessary implementation details |
| Interface | Defines behavior a class agrees to provide |
| `extends` | Used for class inheritance |
| `implements` | Used when a class implements an interface |

---

# Important Distinction

This file explains **OOP concepts**.

It is not meant to be a complete list of Java methods.

Think of the Java reference like this:

```text
OOP
├── Classes
├── Objects
├── Constructors
├── Encapsulation
├── Inheritance
├── Polymorphism
└── Abstraction
```

Separate reference pages can contain:

```text
Java Methods
├── String methods
├── ArrayList methods
├── HashMap methods
├── LocalTime methods
├── Math methods
└── etc.
```

The goal is:

> **Understand the concept first. Use the method as a tool to implement the concept.**

---

# My Notes

Use this section for things I personally learned, struggled with, or want to remember.

Examples:

```text
- A class is not an object.
- `new` creates an object.
- A constructor runs when an object is created.
- `this` refers to the current object.
- OOP is about organizing code around objects and their behavior.
```

Add my own mistakes and explanations here as I learn.
