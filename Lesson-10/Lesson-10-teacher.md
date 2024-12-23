# Teacher’s Edition: Functions in Python

### **Objective:**  
Introduce functions, arguments, parameters, and return statements in Python to help students write modular and reusable code.

---

## 1. Introduction to Functions

In Python, **functions** are reusable blocks of code that perform specific tasks. Emphasize to students:
- Functions help break large programs into smaller, manageable parts (modularization).
- Code reusability: define once, use multiple times.
- Improved readability and maintenance.

**Teacher Tip:**  
Use analogies—such as a machine that takes in ingredients (arguments) and produces something (the return value)—to help students visualize how functions work.

---

## 2. Defining Functions

```python
def greet():
    print("Hello, World!")
```

- The keyword `def` signals the start of a function definition.
- `greet` is the function name.
- The code inside the function is indented.

**Teacher Tip:**  
Encourage students to keep function names short and descriptive. 

---

## 3. Calling Functions

```python
greet()  # Calls the greet function
```

- Calling `greet()` executes everything inside the `greet` function.

**Common Pitfall:**  
Students often forget parentheses when calling the function, leading to errors or references to the function object rather than execution.

---

## 4. Parameters and Arguments

```python
def greet_user(username):  # Parameter: username
    print(f"Hello, {username}!")

greet_user("Alice")       # Argument: "Alice"
```

- **Parameters**: variables in a function’s definition.
- **Arguments**: actual values passed during the function call.

**Teaching Tip:**  
Show variations: positional arguments, keyword arguments, default arguments, etc.

---

## 5. Return Statements

```python
def add_numbers(num1, num2):
    result = num1 + num2
    return result

sum_result = add_numbers(3, 5)
print("Sum:", sum_result)  # Output: 8
```

- `return` immediately exits the function and sends the specified value back to the caller.

**Common Pitfall:**  
Forgetting to store or print the return value. A function that returns something won’t automatically display it on-screen unless explicitly printed.

---

## 6. Scope of Variables

```python
global_variable = 10

def local_scope_example():
    local_variable = 20
    print("Local variable inside function:", local_variable)
    print("Global variable inside function:", global_variable)

local_scope_example()
print("Global variable outside function:", global_variable)
```

- **Local scope**: variables are accessible only within the function where they’re defined.
- **Global scope**: variables accessible throughout the program.

**Teacher Tip:**  
Stress to students that local variables and global variables can have the same name, but they remain separate entities (shadowing).

---

## 7. Additional Examples

### Example 1: Function with Default Parameters

```python
def greet_with_default(name="User"):
    print(f"Hello, {name}!")
```
- If no argument is provided, `name` defaults to `"User"`.

### Example 2: Function with Multiple Return Values

```python
def split_name(full_name):
    first_name, last_name = full_name.split()
    return first_name, last_name

fn, ln = split_name("John Doe")
print(fn, ln)  # Output: John Doe
```
- Python can return multiple values as a tuple.

### Example 3: Recursive Function (Factorial)

```python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)

print(factorial(5))  # Output: 120
```
- A recursive function calls itself until it meets a base condition.

**Teacher Tip:**  
Always discuss base cases for recursive functions to avoid infinite recursion.

---

## 8. Exercises (With **Solutions**)

Below are exercises from the student lesson, now with **detailed solutions and explanations** for teachers.

### Exercise 1
**Prompt:** Write a function that takes two numbers as arguments and returns their product.

```python
def multiply(num1, num2):
    return num1 * num2

# Example usage:
result = multiply(3, 4)
print("Product:", result)  # Expected output: 12
```

**Teacher Notes:**  
- Emphasize the difference between printing and returning values.
- Some students may do `print(num1 * num2)` instead of `return`. Both are valid, but `return` is usually more flexible.

---

### Exercise 2
**Prompt:** Create a function that calculates and returns the area of a rectangle given its length and width.

```python
def rectangle_area(length, width):
    return length * width

# Example usage:
area = rectangle_area(5, 3)
print("Rectangle area:", area)  # Expected output: 15
```

**Teacher Notes:**  
- Reinforce that the formula for the area of a rectangle is `length * width`.
- You can further ask students to handle invalid inputs (e.g., negative values).

---

### Exercise 3
**Prompt:** Implement a recursive function to calculate the nth Fibonacci number.

Recall the Fibonacci sequence:
```
Fib(0) = 0
Fib(1) = 1
Fib(n) = Fib(n-1) + Fib(n-2) for n >= 2
```

```python
def fibonacci(n):
    if n <= 1:
        return n
    else:
        return fibonacci(n - 1) + fibonacci(n - 2)

# Example usage:
nth_fib = fibonacci(5)
print("Fibonacci(5):", nth_fib)  # Expected output: 5
```

**Teacher Notes:**  
- Show students how recursion works step by step for small `n`.
- This exercise can also be done using an iterative approach for efficiency.

---

## 9. Additional Practice Problems (With **Sample Solutions**)

Below are more practice problems with suggested solutions. Encourage students to experiment with different inputs and edge cases.

