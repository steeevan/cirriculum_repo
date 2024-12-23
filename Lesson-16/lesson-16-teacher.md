# Random Art Generator (Teacher’s Edition)

## Table of Contents
1. [Project Overview](#project-overview)  
2. [Section A: Setting Up the Turtle Screen](#section-a-setting-up-the-turtle-screen)  
3. [Section B: Basic Drawing Functions](#section-b-basic-drawing-functions)  
4. [Section C: Incorporating Randomness](#section-c-incorporating-randomness)  
5. [Section D: Optional Features (File Handling & Error Handling)](#section-d-optional-features-file-handling--error-handling)  
6. [Complete Code Example](#complete-code-example)  
7. [Additional Teaching Tips](#additional-teaching-tips)

---

## Project Overview

### Objective
Students will use:
- **Turtle** to create graphical output.
- **Random** to vary colors, positions, shapes, and angles for unpredictability.
- **Functions** to organize their code logically.
- (Optionally) **File Handling** and **Exception Handling** to load/save configurations or handle invalid inputs.

### End Result
Each run produces a **unique** artistic composition made up of randomly colored shapes (circles, squares, etc.) scattered around the Turtle screen.

### Key Skills Practiced
1. **Modular Programming**: Organizing code into functions.  
2. **Randomness**: Using `random.choice()`, `random.randint()`, etc.  
3. **Graphics**: Drawing with `turtle.Turtle()`.  
4. **(Optional) File Handling**: Reading/writing configuration files.  
5. **(Optional) Exception Handling**: Handling user input or file errors gracefully.

---

## Section A: Setting Up the Turtle Screen

### Objective
Configure the **Turtle** module’s screen, set background color, create a turtle for drawing, and optionally set size/speed.

### Detailed Solution
```python
import turtle

def setup_screen(width=800, height=600, bg_color="black"):
    """
    Sets up the turtle screen with given width, height, and background color.
    Returns the screen and turtle objects for further use.
    """
    # Create a Screen object
    screen = turtle.Screen()
    screen.setup(width=width, height=height)
    
    # Set background color
    screen.bgcolor(bg_color)
    
    # Create a Turtle object
    artist = turtle.Turtle()
    artist.speed("fast")  # Speed can be 'fast', 'fastest', or an integer
    artist.penup()        # Start with pen up to avoid accidental lines

    return screen, artist
```

#### Teacher Notes & Tips
- **Pen Up** initially? This can prevent stray lines if you move the turtle before drawing.  
- Encourage students to **experiment** with background colors and screen size.  
- **Error Check**: If `bg_color` is invalid, the turtle module might default to black (no crash).  

#### Additional Hints
- You can demonstrate different speeds (`"slow"`, `"normal"`, or numeric).  
- `penup()` vs. `pendown()`: Great to show how the turtle can reposition without drawing.  

---

## Section B: Basic Drawing Functions

### Objective
Write separate helper functions to draw shapes (e.g., squares, circles, stars, etc.). Each function has randomizable parameters (like side length or radius).

### Detailed Solution

```python
def draw_square(turtle_obj, side_length):
    """
    Draws a filled square using the given turtle object.
    side_length: The length of each side.
    """
    turtle_obj.begin_fill()
    for _ in range(4):
        turtle_obj.forward(side_length)
        turtle_obj.right(90)
    turtle_obj.end_fill()

def draw_circle(turtle_obj, radius):
    """
    Draws a filled circle with the given radius.
    """
    turtle_obj.begin_fill()
    turtle_obj.circle(radius)
    turtle_obj.end_fill()

def draw_star(turtle_obj, size):
    """
    Draws a simple 5-point star with the given size (influences the line length).
    """
    turtle_obj.begin_fill()
    for _ in range(5):
        turtle_obj.forward(size)
        turtle_obj.right(144)  # 144 degrees for a 5-point star
    turtle_obj.end_fill()
```

#### Teacher Notes & Tips
- Students often forget to **lift** the pen (`penup()`) or set it down (`pendown()`) if they want shapes in different locations.  
- `turtle_obj.right(144)` is a typical angle for a 5-point star, but experimenting with angles can produce other star-like shapes.
- **Filling** a shape: `begin_fill()` and `end_fill()` sandwich the shape’s outline, which is then filled with the current color.

#### Additional Hints
- Encourage students to create more shapes (triangles, pentagons, etc.) to see geometry in action.  
- They can also make a **spiral** function by combining forward movement with incremental turning.

---

## Section C: Incorporating Randomness

### Objective
Use the **Random** module to:
1. Choose random colors.
2. Jump turtle to random positions.
3. Randomly select which shape to draw and its size.

### Detailed Solution

```python
import random

def draw_random_art(turtle_obj, num_shapes=10):
    """
    Draws multiple random shapes on the screen.
    num_shapes: How many total shapes to draw.
    """
    colors = ["red", "green", "blue", "yellow", "purple", "orange", "pink"]
    shape_functions = [draw_square, draw_circle, draw_star]  # from Section B

    # We'll set the turtle's pen down only when drawing.
    for _ in range(num_shapes):
        # Random position
        rand_x = random.randint(-300, 300)
        rand_y = random.randint(-250, 250)
        
        turtle_obj.penup()
        turtle_obj.goto(rand_x, rand_y)
        turtle_obj.pendown()

        # Random color
        chosen_color = random.choice(colors)
        turtle_obj.color(chosen_color)

        # Random shape
        shape_func = random.choice(shape_functions)

        # Random size
        if shape_func == draw_square:
            size = random.randint(20, 80)
            shape_func(turtle_obj, size)
        elif shape_func == draw_circle:
            radius = random.randint(10, 60)
            shape_func(turtle_obj, radius)
        elif shape_func == draw_star:
            star_size = random.randint(20, 100)
            shape_func(turtle_obj, star_size)
```

#### Teacher Notes & Tips
- The range for `randint()` in `goto(rand_x, rand_y)` should be smaller than screen size (e.g., \(\pm 300\) for an 800-pixel wide screen).  
- Show how we’re reusing the shape functions from **Section B**.  
- Discuss using `random.choice()` for color selection, shape function, etc.

#### Additional Hints
- Encourage students to add **rotation** variations (e.g., `turtle_obj.left(random.randint(0, 359))` before drawing).  
- If too many shapes overlap, mention layering effects or changing transparency (which Turtle doesn’t natively support, but it's fun to discuss).

---

## Section D: Optional Features (File Handling & Error Handling)

### Objective
Add advanced features:
1. **File Handling**: Load a config file for color palettes, number of shapes, etc.  
2. **Exception Handling**: Tolerate invalid config or user inputs gracefully.

### Basic Example Code Snippet

```python
def read_config_file(filename):
    """
    Attempts to read a config file containing lines like:
        shapes=15
        colors=red,green,blue
    Returns a dictionary of parsed values or a default dictionary if file not found or invalid.
    """
    import os

    # Default config
    config = {"shapes": 10, "colors": "red,green,blue"}
    
    if not os.path.exists(filename):
        print("Config file not found. Using defaults.")
        return config
    
    try:
        with open(filename, "r") as f:
            for line in f:
                if "=" in line:
                    key, value = line.strip().split("=", 1)
                    config[key] = value
    except Exception as e:
        print(f"Error reading config file: {e}")
        print("Using defaults.")
    return config

def parse_colors(color_string):
    """
    Takes a comma-separated string of color names (e.g., "red,blue,yellow").
    Returns a list of color strings.
    """
    color_list = [c.strip() for c in color_string.split(",") if c.strip()]
    # If color_list is empty or invalid, fallback
    return color_list if color_list else ["black"]
```

#### Teacher Notes & Tips
- This is a **simple** approach to config parsing. Students can expand to JSON or other structured formats.  
- **Exception** might arise if the file format is wrong. We catch errors generally with `except Exception as e:`.  
- Encouraging students to handle specific exceptions (e.g., `FileNotFoundError`) can illustrate best practices.

#### Additional Hints
- Use a small file named `config.txt` with:
  ```
  shapes=20
  colors=red,blue,purple,yellow
  ```  
- Show how they can handle unknown color names by trying `turtle.color(color)` in a try-except block, defaulting if invalid.

---

## Complete Code Example

Below is a **comprehensive** sample that combines **Sections A, B, C**, and an optional snippet for **D**. Teachers can mix-and-match or simplify if desired.

```python
"""
Random Art Generator - Teacher's Edition
----------------------------------------
This script demonstrates how to combine Turtle graphics with random
choices in color, position, and shape to produce unique artwork.
"""

import turtle
import random
import os

# --------------- SECTION A: SETUP ---------------
def setup_screen(width=800, height=600, bg_color="black"):
    screen = turtle.Screen()
    screen.setup(width=width, height=height)
    screen.bgcolor(bg_color)

    artist = turtle.Turtle()
    artist.speed("fast")
    artist.penup()
    return screen, artist

# --------------- SECTION B: SHAPE FUNCTIONS ---------------
def draw_square(turtle_obj, side_length):
    turtle_obj.begin_fill()
    for _ in range(4):
        turtle_obj.forward(side_length)
        turtle_obj.right(90)
    turtle_obj.end_fill()

def draw_circle(turtle_obj, radius):
    turtle_obj.begin_fill()
    turtle_obj.circle(radius)
    turtle_obj.end_fill()

def draw_star(turtle_obj, size):
    turtle_obj.begin_fill()
    for _ in range(5):
        turtle_obj.forward(size)
        turtle_obj.right(144)
    turtle_obj.end_fill()

# --------------- SECTION C: RANDOM ART ---------------
def draw_random_art(turtle_obj, num_shapes=10, color_list=None):
    if color_list is None:
        color_list = ["red", "green", "blue", "yellow", "purple", "orange", "pink"]
    
    shape_functions = [draw_square, draw_circle, draw_star]

    for _ in range(num_shapes):
        rand_x = random.randint(-300, 300)
        rand_y = random.randint(-250, 250)

        turtle_obj.penup()
        turtle_obj.goto(rand_x, rand_y)
        turtle_obj.pendown()

        chosen_color = random.choice(color_list)
        turtle_obj.color(chosen_color)

        shape_func = random.choice(shape_functions)

        if shape_func == draw_square:
            size = random.randint(20, 80)
            shape_func(turtle_obj, size)
        elif shape_func == draw_circle:
            radius = random.randint(10, 60)
            shape_func(turtle_obj, radius)
        elif shape_func == draw_star:
            star_size = random.randint(20, 100)
            shape_func(turtle_obj, star_size)

# --------------- SECTION D (OPTIONAL): CONFIG HANDLING ---------------
def read_config_file(filename):
    default_config = {"shapes": 10, "colors": "red,green,blue"}
    if not os.path.isfile(filename):
        print("Config file not found. Using defaults.")
        return default_config
    
    config = default_config.copy()
    try:
        with open(filename, "r") as f:
            for line in f:
                if "=" in line:
                    key, val = line.strip().split("=", 1)
                    config[key] = val
    except Exception as e:
        print(f"Error reading config file '{filename}': {e}")
        print("Using defaults.")
    return config

def parse_colors(color_string):
    if not color_string:
        return ["red", "green", "blue"]
    return [c.strip() for c in color_string.split(",") if c.strip()]

# --------------- MAIN EXECUTION ---------------
def main():
    # 1. (Optional) Read config
    config = read_config_file("config.txt")
    num_shapes = int(config.get("shapes", 10))  # could raise ValueError if invalid
    color_list = parse_colors(config.get("colors", "red,green,blue"))
    
    # 2. Setup Screen
    screen, artist = setup_screen(bg_color="black")
    
    # 3. Draw random art
    try:
        # If num_shapes is negative or invalid, catch that error
        if num_shapes < 1:
            raise ValueError("num_shapes must be >= 1")
        draw_random_art(artist, num_shapes=num_shapes, color_list=color_list)
    except ValueError as e:
        print("Error in configuration:", e)
        print("Falling back to 10 shapes...")
        draw_random_art(artist, num_shapes=10, color_list=color_list)

    # 4. End - keep window open until user closes it
    turtle.done()

# Run the main if the script is executed directly
if __name__ == "__main__":
    main()
```

### Code Walkthrough
1. **Imports**:  
   - `turtle`, `random`, `os` for essential operations.
2. **Setup**: `setup_screen()` function for screen/turtle config.
3. **Shape Functions**: `draw_square()`, `draw_circle()`, `draw_star()`.
4. **Random Art**: `draw_random_art()` orchestrates random shape choice, color, and position.
5. **Config Handling**: `read_config_file()` and `parse_colors()` demonstrate simple file reading and parsing logic.  
6. **Main**:  
   - Reads config from `config.txt`.  
   - Grabs `num_shapes` and color list.  
   - Sets up screen with `setup_screen()`.  
   - Calls `draw_random_art()` in a try-except block to handle potential `ValueError`.  
   - Finishes with `turtle.done()` so the window stays open.

---

## Additional Teaching Tips

1. **Encourage Experimentation**:  
   - Let students tweak shape angles, color lists, and `num_shapes` to see drastically different outputs.
2. **Showcase Debugging**:  
   - Insert `print()` statements to confirm random values.  
   - Demonstrate how reading from a config might fail if the file is malformed.
3. **Encourage Creativity**:  
   - Students can add new shapes (e.g., polygons) or create swirling patterns with repeated turning.
4. **Discuss Performance**:  
   - If `num_shapes` is too high, Turtle might slow down. Talk about the cost of drawing vs. just computing.
5. **Extension**:  
   - Integrate **Time** delays (`import time`) to animate each shape being drawn in slow motion.  
   - Save final canvas as an image (requires additional libraries in many cases, but good to discuss).
6. **Assess Understanding**:  
   - Ask why using separate functions for each shape is beneficial.  
   - Have them explain how random choices are made and how `randint()` or `choice()` works.

---

**Happy Teaching and Creating!**  

With these explanations, code snippets, and tips, you have all the resources needed to guide students through building and extending a **Random Art Generator** that covers multiple Python fundamentals. This project is both visually engaging and a solid demonstration of organized, modular code.
