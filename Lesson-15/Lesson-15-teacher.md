# Teacher’s Edition: Exception Handling in Python

### **Objective:**  
Teach students how to handle errors and exceptions using try-except blocks, as well as how to use `else`, `finally`, and custom exceptions for more robust error handling.

---

## 1. Introduction to Exception Handling

**Key Teaching Points**:
- Exceptions occur when Python encounters an **error condition** in the code.
- Using try-except blocks allows for **graceful recovery** rather than a program crash.

**Analogy**: You can think of try-except like wearing a seatbelt—if something unexpected happens (like a crash), the seatbelt (the except block) can help protect your program from disaster.

---

## 2. Common Exceptions

### Frequently Encountered Exceptions

1. **ValueError**  
   - Occurs when a function receives an argument of the right type but an **inappropriate** value.  
   - Example: `int("abc")` raises a **ValueError**.

2. **ZeroDivisionError**  
   - Raised when dividing by zero.  
   - Example: `10 / 0`.

3. **FileNotFoundError**  
   - Occurs when a file is not found at the specified path.  
   - Example: `open("nonexistent.txt")` if `"nonexistent.txt"` doesn’t exist.

4. **PermissionError**  
   - Occurs when the user does not have the necessary permissions to perform an operation (like writing to a protected file).

**Teacher Tip**:  
- Demonstrate these exceptions with short code snippets.
- Emphasize how recognizing exceptions helps with debugging.

---

## 3. Using Try-Except Blocks

```python
try:
    num = int(input("Enter a number: "))
    result = 10 / num
except ZeroDivisionError:
    print("Division by zero is not allowed.")
except ValueError:
    print("Invalid input. Please enter a valid number.")
```

1. **try**: Code that might produce an exception.  
2. **except**: Handles specific exception types.

**Teacher Tip**:  
- Show how each except block targets a specific error.  
- Discuss how the order of except blocks matters if you’re catching multiple exception types.

---

## 4. Handling Multiple Exceptions

```python
try:
    file = open("nonexistent_file.txt", "r")
    content = file.read()
except (FileNotFoundError, PermissionError):
    print("An error occurred while reading the file.")
```

- A single except block can handle **multiple** exception types by grouping them in a tuple.

**Teacher Tip**:  
- Emphasize the importance of specifying **relevant** exceptions rather than using a catch-all approach unless absolutely necessary.

---

## 5. The `else` and `finally` Blocks

1. **`else` block**: Runs only if **no exception** occurs in the try block.  
2. **`finally` block**: Runs **regardless** of whether an exception happened or not (good for cleanup tasks).

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

**Teacher Tip**:  
- Show how `else` is never called if an exception occurs, but `finally` always runs.

---

## 6. Raising Custom Exceptions

In some scenarios, you’ll want to raise your **own** exceptions to signal a specific error condition.

```python
def divide(x, y):
    if y == 0:
        raise ValueError("Division by zero is not allowed.")
    return x / y
```

**Teacher Tip**:  
- Explain how raising exceptions helps with **validating** inputs or flow control in large applications.

---

## 7. Exercises and Challenges (With **Sample Solutions**)

### Exercise 1  
**Prompt**: Write a program that takes user input and handles the **ValueError** when converting to an integer.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
def get_integer_from_user():
    while True:
        user_input = input("Enter an integer: ")
        try:
            num = int(user_input)
            print("You entered:", num)
            break
        except ValueError:
            print("Invalid input. Please enter a valid integer.")
            # Loop continues until a valid integer is entered

get_integer_from_user()
```

**Explanation**:  
- The `while True:` loop keeps asking for input until a valid integer is provided.  
- If a **ValueError** is raised, it’s caught and an error message is printed.
</details>

---

### Exercise 2  
**Prompt**: Create a function that calculates the **square root** of a number, and handle **ValueError** if a negative number is given. Use `math.sqrt()`.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
import math

def safe_sqrt(number):
    try:
        result = math.sqrt(number)
        return result
    except ValueError:
        print("Cannot take the square root of a negative number.")
        return None

# Example usage:
num = float(input("Enter a number: "))
sqrt_value = safe_sqrt(num)
if sqrt_value is not None:
    print(f"Square root of {num} is: {sqrt_value}")
```

