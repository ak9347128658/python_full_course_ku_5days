# Day 3 - Hour 1: Lists

## Welcome to Day 3!

Welcome to **Data Structures Day**! Today we're learning about collections - ways to group multiple values together. The first and most important is the **list**.

A list is like a shopping list: you can have multiple items, add more, remove items, and look at any item you want.

---

## What is a List?

A **list** is an ordered collection of items. Items can be of any type (strings, numbers, booleans, even other lists!).

```python
# Simple list
fruits = ["apple", "banana", "orange"]

# List with numbers
scores = [85, 90, 78, 92]

# List with mixed types
mixed = [1, "two", 3.0, True]

# Empty list
empty = []
```

---

## Creating Lists

### Syntax

```python
list_name = [item1, item2, item3]
```

### Examples

```python
# String list
colors = ["red", "green", "blue"]

# Number list
ages = [25, 30, 22, 28, 35]

# Mixed list
data = ["Alice", 25, 3.8, True]

# Empty list
my_list = []

# Create list using list() constructor
numbers = list(range(5))        # [0, 1, 2, 3, 4]
```

---

## Accessing List Items

Lists are **indexed**, meaning each item has a position number. **Indexing starts at 0!**

```python
fruits = ["apple", "banana", "orange"]

# Index:      0         1          2

print(fruits[0])                # apple
print(fruits[1])                # banana
print(fruits[2])                # orange
```

### Negative Indexing

Negative numbers count from the end:

```python
fruits = ["apple", "banana", "orange"]

# Index:  -3        -2         -1

print(fruits[-1])               # orange (last item)
print(fruits[-2])               # banana
print(fruits[-3])               # apple (first item)
```

### Out of Range

```python
fruits = ["apple", "banana", "orange"]

print(fruits[5])                # IndexError: list index out of range
```

---

## List Slicing

Get multiple items using slice notation: `list[start:end:step]`

```python
numbers = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

print(numbers[2:5])             # [2, 3, 4] (from index 2 to 4)
print(numbers[:5])              # [0, 1, 2, 3, 4] (from start to 4)
print(numbers[5:])              # [5, 6, 7, 8, 9] (from 5 to end)
print(numbers[::2])             # [0, 2, 4, 6, 8] (every 2nd item)
print(numbers[::-1])            # [9, 8, 7, 6, 5, 4, 3, 2, 1, 0] (reversed!)
```

---

## Modifying Lists

### Adding Items

#### `append()` - Add to end

```python
fruits = ["apple", "banana"]
fruits.append("orange")
print(fruits)                   # ['apple', 'banana', 'orange']
```

#### `insert()` - Add at specific position

```python
fruits = ["apple", "banana"]
fruits.insert(1, "orange")      # Insert at index 1
print(fruits)                   # ['apple', 'orange', 'banana']
```

#### `extend()` - Add multiple items

```python
fruits = ["apple", "banana"]
fruits.extend(["orange", "grape"])
print(fruits)                   # ['apple', 'banana', 'orange', 'grape']
```

### Removing Items

#### `remove()` - Remove by value

```python
fruits = ["apple", "banana", "orange"]
fruits.remove("banana")
print(fruits)                   # ['apple', 'orange']

# If item not found:
fruits.remove("grape")          # ValueError
```

#### `pop()` - Remove by index

```python
fruits = ["apple", "banana", "orange"]
removed = fruits.pop()          # Remove last item
print(removed)                  # orange
print(fruits)                   # ['apple', 'banana']

fruits.pop(0)                   # Remove first item
print(fruits)                   # ['banana']
```

#### `clear()` - Remove all items

```python
fruits = ["apple", "banana", "orange"]
fruits.clear()
print(fruits)                   # []
```

### Modifying Items

```python
fruits = ["apple", "banana", "orange"]
fruits[1] = "grape"
print(fruits)                   # ['apple', 'grape', 'orange']
```

---

## List Useful Methods

### `len()` - Get list length

```python
fruits = ["apple", "banana", "orange"]
print(len(fruits))              # 3
```

### `count()` - Count occurrences

```python
numbers = [1, 2, 2, 3, 2, 4]
print(numbers.count(2))         # 3
```

### `index()` - Find position of item

```python
fruits = ["apple", "banana", "orange"]
print(fruits.index("banana"))   # 1

fruits.index("grape")           # ValueError (not found)
```

### `sort()` - Sort in place

```python
numbers = [3, 1, 4, 1, 5, 9]
numbers.sort()
print(numbers)                  # [1, 1, 3, 4, 5, 9]

# Reverse sort
numbers.sort(reverse=True)
print(numbers)                  # [9, 5, 4, 3, 1, 1]
```

### `reverse()` - Reverse order

```python
numbers = [1, 2, 3, 4, 5]
numbers.reverse()
print(numbers)                  # [5, 4, 3, 2, 1]
```

### `copy()` - Create a copy

```python
original = [1, 2, 3]
copy_list = original.copy()

copy_list[0] = 99
print(original)                 # [1, 2, 3] (unchanged)
print(copy_list)                # [99, 2, 3]
```

---

## Iterating Through Lists

### Using `for` loop

```python
fruits = ["apple", "banana", "orange"]

for fruit in fruits:
    print(fruit)

# Output:
# apple
# banana
# orange
```

### Using `for` with `range()` and index

```python
fruits = ["apple", "banana", "orange"]

for i in range(len(fruits)):
    print(f"Index {i}: {fruits[i]}")

# Output:
# Index 0: apple
# Index 1: banana
# Index 2: orange
```

### Using `enumerate()` - Get index and value

