Assignment Questions

1.Define a sequence. What types of sequences exist in Python?
answer:
A sequence in Python is an ordered collection of elements where each element has a specific position (index). Sequences support operations like indexing, slicing, and iteration.

Types of sequences in Python:

Strings (str)
Lists (list)
Tuples (tuple)
Ranges (range)

2.How are strings, lists, and tuples different from each other?
answer:
Strings, lists, and tuples are all sequences in Python, but they have different characteristics:
- Strings are immutable, meaning they cannot be changed after creation.
- Lists are mutable, meaning they can be changed after creation.
- Tuples are also immutable, but they are faster and more memory-efficient than lists.

3.Explain how indexing works in Python with an example.
answer:
Indexing in Python allows you to access a specific element in a sequence by its position (index).
```python
my_list = ['a', 'b', 'c', 'd']
print(my_list[1])   # 'b'
print(my_list[-1])  # 'd'
```

4.Write code to access the last character of a string.
answer:
```python
my_string = "hello"
print(my_string[-1])  # 'o'
```

5.Create a list of numbers and access the third element.
answer:
```python
my_list = [1, 2, 3, 4, 5]
print(my_list[2])  # 3
```

6.What is the result of len([1, [2, 3], 4]) and why?
answer:
The result of len([1, [2, 3], 4]) is 3.
The len() function counts the number of elements in a sequence. In this case, the sequence is [1, [2, 3], 4].
 The elements are 1, [2,3], and 4. Therefore, the length is 3.

7.Explain slicing with a practical example.
answer:
Slicing in Python allows you to extract a subset of elements from a sequence.
```python
my_list = [1, 2, 3, 4, 5]
print(my_list[1:3])  # [2, 3]
```

8.How would you reverse a string using slicing?
answer:
```python
my_string = "hello"
print(my_string[::-1])  # "olleh"
```
The `[::-1]` slice means start at the end of the string and end at position 0, move with the step -1, which means one step backwards. This effectively reverses the string.

9.Demonstrate list concatenation and repetition with examples.
answer:
```python
my_list1 = [1, 2, 3]
my_list2 = [4, 5, 6]
print(my_list1 + my_list2)  # [1, 2, 3, 4, 5, 6]
print(my_list1 * 2)  # [1, 2, 3, 1, 2, 3]
```
The `+` operator is used for concatenation, and the `*` operator is used for
repetition.

10.Write code to count the occurrences of an element in a list.
answer:
```python
my_list = [1, 2, 2, 3, 3, 3, 4, 5]
print(my_list.count(3))  # 3
```
The `count()` method returns the number of occurrences of the specified element in the list. In this case, the element 3 occurs 3 times.

11.What will my_tuple = (1, 2, 3); print(my_tuple[1:]) output?
answer:
The output will be (2, 3).
The `my_tuple[1:]` slice means start at the second element of the tuple (index 1) and go to the end of the tuple. This effectively returns a new tuple containing the second and third elements of the original tuple.

12.Explain the difference between list.append() and list.extend().
answer:
`list.append()` adds a single element to the end of the list, while `list.extend()` adds multiple elements to the end of the list.
```python
my_list = [1, 2, 3]
print(my_list.append(4))  # None
print(my_list)  # [1, 2, 3, 4]
```
```python
lst = [1, 2, 3]
lst.extend([4, 5])
print(lst)  # [1, 2, 3, 4, 5]
```
In the first example, `append(4)` adds the single element 4 to the end ofthe list. In the second example, `extend([4, 5])` adds the multiple elements 4 and 5 to the end of the list.

13.Write code to split the sentence: "Learn Python, step by step!" into words.
answer:
```python
sentence = "Learn Python, step by step!"
words = sentence.split()
print(words)  # ['Learn', 'Python,', 'step', 'by', 'step!]
```
The `split()` method splits the sentence into words based on whitespace characters.

14.Join a list ['Python', 'is', 'fun'] into a single string.
answer:
```python
list= ['Python', 'is', 'fun'] 
print(' '.join(list)) #'Python is fun'
```
The `' '.join()` method joins the elements of the list into a single string, with spaces in between.

15.Given a list numbers = [1, 2, 2, 3, 4, 2], find the index of the first 2.
answer:
```python
numbers = [1, 2, 2, 3, 4, 2]
print (numbers.index(2)) # output 2
```
The `index()` method returns the index of the first occurrence of the specified element in the list.