**Explanation**:  
- `math.sqrt()` raises a **ValueError** for negative inputs.  
- We catch that error and print a helpful message instead of crashing.
</details>

---

### Challenge 1  
**Prompt**: Implement a function to read a file and handle both `FileNotFoundError` and `PermissionError`.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
def read_file_contents(filename):
    try:
        with open(filename, "r") as file:
            return file.read()
    except FileNotFoundError:
        print("File not found. Please check the filename and try again.")
    except PermissionError:
        print("You do not have permission to read this file.")

# Example usage:
filename = input("Enter filename: ")
contents = read_file_contents(filename)
if contents is not None:
    print("File contents:\n", contents)
```

**Explanation**:  
- `FileNotFoundError`: The file doesn’t exist at the given path.  
- `PermissionError`: The user doesn’t have the rights to read the file.  
- By returning `None` on errors, the program can gracefully handle the missing file or lack of permissions.
</details>

---

### Challenge 2  
**Prompt**: Create a program that simulates a simple **banking system**, raising custom exceptions for invalid transactions (e.g., withdrawing more money than the current balance).

<details>
  <summary>Sample Solution & Explanation</summary>

```python
class InsufficientFundsError(Exception):
    pass

class NegativeDepositError(Exception):
    pass

class BankAccount:
    def __init__(self, balance=0):
        self.balance = balance

    def deposit(self, amount):
        if amount < 0:
            raise NegativeDepositError("Cannot deposit a negative amount.")
        self.balance += amount
        print(f"Deposited ${amount}. New balance: ${self.balance}")

    def withdraw(self, amount):
        if amount > self.balance:
            raise InsufficientFundsError("Insufficient funds for this withdrawal.")
        self.balance -= amount
        print(f"Withdrew ${amount}. New balance: ${self.balance}")

# Example usage:
account = BankAccount(100)
try:
    account.deposit(-50)
except NegativeDepositError as e:
    print("Error:", e)

try:
    account.withdraw(200)
except InsufficientFundsError as e:
    print("Error:", e)
```

**Explanation**:  
- **Custom exceptions** (`InsufficientFundsError`, `NegativeDepositError`) inherit from `Exception`.  
- `deposit()` checks if the amount is negative, raising `NegativeDepositError`.  
- `withdraw()` checks if the amount exceeds the balance, raising `InsufficientFundsError`.  
- This design is clearer than using generic exception types for domain-specific errors.
</details>

---

## Additional Practice Problems (With **Sample Solutions**)

### 1. List Index Handling

<details>
  <summary>Sample Solution & Explanation</summary>

```python
def get_list_element(lst, index):
    try:
        return lst[index]
    except IndexError:
        print("Index out of range.")
        return None

# Example usage:
my_list = [10, 20, 30]
elem = get_list_element(my_list, 5)  # This should trigger an IndexError
```

**Explanation**:  
- If `index` is outside the list’s range, **IndexError** is raised and handled.  
- The function returns `None` if the index is invalid, giving the calling code a way to handle it gracefully.
</details>

---

### 2. Calculator with Multiple Errors

<details>
  <summary>Sample Solution & Explanation</summary>

```python
def calculator():
    try:
        num1 = float(input("Enter the first number: "))
        operator = input("Choose an operator (+, -, *, /): ")
        num2 = float(input("Enter the second number: "))

        if operator == '+':
            result = num1 + num2
        elif operator == '-':
            result = num1 - num2
        elif operator == '*':
            result = num1 * num2
        elif operator == '/':
            result = num1 / num2  # This may raise ZeroDivisionError
        else:
            print("Invalid operator.")
            return

        print("Result:", result)

    except ValueError:
        print("Invalid input. Please enter numeric values.")
    except ZeroDivisionError:
        print("Division by zero is not allowed.")

# Example usage:
calculator()
```

**Explanation**:  
- **ValueError**: If the user inputs non-numeric data (e.g., `"abc"`).  
- **ZeroDivisionError**: If the user attempts to divide by zero.
</details>

---

### 3. User Authentication

<details>
  <summary>Sample Solution & Explanation</summary>

```python
class TooManyAttemptsError(Exception):
    pass

