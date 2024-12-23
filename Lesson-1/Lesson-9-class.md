## 1. Introduction to Python Data Structures

In Python, there are several built-in data structures that help organize and manipulate data in different ways:

- **List**: An ordered collection of values that can be modified (**mutable**).
- **Tuple**: An ordered collection of values that cannot be changed after creation (**immutable**).
- **Dictionary**: A collection of **key-value** pairs for **efficient data retrieval**.
- **Set**: A collection of **unique** elements used for **deduplication** and **membership testing**.

---

## 2. Creating Lists and Tuples

### Lists
- Created using square brackets `[]`.
- Can contain elements of different data types (e.g., strings, integers, floats, etc.).
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

---

## 3. Accessing and Modifying Lists and Tuples

### Indexing
- Both lists and tuples use **zero-based indexing**.
- Access elements by specifying the index in brackets.

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

# Add new key-value pairs
student["major"] = "Computer Science"
print(student)
# Output: {'name': 'Alice', 'age': 26, 'grade': 'A', 'major': 'Computer Science'}
```

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

---

## 6. Additional Examples

### Example 1: Slicing Lists
You can slice lists using the `start:end` syntax (end index is exclusive).

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

---

## 7. Exercises

Below are some exercises to practice and reinforce what you've learned.

### Exercise 1
Create a program that takes a user's first name and last name as input and prints a personalized greeting.

**Example**:
```
Enter your first name: Jane
Enter your last name: Doe
```
**Output**:
```
Hello, Jane Doe! Welcome!
```

### Exercise 2
Given a list of numbers, create a set of unique numbers from the list.

**Example**:
```python
numbers = [1, 2, 2, 3, 4, 4, 4, 5]
# Your code here
# Expected output:
# {1, 2, 3, 4, 5}
```

### Exercise 3
Write a program that counts and prints the frequency of each word in a given text.

**Example**:
```python
text = "apple banana apple cherry banana banana"
# Your code here
# Expected output (frequency might vary based on your approach):
# apple: 2
# banana: 3
# cherry: 1
```

---

## 8. Additional Practice Problems

Here are some more exercises to deepen your understanding:

1. **List Methods Practice**  
   - Create a list of numbers.
   - Use the `.append()`, `.pop()`, and `.remove()` methods to modify the list.
   - Print the updated list after each operation.

2. **Tuple Unpacking**  
   - Create a tuple containing four city names.
   - Unpack the tuple into four separate variables and print them.

3. **Dictionary Methods**  
   - Create a dictionary containing student names as keys and their marks as values.
   - Use the `.keys()`, `.values()`, and `.items()` methods to iterate over the dictionary.
   - Print out each key and value pair.

4. **Set Membership Testing**  
   - Create a set of colors (e.g., `{"red", "blue", "green"}`).
   - Ask the user to input a color name.
   - Check if the color is in the set and print an appropriate message.

5. **Intersection and Difference**  
   - Create two sets of random numbers.
   - Print their intersection and difference.
   - Observe what elements are unique to each set and which are common.

---

## 9. Conclusion

In this lesson, you've learned:
- How to **create** and **manipulate** **Lists** (mutable, ordered collections).
- How to work with **Tuples** (immutable, ordered collections).
- How to use **Dictionaries** for key-value data storage.
- How to use **Sets** for storing unique elements and performing set operations.

By practicing these concepts, you’ll improve your data manipulation skills in Python and gain a deeper understanding of how to choose the right data structure for different tasks.

---

## Vocabulary Words and Definitions

- **List**: An ordered collection of values that can be modified (**mutable**).
- **Tuple**: An ordered collection of values that is immutable (cannot be changed after creation).
- **Dictionary**: A collection of key-value pairs for efficient data retrieval.
- **Set**: A collection of unique elements used for deduplication and membership testing.

---

### Happy Learning and Coding!

Feel free to adapt this lesson to your specific learning needs and add more exercises if you want to continue exploring these powerful Python data structures.