16.Write code to check if a string is a palindrome.
answer:
```python
def is_palindrome(s):
    return s == s[::-1]
s=input()
print (is_palindrome(s))
```

17.Implement a function that returns the length of the longest word in a sentence.
answer:
```python
def longest_word(sentence):
    words = sentence.split()
    return max(words, key=len)
sen=input()
print (longest_word(sen))
```
The `max()` function with the `key` argument set to `len` returns the longest word.

18.Demonstrate nested list indexing.
answer:
```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
print(matrix[0][1]) # Output: 2
```
The `matrix[0][1]` expression accesses the element at the first row and second column.

19.How do you convert a list of characters into a string?
answer:
```python
chars = ['h', 'e', 'l', 'l', 'o']
print(''.join(chars)) # Output: 'hello'
```
The `''.join()` method concatenates the characters in the list into a single string.

20.Write code to remove duplicates from a list while preserving order.
answer:
```python
def remove_duplicates(lst):
    seen = set()
    return [x for x in lst if not (x in seen or seen.add(x))]

lst = [1, 2, 2, 3, 4, 2]
print(remove_duplicates(lst)) # Output: [1, 2, 3, 4]
```
The list comprehension iterates over the list and uses a set to keep track of seen elements. The `or seen.add(x)` expression is a common idiom to add an element to a set while checking if it's already present. If the element is already in the set, it's skipped; otherwise, it's added to the set and included in the output list.

21.Write a function that takes a list of tuples and sorts it by the second element of each tuple.
answer:
```python
def sort_tuples(tuples):
    return sorted(tuples, key=lambda x: x[1])

tuples = input()
print(sort_tuples(tuples)) 
```
The `sorted()` function with the `key` argument set to a lambda function that returns the second element of each tuple sorts the list of tuples by the second element.

22.Implement a program to flatten a nested list of arbitrary depth.
answer:
```python
def flatten(lst):
    result = []
    for i in lst:
        if isinstance(i, list):
            result.extend(flatten(i))
        else:
            result.append(i)
    return result

print(flatten([1, [2, [3, 4]], 5]))  # Output: [1, 2, 3, 4, 5]
```
The `flatten()` function iterates over the input list. If an element is a list, it recursively calls itself with the sublist as argument and extends the result list with the flattened sublist. If an element is not a list, it's appended to the result list.

23.Create a function that rotates a list to the right by k steps.
answer:
```python
def rotate(lst, k):
    k = k % len(lst)
    return lst[-k:] + lst[:-k]
print(rotate([1, 2, 3, 4, 5], 2))
```
The function calculates the effective number of steps by taking the remainder of the division of k by the length of the list. It then returns a new list that is the concatenation of the last k elements of the original list and the rest of the list.

24.Given two strings, write a function that returns True if they are anagrams.  
answer:
```python
def are_anagrams(str1, str2):
    return sorted(str1) == sorted(str2)
print(are_anagrams('listen', 'silent'))
```
The function sorts the characters in each string and compares the sorted lists. If they are equal, the
strings are anagrams.

25.Create a function to split a list into chunks of a specified size.
answer:
```python
def chunk_list(lst, size):
    return [lst[i:i + size] for i in range(0, len(lst), size)]
print(chunk_list([1, 2, 3, 4, 5, 6]))
```
The function uses a list comprehension to create a new list where each element is a chunk of the original
list. The `range()` function generates indices that are multiples of the specified size, and the list
comprehension slices the original list at these indices to create the chunks.

26.Implement a function that merges two sorted lists into one sorted list.
answer:
```python
def merge_sorted_lists(a, b):
    merged = []
    i, j = 0, 0

    while i < len(a) and j < len(b):
        if a[i] < b[j]:
            merged.append(a[i])
            i += 1
        else:
            merged.append(b[j])
            j += 1
    merged.extend(a[i:])
    merged.extend(b[j:])

    return merged

list1 = [1, 3, 5, 7]
list2 = [2, 4, 6, 8]
print(merge_sorted_lists(list1, list2))
```

CODES

```python
def validate_pipelines(pipelines, threshold):
    longest_pipeline = max(pipelines, key=lambda x: x[1])[0]
    exceeding_pipelines = [name for name, time in pipelines if time > threshold]
    return f"Longest Pipeline: {longest_pipeline}\nPipelines exceeding threshold: {exceeding_pipelines}"

pipelines = [("Data Ingestion", 30), ("Preprocessing", 45), ("Model Training", 120), ("Evaluation", 20)]
threshold = 40
print(validate_pipelines(pipelines, threshold))
```