def login_system(correct_password):
    attempts = 0
    while attempts < 3:
        user_pass = input("Enter password: ")
        if user_pass == correct_password:
            print("Login successful!")
            return
        else:
            attempts += 1
            print("Incorrect password.")

    raise TooManyAttemptsError("Too many incorrect attempts.")

# Example usage:
try:
    login_system("secret123")
except TooManyAttemptsError as e:
    print("Error:", e)
```

**Explanation**:  
- We use a **custom exception** `TooManyAttemptsError` to signal the user has exceeded the allowed attempts.  
- The function tracks incorrect attempts. If the limit (3) is reached, it raises the custom exception.
</details>

---

### 4. Try-Else-Finally Demo

<details>
  <summary>Sample Solution & Explanation</summary>

```python
def read_file_demo(filename):
    try:
        with open(filename, "r") as file:
            content = file.read()
    except FileNotFoundError:
        print("File not found.")
    else:
        print("File read successfully:")
        print(content)
    finally:
        print("Program finished execution.")

# Example usage:
read_file_demo("sample.txt")
```

**Explanation**:  
- **try**: Attempts to open and read the file.  
- **except FileNotFoundError**: Catches the error if the file doesn’t exist.  
- **else**: Prints a success message and the content if no exception occurred.  
- **finally**: Prints a closing message whether or not an exception occurred.
</details>

---

### 5. API Request Error Handling (Optional)

<details>
  <summary>Sample Solution & Explanation</summary>

```python
import requests

def fetch_data(url):
    try:
        response = requests.get(url, timeout=5)
        response.raise_for_status()  # Raises HTTPError for bad responses
        return response.text
    except requests.exceptions.Timeout:
        print("The request timed out.")
    except requests.exceptions.ConnectionError:
        print("Failed to connect to the server.")
    except requests.exceptions.HTTPError as e:
        print(f"HTTP error occurred: {e}")

# Example usage:
data = fetch_data("https://www.example.com")
if data:
    print("Data fetched successfully.")
```

**Explanation**:  
- **Timeout**: If the server takes too long to respond, `requests.exceptions.Timeout` is raised.  
- **ConnectionError**: If unable to connect to the server at all.  
- **HTTPError**: For non-2xx responses (like 404, 500, etc.).  
- `response.raise_for_status()` throws an exception if the response code indicates an error.
</details>

---

## 8. Conclusion

**Key Takeaways**:
- **try-except** blocks prevent crashes by handling errors gracefully.  
- **else** runs only if no exception was raised, while **finally** always runs.  
- **Custom exceptions** are helpful for specific domain-related errors, making your code more readable and maintainable.

**Teacher Reminders**:
- Encourage students to consistently handle potential exceptions rather than ignoring them.  
- Emphasize that robust error handling leads to better user experiences and fewer runtime crashes.

---

## Vocabulary Words and Definitions

- **Exception Handling**: Managing and responding to errors in a program so it doesn’t crash unexpectedly.  
- **Exception**: An event (error) that disrupts the normal program flow (e.g., `ValueError`, `ZeroDivisionError`).  
- **Try-Except Block**: A structure in Python to attempt some code (try) and catch exceptions (except) if they occur.  
- **Else Block**: A block that executes only when no exceptions occur in the try block.  
- **Finally Block**: A block that executes no matter what, useful for releasing resources or final messages.  
- **Custom Exception**: A user-defined exception type for handling domain-specific error conditions.  
- **IndexError**: Raised when accessing an index that’s out of range in a sequence.  
- **HTTPError**: An error that occurs when a server returns an unsuccessful HTTP status code.  
- **raise_for_status()**: A `requests` method that raises an HTTPError if the request returned a 4xx or 5xx response.  

---

### Happy Teaching!

Use these solutions and explanations to clarify **exception handling** concepts. Encourage students to practice by deliberately introducing errors in code to see how Python reacts and how effective error handling keeps a program running smoothly.
