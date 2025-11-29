# Day 3 - Hour 2: Tuples

## Welcome to Hour 2!

Now we're learning **tuples** - the immutable cousin of lists. Immutable means **you can't change them after creation**. Once a tuple is made, it stays exactly the same!

Why would you want something you can't change? Great question - tuples are useful for fixed data and as dictionary keys!

---

## What is a Tuple?

A **tuple** is an ordered collection of items that **cannot be changed** (immutable).

```python
# Tuple with parentheses
coordinates = (10, 20)

# Tuple without parentheses (still a tuple!)
point = 1, 2, 3

# Single item tuple (needs trailing comma!)
single = (42,)

# Empty tuple
empty = ()
```

---

## Creating Tuples

### Syntax

```python
tuple_name = (item1, item2, item3)
```

### Examples

```python
# Coordinate tuple
location = (40.7128, 74.0060)  # Latitude, Longitude

# RGB color
color = (255, 128, 0)

# Days of week
days = ("Monday", "Tuesday", "Wednesday")

# Mixed types
data = ("Alice", 25, 3.8)

# Single item (note the comma!)
single = (100,)
print(type(single))             # <class 'tuple'>

# Without comma - NOT a tuple!
not_tuple = (100)
print(type(not_tuple))          # <class 'int'>
```

---

## Accessing Tuple Items

Like lists, tuples are indexed starting at 0.

```python
rgb = (255, 128, 0)

print(rgb[0])                   # 255
print(rgb[1])                   # 128
print(rgb[2])                   # 0
print(rgb[-1])                  # 0 (last item)
```

### Slicing Tuples

```python
numbers = (0, 1, 2, 3, 4, 5)

print(numbers[1:4])             # (1, 2, 3)
print(numbers[:3])              # (0, 1, 2)
print(numbers[3:])              # (3, 4, 5)
print(numbers[::2])             # (0, 2, 4)
```

---

## Why Tuples are Immutable

### You CANNOT modify tuples

```python
colors = ("red", "green", "blue")

# ✗ This fails:
colors[0] = "yellow"            # TypeError

# ✗ This fails:
colors.append("purple")         # AttributeError (no append method)

# ✗ This fails:
colors.remove("red")            # AttributeError (no remove method)
```

### You CAN'T change them, but you CAN create new ones

```python
# Create new tuple by concatenating
original = (1, 2, 3)
new_tuple = original + (4, 5)
print(original)                 # (1, 2, 3) - unchanged
print(new_tuple)                # (1, 2, 3, 4, 5)

# Create new tuple by repeating
repeated = (1, 2) * 3
print(repeated)                 # (1, 2, 1, 2, 1, 2)
```

---

## Tuple Methods

Tuples have only 2 methods (compared to lists which have many):

### `count()` - Count occurrences

```python
numbers = (1, 2, 2, 3, 2, 4)
print(numbers.count(2))         # 3
print(numbers.count(5))         # 0
```

### `index()` - Find position

```python
fruits = ("apple", "banana", "orange")
print(fruits.index("banana"))   # 1

fruits.index("grape")           # ValueError (not found)
```

---

## Iterating Through Tuples

### Using `for` loop

```python
colors = ("red", "green", "blue")

for color in colors:
    print(color)

# Output:
# red
# green
# blue
```

### Using `enumerate()`

```python
colors = ("red", "green", "blue")

for index, color in enumerate(colors):
    print(f"{index}: {color}")

# Output:
# 0: red
# 1: green
# 2: blue
```

---

## Tuple Unpacking

Extract tuple values into individual variables:

```python
# Unpack a tuple
coordinates = (10, 20)
x, y = coordinates
print(x)                        # 10
print(y)                        # 20

# Unpack with more values
data = ("Alice", 25, "Engineer")
name, age, job = data
print(f"{name} is {age} and works as {job}")

# Unpack with *
numbers = (1, 2, 3, 4, 5)
first, *middle, last = numbers
print(first)                    # 1
print(middle)                   # [2, 3, 4]
print(last)                     # 5
```

---

## Tuples as Dictionary Keys

One big advantage of tuples: they can be dictionary keys (lists cannot).

```python
# ✓ Tuples work as keys
locations = {
    (40.7128, 74.0060): "New York",
    (51.5074, 0.1278): "London",
    (48.8566, 2.3522): "Paris"
}

print(locations[(40.7128, 74.0060)])  # New York

# ✗ Lists don't work as keys
locations = {
    [40.7128, 74.0060]: "New York"    # TypeError: unhashable type
}
```

---

## Functions Returning Tuples

Tuples are great for returning multiple values:

```python
def get_min_max(numbers):
    """Return minimum and maximum"""
    return (min(numbers), max(numbers))

result = get_min_max([5, 2, 8, 1, 9])
print(result)                   # (1, 9)

minimum, maximum = result       # Unpack
print(f"Min: {minimum}, Max: {maximum}")
```

### Practical Example

