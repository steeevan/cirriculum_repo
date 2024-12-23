# Teacher’s Edition: File Handling in Python

### **Objective:**  
Enable students to confidently open, read, write, and close files in Python. Provide them with guided examples, exercises, and solutions for deeper understanding.

---

## 1. Introduction to File Handling

**Key Points to Emphasize**:
- Opening a file using `open(<filename>, <mode>)`.
- Closing files to free resources.
- Reading/writing modes and their implications.

---

## 2. Opening and Closing Files

```python
# Opening a file in read mode
file = open("sample.txt", "r")

# Closing a file
file.close()
```

**Teacher Tip**:  
- Explain the concept of **file pointers** and how Python tracks the current position in a file.

---

## 3. Reading from Files

### Read the Entire Content
```python
file = open("sample.txt", "r")
content = file.read()
file.close()

print(content)
```

### Read Lines into a List
```python
file = open("sample.txt", "r")
lines = file.readlines()
file.close()

print(lines)
```

### Read Line by Line with a Loop
```python
file = open("sample.txt", "r")
for line in file:
    print(line.strip())
file.close()
```

**Teacher Tip**:  
- Demonstrate the difference between `read()`, `readline()`, and `readlines()`.

---

## 4. Writing to Files

### Write Mode
```python
file = open("output.txt", "w")
file.write("Hello, World!")
file.close()
```

- Overwrites file content if it already exists.

### Append Mode
```python
file = open("output.txt", "a")
file.write("\nThis is a new line.")
file.close()
```

- Adds new content to the end of an existing file.

**Teacher Tip**:  
- Show how `w` mode will create a file if it doesn’t already exist.

---

## 5. Using the `with` Statement

A safer way to handle files—closes automatically when the block ends:

```python
with open("sample.txt", "r") as file:
    content = file.read()

print(content)
```

**Teacher Tip**:  
- Emphasize that `with` ensures proper cleanup even if exceptions occur.

---

## 6. Exercises and Challenges (With **Solutions**)

Here are the exercises from the student edition, now with suggested solutions and explanations.

### Exercise 1  
**Prompt**: Write a Python program that reads a text file and **counts the number of words** in it.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
def count_words_in_file(filename):
    with open(filename, "r") as file:
        text = file.read()
    
    # Split on whitespace to get individual words
    words = text.split()
    return len(words)

# Example usage:
file_name = "story.txt"
word_count = count_words_in_file(file_name)
print(f"Number of words in {file_name}: {word_count}")
```

**Explanation**:  
1. We open the file using `with open(...)`.  
2. Read its entire content into a string.  
3. Use `split()` to separate the text into words.  
4. `len(words)` gives the total count of words.
</details>

---

### Exercise 2  
**Prompt**: Create a new file and **write a list of names** to it, one name per line.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
def write_names_to_file(names, filename):
    with open(filename, "w") as file:
        for name in names:
            file.write(name + "\n")

# Example usage:
names_list = ["Alice", "Bob", "Charlie", "Diana"]
write_names_to_file(names_list, "names.txt")
```

**Explanation**:  
- Use `with open(filename, "w")` to create/overwrite the file.  
- Write each name on a new line using `"\n"`.
</details>

---

### Challenge 1  
**Prompt**: Write a program that **copies** the contents of one text file to another.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
def copy_file_contents(source, destination):
    with open(source, "r") as src:
        content = src.read()

    with open(destination, "w") as dst:
        dst.write(content)

# Example usage:
copy_file_contents("source.txt", "destination.txt")
```

**Explanation**:  
1. Read the entire content from `source.txt`.  
2. Write the same content to `destination.txt`.  
3. Using two separate `with` blocks ensures both files are properly closed.
</details>

---

### Challenge 2  
**Prompt**: Create a CSV file and **write a program** to read and display the content as a table.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
import csv

def read_csv_and_display(filename):
    with open(filename, "r", newline="") as file:
        reader = csv.reader(file)
        for row in reader:
            # Print each row as a table row
            print("\t".join(row))

# Example usage:
read_csv_and_display("data.csv")
```

**Explanation**:  
- The `csv` module simplifies reading CSV files.  
- `csv.reader` returns each row as a list of strings.  
- `"\t".join(row)` prints the row’s elements separated by tabs (can also use commas, spaces, etc.).
</details>

---

## Additional Practice Problems (With **Sample Solutions**)

### 1. Reverse Line Order
**Prompt**: Reverse the order of lines from `input.txt` and save them to `reversed.txt`.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
def reverse_lines(input_file, output_file):
    with open(input_file, "r") as infile:
        lines = infile.readlines()

    reversed_lines = lines[::-1]  # Reverse the list of lines

    with open(output_file, "w") as outfile:
        for line in reversed_lines:
            outfile.write(line)

