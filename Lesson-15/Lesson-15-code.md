# Lesson Plan: Exception Handling in Python (Student Edition)

### **Objective:**  
Understand how to handle errors and exceptions in Python using **try-except** blocks, as well as how to use **else**, **finally**, and **custom exceptions**.

---

## 1. Introduction to Exception Handling

Exception handling lets you **gracefully manage errors** in your code without causing a complete program crash. This is essential for creating robust, user-friendly applications.

**Example:**  
- If the user enters text where the program expects a number, Python will raise a `ValueError`. By handling this exception, your program can respond kindly instead of crashing.

---

## 2. Common Exceptions

Here are some frequently encountered exceptions in Python:

- **ValueError**: Raised when a function receives an argument of the correct type but inappropriate value (e.g., converting `"abc"` to `int`).
- **ZeroDivisionError**: Raised when attempting to **divide by zero** (e.g., `10 / 0`).
- **FileNotFoundError**: Raised when trying to **open a file** that does not exist.
- **PermissionError**: Raised when you lack the required **permissions** to perform an operation.

---

## 3. Using Try-Except Blocks

A **try-except block** is the basic structure of handling exceptions:

```python
try:
    num = int(input("Enter a number: "))
    result = 10 / num
except ZeroDivisionError:
    print("Division by zero is not allowed.")
except ValueError:
    print("Invalid input. Please enter a valid number.")
```

1. Python tries to **run** the code inside the `try` block.  
2. If an **exception** occurs, Python looks for an `except` block that matches the type of exception.  
3. The matching `except` block handles the error, preventing a crash.

---

## 4. Handling Multiple Exceptions

You can handle multiple exceptions within the same `try` block:

```python
try:
    file = open("nonexistent_file.txt", "r")
    content = file.read()
except (FileNotFoundError, PermissionError):
    print("An error occurred while reading the file.")
```

- This code will catch **both** `FileNotFoundError` and `PermissionError`.

---

## 5. The `else` and `finally` Blocks

- **`else` block**: Runs **only if no exceptions** were raised in the `try` block.  
- **`finally` block**: Runs **regardless** of whether an exception was raised, making it ideal for cleanup tasks (closing files, releasing resources, etc.).

**Example:**
```python
try:
    num = int(input("Enter a number: "))
    result = 10 / num
except ZeroDivisionError:
    print("Division by zero is not allowed.")
else:
    print("Result:", result)
finally:
    print("Execution completed.")
```

---

## 6. Raising Custom Exceptions

In some cases, you might want to **raise** an exception yourself if certain conditions aren’t met.

```python
def divide(x, y):
    if y == 0:
        raise ValueError("Division by zero is not allowed.")
    return x / y

try:
    print(divide(10, 0))
except ValueError as e:
    print("Error:", e)
```

---

## 7. Exercises and Challenges

1. **Exercise 1**:  
   - Write a program that takes user input and **handles the ValueError** when converting to an integer.  
   - *Hint:* Prompt the user to re-enter the number if an exception is raised.

2. **Exercise 2**:  
   - Create a function that calculates the **square root** of a number.  
   - Handle the **ValueError** if a **negative** number is given.  
   - *Hint:* Use the `math.sqrt()` function and wrap it in a try-except block.

3. **Challenge 1**:  
   - Implement a function to **read a file** and handle both `FileNotFoundError` and `PermissionError`.  
   - Ask the user for a filename and display its contents if possible.

4. **Challenge 2**:  
   - Create a program that simulates a simple **banking system**.  
   - Raise custom exceptions for invalid transactions (e.g., withdrawing more money than the current balance).  
   - *Hint:* Create your own exception class that inherits from `Exception`.

---

## Additional Practice Problems

1. **List Index Handling**  
   - Write a function that takes a list and an index from the user.  
   - Handle any **IndexError** if the user provides an index outside the range of the list.

2. **Calculator with Multiple Errors**  
   - Create a small calculator that allows the user to perform basic operations (`+`, `-`, `*`, `/`).  
   - Handle `ValueError` (invalid numbers) and `ZeroDivisionError` (division by zero).

3. **User Authentication**  
   - Simulate a login system that raises a custom exception if the user enters the wrong password three times.  
   - Use a `try-except` block to catch the custom exception and display a warning.

4. **Try-Else-Finally Demo**  
   - Write a script that asks the user for a filename.  
   - In `try`, open the file and read its contents.  
   - Use `else` to print a success message if the file is read successfully.  
   - Use `finally` to print a message indicating the program has ended.

5. **API Request Error Handling** (Optional, if you have requests library)  
   - Make an HTTP request using the `requests` library.  
   - Handle `requests.exceptions.ConnectionError` or `requests.exceptions.Timeout` to demonstrate network error handling.

---

## 8. Conclusion

In this lesson, you learned:
- How to use **try-except** blocks for handling common errors like `ValueError`, `ZeroDivisionError`, and file-related exceptions.
- How to work with **else** and **finally** blocks to create more robust error-handling flows.
- How to **raise custom exceptions** for scenarios unique to your program.

Proper exception handling makes your code more **resilient** and **user-friendly**, preventing crashes when unexpected events occur.

---

## Vocabulary Words and Definitions

- **Exception Handling**: Managing errors and unexpected situations in code so programs don’t crash outright.  
- **Exception**: An event that disrupts normal program flow (e.g., `ValueError`, `ZeroDivisionError`).  
- **Try-Except Block**: A structure to “try” code that might fail and “catch” exceptions.  
- **ValueError**: Raised when a function has a correct data type but an invalid value (e.g., converting letters to int).  
- **ZeroDivisionError**: Raised when dividing by zero.  
- **FileNotFoundError**: Raised when trying to open a non-existent file.  
- **PermissionError**: Raised when attempting an operation without proper permissions.  
- **Else Block**: Runs only if no exception occurred in the `try` block.  
- **Finally Block**: Always runs after a `try` block, regardless of exceptions (useful for cleanup).  
- **Custom Exception**: An exception that you define for specialized error conditions in your code.

---

### Happy Coding!

Keep experimenting with **exception handling**. The more you practice, the better you’ll get at writing code that’s **resilient**, **user-friendly**, and **prepared** for unexpected inputs or system issues!