```python
fruits = ["apple", "banana", "orange"]

for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")

# Output:
# 0: apple
# 1: banana
# 2: orange
```

---

## List Comprehension (Advanced)

Create lists in a compact way:

```python
# Create list of squares
squares = [x ** 2 for x in range(5)]
print(squares)                  # [0, 1, 4, 9, 16]

# Create list with condition
evens = [x for x in range(10) if x % 2 == 0]
print(evens)                    # [0, 2, 4, 6, 8]

# Convert to uppercase
words = ["hello", "world"]
upper_words = [word.upper() for word in words]
print(upper_words)              # ['HELLO', 'WORLD']
```

---

## Real-World Examples

### Example 1: Grade Average

```python
scores = [85, 90, 78, 92, 88]
average = sum(scores) / len(scores)
print(f"Average: {average:.2f}")  # Average: 86.60
```

### Example 2: Student Management

```python
students = ["Alice", "Bob", "Charlie"]

# Add student
students.append("David")

# Remove student
students.remove("Bob")

# Get student count
print(f"Total students: {len(students)}")

# Print all
for student in students:
    print(student)
```

### Example 3: Find Maximum

```python
scores = [85, 92, 78, 95, 88]
max_score = max(scores)
min_score = min(scores)
total = sum(scores)

print(f"Highest: {max_score}")
print(f"Lowest: {min_score}")
print(f"Total: {total}")
```

### Example 4: Filter and Transform

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Get only even numbers
evens = [n for n in numbers if n % 2 == 0]
print(evens)                    # [2, 4, 6, 8, 10]

# Square all numbers
squared = [n ** 2 for n in numbers]
print(squared)                  # [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

---

## Project 1: Todo List

```python
todos = []

while True:
    print("\n1. Add task  2. View tasks  3. Remove task  4. Exit")
    choice = input("Choice: ")
    
    if choice == "1":
        task = input("Enter task: ")
        todos.append(task)
        print(f"'{task}' added!")
    
    elif choice == "2":
        if todos:
            for i, task in enumerate(todos):
                print(f"{i+1}. {task}")
        else:
            print("No tasks!")
    
    elif choice == "3":
        index = int(input("Remove task number: ")) - 1
        removed = todos.pop(index)
        print(f"Removed '{removed}'")
    
    elif choice == "4":
        break
```

---

## Exercises

### Exercise 1: List Basics

Create `list1.py`:

```python
numbers = [10, 20, 30, 40, 50]

# Print all
print(numbers)

# Add 60
numbers.append(60)

# Remove 30
numbers.remove(30)

# Print length
print(f"Length: {len(numbers)}")
```

### Exercise 2: Slicing

Create `list2.py`:

```python
numbers = list(range(1, 11))  # [1, 2, ..., 10]

print(numbers[2:7])           # Items 2 to 6
print(numbers[:5])            # First 5 items
print(numbers[-3:])           # Last 3 items
print(numbers[::2])           # Every 2nd item
```

### Exercise 3: Iteration

Create `list3.py`:

```python
fruits = ["apple", "banana", "orange", "grape"]

# Print each with index
for i, fruit in enumerate(fruits):
    print(f"{i+1}. {fruit}")
```

### Exercise 4: Analysis

Create `list4.py`:

```python
scores = [75, 85, 90, 78, 92, 88]

print(f"Highest: {max(scores)}")
print(f"Lowest: {min(scores)}")
print(f"Average: {sum(scores)/len(scores):.2f}")
```

---

## Common Mistakes

```python
# ✗ WRONG - Out of bounds
fruits = ["apple", "banana"]
print(fruits[5])              # IndexError

# ✓ CORRECT
print(fruits[0])              # apple

# ✗ WRONG - Modifying while iterating
for fruit in fruits:
    fruits.remove(fruit)      # Unpredictable behavior

# ✓ CORRECT
fruits_to_remove = ["apple"]
for fruit in fruits_to_remove:
    fruits.remove(fruit)

# ✗ WRONG - Forgetting list is mutable
list1 = [1, 2, 3]
list2 = list1
list2[0] = 99
print(list1)                  # [99, 2, 3] - Both changed!

# ✓ CORRECT
list1 = [1, 2, 3]
list2 = list1.copy()          # Create separate copy
list2[0] = 99
print(list1)                  # [1, 2, 3] - Original unchanged
```

---

## Key Takeaways

✓ Lists store multiple items in order  
✓ Index starts at 0; negative indices count from end  
✓ Use `append()`, `insert()`, `remove()` to modify  
✓ Slice lists with `list[start:end:step]`  
✓ Iterate with `for` loops or `enumerate()`  
✓ Common methods: `len()`, `sort()`, `max()`, `min()`, `sum()`  
✓ List comprehension creates lists compactly  

---

## Quick Reference

```python
# Create list
my_list = [1, 2, 3]

# Access
my_list[0]                  # First item
my_list[-1]                 # Last item
my_list[1:3]                # Slice

# Modify
my_list.append(4)           # Add to end
my_list.insert(0, 0)        # Insert at index
my_list.remove(2)           # Remove by value
my_list.pop()               # Remove last

# Info
len(my_list)                # Length
max(my_list)                # Maximum
sum(my_list)                # Sum

# Iterate
for item in my_list:
    print(item)
```

---

## Homework

1. ✓ Create a list of 5 numbers and find max, min, average
2. ✓ Create a program that adds/removes items from a list
3. ✓ Use list comprehension to create [1, 4, 9, 16, 25]
4. ✓ Create a program that reverses a list

Next hour: **Tuples!**
