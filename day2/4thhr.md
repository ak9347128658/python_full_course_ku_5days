# Day 2 - Hour 4: Functions, Arguments, and Return Values

## Welcome to the Final Hour of Day 2!

Functions are HUGE in programming! They're the foundation of organized code. A function is a reusable block of code that does one specific job. This hour, you'll learn to write them properly!

Think of a function like a recipe: "To make coffee, you need water, filter, coffee grounds. Then you brew and pour." You can follow this recipe any time without rewriting it.

---

## What is a Function?

A **function** is a reusable block of code that performs a specific task.

**Why use functions?**
1. **Reusability** - Write once, use many times
2. **Organization** - Code is cleaner and easier to understand
3. **Maintainability** - Fix a bug once, it's fixed everywhere
4. **Simplicity** - Break complex problems into smaller parts

---

## Creating a Function

### Basic Syntax

```python
def function_name():
    # Code inside function
    print("Hello from function!")

# Call the function
function_name()
```

### Example 1: Simple Function

```python
def greet():
    print("Hello!")

greet()         # Output: Hello!
greet()         # Output: Hello!
greet()         # Output: Hello!
```

We called the function 3 times without rewriting the code!

### Example 2: Function vs Inline Code

```python
# Without function - repetitive
print("Welcome!")
print("Welcome!")
print("Welcome!")

# With function - clean
def welcome():
    print("Welcome!")

welcome()
welcome()
welcome()
```

---

## Parameters and Arguments

A **parameter** is a variable in the function definition. An **argument** is the actual value you pass when calling the function.

### Syntax

```python
def function_name(parameter1, parameter2):
    # Use parameters inside function
    print(parameter1, parameter2)

# Call with arguments
function_name(argument1, argument2)
```

### Example 1: Single Parameter

```python
def greet(name):
    print(f"Hello, {name}!")

greet("Alice")              # Output: Hello, Alice!
greet("Bob")                # Output: Hello, Bob!
greet("Charlie")            # Output: Hello, Charlie!
```

### Example 2: Multiple Parameters

```python
def add(a, b):
    result = a + b
    print(f"{a} + {b} = {result}")

add(5, 3)                   # Output: 5 + 3 = 8
add(10, 20)                 # Output: 10 + 20 = 30
```

### Example 3: Parameters with Different Types

```python
def introduce(name, age, city):
    print(f"My name is {name}")
    print(f"I am {age} years old")
    print(f"I live in {city}")

introduce("Alice", 25, "New York")
# Output:
# My name is Alice
# I am 25 years old
# I live in New York
```

---

## Return Values

A function can **return** a value that you can use in your program.

### Syntax

```python
def function_name():
    return value

result = function_name()
```

### Example 1: Simple Return

```python
def get_age():
    return 25

age = get_age()
print(age)                  # Output: 25
```

### Example 2: Calculate and Return

```python
def add(a, b):
    return a + b

result = add(5, 3)
print(result)               # Output: 8
print(add(10, 20))          # Output: 30
```

### Example 3: Multiple Use of Return Value

```python
def multiply(x, y):
    return x * y

# Use return value directly
print(multiply(4, 5))       # Output: 20

# Store and use later
area = multiply(10, 5)
print(f"Area: {area}")      # Output: Area: 50

# Use in calculations
total = multiply(3, 4) + multiply(5, 6)
print(total)                # Output: 42 (12 + 30)
```

### Example 4: Return Boolean

```python
def is_even(num):
    return num % 2 == 0

print(is_even(4))           # Output: True
print(is_even(7))           # Output: False

if is_even(10):
    print("10 is even")     # This prints
```

---

## Default Parameters

You can give parameters default values.

```python
def greet(name="Friend"):
    print(f"Hello, {name}!")

greet()                     # Uses default: Hello, Friend!
greet("Alice")              # Uses argument: Hello, Alice!
```

### More Examples

```python
def power(base, exponent=2):
    return base ** exponent

print(power(5))             # 5^2 = 25
print(power(5, 3))          # 5^3 = 125

def make_coffee(size="medium", with_sugar=True):
    print(f"Making {size} coffee", end="")
    if with_sugar:
        print(" with sugar")
    else:
        print(" without sugar")

make_coffee()               # medium coffee with sugar
make_coffee("large")        # large coffee with sugar
make_coffee("small", False) # small coffee without sugar
```

---

## Real-World Function Examples

### Example 1: Grade Calculator

```python
def calculate_grade(score):
    if score >= 90:
        return "A"
    elif score >= 80:
        return "B"
    elif score >= 70:
        return "C"
    elif score >= 60:
        return "D"
    else:
        return "F"

print(calculate_grade(85))  # Output: B
print(calculate_grade(92))  # Output: A
print(calculate_grade(55))  # Output: F
```

### Example 2: Temperature Converter

```python
def celsius_to_fahrenheit(celsius):
    fahrenheit = (celsius * 9/5) + 32
    return fahrenheit

def fahrenheit_to_celsius(fahrenheit):
    celsius = (fahrenheit - 32) * 5/9
    return celsius

print(celsius_to_fahrenheit(0))      # Output: 32.0
print(celsius_to_fahrenheit(100))    # Output: 212.0
print(fahrenheit_to_celsius(32))     # Output: 0.0
```

### Example 3: Validate Email

