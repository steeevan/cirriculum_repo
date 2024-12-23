# Lesson Plan: Modules and Libraries in Python (Student Edition)

### **Objective:**  
Learn how to use built-in modules, install external libraries, and create your own modules to extend Python’s functionality.

---

## 1. Introduction to Modules and Libraries

In Python:
- A **module** is a single file of Python code that can be imported into your program.
- A **library** is a **collection** of modules that help you do more advanced tasks, such as making network requests, handling data, or building websites.

**Why use modules and libraries?**  
- **Reusability**: You don’t need to reinvent the wheel.  
- **Efficiency**: Leverage powerful, well-tested code.  
- **Organization**: Keep your code simpler by delegating tasks to modules.

---

## 2. Using Built-in Modules

Python comes with many **built-in modules** that are ready to use without any extra installation.

```python
import math

sqrt_result = math.sqrt(25)
print("Square root of 25 is:", sqrt_result)  # Output: 5.0
```

**Common Built-in Modules**:
- `math`: mathematical functions (e.g., square root, trigonometry).
- `random`: generate random numbers.
- `datetime`: work with dates and times.

---

## 3. Installing External Libraries

Not everything you need is included in the standard library. You can install external libraries using **package managers** like `pip`.

```bash
# Example command in your terminal or command prompt:
pip install requests
```

- **`pip`** is the default package manager for Python.  
- After installing, you can import the library into your script.

---

## 4. Using External Libraries

Once installed, **import** the library in your Python code:

```python
import requests

response = requests.get("https://www.example.com")
print("Response status code:", response.status_code)
```

- **`requests`** helps you make **HTTP requests** easily.
- There are **thousands** of libraries available on [PyPI (Python Package Index)](https://pypi.org/).

---

## 5. Creating Your Own Modules

You can also write your **own module**:
1. Create a new Python file, say `my_module.py`.
2. Define functions, classes, or variables in it.
3. Import it in another file.

```python
# my_module.py
def say_hello(name):
    return f"Hello, {name}!"

# main.py
import my_module

print(my_module.say_hello("Alice"))
# Output: Hello, Alice!
```

- This is a **great way** to organize your code into smaller pieces.

---

## 6. Exploring Popular Libraries

Here are a few popular libraries you might encounter or want to explore:

- **NumPy**: Advanced numerical operations, efficient arrays, and matrices.  
- **pandas**: Data manipulation and analysis.  
- **Matplotlib**: Data visualization (line graphs, bar charts, etc.).  
- **Flask**: A microframework for building simple web applications.  
- **Django**: A high-level framework for more complex web applications.  
- **TensorFlow**: Machine learning and deep learning tasks.

**Student Tip:** Practice installing, importing, and using at least one of these libraries to get a sense of how they work.

---

## 7. Exercises and Challenges

### Exercise 1  
Use the **math** module to calculate the **area of a circle** given its radius.  
- **Hint**: The formula for the area of a circle is \( \pi \times r^2 \). You can use `math.pi`.

### Exercise 2  
Install the **requests** library and write a program to fetch and print the current weather for a city using an **online weather API** (e.g., OpenWeatherMap).  
- **Hint**: You’ll need an API key. Research how to include query parameters (like `?q=London&appid=YOUR_KEY`) in your request.

### Challenge 1  
Create a function that uses **NumPy** to perform **matrix multiplication**.  
- **Hint**: Use `pip install numpy`, then `import numpy as np`.

### Challenge 2  
Build a simple **web application** using **Flask** that displays a `"Hello, World!"` message.  
- **Hint**: After installing Flask (`pip install flask`), write a simple Flask app:
  ```python
  from flask import Flask
  app = Flask(__name__)

  @app.route("/")
  def hello():
      return "Hello, World!"

  if __name__ == "__main__":
      app.run()
  ```

---

## Additional Practice Problems

1. **Random Password Generator**  
   - Use the `random` module to generate a random, secure password of a given length.  
   - Include a mix of uppercase, lowercase, digits, and special characters.

2. **Date and Time Logger**  
   - Use the `datetime` module to create a log function that prints messages with the current date and time.  
   - For example: `"[2024-01-01 12:00:00] - Process started"`.

3. **Simple Calculator Module**  
   - Create a custom module `calculator.py` with functions for add, subtract, multiply, and divide.  
   - Import the module in another Python file and demonstrate each function.

4. **CSV Data Analysis**  
   - Install and use **pandas** to read a CSV file. Print the first 5 rows and basic statistics about the data.  
   - For example, `.head()`, `.describe()` methods.

5. **Image Downloader**  
   - Use the `requests` library to download an image from a URL and save it to your local system.  
   - **Hint**: Open the file in binary mode (`'wb'`) to write the downloaded content.

---

## 8. Conclusion

- Python’s **modules** and **libraries** allow you to extend its functionality without writing everything from scratch.  
- The built-in modules provide a solid foundation for many tasks.  
- **External libraries** (installed via `pip`) unlock even more powerful and specialized capabilities.  
- You can **organize your own code** into modules to keep it clean and maintainable.

---

## Vocabulary Words and Definitions

- **Module**: A Python file containing code (functions, classes, variables) that can be imported.  
- **Library**: A collection of modules that provide additional functionality.  
- **Package Manager**: A tool (like `pip`) that installs, updates, and manages external libraries.  
- **External Library**: A library created by others, not included in the standard Python library.  
- **NumPy**: A library for numerical operations and efficient handling of arrays and matrices.  
- **pandas**: A library for data manipulation and analysis.  
- **Matplotlib**: A library for creating visualizations like plots and charts.  
- **Flask**: A lightweight web framework for building simple web applications.  
- **Django**: A high-level web framework that encourages rapid development.  
- **TensorFlow**: An open-source machine learning library developed by Google.

---

### Happy Coding!

Experiment with various modules and libraries—both built-in and external—to discover how they can simplify your tasks and help you achieve more in less time!
