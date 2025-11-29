# Day 4 - Hour 1: File Handling

## Welcome to Day 4!

Welcome to **Intermediate Python Day**! Today we're learning real-world skills: working with files, modules, error handling, and object-oriented programming.

Let's start with **file handling** - the ability to read and write files. This is crucial because real programs work with data stored on disk!

---

## Why Work with Files?

Programs need to:
- **Read** configuration files
- **Read** data files
- **Write** logs
- **Save** user data
- **Process** documents

File handling is essential for real-world applications!

---

## Opening Files

### The `open()` Function

```python
file = open("filename.txt", "mode")
```

**Modes:**
- `"r"` - Read (default, file must exist)
- `"w"` - Write (creates new or overwrites)
- `"a"` - Append (adds to end)
- `"x"` - Create (error if exists)
- `"b"` - Binary (add to above, e.g., "rb", "wb")

### Basic Reading

```python
# Open and read
file = open("my_file.txt", "r")
content = file.read()           # Read entire file
print(content)
file.close()                    # IMPORTANT: Always close!
```

---

## Reading Files Properly

### Using `with` Statement (Best Practice!)

The `with` statement automatically closes the file:

```python
# Recommended approach
with open("my_file.txt", "r") as file:
    content = file.read()
    print(content)

# File automatically closed here
```

### Read Entire File

```python
with open("my_file.txt", "r") as file:
    content = file.read()
    print(content)
```

### Read Line by Line

```python
with open("my_file.txt", "r") as file:
    # Read one line
    line = file.readline()
    print(line)
    
    # Read all lines as list
    lines = file.readlines()
    print(lines)
```

### Iterate Through Lines

```python
with open("my_file.txt", "r") as file:
    for line in file:
        print(line.strip())     # strip() removes newline
```

---

## Writing Files

### Write (Overwrites)

```python
with open("output.txt", "w") as file:
    file.write("Hello, World!\n")
    file.write("This is line 2\n")
```

### Append (Adds to End)

```python
with open("output.txt", "a") as file:
    file.write("Added line\n")
```

### Write Multiple Lines

```python
lines = ["Line 1\n", "Line 2\n", "Line 3\n"]

with open("output.txt", "w") as file:
    file.writelines(lines)
```

---

## Practical File Examples

### Example 1: Create a File

```python
# Create a file with user information
with open("user_data.txt", "w") as file:
    name = input("Name: ")
    age = input("Age: ")
    email = input("Email: ")
    
    file.write(f"Name: {name}\n")
    file.write(f"Age: {age}\n")
    file.write(f"Email: {email}\n")

print("User data saved!")
```

### Example 2: Read and Display

```python
# Read and display file
with open("user_data.txt", "r") as file:
    content = file.read()
    print(content)
```

### Example 3: Count Lines and Words

```python
file_path = "my_file.txt"

with open(file_path, "r") as file:
    lines = file.readlines()
    word_count = 0
    
    for line in lines:
        words = line.split()
        word_count += len(words)
    
    print(f"Lines: {len(lines)}")
    print(f"Words: {word_count}")
```

### Example 4: Copy File

```python
# Copy one file to another
with open("source.txt", "r") as source:
    content = source.read()

with open("destination.txt", "w") as dest:
    dest.write(content)

print("File copied!")
```

### Example 5: Process Data File

```python
# Read numbers and calculate average
with open("numbers.txt", "r") as file:
    numbers = []
    for line in file:
        num = int(line.strip())
        numbers.append(num)
    
    average = sum(numbers) / len(numbers)
    print(f"Average: {average:.2f}")
```

---

## Working with CSV Files

CSV (Comma-Separated Values) is a common format.

### Reading CSV

```python
# Read simple CSV file
with open("students.csv", "r") as file:
    for line in file:
        parts = line.strip().split(",")
        name, age, grade = parts
        print(f"{name} - Age {age} - Grade {grade}")
```

### Writing CSV

```python
# Write CSV file
with open("output.csv", "w") as file:
    file.write("name,age,grade\n")
    file.write("Alice,25,A\n")
    file.write("Bob,23,B\n")
    file.write("Charlie,24,A\n")
```

---

## File Path Handling

### Absolute vs Relative Paths

```python
# Absolute path (full path from root)
# Windows: "C:\\Users\\Name\\file.txt"
# Mac/Linux: "/home/user/file.txt"

# Relative path (from current directory)
file = open("file.txt", "r")
file = open("data/file.txt", "r")
file = open("../parent/file.txt", "r")
```

### Using `os` Module for Paths

```python
import os

# Check if file exists
if os.path.exists("my_file.txt"):
    print("File exists!")
else:
    print("File not found")

# Get file size
size = os.path.getsize("my_file.txt")
print(f"File size: {size} bytes")

# Get current directory
current_dir = os.getcwd()
print(f"Current directory: {current_dir}")
```

