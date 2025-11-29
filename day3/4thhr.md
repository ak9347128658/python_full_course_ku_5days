# Day 3 - Hour 4: Dictionaries

## Welcome to the Final Hour of Day 3!

You've learned lists, tuples, and sets. Now comes **dictionaries** - the most powerful and useful data structure! Dictionaries store **key-value pairs**, like a real dictionary where you look up a word (key) to find its meaning (value).

---

## What is a Dictionary?

A **dictionary** is an unordered collection of **key-value pairs**.

```python
# Dictionary syntax
student = {
    "name": "Alice",
    "age": 25,
    "gpa": 3.8
}

# Access by key
print(student["name"])          # Alice
print(student["age"])           # 25
```

Unlike lists which use numbers (0, 1, 2), dictionaries use **meaningful keys**.

---

## Creating Dictionaries

### Syntax

```python
dict_name = {
    key1: value1,
    key2: value2,
    key3: value3
}
```

### Examples

```python
# Simple dictionary
person = {
    "name": "Bob",
    "age": 30,
    "city": "New York"
}

# Number keys and values
scores = {
    "math": 95,
    "english": 88,
    "science": 92
}

# Mixed types
mixed = {
    "name": "Alice",
    1: "one",
    True: "boolean",
    3.14: "pi"
}

# Empty dictionary
empty = {}

# Create from list of tuples
data = dict([("name", "Alice"), ("age", 25)])
print(data)                     # {'name': 'Alice', 'age': 25}
```

---

## Accessing Dictionary Values

### By Key

```python
person = {
    "name": "Alice",
    "age": 25,
    "city": "New York"
}

print(person["name"])           # Alice
print(person["age"])            # 25
print(person["city"])           # New York
```

### KeyError - Key Doesn't Exist

```python
person = {"name": "Alice", "age": 25}
print(person["email"])          # KeyError: 'email'
```

### Using `get()` - Safe Access

```python
person = {"name": "Alice", "age": 25}

print(person.get("name"))       # Alice
print(person.get("email"))      # None (no error!)
print(person.get("email", "Not found"))  # Not found (default value)
```

---

## Modifying Dictionaries

### Adding Items

```python
student = {"name": "Alice"}

# Add new key-value pair
student["age"] = 25
student["gpa"] = 3.8

print(student)
# {'name': 'Alice', 'age': 25, 'gpa': 3.8}
```

### Updating Items

```python
student = {"name": "Alice", "age": 25}

# Update existing key
student["age"] = 26
student["name"] = "Alicia"

print(student)
# {'name': 'Alicia', 'age': 26}
```

### Removing Items

#### `del` - Delete a key-value pair

```python
student = {"name": "Alice", "age": 25, "gpa": 3.8}

del student["gpa"]
print(student)                  # {'name': 'Alice', 'age': 25}

del student["email"]            # KeyError
```

#### `pop()` - Remove and return value

```python
student = {"name": "Alice", "age": 25}

age = student.pop("age")
print(age)                      # 25
print(student)                  # {'name': 'Alice'}

student.pop("email", "Not found")  # Returns "Not found"
```

#### `clear()` - Remove all items

```python
student = {"name": "Alice", "age": 25}
student.clear()
print(student)                  # {}
```

---

## Dictionary Methods

### `keys()` - Get all keys

```python
student = {"name": "Alice", "age": 25, "gpa": 3.8}

keys = student.keys()
print(keys)                     # dict_keys(['name', 'age', 'gpa'])

# Convert to list
keys_list = list(keys)
print(keys_list)                # ['name', 'age', 'gpa']
```

### `values()` - Get all values

```python
student = {"name": "Alice", "age": 25, "gpa": 3.8}

values = student.values()
print(values)                   # dict_values(['Alice', 25, 3.8])

# Convert to list
values_list = list(values)
print(values_list)              # ['Alice', 25, 3.8]
```

### `items()` - Get key-value pairs

```python
student = {"name": "Alice", "age": 25}

items = student.items()
print(items)                    # dict_items([('name', 'Alice'), ('age', 25)])

# Convert to list of tuples
items_list = list(items)
print(items_list)               # [('name', 'Alice'), ('age', 25)]
```

### `update()` - Merge dictionaries

