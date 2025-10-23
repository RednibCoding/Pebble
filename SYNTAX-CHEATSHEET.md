# Pebble Syntax Cheatsheet

A quick reference for Pebble's syntax and core features.

## Comments

```pebble
# Single-line comment

## Documentation comment (used for hover info)
```

## Variables

```pebble
let x = 42                    # Immutable by default
let name = "Alice"
let pi = 3.14159
let flag = true
let nothing = nil
```

## Operators

```pebble
# Arithmetic
+ - * / %

# Comparison
== != < > <= >=

# Logical
and or not

# String concatenation
"Hello" + " " + "World"
```

## Control Flow

```pebble
# If-else
if condition:
    # code
elif other_condition:
    # code
else:
    # code
end

# While loop
while condition:
    # code
end
```

## Functions

```pebble
# Basic function
def greet(name):
    return "Hello, " + name
end

# Multiple parameters
def add(a, b):
    return a + b
end

# No return value
def print_info(msg):
    io_print(msg)
end
```

## Arrays

```pebble
# Creation
let numbers = [1, 2, 3, 4, 5]
let empty = []

# Multiline
let items = [
    "apple",
    "banana",
    "cherry",
]

# Access and modification
numbers[0]              # Get first element
numbers[2] = 99         # Set element

# Built-in functions
array_push(arr, value)
array_pop(arr)
array_insert(arr, index, value)
array_remove(arr, index)
type_len(arr)           # Get length
```

## Maps

```pebble
# Creation
let person = {
    "name": "Alice",
    "age": 30,
    "city": "Berlin"
}

let empty = {}

# Access and modification
person["name"]          # Get value
person["age"] = 31      # Set value
person["job"] = "Dev"   # Add new key

# Built-in functions
map_keys(map)
map_values(map)
map_has_key(map, key)
map_delete(map, key)
type_len(map)           # Get size
```

## Records (Structs)

```pebble
# Definition
record Point:
    field x
    field y
end

# Usage with type annotation (required for records)
let p: Point = Point
p.x = 10
p.y = 20

# Nested records
record Circle:
    field center: Point   # Type annotation enables nested access
    field radius
end

let c: Circle = Circle
c.center = p
c.radius = 50
io_print(c.center.x)      # Nested access

# Functions with record parameters
def distance(p1: Point, p2: Point):
    let dx = p2.x - p1.x
    let dy = p2.y - p1.y
    return dx * dx + dy * dy
end
```

## Strings

```pebble
# Creation
let text = "Hello, World!"
let multiline = "Line 1\nLine 2"

# Built-in functions
type_len(str)                           # String length
string_char_at(str, index)              # Get character at index
string_substr(str, start, end)          # Substring (end optional)
string_index_of(str, substr)            # Find first occurrence (-1 if not found)
string_upper(str)                       # Convert to uppercase
string_lower(str)                       # Convert to lowercase
string_split(str, delimiter)            # Split into array
string_join(arr, separator)             # Join array into string
string_replace(str, old, new)           # Replace all occurrences
string_contains(str, substr)            # Check if contains substring
string_starts_with(str, prefix)         # Check if starts with prefix
string_ends_with(str, suffix)           # Check if ends with suffix
```

## Type Checking & Conversion

```pebble
# Type checking
typeof(value)           # Returns the type name: "int", "float", "string", etc.
type_len(collection)    # Length of array/map/string

# Conversion
type_int(value)         # Convert to integer
type_float(value)       # Convert to float
type_str(value)         # Convert to string
```

## I/O

```pebble
# Console output
io_print("Hello")
io_print("x =", x, "y =", y)

# File operations
file_read_file("path.txt")              # Read entire file as string
file_write_file("path.txt", content)    # Write to file (overwrite)
file_append_file("path.txt", content)   # Append to file
file_exists("path.txt")                 # Check if file exists
file_delete_file("path.txt")            # Delete a file
file_read_lines("path.txt")             # Read file as array of lines

# Directory operations
file_list_dir(".")                      # List files in directory
file_is_dir("path")                     # Check if path is directory
file_make_dir("newdir")                 # Create directory
file_make_dir_all("path/to/dir")        # Create nested directories
file_get_cwd()                          # Get current working directory
```

## Collision Detection

```pebble
# Point-shape collision
collision_point_in_rect(px, py, rx, ry, rw, rh)      # Point in rectangle
collision_point_in_circle(px, py, cx, cy, radius)    # Point in circle

# Shape-shape collision
collision_rect_rect(x1, y1, w1, h1, x2, y2, w2, h2)  # AABB rectangle collision
collision_circle_circle(x1, y1, r1, x2, y2, r2)      # Circle overlap
collision_rect_circle(rx, ry, rw, rh, cx, cy, r)     # Rectangle-circle collision

# Math helpers
math_distance(x1, y1, x2, y2)                        # Distance between points
math_angle(x1, y1, x2, y2)                           # Angle in radians
math_lerp(start, end, t)                             # Linear interpolation
math_normalize(x, y)                                 # Returns [nx, ny] array
math_clamp(value, min, max)                          # Clamp to range
```

## JSON

```pebble
# Parse JSON string to Pebble value
let data = json_parse('{"name": "Alice", "age": 30}')
io_print(data["name"])

# Convert Pebble value to JSON string
let obj = {"x": 10, "y": 20}
let json_str = json_stringify(obj)
io_print(json_str)      # {"x": 10, "y": 20}
```

## Imports

```pebble
# Import from same directory
import "helper"

# Import from subdirectory
import "utils/math"

# Import from parent directory
import "../shared/config"

# Use imported functions
let result = helper_function()
```

## Key Features

- **No for loops**: Use `while` loops with manual indexing
- **No closures**: Functions cannot capture outer scope variables
- **Records need type annotations**: Required for field access inference
- **String-only map keys**: Maps use string keys only
- **O(1) operations**: Arrays (index access), Maps (key lookup), Records (field access)
- **Garbage collected**: Automatic memory management
- **Pass-by-value semantics**: Collections are reference types

## Quick Example

```pebble
## Calculate distance between two points
record Point:
    field x
    field y
end

def distance(p1: Point, p2: Point):
    let dx = p2.x - p1.x
    let dy = p2.y - p1.y
    return (dx * dx + dy * dy) ** 0.5
end

let a: Point = Point
a.x = 0
a.y = 0

let b: Point = Point
b.x = 3
b.y = 4

let dist = distance(a, b)
io_print("Distance:", dist)  # Distance: 5
```