```python
def is_valid_email(email):
    return "@" in email and "." in email

print(is_valid_email("john@example.com"))    # Output: True
print(is_valid_email("john@example"))        # Output: False
print(is_valid_email("johnexample.com"))     # Output: False
```

### Example 4: List Operations

```python
def find_average(numbers):
    total = sum(numbers)
    count = len(numbers)
    return total / count

scores = [85, 90, 78, 92]
print(find_average(scores))         # Output: 86.25

def find_max(numbers):
    maximum = numbers[0]
    for num in numbers:
        if num > maximum:
            maximum = num
    return maximum

print(find_max(scores))             # Output: 92
```

---

## Using Loops in Functions

```python
def print_stars(count):
    for i in range(count):
        print("*", end="")
    print()

print_stars(5)              # Output: *****
print_stars(10)             # Output: **********

def calculate_factorial(n):
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result

print(calculate_factorial(5))        # Output: 120 (5! = 5*4*3*2*1)
```

---

## Function Best Practices

### 1. Use Descriptive Names

```python
# ✗ Bad
def f(x):
    return x * 2

# ✓ Good
def double(number):
    return number * 2
```

### 2. One Job Per Function

```python
# ✗ Bad - does too much
def process_user():
    name = input("Name: ")
    age = input("Age: ")
    # ... plus 50 more lines

# ✓ Good - each function does one thing
def get_user_name():
    return input("Name: ")

def get_user_age():
    return int(input("Age: "))
```

### 3. Add Comments for Complex Functions

```python
def fibonacci(n):
    """Calculate the nth Fibonacci number"""
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
```

---

## Project 1: Calculator Functions

```python
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        return "Cannot divide by zero"
    return a / b

# Use functions
print(f"10 + 5 = {add(10, 5)}")
print(f"10 - 5 = {subtract(10, 5)}")
print(f"10 * 5 = {multiply(10, 5)}")
print(f"10 / 5 = {divide(10, 5)}")
```

---

## Project 2: Password Validator

```python
def is_strong_password(password):
    """Check if password is strong (8+ chars, has letter and number)"""
    if len(password) < 8:
        return False
    
    has_letter = False
    has_number = False
    
    for char in password:
        if char.isalpha():
            has_letter = True
        if char.isdigit():
            has_number = True
    
    return has_letter and has_number

# Test
print(is_strong_password("pass"))            # False (too short)
print(is_strong_password("password"))        # False (no number)
print(is_strong_password("password123"))     # True
```

---

## Exercises

### Exercise 1: Area Calculation

Create `area.py`:

```python
def circle_area(radius):
    return 3.14159 * radius ** 2

def rectangle_area(length, width):
    return length * width

print(f"Circle area: {circle_area(5):.2f}")
print(f"Rectangle area: {rectangle_area(10, 5)}")
```

### Exercise 2: String Functions

Create `strings.py`:

```python
def reverse_string(text):
    return text[::-1]

def count_vowels(text):
    vowels = "aeiouAEIOU"
    count = 0
    for char in text:
        if char in vowels:
            count += 1
    return count

print(reverse_string("Python"))
print(count_vowels("Hello World"))
```

### Exercise 3: Number Functions

Create `numbers.py`:

```python
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, n):
        if n % i == 0:
            return False
    return True

def is_perfect_square(n):
    root = int(n ** 0.5)
    return root * root == n

print(is_prime(17))
print(is_perfect_square(25))
```

### Exercise 4: Conversion Functions

Create `conversion.py`:

```python
def miles_to_km(miles):
    return miles * 1.60934

def kg_to_lbs(kg):
    return kg * 2.20462

print(f"10 miles = {miles_to_km(10):.2f} km")
print(f"75 kg = {kg_to_lbs(75):.2f} lbs")
```

---

## Common Mistakes

```python
# ✗ WRONG - Missing colon
def add(a, b)
    return a + b

# ✓ CORRECT
def add(a, b):
    return a + b

# ✗ WRONG - Forgot to call function
def greet():
    print("Hello")

greet  # Nothing happens - forgot ()

# ✓ CORRECT
greet()  # Output: Hello

# ✗ WRONG - Using return value without storing
def add(a, b):
    return a + b

add(5, 3)  # Return value is ignored

# ✓ CORRECT
result = add(5, 3)
print(result)
```

---

## Key Takeaways

✓ Functions are reusable blocks of code  
✓ Define with `def function_name():` and call with `function_name()`  
✓ Parameters are variables; arguments are values you pass  
✓ Use `return` to send a value back  
✓ Default parameters provide fallback values  
✓ Functions make code cleaner and more maintainable  
✓ One function = one job  

---

## Quick Reference

```python
# Define function
def greet():
    print("Hello")

# Call function
greet()

# Function with parameter
def add(a, b):
    return a + b

result = add(5, 3)

# Function with default parameter
def power(base, exp=2):
    return base ** exp

print(power(5))          # Uses default exp=2
print(power(5, 3))       # Uses exp=3
```

---

## Congratulations! 🎉

You've completed **Day 2 - Core Programming**! You now know:
- ✓ Conditional statements (if/elif/else)
- ✓ Loops (for and while)
- ✓ Loop control (break, continue)
- ✓ Functions with parameters and returns

**Tomorrow: Data Structures (Lists, Tuples, Sets, Dictionaries)!**
