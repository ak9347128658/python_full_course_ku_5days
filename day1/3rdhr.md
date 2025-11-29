# Day 1 - Hour 3: Operators & Expressions

## Welcome to Hour 3!

You now know variables and datatypes. Today we're learning **operators** - the symbols that let us do things with values. Addition, subtraction, comparison, logic... all powered by operators!

Think of operators as the tools in your toolbox. Variables are the materials, operators are how you shape them.

---

## What is an Operator?

An **operator** is a symbol that tells Python to perform a specific operation on one or more values.

```python
x = 5 + 3      # + is the operator, 5 and 3 are operands
result = x * 2 # * is the operator, x and 2 are operands
```

---

## 1. Arithmetic Operators

These perform mathematical operations.

### Addition `+`

```python
a = 10
b = 5
result = a + b
print(result)               # 15

# Also works with strings (concatenation)
first_name = "John"
last_name = "Doe"
full_name = first_name + " " + last_name
print(full_name)            # John Doe
```

### Subtraction `-`

```python
x = 20
y = 8
print(x - y)                # 12
print(5 - 10)               # -5
```

### Multiplication `*`

```python
length = 5
width = 3
area = length * width
print(area)                 # 15

# String repetition
print("Ha" * 3)             # HaHaHa
print("=" * 10)             # ==========
```

### Division `/`

Always returns a float:

```python
a = 10
b = 2
print(a / b)                # 5.0 (NOT 5!)

c = 7
d = 2
print(c / d)                # 3.5
```

### Floor Division `//`

Divides and rounds down:

```python
print(10 // 3)              # 3
print(10 // 2)              # 5
print(-10 // 3)             # -4 (rounds DOWN)
```

### Modulo `%`

Gives the remainder:

```python
print(10 % 3)               # 1 (10 divided by 3 is 3 remainder 1)
print(10 % 2)               # 0 (10 is divisible by 2)
print(17 % 5)               # 2

# Check if a number is even
number = 4
if number % 2 == 0:
    print("Even")
```

### Exponentiation `**`

Raises to a power:

```python
print(2 ** 3)               # 8 (2 to the power of 3)
print(5 ** 2)               # 25
print(10 ** -1)             # 0.1
```

---

## 2. Comparison Operators

These compare two values and return `True` or `False`.

### Equal to `==`

```python
x = 5
y = 5
print(x == y)               # True

print("hello" == "hello")   # True
print(5 == "5")             # False (different types)
```

### Not equal to `!=`

```python
print(5 != 3)               # True
print(5 != 5)               # False
```

### Greater than `>`

```python
print(10 > 5)               # True
print(3 > 5)                # False
print(5 > 5)                # False
```

### Less than `<`

```python
print(3 < 5)                # True
print(10 < 5)               # False
```

### Greater than or equal to `>=`

```python
print(5 >= 5)               # True
print(6 >= 5)               # True
print(4 >= 5)               # False
```

### Less than or equal to `<=`

```python
print(5 <= 5)               # True
print(4 <= 5)               # True
print(6 <= 5)               # False
```

---

## 3. Logical Operators

These combine conditions.

### AND `and`

Returns `True` if ALL conditions are true:

```python
age = 25
has_license = True

if age >= 18 and has_license:
    print("You can drive")      # This prints

# Both must be True
print(True and True)            # True
print(True and False)           # False
print(False and False)          # False
```

### OR `or`

Returns `True` if ANY condition is true:

```python
is_weekend = False
is_vacation = True

if is_weekend or is_vacation:
    print("No work today!")      # This prints

# At least one must be True
print(True or False)            # True
print(False or False)           # False
```

### NOT `not`

Reverses a boolean:

```python
is_raining = True
print(not is_raining)           # False

is_sunny = False
print(not is_sunny)             # True

if not is_sunny:
    print("Bring an umbrella")   # This prints
```

---

## 4. Assignment Operators

These assign and modify values.

### Basic assignment `=`

```python
x = 10
```

### Add and assign `+=`

```python
x = 10
x += 5                          # x = x + 5
print(x)                        # 15
```

### Subtract and assign `-=`

```python
x = 10
x -= 3                          # x = x - 3
print(x)                        # 7
```

### Multiply and assign `*=`

```python
x = 10
x *= 2                          # x = x * 2
print(x)                        # 20
```

### Divide and assign `/=`

```python
x = 10
x /= 2                          # x = x / 2
print(x)                        # 5.0
```

---

## 5. Membership Operators

Check if something exists in a sequence.

### `in`

```python
fruits = ["apple", "banana", "orange"]
print("apple" in fruits)        # True
print("grape" in fruits)        # False

text = "Hello World"
print("H" in text)              # True
print("xyz" in text)            # False
```

### `not in`

```python
print("grape" not in fruits)    # True
print("apple" not in fruits)    # False
```

---

## Operator Precedence

When multiple operators exist, Python follows order of operations (like math!).

