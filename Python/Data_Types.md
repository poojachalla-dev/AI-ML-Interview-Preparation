# Python Data Types Interview Questions & Answers (1–25)

## Numbers

### 1. What are Python's numeric data types?

**Answer:**
Python provides three main numeric types:

* `int` – Integer values
* `float` – Floating-point values
* `complex` – Complex numbers

Example:

```python
x = 10
y = 3.14
z = 2 + 3j
```

---

### 2. What is the difference between int and float?

**Answer:**

* `int` stores whole numbers.
* `float` stores decimal numbers.

Example:

```python
a = 10
b = 10.5
```

Key Point: Floats use more memory and may introduce precision errors.

---

### 3. How are integers stored internally in Python?

**Answer:**
Python integers are objects. Unlike C/C++, Python integers can grow dynamically and are not limited to fixed sizes like 32-bit or 64-bit integers.

Example:

```python
x = 999999999999999999999999999999
```

Python allocates additional memory as needed.

---

### 4. What is arbitrary precision integer support?

**Answer:**
Python integers can grow to virtually any size limited only by available memory.

Example:

```python
x = 10 ** 1000
```

This capability is called arbitrary precision arithmetic.

---

### 5. What is the difference between float and decimal?

**Answer:**

| float                         | Decimal                                 |
| ----------------------------- | --------------------------------------- |
| Faster                        | More precise                            |
| Binary representation         | Decimal representation                  |
| May introduce rounding errors | Designed for exact decimal calculations |

Example:

```python
from decimal import Decimal

Decimal("0.1") + Decimal("0.2")
```

---

### 6. Why do floating-point precision errors occur?

**Answer:**
Computers store floating-point numbers in binary format. Some decimal values cannot be represented exactly in binary.

Example:

```python
0.1 + 0.2
```

Output:

```python
0.30000000000000004
```

---

### 7. What is the Decimal module?

**Answer:**
The Decimal module provides exact decimal arithmetic.

Example:

```python
from decimal import Decimal

result = Decimal("0.1") + Decimal("0.2")
```

Useful for financial applications.

---

### 8. What is the Fraction module?

**Answer:**
The Fraction module represents rational numbers exactly.

Example:

```python
from fractions import Fraction

Fraction(1, 3)
```

Useful when exact fractions are required.

---

### 9. What is complex data type in Python?

**Answer:**
Complex numbers contain a real and imaginary component.

Example:

```python
z = 3 + 4j
```

Real part:

```python
z.real
```

Imaginary part:

```python
z.imag
```

---

### 10. How do you perform arithmetic with complex numbers?

**Answer:**

Example:

```python
a = 2 + 3j
b = 1 + 2j

print(a + b)
print(a - b)
print(a * b)
print(a / b)
```

Python supports all standard arithmetic operations on complex numbers.

---

## Strings

### 11. What is a string in Python?

**Answer:**
A string is an immutable sequence of Unicode characters.

Example:

```python
name = "Python"
```

---

### 12. Why are strings immutable?

**Answer:**
Immutability improves:

* Performance
* Memory optimization
* Thread safety
* Hashability

Once created, a string cannot be modified.

---

### 13. What are the advantages of immutable strings?

**Answer:**

* Safe to use as dictionary keys
* Memory efficient
* Thread-safe
* Easier caching and optimization

---

### 14. What is string interning?

**Answer:**
String interning is an optimization where identical strings share the same memory location.

Example:

```python
a = "hello"
b = "hello"

a is b
```

Often returns:

```python
True
```

---

### 15. What is the difference between str and bytes?

**Answer:**

| str             | bytes            |
| --------------- | ---------------- |
| Unicode text    | Raw binary data  |
| Human-readable  | Machine-oriented |
| Uses characters | Uses byte values |

Example:

```python
text = "hello"
data = b"hello"
```

---

### 16. What is Unicode?

**Answer:**
Unicode is a universal standard for representing characters from different languages and writing systems.

Example:

```python
"こんにちは"
"नमस्ते"
```

---

### 17. What is UTF-8 encoding?

**Answer:**
UTF-8 is the most widely used Unicode encoding format.

Features:

* Variable length
* Backward compatible with ASCII
* Efficient storage

---

### 18. What is the difference between encode() and decode()?

**Answer:**

`encode()`

Converts string → bytes

```python
text = "hello"
text.encode()
```

`decode()`

Converts bytes → string

```python
data = b"hello"
data.decode()
```

---

### 19. How are strings stored internally?

