# Day 01 — Variables & Data Types
### Python Journey | Week 1

---

## Part 1 — What is Python & How It Works

Before writing a single line, understand this — Python is fundamentally different from Java in how it runs.

**Java** → you write code → compiler converts it to bytecode → JVM runs it
**Python** → you write code → interpreter reads and runs it LINE BY LINE

This means:
- No `public class Main {}` wrapper needed
- No `public static void main(String[] args)` needed
- No compile step — just write and run
- Errors show up at runtime, not compile time (this is a trap — explained below)

```python
# This is a complete, valid Python program — just 1 line!
print("Hello, World!")
```

```java
// Java needs all this just to print one line:
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello, World!");
    }
}
```

Python removes all the ceremony. You focus on logic, not boilerplate.

---

## Part 2 — Variables

### What is a variable?
A variable is a **named container** that stores a value in memory.
Think of it like a labelled box — you put something inside and refer to it by the label.

### Java vs Python

```java
// Java — you MUST declare the type
int age = 21;
double gpa = 8.75;
String name = "Arjun";
boolean isStudent = true;
```

```python
# Python — just assign, no type needed
age = 21
gpa = 8.75
name = "Arjun"
is_student = True
```

Python is **dynamically typed** — the type is attached to the VALUE, not the variable.
The variable `age` doesn't have a type. The value `21` has a type (int).

### Naming rules for variables
```python
# ✅ Valid names
age = 21
my_name = "Arjun"
_score = 95
value1 = 100

# ❌ Invalid names
1value = 10      # cannot start with number
my-name = "hi"   # hyphens not allowed
class = 5        # 'class' is a reserved keyword
```

Python convention: use `snake_case` (words separated by underscores)
Java convention: use `camelCase`

```python
# Python style ✅
student_name = "Arjun"
total_marks = 450

# Java style — works but not pythonic ❌
studentName = "Arjun"
```

### print() — Python's System.out.println()

```python
name = "Arjun"
age = 21

print("Hello")            # Hello
print(name)               # Arjun
print(age)                # 21
print(name, age)          # Arjun 21  ← print multiple values with comma
print("Name:", name)      # Name: Arjun
print()                   # blank line
```

---

## Part 3 — The 4 Basic Data Types

Python has 4 fundamental data types you'll use every single day.

---

### 3a. int — Integer (whole numbers)

```python
marks = 95
students = 30
negative = -10
zero = 0
big = 1_000_000     # underscores for readability (Python 3.6+)
                    # same as 1000000 — just easier to read

print(marks)        # 95
print(type(marks))  # <class 'int'>
```

**Arithmetic with int:**

```python
a = 10
b = 3

print(a + b)    # 13   — addition
print(a - b)    # 7    — subtraction
print(a * b)    # 30   — multiplication
print(a / b)    # 3.3333... ← IMPORTANT: always gives FLOAT in Python 3!
print(a // b)   # 3    — integer division (like Java's int/int)
print(a % b)    # 1    — modulo / remainder
print(a ** b)   # 1000 — exponent (10³), no Math.pow() needed!
```

> ⚠️ Java trap: In Java, `10 / 3 = 3` (integer). In Python, `10 / 3 = 3.333...` (float).
> Use `//` in Python to get Java-style integer division.

---

### 3b. float — Floating point (decimal numbers)

```python
gpa = 8.75
pi = 3.14159
temperature = -12.5
price = 99.99

print(gpa)          # 8.75
print(type(gpa))    # <class 'float'>
```

**Important float behavior:**

```python
print(10 / 2)       # 5.0   ← still float even if result is whole!
print(type(10 / 2)) # <class 'float'>

# Famous floating point issue (same in Java, C, every language):
print(0.1 + 0.2)    # 0.30000000000000004 ← not exactly 0.3!
# This is how computers store decimals — not a Python bug
```

---

### 3c. str — String (text)

A string is a **sequence of characters** enclosed in quotes.

