## 📘 Chapter 10: Dictionaries

### 10.1. Introduction: Dictionaries

#### 10.1.1. Learning Goals

- Understand what dictionaries are and how they differ from other data structures.
- Learn how to create, modify, and access data in dictionaries.
- Master dictionary operations and advanced patterns such as accumulation.
- Learn when and why dictionaries should be used in real-world scenarios.

#### 10.1.2. Objectives

- Define dictionaries and identify key-value pairs.
- Perform insertions, deletions, updates, and lookups.
- Use dictionary methods to manipulate and traverse data.
- Implement accumulation and aggregation tasks using dictionaries.
- Understand dictionary copying and aliasing behavior.

---

### 10.2. Getting Started with Dictionaries

Dictionaries in Python are **unordered collections** of data values used to store data in **key:value** pairs.

```python
# Basic dictionary
student = {"name": "Aman", "age": 22, "courses": ["Math", "CompSci"]}
```

- Keys are **unique** and must be **immutable** (str, int, tuple).
- Values can be any type.

Accessing elements:

```python
print(student["name"])         # Aman
print(student.get("age"))      # 22
print(student.get("grade", "N/A"))  # N/A (default)
```

---

### 10.3. Dictionary Operations

- **Accessing**: `dict[key]` or `dict.get(key)`
- **Adding/Updating**: `dict[key] = value`
- **Deleting**: `del dict[key]` or `dict.pop(key)`
- **Membership Test**: `'key' in dict`
- **Length**: `len(dict)`

```python
student["grade"] = "A"      # Add new key
del student["courses"]      # Delete key
```

---

### 10.4. Dictionary Methods

- `dict.keys()`
- `dict.values()`
- `dict.items()`
- `dict.pop(key)`
- `dict.popitem()`
- `dict.update(other_dict)`
- `dict.clear()`

#### 10.4.1. Iterating over Dictionaries

```python
for key, value in student.items():
    print(f"{key}: {value}")
```

#### 10.4.2. Safely Retrieving Values

Use `get()` to avoid `KeyError`.

```python
email = student.get("email", "Not Found")
```

---

### 10.5. Aliasing and Copying

```python
a = {"x": 1, "y": 2}
b = a              # aliasing, both refer to same object
c = a.copy()       # shallow copy

a["x"] = 99
print(b["x"])      # 99 (since b is alias)
print(c["x"])      # 1 (copy is unaffected)
```

Deep copies for nested structures:

```python
import copy
deep_copy = copy.deepcopy(nested_dict)
```

---

### 10.6. Accumulating Multiple Results in a Dictionary

Use `dict.setdefault()` or `collections.defaultdict()`.

```python
from collections import defaultdict

scores = defaultdict(list)
scores["Math"].append(90)
scores["Math"].append(85)
print(scores)  # {'Math': [90, 85]}
```

---

### 10.7. Accumulating Results from a Dictionary

Example: Counting word occurrences.

```python
text = "to be or not to be"
counts = {}

for word in text.split():
    counts[word] = counts.get(word, 0) + 1

print(counts)  # {'to': 2, 'be': 2, 'or': 1, 'not': 1}
```

---

### 10.8. Accumulating the Best Key

Find the key with the maximum value.

```python
grades = {'Alice': 91, 'Bob': 85, 'Charlie': 99}
top_student = max(grades, key=grades.get)
print(top_student)  # Charlie
```

---

### 10.9. 👩💻 When to Use a Dictionary

Use dictionaries when:

- Fast lookups and updates are needed.
- Data is best represented as key-value pairs.
- Frequency counting or grouping is required.
- Order of insertion matters (Python 3.7+ maintains order).

---

## 💡 Advanced Assignment: Mastering Dictionaries

### 🧠 **Level: Hard**

#### **Q1. Nested Aggregation**

Write a function that takes a list of tuples, each containing (department, employee, salary), and returns a dictionary with departments as keys and a list of (employee, salary) sorted by salary descending.

```python
data = [
    ('HR', 'Alice', 50000),
    ('HR', 'Bob', 60000),
    ('Tech', 'Charlie', 120000),
    ('Tech', 'Dave', 110000),
    ('Tech', 'Eve', 115000)
]
```

