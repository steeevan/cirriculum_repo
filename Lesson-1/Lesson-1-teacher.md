## 1. Introduction to Python Data Structures

In Python, there are several built-in data structures that allow you to store and manipulate data in diverse ways.

- **List**: An ordered collection of values that can be modified (**mutable**).
- **Tuple**: An ordered collection of values that cannot be changed after creation (**immutable**).
- **Dictionary**: A collection of **key-value** pairs for **efficient data retrieval**.
- **Set**: A collection of **unique** elements used for **deduplication** and **membership testing**.

### Teacher Notes
- Emphasize the differences in mutability (lists vs. tuples).
- Highlight the importance of **key-value** pairs in dictionaries for fast lookups.
- Stress that **sets** eliminate duplicates automatically and are great for membership checks.

---

## 2. Creating Lists and Tuples

### Lists
- Created using square brackets `[]`.
- Can contain elements of **any data type** (mixed data types are allowed).
- **Mutable**: You can add, remove, or change elements after creation.

```python
fruits_list = ["apple", "banana", "cherry"]
print(fruits_list)  
# Output: ['apple', 'banana', 'cherry']
```

### Tuples
- Created using parentheses `()`.
- **Immutable**: Once created, you **cannot** modify the elements.
  
```python
colors_tuple = ("red", "green", "blue")
print(colors_tuple)
# Output: ('red', 'green', 'blue')
```

### Teacher Notes
- Sometimes students forget to include the commas when creating tuples with a single element. For example, `(5,)` creates a tuple, whereas `(5)` is just an integer expression.

---

## 3. Accessing and Modifying Lists and Tuples

### Indexing
- Both lists and tuples use **zero-based indexing**.
- Access elements by specifying the index in brackets, e.g. `my_list[0]`, `my_tuple[1]`.

```python
fruits_list = ["apple", "banana", "cherry"]
first_fruit = fruits_list[0]
print(first_fruit)  
# Output: apple

colors_tuple = ("red", "green", "blue")
second_color = colors_tuple[1]
print(second_color)
# Output: green
```

### Modifying a List

```python
fruits_list = ["apple", "banana", "cherry"]
fruits_list[1] = "blueberry" 
print(fruits_list)
# Output: ['apple', 'blueberry', 'cherry']

# Appending a new element
fruits_list.append("dragonfruit")
print(fruits_list)
# Output: ['apple', 'blueberry', 'cherry', 'dragonfruit']
```

### Tuples Are Immutable

```python
colors_tuple = ("red", "green", "blue")
# colors_tuple[1] = "yellow"  # This will raise a TypeError because tuples are immutable
```

### Teacher Notes
- Reinforce the concept that lists can be modified at any point, but tuples cannot be changed after creation.
- Show how to create a new tuple if a “changed” version is needed (e.g., by concatenation or slicing).

---

## 4. Dictionary Operations

A **dictionary** in Python is a collection of **key-value** pairs. You can access and modify values using their keys.

```python
student = {
    "name": "Alice",
    "age": 25,
    "grade": "A"
}

# Access values
print(student["name"])  
# Output: Alice

# Modify values
student["age"] = 26
print(student)
# Output: {'name': 'Alice', 'age': 26, 'grade': 'A'}

# Add a new key-value pair
student["major"] = "Computer Science"
print(student)
# Output: {'name': 'Alice', 'age': 26, 'grade': 'A', 'major': 'Computer Science'}
```

### Teacher Notes
- Emphasize that dictionaries are **unordered** in Python versions < 3.7. In 3.7+, dictionaries **remember insertion order**, but conceptually, we often treat them as unordered.
- Show examples of dictionary methods like `.keys()`, `.values()`, and `.items()`.

---

## 5. Set Operations

A **set** in Python stores **unique** elements. Common operations include **union**, **intersection**, and **difference**.

