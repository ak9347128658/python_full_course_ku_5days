# Day 1 - Hour 4: Input/Output & Type Casting

## Welcome to the Final Hour of Day 1!

You're crushing it! In this final hour, we're learning how to:
1. Take **input** from users
2. Display **formatted output**
3. Convert between **datatypes**

These skills make programs **interactive** - the real magic of programming!

---

## Input - Getting User Data

So far, we've only used values we hardcode. Real programs get input from users. Let's learn how!

### The `input()` Function

The `input()` function displays a prompt and waits for the user to type something.

```python
name = input("What is your name? ")
print(name)
```

**Run this and type "Alice":**
```
What is your name? Alice
Alice
```

The user types at the `?` prompt, presses Enter, and their input is stored in `name`.

### Important: Input is Always a String

**This is crucial:** `input()` ALWAYS returns a **string**, even if the user types a number!

```python
age = input("How old are you? ")
print(age)                      # The value is stored as text
print(type(age))                # <class 'str'> - It's a string!

# Even though user typed 25, Python treats it as "25"
```

---

## Type Casting - Converting Types

Since `input()` always returns strings, we need to convert them to numbers if we want to do math.

### Converting to Integer: `int()`

```python
age_string = "25"
age_int = int(age_string)
print(age_int)                  # 25
print(type(age_int))            # <class 'int'>

# Now we can do math
age_int += 1
print(age_int)                  # 26
```

### Real Example: User Input for Math

```python
# Get age from user
age_input = input("Enter your age: ")
age = int(age_input)            # Convert to integer

# Calculate years until 100
years_until_100 = 100 - age
print(f"You will be 100 in {years_until_100} years")
```

**Run it:**
```
Enter your age: 25
You will be 100 in 75 years
```

### Converting to Float: `float()`

```python
price_string = "19.99"
price_float = float(price_string)
print(price_float)              # 19.99
print(type(price_float))        # <class 'float'>

# Do math
total = price_float * 5
print(total)                    # 99.95
```

### Converting to String: `str()`

```python
age = 25
age_string = str(age)
print(age_string)               # "25"
print(type(age_string))         # <class 'str'>

# Useful for concatenation
message = "I am " + str(age) + " years old"
print(message)                  # I am 25 years old
```

### Converting to Boolean: `bool()`

```python
print(bool(1))                  # True
print(bool(0))                  # False
print(bool("text"))             # True
print(bool(""))                 # False (empty string)
print(bool(None))               # False
```

---

## Working with Input and Type Casting

### Example 1: Calculate Area

```python
print("=== Rectangle Area Calculator ===")

length_input = input("Enter length: ")
width_input = input("Enter width: ")

# Convert to float for decimal numbers
length = float(length_input)
width = float(width_input)

# Calculate area
area = length * width

print(f"Area: {area}")
```

**Run it:**
```
=== Rectangle Area Calculator ===
Enter length: 5.5
Enter width: 3.2
Area: 17.6
```

### Example 2: Simple Calculator

```python
print("=== Simple Calculator ===")

num1 = float(input("Enter first number: "))
num2 = float(input("Enter second number: "))

addition = num1 + num2
subtraction = num1 - num2
multiplication = num1 * num2
division = num1 / num2

print(f"Addition: {addition}")
print(f"Subtraction: {subtraction}")
print(f"Multiplication: {multiplication}")
print(f"Division: {division}")
```

**Run it:**
```
=== Simple Calculator ===
Enter first number: 10
Enter second number: 3
Addition: 13.0
Subtraction: 7.0
Multiplication: 30.0
Division: 3.3333333333333335
```

### Example 3: Temperature Converter

```python
print("=== Fahrenheit to Celsius ===")

fahrenheit_input = input("Enter temperature in F: ")
fahrenheit = float(fahrenheit_input)

# Convert to Celsius
celsius = (fahrenheit - 32) * 5/9

print(f"{fahrenheit}°F = {celsius:.2f}°C")
```

**Run it:**
```
=== Fahrenheit to Celsius ===
Enter temperature in F: 98.6
98.6°F = 37.0°C
```

---

## Output - Displaying Information

You already know `print()`, but let's master it!

