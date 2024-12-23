# Lesson Plan: Functions Part 2 in Python

### **Objective:**  
Continue working with functions, arguments, parameters, and return statements in Python. Complete exercises and challenges in class.

---

## 1. Review of Functions

Let’s begin by reviewing the basics of functions:
- Functions are defined using the `def` keyword.
- Parameters are variables listed in parentheses after the function name.
- Arguments are the values passed to the function when it’s called.
- Functions can **return** a value back to the caller using the `return` statement.

**Example:**
```python
def greet_user(name):
    return f"Hello, {name}!"
```
- Here, `name` is a **parameter**.
- When we call `greet_user("Alice")`, the argument `"Alice"` is passed in.

---

## 2. Function Parameters (Default and Keyword)

### Default Parameters

A **default parameter** has a default value if no argument is provided.

```python
def greet_with_default(name="User"):
    return f"Hello, {name}!"
```
- If you call `greet_with_default()` with **no** arguments, it will use `"User"` as the default.

### Keyword Arguments

**Keyword arguments** let you specify arguments by name.

```python
def greet_with_keyword_args(first_name, last_name):
    return f"Hello, {first_name} {last_name}!"

# Calling with keyword arguments:
print(greet_with_keyword_args(last_name="Doe", first_name="John"))
# Output: "Hello, John Doe!"
```

---

## 3. Variable-Length Argument Lists

Use variable-length argument lists when you don’t know how many arguments you’ll receive.

```python
def sum_numbers(*numbers):
    total = 0
    for num in numbers:
        total += num
    return total

print(sum_numbers(1, 2, 3))  
# Output: 6
print(sum_numbers(5, 10, 15, 20))
# Output: 50
```

- `*numbers` is a **tuple** inside the function.

---

## 4. Lambda Functions (Anonymous Functions)

A **lambda function** is a short, anonymous function that can take any number of arguments but has only one expression.

```python
add = lambda x, y: x + y

print(add(3, 4))  
# Output: 7
```

- Useful for quick, one-line operations.

---

## 5. Recursive Functions

A **recursive function** calls itself until it reaches a **base case**.

```python
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n - 1)

print(factorial(5))
# Output: 120
```

- **Base case**: `n == 0`.
- Each recursive call reduces the problem size (n - 1).

---

## 6. Exercises and Challenges

1. **Exercise 1:** Create a function that calculates the average of a list of numbers.  
   *Hint:* Sum the numbers and divide by the length of the list.

2. **Exercise 2:** Write a function that takes a string and returns the reverse of the string.  
   *Hint:* Explore Python slicing `[::-1]` or use a loop.

3. **Exercise 3:** Implement a function to find the largest element in a list.  
   *Hint:* You could sort the list or compare elements in a loop.

4. **Challenge 1:** Write a function to check if a given word is a palindrome.  
   *Hint:* A palindrome reads the same forward and backward.

5. **Challenge 2:** Create a function to compute the nth Fibonacci number **without** using recursion.  
   *Hint:* Use a loop and store the current and previous Fibonacci numbers.

---

## Additional Practice Problems

1. **Remove Duplicates**  
   Write a function that takes a list and returns a new list with duplicates removed.

2. **Lambda Multiplication**  
   Use a lambda function to multiply pairs of numbers from two separate lists. Store the products in a new list.

3. **Merge Dictionaries**  
   Create a function that accepts multiple dictionaries (using `*args` or `**kwargs`) and returns a single merged dictionary.

4. **Sum of Digits (Recursive)**  
   Write a recursive function that sums the digits of a positive integer (e.g., 345 → 3 + 4 + 5 = 12).

5. **String Formatting**  
   Create a function that takes a variable number of keyword arguments (using `**kwargs`) and prints them in a formatted string (e.g., `"name=John, age=25, city=New York"`).

---

## 7. Conclusion

In this lesson, you’ve:
- Explored **default** and **keyword** parameters to make your functions more flexible.
- Learned about **variable-length argument lists** to handle multiple inputs.
- Created **lambda functions** for quick operations.
- Practiced with **recursive functions**.
  
Keep practicing these concepts to build more powerful and maintainable Python programs. Don’t forget to experiment with different function types and challenge yourself with bigger projects!

---

## Vocabulary Words and Definitions

- **Default Parameter**: A parameter in a function that has a default value if no argument is provided.
- **Keyword Argument**: An argument in a function call specified by the parameter name (`param_name=value`).
- **Variable-Length Argument List**: A feature (`*args`, `**kwargs`) allowing a function to accept a variable number of positional or keyword arguments.
- **Lambda Function**: An anonymous function defined using the `lambda` keyword, typically limited to a single expression.
- **Recursive Function**: A function that calls itself until it reaches a base condition.
- **Palindrome**: A word or sequence that reads the same backward and forward.
- **Fibonacci Number**: A sequence of numbers where each number is the sum of the two preceding ones (0, 1, 1, 2, 3, 5, 8, …).

---

### Happy Coding!

Try to combine these concepts to solve more complex tasks—e.g., writing a program that uses both lambda functions and recursion, or experimenting with different ways to pass arguments to a function. The more you practice, the more comfortable you’ll become!
