# **Chapter 9: Files in Python**

---

## **9.1. Introduction: Working with Data Files**

When you create programs, sometimes you want your data to _survive_ after the program ends. This is where **files** come in. Files allow us to store information permanently on the disk.

> **Real Life Example:** Think of a file as a notebook where you write down your shopping list so you don’t forget it later.

📂 **Types of Files:**

- **Text files:** Store data in readable form (.txt, .csv, .json).
- **Binary files:** Store data in a format readable only by programs (.exe, .jpg, .bin).

---

## **9.1.1 Learning Goals**

- Understand how to read and write files.
- Process data stored in external files.
- Learn to use CSV files.
- Handle file operations safely and efficiently.

---

## **9.1.2 Objectives**

After this chapter, you should be able to:

- Open and read from a file.
- Write data into a file.
- Find files on your system.
- Process files line-by-line.
- Read and write CSV data.

---

## **9.2. Reading a File**

```python
file = open('example.txt', 'r')
content = file.read()
print(content)
file.close()
```

📘 **Explanation:**

- `'r'` stands for read mode.
- Always **close** the file to free system resources.

> ⚡ **Warning:** If the file does not exist, `open()` will throw an error!

---

## **9.3. Alternative File Reading Methods**

Sometimes you don’t want the whole file at once.

- **Read line by line:**

```python
file = open('example.txt', 'r')
line = file.readline()
print(line)
file.close()
```

- **Read all lines into a list:**

```python
file = open('example.txt', 'r')
lines = file.readlines()
print(lines)
file.close()
```

📝 **Note:** `readlines()` will include `\n` at the end of each line.

---

## **9.4. Iterating over lines in a file**

**Best practice:** loop through the file directly.

```python
with open('example.txt', 'r') as file:
    for line in file:
        print(line.strip())  # .strip() removes \n
```

📈 **Diagram: Iteration over lines**

```plaintext
File: example.txt

Line 1: Hello World
Line 2: Welcome to Python
Line 3: End

Loop:
|-- Hello World
|-- Welcome to Python
|-- End
```

---

## **9.5. Finding a File in your Filesystem**

You can use the **os** module to navigate files.

```python
import os

path = '/path/to/folder'
print(os.listdir(path))  # Lists files in the directory
```

🔍 **To check if a file exists:**

```python
import os

if os.path.exists('example.txt'):
    print("File found!")
else:
    print("File not found.")
```

---

## **9.6. Using `with` for Files**

Using `with` is safer because it automatically closes the file even if an error occurs.

```python
with open('example.txt', 'r') as file:
    content = file.read()
    print(content)
```

💡 **Tip:** Always use `with` when working with files!

---

## **9.7. Recipe for Reading and Processing a File**

📋 **Steps:**

1. Open the file.
2. Read line-by-line.
3. Process each line.
4. Close the file.

```python
filename = 'data.txt'
with open(filename, 'r') as file:
    for line in file:
        processed_line = line.strip().upper()
        print(processed_line)
```

---

## **9.8. Writing Text Files**

```python
with open('output.txt', 'w') as file:
    file.write("Hello, this is a new file!\n")
    file.write("Writing more text.\n")
```

🛠️ **Modes:**

- `'w'` — write (overwrites file)
- `'a'` — append (adds to file)

---

## **9.9. CSV Format**

CSV = **Comma-Separated Values**.

```plaintext
Name,Age,City
Alice,30,New York
Bob,25,Los Angeles
```

🔗 **CSV is easy to read and used for data storage and sharing**.

---

## **9.10. Reading in Data from a CSV File**

Using the `csv` module:

```python
import csv

with open('data.csv', 'r') as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```

🧠 **Row Example:** `['Alice', '30', 'New York']`

---

## **9.11. Writing Data to a CSV File**

```python
import csv

with open('data.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerow(['Name', 'Age', 'City'])
    writer.writerow(['Charlie', '22', 'Chicago'])
```

🛡️ **Important:** Use `newline=''` to prevent extra blank lines on Windows.

---

## **9.12. 👩‍💻 Tips on Handling Files**

- Always close your files (`with` does it automatically).
- Handle exceptions using `try-except` blocks.
- Check if the file exists before opening.
- Process large files **line-by-line** to save memory.

```python
try:
    with open('data.txt', 'r') as file:
        content = file.read()
except FileNotFoundError:
    print("The file was not found.")
```

---

## 📝 **Problem Statement:**

Build a Python program that:

1. Reads a text file (`students.txt`) containing student names and their marks.
2. Calculates the average marks.
3. Writes the names of students who scored above the average into a new file called `top_students.txt`.
4. Also, save the data into a CSV file (`students.csv`).

---

### **Example `students.txt`:**

```plaintext
Alice,85
Bob,78
Charlie,90
Diana,95
Evan,65
```

---

### **Final Outputs:**

- `top_students.txt`
- `students.csv`

---

