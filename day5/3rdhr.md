# Day 5 - Hour 3: Virtual Environments, Pip, External Libraries

## Welcome to Hour 3!

Welcome to the world of **real Python development**! We're learning how to:
1. Use **virtual environments**
2. Manage packages with **pip**
3. Use **external libraries**

These are essential skills for professional Python development!

---

## Why Virtual Environments?

Imagine you have two projects:
- Project A needs `numpy` version 1.20
- Project B needs `numpy` version 1.25

Without virtual environments, you have a conflict! Virtual environments solve this by isolating each project's packages.

---

## Creating Virtual Environments

### On Windows PowerShell

```powershell
# Create virtual environment
python -m venv my_env

# Activate it
my_env\Scripts\Activate.ps1

# You should see (my_env) in your terminal
```

### On Mac/Linux

```bash
# Create virtual environment
python3 -m venv my_env

# Activate it
source my_env/bin/activate

# You should see (my_env) in your terminal
```

### What's in a Virtual Environment?

```
my_env/
  Scripts/         (Windows) or bin/ (Mac/Linux)
    activate       Scripts to activate environment
    python         Python executable
    pip            Package manager
  Lib/             Third-party packages installed here
  pyvenv.cfg       Configuration file
```

---

## Using Pip - Python Package Manager

### Check Installed Packages

```bash
pip list
```

Shows all installed packages in current environment.

### Search for Package

```bash
pip search requests
```

### Install Package

```bash
# Install latest version
pip install package_name

# Install specific version
pip install package_name==1.2.3

# Install from requirements file
pip install -r requirements.txt
```

### Uninstall Package

```bash
pip uninstall package_name
```

### Freeze Requirements

Create `requirements.txt` with all current packages:

```bash
pip freeze > requirements.txt
```

Then someone can install all at once:

```bash
pip install -r requirements.txt
```

---

## Popular External Libraries

### 1. `requests` - HTTP Requests

```bash
pip install requests
```

```python
import requests

# Fetch data from API
response = requests.get('https://api.example.com/data')
data = response.json()
print(data)

# Send POST request
payload = {"name": "Alice"}
response = requests.post('https://api.example.com/users', json=payload)
```

### 2. `numpy` - Numerical Computing

```bash
pip install numpy
```

```python
import numpy as np

# Create array
arr = np.array([1, 2, 3, 4, 5])
print(arr.mean())           # Average
print(arr.sum())            # Sum
print(arr * 2)              # Element-wise multiplication

# 2D array (matrix)
matrix = np.array([[1, 2], [3, 4]])
print(matrix.shape)         # (2, 2)
```

### 3. `pandas` - Data Analysis

```bash
pip install pandas
```

```python
import pandas as pd

# Read CSV
df = pd.read_csv('data.csv')

# Display first rows
print(df.head())

# Get column
names = df['name']

# Filter
adults = df[df['age'] > 18]

# Statistics
print(df.describe())
```

### 4. `matplotlib` - Data Visualization

```bash
pip install matplotlib
```

```python
import matplotlib.pyplot as plt

# Create plot
plt.plot([1, 2, 3, 4], [1, 4, 9, 16])
plt.xlabel('X axis')
plt.ylabel('Y axis')
plt.title('Simple Plot')
plt.show()
```

### 5. `Flask` - Web Framework

```bash
pip install flask
```

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello, World!'

if __name__ == '__main__':
    app.run()
```

### 6. `pytest` - Testing Framework

```bash
pip install pytest
```

```python
# test_math.py
def add(a, b):
    return a + b

def test_add():
    assert add(2, 3) == 5
    assert add(0, 0) == 0

# Run: pytest test_math.py
```

---

## Practical Example: Weather App

```bash
# Setup
python -m venv weather_env
# Activate environment

# Install requirements
pip install requests
```

Create `weather_app.py`:

```python
import requests

def get_weather(city):
    """Get weather for a city"""
    url = f"https://api.weatherapi.com/v1/current.json"
    params = {
        "key": "YOUR_API_KEY",  # Get from weatherapi.com
        "q": city,
        "aqi": "no"
    }
    
    response = requests.get(url, params=params)
    
    if response.status_code == 200:
        data = response.json()
        return {
            "city": data['location']['name'],
            "temp": data['current']['temp_c'],
            "condition": data['current']['condition']['text']
        }
    else:
        return None

# Use it
weather = get_weather("London")
if weather:
    print(f"Weather in {weather['city']}: {weather['temp']}°C, {weather['condition']}")
