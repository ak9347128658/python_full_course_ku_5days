# Day 4 - Hour 2: Modules & Packages

## Welcome to Hour 2!

Python's real power comes from **modules** and **packages** - reusable code written by others. Instead of writing everything from scratch, you import existing code and use it!

Think of modules like tools in a toolbox - you don't build your own hammer, you just use the one that's already there!

---

## What is a Module?

A **module** is a file containing Python code (functions, classes, variables) that you can import and use.

```python
# my_math.py - This is a module
def add(a, b):
    return a + b

def multiply(a, b):
    return a * b

PI = 3.14159
```

```python
# main.py - Using the module
import my_math

result = my_math.add(5, 3)
print(result)                   # 8
```

---

## Built-in Modules

Python comes with many built-in modules. No installation needed!

### `math` Module

```python
import math

print(math.pi)                  # 3.141592653589793
print(math.sqrt(16))            # 4.0
print(math.floor(3.7))          # 3
print(math.ceil(3.2))           # 4
print(math.pow(2, 3))           # 8.0 (2^3)
```

### `random` Module

```python
import random

# Random integer
num = random.randint(1, 10)
print(num)                      # Random 1-10

# Random float
decimal = random.random()       # 0.0 to 1.0
print(decimal)

# Random from list
fruits = ["apple", "banana", "orange"]
choice = random.choice(fruits)
print(choice)

# Shuffle list
numbers = [1, 2, 3, 4, 5]
random.shuffle(numbers)
print(numbers)
```

### `datetime` Module

```python
import datetime

# Current date and time
now = datetime.datetime.now()
print(now)                      # 2024-01-15 14:30:45.123456

# Create specific date
date = datetime.datetime(2024, 12, 25)
print(date)

# Get components
print(now.year)                 # 2024
print(now.month)                # 1
print(now.day)                  # 15
print(now.hour)                 # 14
```

### `time` Module

```python
import time

# Current time (seconds since 1970)
current = time.time()
print(current)

# Pause execution
print("Starting...")
time.sleep(2)                   # Wait 2 seconds
print("Done!")
```

### `os` Module

```python
import os

# Current directory
print(os.getcwd())

# List files
files = os.listdir(".")
print(files)

# Check if path exists
print(os.path.exists("file.txt"))

# Create directory
os.mkdir("new_folder")

# Change directory
os.chdir("new_folder")
```

---

## Importing Modules

### Import Entire Module

```python
import math

print(math.pi)
print(math.sqrt(4))
```

### Import Specific Function

```python
from math import sqrt, pi

print(pi)                       # Direct access
print(sqrt(4))                  # Direct access
```

### Import with Alias

```python
import math as m

print(m.pi)
print(m.sqrt(4))

# Or for specific functions
from math import sqrt as square_root
print(square_root(9))
```

### Import All (Not Recommended)

```python
from math import *

print(pi)                       # Works but not clear where it comes from
```

---

## Creating Your Own Module

### Create a Module File

Create `calculator.py`:

```python
"""
Simple calculator module
"""

def add(a, b):
    """Add two numbers"""
    return a + b

def subtract(a, b):
    """Subtract two numbers"""
    return a - b

def multiply(a, b):
    """Multiply two numbers"""
    return a * b

def divide(a, b):
    """Divide two numbers"""
    if b == 0:
        return "Cannot divide by zero"
    return a / b

# Module variable
VERSION = "1.0"
```

### Use Your Module

Create `use_calculator.py`:

```python
import calculator

result = calculator.add(10, 5)
print(f"10 + 5 = {result}")

result = calculator.multiply(4, 3)
print(f"4 * 3 = {result}")

print(f"Calculator v{calculator.VERSION}")
```

---

## What is a Package?

A **package** is a directory containing modules and a special `__init__.py` file.

```
my_package/
    __init__.py
    math_module.py
    string_module.py
```

### Create a Package

Create folder structure:
```
my_app/
    __init__.py (empty file)
    utils/
        __init__.py
        strings.py
        numbers.py
```

In `my_app/utils/strings.py`:

```python
def reverse(text):
    return text[::-1]

def uppercase(text):
    return text.upper()
```

In `my_app/utils/numbers.py`:

```python
def square(n):
    return n ** 2

def cube(n):
    return n ** 3
```

### Use the Package

```python
from my_app.utils.strings import reverse, uppercase
from my_app.utils.numbers import square

print(reverse("Hello"))         # olleH
print(uppercase("Hello"))       # HELLO
print(square(5))                # 25
```

---

## Popular External Packages

Install packages with `pip`:

```bash
pip install package_name
```

### `requests` - HTTP Requests

```python
import requests

# Fetch data from URL
response = requests.get("https://api.example.com/data")
data = response.json()
```

### `numpy` - Numerical Computing

