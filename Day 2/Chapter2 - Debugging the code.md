# Advanced Debugging: Notes and Assignment

## 3.1. Introduction to Debugging

### 3.1.1. Learning Goals

By the end of this module, students should be able to:

- Understand the significance of debugging in the software development lifecycle.
- Identify common types of programming errors.
- Apply various debugging techniques to isolate and fix bugs.
- Utilize debugging tools effectively.

### 3.1.2. Objectives

- Grasp the real-world importance of debugging.
- Learn strategies to prevent bugs.
- Master the use of debugging tools and techniques.
- Practice advanced problem-solving skills.

---

## 3.2. Programming in the Real World

In real-world programming, code rarely works perfectly on the first try. Debugging is a critical skill that involves identifying and fixing errors in code. Professional developers spend a significant portion of their time debugging and ensuring code reliability. Understanding the art of debugging can make the difference between a novice and a proficient developer.

### Common types of errors:

- **Syntax Errors:** Mistakes in the code structure (e.g., missing colons, unmatched parentheses).
- **Runtime Errors:** Errors that occur while the program is running (e.g., division by zero).
- **Logic Errors:** The program runs without crashing but produces incorrect results.

### Debugging often involves:

1. Reproducing the error.
2. Isolating the problematic code.
3. Fixing the bug.
4. Testing thoroughly to ensure the fix is correct and doesn’t introduce new issues.

#### Additional Reading:

- [Python Official Debugging Guide](https://docs.python.org/3/library/pdb.html)
- [Real Python Debugging Tutorial](https://realpython.com/python-debugging-pdb/)
- [Effective Debugging Techniques](https://hackernoon.com/10-ways-to-debug-your-code-faster-33d91b55592c)

---

## 3.3. Debugging

### 3.3.1. How to Avoid Debugging

While debugging is inevitable, writing clean and predictable code reduces the chances of bugs. Here are strategies to minimize bugs:

- **Write Clear Code:** Use meaningful variable names and write self-explanatory functions.
- **Test Incrementally:** Test your code step-by-step rather than writing everything at once.
- **Use Assertions:** Assertions help catch unexpected states early.
- **Version Control:** Commit working code often, so you can easily revert to a stable state.
- **Peer Reviews:** Having another person review your code can uncover issues you might have missed.

### Tools and Techniques:

- **Print Statements:** Insert print statements to trace variable values.
- **Debuggers:** Use tools like Python's built-in `pdb` or IDE-integrated debuggers.
- **Logging:** Implement logging to track the flow of execution and catch unexpected behaviors.
- **Rubber Duck Debugging:** Explain your code to someone (or an inanimate object) to uncover mistakes.

### Pro Tips:

- Break down problems into smaller chunks.
- Focus on one bug at a time.
- Write test cases for critical parts of your code.
- Avoid making multiple changes at once while debugging.

---

### Understanding Try-Except (Try-Catch)

The `try` and `except` blocks in Python help handle exceptions gracefully, ensuring the program doesn’t crash unexpectedly.

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
```

#### Steps to Use Try-Except:

1. Identify the code that might raise an exception.
2. Wrap the risky code inside a `try` block.
3. Use `except` to handle specific exceptions.
4. Optionally add `else` for code that runs if no exceptions occur and `finally` for cleanup actions.

#### Learn More:

- [Python Exceptions Documentation](https://docs.python.org/3/tutorial/errors.html)
- [Real Python Try-Except Guide](https://realpython.com/python-exceptions/)

---

## Advanced Debugging Assignment

### 1. Error Classification

Identify the type of error in the following code snippets and fix them:

```python
# a) Syntax Error
for i in range(5)
    print(i)

# b) Runtime Error
x = 10 / 0

# c) Logic Error
def calculate_area(radius):
    return 2 * 3.14 * radius  # Incorrect formula for area
```

### 2. Debugging Complex Functions

Debug the following function and correct the mistakes:

```python
def process_data(data):
    total = 0
    for item in data:
        total += int(item)  # This may throw an error if item is not convertible to int
    return total / len(data)  # Handle division by zero error

print(process_data(['10', '20', 'abc', '30']))
```

### 3. Advanced Debugging Challenge

You’re given a function that fails intermittently. Investigate the bug and fix it:

```python
import random

def unreliable_function():
    number = random.choice([0, 1, 2])
    return 10 / number

for i in range(10):
    print(unreliable_function())
```

### 4. Writing Debug-Friendly Code

Refactor the following function to improve readability and add error handling:

```python
def calculate_discount(price, discount):
    return price - (price * discount / 100)

print(calculate_discount(100, '10%'))
```

### 5. Rubber Duck Debugging

Explain the following code snippet step-by-step as if you’re teaching someone unfamiliar with coding:

```python
numbers = [1, 2, 3, 4, 5]
result = 1
for num in numbers:
    result *= num
print("Product:", result)
```

### 6. Advanced Challenge: Debug a Multi-threaded Program

Fix the race condition in the following code:

```python
import threading

counter = 0
def increment():
    global counter
    for _ in range(100000):
        counter += 1

threads = [threading.Thread(target=increment) for _ in range(2)]
for t in threads:
    t.start()
for t in threads:
    t.join()

print("Counter:", counter)  # Expected: 200000
```

### 7. Activity: Debug with Breakpoints

Learn to use breakpoints in your IDE (e.g., VSCode, PyCharm) to inspect variable states step-by-step.

**Steps:**

1. Open your IDE and load the following code:

```python
def divide(a, b):
    result = a / b
    return result

a = 10
b = 0
print(divide(a, b))
```

2. Set a breakpoint at the line where `result` is calculated.
3. Run the code in debug mode.
4. Inspect the values of `a` and `b` before the division.
5. Step through the code to observe the flow of execution.
6. Fix the division by zero error and re-run the code.

#### Learn More:

- [VSCode Debugging Guide](https://code.visualstudio.com/docs/editor/debugging)
- [PyCharm Debugger](https://www.jetbrains.com/help/pycharm/debugging-your-first-python-application.html)

### 8. Memory Leaks and Performance Debugging

Optimize the following code and fix potential memory leaks:

```python
import time

def inefficient_function():
    result = []
    for i in range(100000):
        result.append(i * 2)
    time.sleep(2)
    return result

print(len(inefficient_function()))
```

---

## Submission Guidelines:

- Submit a Python file containing your solutions.
- Include comments explaining each fix.
- Add a README file summarizing the challenges you faced and how you solved them.

Happy Debugging! 🐞
