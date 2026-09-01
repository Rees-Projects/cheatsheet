# Classes vs Objects

A **class** is a blueprint that defines the structure and behavior of an object.

An **object** is a specific instance created from that class.

Think:

```text
Class  = Blueprint
Object = Instance built from the blueprint
```

---

## The Class (Blueprint)

```java
public class Car {
    String brand;
    int year;

    public Car(String brand, int year) {
        this.brand = brand;
        this.year = year;
    }

    public String getInfo() {
        return this.brand + " (" + this.year + ")";
    }
}
```

The `Car` class defines what a car object has:

- `brand`
- `year`

It also defines what a car object can do:

- `getInfo()`

---

## Creating Objects (Instances)

You can create multiple objects from the same class.

```java
Car car1 = new Car("Tesla", 2023);
Car car2 = new Car("Honda", 2020);

System.out.println(car1.getInfo());
System.out.println(car2.getInfo());
```

Output:

```text
Tesla (2023)
Honda (2020)
```

---

## Each Object Has Its Own Data

Even though both objects were created from the same `Car` class, they contain different data.

```text
Car class
    |
    ├── car1
    │    ├── brand = Tesla
    │    └── year = 2023
    │
    └── car2
         ├── brand = Honda
         └── year = 2020
```

Changing `car1` does not automatically change `car2`.

Each object has its own instance data.

---

## Class vs Object

| Class | Object |
|---|---|
| Blueprint | Instance |
| Defines structure | Contains actual data |
| Defines behavior | Uses that behavior |
| `Car` | `car1` |
| Describes what a car has | Represents one specific car |

---

## Important Mental Model

When you see:

```java
Car car1 = new Car("Tesla", 2023);
```

Think:

```text
Car
 ↓
Class/type

car1
 ↓
Variable referring to an object

new Car(...)
 ↓
Creates a new Car object

"Tesla", 2023
 ↓
Data passed to the constructor
```

---

## Key Takeaway

> **A class is the blueprint. An object is an instance created from that blueprint.**

One class can be used to create many objects, and each object can have its own data.

```text
          Car Class
             |
     ┌───────┼───────┐
     ↓       ↓       ↓
   car1    car2    car3
  Tesla   Honda    Ford
  2023    2020     2024
```

This is one of the fundamental ideas behind Object-Oriented Programming.