```python
set1 = {1, 2, 3}
set2 = {3, 4, 5}

# Union - combines all unique elements from both sets
union_set = set1.union(set2)
print(union_set)
# Output: {1, 2, 3, 4, 5}

# Intersection - elements common to both sets
intersection_set = set1.intersection(set2)
print(intersection_set)
# Output: {3}

# Difference - elements in set1 but not in set2
difference_set = set1.difference(set2)
print(difference_set)
# Output: {1, 2}
```

### Teacher Notes
- Stress the fact that sets are **unordered**, which means there is no guarantee of the order of elements when printing.
- Another common set operation is `symmetric_difference`, which returns elements in either set but not both.

---

## 6. Additional Examples

### Example 1: Slicing Lists
You can slice lists using the `start:end` syntax (end index is **exclusive**).

```python
numbers_list = [1, 2, 3, 4, 5]
sliced_list = numbers_list[1:4]  
print(sliced_list)
# Output: [2, 3, 4]
```

### Example 2: Concatenating Lists
Lists can be added together using the `+` operator.

```python
list1 = [1, 2, 3]
list2 = [4, 5, 6]
combined_list = list1 + list2
print(combined_list)
# Output: [1, 2, 3, 4, 5, 6]
```

### Example 3: Creating a Set from a List
Converting a list to a set removes duplicate elements.

```python
fruits_list = ["apple", "banana", "cherry", "apple"]
unique_fruits = set(fruits_list)
print(unique_fruits)
# Output: {'banana', 'apple', 'cherry'} 
# (Order may vary as sets are unordered)
```

### Teacher Notes
- Remind students that slicing can also include optional start or end indexes (e.g., `numbers_list[:3]` or `numbers_list[2:]`).
- Demonstrate negative indexes (e.g., `numbers_list[-1]`).

---

## 7. Exercises (With **Solutions**)

Below are some exercises to practice and reinforce the concepts.

### Exercise 1
Create a program that takes a user's first name and last name as input and prints a personalized greeting.

**Sample Input**:
```
Enter your first name: Jane
Enter your last name: Doe
```
**Expected Output**:
```
Hello, Jane Doe! Welcome!
```

<details>
  <summary>**Solution Explanation**</summary>

1. Prompt the user to input their first name.
2. Prompt the user to input their last name.
3. Concatenate the strings to form a greeting.
4. Print the greeting.

```python
first_name = input("Enter your first name: ")
last_name = input("Enter your last name: ")

print(f"Hello, {first_name} {last_name}! Welcome!")
```
</details>

---

### Exercise 2
Given a list of numbers, create a set of unique numbers from the list.

**Example**:
```python
numbers = [1, 2, 2, 3, 4, 4, 4, 5]
# Expected output:
# {1, 2, 3, 4, 5}
```

<details>
  <summary>**Solution Explanation**</summary>

1. Convert the list to a set using the `set()` constructor.
2. Print the resulting set.

```python
numbers = [1, 2, 2, 3, 4, 4, 4, 5]
unique_numbers = set(numbers)
print(unique_numbers)
# Output: {1, 2, 3, 4, 5}
```
</details>

---

### Exercise 3
Write a program that counts and prints the frequency of each word in a given text.

**Example**:
```python
text = "apple banana apple cherry banana banana"
```
**Expected Output** (actual order may vary):
```
apple: 2
banana: 3
cherry: 1
```

<details>
  <summary>**Solution Explanation**</summary>

1. Split the text into words using `.split()`.
2. Iterate through each word and maintain a count in a dictionary.
3. Print the frequency of each word.

```python
text = "apple banana apple cherry banana banana"
words = text.split()
frequency_dict = {}

for word in words:
    if word in frequency_dict:
        frequency_dict[word] += 1
    else:
        frequency_dict[word] = 1

for word, count in frequency_dict.items():
    print(f"{word}: {count}")
```
</details>

---

## 8. Additional Practice Problems (With **Sample Solutions**)

