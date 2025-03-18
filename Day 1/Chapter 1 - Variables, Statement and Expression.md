# Variables, Statements, and Expressions: A Learning Task

## 2.1. Introduction

### 2.1.1. Learning Goals

By the end of this task, students should be able to:

- Understand the basics of variables, expressions, and statements in Python.
- Differentiate between data types and apply type conversions.
- Properly name variables following Python conventions.
- Grasp the flow of execution through function calls and expressions.
- Update and reassign variables effectively.

### 2.1.2. Objectives

- Identify values and their data types.
- Perform operations using different operators.
- Understand function calls and their role in expressions.
- Explore Python's order of operations.
- Practice variable reassignment and updating.

---

## 2.2. Values and Data Types

1. **Research:**
   - What is a value in Python?
   Answer:
   A value in Python refers to a piece of data that can be stored in a variable or used in expressions. Every value has a specific data type that defines how it behaves in operations.
  
   ```python
   x = 10  # 10 is an integer value
   y = "Hello"  # "Hello" is a string value
   z = 3.14  # 3.14 is a float value
   ```

   - Identify different data types in Python (e.g., integers, floats, strings, booleans).
   Answer:
   Integers (int) – Whole numbers, positive or negative.
   Floats (float) – Decimal (floating-point) numbers.
   Strings (str) – Text enclosed in quotes.
   Booleans (bool) – True or False values.
   Lists (list) – Ordered, mutable collections of values.
   Tuples (tuple) – Ordered, immutable collections of values.
   Dictionaries (dict) – Key-value pairs.
   Sets (set) – Unordered collections of unique values.
   NoneType (None) – Represents absence of value.
2. **Fun Fact:**
   - Python is dynamically typed — you don’t need to declare the type of a variable when you create one.
3. **Exercise:**
   - Write a program that:
     - Assigns different values to variables.
     - Prints the type of each variable.
   - Example:
     ```python
     x = 42
     y = 3.14
     z = 'Hello'
     print(type(x), type(y), type(z))
     ```

## 2.3. Operators and Operands

1. **Research:**
   - Learn about arithmetic, comparison, and logical operators.
   Answer:
   1. Arithmetic Operators
These operators are used for mathematical calculations.

+	Addition	(5 + 3 =	8)
-	Subtraction	(10 - 4 = 6)
*	Multiplication	(6 * 3	= 18)
/	Division (float)	(10 / 2 = 5.0)
//	Floor Division (integer)	(10 // 3 = 3)
%	Modulus (remainder)	(10 % 3 = 1)
**	Exponentiation	(2 ** 3 = 8)

2. Comparison Operators
These operators compare two values and return a boolean (True or False).

==	Equal to	(5 == 5	True)
!=	Not equal to	(5 != 3	True)
>	Greater than	(10 > 5	True)
<	Less than	(2 < 5	True)
>=	Greater than or equal to	(7 >= 7	True)
<=	Less than or equal to	(4 <= 3	False)

3. Logical Operators
These operators are used to combine conditional statements.

and	Returns True if both conditions are True	((5 > 2) and (10 > 3)	True)
or	Returns True if at least one condition is True	((5 > 10) or (3 < 8)	True)
not	Reverses the result	(not(5 > 2)	False)


2. **Fun Fact:**
   - Python uses `//` for floor division, ensuring the result is always an integer.
3. **Exercise:**
   - Create a Python script that demonstrates:
     - Addition, subtraction, multiplication, and division.
     - Comparisons between numbers.
     - Logical operations like `and`, `or`, `not`.

```python
# Arithmetic Operations
a = 15
b = 5

print("Addition:", a + b)          # 15 + 5 = 20
print("Subtraction:", a - b)       # 15 - 5 = 10
print("Multiplication:", a * b)    # 15 * 5 = 75
print("Division:", a / b)          # 15 / 5 = 3.0

# Comparison Operations
x = 10
y = 20

print("\nComparison Operators:")
print("x == y:", x == y)   # False
print("x != y:", x != y)   # True
print("x > y:", x > y)     # False
print("x < y:", x < y)     # True
print("x >= y:", x >= y)   # False
print("x <= y:", x <= y)   # True

# Logical Operations
p = True
q = False

print("\nLogical Operators:")
print("p and q:", p and q)  # False (Both must be True)
print("p or q:", p or q)    # True (At least one True)
print("not p:", not p)      # False (Reverses True to False)
```
## 2.4. Function Calls

### 2.4.1. Function Calls as Part of Complex Expressions

1. **Fun Fact:**
   - In Python, functions are first-class objects, meaning they can be assigned to variables and passed as arguments.
2. **Exercise:**
   - Write a program that uses built-in functions inside expressions:
     ```python
     numbers = [5, 3, 8, 1]
     print(max(numbers) - min(numbers))
     ```

### 2.4.2. Functions are Objects; Parentheses Invoke Functions

1. **Exercise:**
   - Assign a function to a variable, then call the function using the new variable:
     ```python
     greet = print
     greet('Hello, World!')
     ```

## 2.5. Data Types

1. **Research:**
   - Investigate Python’s dynamic typing.

   Python is a dynamically typed language, meaning that you don’t need to declare variable types explicitly. Instead, the type of a variable is determined at runtime, and it can change as the program executes.