# Example usage:
reverse_lines("input.txt", "reversed.txt")
```

**Explanation**:  
1. Read all lines into a list.  
2. Reverse the list using `[::-1]`.  
3. Write them out in reversed order.
</details>

---

### 2. Search for a Keyword
**Prompt**: Ask the user for a **keyword** and search for it in a text file. Print lines where the keyword appears.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
def search_keyword_in_file(filename, keyword):
    with open(filename, "r") as file:
        for line_number, line in enumerate(file, start=1):
            if keyword.lower() in line.lower():
                print(f"Line {line_number}: {line.strip()}")

# Example usage:
keyword_input = input("Enter a keyword to search: ")
search_keyword_in_file("sample.txt", keyword_input)
```

**Explanation**:  
- Convert both the line and the keyword to **lowercase** for case-insensitive matching.  
- `enumerate(file, start=1)` helps display the line number.
</details>

---

### 3. Word Frequency
**Prompt**: Read a text file, **count how many times each word appears**, and print the top 5 words with their counts.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
from collections import Counter

def top_word_frequencies(filename, top_n=5):
    with open(filename, "r") as file:
        text = file.read().lower()

    words = text.split()
    counter = Counter(words)
    most_common = counter.most_common(top_n)

    print(f"Top {top_n} most frequent words in {filename}:")
    for word, count in most_common:
        print(f"{word}: {count}")

# Example usage:
top_word_frequencies("story.txt", 5)
```

**Explanation**:  
1. Convert text to lowercase for uniform comparison.  
2. Use `collections.Counter` to count occurrences of each word.  
3. `most_common(top_n)` returns the top `n` frequent words.
</details>

---

### 4. Error Logging
**Prompt**: Create a simple script that **logs errors** to a file (`error.log`) whenever an exception is caught.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
import traceback
from datetime import datetime

def risky_operation():
    # Example operation that might raise an exception
    return 10 / 0

try:
    risky_operation()
except Exception as e:
    with open("error.log", "a") as log:
        timestamp = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
        log.write(f"[{timestamp}] - ERROR: {str(e)}\n")
        # Optionally, write detailed traceback
        log.write(traceback.format_exc() + "\n")

print("Program continues despite the error. Check error.log for details.")
```

**Explanation**:  
- `try/except` handles potential errors.  
- `datetime.now().strftime(...)` adds a timestamp for each error.  
- `traceback.format_exc()` captures the full traceback for debugging.
</details>

---

### 5. CSV Writer
**Prompt**: Ask the user for 3 products and their prices, then write the data as rows in a CSV file named `products.csv`. Read the file back and print each row.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
import csv

def write_products_to_csv(filename):
    with open(filename, "w", newline="") as file:
        writer = csv.writer(file)
        writer.writerow(["Product", "Price"])

        for _ in range(3):
            product = input("Enter product name: ")
            price = input("Enter product price: ")
            writer.writerow([product, price])

def read_and_display_csv(filename):
    with open(filename, "r", newline="") as file:
        reader = csv.reader(file)
        for row in reader:
            print(" | ".join(row))

# Example usage:
write_products_to_csv("products.csv")
read_and_display_csv("products.csv")
```

**Explanation**:  
1. `csv.writer` writes rows to a CSV file.  
2. The `writer.writerow([...])` method saves each row as a list.  
3. Use `csv.reader` to read and print each row.  
4. `" | ".join(row)` customizes the display format.
</details>

---

## 7. Conclusion

**Key Takeaways**:
- Python’s file handling is **straightforward**, but requires attention to **modes** (`"r"`, `"w"`, `"a"`).  
- The **`with`** statement simplifies file handling by ensuring automatic closure.  
- Handling **CSV** files often involves the built-in `csv` module.  
- Regular practice with reading/writing files helps students handle real-world data processing tasks.

---

## Vocabulary Words and Definitions

- **File Handling**: The process of working with files (opening, reading, writing, and closing).  
- **File Pointer**: The current position in a file where the next read/write will occur.  
- **Read Mode** (`"r"`): Opens a file for reading.  
- **Write Mode** (`"w"`): Creates/overwrites a file for writing.  
- **Append Mode** (`"a"`): Opens a file for appending (adds data at the end).  
- **`with` Statement**: A Python construct that automatically closes a file after its block is exited.  
- **Buffer**: Temporary storage for data being read/written.  
- **CSV**: Comma-Separated Values, a file format for tabular data.  
- **Timestamp**: A string/data that indicates date and time (`"2024-01-01 12:00:00"`).  
- **Enumerate**: A Python function that allows you to loop over items and have an automatic counter (`for i, item in enumerate(list)`).  

---

### Happy Teaching!

Use these solutions and explanations to guide class discussions, demonstrate code examples, and address common pitfalls. Encourage students to explore file handling creatively—e.g., by logging events, storing quiz questions, or processing simple databases in text form.