1. **List Maximum**  
   **Prompt:** Create a function that takes a list of numbers and returns the largest number in the list.

   ```python
   def find_max(numbers):
       if not numbers:  # Handle empty list case
           return None
       max_num = numbers[0]
       for num in numbers[1:]:
           if num > max_num:
               max_num = num
       return max_num

   # Example usage:
   nums = [3, 10, 2, 8, 6]
   print("Maximum:", find_max(nums))  # Expected output: 10
   ```

   **Teacher Note:**  
   - Some students might use the built-in `max(numbers)` which is perfectly valid.  
   - Highlight how to handle edge cases like an empty list.

2. **Palindrome Check**  
   **Prompt:** Create a function that checks if a given string is a palindrome (reads the same forwards and backwards). Return `True` if it is a palindrome, and `False` otherwise.

   ```python
   def is_palindrome(text):
       # Convert text to lowercase to make it case-insensitive
       text = text.lower()
       # Remove spaces or special characters if you want a pure palindrome check
       return text == text[::-1]

   # Example usage:
   print(is_palindrome("Racecar"))  # Expected output: True
   print(is_palindrome("Hello"))    # Expected output: False
   ```

   **Teacher Tip:**  
   - This can be expanded by removing punctuation or spaces before checking.  
   - Demonstrate `[::-1]` for reversing strings in Python.

3. **Sum of List**  
   **Prompt:** Write a function that accepts a list of numbers and returns the total sum.

   ```python
   def list_sum(numbers):
       total = 0
       for num in numbers:
           total += num
       return total

   # Example usage:
   nums = [1, 2, 3, 4]
   print("Sum of list:", list_sum(nums))  # Expected output: 10
   ```

   **Teacher Note:**  
   - Again, the built-in `sum()` is valid. 
   - Encourage students to understand how iteration accumulates a total.

4. **String Reversal**  
   **Prompt:** Write a function that takes a string as a parameter and returns the reversed string.

   ```python
   def reverse_string(text):
       return text[::-1]

   # Example usage:
   print(reverse_string("Hello"))  # Expected output: "olleH"
   ```

   **Teacher Tip:**  
   - Demonstrate slicing with a negative step to reverse strings.  
   - Students can also experiment with a loop-based approach.

5. **Exponent Function**  
   **Prompt:** Implement a function `power(base, exponent)` that calculates \( base^{exponent} \) using a loop or recursion.

   **Loop version**:
   ```python
   def power(base, exponent):
       result = 1
       for _ in range(exponent):
           result *= base
       return result

   print("2^5 =", power(2, 5))  # Expected output: 32
   ```

   **Recursive version**:
   ```python
   def power_recursive(base, exponent):
       if exponent == 0:
           return 1
       else:
           return base * power_recursive(base, exponent - 1)

   print("2^5 (recursive) =", power_recursive(2, 5))  # Output: 32
   ```

   **Teacher Tip:**  
   - Discuss efficiency differences: iterative vs. recursive.  
   - Show how exponent = 0 is the base case.

---

## 10. Conclusion

In this lesson, we covered:
- **Defining** functions using `def`.
- **Calling** functions and passing in **arguments**.
- Using **return** to get values back from functions.
- Understanding **scope** (local vs. global).
- Writing **recursive** functions.

**Key Takeaways:**
- Functions keep code organized and reusable.
- Return values give flexibility for further computations.
- Variable scope matters (no “leaking” local variables).
- Recursion solves some problems elegantly, but requires a base case.

**Teacher Prompt:**  
- Encourage students to practice by writing multiple small functions.  
- Assign more advanced challenges, such as validating inputs, handling errors, or combining multiple functions in a program.

---

## Vocabulary Words and Definitions

- **Function**: A reusable block of code that performs a specific task.  
- **Parameter**: A variable in a function’s definition that accepts an argument.  
- **Argument**: The actual value passed to a function when it is called.  
- **Return Statement**: A statement that ends a function’s execution and sends a value back to the caller.  
- **Scope**: The region of code where a variable can be accessed.  
- **Local Scope**: Variables accessible only within a function.  
- **Global Scope**: Variables accessible throughout the program.  
- **Recursive Function**: A function that calls itself until a specific condition is met.  
- **Default Parameter**: A parameter with a default value if no argument is provided.  

---

## Extension Ideas

- **Higher-Order Functions**: Show how functions can accept other functions as parameters or return them.
- **Anonymous Functions (Lambdas)**: Introduce lambdas to handle simple tasks inline.
- **Built-In Functions**: Explore how Python’s built-in functions (e.g., `map`, `filter`, `reduce`) can be combined with user-defined functions.

**References & Further Reading**:  
- [Official Python Documentation: Functions](https://docs.python.org/3/tutorial/controlflow.html#defining-functions)  
- [Real Python Tutorial: Defining Your Own Python Function](https://realpython.com/defining-your-own-python-function/)

---

### Happy Teaching!

Use these solutions and explanations as a guide to support students in mastering the fundamentals of functions in Python. Encourage curiosity, experimentation, and plenty of practice to solidify their understanding.
