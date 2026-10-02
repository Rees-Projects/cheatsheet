# Java Syntax — Notes Index

Plain Java language syntax: how to write it and when to reach for it. This is
the *language* reference — object-oriented design lives in [`../oop/`](../oop),
and specific library APIs in [`../Libraries/`](../Libraries).

Ordered roughly by how often each thing comes up in real code.

---

## Start Here

| File | What it covers |
|---|---|
| **[01_Basics.md](01_Basics.md)** | Program structure, `main`, comments, imports, variables, the 8 primitive types, `var`, printing with `println`/`printf`, casting, `parseInt`, boxing, scope |
| **[02_Operators.md](02_Operators.md)** | Arithmetic, `%`, compound assignment, `++`, comparison, `&&`/`\|\|`/`!`, string concatenation, ternary, bitwise, precedence |
| **[03_Conditionals.md](03_Conditionals.md)** | `if` / `else if` / `else`, blocks and scope, combined conditions, nesting, `switch` (classic + arrow), `switch` vs `if` |
| **[04_Loops.md](04_Loops.md)** | `for`, `while`, `do...while`, for-each, `break`/`continue`, nested loops, which loop to use, off-by-one |
| **[05_Arrays.md](05_Arrays.md)** | Declaration, indexing, `.length`, iteration, multi-dimensional arrays, the `Arrays` class, array vs `ArrayList` |

## Planned

Cross-references above point here — these don't exist yet.

| File | What it will cover |
|---|---|
| `06_Strings.md` | `String` methods (`.length`, `.substring`, `.charAt`, `.indexOf`, `.split`, `.equals`, `.contains`, `.replace`, `.trim`, `.toUpperCase`), `StringBuilder`, `==` vs `.equals()` |
| `07_Exceptions.md` | `try`/`catch`/`finally`, checked vs unchecked, `throw` vs `throws`, custom exceptions, `NumberFormatException` |
| `08_Collections.md` | `HashMap`, `HashSet`, `Map`/`Set`, `Collections.sort`, iterating with an index |
| `09_OOP_Syntax.md` | Interfaces in depth, `abstract`, `super`, `@Override`, method overloading, `instanceof`, `enum`, varargs, `record` |

---

## Conventions Used in These Notes

- Every construct is **how to write it**, then **when to use it** — that
  ordering is deliberate.
- Code fences are ` ```java ` (compilable, 4-space indent). Diagrams, memory
  aids and program output use ` ```text `.
- Illegal code is shown **commented out** with `❌` so you see the error rather
  than wondering why it's missing.
- Snippets are verified against **JDK 21**. Anything newer than that is
  labelled with its version.

## Where the Rest of the Notes Live

| Topic | Folder |
|---|---|
| Classes, objects, access modifiers, `static`, `final`, methods | [`../oop/`](../oop) |
| `ArrayList`, `Scanner`, `java.time` | [`../Libraries/`](../Libraries) |
| Method syntax in depth | [`../Methods/`](../Methods) |
| Project retrospective (finance simulator) | [`../my_notes/`](../my_notes) |

---

> **The three mistakes that cost the most marks:** integer division
> (`7 / 2` → `3`), `==` instead of `.equals()` on Strings, and `a.length()`
> instead of `a.length`. All three are covered above.
