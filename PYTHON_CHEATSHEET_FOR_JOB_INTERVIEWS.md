# PYTHON CHEATSHEET🚨 FOR JOB INTERVIEWS📝

---

## **1. Functions: Define and Use Functions**
**Explanation:** Defines a reusable function to greet a user and demonstrates its use.

```python
# Function to greet a user
def greet(name):
    return f"Hello, {name}!"

# Usage
greeting = greet("Alice")
print(greeting)
```

---

## **2. Lists: Basic Operations on Lists**
**Explanation:** Shows how to add, remove, and manipulate elements in a list.

```python
fruits = ["apple", "banana", "cherry"]
fruits.append("orange")
fruits.remove("banana")
fruits[1] = "blueberry"
print(fruits)
```

---

## **3. Loops: Iterating Over Lists**
**Explanation:** Iterates over a list and prints each item.

```python
for fruit in ["apple", "banana", "cherry"]:
    print(fruit)
```

---

## **4. File Handling: Read and Write Files**
**Explanation:** Demonstrates writing to and reading from a text file using the 'with' statement.

```python
# Writing to a file
with open("example.txt", "w") as file:
    file.write("Hello, World!\n")

# Reading from a file
with open("example.txt", "r") as file:
    content = file.read()
    print(content)
```

---

## **5. Data Manipulation with Dictionaries**
**Explanation:** Adds and accesses elements in a dictionary, demonstrating data manipulation.

```python
person = {"name": "John", "age": 30}
person["city"] = "New York"
print(person["name"])
print(person)
```

---

## **6. List Comprehensions**
**Explanation:** Creates a list of squares using list comprehension.

```python
squares = [x**2 for x in range(10)]
print(squares)
```

---

## **7. Exception Handling**
**Explanation:** Handles division by zero error using a try-except block.

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero!")
```

---

## **8. Reading CSV Files**
**Explanation:** Reads and prints rows from a CSV file using the csv module.

```python
import csv

with open("data.csv", newline='') as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)
```

---

## **9. Writing JSON Data**
**Explanation:** Writes a dictionary to a JSON file using the json module.

```python
import json

data = {"name": "Alice", "age": 25}

with open("data.json", "w") as json_file:
    json.dump(data, json_file)
```

---

## **10. Pandas: DataFrame Basics**
**Explanation:** Creates a simple Pandas DataFrame and prints it.

```python
import pandas as pd

data = {"Name": ["John", "Alice"], "Age": [30, 25]}
df = pd.DataFrame(data)
print(df)
```

---

# PRACTICAL QUESTIONS FOR INTERVIEWS

---

## **1. Reverse a String Without Using Built-in Functions**
```python
def reverse_string(s):
    result = ""
    for char in s:
        result = char + result
    return result

print(reverse_string("hello"))
```

---

## **2. Check if Two Strings are Anagrams**
```python
def are_anagrams(str1, str2):
    return sorted(str1) == sorted(str2)

print(are_anagrams("listen", "silent"))
```

---

## **3. Find the Missing Number in a List**
```python
def find_missing_number(arr):
    n = len(arr) + 1
    total = n * (n + 1) // 2
    return total - sum(arr)

print(find_missing_number([1, 2, 4, 5]))
```

---

## **4. Flatten a Nested List**
```python
def flatten(nested_list):
    result = []
    for item in nested_list:
        if isinstance(item, list):
            result.extend(flatten(item))
        else:
            result.append(item)
    return result

print(flatten([1, [2, [3, 4], 5]]))
```

---

## **5. Implement a Simple Cache (Memoization)**
```python
cache = {}

def expensive_function(x):
    if x in cache:
        return cache[x]
    result = x * x  # Simulate expensive computation
    cache[x] = result
    return result

print(expensive_function(4))
print(expensive_function(4))  # Cached result
```

---

## **6. Find the First Non-Repeating Character**
```python
from collections import Counter

def first_non_repeating_char(s):
    count = Counter(s)
    for char in s:
        if count[char] == 1:
            return char
    return None

print(first_non_repeating_char("aabbcddce"))
```

---

## **7. Sort a Dictionary by Its Values**
```python
my_dict = {"apple": 3, "banana": 1, "cherry": 2}
sorted_dict = dict(sorted(my_dict.items(), key=lambda item: item[1]))
print(sorted_dict)
```

---

## **8. Find the Longest Palindromic Substring**
```python
def longest_palindrome(s):
    n = len(s)
    result = ""
    for i in range(n):
        for j in range(i, n):
            temp = s[i:j+1]
            if temp == temp[::-1] and len(temp) > len(result):
                result = temp
    return result

print(longest_palindrome("babad"))
```

---

## **9. Count the Frequency of Words in a String**
```python
def word_frequency(text):
    words = text.split()
    freq = {}
    for word in words:
        freq[word] = freq.get(word, 0) + 1
    return freq

print(word_frequency("this is a test this is only a test"))
```

---

## **10. Generate All Permutations of a List**
```python
from itertools import permutations

def all_permutations(lst):
    return list(permutations(lst))

print(all_permutations([1, 2, 3]))
```

---

> **Tip:** Copy these code snippets into your IDE, run them, tweak them, and be job-interview-ready!
> 