```python
first_name = "Arjun"       # double quotes ✅
last_name = 'Sharma'       # single quotes ✅ — both work in Python!
empty = ""                 # empty string

# Java only allows double quotes for strings
# Python allows both — use whichever you prefer, be consistent
```

**String operations:**

```python
name = "Python"

print(len(name))            # 6        — length of string
print(name.upper())         # PYTHON   — uppercase
print(name.lower())         # python   — lowercase
print(name[0])              # P        — first character (index 0)
print(name[-1])             # n        — last character (negative index!)
print(name[0:3])            # Pyt      — slicing (characters 0,1,2)
```

**Concatenation — joining strings:**

```python
first = "Arjun"
last = "Sharma"

# Method 1: + operator
full = first + " " + last
print(full)                 # Arjun Sharma

# Method 2: f-strings (BEST WAY — use this always!)
print(f"Hello, {first} {last}!")   # Hello, Arjun Sharma!
```

**f-strings — your best friend in Python:**

```python
name = "Arjun"
age = 21
score = 95.678

# Put variable name inside {} — it gets replaced with the value
print(f"My name is {name}")                    # My name is Arjun
print(f"I am {age} years old")                 # I am 21 years old
print(f"Score: {score:.2f}")                   # Score: 95.68 (2 decimal places)
print(f"Next year I'll be {age + 1}")          # Next year I'll be 22
print(f"Is adult: {age >= 18}")                # Is adult: True
```

> f-strings are like Java's `String.format()` but much cleaner and more readable.
> Always prefer f-strings over `+` concatenation.

---

### 3d. bool — Boolean (True or False)

```python
is_raining = False
has_java_knowledge = True
is_logged_in = True

print(is_raining)           # False
print(type(is_raining))     # <class 'bool'>
```

> ⚠️ Java trap: Java uses `true` and `false` (lowercase).
> Python uses `True` and `False` (capital first letter). Always.

```python
# Comparisons give bool results:
print(5 > 3)       # True
print(5 == 3)      # False
print(5 != 3)      # True
print(10 >= 10)    # True
print(10 <= 9)     # False
```

**What is "truthy" and "falsy"?**
In Python, every value has a boolean meaning even without being True/False:

```python
# These are FALSY (act like False):
print(bool(0))        # False
print(bool(0.0))      # False
print(bool(""))       # False — empty string
print(bool(None))     # False — Python's null

# These are TRUTHY (act like True):
print(bool(1))        # True
print(bool(-99))      # True — any non-zero number
print(bool("hello"))  # True — any non-empty string
print(bool("False"))  # True ← TRAP! Non-empty string is always True
```

> The last one is a classic trap: `bool("False")` is `True` because `"False"` is a non-empty string!

---

## Part 4 — type() and isinstance()

### type() — tells you the type of any value

```python
print(type(42))          # <class 'int'>
print(type(3.14))        # <class 'float'>
print(type("hello"))     # <class 'str'>
print(type(True))        # <class 'bool'>
print(type(None))        # <class 'NoneType'>  ← Python's version of null
```

### isinstance() — checks if a value is of a certain type

```python
x = 42

print(isinstance(x, int))           # True
print(isinstance(x, str))           # False
print(isinstance(x, (int, float)))  # True ← check multiple types at once!
```

> Prefer `isinstance()` over `type()` for type checking in real code —
> it's safer and works better with inheritance (you'll learn this in OOP week).

---

## Part 5 — Type Conversion (Casting)

Converting one type to another is called **type conversion** or **casting**.

```python
# int() — convert to integer
print(int(3.9))      # 3   ← TRUNCATES (cuts off decimal), does NOT round!
print(int(3.1))      # 3   ← same! Decimal is just removed
print(int("42"))     # 42  ← string "42" to integer 42
print(int(True))     # 1
print(int(False))    # 0

# float() — convert to float
print(float(5))      # 5.0
print(float("3.14")) # 3.14
print(float("5"))    # 5.0

# str() — convert to string
print(str(100))      # "100"
print(str(3.14))     # "3.14"
print(str(True))     # "True"

# bool() — convert to boolean
print(bool(0))       # False
print(bool(1))       # True
print(bool(""))      # False
print(bool("hi"))    # True
```

