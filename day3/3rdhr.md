# Day 3 - Hour 3: Sets

## Welcome to Hour 3!

Now we're learning **sets** - unique, unordered collections. Use sets when you need to:
1. Store unique values (no duplicates!)
2. Quickly check if something exists
3. Perform mathematical operations (union, intersection)

Sets are powerful but work differently than lists and tuples!

---

## What is a Set?

A **set** is an unordered collection of unique items.

```python
# Set with items
colors = {"red", "green", "blue"}

# Set from list (removes duplicates!)
numbers = {1, 1, 2, 2, 3, 3}    # {1, 2, 3}

# Empty set (must use set(), not {})
empty = set()

# NOT empty - this is an empty dict
empty_dict = {}
```

---

## Creating Sets

### Syntax

```python
set_name = {item1, item2, item3}
```

### Examples

```python
# String set
colors = {"red", "green", "blue"}

# Number set
numbers = {1, 2, 3, 4, 5}

# Mixed types
mixed = {"apple", 1, 3.14, True}

# From a list
from_list = set([1, 2, 2, 3, 3, 4])
print(from_list)                # {1, 2, 3, 4}

# Empty set
empty = set()
print(type(empty))              # <class 'set'>
```

---

## Key Feature: Duplicates Removed

```python
# Create set with duplicates
numbers = {1, 1, 1, 2, 2, 3}

# Duplicates automatically removed
print(numbers)                  # {1, 2, 3}

# Useful for removing duplicates from list
my_list = [1, 1, 2, 2, 3, 3]
unique = set(my_list)
print(unique)                   # {1, 2, 3}

# Convert back to list
unique_list = list(unique)
print(unique_list)              # [1, 2, 3]
```

---

## Set Operations

### Adding Items

#### `add()` - Add single item

```python
colors = {"red", "green"}
colors.add("blue")
print(colors)                   # {'red', 'green', 'blue'}

# Adding duplicate does nothing
colors.add("red")
print(colors)                   # Unchanged
```

#### `update()` - Add multiple items

```python
colors = {"red", "green"}
colors.update(["blue", "yellow"])
print(colors)                   # {'red', 'green', 'blue', 'yellow'}
```

### Removing Items

#### `remove()` - Remove (error if not found)

```python
colors = {"red", "green", "blue"}
colors.remove("green")
print(colors)                   # {'red', 'blue'}

colors.remove("orange")         # KeyError (not found)
```

#### `discard()` - Remove (no error if not found)

```python
colors = {"red", "green", "blue"}
colors.discard("green")
print(colors)                   # {'red', 'blue'}

colors.discard("orange")        # No error!
print(colors)                   # {'red', 'blue'}
```

#### `pop()` - Remove random item

```python
colors = {"red", "green", "blue"}
removed = colors.pop()          # Remove a random item
print(removed)                  # Could be any color
print(colors)                   # 2 items left
```

#### `clear()` - Remove all items

```python
colors = {"red", "green", "blue"}
colors.clear()
print(colors)                   # set()
```

---

## Checking Set Membership

### `in` operator

```python
colors = {"red", "green", "blue"}

print("red" in colors)          # True
print("yellow" in colors)       # False

# Great for fast lookups!
if "green" in colors:
    print("Green is available")
```

---

## Iterating Through Sets

### Using `for` loop

```python
colors = {"red", "green", "blue"}

for color in colors:
    print(color)

# Order is not guaranteed (sets are unordered)
```

### Using `enumerate()` for index

```python
colors = {"red", "green", "blue"}

for index, color in enumerate(colors):
    print(f"{index}: {color}")
```

---

## Set Mathematical Operations

Sets support mathematical operations like union and intersection!

### Union `|` - Combine all items

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

union = set1 | set2
print(union)                    # {1, 2, 3, 4, 5}

# Using method
union = set1.union(set2)
print(union)                    # {1, 2, 3, 4, 5}
```

### Intersection `&` - Common items only

```python
set1 = {1, 2, 3}
set2 = {2, 3, 4}

intersection = set1 & set2
print(intersection)             # {2, 3}

# Using method
intersection = set1.intersection(set2)
print(intersection)             # {2, 3}
```

### Difference `-` - Items in first set only

```python
set1 = {1, 2, 3}
set2 = {2, 3, 4}

difference = set1 - set2
print(difference)               # {1}

# Using method
difference = set1.difference(set2)
print(difference)               # {1}
```

### Symmetric Difference `^` - Items not in both

```python
set1 = {1, 2, 3}
set2 = {2, 3, 4}

sym_diff = set1 ^ set2
print(sym_diff)                 # {1, 4}

# Using method
sym_diff = set1.symmetric_difference(set2)
print(sym_diff)                 # {1, 4}
```

---

## Set Comparison

### `issubset()` - Check if one set is inside another

```python
set1 = {1, 2}
set2 = {1, 2, 3}

print(set1.issubset(set2))      # True (all of set1 in set2)
print(set2.issubset(set1))      # False
```

### `issuperset()` - Check if one set contains another

```python
set1 = {1, 2, 3}
set2 = {1, 2}

