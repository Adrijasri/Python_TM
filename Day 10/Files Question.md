## 🔰 **Beginner-Level Questions (Concept + Code)**

1. **Open and Read File**

   - Write a Python program to read a file `notes.txt` and print its contents line-by-line.
   - 📌 _Concept tested_: File opening, reading, and loop.

```python
   # Open and read the file line by line
with open('notes.txt', 'r') as file:
    for line in file:
        print(line.strip())  # strip() removes trailing newline characters
```

2. **Count Lines in a File**

   - Count how many lines exist in a file `poem.txt`.

```python
# Count the number of lines in poem.txt
with open('poem.txt', 'r') as file:
    line_count = sum(1 for _ in file)
print("Number of lines:", line_count)
```

3. **Write to a File**

   - Create a new file `reminder.txt` and write 5 tasks to it, one per line.

```python
# Write 5 tasks to reminder.txt
tasks = [
    "Buy groceries",
    "Complete Python assignment",
    "Call John",
    "Go for a run",
    "Read a book"
]

with open('reminder.txt', 'w') as file:
    for task in tasks:
        file.write(task + '\n')
```

4. **Append to a File**

   - Add a new task to `reminder.txt` without deleting existing ones.

```python
# Append a new task to reminder.txt
new_task = "Pay electricity bill"

with open('reminder.txt', 'a') as file:
    file.write(new_task + '\n')
```

5. **Check File Exists**
   - Use `os.path.exists()` to check if `data.txt` exists before opening.

```python
import os

# Check if data.txt exists
if os.path.exists('data.txt'):
    with open('data.txt', 'r') as file:
        print(file.read())
else:
    print("File data.txt does not exist.")
```
---

## 🧪 **Intermediate-Level Questions**

6. **Remove Blank Lines**

   - Write a program that reads `input.txt` and creates `cleaned.txt` with no empty lines.

```python
# Remove blank lines from input.txt and write to cleaned.txt
with open('input.txt', 'r') as infile, open('cleaned.txt', 'w') as outfile:
    for line in infile:
        if line.strip():  # Only write non-empty lines
            outfile.write(line)
```

7. **Find and Replace**

   - Search and replace the word “Python” with “PYTHON” in `article.txt`.

```python
# Replace "Python" with "PYTHON" in article.txt
with open('article.txt', 'r') as file:
    content = file.read()

content = content.replace('Python', 'PYTHON')

with open('article.txt', 'w') as file:
    file.write(content)
```

8. **Uppercase Writer**

   - Read a file and write its contents in all **uppercase** to `output.txt`.

```python
# Convert content to uppercase and write to output.txt
with open('input.txt', 'r') as infile, open('output.txt', 'w') as outfile:
    for line in infile:
        outfile.write(line.upper())
```

9. **Student Report Generator**

   - Read `students.txt` containing `Name,Marks`, calculate and save the pass/fail status in `report.txt` (`Pass` if Marks ≥ 50).

```python
# Generate student pass/fail report
with open('students.txt', 'r') as infile, open('report.txt', 'w') as outfile:
    for line in infile:
        name, marks = line.strip().split(',')
        status = 'Pass' if int(marks) >= 50 else 'Fail'
        outfile.write(f"{name},{marks},{status}\n")
```

10. **Reverse File Lines**
    - Reverse the order of lines in `quotes.txt` and write to `reversed_quotes.txt`.
```python
# Reverse the order of lines
with open('quotes.txt', 'r') as infile:
    lines = infile.readlines()

with open('reversed_quotes.txt', 'w') as outfile:
    for line in reversed(lines):
        outfile.write(line)
```
---

## 💡 **Advanced-Level Questions / Mini Projects**

11. **Log File Analyzer**

    - Read a `server.log` file, count how many times the word `"ERROR"` appears, and write all lines with errors to `errors_only.log`.
```python
# Analyze server.log for "ERROR" entries
error_count = 0

with open('server.log', 'r') as infile, open('errors_only.log', 'w') as outfile:
    for line in infile:
        if "ERROR" in line:
            outfile.write(line)
            error_count += 1

print("Total ERROR entries:", error_count)
```

12. **Word Frequency Counter**

    - Read `story.txt` and create a dictionary of word frequency (how many times each word appears), and write it to `frequency.txt`.