2. **Exercise:**
   - Create variables of different types and print their types:
     ```python
     a = 10
     b = 'Python'
     c = 3.14
     print(type(a), type(b), type(c))
     ```

## 2.6. Type Conversion Functions

1. **Fun Fact:**
   - Python provides built-in functions like `int()`, `float()`, and `str()` to handle type conversions.
2. **Exercise:**
   - Convert variables between types and observe the results:
     ```python
     num = '123'
     converted_num = int(num)
     print(converted_num, type(converted_num))
     ```

## 2.7. Variables

1. **Research:**
   - Understand how Python stores variables in memory.

   1. Python Variables as References
When you assign a value to a variable, Python creates an object in memory and the variable stores a reference to that object.
Multiple variables can reference the same object in memory.
Example:
```python
x = 10
y = x  # Both x and y refer to the same object in memory
print(id(x), id(y))  # Output: Same memory address for both
🔹 id(x) returns the memory address of the object x points to.
```
2. Mutable vs Immutable Objects
Python has two types of objects:

Immutable Objects (cannot change in place) → int, float, str, tuple, bool
Mutable Objects (can be modified in place) → list, dict, set
Example of Immutable Behavior:
```python
a = 5
b = a  # Both a and b refer to the same memory location
a = 10  # Now a points to a new object, b remains unchanged
print(b)  # Output: 5
🔹 Integer values are immutable, so a = 10 creates a new object instead of modifying the existing one.
```
Example of Mutable Behavior:
```python
lst1 = [1, 2, 3]
lst2 = lst1  # Both lst1 and lst2 point to the same list
lst1.append(4)  # Modifying lst1 affects lst2 as well
print(lst2)  # Output: [1, 2, 3, 4]
🔹 Lists are mutable, so modifying lst1 also changes lst2 since they share the same memory reference.
```
3. Memory Management in Python
Python manages memory using:

Reference Counting: Each object has a count of how many variables reference it.
Garbage Collection: If an object has no references, Python automatically deletes it to free up memory.
Example of Reference Counting:
```python
import sys
x = "hello"
print(sys.getrefcount(x))  # Output: Number of references to "hello"
```
4. Using is vs ==
is → Checks if two variables refer to the same object in memory.
== → Checks if two variables have the same value.
2. **Exercise:**
   - Assign values to variables, print them, and observe changes upon reassignment.
```python
   # Assign initial values
x = 10
y = "Hello"
z = [1, 2, 3]

# Print initial values
print("Initial values:")
print("x =", x)   # 10
print("y =", y)   # Hello
print("z =", z)   # [1, 2, 3]

# Reassign new values
x = 20
y = "Python"
z.append(4)  # Modifying the list (mutable object)

# Print values after reassignment
print("\nValues after reassignment:")
print("x =", x)   # 20 (new value assigned)
print("y =", y)   # Python (new string assigned)
print("z =", z)   # [1, 2, 3, 4] (list modified in place)
```

## 2.8. Variable Names and Keywords

1. **Exercise:**
   - Try using reserved keywords as variable names and observe the errors.

   Python has reserved keywords that cannot be used as variable names because they have special meanings in the language.
2. **Fun Fact:**
   - Use `import keyword; print(keyword.kwlist)` to list all reserved keywords in Python.

## 2.9. Choosing the Right Variable Name

1. **Exercise:**
   - Rewrite a piece of code with meaningful variable names.

Before (Unclear Variable Names)
```python
a = 50
b = 0.2
c = a * b
print(c)
```
After (Meaningful Variable Names)
```python
item_price = 50
discount_rate = 0.2
discount_amount = item_price * discount_rate
print(discount_amount)
```
2. **Challenge:**
   - Why is `total_price` a better name than `tp`?

   This improves code readability and makes it easier to understand.

## 2.10. Statements and Expressions

1. **Research:**
   - Differentiate between statements and expressions.  
	Expression	                            Statement
Produces a value	                        Performs an action
5 + 3, "Hello".upper(), x * 2           	x = 5 + 3, print(x), if x > 0:
Evaluates to	A single value	            Does not return a value directly

2. **Exercise:**
   - Identify statements and expressions in this code:
     ```python
     x = 5 + 3 #statement 
     print(x) #statement
     #(5+3) is an expression
     ```

## 2.11. Order of Operations

1. **Fun Fact:**
   - Python follows PEMDAS (Parentheses, Exponents, Multiplication/Division, Addition/Subtraction) rules.
2. **Exercise:**
   - Write expressions using multiple operators to explore Python’s order of operations.
     ```python
     result = 2 + 3 * 4 ** 2 / 8
     print(result)
     ```

## 2.12. Reassignment

### 2.12.1. Developing Your Mental Model of How Python Evaluates

1. **Exercise:**
   - Assign a value to a variable, reassign it, and observe the changes:
     ```python
     count = 10
     print(count)
     count = 20
     print(count)
     ```

## 2.13. Updating Variables

1. **Exercise:**
   - Increment and decrement variables using `+=` and `-=`.
     ```python
     score = 100
     score += 10
     print(score)
     score -= 5
     print(score)
     ```

## Submission Guidelines:

- Upload all Python files in a zip folder.
- Ensure your code is well-commented.
- Include a README file explaining your submission.

Happy coding! 🚀
