# Instance vs Static Variables

So far, every field we've created belongs to a specific object. Each `BankAccount` has its own `balance`, and each `Product` has its own `name`. These are **instance variables** — they exist separately for each instance of a class.

But what if you need data that's shared across all objects? That's where **static variables** (also called class variables) come in. A static variable belongs to the class itself, not to any particular object.

## Code Example (Java)

```java
public class Student {
    private String name;           // Instance variable - unique per student
    private static int totalCount; // Static variable - shared by all students
    
    public Student(String name) {
        this.name = name;
        totalCount++;  // Increments the shared counter
    }
    
    public static int getTotalCount() {
        return totalCount;
    }
}
```

When you create multiple students, each has their own `name`, but they all share the same `totalCount`:

```java
Student s1 = new Student("Alice");
Student s2 = new Student("Bob");

System.out.println(Student.getTotalCount());  // Output: 2
```

Notice how we access the static variable through the **class name** (`Student.getTotalCount()`) rather than through an object instance. This emphasizes that static members belong to the class, not to individual instances.

---

## When to Use Which?

* **Instance Variables:** Use for data that varies between objects (e.g., a student's name, account balance).
* **Static Variables:** Use for data that should be shared across all instances (e.g., counting total objects created, global configuration constants).
