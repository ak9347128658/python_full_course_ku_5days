# Day 1 - Hour 2: Variables & Datatypes

## Welcome Back!

Great job completing Hour 1! You've got Python running and you've written your first program. Now we're going to talk about **variables** and **datatypes** - the fundamental building blocks of any program.

Think of a variable like a labeled box. You store information inside it, give it a name, and can retrieve it whenever you need it.

---

## What is a Variable?

A variable is a **named container that stores a value** in your program's memory.

### Creating Variables

In Python, creating a variable is simple:

```python
name = "Alice"
age = 25
height = 5.7
is_student = True
```

That's it! You use the `=` operator to **assign** a value to a variable.

### Variable Naming Rules

Python isn't too strict, but follow these conventions:

```python
# ✓ GOOD
first_name = "Bob"
student_age = 20
score_2024 = 95
_private_var = 100

# ✗ WRONG
2nd_name = "Charlie"        # Can't start with a number
first-name = "David"        # Can't use hyphens
first name = "Eve"          # Can't have spaces
class = "Python"            # Can't use reserved keywords
```

**Key Rules:**
1. Start with a letter or underscore `_`
2. Use only letters, numbers, and underscores
3. Case sensitive (`Name` ≠ `name`)
4. Don't use Python's reserved keywords (if, else, for, while, etc.)

### Variable Naming Conventions

```python
# Snake_case (RECOMMENDED in Python)
user_name = "Alice"
total_score = 100
is_active = True

# camelCase (Avoid in Python - used in Java/JS)
userName = "Bob"
totalScore = 100

# UPPERCASE (Used for constants - values that never change)
MAX_ATTEMPTS = 5
PI_VALUE = 3.14159
GRAVITY = 9.8
```

---

## Python Datatypes

Every value in Python has a **type**. Python automatically figures out which type based on what you assign. Let me show you the main ones:

### 1. **String (str)** - Text

A string is any text wrapped in quotes (single `'` or double `"`).

```python
name = "Alice"              # Double quotes
city = 'New York'           # Single quotes
message = """
This is a
multi-line string
Very cool!
"""

# Empty string
empty = ""

print(name)                 # Output: Alice
print(type(name))           # Output: <class 'str'>
```

**Fun fact**: In Python, `"text"` and `'text'` are identical. Pick one and stick with it!

### 2. **Integer (int)** - Whole Numbers

```python
age = 25
score = 100
temperature = -10
zero = 0

print(age)                  # Output: 25
print(type(age))            # Output: <class 'int'>
print(age + 5)              # Output: 30
```

### 3. **Float (float)** - Decimal Numbers

```python
height = 5.7
price = 19.99
pi = 3.14159
negative_decimal = -2.5

print(height)               # Output: 5.7
print(type(height))         # Output: <class 'float'>
print(height + 0.3)         # Output: 6.0
```

**Important**: Even if you write `5.0`, Python treats it as a float, not an integer.

```python
x = 5
y = 5.0

print(type(x))              # <class 'int'>
print(type(y))              # <class 'float'>
```

### 4. **Boolean (bool)** - True or False

Used for conditions and logical operations.

```python
is_student = True
is_raining = False
game_over = True

print(is_student)           # Output: True
print(type(is_student))     # Output: <class 'bool'>
```

**IMPORTANT**: In Python, `True` and `False` are capitalized!

### 5. **NoneType (None)** - Empty/No Value

`None` represents the absence of a value.

```python
result = None
print(result)               # Output: None
print(type(result))         # Output: <class 'NoneType'>
```

---

## Checking Datatypes

Use the `type()` function to check what type a value is:

```python
print(type("Hello"))        # <class 'str'>
print(type(42))             # <class 'int'>
print(type(3.14))           # <class 'float'>
print(type(True))           # <class 'bool'>
print(type(None))           # <class 'NoneType'>
```

---

## Working with Variables

### Assignment (Storing Values)

