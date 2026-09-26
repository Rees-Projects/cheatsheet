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

---

## Static Blocks

Sometimes you need to initialize static variables with logic that's more complex than a simple assignment. A **static block** (also called a **static initializer**) runs once when the class is first initialized — before any objects are created or static methods are called.

```java
public class DatabaseConfig {
    private static String connectionString;
    private static int maxConnections;
    
    static {
        // Complex initialization logic
        connectionString = "jdbc:mysql://localhost:3306/mydb";
        maxConnections = 10;
        System.out.println("Database configuration loaded");
    }
}
```

The static block executes automatically when the class is initialized. This happens **only once**, regardless of how many objects you create. It's perfect for initialization that requires multiple statements, calculations, or conditional logic.

### Multiple Static Blocks

You can have multiple static blocks in a class, and they execute in the order they appear:

```java
public class AppSettings {
    private static int[] values;
    
    static {
        values = new int[5];
    }
    
    static {
        for (int i = 0; i < values.length; i++) {
            values[i] = i * 10;
        }
    }
}
```

The second block depends on the first having already run, so order matters.

### Common Uses

* Initializing static arrays or collections
* Setting up configuration values that require computation
* Performing one-time setup tasks at the class level

---

## Execution Order

This is the part that trips people up. Java initializes in a fixed sequence:

```text
1. Static fields and static blocks   ← in the order they appear in the file
2. Instance fields and init blocks   ← per object, every time an object is made
3. Constructor body
```

```text
    static field
    static block
    static field
    static block
      ↓  all run once, top to bottom
    instance field
    instance block
      ↓  run for EACH new object
    constructor
```

Two consequences:

* Static blocks finish **before** any constructor runs, so a constructor can safely use values a static block set up.
* A static block runs only when the class is *initialized* — on the first `new`, or the first static member access. Merely compiling or declaring a class does nothing.

---

## Gotchas

* **Can't use `this`.** A static block has no instance context, so `this.field` won't compile. Only static members are in scope.
* **Can't assign to `static final` fields.** A `final` field must be assigned at its declaration, not in a block:
  ```java
  private static final int MAX = 10;              // ✅ assign at declaration
  private static final int MAX; static { MAX = 10; }  // ❌ compile error
  ```
  If you want a constant, declare it `static final` and initialize it inline — no block needed.
* **Blocks can't be triggered manually.** You don't call them. They run when the class initializes.
* **Exception risk.** If a static block throws, the class fails to initialize and you get an `ExceptionInInitializerError` — and it can be genuinely painful to debug, because the real cause is buried.

---

## Static Blocks vs Static Methods

```text
Static block
  • runs ONCE, automatically, at class initialization
  • for initialization only
  • cannot be called or re-run

Static method
  • runs every time you call it
  • for behaviour and work
  • callable via ClassName.method()
```

If you need to run the logic more than once, it's a static method, not a static block.