print(set1.issuperset(set2))    # True (set1 contains all of set2)
print(set2.issuperset(set1))    # False
```

### `isdisjoint()` - Check if no common items

```python
set1 = {1, 2, 3}
set2 = {4, 5, 6}

print(set1.isdisjoint(set2))    # True (no common items)
```

---

## Real-World Examples

### Example 1: Remove Duplicates

```python
# Remove duplicate emails
emails = ["john@example.com", "jane@example.com", "john@example.com", "bob@example.com"]

unique_emails = list(set(emails))
print(unique_emails)
```

### Example 2: Find Common Friends

```python
alice_friends = {"Bob", "Charlie", "David"}
bob_friends = {"Alice", "Charlie", "Eve"}

common = alice_friends & bob_friends
print(f"Common friends: {common}")    # {'Charlie'}
```

### Example 3: Track Visited Pages

```python
visited = set()

# User visits pages
pages = ["home", "about", "contact", "home", "products", "home"]

for page in pages:
    visited.add(page)

print(f"Visited {len(visited)} unique pages: {visited}")
# Visited 4 unique pages: {'home', 'about', 'contact', 'products'}
```

### Example 4: Check Unique Languages

```python
required_languages = {"Python", "JavaScript", "SQL"}
my_languages = {"Python", "JavaScript", "Java", "C++"}

missing = required_languages - my_languages
extra = my_languages - required_languages

print(f"Missing: {missing}")        # {'SQL'}
print(f"Extra: {extra}")            # {'Java', 'C++'}
```

---

## Project 1: Inventory Manager

```python
inventory = set()

while True:
    print("\n1. Add item  2. Remove item  3. View items  4. Exit")
    choice = input("Choice: ")
    
    if choice == "1":
        item = input("Item to add: ")
        inventory.add(item)
        print(f"Added '{item}'")
    
    elif choice == "2":
        item = input("Item to remove: ")
        inventory.discard(item)
        print(f"Removed '{item}'")
    
    elif choice == "3":
        if inventory:
            print("Inventory:", inventory)
        else:
            print("Empty inventory")
    
    elif choice == "4":
        break
```

---

## Exercises

### Exercise 1: Basic Set Operations

Create `set1.py`:

```python
# Create sets
numbers1 = {1, 2, 3, 4, 5}
numbers2 = {4, 5, 6, 7, 8}

# Operations
print("Union:", numbers1 | numbers2)
print("Intersection:", numbers1 & numbers2)
print("Difference:", numbers1 - numbers2)
```

### Exercise 2: Remove Duplicates

Create `set2.py`:

```python
# Original list with duplicates
numbers = [1, 2, 2, 3, 3, 3, 4, 4, 5]

# Remove duplicates
unique = list(set(numbers))
print(f"Unique numbers: {sorted(unique)}")
```

### Exercise 3: Set Membership

Create `set3.py`:

```python
allowed_users = {"alice", "bob", "charlie"}

username = input("Username: ")

if username in allowed_users:
    print("Welcome!")
else:
    print("Access denied")
```

### Exercise 4: Find Common Items

Create `set4.py`:

```python
students_morning = {"Alice", "Bob", "Charlie"}
students_afternoon = {"Bob", "Charlie", "David"}

# Find students in both
both_classes = students_morning & students_afternoon
print(f"Students in both classes: {both_classes}")
```

---

## Common Mistakes

```python
# ✗ WRONG - Using {} for empty set creates dict
empty = {}
print(type(empty))              # <class 'dict'>

# ✓ CORRECT
empty = set()
print(type(empty))              # <class 'set'>

# ✗ WRONG - Sets don't support indexing
my_set = {1, 2, 3}
print(my_set[0])                # TypeError

# ✓ CORRECT - Convert to list if you need indexing
my_list = list(my_set)
print(my_list[0])

# ✗ WRONG - Assuming order
my_set = {3, 1, 2}
print(my_set)                   # Order not guaranteed

# ✓ CORRECT - Convert to sorted list
sorted_list = sorted(my_set)
print(sorted_list)              # [1, 2, 3]
```

---

## Key Takeaways

✓ Sets store unique values only  
✓ Unordered collection (no indexing)  
✓ Add/remove items with `add()`, `remove()`, `discard()`  
✓ Check membership with `in` operator  
✓ Use mathematical operations: union `|`, intersection `&`, difference `-`  
✓ Great for removing duplicates  
✓ Fast lookup time (excellent for membership checks)  

---

## Quick Reference

```python
# Create set
my_set = {1, 2, 3}

# Add
my_set.add(4)

# Remove
my_set.remove(2)                # Error if not found
my_set.discard(2)               # No error if not found

# Check membership
1 in my_set                     # True

# Mathematical operations
set1 | set2                     # Union
set1 & set2                     # Intersection
set1 - set2                     # Difference
set1 ^ set2                     # Symmetric difference

# Convert
my_list = list(my_set)
my_set = set(my_list)
```

---

## Homework

1. ✓ Create a set and add/remove multiple items
2. ✓ Find union and intersection of two sets
3. ✓ Remove duplicates from a list using set
4. ✓ Create a program that finds common items between two lists

Next hour: **Dictionaries!**