Expected output:

```python
{
    'HR': [('Bob', 60000), ('Alice', 50000)],
    'Tech': [('Charlie', 120000), ('Eve', 115000), ('Dave', 110000)]
}
```

```python
def aggregate_by_department(data):
    department_dict = {}
    
    # Group by department
    for department, employee, salary in data:
        if department not in department_dict:
            department_dict[department] = []
        department_dict[department].append((employee, salary))
    
    # Sort each department by salary in descending order
    for department in department_dict:
        department_dict[department].sort(key=lambda x: x[1], reverse=True)
    
    return department_dict

# Test data
data = [
    ('HR', 'Alice', 50000),
    ('HR', 'Bob', 60000),
    ('Tech', 'Charlie', 120000),
    ('Tech', 'Dave', 110000),
    ('Tech', 'Eve', 115000)
]

result = aggregate_by_department(data)
print(result)
```

---

#### **Q2. Inverted Index**

Create a dictionary from a list of sentences that maps each word to the indices of the sentences it appears in.

```python
sentences = ["the quick brown fox", "jumps over the lazy dog", "the dog barked"]
```

Expected output:

```python
{
    'the': [0, 1, 2],
    'quick': [0],
    'dog': [1, 2],
    ...
}
```

```python
def inverted_index(sentences):
    word_index = {}
    
    for index, sentence in enumerate(sentences):
        for word in sentence.split():
            if word not in word_index:
                word_index[word] = []
            word_index[word].append(index)
    
    return word_index

# Test data
sentences = ["the quick brown fox", "jumps over the lazy dog", "the dog barked"]

result = inverted_index(sentences)
print(result)
```

---

#### **Q3. Deep Copy Trap**

Demonstrate a scenario where using `dict.copy()` fails due to nested structures. Show how `deepcopy` fixes it.

---
```python
import copy

# Example of shallow copy failure
nested_dict = {"employees": [{"name": "Alice", "age": 30}, {"name": "Bob", "age": 25}]}
shallow_copy = nested_dict.copy()

# Modify original nested data
nested_dict["employees"][0]["age"] = 35

# The shallow copy still references the same data
print("Original:", nested_dict)
print("Shallow Copy:", shallow_copy)

# Deep copy example
deep_copy = copy.deepcopy(nested_dict)
nested_dict["employees"][0]["age"] = 40

print("Original:", nested_dict)
print("Deep Copy:", deep_copy)
```
#### **Q4. Accumulate Word Lengths**

Write a program that takes a list of words and creates a dictionary where the key is the length of the word, and the value is a list of words of that length.

```python
words = ["hi", "hello", "hey", "bye", "thanks", "ok"]
```

Expected output:

```python
{2: ['hi', 'ok'], 5: ['hello', 'thanks'], 3: ['hey', 'bye']}
```
```python
def accumulate_word_lengths(words):
    length_dict = {}
    
    for word in words:
        word_length = len(word)
        if word_length not in length_dict:
            length_dict[word_length] = []
        length_dict[word_length].append(word)
    
    return length_dict

# Test data
words = ["hi", "hello", "hey", "bye", "thanks", "ok"]

result = accumulate_word_lengths(words)
print(result)
```

---

#### **Q5. Dictionary Merge with Conflict Resolution**

Given two dictionaries, merge them such that:

- If keys are unique, include both.
- If keys conflict, take the larger value.

```python
d1 = {'a': 5, 'b': 10}
d2 = {'b': 7, 'c': 3}

# Output: {'a': 5, 'b': 10, 'c': 3}
```
```python
def merge_dicts(d1, d2):
    merged = d1.copy()  # Start with a copy of the first dictionary
    for key, value in d2.items():
        if key in merged:
            merged[key] = max(merged[key], value)  # Take the larger value
        else:
            merged[key] = value
    return merged

# Test data
d1 = {'a': 5, 'b': 10}
d2 = {'b': 7, 'c': 3}

result = merge_dicts(d1, d2)
print(result)
```
---