> ⚠️ `int()` truncates, it does NOT round!
> `int(3.9)` gives `3`, not `4`.
> Use `round(3.9)` → `4` if you want rounding.

---

## Part 6 — Multiple Assignment & Swap

Python lets you assign multiple variables in one line:

```python
# Assign multiple variables at once
a, b, c = 10, 20, 30
print(a)    # 10
print(b)    # 20
print(c)    # 30

# Assign same value to multiple variables
x = y = z = 0
print(x, y, z)   # 0 0 0
```

**Swap without a temp variable — Python magic:**

```java
// Java — needs 3 lines and a temp variable
int temp = a;
a = b;
b = temp;
```

```python
# Python — one line, no temp variable!
a, b = 10, 20
a, b = b, a
print(a, b)   # 20 10
```

---

## Part 7 — input() — Taking User Input

```python
# input() always returns a STRING — this is a very common trap
name = input("Enter your name: ")
print(f"Hello, {name}!")

# If you need a number, you MUST convert it:
age = int(input("Enter your age: "))       # cast to int
gpa = float(input("Enter your GPA: "))    # cast to float

print(f"In 5 years you will be {age + 5}")
```

> ⚠️ Trap: `input()` always returns `str`. Even if the user types `25`, you get `"25"` not `25`.
> `"25" + 5` → TypeError! Always cast with `int()` or `float()` when you need numbers.

---

## 🚨 5 Big Traps Summary (Java developer edition)

| Trap | Java behavior | Python behavior |
|------|--------------|-----------------|
| Division | `10/3 = 3` (int) | `10/3 = 3.333` (float) — use `//` for int division |
| Boolean spelling | `true` / `false` | `True` / `False` — capital first letter |
| input() | `sc.nextInt()` returns int | `input()` always returns `str` — must cast! |
| Casting | `(int) 3.9 = 3` | `int(3.9) = 3` — truncates, NOT rounds |
| Type errors | Caught at compile time | Caught at runtime — silent bugs possible |

---

## 🔑 Key Takeaways

1. No type declarations — `x = 5` is all you need
2. No semicolons, no curly braces — indentation is the structure
3. 4 basic types: `int`, `float`, `str`, `bool`
4. `type(x)` checks type, `isinstance(x, int)` is better for checks
5. f-strings `f"Hello {name}"` — always use these for formatting
6. `10 / 3 = 3.333` in Python — use `//` for integer division
7. `input()` always returns `str` — always cast when you need a number
8. `True` / `False` — capital first letter always
9. `int(3.9) = 3` — truncates. Use `round(3.9) = 4` for rounding
10. `a, b = b, a` — swap in one line, no temp variable

---

## 🎯 Interview Output Questions

Answer all 5 below. Write your answers and paste them in the chat.
Code file drops after you answer! 💪

**Q1. What is the output?**
```python
print(10 / 2)
print(10 // 3)
print(10 % 3)
print(2 ** 4)
```

**Q2. What is the output?**
```python
x = 5
y = 2
print(x / y)
print(type(x / y))
print(x // y)
print(type(x // y))
```

**Q3. What is the output?**
```python
print(int(9.99))
print(round(9.5))
print(bool(0))
print(bool(""))
print(bool("False"))
```

**Q4. What is the output?**
```python
a, b = 100, 200
a, b = b, a
print(f"a={a}, b={b}")
```

**Q5. What is the output?**
```python
name = "Python"
version = 3
marks = 95.5678
print(f"{name} {version} is great!")
print(f"Score: {marks:.2f}")
print(f"Double version: {version * 2}")
```

---

Answer all 5 → I grade them → code file + repo content drops! 🚀