```python
student = {"name": "Alice"}
more_info = {"age": 25, "city": "New York"}

student.update(more_info)
print(student)
# {'name': 'Alice', 'age': 25, 'city': 'New York'}
```

### `copy()` - Create a copy

```python
original = {"name": "Alice", "age": 25}
copy_dict = original.copy()

copy_dict["age"] = 30
print(original)                 # {'name': 'Alice', 'age': 25}
print(copy_dict)                # {'name': 'Alice', 'age': 30}
```

---

## Iterating Through Dictionaries

### Iterate over keys

```python
student = {"name": "Alice", "age": 25, "gpa": 3.8}

for key in student:
    print(key)

# Output:
# name
# age
# gpa
```

### Iterate over values

```python
student = {"name": "Alice", "age": 25, "gpa": 3.8}

for value in student.values():
    print(value)

# Output:
# Alice
# 25
# 3.8
```

### Iterate over key-value pairs

```python
student = {"name": "Alice", "age": 25, "gpa": 3.8}

for key, value in student.items():
    print(f"{key}: {value}")

# Output:
# name: Alice
# age: 25
# gpa: 3.8
```

---

## Nested Dictionaries

Dictionaries inside dictionaries!

```python
# Company data
company = {
    "name": "TechCorp",
    "employees": {
        "alice": {"role": "Developer", "salary": 80000},
        "bob": {"role": "Designer", "salary": 70000},
        "charlie": {"role": "Manager", "salary": 90000}
    }
}

# Access nested values
print(company["name"])                          # TechCorp
print(company["employees"]["alice"]["role"])   # Developer
print(company["employees"]["bob"]["salary"])   # 70000
```

---

## Real-World Examples

### Example 1: Student Grades

```python
grades = {
    "Alice": [85, 90, 88],
    "Bob": [92, 88, 95],
    "Charlie": [78, 82, 80]
}

# Calculate average for each student
for student, scores in grades.items():
    average = sum(scores) / len(scores)
    print(f"{student}: {average:.2f}")

# Output:
# Alice: 87.67
# Bob: 91.67
# Charlie: 80.00
```

### Example 2: Phone Book

```python
phonebook = {
    "Alice": "555-1234",
    "Bob": "555-5678",
    "Charlie": "555-9012"
}

# Look up phone number
name = "Bob"
if name in phonebook:
    print(f"Phone: {phonebook[name]}")
else:
    print("Not found")
```

### Example 3: Product Inventory

```python
inventory = {
    "apple": 50,
    "banana": 30,
    "orange": 20
}

# Update stock
inventory["apple"] -= 5
inventory["banana"] += 10

# Display inventory
for product, quantity in inventory.items():
    print(f"{product}: {quantity}")
```

### Example 4: Configuration Settings

```python
config = {
    "host": "localhost",
    "port": 8000,
    "debug": True,
    "database": {
        "name": "mydb",
        "user": "admin",
        "password": "secret"
    }
}

# Access settings
print(f"Server: {config['host']}:{config['port']}")
print(f"Debug mode: {config['debug']}")
print(f"Database: {config['database']['name']}")
```

---

## Project 1: Contact Manager

```python
contacts = {}

while True:
    print("\n1. Add contact  2. View contact  3. Remove contact  4. Show all  5. Exit")
    choice = input("Choice: ")
    
    if choice == "1":
        name = input("Name: ")
        phone = input("Phone: ")
        email = input("Email: ")
        contacts[name] = {"phone": phone, "email": email}
        print(f"Added {name}")
    
    elif choice == "2":
        name = input("Name: ")
        if name in contacts:
            contact = contacts[name]
            print(f"Name: {name}")
            print(f"Phone: {contact['phone']}")
            print(f"Email: {contact['email']}")
        else:
            print("Contact not found")
    
    elif choice == "3":
        name = input("Name: ")
        if name in contacts:
            del contacts[name]
            print(f"Deleted {name}")
        else:
            print("Contact not found")
    
    elif choice == "4":
        if contacts:
            for name, info in contacts.items():
                print(f"{name}: {info['phone']}")
        else:
            print("No contacts")
    
    elif choice == "5":
        break
```

---

## Project 2: Student Grade System