```python
def parse_config(config):
    return [tuple(item.split("=")) for item in config.split(";")]

config = "host=127.0.0.1;port=8080;mode=debug"
print(parse_config(config))
```

```python
def extract_hashtags(post):
    return list(set([word for word in post.split() if word.startswith("#")]))

post = "Loving the new #Python course! #Coding #Python #Learning"
print(extract_hashtags(post))
```

```python
def decode_message(secret_message):
    return secret_message[::2]

secret_message = "hweollrolwd"
print(decode_message(secret_message))
```

```python
def highest_quantity_product(inventory):
    return max(inventory, key=lambda x: x[1])[0]

inventory = [("Apples", 50), ("Oranges", 75), ("Bananas", 30)]
print(highest_quantity_product(inventory))
```

```python
def analyze_survey(survey_data):
    scores = list(map(int, survey_data.split(",")))
    return f"Max Score: {max(scores)}, Min Score: {min(scores)}"

survey_data = "5,3,4,1,2"
print(analyze_survey(survey_data))
```

```python
def assign_roles(users, roles):
    return [f"{users[i]}: {roles[i]}" for i in range(len(users))]

users = ["Alice", "Bob", "Charlie"]
roles = ("Admin", "Editor", "Viewer")
print(assign_roles(users, roles))
```
```python
def categorize_message(message):
    length = len(message)
    category = "Short" if length < 20 else "Medium" if length < 50 else "Long"
    return f"Category: {category}"

message = "My account is locked, please help!"
print(categorize_message(message))
```

```python
def longest_product_name(products):
    return max(products, key=len)

products = ["Laptop", "Smartphone", "Wireless Headphones"]
print(longest_product_name(products))
```

```python
def average_last_readings(sensor_readings):
    last_10 = sensor_readings[-10:]
    return f"Average: {sum(last_10) // len(last_10)}"

sensor_readings = [12, 15, 14, 16, 20, 22, 21, 23, 25, 30, 28, 27]
print(average_last_readings(sensor_readings))
```

```python
def reverse_transactions(transactions):
    return transactions[::-1]

transactions = [100, -50, 200, -150, 50]
print(reverse_transactions(transactions))
```

```python
def format_logs(logs, timestamp):
    return [f"{timestamp}: {log}" for log in logs]

logs = ["System Boot", "Network Connected", "User Login"]
timestamp = "2025-03-20"
print(format_logs(logs, timestamp))
```

```python
def generate_pattern(symbol, count):
    return " ".join([symbol] * count)

symbol = "*"
count = 5
print(generate_pattern(symbol, count))
```

```python
def count_word_occurrences(feedback, word="excellent"):
    return f"'{word}' count: {feedback.lower().split().count(word)}"

feedback = "The product is excellent, absolutely excellent!"
print(count_word_occurrences(feedback))
```

```python
def find_error_index(log):
    return f"Index: {log.lower().find('error')}"

log = "INFO: All systems go. ERROR: Failed to start service."
print(find_error_index(log))
```

```python
def parse_csv(csv_data):
    return [line.split(",") for line in csv_data.split("\n")]

csv_data = "Alice,25,Engineer\nBob,30,Doctor\nCharlie,22,Artist"
print(parse_csv(csv_data))
```

```python
def generate_usernames(names):
    return [f"{name.split()[0][0]}{name.split()[1]}" for name in names]

names = ["Alice Wonderland", "Bob Builder", "Charlie Chaplin"]
print(generate_usernames(names))
```

```python
from collections import Counter

def count_messages(chat_logs):
    user_counts = Counter(log.split(":")[0] for log in chat_logs)
    return [f"{user}: {count} messages" for user, count in user_counts.items()]

chat_logs = ["Alice: Hi!", "Bob: Hello!", "Alice: How are you?", "Bob: I’m good, thanks!"]
print(count_messages(chat_logs))
```

```python
def compress(data):
    for i in range(1, len(data) // 2 + 1):
        if data == data[:i] * (len(data) // i):
            return f"'{data[:i]}' repeated {len(data) // i} times"
    return data

data = "abababababab"
print(compress(data))
```