```python
# Single assignment
x = 10

# Multiple assignments
a = b = c = 5              # All three get value 5

# Unpacking (assigning multiple values at once)
x, y, z = 1, 2, 3
print(x)                    # 1
print(y)                    # 2
print(z)                    # 3
```

### Variable Reassignment

Variables can change their values (and even their types!):

```python
x = 5
print(x)                    # 5

x = 10                      # Reassign to new value
print(x)                    # 10

x = "Now I'm a string!"     # Reassign to different type
print(x)                    # Now I'm a string!
print(type(x))              # <class 'str'>
```

### Getting the Value

Simply use the variable name:

```python
name = "Alice"
age = 25

print(name)                 # Alice
print(age)                  # 25
print(name + " is " + str(age) + " years old")  # Alice is 25 years old
```

---

## Real-World Example

Let's create a program that stores student information:

```python
# Student Information Program
student_name = "Bob Johnson"
student_age = 20
gpa = 3.85
is_scholarship_recipient = True
graduation_year = None

print("Student Profile:")
print("Name:", student_name)
print("Age:", student_age)
print("GPA:", gpa)
print("Scholarship:", is_scholarship_recipient)
print("Graduation Year:", graduation_year)
```

Output:
```
Student Profile:
Name: Bob Johnson
Age: 20
GPA: 3.85
Scholarship: True
Graduation Year: None
```

---

## Exercise Time!

### Exercise 1: Basic Variables

Create a file called `variables.py`:

```python
# TODO: Create variables for:
# - Your name (string)
# - Your age (integer)
# - Your height in meters (float)
# - Whether you like programming (boolean)

# Print each variable on a new line
```

**Solution:**
```python
my_name = "Your Name"
my_age = 25
my_height = 1.75
like_programming = True

print(my_name)
print(my_age)
print(my_height)
print(like_programming)
```

### Exercise 2: Variable Types

```python
# Create the following and print their types:
name = "Alice"
year = 2024
temperature = 98.6
is_raining = False

print(type(name))
print(type(year))
print(type(temperature))
print(type(is_raining))
```

### Exercise 3: Real Application

Create a `book_info.py` file:

```python
# Store book information
book_title = "Python for Beginners"
author = "John Smith"
pages = 350
price = 29.99
is_bestseller = True

print("Book: " + book_title)
print("Author: " + author)
print("Pages: " + str(pages))
print("Price: $" + str(price))
print("Bestseller: " + str(is_bestseller))
```

---

## Common Mistakes to Avoid

```python
# ✗ WRONG - Forgetting quotes for strings
name = Alice          # Error: name 'Alice' is not defined

# ✓ CORRECT
name = "Alice"

# ✗ WRONG - Mixing quotes incorrectly
message = "Hello'      # Error: invalid syntax

# ✓ CORRECT
message = "Hello"

# ✗ WRONG - Using reserved keywords
class = "Python"      # Error: 'class' is a reserved word

# ✓ CORRECT
my_class = "Python"
```

---

## Key Takeaways

✓ Variables store values with descriptive names  
✓ Follow naming conventions: use `snake_case`  
✓ Python has 5 main datatypes: str, int, float, bool, None  
✓ Use `type()` to check a variable's datatype  
✓ Variables can be reassigned and change types  
✓ Strings need quotes; numbers don't  

---

## Quick Reference

```python
# Creating variables
name = "Alice"
age = 25
height = 5.7
is_active = True
nothing = None

# Checking types
type(name)              # <class 'str'>
type(age)               # <class 'int'>

# Multiple assignment
a, b, c = 1, 2, 3

# Reassignment
x = 5
x = 10                  # New value
x = "text"              # New type!
```

---

## Homework

1. ✓ Create 5 variables of different types
2. ✓ Print each variable and its type
3. ✓ Create a program storing information about your favorite movie (title, year, rating, is_watched)
4. ✓ Reassign one variable multiple times and print it each time

Next hour: **Operators & Expressions!**
