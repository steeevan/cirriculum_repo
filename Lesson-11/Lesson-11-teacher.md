# Teacher’s Edition: Functions Part 2 in Python

### **Objective:**  
Continue working with functions, arguments, parameters, and return statements in Python. Complete exercises and challenges with provided solutions and insights.

---

## 1. Review of Functions

**Quick Recap**  
- Define functions using `def function_name(parameters): ...`
- Pass arguments when calling the function.
- Return values using `return`.

<details>
  <summary>Review Example</summary>

```python
def greet_user(name):
    return f"Hello, {name}!"
```
</details>

**Teacher Note:**  
Emphasize the difference between **parameters** (in the definition) and **arguments** (in the call).

---

## 2. Function Parameters (Default and Keyword)

### Default Parameters

```python
def greet_with_default(name="User"):
    return f"Hello, {name}!"
```

- If no argument is provided, `name` defaults to `"User"`.

### Keyword Arguments

```python
def greet_with_keyword_args(first_name, last_name):
    return f"Hello, {first_name} {last_name}!"

# Example call:
print(greet_with_keyword_args(last_name="Doe", first_name="John"))
```

- Makes the code more readable and order-independent.

**Teacher Tip:**  
Show students how default parameters must come **after** non-default parameters in the function signature.

---

## 3. Variable-Length Argument Lists

```python
def sum_numbers(*numbers):
    total = 0
    for num in numbers:
        total += num
    return total
```

- `*numbers` collects all positional arguments into a **tuple**.

**Teacher Tip:**  
Demonstrate usage with varying numbers of arguments to illustrate flexibility.

---

## 4. Lambda Functions (Anonymous Functions)

```python
add = lambda x, y: x + y
```

- Lambdas are **one-line** anonymous functions useful for quick operations.

**Teacher Note:**  
Encourage students to compare a lambda to a regular function definition for clarity.

---

## 5. Recursive Functions

```python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)
```

- A **recursive function** calls itself, gradually reducing the problem size until the base case (`n == 0`) is reached.

**Teacher Tip:**  
Discuss potential pitfalls of recursion, like exceeding the recursion limit if the base case is incorrect or absent.

---

## 6. Exercises and Challenges (With **Solutions**)

Below are the exercises and challenges for students, along with complete solutions for teachers to reference.

### Exercise 1
**Prompt:** Create a function that calculates the average of a list of numbers.

<details>
  <summary>Solution & Explanation</summary>

```python
def average(numbers):
    if not numbers:
        return 0  # Handle empty list case
    return sum(numbers) / len(numbers)

# Example usage:
nums = [10, 20, 30, 40]
print("Average:", average(nums))
# Explanation:
#  - sum(numbers) adds up all values in the list
#  - len(numbers) gets the total count of elements
#  - Dividing sum by count yields the average
```
</details>

---

### Exercise 2
**Prompt:** Write a function that takes a string and returns the reverse of the string.

<details>
  <summary>Solution & Explanation</summary>

```python
def reverse_string(text):
    return text[::-1]

# Example usage:
my_string = "Hello"
print("Reverse:", reverse_string(my_string))
# Explanation:
#  - text[::-1] uses slicing with a negative step to reverse the string
```
</details>

---

### Exercise 3
**Prompt:** Implement a function to find the largest element in a list.

<details>
  <summary>Solution & Explanation</summary>

```python
def find_largest(numbers):
    if not numbers:
        return None  # or raise an error for empty list
    largest = numbers[0]
    for num in numbers[1:]:
        if num > largest:
            largest = num
    return largest

# Example usage:
nums = [10, 50, 20, 40]
print("Largest element:", find_largest(nums))
# Explanation:
#  - Initialize "largest" to the first element
#  - Compare each element to "largest", update if bigger
```
</details>

---

### Challenge 1
**Prompt:** Write a function to check if a given word is a palindrome.

<details>
  <summary>Solution & Explanation</summary>

```python
def is_palindrome(word):
    word = word.lower()  # optional: make it case-insensitive
    return word == word[::-1]

# Example usage:
print(is_palindrome("Racecar"))  # True
print(is_palindrome("Hello"))    # False
# Explanation:
#  - A palindrome reads the same forwards and backwards
#  - Lowercasing ensures consistent comparison
```
</details>

---

### Challenge 2
**Prompt:** Create a function to compute the nth Fibonacci number **without** using recursion.

<details>
  <summary>Solution & Explanation</summary>

```python
def fibonacci_iterative(n):
    if n < 0:
        return None  # handle invalid inputs if necessary
    if n == 0:
        return 0
    if n == 1:
        return 1

    prev, curr = 0, 1
    for _ in range(2, n + 1):
        nxt = prev + curr
        prev, curr = curr, nxt
    return curr

# Example usage:
print("Fibonacci(5):", fibonacci_iterative(5))
# Explanation:
#  - We start with fib(0)=0 and fib(1)=1
#  - Loop from 2 up to n, updating the previous and current Fibonacci numbers
```
</details>

---

## Additional Practice Problems (With **Sample Solutions**)

Use these for further class activities or homework assignments.

### 1. Remove Duplicates
**Prompt:** Write a function that takes a list and returns a new list with duplicates removed.

<details>
  <summary>Sample Solution</summary>

