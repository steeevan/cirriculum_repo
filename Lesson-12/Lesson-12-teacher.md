# Teacher’s Edition: Modules and Libraries in Python

### **Objective:**  
Learn how to use built-in modules, install external libraries, and create your own modules to extend Python’s functionality.

---

## 1. Introduction to Modules and Libraries

- **Module**: A single file of Python code that can be imported into other programs.
- **Library**: A collection of modules providing a wide range of functionalities.

**Teaching Tips**:  
- Emphasize that modules and libraries let us reuse code someone else wrote.
- Showcase how they reduce development time and minimize errors.

---

## 2. Using Built-in Modules

```python
import math

sqrt_result = math.sqrt(25)
print("Square root of 25 is:", sqrt_result)  # Output: 5.0
```

**Teaching Tips**:  
- Demonstrate a few more `math` functions such as `math.pi` and `math.floor()`.
- Mention other built-in modules like `datetime` and `random`.

---

## 3. Installing External Libraries

```bash
pip install requests
```

- After installation, students can use `requests` in their Python scripts.

**Teaching Tips**:  
- Show students how to check if a library is successfully installed (`pip show requests`).
- Mention environments (like virtual environments) to avoid conflicts.

---

## 4. Using External Libraries

```python
import requests

response = requests.get("https://www.example.com")
print("Response status code:", response.status_code)
```

- **requests** simplifies making HTTP requests.

**Teaching Tips**:  
- Encourage students to explore other attributes like `response.text` or `response.json()` (for APIs).

---

## 5. Creating Your Own Modules

1. Create `my_module.py` with functions, classes, or variables.
2. Import it in another file using `import my_module`.

```python
# my_module.py
def say_hello(name):
    return f"Hello, {name}!"

# main.py
import my_module

print(my_module.say_hello("Alice"))  # "Hello, Alice!"
```

**Teaching Tips**:  
- Highlight how creating modules helps keep large projects organized.
- Mention naming conventions (lowercase letters, underscores).

---

## 6. Exploring Popular Libraries

- **NumPy**: Numerical operations, arrays, and matrices.  
- **pandas**: Data manipulation and analysis.  
- **Matplotlib**: Data visualization.  
- **Flask**: Lightweight web framework.  
- **Django**: High-level web framework.  
- **TensorFlow**: Machine learning and deep learning.

**Teaching Tips**:  
- Provide small code snippets using each library (e.g., basic NumPy array creation).
- Encourage independent exploration or mini-projects in class.

---

## 7. Exercises and Challenges (With **Solutions**)

Below are the exercises from the student edition, now with suggested solutions. Encourage students to explore alternative solutions or add extra features.

### Exercise 1  
**Prompt:** Use the **math** module to calculate the **area of a circle** given its radius.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
import math

def circle_area(radius):
    return math.pi * (radius ** 2)

# Example usage:
r = 5
print("Area of circle with radius 5:", circle_area(r))
```
**Explanation**:  
- We use `math.pi` for \(\pi\).  
- The area of a circle formula is \(\pi r^2\).
- This function returns the computed area.
</details>

---

### Exercise 2  
**Prompt:** Install the **requests** library and write a program to fetch and print the current weather for a city using an online weather API.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
import requests

def get_weather(city, api_key):
    base_url = "http://api.openweathermap.org/data/2.5/weather"
    # Example query: http://api.openweathermap.org/data/2.5/weather?q=London&appid=YOUR_KEY
    params = {
        "q": city,
        "appid": api_key,
        "units": "metric"  # for Celsius
    }
    response = requests.get(base_url, params=params)
    
    if response.status_code == 200:
        data = response.json()
        # Extract main weather info
        temperature = data["main"]["temp"]
        weather_desc = data["weather"][0]["description"]
        print(f"Current weather in {city}:")
        print(f"Temperature: {temperature}°C")
        print(f"Description: {weather_desc}")
    else:
        print(f"Failed to get weather data. Status code: {response.status_code}")

# Example usage:
# get_weather("London", "YOUR_API_KEY")
```

**Explanation**:  
- Students must sign up for a **free API key** (e.g., OpenWeatherMap).
- The `params` dictionary is passed to `requests.get` to build the query string.
- `response.json()` decodes the JSON payload into a Python dictionary.
</details>

---

### Challenge 1  
**Prompt:** Create a function that uses **NumPy** to perform **matrix multiplication**.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
import numpy as np

def matrix_multiply(A, B):
    """
    A and B are assumed to be 2D lists or NumPy arrays.
    """
    # Convert to NumPy arrays if they aren't already
    A_np = np.array(A)
    B_np = np.array(B)
    result = np.matmul(A_np, B_np)
    return result

# Example usage:
A = [[1, 2], [3, 4]]
B = [[5, 6], [7, 8]]
C = matrix_multiply(A, B)
print("Result of matrix multiplication:\n", C)
```

**Explanation**:  
- `np.array()` converts Python lists to NumPy arrays.
- `np.matmul()` performs matrix multiplication (\(A \times B\)).
- Students can experiment with shapes to ensure valid multiplication.
</details>

---

### Challenge 2  
**Prompt:** Build a simple **web application** using **Flask** that displays a `"Hello, World!"` message.

<details>
  <summary>Sample Solution & Explanation</summary>

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def hello():
    return "Hello, World!"

if __name__ == "__main__":
    app.run(debug=True)
```

