---
## 📘 11.1 Introduction to Functions

### 11.1.1 Topics:
- What is a function?
- Importance of functions
- Types of functions (built-in vs user-defined)
- Modularity and code reuse

### 11.1.2 Learning Objectives:
- Understand how functions enhance code structure and readability.
- Define and invoke functions.
- Differentiate between returning and printing in a function.
---

## 🧱 11.2 Function Definition

### Notes:

```python
def greet():
    print("Hello, world!")
```

- `def` keyword starts function definition.
- `greet()` is the function name.
- `()` encloses optional parameters.

### 🔍 Key Points:

- The body is indented.
- Function definitions do not execute until called.

---

## 🚀 11.3 Function Invocation

### Notes:

```python
greet()
```

- This executes the function body.
- A function can be called multiple times.

---

## 🎯 11.4 Function Parameters

### Notes:

```python
def greet(name):
    print("Hello", name)
greet("Alice")
```

- Parameters are placeholders for input.
- Arguments are actual values passed.

---

## 🎁 11.5 Returning a Value from a Function

### Notes:

```python
def add(x, y):
    return x + y
result = add(3, 4)
```

- `return` sends a value back to the caller.
- Use the result further in your code.

---

## 👩‍💻 11.6 Decoding a Function

### Practice:

Break down and explain:

```python
def mystery(a, b):
    c = a * b
    print("Sum is", a + b)
    return c
```

---

## 📏 11.7 Type Annotations

### Notes:

```python
def add(x: int, y: int) -> int:
    return x + y
```

- Helps with readability and debugging.
- Not enforced at runtime.

---

## 🧮 11.8 A Function That Accumulates

### Notes:

```python
def accumulate(numbers):
    total = 0
    for num in numbers:
        total += num
    return total
```

- Used in summation, averages, etc.

---

## 🎯 11.9 Variables and Parameters are Local

### Notes:

```python
def func(x):
    x = x + 1
    print(x)

x = 10
func(x)
print(x)  # Still 10
```

- Variables inside functions are local unless declared global.

---

## 🌍 11.10 Global Variables

### Notes:

```python
count = 0
def increment():
    global count
    count += 1
```

- Use `global` to modify global variables inside a function.

---

## 🔁 11.11 Functions Can Call Other Functions (Composition)

### Notes:

```python
def square(x):
    return x * x

def sum_of_squares(a, b):
    return square(a) + square(b)
```

- Break large problems into smaller, reusable parts.

---

## 🧭 11.12 Flow of Execution Summary

### Key Ideas:

- Python reads from top to bottom.
- Function body executes **only** when called.
- Each function call starts a new local scope.

---

## 👩‍💻 11.13 Print vs Return

### Notes:

- `print()` outputs to console, used for user-facing messages.
- `return` sends data back to the caller.

```python
def f():
    print("Hi")  # Side effect

def g():
    return "Hi"  # Pure function
```

---

## 🔄 11.14 Passing Mutable Objects

### Notes:

```python
def modify_list(lst):
    lst.append(10)

my_list = [1, 2]
modify_list(my_list)
print(my_list)  # [1, 2, 10]
```

- Mutable objects (lists, dicts) can be changed inside functions.

---

## 💥 11.15 Side Effects

### Notes:

- Any modification of external state (printing, modifying global or mutable objects) is a side effect.

---

# 📘 In-depth Assignments

---

## 🧠 Level 1 – Basic Understanding

> Focus: Syntax, simple usage, function calls, return values

1. **Create a function `welcome()` that prints "Welcome to Python!" and call it three times.**
```python
def welcome():
    print("Welcome to Python!")

for_ in range(3):
     welcome()
```
2. **Write a function `square(n)` that takes a number `n` and returns its square.**
```python
def square(n):
    return n * n

# Example usage
print(square(5))  # Output: 25
```
3. **Write a function `is_even(num)` that returns `True` if a number is even, else `False`.**
```python
def is_even(num):
    return num % 2 == 0

# Example usage
print(is_even(4))  # True
print(is_even(7))  # False
```
4. **Define a function `full_name(first, last)` that returns the full name as a string.**
```python
def full_name(first, last):
    return first + " " + last

# Example usage
print(full_name("Alice", "Johnson"))  # Output: Alice Johnson
```
5. **Create a function `circle_area(radius)` that returns the area of a circle using `πr²`. Use `pi = 3.14`.**
```python
def circle_area(radius):
    pi = 3.14
    return pi * radius * radius

# Example usage
print(circle_area(5))  # Output: 78.5
```
---