```python
import numpy as np

# Create array
arr = np.array([1, 2, 3, 4, 5])
print(np.mean(arr))             # Average
print(np.sum(arr))              # Sum
```

### `pandas` - Data Analysis

```python
import pandas as pd

# Create DataFrame
df = pd.read_csv("data.csv")
print(df.head())
```

---

## Real-World Examples

### Example 1: Random Quiz Game

```python
import random

questions = {
    "What is 2 + 2?": "4",
    "What is the capital of France?": "Paris",
    "What is 10 / 2?": "5"
}

score = 0
for question, answer in questions.items():
    user_answer = input(question + " ")
    if user_answer == answer:
        score += 1
        print("Correct!")
    else:
        print(f"Wrong! Answer: {answer}")

print(f"\nFinal score: {score}/{len(questions)}")
```

### Example 2: Current Time Display

```python
import datetime

now = datetime.datetime.now()

print(f"Current date: {now.strftime('%Y-%m-%d')}")
print(f"Current time: {now.strftime('%H:%M:%S')}")
print(f"Day of week: {now.strftime('%A')}")
```

### Example 3: File System Operations

```python
import os

# Create backup
source = "important.txt"
backup = f"{source}.backup"

if os.path.exists(source):
    with open(source, "r") as src:
        content = src.read()
    
    with open(backup, "w") as bak:
        bak.write(content)
    
    print(f"Backup created: {backup}")
```

---

## Project 1: Random Password Generator

```python
import random
import string

def generate_password(length=12):
    """Generate random password"""
    characters = string.ascii_letters + string.digits + string.punctuation
    password = ''.join(random.choice(characters) for _ in range(length))
    return password

# Main program
length = int(input("Password length: "))
password = generate_password(length)
print(f"Generated password: {password}")
```

---

## Project 2: File Manager with datetime

```python
import os
import datetime

def list_files():
    """List files with modification time"""
    files = os.listdir(".")
    for file in files:
        mtime = os.path.getmtime(file)
        mod_time = datetime.datetime.fromtimestamp(mtime)
        print(f"{file} - Modified: {mod_time}")

# Run
list_files()
```

---

## Exercises

### Exercise 1: Math Module

Create `math_ops.py`:

```python
import math

# Calculate area of circle
radius = 5
area = math.pi * math.pow(radius, 2)
print(f"Area: {area:.2f}")

# Calculate hypotenuse
a = 3
b = 4
c = math.sqrt(a**2 + b**2)
print(f"Hypotenuse: {c}")
```

### Exercise 2: Random Module

Create `randomizer.py`:

```python
import random

# Roll dice
die1 = random.randint(1, 6)
die2 = random.randint(1, 6)
print(f"Dice: {die1}, {die2}")

# Lucky number
lucky = random.randint(1, 100)
print(f"Lucky number: {lucky}")
```

### Exercise 3: Current Date/Time

Create `time_display.py`:

```python
import datetime

now = datetime.datetime.now()
print(f"Date: {now.date()}")
print(f"Time: {now.time()}")
print(f"Timestamp: {now.timestamp()}")
```

### Exercise 4: Custom Module

Create `greetings.py` (module):

```python
def hello(name):
    return f"Hello, {name}!"

def goodbye(name):
    return f"Goodbye, {name}!"
```

Create `use_greetings.py`:

```python
import greetings

print(greetings.hello("Alice"))
print(greetings.goodbye("Bob"))
```

---

## Common Mistakes

```python
# ✗ WRONG - Using function name as variable
import random
random = 5              # Overwrites module!
random.randint(1, 10)   # Error!

# ✓ CORRECT
import random as rnd
rnd.randint(1, 10)

# ✗ WRONG - Forgetting to import
print(sqrt(4))          # NameError

# ✓ CORRECT
from math import sqrt
print(sqrt(4))

# ✗ WRONG - Wrong import path
from module.function import foo  # Should be from module import function

# ✓ CORRECT
from module import function
```

---

## Key Takeaways

✓ Modules contain reusable code  
✓ Use `import` to load modules  
✓ Built-in modules: math, random, datetime, os  
✓ `from module import function` for specific functions  
✓ Create your own modules as .py files  
✓ Packages are directories of modules  
✓ External packages installed with pip  

---

## Quick Reference

```python
# Import module
import math
print(math.pi)

# Import specific item
from math import sqrt
print(sqrt(4))

# Import with alias
import datetime as dt
print(dt.datetime.now())

# Built-in modules
import math              # Math functions
import random            # Random numbers
import datetime          # Date/time
import os                # Operating system
import time              # Time operations
```

---

## Homework

1. ✓ Use math module to calculate circle area
2. ✓ Use random module to create a number guessing game
3. ✓ Use datetime to display current date/time
4. ✓ Create your own module with 3 functions

Next hour: **Error Handling!**
