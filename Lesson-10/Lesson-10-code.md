# Lesson Plan: Functions in Python

### **Objective:**  
Introduce functions, arguments, parameters, and return statements in Python to help students write modular and reusable code.

---

## 1. Introduction to Functions

In Python (and many other programming languages), **functions** are reusable blocks of code that perform specific tasks. They are essential for:
- **Modularizing** your program (breaking it into smaller parts),
- **Reusability** (using the same code in multiple places),
- **Readability** (making your code easier to understand and maintain).

---

## 2. Defining Functions

You can **define** a function in Python using the `def` keyword, followed by the function name and parentheses `()`.

```python
def greet():
    print("Hello, World!")
```

When Python sees the keyword `def`, it knows you’re about to define a new function named `greet`. Anything indented below the `def` line belongs to that function.

---

## 3. Calling Functions

Once defined, you can **call** (execute) a function by writing its name followed by parentheses.

```python
greet()  # This calls the greet function
```

When you call `greet()`, Python will run all the code inside the function’s body.

---

## 4. Parameters and Arguments

- **Parameters** are placeholders for input values your function can receive.  
- **Arguments** are the actual values you pass to the function.

**Example:**
```python
def greet_user(username):  # "username" is a parameter
    print(f"Hello, {username}!")

greet_user("Alice")  # "Alice" is the argument
```

When calling `greet_user("Alice")`, the argument `"Alice"` is assigned to the parameter `username`.

---

## 5. Return Statements

A function can **return** a value to its caller using the `return` keyword.  

```python
def add_numbers(num1, num2):
    result = num1 + num2
    return result

sum_result = add_numbers(3, 5)
print("Sum:", sum_result)  # Output: Sum: 8
```

- Once Python encounters a `return` statement, the function **exits immediately** and sends the specified value back to the caller.

---

## 6. Scope of Variables

- **Local Scope**: Variables created inside a function exist **only within** that function.  
- **Global Scope**: Variables created outside all functions are accessible **throughout** the program.

**Example**:
```python
global_variable = 10

def local_scope_example():
    local_variable = 20
    print("Local variable inside function:", local_variable)
    print("Global variable inside function:", global_variable)

local_scope_example()
print("Global variable outside function:", global_variable)
```

Notice that `local_variable` can’t be accessed outside the function because it only exists inside `local_scope_example()`.

---

## 7. Additional Examples

### Example 1: Function with Default Parameters

```python
def greet_with_default(name="User"):
    print(f"Hello, {name}!")
```
- If you **don’t** provide an argument, `name` defaults to `"User"`.
- If you call `greet_with_default("Bob")`, it prints `Hello, Bob!`.

### Example 2: Function with Multiple Return Values

```python
def split_name(full_name):
    first_name, last_name = full_name.split()
    return first_name, last_name

fn, ln = split_name("John Doe")
print(fn, ln)  # Output: John Doe
```
- Functions can return **multiple values** as a **tuple**.

### Example 3: Recursive Function (Factorial)

```python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)

print(factorial(5))  # Output: 120
```
- A **recursive function** calls **itself** until a base condition is met.

---

## 8. Exercises

1. **Exercise 1:** Write a function that takes two numbers as arguments and returns their product.

2. **Exercise 2:** Create a function that calculates and returns the area of a rectangle given its length and width.

3. **Exercise 3:** Implement a recursive function to calculate the nth Fibonacci number.

---

## 9. Additional Practice Problems

Here are more problems to deepen your understanding of functions:

1. **List Maximum**  
   Create a function that takes a list of numbers and returns the largest number in the list.

2. **Palindrome Check**  
   Create a function that checks if a given string is a palindrome (reads the same forwards and backwards). The function should return `True` if it is a palindrome, and `False` otherwise.

3. **Sum of List**  
   Write a function that accepts a list of numbers and returns the total sum.

4. **String Reversal**  
   Write a function that takes a string as a parameter and returns the reversed string.

5. **Exponent Function**  
   Implement a function `power(base, exponent)` that calculates \( base^{exponent} \) using a loop or recursion.

---

## 10. Conclusion

In this lesson, you have learned:

- How to **define** a function using the `def` keyword.
- How to **call** a function and pass **arguments**.
- How to use **return** statements to get values back from functions.
- The concept of **local** and **global** scopes.
- How to write **recursive** functions.

Functions are crucial for keeping code organized, reusable, and easy to maintain. Continue to practice writing and using functions in your projects!

---

## Vocabulary Words and Definitions

- **Function**: A reusable block of code that performs a specific task.
- **Parameter**: A variable in a function definition that accepts an argument.
- **Argument**: The actual value passed to a function when it is called.
- **Return Statement**: A statement that ends a function’s execution and sends a value back to the caller.
- **Scope**: The region of code where a variable can be accessed and manipulated.
- **Local Scope**: The scope within a function; variables are created and destroyed each time the function is called.
- **Global Scope**: The scope of variables accessible throughout the program.
- **Recursive Function**: A function that calls itself until a specific condition is met.
- **Default Parameter**: A parameter that has a default value if no argument is provided.

---

### Happy Learning!

Practice these concepts by experimenting with small programs and trying out different function types (with parameters, without parameters, returning values, etc.). The more you code, the more comfortable you’ll become with functions in Python!