```python
def remove_duplicates(items):
    return list(set(items))

# Example usage:
my_list = [1, 2, 2, 3, 4, 4, 5]
print("No duplicates:", remove_duplicates(my_list))
# Explanation:
#  - Converting to a set removes duplicates
#  - Converting back to a list gets the final result
```
</details>

---

### 2. Lambda Multiplication
**Prompt:** Use a lambda function to multiply pairs of numbers from two separate lists. Store the products in a new list.

<details>
  <summary>Sample Solution</summary>

```python
def multiply_pairs(list1, list2):
    # Pair up elements using zip, then multiply with a lambda
    return list(map(lambda x: x[0] * x[1], zip(list1, list2)))

# Example usage:
l1 = [1, 2, 3]
l2 = [4, 5, 6]
products = multiply_pairs(l1, l2)
print("Products:", products)
# Explanation:
#  - zip(l1, l2) produces pairs (1,4), (2,5), (3,6)
#  - map(lambda x: x[0] * x[1], zip(...)) multiplies each pair
```
</details>

---

### 3. Merge Dictionaries
**Prompt:** Create a function that accepts multiple dictionaries (using `*args` or `**kwargs`) and returns a single merged dictionary.

<details>
  <summary>Sample Solution (Using *args)</summary>

```python
def merge_dictionaries(*dicts):
    merged = {}
    for d in dicts:
        merged.update(d)
    return merged

# Example usage:
dict1 = {"a": 1, "b": 2}
dict2 = {"b": 3, "c": 4}
merged_result = merge_dictionaries(dict1, dict2)
print("Merged dict:", merged_result)
# Explanation:
#  - *dicts treats each dictionary as a separate argument
#  - merged.update(d) adds items from each dict
#  - Later dictionaries overwrite keys with the same name
```
</details>

<details>
  <summary>Alternative (Using **kwargs)</summary>

```python
def merge_kwargs(**kwargs):
    return kwargs

# Example usage:
merged_kwargs = merge_kwargs(a=1, b=2, c=3)
print("Merged kwargs dict:", merged_kwargs)
# Explanation:
#  - **kwargs collects named arguments into a dictionary
```
</details>

---

### 4. Sum of Digits (Recursive)
**Prompt:** Write a recursive function that sums the digits of a positive integer (e.g., 345 → 3 + 4 + 5 = 12).

<details>
  <summary>Sample Solution & Explanation</summary>

```python
def sum_of_digits(n):
    if n < 10:
        return n
    else:
        return (n % 10) + sum_of_digits(n // 10)

# Example usage:
print("Sum of digits in 345:", sum_of_digits(345))
# Explanation:
#  - If n < 10, it's a single digit, so just return it
#  - Otherwise, add the last digit (n % 10) to the sum of digits of the rest (n // 10)
```
</details>

---

### 5. String Formatting
**Prompt:** Create a function that takes a variable number of keyword arguments (using `**kwargs`) and prints them in a formatted string (e.g., `"name=John, age=25, city=New York"`).

<details>
  <summary>Sample Solution & Explanation</summary>

```python
def format_kwargs(**kwargs):
    # Each item in kwargs is a key-value pair
    formatted_pairs = [f"{key}={value}" for key, value in kwargs.items()]
    return ", ".join(formatted_pairs)

# Example usage:
info = format_kwargs(name="John", age=25, city="New York")
print("Formatted kwargs:", info)
# Explanation:
#  - kwargs.items() returns key-value pairs
#  - Use a list comprehension to create "key=value" strings
#  - Join them with ", " to create the final string
```
</details>

---

## 7. Conclusion

In this **Functions Part 2** lesson, students expanded their knowledge of:
- **Default & Keyword Parameters**: providing more flexibility in function calls.
- **Variable-Length Argument Lists**: handling an unknown number of arguments.
- **Lambda Functions**: quick, one-line anonymous functions.
- **Recursive Functions**: calling a function within itself until a base condition is met.

By working through the exercises, students will strengthen their understanding of how to write and utilize functions to create cleaner, more organized code.

**Teacher Reminders:**
- Encourage students to try variations and look at edge cases (e.g., empty lists, negative numbers).
- Push them to articulate **why** a certain solution works.
- Offer guidance on how to choose between **iteration** and **recursion**.

---

## Vocabulary Words and Definitions

- **Default Parameter**: A parameter in a function that has a default value if no argument is provided.  
- **Keyword Argument**: An argument in a function call that is specified using the parameter name (`param_name=value`).  
- **Variable-Length Argument List**: A feature (`*args` / `**kwargs`) allowing a function to accept a variable number of arguments.  
- **Lambda Function**: An anonymous function defined with the `lambda` keyword, limited to a single expression.  
- **Recursive Function**: A function that calls itself until it reaches a base condition.  
- **Palindrome**: A word or sequence that reads the same forward and backward (e.g., "racecar").  
- **Fibonacci Number**: A sequence of numbers where each number is the sum of the two preceding ones (0, 1, 1, 2, 3, 5, 8, …).  

---

### Happy Teaching!

Use these solutions and explanations to help guide your class through the exercises, clarify tricky points, and spark meaningful discussions about the power and flexibility of Python functions. Encourage students to continue exploring and to experiment with their own function-based projects!
