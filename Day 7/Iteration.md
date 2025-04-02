# Iteration: Notes and Assignment

## 6.1. Introduction: Iteration

Iteration is the process of repeatedly executing a set of instructions. In Python, iteration is commonly performed using loops.

## 6.2. The for Loop

A **for loop** allows you to iterate over a sequence (like a list, string, or range) and execute a block of code for each item.

```python
for item in [1, 2, 3]:
    print(item)
```
Output
1
2
3

## 6.3. Flow of Execution of the for Loop

1. Initialize the loop variable with the first item in the sequence.
2. Execute the loop body.
3. Move to the next item and repeat until the sequence is exhausted.

## 6.4. Strings and for Loops

Strings are iterable, meaning you can loop through each character:

```python
for char in "Python":
    print(char)
```
Output
P
y
t
h
o
n

## 6.5. Lists and for Loops

You can iterate through lists directly or use the `range()` function.

### 6.5.1. Using the range Function to Generate a Sequence to Iterate Over

```python
for i in range(5):
    print(i)
```
Output
0
1
2
3
4

### 6.5.2. Iteration Simplifies our Turtle Program

You can use loops to draw repetitive patterns in Turtle graphics:

```python
import turtle
for _ in range(4):
    turtle.forward(100)
    turtle.right(90)
```
It will draw a square

## 6.6. The Accumulator Pattern

Accumulators collect values during iteration, often used for summation or building strings.

```python
total = 0
for i in range(5):
    total += i
print(total)  # 10
```

## 6.7. Traversal and the for Loop: By Index

Use `range()` with `len()` for index-based iteration:

```python
fruits = ["apple", "banana", "cherry"]
for i in range(len(fruits)):
    print(fruits[i])
```
Output
'apple'
'banana'
'cherry'

## 6.8. Nested Iteration: Image Processing

Nested loops handle two-dimensional data like images.

### 6.8.1. The RGB Color Model

Each pixel in an image is represented by Red, Green, and Blue (RGB) values.

### 6.8.2. Image Objects

Libraries like PIL (Pillow) help process images.

```python
from PIL import Image
img = Image.open('example.jpg')
```

### 6.8.3. Image Processing and Nested Iteration

```python
width, height = img.size
for x in range(width):
    for y in range(height):
        r, g, b = img.getpixel((x, y))
        img.putpixel((x, y), (255 - r, 255 - g, 255 - b))  # Invert colors
```

## 6.9. 👩‍💻 Printing Intermediate Results

Print intermediate results to debug:

```python
for i in range(5):
    print(f"i: {i}")
```
Output
i:0
i:1
i:2
i:3
i:4

## 6.10. 👩‍💻 Naming Variables in For Loops

Use meaningful names:

```python
for student in students:
    print(student)
```
Error will be shown as students not defined.

## 6.11. The Gory Details: Iterables

An **iterable** is any object that can return its elements one at a time, like lists, tuples, strings, and dictionaries.

## 6.12. 👩‍💻 Keeping Track of Your Iterator Variable and Your Iterable

Use separate variables for iteration and data to avoid confusion:

```python
students = ["Alice", "Bob", "Charlie"]
for index, student in enumerate(students):
    print(index, student)
```

# Assignment

1. **For Loop Basics:** Write a for loop to print numbers from 1 to 10.

```python
for i in range(1, 11):
    print(i)
```

2. **String Iteration:** Write a program that counts vowels in a string.

```python
def count_vowels(s):
    vowels = "aeiou"
    count = 0
    for char in s:
        if char.lower() in vowels:
            count += 1
    return count
s=input()
print(count_vowels(s))
```
3. **Accumulator Pattern:** Calculate the sum of squares from 1 to 100.
```python
sum=0
for i in range(101):
    sum+=i*i
print(sum)
```
4. **Nested Loops:** Create a multiplication table up to 10x10.
```python
for i in range(1,11):
    for j in range(1,11):
        print(f"{i}*{j}={i*j}")
    print()
```
5. **Image Processing:** Use PIL to invert the colors of an image.
```python
from PIL import Image
img = Image.open('example.jpg')
width, height = img.size
for x in range(width):
    for y in range(height):
        r, g, b = img.getpixel((x, y))
        img.putpixel((x, y), (255 - r, 255 - g, 255 - b))

```
Would you like any diagrams or flowcharts added? Let me know! 🚀