## ⚙️ Level 2 – Intermediate Skills

> Focus: Parameters, return, iteration, conditionals, type annotations

1. **Define a function `sum_even(numbers: list[int]) -> int` that returns the sum of all even numbers in a list.**
```python
def sum_even(numbers: list[int]) -> int:
    return sum(num for num in numbers if num % 2 == 0)

# Example
print(sum_even([1, 2, 3, 4, 5, 6]))  # Output: 12
```
2. **Write a function `reverse_string(s: str) -> str` to return the reverse of a string.**
```python
def reverse_string(s: str) -> str:
    return s[::-1]

# Example
print(reverse_string("hello"))  # Output: "olleh"
```
3. **Create a function `fibonacci(n: int) -> list[int]` that returns the first `n` Fibonacci numbers.**
```python
def fibonacci(n: int) -> list[int]:
    fib = []
    a, b = 0, 1
    for _ in range(n):
        fib.append(a)
        a, b = b, a + b
    return fib

# Example
print(fibonacci(6))  # Output: [0, 1, 1, 2, 3, 5]
```
4. **Write a function `count_vowels(sentence: str) -> int` that counts and returns the number of vowels.**
```python
def count_vowels(sentence: str) -> int:
    vowels = "aeiouAEIOU"
    return sum(1 for char in sentence if char in vowels)

# Example
print(count_vowels("Python is awesome"))  # Output: 6
```
5. **Write a function `average_marks(marks: list[float]) -> float` that returns the average of marks.**
```python
def average_marks(marks: list[float]) -> float:
    if not marks:
        return 0.0
    return sum(marks) / len(marks)

# Example
print(average_marks([85.5, 90.0, 78.0]))  # Output: 84.5
```

---

## 🔬 Level 3 – Advanced Practice

> Focus: Function composition, scope, mutation, edge cases, pure vs impure functions

1. **Create a function `analyze_text(text: str)` that returns:**

   - Number of words
   - Number of unique words
   - Frequency of each word

```python
def analyze_text(text: str) -> dict:
    words = text.lower().split()
    word_count = len(words)
    unique_words = set(words)
    frequency = {}

    for word in words:
        frequency[word] = frequency.get(word, 0) + 1

    return {
        "word_count": word_count,
        "unique_word_count": len(unique_words),
        "frequency": frequency
    }

# Example
result = analyze_text("This is a test. This test is fun.")
print(result)
```

2. **Write a function `is_palindrome(s: str) -> bool` that checks if the input string is a palindrome. Ignore cases and spaces.**
```python
def is_palindrome(s: str) -> bool:
    cleaned = ''.join(c.lower() for c in s if c.isalnum())
    return cleaned == cleaned[::-1]

# Example
print(is_palindrome("A man a plan a canal Panama"))  # Output: True
```

3. **Implement `nested_sum(data: list) -> int` that takes a nested list of integers and returns the sum of all integers.**

   ```python
   nested_sum([[1, 2], [3, [4, 5]], 6])  # Output: 21
   ```
```python
def nested_sum(data: list) -> int:
    total = 0
    for item in data:
        if isinstance(item, list):
            total += nested_sum(item)
        else:
            total += item
    return total

# Example
print(nested_sum([[1, 2], [3, [4, 5]], 6]))  # Output: 21
```

4. **Create a function `safe_divide(x: float, y: float) -> float` that handles divide-by-zero using try-except.**
```python
def safe_divide(x: float, y: float) -> float:
    try:
        return x / y
    except ZeroDivisionError:
        return float('inf')  # or return 0.0 or custom message

# Example
print(safe_divide(10, 2))  # Output: 5.0
print(safe_divide(10, 0))  # Output: inf
```
5. **Simulate a digital clock with a function `time_increment(h: int, m: int) -> tuple[int, int]` that returns the time after 1 minute. Handle boundary cases (e.g., 23:59).**
```python
def time_increment(h: int, m: int) -> tuple[int, int]:
    m += 1
    if m == 60:
        m = 0
        h += 1
    if h == 24:
        h = 0
    return h, m

# Example
print(time_increment(23, 59))  # Output: (0, 0)
print(time_increment(12, 5))   # Output: (12, 6)
```
---

