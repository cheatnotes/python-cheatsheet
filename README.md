# Python Comprehensive Cheatsheet

> **Complete reference covering syntax, data structures, control flow, functions, OOP, file I/O, exceptions, decorators, generators, lambdas, regex, datetime, and common libraries (NumPy, Pandas). Ideal for beginners and pros. Quick lookup with table of contents.**

## Table of Contents

1. [Basic Syntax & Operators](#1-basic-syntax--operators)
2. [Data Types & Structures](#2-data-types--structures)
3. [Control Flow](#3-control-flow)
4. [Functions](#4-functions)
5. [Modules & Packages](#5-modules--packages)
6. [File Handling](#6-file-handling)
7. [Error & Exception Handling](#7-error--exception-handling)
8. [Object-Oriented Programming (OOP)](#8-object-oriented-programming-oop)
9. [List Comprehensions & Generators](#9-list-comprehensions--generators)
10. [Lambda & Functional Tools](#10-lambda--functional-tools)
11. [Decorators](#11-decorators)
12. [Working with Dates & Times](#12-working-with-dates--times)
13. [Regular Expressions](#13-regular-expressions)
14. [Common Built-in Functions](#14-common-built-in-functions)
15. [Useful Libraries (Quick Start)](#15-useful-libraries-quick-start)

---

## 1. Basic Syntax & Operators

```python
# Single-line comment
""" Multi-line
    comment """

# Printing output
print("Hello", "World", sep="-", end="!\n")   # Hello-World!

# Taking input
name = input("Enter name: ")   # always returns string
age = int(input("Enter age: "))  # type conversion

# Variables (dynamic typing, snake_case convention)
x = 10          # int
pi = 3.14       # float
is_valid = True # bool (True/False)
message = "Hi"  # str

# Type checking
type(x)         # <class 'int'>
isinstance(x, int)  # True

# Arithmetic: + - * / % // **
5 / 2    # 2.5 (float division)
5 // 2   # 2 (integer division)
5 ** 2   # 25 (exponent)

# Comparison: == != < > <= >=
# Logical: and, or, not
# Assignment: = += -= *= /= //= %= **=
```

---

## 2. Data Types & Structures

### Strings
```python
s = "python"
s[0]          # 'p' (indexing)
s[-1]         # 'n'
s[1:4]        # 'yth' (slicing start:stop:step)
s[::-1]       # 'nohtyp' (reverse)

# Methods
s.upper()       # 'PYTHON'
s.lower()       
s.capitalize()
s.title()
s.strip()       # remove whitespace
s.replace("py", "PY")
s.split(",")    # list from string
",".join(["a","b"])  # 'a,b'
f"Value = {x}"  # f-string formatting
"Value = {}".format(x)
```

### Lists (mutable, ordered)
```python
lst = [1, 2, 3]
lst.append(4)          # [1,2,3,4]
lst.extend([5,6])      # [1,2,3,4,5,6]
lst.insert(0, 0)       # [0,1,2,3,...]
lst.pop()              # removes last, returns it
lst.pop(2)             # remove index 2
lst.remove(3)          # remove first 3
lst.index(2)           # first index of 2
lst.sort()             # in-place sort
sorted(lst)            # returns new sorted list
lst.reverse()
len(lst)
del lst[2]             # delete by index
```

### Tuples (immutable, ordered)
```python
t = (1, 2, 3)
t = 1, 2, 3            # packing
a, b, c = t            # unpacking
t.count(2)             # 1
t.index(2)             # 1
```

### Dictionaries (key-value, unordered until 3.7+)
```python
d = {"a": 1, "b": 2}
d["c"] = 3
d.get("x", 0)          # 0 if missing, avoids KeyError
d.keys()
d.values()
d.items()              # view of (key,value) pairs
for k, v in d.items():
    print(k, v)
d.pop("a")             # remove key 'a'
del d["b"]
```
**Dict comprehension:**
```python
{x: x**2 for x in range(5)}
```

### Sets (unique, unordered)
```python
s = {1, 2, 3}
s.add(4)
s.remove(2)
s.union({3,4})    # | operator
s.intersection({2,3})  # & operator
s.difference({3})      # - operator
```

---

## 3. Control Flow

### Conditional Statements
```python
if condition:
    pass
elif other_condition:
    pass
else:
    pass

# Ternary operator
result = "Even" if x % 2 == 0 else "Odd"
```

### Loops
```python
# While loop
while count < 5:
    print(count)
    count += 1
else:               # runs if no break occurred
    print("Loop finished normally")

# For loop over iterable
for i in range(5):      # 0,1,2,3,4
for i in range(2, 10, 2):  # 2,4,6,8
for idx, val in enumerate(lst):
for key, val in dict.items():
for item in reversed(lst):

# Loop control
break       # exit loop
continue    # skip to next iteration
pass        # placeholder, does nothing
```

---

## 4. Functions

```python
def function_name(param1, param2="default"):
    """Docstring: explains function."""
    result = param1 + param2
    return result

# Call
function_name(5, 6)

# Variable number of arguments
def func(*args):        # tuple of positional args
def func(**kwargs):     # dict of keyword args

# Example
def sum_all(*nums):
    return sum(nums)
sum_all(1,2,3,4)   # 10

def print_info(**data):
    for k,v in data.items():
        print(f"{k}: {v}")
print_info(name="Alice", age=30)

# Mixed order: standard, *args, **kwargs
def example(a, b, *args, option=True, **kwargs):
    pass

# Type hints (Python 3.5+)
def add(x: int, y: int) -> int:
    return x + y
```

---

## 5. Modules & Packages

```python
# Import a module
import math
math.sqrt(25)

# Specific import
from math import sqrt, pi
sqrt(25)

# Alias
import numpy as np

# Import everything (not recommended)
from os import *

# Your own module: save as mymodule.py
import mymodule

# Package: directory with __init__.py
from mypackage import mymodule

# Useful built-in modules: os, sys, datetime, json, re, random, math, collections, itertools, functools
```

---

## 6. File Handling

```python
# Read file
with open("file.txt", "r") as f:
    content = f.read()          # entire file
    line = f.readline()         # one line
    lines = f.readlines()       # list of lines

# Write/overwrite
with open("file.txt", "w") as f:
    f.write("Hello\n")
    f.writelines(["line1\n", "line2\n"])

# Append
with open("file.txt", "a") as f:
    f.write("append this")

# Modes: r (read), w (write, truncates), a (append), x (exclusive create), b (binary), t (text, default)
# Combine: "rb", "wb", "r+", etc.

# JSON handling
import json
data = {"name": "Alice", "age": 30}
with open("data.json", "w") as f:
    json.dump(data, f)
with open("data.json", "r") as f:
    loaded = json.load(f)
```

---

## 7. Error & Exception Handling

```python
# Basic try/except
try:
    risky_code()
except ValueError as e:
    print(f"Value error: {e}")
except (TypeError, ZeroDivisionError):
    print("Math error")
except Exception as e:   # catches any exception
    print(f"Unexpected: {e}")
else:
    print("No error occurred")
finally:
    print("Always runs (closing resources, etc.)")

# Raising exceptions
if x < 0:
    raise ValueError("x cannot be negative")

# Custom exception
class MyError(Exception):
    pass
raise MyError("Something went wrong")
```

---

## 8. Object-Oriented Programming (OOP)

```python
class Dog:
    # Class attribute
    species = "Canis familiaris"

    # Constructor
    def __init__(self, name, age):
        self.name = name   # instance attribute
        self.age = age

    # Instance method
    def bark(self):
        return f"{self.name} says woof!"

    # String representation
    def __str__(self):
        return f"{self.name}, {self.age} years old"

    def __repr__(self):
        return f"Dog('{self.name}', {self.age})"

# Inheritance
class Beagle(Dog):
    def __init__(self, name, age, color):
        super().__init__(name, age)   # call parent constructor
        self.color = color

    # Override method
    def bark(self):
        return "Arooooo!"

# Usage
my_dog = Dog("Rex", 5)
print(my_dog.bark())
print(my_dog)          # uses __str__

# Property decorator (getter/setter)
class Person:
    def __init__(self, first):
        self._first = first

    @property
    def first(self):
        return self._first.capitalize()

    @first.setter
    def first(self, value):
        self._first = value.strip()
```

---

## 9. List Comprehensions & Generators

```python
# List comprehension
squares = [x**2 for x in range(10)]                     # [0,1,4,...,81]
evens = [x for x in range(20) if x % 2 == 0]            # with condition
matrix = [[j for j in range(5)] for i in range(3)]      # nested

# Set comprehension
unique_lens = {len(word) for word in ["hi", "hello"]}

# Dict comprehension
squares_dict = {x: x**2 for x in range(5)}

# Generator expression (memory efficient, parentheses)
gen = (x**2 for x in range(1000000))
next(gen)   # get next value
for val in gen: ...

# Generator function (yield)
def fibonacci(limit):
    a, b = 0, 1
    while a < limit:
        yield a
        a, b = b, a + b
for num in fibonacci(100):
    print(num)
```

---

## 10. Lambda & Functional Tools

```python
# Lambda: anonymous function
square = lambda x: x**2
# equivalent to def square(x): return x**2

# Used with map, filter, sorted
list(map(lambda x: x*2, [1,2,3]))        # [2,4,6]
list(filter(lambda x: x > 2, [1,2,3,4])) # [3,4]
sorted([(1,2), (3,1)], key=lambda t: t[1])  # sort by second element

# functools.reduce
from functools import reduce
reduce(lambda a,b: a*b, [1,2,3,4])   # 24 (1*2*3*4)

# Partial application
from functools import partial
multiply = lambda x, y: x * y
double = partial(multiply, 2)   # fixes first argument to 2
double(5)   # 10
```

---

## 11. Decorators

```python
# Function decorator (modify/ enhance function)
def timer(func):
    import time
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        print(f"Time: {time.time()-start:.4f}s")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(1)
    return "Done"

# Decorator with arguments
def repeat(times):
    def decorator(func):
        def wrapper(*args, **kwargs):
            for _ in range(times):
                result = func(*args, **kwargs)
            return result
        return wrapper
    return decorator

@repeat(3)
def greet(name):
    print(f"Hi {name}")
```

---

## 12. Working with Dates & Times

```python
from datetime import datetime, date, time, timedelta

# Current
now = datetime.now()
today = date.today()

# Create
dt = datetime(2024, 3, 15, 14, 30)

# Format
dt.strftime("%Y-%m-%d %H:%M:%S")   # '2024-03-15 14:30:00'
dt.strftime("%A")                   # 'Friday'
# Parse string
parsed = datetime.strptime("2024-03-15", "%Y-%m-%d")

# Arithmetic
tomorrow = today + timedelta(days=1)
diff = dt2 - dt1   # timedelta object
diff.days
diff.total_seconds()
```

---

## 13. Regular Expressions

```python
import re

pattern = r"\d+"   # raw string for backslashes

# Search
match = re.search(r"\d+", "Order 42")
if match:
    print(match.group())   # '42'

# Find all
re.findall(r"\d+", "12 apples, 34 oranges")  # ['12','34']

# Split
re.split(r"\s+", "a   b  c")    # ['a','b','c']

# Replace
re.sub(r"\d+", "NUM", "Item 42")   # 'Item NUM'

# Compile for reuse
phone = re.compile(r"\d{3}-\d{3}-\d{4}")
phone.findall("Call 123-456-7890")

# Common patterns
.       # any character (except newline)
\d      # digit
\w      # word char [a-zA-Z0-9_]
\s      # whitespace
^       # start of string
$       # end of string
* + ?   # 0+, 1+, 0 or 1
{3,5}   # 3 to 5 repetitions
(a|b)   # either a or b
```

---

## 14. Common Built-in Functions

```python
len([1,2,3])         # 3
type(42)             # <class 'int'>
int("10")            # 10
str(10)              # "10"
list((1,2))          # [1,2]
tuple([1,2])         # (1,2)
dict([("a",1)])      # {'a':1}
set([1,1,2])         # {1,2}
sum([1,2,3])         # 6
max([1,5,3])         # 5
min([1,5,3])         # 1
abs(-5)              # 5
round(3.14159, 2)    # 3.14
pow(2,3)             # 8
sorted([3,1,2])      # [1,2,3]
reversed([1,2,3])    # iterator [3,2,1]
enumerate(["a","b"]) # (0,'a'), (1,'b')
zip([1,2], ["a","b"])  # (1,'a'), (2,'b')
any([True, False])   # True
all([True, True])    # True
range(5)             # 0..4
map(func, iterable)
filter(func, iterable)
help(print)          # documentation
dir(list)            # attributes/methods
```

---

## 15. Useful Libraries (Quick Start)

```python
# NumPy (arrays, math)
import numpy as np
arr = np.array([1,2,3])
arr.mean(), arr.std()
np.linspace(0, 1, 5)   # 0, 0.25, 0.5, 0.75, 1

# Pandas (data analysis)
import pandas as pd
df = pd.DataFrame({"col1": [1,2], "col2": [3,4]})
df.head(), df.describe()
df[df.col1 > 1]

# Matplotlib (plotting)
import matplotlib.pyplot as plt
plt.plot([1,2,3], [4,5,6])
plt.show()

# Random
import random
random.randint(1,10)    # integer between 1 and 10
random.random()         # float 0..1
random.choice([1,2,3])
random.sample(range(100), 5)  # 5 unique samples
random.shuffle(lst)

# OS module
import os
os.getcwd()            # current dir
os.listdir(".")
os.path.join("folder", "file.txt")
os.path.exists("file.txt")

# Sys
import sys
sys.argv               # command-line arguments
sys.exit(1)            # exit with error code
```

---

**Pro Tips:**
- Use `python -m pdb script.py` for debugging
- Virtual environment: `python -m venv venv`
- Linting: `pylint`, Formatting: `black`
- Speed up loops with local variable caching: `for i in range(n):` → assign `range_local = range` outside loop
- Use `__slots__` in classes to save memory for many instances