```python
from collections import Counter
import re

# Count word frequency
with open('story.txt', 'r') as file:
    text = file.read().lower()
    words = re.findall(r'\b\w+\b', text)  # extract words
    freq = Counter(words)

with open('frequency.txt', 'w') as outfile:
    for word, count in freq.items():
        outfile.write(f"{word}: {count}\n")
```

13. **CSV Reader + Filter**

    - Read `sales.csv`, display all sales above ₹10,000 and write those entries to `high_sales.csv`.

```python
import csv

# Filter sales > 10000
with open('sales.csv', 'r') as infile, open('high_sales.csv', 'w', newline='') as outfile:
    reader = csv.reader(infile)
    writer = csv.writer(outfile)

    header = next(reader)
    writer.writerow(header)  # Write header

    for row in reader:
        if float(row[1]) > 10000:  # Assuming column 2 is the amount
            writer.writerow(row)
```
14. **Merge Multiple Files**

    - Combine the contents of `chapter1.txt`, `chapter2.txt`, and `chapter3.txt` into `full_book.txt`.

```python
# Merge chapters into full_book.txt
files = ['chapter1.txt', 'chapter2.txt', 'chapter3.txt']

with open('full_book.txt', 'w') as outfile:
    for fname in files:
        with open(fname, 'r') as infile:
            outfile.write(infile.read() + '\n')  # Add newline between chapters
```

15. **Directory File Scanner**
    - List all `.txt` or `.csv` files in a given folder using `os.listdir()` and `os.path`.

```python
import os

# List all .txt and .csv files
folder = 'your_folder_path_here'  # replace with your actual path

for file in os.listdir(folder):
    if file.endswith('.txt') or file.endswith('.csv'):
        print(file)
```
---

## 🚀 **Bonus Challenges**

16. **Auto Backup System**

    - Copy the contents of `data.csv` into `backup/data_backup.csv` with the current date in the filename.

```python
import shutil
import datetime
import os

# Create backup folder if it doesn't exist
os.makedirs('backup', exist_ok=True)

# Generate backup filename with current date
date_str = datetime.datetime.now().strftime('%Y%m%d')
backup_filename = f"backup/data_backup_{date_str}.csv"

# Copy file
shutil.copyfile('data.csv', backup_filename)

print("Backup created:", backup_filename)
```
17. **Text Formatter**

    - Remove leading/trailing spaces and convert tabs to spaces in `raw_text.txt`.

```python
# Format raw_text.txt
with open('raw_text.txt', 'r') as infile, open('formatted_text.txt', 'w') as outfile:
    for line in infile:
        cleaned = line.strip().replace('\t', '    ')  # Replace tabs with 4 spaces
        outfile.write(cleaned + '\n')
```

18. **Chat History Logger**

    - Build a basic chat logger: take user input until “exit” and save all messages with timestamps to `chat_log.txt`.

```python
from datetime import datetime

# Chat logger
with open('chat_log.txt', 'a') as logfile:
    while True:
        message = input("You: ")
        if message.lower() == 'exit':
            break
        timestamp = datetime.now().strftime('%Y-%m-%d %H:%M:%S')
        logfile.write(f"[{timestamp}] {message}\n")
```

19. **Custom CSV Sorter**

    - Read `products.csv` and sort by price (ascending). Write the sorted records to `products_sorted.csv`.

```python
import csv

# Sort products by price
with open('products.csv', 'r') as infile:
    reader = list(csv.reader(infile))
    header, data = reader[0], reader[1:]

    sorted_data = sorted(data, key=lambda x: float(x[1]))  # Assuming price is in column 2

with open('products_sorted.csv', 'w', newline='') as outfile:
    writer = csv.writer(outfile)
    writer.writerow(header)
    writer.writerows(sorted_data)
```

20. **JSON Converter**
    - Read `students.txt` with comma-separated values, convert it to a list of dictionaries, and write to `students.json`.

```python
import json

# Convert students.txt to JSON
students = []

with open('students.txt', 'r') as file:
    for line in file:
        name, marks = line.strip().split(',')
        students.append({'name': name, 'marks': int(marks)})

with open('students.json', 'w') as json_file:
    json.dump(students, json_file, indent=4)
```


---