### Simple Print

```python
print("Hello, World!")
```

### Print Multiple Values

```python
name = "Alice"
age = 25
print(name, age)                # Alice 25
print(name, age, sep="-")       # Alice-25
print(name, age, sep=" | ")     # Alice | 25
```

### String Concatenation

```python
name = "Alice"
age = 25

# Using + (need to convert to string)
print("Name: " + name + ", Age: " + str(age))

# Better way: String Formatting (next section!)
```

---

## String Formatting - The Modern Way!

### F-strings (Recommended - Python 3.6+)

F-strings are the most modern and readable way to format strings.

```python
name = "Bob"
age = 30
gpa = 3.85

print(f"Name: {name}")          # Name: Bob
print(f"Age: {age}")            # Age: 30
print(f"GPA: {gpa}")            # GPA: 3.85

# Multi-variable
print(f"{name} is {age} years old with a {gpa} GPA")
# Bob is 30 years old with a 3.85 GPA
```

### Formatting Numbers

```python
pi = 3.14159265

print(f"{pi}")                  # 3.14159265
print(f"{pi:.2f}")              # 3.14 (2 decimal places)
print(f"{pi:.4f}")              # 3.1416 (4 decimal places)

price = 19.5
print(f"Price: ${price:.2f}")   # Price: $19.50
```

### Formatting with Width

```python
name = "Alice"
print(f"Name: {name:>10}")      # Name:      Alice (right-aligned)
print(f"Name: {name:<10}")      # Name: Alice       (left-aligned)
print(f"Name: {name:^10}")      # Name:    Alice    (centered)
```

### Practical Formatting Example

```python
print("=== STUDENT REPORT ===")

student_name = "John Doe"
student_id = 12345
math_score = 87.5
english_score = 92.3
average = (math_score + english_score) / 2

print(f"Name:      {student_name:20}")
print(f"ID:        {student_id}")
print(f"Math:      {math_score:.2f}")
print(f"English:   {english_score:.2f}")
print(f"Average:   {average:.2f}")
```

Output:
```
=== STUDENT REPORT ===
Name:      John Doe
ID:        12345
Math:      87.50
English:   92.30
Average:   89.90
```

### The `format()` Method (Alternative)

```python
name = "Alice"
age = 25

print("Name: {}, Age: {}".format(name, age))
# Name: Alice, Age: 25

print("Name: {0}, Age: {1}".format(name, age))
# Name: Alice, Age: 25

print("{name} is {age} years old".format(name="Alice", age=25))
# Alice is 25 years old
```

---

## Complete Project: Personal Information System

Let's build a program that takes user input and displays formatted output!

```python
print("=" * 40)
print("    PERSONAL INFORMATION SYSTEM")
print("=" * 40)

# Get user input
name = input("\nEnter your name: ")
age_input = input("Enter your age: ")
height_input = input("Enter your height in cm: ")
city = input("Enter your city: ")

# Convert types
age = int(age_input)
height = float(height_input)

# Calculate some info
birth_year = 2024 - age

# Display formatted output
print("\n" + "=" * 40)
print("    YOUR INFORMATION")
print("=" * 40)
print(f"Name:          {name:20}")
print(f"Age:           {age}")
print(f"Birth Year:    {birth_year}")
print(f"Height:        {height:.2f} cm")
print(f"City:          {city:20}")
print("=" * 40)

# Simple calculation
print(f"\nIn 10 years, you'll be {age + 10} years old!")
```

**Run it and interact:**
```
========================================
    PERSONAL INFORMATION SYSTEM
========================================

Enter your name: Alice Johnson
Enter your age: 25
Enter your height in cm: 167.5
Enter your city: New York

========================================
    YOUR INFORMATION
========================================
Name:          Alice Johnson
Age:           25
Birth Year:    1999
Height:        167.50 cm
City:          New York
========================================

In 10 years, you'll be 35 years old!
```

---

## Exercises

### Exercise 1: Simple Greeter

Create `greeter.py`:

```python
# Get user's name
name = input("What's your name? ")

# Get user's favorite color
color = input("What's your favorite color? ")

# Display greeting
print(f"Hello {name}! I love {color} too!")
```