```

---

## Project 1: Simple Package

Create project structure:

```
my_package/
  my_package/
    __init__.py
    utils.py
  setup.py
  requirements.txt
```

In `my_package/utils.py`:

```python
def reverse_string(s):
    return s[::-1]

def is_palindrome(s):
    return s == s[::-1]
```

In `my_package/__init__.py`:

```python
from .utils import reverse_string, is_palindrome

__version__ = "1.0.0"
```

In `setup.py`:

```python
from setuptools import setup

setup(
    name="my_package",
    version="1.0.0",
    description="A simple utility package",
    packages=["my_package"],
)
```

Install locally:

```bash
pip install -e .
```

Use it:

```python
import my_package

print(my_package.reverse_string("Hello"))      # olleH
print(my_package.is_palindrome("level"))       # True
```

---

## Project 2: Data Analysis with Pandas

```bash
pip install pandas openpyxl
```

Create `analyze_sales.py`:

```python
import pandas as pd

# Read data
df = pd.read_csv('sales.csv')

print("Sales Data:")
print(df.head())

# Basic statistics
print(f"\nTotal Sales: ${df['amount'].sum():.2f}")
print(f"Average Sale: ${df['amount'].mean():.2f}")
print(f"Max Sale: ${df['amount'].max():.2f}")

# Group by product
sales_by_product = df.groupby('product')['amount'].sum()
print(f"\nSales by Product:\n{sales_by_product}")

# Filter
high_value = df[df['amount'] > 100]
print(f"\nHigh Value Transactions:\n{high_value}")
```

---

## Best Practices

### 1. Always Use Virtual Environments

```bash
# Good
python -m venv venv
source venv/bin/activate

# Bad
pip install package_name (global)
```

### 2. Keep requirements.txt Updated

```bash
pip freeze > requirements.txt
```

### 3. Use `.gitignore` for Version Control

```
venv/
__pycache__/
*.pyc
.DS_Store
```

### 4. Document Your Environment

```txt
# requirements.txt
requests==2.28.0
numpy==1.23.0
pandas==1.4.0
```

---

## Exercises

### Exercise 1: Virtual Environment Setup

```bash
# Create and activate
python -m venv test_env

# Windows:
test_env\Scripts\Activate.ps1

# Mac/Linux:
source test_env/bin/activate

# Verify
python --version
pip list
```

### Exercise 2: Install External Packages

```bash
# Activate environment first!
pip install requests

# Create test.py
import requests
response = requests.get('https://api.github.com')
print(response.status_code)
```

### Exercise 3: Create requirements.txt

```bash
pip install numpy pandas matplotlib

pip freeze > requirements.txt

# Show file contents
cat requirements.txt
```

### Exercise 4: Use Pandas

```bash
pip install pandas
```

Create `data_test.py`:

```python
import pandas as pd

data = {
    'Name': ['Alice', 'Bob', 'Charlie'],
    'Age': [25, 30, 35],
    'Salary': [50000, 60000, 70000]
}

df = pd.DataFrame(data)
print(df)
print(df.describe())
```

---

## Common Issues

### Issue: `No module named 'package'`

```
# Solution: Activate virtual environment first!
python -m venv venv
source venv/bin/activate
pip install package_name
```

### Issue: `pip: command not found`

```
# Solution: Make sure venv is activated
source venv/bin/activate  # Mac/Linux
venv\Scripts\Activate.ps1 # Windows
```

### Issue: Incompatible Versions

```bash
# Solution: Check versions
pip show package_name

# Install specific version
pip install package_name==1.23.0
```

---

## Key Takeaways

✓ Virtual environments isolate project dependencies  
✓ Use `python -m venv venv` to create  
✓ Activate before installing packages  
✓ `pip` is Python package manager  
✓ `pip freeze > requirements.txt` exports dependencies  
✓ External libraries extend Python functionality  
✓ Popular: requests, numpy, pandas, matplotlib  

---

## Quick Reference

```bash
# Virtual Environment
python -m venv venv
source venv/bin/activate  # Mac/Linux
venv\Scripts\Activate.ps1 # Windows

# Pip Commands
pip install package_name
pip list
pip freeze > requirements.txt
pip install -r requirements.txt
pip uninstall package_name

# Popular Packages
requests             # HTTP
numpy                # Numbers
pandas               # Data
matplotlib           # Plots
flask                # Web
pytest               # Tests
```

---

## Homework

1. ✓ Create a virtual environment and activate it
2. ✓ Install 3 external packages
3. ✓ Create requirements.txt with those packages
4. ✓ Use one external package (requests, numpy, etc.)

Next hour: **Final Capstone Project!**