```python
students = {}

while True:
    print("\n1. Add student  2. View grades  3. Add grade  4. Average  5. Exit")
    choice = input("Choice: ")
    
    if choice == "1":
        name = input("Name: ")
        students[name] = []
        print(f"Added {name}")
    
    elif choice == "2":
        name = input("Name: ")
        if name in students:
            grades = students[name]
            if grades:
                print(f"Grades: {grades}")
            else:
                print("No grades yet")
        else:
            print("Student not found")
    
    elif choice == "3":
        name = input("Name: ")
        if name in students:
            grade = int(input("Grade: "))
            students[name].append(grade)
            print("Grade added")
        else:
            print("Student not found")
    
    elif choice == "4":
        name = input("Name: ")
        if name in students:
            grades = students[name]
            if grades:
                avg = sum(grades) / len(grades)
                print(f"Average: {avg:.2f}")
            else:
                print("No grades yet")
        else:
            print("Student not found")
    
    elif choice == "5":
        break
```

---

## Exercises

### Exercise 1: Dictionary Basics

Create `dict1.py`:

```python
person = {
    "name": "Alice",
    "age": 25,
    "city": "New York"
}

# Access values
print(person["name"])
print(person["age"])

# Add new key
person["job"] = "Engineer"

# Display all
print(person)
```

### Exercise 2: Dictionary Iteration

Create `dict2.py`:

```python
scores = {"math": 95, "english": 88, "science": 92}

# Print all
for subject, score in scores.items():
    print(f"{subject}: {score}")

# Calculate average
average = sum(scores.values()) / len(scores)
print(f"Average: {average:.2f}")
```

### Exercise 3: Nested Dictionary

Create `dict3.py`:

```python
company = {
    "employees": {
        "alice": {"role": "Developer", "salary": 80000},
        "bob": {"role": "Designer", "salary": 70000}
    }
}

# Access nested values
for name, info in company["employees"].items():
    print(f"{name}: {info['role']} (${info['salary']})")
```

### Exercise 4: Dictionary Methods

Create `dict4.py`:

```python
dictionary = {"a": 1, "b": 2, "c": 3}

print("Keys:", list(dictionary.keys()))
print("Values:", list(dictionary.values()))
print("Items:", list(dictionary.items()))
```

---

## Common Mistakes

```python
# ✗ WRONG - Using list as key
dict_bad = {[1, 2]: "value"}    # TypeError: unhashable type

# ✓ CORRECT - Use tuple as key
dict_good = {(1, 2): "value"}

# ✗ WRONG - Accessing non-existent key
my_dict = {"name": "Alice"}
print(my_dict["age"])           # KeyError

# ✓ CORRECT - Use get() method
print(my_dict.get("age", "Unknown"))

# ✗ WRONG - Confusing dict() with dict literal
# Both work but different syntax
dict1 = {"a": 1}                # Literal (preferred)
dict2 = dict(a=1)               # Constructor
```

---

## Key Takeaways

✓ Dictionaries store key-value pairs  
✓ Access with `dict[key]` or `dict.get(key)`  
✓ Add/modify with `dict[key] = value`  
✓ Remove with `del dict[key]` or `pop()`  
✓ Iterate with `.keys()`, `.values()`, `.items()`  
✓ Keys must be immutable (strings, numbers, tuples)  
✓ Great for structured data and lookups  

---

## Quick Reference

```python
# Create
my_dict = {"key1": "value1", "key2": "value2"}

# Access
my_dict["key1"]                 # value1
my_dict.get("key2")             # value2

# Add/modify
my_dict["key3"] = "value3"

# Remove
del my_dict["key1"]
my_dict.pop("key2")

# Check
"key1" in my_dict               # True

# Iterate
for key in my_dict:
    print(key)

for value in my_dict.values():
    print(value)

for key, value in my_dict.items():
    print(key, value)
```

---

## Congratulations! 🎉

You've completed **Day 3 - Data Structures**! You now know:
- ✓ Lists (ordered, mutable, indexed)
- ✓ Tuples (ordered, immutable)
- ✓ Sets (unordered, unique, mathematical operations)
- ✓ Dictionaries (key-value pairs)

**Tomorrow: Intermediate Python (File Handling, Modules, Error Handling, OOP)!**