```python
# Order: ** then * / // % then + -
result = 2 + 3 * 4
print(result)                   # 14 (NOT 20!)
# Because: 3 * 4 = 12, then 2 + 12 = 14

result = (2 + 3) * 4
print(result)                   # 20 (parentheses first!)
```

**Complete precedence from highest to lowest:**
1. `**` (Exponentiation)
2. `*, /, //, %` (Multiplication, Division)
3. `+, -` (Addition, Subtraction)
4. `==, !=, <, >, <=, >=` (Comparisons)
5. `not` (Logical NOT)
6. `and` (Logical AND)
7. `or` (Logical OR)

---

## Expressions

An **expression** is a combination of values, variables, and operators that produces a result.

```python
# Simple expression
5 + 3                           # Expression = 8

# Expression with variables
x = 10
y = 5
x + y * 2                       # Expression = 20

# Expression with multiple operators
result = (5 + 3) * 2 - 1        # Expression = 15

# Boolean expression
age = 25
age > 18 and age < 65           # Expression = True
```

---

## Real-World Examples

### Example 1: Calculate Discount

```python
original_price = 100
discount_percentage = 20

discount_amount = original_price * (discount_percentage / 100)
final_price = original_price - discount_amount

print(f"Original: ${original_price}")
print(f"Discount: ${discount_amount}")
print(f"Final Price: ${final_price}")
```

Output:
```
Original: $100
Discount: $20.0
Final Price: $80.0
```

### Example 2: Check Eligibility

```python
age = 25
has_experience = True
has_degree = False

eligible = (age >= 21) and (has_experience or has_degree)
print(f"Eligible for job: {eligible}")       # True
```

### Example 3: Calculate Grade

```python
score = 85
passing_score = 60

is_passing = score >= passing_score
print(f"Passing: {is_passing}")               # True

percentage = (score / 100) * 100
print(f"Percentage: {percentage}%")           # 85.0%
```

---

## Exercises

### Exercise 1: Basic Arithmetic

Create `arithmetic.py`:

```python
# Calculate the area of a rectangle
length = 10
width = 5
area = length * width
print(f"Area: {area}")

# Calculate compound interest
principal = 1000
rate = 0.05
time = 2
compound_interest = principal * (1 + rate) ** time
print(f"Future Value: ${compound_interest}")
```

### Exercise 2: Comparisons

Create `comparisons.py`:

```python
# Check if someone can vote
age = 20
can_vote = age >= 18
print(f"Can vote: {can_vote}")

# Check if number is even
number = 7
is_even = number % 2 == 0
print(f"Is even: {is_even}")

# Multiple conditions
score = 75
subject = "Math"
passed = (score >= 60) and (subject != "")
print(f"Passed: {passed}")
```

### Exercise 3: Logical Operators

Create `logic.py`:

```python
# Check if it's a good day for outdoor activity
is_sunny = True
is_weekend = True
temperature = 22

good_day = (is_sunny and is_weekend) or (temperature > 20)
print(f"Good day for outdoor: {good_day}")

# Check access permissions
is_admin = False
is_owner = True
has_access = is_admin or is_owner
print(f"Has access: {has_access}")
```

---

## Common Mistakes

```python
# ✗ WRONG - Using = in comparison
if x = 5:
    print("x is 5")

# ✓ CORRECT - Using == for comparison
if x == 5:
    print("x is 5")

# ✗ WRONG - Mixing operators
result = 5 + * 3      # Syntax error

# ✓ CORRECT
result = 5 + 3 * 2

# ✗ WRONG - Not using parentheses when needed
result = 10 / 2 + 3   # 8.0 (not what you might expect)

# ✓ CORRECT - When you need priority
result = 10 / (2 + 3) # 2.0
```

---

## Key Takeaways

✓ Arithmetic operators: `+`, `-`, `*`, `/`, `//`, `%`, `**`  
✓ Comparison operators: `==`, `!=`, `>`, `<`, `>=`, `<=`  
✓ Logical operators: `and`, `or`, `not`  
✓ Assignment operators: `=`, `+=`, `-=`, `*=`, `/=`  
✓ Operator precedence matters - use parentheses when unclear  
✓ Expressions combine values and operators to produce results  

---

## Quick Reference

```python
# Arithmetic
10 + 5                  # 15
10 - 5                  # 5
10 * 5                  # 50
10 / 5                  # 2.0
10 // 3                 # 3
10 % 3                  # 1
2 ** 3                  # 8

# Comparison (returns bool)
5 == 5                  # True
5 != 5                  # False
5 > 3                   # True
5 < 3                   # False

# Logical
True and False          # False
True or False           # True
not True                # False

# Assignment
x = 5
x += 3                  # x is now 8
```

---

## Homework

1. ✓ Create a calculator that performs: addition, subtraction, multiplication, division
2. ✓ Write a program that checks if a number is even or odd
3. ✓ Create a program that calculates age based on birth year
4. ✓ Write an expression that checks if a person is eligible for a loan (age >= 21 and credit_score > 700)

Next hour: **Input/Output & Type Casting!**
