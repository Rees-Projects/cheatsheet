# Math

## Package
```java
// no import needed — Math is in java.lang
```

## Rounding
```java
Math.abs(-5);       // 5      always positive
Math.round(4.5);    // 5      long  ← .5 rounds UP
Math.round(4.4);    // 4
Math.floor(4.9);    // 4.0    double, always down
Math.ceil(4.1);     // 5.0    double, always up
```

## Power & Roots
```java
Math.pow(2, 3);     // 8.0    double, second arg is the exponent
Math.sqrt(16);      // 4.0
Math.cbrt(27);      // 3.0    cube root
```

## Picking One
```java
Math.max(3, 7);     // 7
Math.min(3, 7);     // 3
Math.max(2.5, 1);   // 2.5
```

## Random Numbers
```java
Math.random();              // 0.0 (inclusive) to 1.0 (exclusive)
(int)(Math.random() * 100)  // 0 to 99

// better, clearer
import java.util.Random;
Random rand = new Random();
rand.nextInt(100);          // 0 to 99
rand.nextInt(1, 7);         // 1 to 6  ← dice
rand.nextDouble();          // 0.0 to 1.0
```

## Constants
```java
Math.PI      // 3.141592653589793
Math.E       // 2.718281828459045
```

## Logs & Trig
```java
Math.log(10);      // natural log (base e)
Math.log10(100);   // 2.0
Math.sin(1.0); Math.cos(1.0); Math.tan(1.0);
Math.toRadians(180);   // 3.14159...
Math.toDegrees(Math.PI);  // 180.0
```

## The Rounding Trap
```java
double price = 19.99;

System.out.println(price);                  // 19.99
System.out.println((int) price);            // 19      ⚠️ truncated
System.out.println(Math.round(price));      // 20      ✅ rounded
System.out.printf("%.2f", price);          // 19.99   ✅ 2 decimals

// Math.round returns long, so cast back to double
double rounded = Math.round(price);         // long 20 → double 20.0
```

```text
⚠️ (int) 19.99  → 19   cuts it off
   Math.round()  → 20   goes to the nearest
   %.0f          → 20   for printing
```

## Quick Reference
| Method | Does |
|---|---|
| `Math.abs(x)` | positive version |
| `Math.round(x)` | nearest whole number (`.5` goes up) |
| `Math.floor(x)` | always down |
| `Math.ceil(x)` | always up |
| `Math.pow(a,b)` | a to the power of b |
| `Math.sqrt(x)` | square root |
| `Math.max(a,b)` | the bigger one |
| `Math.min(a,b)` | the smaller one |
| `Math.random()` | 0.0 to 1.0 |
| `Math.PI` | pi |

## Things I Want to Remember
- No import needed, it's part of `java.lang`.
- `pow` takes two arguments: `pow(2, 3)` not `pow(23)`.
- `round()` returns a `long`, `floor()`/`ceil()` return `double`.
- `(int) 19.99` truncates to 19 — use `Math.round()` to actually round.