**Explanation**:  
- `app = Flask(__name__)` creates a Flask application instance.
- The `@app.route("/")` decorator maps the root URL (`"/"`) to the `hello` function.
- `app.run(debug=True)` starts the development server (debug mode shows detailed error messages).
</details>

---

## Additional Practice Problems (With **Sample Solutions**)

1. **Random Password Generator**  
   **Prompt**: Use the `random` module to generate a random, secure password of a given length.

   <details>
     <summary>Sample Solution & Explanation</summary>

   ```python
   import random
   import string

   def generate_password(length=8):
       # Use uppercase, lowercase, digits, and punctuation
       chars = string.ascii_letters + string.digits + string.punctuation
       password = "".join(random.choice(chars) for _ in range(length))
       return password

   # Example usage:
   print("Generated password:", generate_password(12))
   ```
   **Explanation**:  
   - `string.ascii_letters` combines uppercase and lowercase letters.  
   - `random.choice(chars)` picks a random character from the pool.  
   - The password length defaults to 8 if no argument is given.
   </details>

2. **Date and Time Logger**  
   **Prompt**: Use the `datetime` module to create a log function that prints messages with the current date and time.

   <details>
     <summary>Sample Solution & Explanation</summary>

   ```python
   from datetime import datetime

   def log_message(message):
       current_time = datetime.now().strftime("%Y-%m-%d %H:%M:%S")
       print(f"[{current_time}] - {message}")

   # Example usage:
   log_message("Process started")
   log_message("Process finished")
   ```
   **Explanation**:  
   - `datetime.now()` retrieves the current local date and time.  
   - `.strftime(...)` formats it in a readable way.
   </details>

3. **Simple Calculator Module**  
   **Prompt**: Create a custom module `calculator.py` with functions for add, subtract, multiply, and divide.

   <details>
     <summary>Sample Solution & Explanation</summary>

   ```python
   # calculator.py
   def add(a, b):
       return a + b

   def subtract(a, b):
       return a - b

   def multiply(a, b):
       return a * b

   def divide(a, b):
       if b == 0:
           raise ValueError("Cannot divide by zero.")
       return a / b

   # main.py
   import calculator

   print("Add:", calculator.add(4, 5))
   print("Subtract:", calculator.subtract(10, 3))
   print("Multiply:", calculator.multiply(6, 7))
   print("Divide:", calculator.divide(8, 2))
   ```
   **Explanation**:  
   - Separate arithmetic functions are defined in `calculator.py`.  
   - A `ValueError` is raised to handle division by zero gracefully.
   </details>

4. **CSV Data Analysis**  
   **Prompt**: Install and use **pandas** to read a CSV file, then print the first 5 rows and basic statistics.

   <details>
     <summary>Sample Solution & Explanation</summary>

   ```python
   import pandas as pd

   def analyze_csv(filename):
       df = pd.read_csv(filename)
       print("First 5 rows:")
       print(df.head())
       print("\nSummary statistics:")
       print(df.describe())

   # Example usage:
   # analyze_csv("data.csv")
   ```
   **Explanation**:  
   - `pandas.read_csv(...)` loads a CSV file into a DataFrame.  
   - `.head()` shows the first 5 rows.  
   - `.describe()` shows mean, standard deviation, and other statistics.
   </details>

5. **Image Downloader**  
   **Prompt**: Use the `requests` library to download an image from a URL and save it to your local system.

   <details>
     <summary>Sample Solution & Explanation</summary>

   ```python
   import requests

   def download_image(url, filename):
       response = requests.get(url)
       if response.status_code == 200:
           with open(filename, 'wb') as file:
               file.write(response.content)
           print(f"Image saved as {filename}")
       else:
           print(f"Failed to download. Status code: {response.status_code}")

   # Example usage:
   # download_image("https://www.example.com/image.jpg", "my_image.jpg")
   ```
   **Explanation**:  
   - Use `response.content` to get binary data.  
   - Open the file in `'wb'` mode to write binary data.
   </details>

---

## 8. Conclusion

**Key Takeaways**:  
1. **Modules** and **libraries** let you reuse and organize code more effectively.  
2. The **standard library** has extensive functionality, but you can go even further by installing **external libraries** using `pip`.  
3. Creating your **own modules** helps maintain and structure larger projects.  
4. Popular libraries like **NumPy**, **pandas**, **Matplotlib**, **Flask**, etc., can drastically speed up development in their respective domains.

**Teacher Reminders**:  
- Encourage students to experiment with different libraries to discover how they can simplify tasks.  
- Remind them to keep dependencies and library versions in mind for compatibility.  
- Ask them to present small demonstrations on any external library they find interesting.

---

## Vocabulary Words and Definitions

- **Module**: A Python file containing definitions (functions, classes, variables) that can be imported.  
- **Library**: A collection of modules offering additional functionality.  
- **Package Manager**: A tool (like `pip`) for installing/updating external libraries.  
- **External Library**: A library not in the Python standard library (e.g., `requests`, `NumPy`).  
- **NumPy**: A library for numerical operations on arrays and matrices.  
- **pandas**: A library for data manipulation and analysis.  
- **Matplotlib**: A library for data visualization.  
- **Flask**: A micro web framework for simple web applications.  
- **Django**: A high-level web framework for faster, more complex web development.  
- **TensorFlow**: An open-source machine learning library from Google.

---

### Happy Teaching!

Use these solutions and explanations to guide your students. Encourage them to explore new libraries, share discoveries, and collaborate on projects that showcase the power of Python’s modules and libraries.