```python
import csv

# Step 1: Read and parse students.txt
with open('students.txt', 'r') as file:
    content = file.read().strip()

# Split into pairs and process
entries = content.split()
students = []

for entry in entries:
    name, marks = entry.split(',')
    students.append((name, int(marks)))

# Step 2: Calculate average marks
total_marks = sum(marks for _, marks in students)
average = total_marks / len(students)
print(f"Average Marks: {average:.2f}")

# Step 3: Write top students to top_students.txt
with open('top_students.txt', 'w') as top_file:
    for name, marks in students:
        if marks > average:
            top_file.write(name + '\n')

# Step 4: Write all data to students.csv
with open('students.csv', 'w', newline='') as csv_file:
    writer = csv.writer(csv_file)
    writer.writerow(['Name', 'Marks'])  # Header
    for name, marks in students:
        writer.writerow([name, marks])
```

**Assignment Title**: Student Records Management System

### Objective:

Build a program that:

1. Creates a file `students.csv`.
2. Takes user input for multiple students (name, age, grade).
3. Saves student data into the file.
4. Reads and displays all students.
5. Finds and displays students above a certain grade.

---

### Requirements:

✅ Create the CSV file if it doesn’t exist.  
✅ Use **`csv.DictWriter`** to write rows.  
✅ Use **`csv.DictReader`** to read rows.  
✅ Handle exceptions properly (e.g., FileNotFoundError).

---

### Starter Code:

```python
import csv

def add_student():
    name = input("Enter name: ")
    age = input("Enter age: ")
    grade = input("Enter grade: ")

    with open('students.csv', 'a', newline='') as file:
        writer = csv.DictWriter(file, fieldnames=['Name', 'Age', 'Grade'])
        if file.tell() == 0:  # Write header only if file is empty
            writer.writeheader()
        writer.writerow({'Name': name, 'Age': age, 'Grade': grade})

def view_students():
    try:
        with open('students.csv', 'r') as file:
            reader = csv.DictReader(file)
            for row in reader:
                print(row)
    except FileNotFoundError:
        print("No records found.")

def main():
    while True:
        print("\n1. Add Student\n2. View Students\n3. Exit")
        choice = input("Enter choice: ")
        if choice == '1':
            add_student()
        elif choice == '2':
            view_students()
        elif choice == '3':
            break
        else:
            print("Invalid choice.")

if __name__ == "__main__":
    main()
```

---

📖 **Illustrations for Assignment:** (for adding in the book)

- **Flowchart**: Student input → Save to file → Read from file → Display.
- **Table**: Example of what `students.csv` would look like.

| Name  | Age | Grade |
| ----- | --- | ----- |
| Alice | 21  | 88    |
| Bob   | 22  | 75    |

---

### **Bonus Challenges (⭐⭐⭐):**

1. If the `students.txt` file is missing, handle it gracefully.
2. Make your program case insensitive (`alice` and `Alice` are the same).
3. Sort the output file alphabetically by name.

---

# 📈 **Diagram: Assignment Workflow**

```plaintext
students.txt
    |
    v
Read data
    |
    v
Calculate Average
    |
    v
Find top students
    |
    v
Write to top_students.txt
    |
    +--> Also save all data into students.csv
```
```python
import csv
import os

CSV_FILE = 'students.csv'
FIELDNAMES = ['Name', 'Age', 'Grade']

def add_student():
    name = input("Enter name: ").strip().title()  # Normalize name (case-insensitive)
    age = input("Enter age: ").strip()
    grade = input("Enter grade: ").strip()

    # Create file if not exists and write data
    with open(CSV_FILE, 'a', newline='') as file:
        writer = csv.DictWriter(file, fieldnames=FIELDNAMES)
        if file.tell() == 0:  # Empty file check
            writer.writeheader()
        writer.writerow({'Name': name, 'Age': age, 'Grade': grade})
    print(f"✅ Student {name} added.")

def view_students():
    try:
        with open(CSV_FILE, 'r') as file:
            reader = csv.DictReader(file)
            students = sorted(reader, key=lambda x: x['Name'])
            print("\n📄 All Students:")
            for row in students:
                print(f"Name: {row['Name']}, Age: {row['Age']}, Grade: {row['Grade']}")
    except FileNotFoundError:
        print("⚠️ File not found. No records to display.")

def students_above_grade():
    try:
        threshold = float(input("Enter grade threshold: "))
        with open(CSV_FILE, 'r') as file:
            reader = csv.DictReader(file)
            top_students = [row for row in reader if float(row['Grade']) > threshold]
            if top_students:
                print(f"\n🎯 Students scoring above {threshold}:")
                for student in sorted(top_students, key=lambda x: x['Name']):
                    print(f"{student['Name']} - Grade: {student['Grade']}")
            else:
                print("No students found above the given grade.")
    except FileNotFoundError:
        print("⚠️ File not found. Cannot perform search.")
    except ValueError:
        print("❌ Invalid grade input.")

def main():
    while True:
        print("\n📘 Student Manager")
        print("1. Add Student")
        print("2. View Students")
        print("3. View Students Above Grade")
        print("4. Exit")

        choice = input("Enter choice: ").strip()
        if choice == '1':
            add_student()
        elif choice == '2':
            view_students()
        elif choice == '3':
            students_above_grade()
        elif choice == '4':
            print("👋 Exiting. Goodbye!")
            break
        else:
            print("❌ Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
```
---
