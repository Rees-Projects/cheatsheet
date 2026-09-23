# ArrayList

## Package

```java
import java.util.ArrayList;
```

## What is it?

`ArrayList` is a resizable list that stores objects. Its size can grow or shrink as items are added or removed.

## Creating an ArrayList

```java
ArrayList<Transaction> transactions = new ArrayList<>();
```

## Methods I've Used

### `.add()`

Adds an object to the list.

```java
transactions.add(newTransaction);
```

### `.get()`

Gets an object at a specific index.

```java
Transaction transaction = transactions.get(0);
```

### `.size()`

Returns the number of items in the list.

```java
int numberOfTransactions = transactions.size();
```

### `.remove()`

Removes an item from the list.

```java
transactions.remove(0);
```

## Looping Through an ArrayList

```java
for (Transaction transaction : transactions) {
    System.out.println(transaction);
}
```

## Example From My Finance Simulator

```java
ArrayList<Transaction> transactions = new ArrayList<>();

transactions.add(newTransaction);

for (Transaction transaction : transactions) {
    System.out.println(transaction);
}
```

## Things I Want to Remember

- `ArrayList` stores objects.
- `add()` puts something into the list.
- `get()` retrieves something by index.
- `size()` tells me how many items are in the list.
- I can loop through an `ArrayList` with a for-each loop.