**Answer:**
Python stores strings as immutable Unicode objects.

Modern Python optimizes storage based on the character set used.

Benefits:

* Reduced memory consumption
* Faster access

---

### 20. What is slicing in Python?

**Answer:**
Slicing extracts a portion of a sequence.

Syntax:

```python
sequence[start:stop:step]
```

Example:

```python
text = "Python"

text[0:3]
```

Output:

```python
Pyt
```

---

### 21. Explain string indexing.

**Answer:**
Indexing accesses individual characters.

Example:

```python
text = "Python"

text[0]
```

Output:

```python
P
```

---

### 22. What is negative indexing?

**Answer:**
Negative indices count from the end.

Example:

```python
text = "Python"

text[-1]
```

Output:

```python
n
```

---

### 23. What is the difference between find() and index()?

**Answer:**

| find()                  | index()                             |
| ----------------------- | ----------------------------------- |
| Returns -1 if not found | Raises ValueError                   |
| Safer for searches      | Useful when existence is guaranteed |

Example:

```python
"Python".find("x")
```

Returns:

```python
-1
```

---

### 24. What is the difference between split() and partition()?

**Answer:**

`split()`

* Returns a list
* Splits all occurrences

Example:

```python
"a,b,c".split(",")
```

`partition()`

* Returns a tuple
* Splits only first occurrence

Example:

```python
"a,b,c".partition(",")
```

---

### 25. What is the difference between join() and concatenation?

**Answer:**

Concatenation:

```python
a + b
```

Join:

```python
",".join(items)
```

`join()` is preferred when combining many strings because it is significantly more efficient than repeated concatenation.

---

## Strings

### 26. Why is `join()` faster than repeated string concatenation?

**Answer:**
Strings are immutable. Every concatenation creates a new string object, requiring memory allocation and copying. `join()` calculates the required memory once and builds the final string efficiently.

Example:

```python
words = ["Python", "is", "awesome"]
result = " ".join(words)
```

### Key Interview Point

Use `join()` when combining many strings.

---

### 27. What is a raw string?

