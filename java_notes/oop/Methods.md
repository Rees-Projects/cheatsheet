# Methods

Methods define **actions an object can perform**.

A method can have:
- A **return type**
- A **name**
- Optional **parameters**
- A **body** containing the code the method performs

---

# Basic Method Structure

```java
accessModifier returnType methodName(parameters) {
    // code
}
```

Example:

```java
public String sayHello() {
    return "Hello!";
}
```

Breaking it down:

```text
public      → access modifier
String      → return type
sayHello    → method name
()          → parameters
return      → sends a value back
```

---

# Method With No Parameters

A method does not have to receive any information.

```java
public class Greeter {

    public String sayHello() {
        return "Hello!";
    }
}
```

There are no parameters between the parentheses:

```java
sayHello()
```

Calling the method:

```java
Greeter greeter = new Greeter();

System.out.println(greeter.sayHello());
```

Output:

```text
Hello!
```

---

# Method With Parameters and a Return Type

A method can receive information through **parameters**.

```java
public class Calculator {

    public int add(int a, int b) {
        return a + b;
    }
}
```

Here:

```text
int    → return type
add    → method name
int a  → parameter
int b  → parameter
```

Calling the method:

```java
Calculator calc = new Calculator();

int result = calc.add(5, 3);

System.out.println(result);
```

Output:

```text
8
```

The values `5` and `3` are called **arguments** when the method is called.

```text
Parameters → variables defined by the method
Arguments  → actual values passed to the method
```

---

# Void Methods

A method does not always need to return a value.

Use `void` when the method performs an action but does not return data.

```java
public class Printer {

    public void printMessage(String msg) {
        System.out.println(msg);
    }
}
```

Calling the method:

```java
Printer printer = new Printer();

printer.printMessage("Hello!");
```

Output:

```text
Hello!
```

Because the method is `void`, there is no value to store.

---

# Return Types

The **return type** tells Java what kind of data the method sends back.

```java
public int getNumber() {
    return 10;
}
```

Returns an `int`.

```java
public String getName() {
    return "Buddy";
}
```

Returns a `String`.

```java
public boolean isAdult() {
    return true;
}
```

Returns a `boolean`.

```java
public void sayHello() {
    System.out.println("Hello!");
}
```

Returns nothing.

---

# Calling Methods

To call an instance method, you normally use an object:

```java
Calculator calc = new Calculator();

int result = calc.add(5, 3);
```

Think:

```text
object.method(arguments)
```

Example:

```java
calc.add(5, 3);
```

```text
calc       → object
add        → method
5, 3       → arguments
```

---

# Method Mental Model

Think of a method like a small machine:

```text
       INPUT
         ↓
    ┌──────────┐
    │  METHOD  │
    │   CODE   │
    └──────────┘
         ↓
       OUTPUT
```

Example:

```java
int result = calc.add(5, 3);
```

```text
5 + 3
  ↓
add()
  ↓
8
```

Not every method needs input or output.

```text
No input → Output

sayHello()
    ↓
"Hello!"
```

```text
Input → Output

add(5, 3)
    ↓
8
```

```text
Input → Action → No output

printMessage("Hello!")
    ↓
prints to console
```

---

# Quick Reference

| Part | Meaning |
|---|---|
| Return type | Type of data the method sends back |
| Method name | Name used to call the method |
| Parameter | Variable that receives input |
| Argument | Actual value passed to a method |
| `return` | Sends a value back |
| `void` | Method does not return a value |
| Method body | Code the method performs |

---

# Key Takeaways

- Methods define behavior/actions.
- Methods can receive input through parameters.
- Methods can return a value.
- `void` means the method does not return a value.
- The return type must match the value being returned.
- Parameters are defined in the method.
- Arguments are the actual values passed when calling the method.
- Methods can be called using an object.

The basic pattern:

```java
returnType methodName(parameters) {
    // code
    return value;
}
```

For a `void` method:

```java
void methodName(parameters) {
    // code
}
```

---

# My Notes

Use this section for things I personally learned, struggled with, or want to remember.

Examples:

```text
- A parameter is the variable in the method definition.
- An argument is the actual value I pass when calling the method.
- The return type tells me what type of data comes back.
- `void` means nothing is returned.
- A method is basically behavior/action that I can call.
```