1. **List Methods Practice**  
   - Create a list of numbers.  
   - Use `.append()`, `.pop()`, and `.remove()` to modify the list.  
   - Print the updated list after each operation.

   <details>
     <summary>Sample Solution</summary>

   ```python
   numbers = [10, 20, 30, 40, 50]
   print("Initial list:", numbers)

   # Append
   numbers.append(60)
   print("After append:", numbers)

   # Pop
   popped_item = numbers.pop()
   print(f"After pop (removed {popped_item}):", numbers)

   # Remove
   numbers.remove(30)
   print("After remove(30):", numbers)
   ```
   </details>

2. **Tuple Unpacking**  
   - Create a tuple containing four city names.  
   - Unpack the tuple into four separate variables and print them.

   <details>
     <summary>Sample Solution</summary>

   ```python
   cities_tuple = ("New York", "Paris", "Tokyo", "Sydney")
   city1, city2, city3, city4 = cities_tuple

   print(city1)  # New York
   print(city2)  # Paris
   print(city3)  # Tokyo
   print(city4)  # Sydney
   ```
   </details>

3. **Dictionary Methods**  
   - Create a dictionary containing student names as keys and their marks as values.  
   - Use `.keys()`, `.values()`, and `.items()` to iterate.  
   - Print each key and value pair.

   <details>
     <summary>Sample Solution</summary>

   ```python
   students_scores = {
       "Alice": 90,
       "Bob": 85,
       "Charlie": 92
   }

   print("Keys:", students_scores.keys())
   print("Values:", students_scores.values())
   print("Items:", students_scores.items())

   # Iterate over items
   for name, score in students_scores.items():
       print(f"{name} scored {score}")
   ```
   </details>

4. **Set Membership Testing**  
   - Create a set of colors (e.g., `{"red", "blue", "green"}`).  
   - Ask the user to input a color name.  
   - Check if the color is in the set and print an appropriate message.

   <details>
     <summary>Sample Solution</summary>

   ```python
   colors = {"red", "blue", "green"}
   user_color = input("Enter a color: ")

   if user_color.lower() in colors:
       print(f"{user_color} is in the set.")
   else:
       print(f"{user_color} is not in the set.")
   ```
   </details>

5. **Intersection and Difference**  
   - Create two sets of random numbers.  
   - Print their intersection and difference.  
   - Observe which elements are unique to each set and which are common.

   <details>
     <summary>Sample Solution</summary>

   ```python
   setA = {1, 3, 5, 7}
   setB = {3, 5, 9}

   print("Set A:", setA)
   print("Set B:", setB)

   intersection = setA.intersection(setB)
   difference = setA.difference(setB)

   print("Intersection:", intersection)
   # Output: {3, 5}
   print("Difference:", difference)
   # Output: {1, 7}
   ```
   </details>

---

## 9. Conclusion

In this lesson, we covered:

- **Lists**: Mutable, ordered collections.
- **Tuples**: Immutable, ordered collections.
- **Dictionaries**: Key-value data storage.
- **Sets**: Unique elements and set operations (union, intersection, difference).

**Key Takeaways**:
- Choose **lists** or **tuples** depending on whether you need to modify the data.
- Use **dictionaries** for fast lookups by keys.
- Use **sets** to avoid duplicates and for quick membership checks.

Encourage students to practice creating, modifying, and iterating over these data structures. Real-world scenarios often involve combining these data structures effectively.

---

## Vocabulary Words and Definitions

- **List**: An ordered collection of values that can be modified (**mutable**).
- **Tuple**: An ordered collection of values that is immutable (cannot be changed after creation).
- **Dictionary**: A collection of key-value pairs for efficient data retrieval.
- **Set**: A collection of unique elements used for deduplication and membership testing.

---

### Teacher’s Final Tips
- Prompt students to think about **time complexity** in real applications (e.g., dictionary and set lookups are on average O(1) time complexity).
- Encourage experimentation with nested data structures (lists within dictionaries, sets of tuples, etc.).
- Reinforce the concept of **immutability** by showing how tuples can be used as **dictionary keys** or **set elements**, but lists cannot.

**Happy Teaching and Coding!**