```python
def divmod_custom(a, b):
    """Return quotient and remainder"""
    quotient = a // b
    remainder = a % b
    return (quotient, remainder)

q, r = divmod_custom(17, 5)
print(f"17 ÷ 5 = {q} remainder {r}")  # 17 ÷ 5 = 3 remainder 2
```

---

## Tuples vs Lists

| Feature | List | Tuple |
|---------|------|-------|
| Changeable | Yes | No |
| Speed | Slower | Faster |
| Use as dict key | No | Yes |
| Syntax | `[]` | `()` |
| When to use | Changing data | Fixed data |

```python
# Use LIST when data changes
shopping = ["milk", "eggs", "bread"]
shopping.append("cheese")       # Add item

# Use TUPLE when data is fixed
rgb = (255, 0, 0)              # Never changes
coordinates = (10, 20)         # Never changes
```

---

## Real-World Examples

### Example 1: Store Fixed Data

```python
# Student information (doesn't change)
student = ("Alice", 25, 3.8, 12345)

name, age, gpa, student_id = student
print(f"Student: {name} (ID: {student_id})")
```

### Example 2: Return Multiple Values

```python
def get_user_info():
    """Get user info from input"""
    name = input("Name: ")
    age = int(input("Age: "))
    email = input("Email: ")
    return (name, age, email)

user = get_user_info()
name, age, email = user
print(f"{name} ({age}) - {email}")
```

### Example 3: Geometric Shapes

```python
shapes = [
    ("circle", (5,)),           # radius
    ("rectangle", (10, 5)),     # width, height
    ("triangle", (3, 4, 5))     # sides
]

for shape_type, dimensions in shapes:
    print(f"{shape_type}: {dimensions}")
```

---

## Project 1: Game Coordinates

```python
# Store player positions as tuples
players = {
    "Alice": (10, 20),
    "Bob": (15, 25),
    "Charlie": (5, 10)
}

# Find player position
target = "Bob"
if target in players:
    x, y = players[target]
    print(f"{target} is at ({x}, {y})")

# Move player (create new tuple)
players["Alice"] = (12, 22)     # New position
print(f"Alice moved to {players['Alice']}")
```

---

## Exercises

### Exercise 1: Basic Tuples

Create `tuple1.py`:

```python
# Create and access
colors = ("red", "green", "blue", "yellow")

print(colors[0])
print(colors[-1])
print(colors[1:3])
```

### Exercise 2: Unpacking

Create `tuple2.py`:

```python
# Unpack coordinates
point = (10, 20, 30)
x, y, z = point

print(f"X: {x}, Y: {y}, Z: {z}")
```

### Exercise 3: Tuple Operations

Create `tuple3.py`:

```python
# Create new tuples from old
t1 = (1, 2, 3)
t2 = (4, 5, 6)

combined = t1 + t2
print(combined)                 # (1, 2, 3, 4, 5, 6)

repeated = t1 * 2
print(repeated)                 # (1, 2, 3, 1, 2, 3)
```

### Exercise 4: Function Returns

Create `tuple4.py`:

```python
def swap(a, b):
    """Swap two values"""
    return (b, a)

x, y = swap(5, 10)
print(f"x: {x}, y: {y}")        # x: 10, y: 5
```

---

## Common Mistakes

```python
# ✗ WRONG - Trying to modify tuple
colors = ("red", "green")
colors[0] = "blue"              # TypeError

# ✓ CORRECT - Create new tuple
colors = ("blue", "green")

# ✗ WRONG - Single item without comma
single = (5)                    # This is an integer!
print(type(single))             # <class 'int'>

# ✓ CORRECT - Comma makes it a tuple
single = (5,)
print(type(single))             # <class 'tuple'>

# ✗ WRONG - Unpacking mismatch
data = (1, 2)
a, b, c = data                  # ValueError: not enough values

# ✓ CORRECT - Same number of variables
a, b = data
```

---

## Key Takeaways

✓ Tuples are immutable (can't change after creation)  
✓ Create with `()`, access with `[index]`  
✓ Use tuples for fixed data  
✓ Can use tuples as dictionary keys  
✓ Tuple unpacking extracts values  
✓ Only 2 methods: `count()` and `index()`  
✓ Functions can return tuples for multiple values  

---

## Quick Reference

```python
# Create tuple
my_tuple = (1, 2, 3)

# Access
my_tuple[0]                 # 1
my_tuple[-1]                # 3

# Slice
my_tuple[1:3]               # (2, 3)

# Unpack
a, b, c = my_tuple

# Concatenate
new_tuple = my_tuple + (4, 5)

# Repeat
repeated = my_tuple * 2

# Info
len(my_tuple)               # 3
```

---

## Homework

1. ✓ Create a tuple of RGB colors and unpack them
2. ✓ Create a function that returns (min, max, average) as tuple
3. ✓ Use tuples as dictionary keys for a coordinate system
4. ✓ Compare immutability of tuples vs lists

Next hour: **Sets!**
