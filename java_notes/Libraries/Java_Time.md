# Java Time

## Package

```java
import java.time.*;
```

Java's `java.time` package provides classes for working with dates and times.

---

# LocalDate

`LocalDate` represents a date without a time.

```java
import java.time.LocalDate;
```

## Creating Today's Date

```java
LocalDate date = LocalDate.now();
```

## Useful Methods

### `.now()`

Gets the current date.

```java
LocalDate today = LocalDate.now();
```

### `.plusDays()`

Adds days.

```java
LocalDate future = today.plusDays(30);
```

### `.minusDays()`

Subtracts days.

```java
LocalDate previous = today.minusDays(30);
```

---

# LocalTime

`LocalTime` represents a time without a date.

```java
import java.time.LocalTime;
```

## Parsing a Time

```java
LocalTime time = LocalTime.parse("14:30");
```

## Useful Methods

### `.plusHours()`

```java
LocalTime later = time.plusHours(2);
```

### `.plusMinutes()`

```java
LocalTime later = time.plusMinutes(30);
```

### `.minusHours()`

```java
LocalTime earlier = time.minusHours(2);
```

### `.minusMinutes()`

```java
LocalTime earlier = time.minusMinutes(30);
```

## Things I Want to Remember

- `LocalDate` = date only.
- `LocalTime` = time only.
- `LocalDateTime` = date + time.
- `now()` gets the current date/time for the relevant class.
- `parse()` converts a properly formatted string into a date/time object.
