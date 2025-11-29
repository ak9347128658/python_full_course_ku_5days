# Day 4 - Hour 3: Error Handling

## Welcome to Hour 3!

Real programs break! Users enter wrong data, files disappear, networks fail. **Error handling** lets your program survive these problems gracefully instead of crashing.

Without error handling: crash!
With error handling: "Sorry, that didn't work. Try again."

---

## What is an Error?

An **error** occurs when something goes wrong during execution.

```python
# ✗ Different types of errors:

print(x)                        # NameError: x not defined
int("hello")                    # ValueError: invalid literal
numbers[10]                     # IndexError: list index out of range
file = open("missing.txt")      # FileNotFoundError
5 / 0                           # ZeroDivisionError: division by zero
```

Your program crashes and stops. Not good!

---

## The `try-except` Block

Wrap potentially problematic code in `try-except`:

### Syntax

```python
try:
    # Code that might cause an error
    risky_code()
except ErrorType:
    # Code to run if error occurs
    print("An error happened!")
```

### Example 1: Division by Zero

```python
# Without error handling - crashes
result = 10 / 0             # ZeroDivisionError!

# With error handling - survives
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
    result = 0

print(f"Result: {result}")   # Result: 0
```

### Example 2: Invalid Input

```python
try:
    age = int(input("Age: "))
    print(f"You are {age} years old")
except ValueError:
    print("Please enter a number!")
```

### Example 3: File Not Found

```python
try:
    with open("missing.txt", "r") as file:
        content = file.read()
except FileNotFoundError:
    print("File not found!")
```

---

## Multiple Exception Types

Handle different errors differently:

```python
try:
    # User enters age
    age = int(input("Age: "))
    
    # Calculate birth year
    birth_year = 2024 - age
    print(f"Birth year: {birth_year}")

except ValueError:
    # User didn't enter a number
    print("Age must be a number!")

except IndexError:
    # (This won't happen in this code, but show pattern)
    print("Index out of range!")

except Exception as e:
    # Catch any other error
    print(f"Unexpected error: {e}")
```

---

## `else` Block

Code in `else` runs if NO error occurred:

```python
try:
    age = int(input("Age: "))
except ValueError:
    print("Invalid age!")
else:
    print(f"You entered: {age}")
    print("Age validation passed!")
```

---

## `finally` Block

Code in `finally` ALWAYS runs (whether error or not):

```python
try:
    file = open("data.txt", "r")
    content = file.read()
except FileNotFoundError:
    print("File not found!")
finally:
    print("Closing file...")
    # This prints whether error happened or not
```

**Real use:** Clean up resources (close files, close connections)

```python
try:
    file = open("data.txt", "r")
    content = file.read()
    print(content)
except FileNotFoundError:
    print("File not found!")
finally:
    file.close()            # Always close, even if error
```

---

## Common Exception Types

```python
ValueError              # Wrong type of value
TypeError               # Wrong type of object
IndexError              # Index out of range
KeyError                # Dictionary key not found
FileNotFoundError       # File doesn't exist
ZeroDivisionError       # Division by zero
NameError               # Variable not defined
AttributeError          # Object has no attribute
IOError                 # Input/output error
Exception               # Base class (catches all)
```

---

## Real-World Examples

### Example 1: Safe User Input

```python
def get_positive_number():
    """Get a positive number from user, retry if invalid"""
    while True:
        try:
            num = float(input("Enter positive number: "))
            if num < 0:
                print("Number must be positive!")
                continue
            return num
        except ValueError:
            print("Please enter a valid number!")

number = get_positive_number()
print(f"Got: {number}")
```

### Example 2: Dictionary Access

```python
def get_student_grade(students, name):
    """Safely get student grade"""
    try:
        grade = students[name]
        return grade
    except KeyError:
        print(f"Student '{name}' not found")
        return None

students = {"Alice": "A", "Bob": "B"}

print(get_student_grade(students, "Alice"))    # A
print(get_student_grade(students, "Charlie"))  # Student 'Charlie' not found
```

### Example 3: File Operations

```python
def safe_read_file(filename):
    """Safely read file"""
    try:
        with open(filename, "r") as file:
            return file.read()
    except FileNotFoundError:
        print(f"File '{filename}' not found")
        return None
    except IOError:
        print(f"Error reading '{filename}'")
        return None

content = safe_read_file("my_file.txt")
if content:
    print(content)
```

### Example 4: List Operations

```python
def safe_get_item(my_list, index):
    """Safely get list item"""
    try:
        return my_list[index]
    except IndexError:
        print(f"Index {index} out of range")
        return None

numbers = [1, 2, 3]
print(safe_get_item(numbers, 1))    # 2
print(safe_get_item(numbers, 10))   # Index 10 out of range
```

---

## Project 1: Calculator with Error Handling