## 💻 Real-world Problem Set: Function Design and Architecture

> Focus: Realistic situations, reusable function design, side effects, mutable arguments

### **Personal Expense Tracker**

1. Create the following functions:

   - `add_expense(expenses: list[float], amount: float) -> None`
   - `total_expense(expenses: list[float]) -> float`
   - `highest_expense(expenses: list[float]) -> float`
   - `average_expense(expenses: list[float]) -> float`
   - `expense_summary(expenses: list[float]) -> dict[str, float]`

2. Use `global` variable to maintain a transaction count across functions.

3. Add a function `print_report()` that **prints** the entire summary — this demonstrates **side effects vs return**.

4. Apply **function composition** to build `generate_report()` that internally calls the above functions.
```python
transaction_count = 0  # Global variable

def add_expense(expenses: list[float], amount: float) -> None:
    global transaction_count
    expenses.append(amount)
    transaction_count += 1

def total_expense(expenses: list[float]) -> float:
    return sum(expenses)

def highest_expense(expenses: list[float]) -> float:
    return max(expenses) if expenses else 0.0

def average_expense(expenses: list[float]) -> float:
    return sum(expenses) / len(expenses) if expenses else 0.0

def expense_summary(expenses: list[float]) -> dict[str, float]:
    return {
        "total": total_expense(expenses),
        "highest": highest_expense(expenses),
        "average": average_expense(expenses),
        "transactions": transaction_count
    }

def print_report(expenses: list[float]) -> None:
    summary = expense_summary(expenses)
    print("Expense Report:")
    for key, value in summary.items():
        print(f"{key.capitalize()}: {value}")

def generate_report(expenses: list[float]) -> None:
    print_report(expenses)
```
---

## 🧠 Conceptual Questions (Code + Theory)

1. **What is the difference between returning a value and printing it? Illustrate with two functions.**
```python
def print_name():
    print("Alice")  # Only prints, can't reuse

def return_name():
    return "Alice"  # Can be stored or manipulated
```
2. **Explain with code how passing a mutable object (like a list) affects the original outside the function.**
```python
def add_item(lst):
    lst.append(10)

nums = [1, 2]
add_item(nums)
print(nums)  # [1, 2, 10] – Original list changed
```
3. **Write a function where a global variable is modified and explain the risks involved.**
```python
counter = 0

def increment():
    global counter
    counter += 1

# Risk: unexpected side effects across the codebase
```
4. **Demonstrate function composition by creating a calculator that computes `sqrt(x² + y²)` using helper functions.**
```python
import math

def square(x):
    return x * x

def hypotenuse(a, b):
    return math.sqrt(square(a) + square(b))
```
5. **Create an example where misunderstanding local scope causes a logic bug. Fix it using correct scoping.**
```python
def buggy():
    x = 10

def fixed():
    global x
    x = 10

buggy()
# print(x)  # Error
fixed()
print(x)  # 10
```
---

## 🌐 Bonus: Mini Challenges

1. **Write a recursive function to compute factorial of a number.**
```python
def factorial(n: int) -> int:
    return 1 if n == 0 else n * factorial(n - 1)
```
2. **Create a function that accepts variable number of arguments and returns their sum.**
```python
def sum_all(*args: float) -> float:
    return sum(args)
```
3. **Build a mock `login()` function that checks a username and password from a predefined list of users.**
```python
users = {"alice": "pass123", "bob": "qwerty"}

def login(username: str, password: str) -> bool:
    return users.get(username) == password
```
4. **Write a function `flatten_list(nested: list) -> list` that flattens a nested list of any depth.**
```python
def flatten_list(nested: list) -> list:
    flat = []
    for item in nested:
        if isinstance(item, list):
            flat.extend(flatten_list(item))
        else:
            flat.append(item)
    return flat
```
5. **Use function annotations and docstrings to fully document a `bmi(weight: float, height: float) -> float` calculator.**
```python
def bmi(weight: float, height: float) -> float:
    """Calculate BMI given weight (kg) and height (m)."""
    return weight / (height ** 2)
```
---
