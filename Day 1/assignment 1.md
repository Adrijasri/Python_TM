# Advanced Python Assignment: Variables, Statements, and Expressions

## 1. Advanced Data Types and Type Conversion

### Challenge:

- Create a Python program that accepts user inputs of different types (integer, float, string, boolean) and dynamically stores them in a dictionary.
- Implement type-checking logic to ensure that inputs are stored as the correct data type.
- Write a function `convert_and_calculate` that converts all numeric values to floats and calculates their sum.

```python
def get_user_input():
    
    data = {
        "integer": int(input("Enter an integer: ") or 0),
        "float": float(input("Enter a float: ") or 0.0),
        "string": input("Enter a string: ") or "",
        "boolean": input("Enter a boolean (true/false): ").strip().lower() in ["true", "1", "yes"]
    }

    return data

def convert_and_calculate(data):
    return sum([float(value) for value in data.values() if isinstance(value, (int, float))])

user_data = get_user_input()
print("\nStored Data:", user_data)

numeric_sum = convert_and_calculate(user_data)
print("Sum of numeric values:", numeric_sum)

```
### prerequisite:

Dictionary, list comprehension

## 2. Complex Expressions and Order of Operations

### Challenge:

- Write a Python function `evaluate_expression` that accepts a string representing a mathematical expression and evaluates it.
- The function should handle parentheses, exponentiation, and mixed operators.
- Implement error handling to manage invalid expressions.

```python
def evaluate_expression(expression):
    try:
        result = eval(expression, {"__builtins__": {}}, {})
        return result
    except ZeroDivisionError:
        return "Error: Division by zero is not allowed."
    except (SyntaxError, NameError, TypeError):
        return "Error: Invalid mathematical expression."

expressions = [
    "5 + 3 * 2",        # 11
    "(10 + 5) / 3",     # 5.0
    "2 ** 3",           # 8
    "100 / (5 - 5)",    # Error: Division by zero
    "10 + abc",         # Error: Invalid expression
    "5 * (2 + 3))"      # Error: Syntax error
]

for expr in expressions:
    print(f"Expression: {expr} → Result: {evaluate_expression(expr)}")
```

### prerequisite:

eval function

## 3. Dynamic Variable Management

### Challenge:

- Create a program where the user can dynamically create variables with names and values entered as inputs.
- Store these variables in a dictionary, and allow the user to update any variable by providing its name and a new value.

```python
def create_variables():
    variables = {}
    while (name := input("Enter variable name (or 'done' to finish): ").strip().lower()) != "done":
        value = input(f"Enter value for '{name}': ").strip()
        variables[name] = int(value) if value.isdigit() else (float(value) if value.replace('.', '', 1).isdigit() else value)
    return variables

def update_variable(variables):
    if (name := input("Enter variable name to update: ").strip()) in variables:
        value = input(f"Enter new value for '{name}': ").strip()
        variables[name] = int(value) if value.isdigit() else (float(value) if value.replace('.', '', 1).isdigit() else value)
        print(f"Updated '{name}' to {variables[name]}")
    else:
        print("Variable not found!")

user_variables = create_variables()
print("\nStored Variables:", user_variables)

while input("\nUpdate a variable? (yes/no): ").strip().lower() == "yes":
    update_variable(user_variables)
    print("\nUpdated Variables:", user_variables)

print("Final Variables:", user_variables)
```
### prerequisite:

Dictionary

## 4. Advanced Function Calls and Nested Expressions

### Challenge:

- Implement a function `nested_function_call` that accepts a list of numbers and returns the result of `max(numbers) - min(numbers) + sum(numbers)`.
- Avoid using loops; rely solely on built-in functions and expressions.
```python
def nested_function_call(numbers):
    return max(numbers) - min(numbers) + sum(numbers) if numbers else 0
numbers = [10, 20, 5, 8]
result = nested_function_call(numbers)
print("Result:", result)
```

## 5. Reassignment and Updating Variables

### Challenge:

- Create a simulation where a variable `balance` starts at 1000.
- Simulate daily transactions, updating the balance accordingly.
- Print the balance after each transaction.

```python
import random

def simulate_transactions(days=7):
    balance = 1000  

    for day in range(1, days + 1):
        transaction = random.randint(-200, 200) 
        balance += transaction
        print(f"Day {day}: Transaction {transaction}, New Balance: {balance}")

simulate_transactions(7) 
```

### Example

balance = 1000
transactions = [100, -50, 200, -75]

## 6. Investigating Memory Allocation

### Challenge:

- Write a program that compares the memory addresses of variables before and after reassignment.
- Use the `id()` function to inspect the memory addresses.

```python
def compare_memory():
    x = 42
    print(f"Before reassignment: x = {x}, Memory Address: {id(x)}")

    x = 99  
    print(f"After reassignment: x = {x}, Memory Address: {id(x)}")

    y = [1, 2, 3]
    print(f"\nBefore modifying list: y = {y}, Memory Address: {id(y)}")

    y.append(4)
    print(f"After modifying list: y = {y}, Memory Address: {id(y)}")

compare_memory()
```