```python
def safe_calculator():
    """Calculator with error handling"""
    try:
        num1 = float(input("First number: "))
        operation = input("Operation (+, -, *, /): ")
        num2 = float(input("Second number: "))
        
        if operation == "+":
            result = num1 + num2
        elif operation == "-":
            result = num1 - num2
        elif operation == "*":
            result = num1 * num2
        elif operation == "/":
            if num2 == 0:
                print("Cannot divide by zero!")
                return
            result = num1 / num2
        else:
            print("Invalid operation!")
            return
        
        print(f"Result: {result}")
    
    except ValueError:
        print("Please enter valid numbers!")
    except Exception as e:
        print(f"Error: {e}")

safe_calculator()
```

---

## Project 2: Data Processor

```python
def process_data():
    """Process data from file"""
    try:
        # Open file
        filename = input("Filename: ")
        with open(filename, "r") as file:
            lines = file.readlines()
        
        # Process data
        total = 0
        for line in lines:
            try:
                num = int(line.strip())
                total += num
            except ValueError:
                print(f"Skipped invalid line: {line.strip()}")
        
        print(f"Total: {total}")
    
    except FileNotFoundError:
        print("File not found!")
    except Exception as e:
        print(f"Error: {e}")

process_data()
```

---

## Raising Exceptions

You can raise your own exceptions!

```python
def set_age(age):
    """Set age with validation"""
    if age < 0:
        raise ValueError("Age cannot be negative")
    if age > 150:
        raise ValueError("Age too high")
    return age

try:
    age = set_age(200)
except ValueError as e:
    print(f"Invalid age: {e}")
```

---

## Exercises

### Exercise 1: Safe Division

Create `safe_division.py`:

```python
try:
    num1 = int(input("Numerator: "))
    num2 = int(input("Denominator: "))
    result = num1 / num2
    print(f"Result: {result}")
except ZeroDivisionError:
    print("Cannot divide by zero!")
except ValueError:
    print("Please enter numbers!")
```

### Exercise 2: Safe File Reading

Create `safe_read.py`:

```python
try:
    filename = input("Filename: ")
    with open(filename, "r") as file:
        content = file.read()
    print(content)
except FileNotFoundError:
    print("File not found!")
```

### Exercise 3: Safe List Access

Create `safe_list.py`:

```python
items = ["apple", "banana", "orange"]

try:
    index = int(input("Index: "))
    print(f"Item: {items[index]}")
except ValueError:
    print("Please enter a number!")
except IndexError:
    print("Index out of range!")
```

### Exercise 4: User Input Validation

Create `validate_input.py`:

```python
def get_grade():
    while True:
        try:
            grade = int(input("Grade (0-100): "))
            if grade < 0 or grade > 100:
                print("Grade must be 0-100!")
                continue
            return grade
        except ValueError:
            print("Please enter a number!")

grade = get_grade()
print(f"Grade: {grade}")
```

---

## Common Mistakes

```python
# ✗ WRONG - Catching too broad exception
try:
    age = int(input("Age: "))
except:              # Catches ALL errors (bad practice)
    print("Error")

# ✓ CORRECT - Catch specific exception
try:
    age = int(input("Age: "))
except ValueError:
    print("Please enter a number!")

# ✗ WRONG - Empty except
try:
    risky_code()
except:
    pass            # Silently ignores all errors (dangerous!)

# ✓ CORRECT - Handle properly
try:
    risky_code()
except Exception as e:
    print(f"Error: {e}")

# ✗ WRONG - Exception handling only
try:
    file = open("data.txt")
    data = file.read()
except:
    print("Error")
# File never closed!

# ✓ CORRECT - Use finally
try:
    file = open("data.txt")
    data = file.read()
except FileNotFoundError:
    print("File not found")
finally:
    file.close()
```

---

## Key Takeaways

✓ `try-except` catches errors and prevents crashes  
✓ Handle specific exception types  
✓ `else` runs if no error; `finally` always runs  
✓ Use try-except for: user input, file operations, calculations  
✓ Provide helpful error messages  
✓ Never use bare `except:` or `except Exception:`  
✓ Clean up resources in `finally` block  

---

## Quick Reference

```python
# Basic try-except
try:
    risky_code()
except ErrorType:
    print("Error occurred")

# Multiple exceptions
try:
    code()
except ValueError:
    print("Value error")
except KeyError:
    print("Key error")

# With else and finally
try:
    code()
except Error:
    print("Error")
else:
    print("Success")
finally:
    print("Cleanup")

# Raise exception
if condition:
    raise ValueError("Message")
```

---

## Homework

1. ✓ Create a calculator with error handling for all operations
2. ✓ Create a program that reads user ages and validates (0-150)
3. ✓ Create file operations with FileNotFoundError handling
4. ✓ Create a function that raises custom exceptions

Next hour: **Object-Oriented Programming!**