### Exercise 2: Store Calculator

Create `store_calculator.py`:

```python
# Get product details
product = input("What are you buying? ")
price_input = input("Price per item: $")
quantity_input = input("How many? ")

# Convert to numbers
price = float(price_input)
quantity = int(quantity_input)

# Calculate
total = price * quantity
tax = total * 0.08
final_total = total + tax

# Display formatted output
print("\n" + "-" * 30)
print(f"Item:          {product}")
print(f"Unit Price:    ${price:.2f}")
print(f"Quantity:      {quantity}")
print(f"Subtotal:      ${total:.2f}")
print(f"Tax (8%):      ${tax:.2f}")
print(f"Total:         ${final_total:.2f}")
print("-" * 30)
```

### Exercise 3: Time Conversion

Create `time_converter.py`:

```python
# Get hours from user
hours_input = input("Enter hours: ")
minutes_input = input("Enter minutes: ")

# Convert to integers
hours = int(hours_input)
minutes = int(minutes_input)

# Convert to total seconds
total_seconds = (hours * 3600) + (minutes * 60)

# Convert to total minutes
total_minutes = hours * 60 + minutes

print(f"\n{hours} hours and {minutes} minutes is:")
print(f"  {total_minutes} total minutes")
print(f"  {total_seconds} total seconds")
```

### Exercise 4: Advanced - BMI Calculator

Create `bmi_calculator.py`:

```python
print("=== BMI Calculator ===\n")

# Get weight and height
weight_input = input("Enter your weight (kg): ")
height_input = input("Enter your height (m): ")

# Convert to float
weight = float(weight_input)
height = float(height_input)

# Calculate BMI
bmi = weight / (height ** 2)

# Display result
print(f"\nYour BMI: {bmi:.2f}")

# Interpret BMI
if bmi < 18.5:
    status = "Underweight"
elif bmi < 25:
    status = "Normal weight"
elif bmi < 30:
    status = "Overweight"
else:
    status = "Obese"

print(f"Status: {status}")
```

---

## Debugging Input Issues

### Problem 1: User Enters Non-Number

```python
# This crashes if user doesn't enter a number
age = int(input("Enter age: "))    # If user types "abc", ERROR!
```

Solution (we'll learn proper error handling tomorrow!):
```python
# For now, always tell users what to enter
age = int(input("Enter your age (number): "))
```

### Problem 2: Extra Spaces

```python
name = input("Name: ")             # If user types " Alice " (with spaces)
print(name)                        # Displays " Alice " with spaces

# Better:
name = input("Name: ").strip()     # Remove leading/trailing spaces
print(name)                        # Displays "Alice" cleanly
```

---

## Key Takeaways

✓ `input()` function gets user input (always as string)  
✓ Use `int()`, `float()`, `str()` to convert between types  
✓ F-strings are the modern way to format output  
✓ Use `.2f` for 2 decimal places  
✓ Always convert input when doing math  
✓ Format output for clean, professional displays  

---

## Quick Reference

```python
# Input
name = input("Enter name: ")

# Type Conversion
age_int = int("25")
height_float = float("5.7")
text = str(123)

# Print with formatting
print(f"Age: {age_int}")
print(f"Height: {height_float:.2f}")
print(f"Name: {name:20}")

# String concatenation (old way, not recommended)
message = "Hello " + name

# F-string concatenation (modern way, recommended)
message = f"Hello {name}"
```

---

## Homework for Tomorrow

Before Day 2, complete these:

1. ✓ Create a program that takes name, age, and city as input, then displays formatted output
2. ✓ Create a simple calculator that takes two numbers and displays addition, subtraction, multiplication, division
3. ✓ Create a program that converts inches to centimeters
4. ✓ Create a program that calculates the cost of items with tax

---

## Congratulations! 🎉

You've completed **Day 1 - Python Basics**! You now know:
- ✓ Python basics and setup
- ✓ Variables and datatypes
- ✓ Operators and expressions
- ✓ Input/output and type casting

**Tomorrow: Conditional Statements & Loops!**

The programs you're about to build will have logic, decisions, and repetition - things will get really interesting!