**Answer:**
A raw string treats backslashes (`\`) as literal characters and does not process escape sequences.

Example:

```python
path = r"C:\Users\Pooh\Documents"
```

### Key Interview Point

Useful for file paths and regular expressions.

---

### 28. What is an f-string?

**Answer:**
An f-string (formatted string literal) allows embedding expressions inside strings.

Example:

```python
name = "Pooh"
print(f"Hello, {name}")
```

Output:

```python
Hello, Pooh
```

### Key Interview Point

Introduced in Python 3.6 and is the preferred formatting method.

---

### 29. What are formatted string literals?

**Answer:**
Formatted string literals are strings prefixed with `f` that evaluate expressions at runtime.

Example:

```python
age = 22
print(f"Age: {age}")
```

### Key Interview Point

Supports expressions, formatting, and calculations directly inside strings.

---

### 30. What are common string methods?

**Answer:**

Common methods include:

```python
upper()
lower()
strip()
replace()
split()
join()
find()
count()
startswith()
endswith()
```

Example:

```python
text = "python"
text.upper()
```

Output:

```python
PYTHON
```

---

# Lists

### 31. What is a list?

**Answer:**
A list is an ordered, mutable collection that can store heterogeneous data types.

Example:

```python
items = [1, "Python", 3.14]
```

### Key Interview Point

Lists allow duplicates and preserve insertion order.

---

### 32. Why are lists mutable?

**Answer:**
Lists are designed for dynamic data manipulation. Elements can be added, removed, or modified without creating a new object.

Example:

```python
nums = [1, 2]
nums.append(3)
```

---

### 33. How are lists stored internally?

**Answer:**
Python lists are implemented as dynamic arrays containing references to objects.

### Key Interview Point

Elements may be stored in different memory locations, while the list stores references.

---

### 34. What is dynamic array implementation?

**Answer:**
A dynamic array automatically resizes when capacity is exceeded.

When a list grows:

1. New memory is allocated.
2. Existing references are copied.
3. Old memory is released.

### Key Interview Point

Provides efficient append operations.

---

### 35. What is list resizing?

**Answer:**
When a list reaches capacity, Python allocates additional space and copies existing elements.

### Key Interview Point

Resizing is expensive but happens infrequently, making average append operations efficient.

---

### 36. What is the time complexity of `append()`?

**Answer:**

Average Case:

```text
O(1)
```

Worst Case:

```text
O(n)
```

when resizing occurs.

### Key Interview Point

Append is amortized O(1).

---

### 37. What is the time complexity of `insert()`?

**Answer:**

```text
O(n)
```

because elements may need to be shifted.

Example:

```python
nums.insert(0, 100)
```

---

### 38. What is the time complexity of `remove()`?

**Answer:**

```text
O(n)
```

because Python must search for the element and shift remaining elements.

Example:

```python
nums.remove(5)
```

---

### 39. What is the difference between `append()` and `extend()`?

**Answer:**

`append()` adds a single object.

```python
lst = [1, 2]
lst.append([3, 4])

# [1, 2, [3, 4]]
```

`extend()` adds elements individually.

```python
lst = [1, 2]
lst.extend([3, 4])

# [1, 2, 3, 4]
```

---

### 40. What is the difference between `remove()` and `pop()`?

**Answer:**

| remove()         | pop()                |
| ---------------- | -------------------- |
| Removes by value | Removes by index     |
| Returns nothing  | Returns removed item |

Example:

```python
lst.remove(3)
lst.pop(0)
```

---

### 41. What is list comprehension?

**Answer:**
A concise way to create lists.

Example:

```python
squares = [x*x for x in range(5)]
```

Output:

```python
[0, 1, 4, 9, 16]
```

### Key Interview Point

Often faster and more readable than loops.

---

### 42. What are nested list comprehensions?

**Answer:**
List comprehensions inside another list comprehension.

Example:

```python
matrix = [[i*j for j in range(3)] for i in range(3)]
```

### Key Interview Point

Useful for matrix operations.

---

### 43. What is the difference between list comprehension and `map()`?

**Answer:**

List Comprehension:

```python
[x*x for x in nums]
```

Map:

```python
list(map(lambda x: x*x, nums))
```

### Key Interview Point

List comprehensions are generally more Pythonic and readable.

---

### 44. What is the difference between list comprehension and generator expression?

**Answer:**

List Comprehension:

```python
[x*x for x in nums]
```

Generator Expression:

```python
(x*x for x in nums)
```

### Key Interview Point

| List                | Generator               |
| ------------------- | ----------------------- |
| Stores all values   | Generates values lazily |
| Higher memory usage | Lower memory usage      |

---

### 45. How do shallow copies affect lists?

**Answer:**
A shallow copy creates a new list but shares references to nested objects.

Example:

```python
import copy

a = [[1, 2]]
b = copy.copy(a)
```

Changing nested objects affects both lists.

---

### 46. How do deep copies affect lists?

**Answer:**
A deep copy recursively copies all nested objects.

Example:

```python
import copy

a = [[1, 2]]
b = copy.deepcopy(a)
```

Changes remain independent.

---

### 47. What is list unpacking?

**Answer:**
Assigning list elements directly to variables.

Example:

```python
nums = [1, 2, 3]

a, b, c = nums
```

---

### 48. What is sequence unpacking?

**Answer:**
Extracting elements from any iterable into variables.

Example:

```python
name, age = ("Pooh", 22)
```

Works with:

* Lists
* Tuples
* Strings
* Sets

---

### 49. What is starred expression (`*`) unpacking?

**Answer:**
The `*` operator collects multiple values into a list.

Example:

```python
a, *b = [1, 2, 3, 4]
```

Result:

```python
a = 1
b = [2, 3, 4]
```

### Key Interview Point

Useful when the number of elements is unknown.

---

### 50. What are common list operations?

**Answer:**

Adding:

```python
append()
extend()
insert()
```

Removing:

```python
remove()
pop()
clear()
```

Searching:

```python
index()
count()
```

Sorting:

```python
sort()
reverse()
```

Copying:

```python
copy()
```

### Key Interview Point

Lists are one of the most commonly used Python data structures and understanding their operations and complexities is essential for interviews.

---

# Tuples

### 51. What is a tuple?

**Answer:**
A tuple is an ordered, immutable collection of elements. It can store heterogeneous data types and allows duplicate values.

Example:

```python
person = ("Pooh", 22, "AI Engineer")
```

### Key Interview Point

Tuples are faster and more memory-efficient than lists when data should not change.

---

### 52. Why are tuples immutable?

**Answer:**
Tuples are immutable to provide:

* Data integrity
* Hashability
* Better performance
* Thread safety

Once created, elements cannot be modified.

Example:

```python
t = (1, 2, 3)
# t[0] = 10  # TypeError
```

---

### 53. What are the advantages of tuples?

**Answer:**

* Faster than lists
* Less memory usage
* Hashable (if all elements are hashable)
* Can be used as dictionary keys
* Safer for fixed data

---

### 54. When should tuples be preferred over lists?

**Answer:**
Use tuples when:

* Data should not change
* Performance matters
* Using keys in dictionaries
* Returning multiple values from functions

Example:

```python
coordinates = (10, 20)
```

---

### 55. How are tuples stored internally?

**Answer:**
Tuples are stored as fixed-size arrays of object references.

Since size cannot change after creation:

* No resizing overhead
* Better memory efficiency
* Faster access

---

### 56. What is tuple packing?

**Answer:**
Packing means placing multiple values into a tuple.

Example:

```python
person = "Pooh", 22, "Engineer"
```

Equivalent to:

```python
person = ("Pooh", 22, "Engineer")
```

---

### 57. What is tuple unpacking?

**Answer:**
Unpacking assigns tuple elements directly to variables.

Example:

```python
person = ("Pooh", 22)

name, age = person
```

Result:

```python
name = "Pooh"
age = 22
```

---

### 58. Can a tuple contain mutable objects?

**Answer:**
Yes.

Example:

```python
t = (1, [2, 3], 4)
```

The tuple itself is immutable, but the list inside it can be modified.

---

### 59. Why can a tuple containing a list still change?

**Answer:**
The tuple's reference to the list cannot change, but the list object itself remains mutable.

Example:

```python
t = (1, [2, 3])

t[1].append(4)
```

Result:

```python
(1, [2, 3, 4])
```

---

### 60. What are named tuples?

**Answer:**
Named tuples provide field names for tuple elements.

Example:

```python
from collections import namedtuple

Person = namedtuple("Person", ["name", "age"])

p = Person("Pooh", 22)
```

Access:

```python
p.name
p.age
```

### Key Interview Point

Named tuples combine tuple efficiency with object-like readability.

---

# Sets

### 61. What is a set?

**Answer:**
A set is an unordered collection of unique elements.

Example:

```python
nums = {1, 2, 3}
```

Duplicate values are automatically removed.

---

### 62. Why are sets unordered?

**Answer:**
Sets are implemented using hash tables.

Elements are placed according to hash values rather than insertion position.

### Key Interview Point

Ordering is not guaranteed.

---

### 63. How are sets implemented internally?

**Answer:**
Sets are implemented using hash tables.

Each element:

1. Is hashed.
2. Stored according to hash value.
3. Allows fast lookup.

### Key Interview Point

Membership testing is usually O(1).

---

### 64. What is hashing?

**Answer:**
Hashing converts an object into an integer hash value.

Example:

```python
hash("Python")
```

Hash values are used in:

* Sets
* Dictionaries

---

### 65. What is a hash table?

**Answer:**
A hash table stores data using hash values as lookup indices.

Benefits:

* Fast lookup
* Fast insertion
* Fast deletion

Average complexity:

```text
O(1)
```

---

### 66. Why are sets faster than lists for membership testing?

**Answer:**

List lookup:

```text
O(n)
```

Set lookup:

```text
O(1)
```

Example:

```python
100 in my_set
```

Python directly computes the hash and locates the element.

---

### 67. What is the difference between set and frozenset?

**Answer:**

| set                  | frozenset     |
| -------------------- | ------------- |
| Mutable              | Immutable     |
| Hashable? No         | Yes           |
| Can add/remove items | Cannot modify |

Example:

```python
s = frozenset([1, 2, 3])
```

---

### 68. What are set union, intersection, and difference operations?

**Answer:**

Union:

```python
a | b
```

Intersection:

```python
a & b
```

Difference:

```python
a - b
```

Example:

```python
a = {1, 2, 3}
b = {3, 4, 5}
```

Results:

```python
a | b  # {1,2,3,4,5}
a & b  # {3}
a - b  # {1,2}
```

---

### 69. What is a hash collision?

**Answer:**
A collision occurs when two different objects produce the same hash value.

Example:

```text
hash(obj1) == hash(obj2)
```

even though:

```text
obj1 != obj2
```

---

### 70. How does Python handle hash collisions?

**Answer:**
Python uses collision resolution techniques internally.

When collisions occur:

1. Compare hash values.
2. Probe alternative locations.
3. Verify actual object equality.

### Key Interview Point

Collisions do not break dictionaries or sets.

---

# Dictionaries

### 71. What is a dictionary?

**Answer:**
A dictionary is a collection of key-value pairs.

Example:

```python
student = {
    "name": "Pooh",
    "age": 22
}
```

---

### 72. How are dictionaries implemented internally?

**Answer:**
Python dictionaries are implemented using hash tables.

Each key:

1. Is hashed.
2. Maps to a memory location.
3. Retrieves values efficiently.

### Key Interview Point

Average lookup complexity is O(1).

---

### 73. What is key-value mapping?

**Answer:**
A dictionary associates unique keys with values.

Example:

```python
employee = {
    "id": 101,
    "name": "Pooh"
}
```

Keys identify values uniquely.

---

### 74. Why must dictionary keys be hashable?

**Answer:**
Dictionary lookup relies on hashing.

Only immutable objects can provide stable hash values.

Examples of hashable types:

```python
int
float
str
tuple
frozenset
```

---

### 75. What types can be used as dictionary keys?

**Answer:**

Valid keys:

```python
1
3.14
"Python"
(True)
(1, 2)
frozenset([1, 2])
```

### Key Interview Point

Keys must be:

* Immutable
* Hashable
* Consistent throughout their lifetime

---

# Dictionaries

### 76. Why can't lists be dictionary keys?

**Answer:**
Dictionary keys must be hashable. Lists are mutable, meaning their contents can change after creation. If a list were used as a key and then modified, its hash value would change, making dictionary lookups unreliable.

Example:

```python
# TypeError
d = {
    [1, 2]: "value"
}
```

### Key Interview Point

Mutable objects are generally not hashable and cannot be dictionary keys.

---

### 77. What is dictionary comprehension?

**Answer:**
Dictionary comprehension provides a concise way to create dictionaries.

Example:

```python
squares = {x: x*x for x in range(5)}
```

Output:

```python
{
    0: 0,
    1: 1,
    2: 4,
    3: 9,
    4: 16
}
```

### Key Interview Point

Dictionary comprehensions improve readability and reduce boilerplate code.

---

### 78. What is the difference between `get()` and `[]` access?

**Answer:**

Using `[]`:

```python
student["age"]
```

Raises `KeyError` if the key is missing.

Using `get()`:

```python
student.get("age")
```

Returns `None` by default if the key is missing.

Example:

```python
student.get("age", 0)
```

### Key Interview Point

Use `get()` when a missing key is possible.

---

### 79. What is `defaultdict`?

**Answer:**
`defaultdict` is a dictionary subclass from the `collections` module that automatically provides default values for missing keys.

Example:

```python
from collections import defaultdict

d = defaultdict(int)

d["count"] += 1
```

Output:

```python
{'count': 1}
```

### Key Interview Point

Eliminates the need for manual key existence checks.

---

### 80. What is `OrderedDict`?

**Answer:**
`OrderedDict` is a specialized dictionary that preserves insertion order and provides additional ordering operations.

Example:

```python
from collections import OrderedDict

d = OrderedDict()
```

### Key Interview Point

Since Python 3.7, standard dictionaries preserve insertion order, reducing the need for `OrderedDict` in many cases.

---

### 81. Are dictionaries ordered in Python?

**Answer:**
Yes.

From Python 3.7 onward, dictionaries preserve insertion order as part of the language specification.

Example:

```python
d = {
    "a": 1,
    "b": 2,
    "c": 3
}
```

Iteration preserves insertion order.

### Key Interview Point

Prior to Python 3.7, ordering was not guaranteed.

---

### 82. What is the time complexity of dictionary lookup?

**Answer:**

Average Case:

```text
O(1)
```

Worst Case:

```text
O(n)
```

in extreme collision scenarios.

### Key Interview Point

Hash tables provide near-constant-time lookups.

---

### 83. What is the time complexity of dictionary insertion?

**Answer:**

Average Case:

```text
O(1)
```

Worst Case:

```text
O(n)
```

during resizing or severe hash collisions.

### Key Interview Point

Insertions are highly efficient due to hashing.

---

### 84. What is the time complexity of dictionary deletion?

**Answer:**

Average Case:

```text
O(1)
```

Worst Case:

```text
O(n)
```

### Key Interview Point

Deletion remains efficient because dictionary entries are located using hashes.

---

### 85. How does Python optimize dictionary performance?

**Answer:**

Python optimizes dictionaries through:

* Efficient hash tables
* Open addressing techniques
* Dynamic resizing
* Cached hash values
* Compact dictionary representation

### Key Interview Point

Python dictionaries are among the most optimized built-in data structures.

---

# Advanced Data Type Concepts

### 86. What is mutability?

**Answer:**
Mutability refers to the ability of an object to be modified after creation.

Mutable types include:

```python
list
dict
set
bytearray
```

Example:

```python
nums = [1, 2]
nums.append(3)
```

### Key Interview Point

Changes occur in-place without creating a new object.

---

### 87. What is immutability?

**Answer:**
Immutability means an object cannot be modified after creation.

Immutable types include:

```python
int
float
str
tuple
frozenset
```

Example:

```python
name = "Python"
name = name + "3"
```

A new string object is created.

### Key Interview Point

Immutable objects are generally safer and hashable.

---

### 88. What is hashability?

**Answer:**
Hashability is the ability of an object to produce a stable hash value during its lifetime.

Example:

```python
hash("Python")
hash((1, 2))
```

### Key Interview Point

Hashable objects can be used as:

* Dictionary keys
* Set elements

---

### 89. What makes an object hashable?

**Answer:**

An object is hashable if:

1. It has a hash value.
2. Its hash value does not change during its lifetime.
3. It supports equality comparison.

Examples:

```python
str
int
float
tuple
frozenset
```

### Key Interview Point

Most immutable objects are hashable.

---

### 90. What is object identity?

**Answer:**
Object identity refers to an object's unique memory location.

Example:

```python
x = [1, 2]

id(x)
```

### Key Interview Point

Identity remains constant throughout the object's lifetime.

---

### 91. What is object equality?

**Answer:**
Equality determines whether two objects have equivalent values.

Example:

```python
a = [1, 2]
b = [1, 2]

a == b
```

Output:

```python
True
```

### Key Interview Point

Equality compares content, not memory location.

---

### 92. What is the difference between identity and equality?

**Answer:**

Identity:

```python
a is b
```

Checks whether both variables reference the same object.

Equality:

```python
a == b
```

Checks whether values are equivalent.

Example:

```python
a = [1, 2]
b = [1, 2]

a == b   # True
a is b   # False
```

### Key Interview Point

One of the most commonly asked Python interview questions.

---

### 93. What is memory aliasing?

**Answer:**
Memory aliasing occurs when multiple variables reference the same object.

Example:

```python
a = [1, 2]
b = a
```

Both variables point to the same list.

### Key Interview Point

Changes through one reference affect the other.

---

### 94. What are reference semantics?

**Answer:**
Reference semantics means variables store references to objects rather than the objects themselves.

Example:

```python
a = [1, 2]
b = a
```

Both variables reference the same object.

### Key Interview Point

Important for understanding mutability and copying behavior.

---

### 95. What are value semantics?

**Answer:**
Value semantics means operations behave as if values themselves are copied.

Example:

```python
x = 10
y = x
```

Changing `y` does not affect `x`.

### Key Interview Point

Immutable objects often appear to follow value semantics.

---

### 96. What are Python collections?

**Answer:**
Collections are container data structures used to store groups of objects.

Examples:

```python
list
tuple
set
dict
```

Specialized collections are available through the `collections` module.

---

### 97. What is the `collections` module?

**Answer:**
The `collections` module provides specialized container data structures.

Examples:

```python
Counter
defaultdict
OrderedDict
deque
namedtuple
ChainMap
```

### Key Interview Point

Frequently used in production code and coding interviews.

---

### 98. What are specialized container data structures?

**Answer:**
Specialized containers are optimized for specific use cases.

Examples:

```python
Counter
deque
defaultdict
namedtuple
```

Benefits:

* Better readability
* Better performance
* Less code

---

### 99. How does memory usage differ among Python data types?

**Answer:**

General trend:

```text
Tuple < List < Dictionary
```

Reason:

* Tuples have fixed size.
* Lists require dynamic resizing.
* Dictionaries maintain hash tables.

### Key Interview Point

Choosing the right data structure impacts memory efficiency.

---

### 100. How do you choose the right data structure for a problem?

**Answer:**

Choose:

| Requirement                   | Data Structure |
| ----------------------------- | -------------- |
| Ordered mutable collection    | List           |
| Ordered immutable collection  | Tuple          |
| Fast membership testing       | Set            |
| Key-value mapping             | Dictionary     |
| Double-ended queue operations | deque          |
| Frequency counting            | Counter        |

### Key Interview Point

Interviewers often test whether you understand the trade-offs between different data structures, not just how to use them.
