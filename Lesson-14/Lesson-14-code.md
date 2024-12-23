# Lesson Plan: File Handling in Python (Student Edition)

### **Objective:**  
Learn how to **open, read, write, and close** files in Python, enabling you to store and retrieve data from external sources.

---

## 1. Introduction to File Handling

File handling in Python involves:
- **Opening** a file to access its content.
- **Reading** data from the file.
- **Writing** data to the file.
- **Closing** the file when finished.

Examples of file handling tasks:
- Reading configuration data.
- Saving user input to a text file.
- Processing logs or CSV files.

---

## 2. Opening and Closing Files

### Opening a File
Use the `open()` function to specify the file name (and path) and the **mode**:

```python
file = open("sample.txt", "r")  # Opens 'sample.txt' in read mode
```

### Closing a File
Always remember to **close** a file once you’re done to free up resources:
```python
file.close()
```

### File Modes
- **"r"** (Read Mode): Opens a file for reading (default mode).  
- **"w"** (Write Mode): Creates a new file or **overwrites** an existing file.  
- **"a"** (Append Mode): Opens a file to add new data to the end.  
- **"r+"** (Read/Write Mode): Opens a file for both reading and writing.

---

## 3. Reading from Files

You can read the contents of a file in several ways.

### Read the Entire Content
```python
file = open("sample.txt", "r")
content = file.read()  # Reads all text as a single string
file.close()

print(content)
```

### Read Lines into a List
```python
file = open("sample.txt", "r")
lines = file.readlines()  # Each line is a separate element in a list
file.close()

print(lines)
```

### Read Line by Line with a Loop
```python
file = open("sample.txt", "r")
for line in file:
    print(line.strip())  # .strip() removes extra whitespace/newline
file.close()
```

---

## 4. Writing to Files

You can create or modify files using **write** (`"w"`) and **append** (`"a"`) modes.

### Write Mode
```python
file = open("output.txt", "w")
file.write("Hello, World!")
file.close()
```
- If `output.txt` doesn’t exist, it **creates** the file.
- If `output.txt` exists, it **overwrites** existing content.

### Append Mode
```python
file = open("output.txt", "a")
file.write("\nThis is a new line.")
file.close()
```
- Opens `output.txt` and **adds** new data at the end.

---

## 5. Using the `with` Statement

Using a `with` block is a **best practice** because the file is automatically closed once the block finishes, even if an error occurs.

```python
with open("sample.txt", "r") as file:
    content = file.read()

print(content)  
# 'sample.txt' is closed automatically after the with-block.
```

---

## 6. Exercises and Challenges

1. **Exercise 1**:  
   Write a program that **reads a text file** and **counts the number of words** in it.  
   *Hint:* Use `file.read()` and split the text by spaces or newline characters.

2. **Exercise 2**:  
   Create a **new file** (e.g., `names.txt`) and write a **list of names** to it, one name per line.  
   *Hint:* Use `file.write()` in a loop or join names with `"\n"`.

3. **Challenge 1**:  
   Write a program that **copies** the contents of one text file (e.g., `source.txt`) to another (`destination.txt`).  
   *Hint:* Read from `source.txt` and write to `destination.txt`.

4. **Challenge 2**:  
   Create a **CSV file** (e.g., `data.csv`) and **write** a program that reads and displays the content as a table.  
   *Hint:* Split each row by commas and print in a formatted way.

---

## Additional Practice Problems

1. **Reverse Line Order**  
   - Write a program to **reverse the order** of lines from `input.txt` and save them to `reversed.txt`.  
   - *Hint:* Read lines into a list, reverse the list, and then write them back.

2. **Search for a Keyword**  
   - Ask the user for a **keyword** and search for it in a text file.  
   - Print all lines where the keyword **appears**.

3. **Word Frequency**  
   - Write a program that reads a text file, **counts how many times each word appears**, and prints the top 5 words with their counts.  
   - *Hint:* Use a dictionary to keep track of frequencies.

4. **Error Logging**  
   - Create a simple script that **logs errors** to a file (`error.log`).  
   - Whenever an exception is caught, write a timestamp and the error message to `error.log`.

5. **CSV Writer**  
   - Prompt the user for 3 products and their prices.  
   - Write the data as rows in a CSV file named `products.csv`.  
   - Then read the file back and print each row.

---

## 7. Conclusion

In this lesson, you’ve learned:
- How to **open** and **close** files in Python.
- Different **modes** for reading, writing, and appending.
- How to use the **`with`** statement to simplify file handling.
- Best practices for organizing data with **text files** and **CSV files**.

By practicing these techniques, you’ll be able to work with external data sources and persist information effectively in Python.

---

## Vocabulary Words and Definitions

- **File Handling**: Working with files in a program, including opening, reading, writing, and closing files.  
- **File Pointer**: An internal marker that keeps track of the current position in a file.  
- **Read Mode** (`"r"`): A mode for reading data from an existing file.  
- **Write Mode** (`"w"`): A mode for writing data to a new or existing file (overwrites existing content).  
- **Append Mode** (`"a"`): A mode for adding new data at the end of an existing file.  
- **`with` Statement**: A Python construct that ensures a file is automatically closed after use.  
- **Buffer**: A temporary storage area for data before it’s written to or read from a file.  
- **File Path**: The location of a file in a computer’s directory structure (e.g., `C:\Documents\sample.txt` or `/home/user/sample.txt`).  
- **CSV (Comma-Separated Values)**: A file format in which values are separated by commas, often used for tabular data.  
- **Timestamp**: A string or data that identifies a specific date and time (e.g., `2024-01-01 12:00:00`).

---

### Happy Coding!

Practice reading and writing to files often—log user activity, store data, or create custom CSV reports. As you explore file handling, you’ll find it’s a crucial skill for building real-world Python applications!