---

## Error Handling with Files

Files might not exist or be readable. Handle errors gracefully!

```python
try:
    with open("file.txt", "r") as file:
        content = file.read()
except FileNotFoundError:
    print("File not found!")
except IOError:
    print("Error reading file!")
```

---

## Project 1: Simple Note-Taking App

```python
def save_note():
    filename = input("Filename: ")
    content = input("Enter note content:\n")
    
    with open(filename, "w") as file:
        file.write(content)
    
    print("Note saved!")

def read_note():
    filename = input("Filename: ")
    
    try:
        with open(filename, "r") as file:
            content = file.read()
            print("\n--- Content ---")
            print(content)
    except FileNotFoundError:
        print("File not found!")

# Main program
while True:
    print("\n1. Save note  2. Read note  3. Exit")
    choice = input("Choice: ")
    
    if choice == "1":
        save_note()
    elif choice == "2":
        read_note()
    elif choice == "3":
        break
```

---

## Project 2: To-Do List Saver

```python
def load_todos():
    """Load todos from file"""
    try:
        with open("todos.txt", "r") as file:
            return [line.strip() for line in file.readlines()]
    except FileNotFoundError:
        return []

def save_todos(todos):
    """Save todos to file"""
    with open("todos.txt", "w") as file:
        for todo in todos:
            file.write(todo + "\n")

# Main program
todos = load_todos()

while True:
    print("\n1. Add  2. View  3. Remove  4. Exit")
    choice = input("Choice: ")
    
    if choice == "1":
        todo = input("Add todo: ")
        todos.append(todo)
        save_todos(todos)
        print("Saved!")
    
    elif choice == "2":
        for i, todo in enumerate(todos):
            print(f"{i+1}. {todo}")
    
    elif choice == "3":
        index = int(input("Remove number: ")) - 1
        removed = todos.pop(index)
        save_todos(todos)
        print(f"Removed: {removed}")
    
    elif choice == "4":
        break
```

---

## Exercises

### Exercise 1: Create File

Create `file1.py`:

```python
# Create a file with your information
with open("info.txt", "w") as file:
    file.write("Name: Your Name\n")
    file.write("Age: Your Age\n")
    file.write("Hobbies: Your Hobbies\n")

print("File created!")
```

### Exercise 2: Read File

Create `file2.py`:

```python
# Read and display file
with open("info.txt", "r") as file:
    for line in file:
        print(line.strip())
```

### Exercise 3: Count Lines

Create `file3.py`:

```python
# Count lines in a file
filename = input("Filename: ")

with open(filename, "r") as file:
    lines = file.readlines()
    print(f"Total lines: {len(lines)}")
```

### Exercise 4: Copy Content

Create `file4.py`:

```python
# Copy file content
source = input("Source file: ")
destination = input("Destination file: ")

with open(source, "r") as src:
    content = src.read()

with open(destination, "w") as dest:
    dest.write(content)

print("Copied!")
```

---

## Common Mistakes

```python
# ✗ WRONG - Not closing file
file = open("file.txt", "r")
content = file.read()
# File left open!

# ✓ CORRECT - Using with statement
with open("file.txt", "r") as file:
    content = file.read()
# Automatically closed

# ✗ WRONG - File not found
with open("nonexistent.txt", "r") as file:  # FileNotFoundError
    content = file.read()

# ✓ CORRECT - Check first or handle error
import os
if os.path.exists("nonexistent.txt"):
    with open("nonexistent.txt", "r") as file:
        content = file.read()
```

---

## Key Takeaways

✓ Use `open()` to work with files  
✓ Always use `with` statement (auto-closes)  
✓ Modes: "r" (read), "w" (write), "a" (append)  
✓ Read: `read()`, `readline()`, `readlines()`  
✓ Write: `write()`, `writelines()`  
✓ Handle file errors gracefully  
✓ Close files properly (done with `with`)  

---

## Quick Reference

```python
# Read entire file
with open("file.txt", "r") as file:
    content = file.read()

# Read line by line
with open("file.txt", "r") as file:
    for line in file:
        print(line.strip())

# Write to file
with open("file.txt", "w") as file:
    file.write("Hello")

# Append to file
with open("file.txt", "a") as file:
    file.write("New line")

# Check if exists
import os
if os.path.exists("file.txt"):
    print("Exists")
```

---

## Homework

1. ✓ Create a file and write 5 lines of text
2. ✓ Read a file and count total characters
3. ✓ Create a program that appends user input to a file
4. ✓ Copy content from one file to another

Next hour: **Modules & Packages!**
