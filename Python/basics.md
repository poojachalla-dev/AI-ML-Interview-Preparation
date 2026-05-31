# Python Basics Interview Questions & Answers

## 1. What is Python?

### Answer

Python is a high-level, interpreted, general-purpose programming language known for its readability and simplicity. It supports multiple programming paradigms, including procedural, object-oriented, and functional programming.

---

## 2. What are the key features of Python?

### Answer

* Easy-to-read syntax
* Interpreted language
* Dynamically typed
* Object-oriented
* Cross-platform
* Extensive standard library
* Automatic memory management
* Large ecosystem of third-party packages

---

## 3. Why is Python called an interpreted language?

### Answer

Python code is executed by an interpreter rather than being directly compiled into machine code. The interpreter reads and executes instructions at runtime.

Although Python first compiles source code into bytecode, execution is performed by the Python Virtual Machine (PVM).

---

## 4. What is bytecode in Python?

### Answer

Bytecode is an intermediate representation of Python code generated after compilation. It is platform-independent and executed by the Python Virtual Machine.

Example:

```python
print("Hello")
```

is first converted into bytecode before execution.

---

## 5. What is the Python Virtual Machine (PVM)?

### Answer

The Python Virtual Machine is the runtime engine that executes Python bytecode. It acts as an abstraction layer between Python programs and the operating system.

Execution Flow:

```text
Python Source Code
        ↓
     Compiler
        ↓
     Bytecode
        ↓
        PVM
        ↓
 Program Execution
```

---

## 6. What is dynamic typing?

### Answer

Dynamic typing means variable types are determined at runtime rather than during compilation.

Example:

```python
x = 10
x = "Python"
```

The same variable can hold values of different types.

---

## 7. What is strong typing in Python?

### Answer

Python is strongly typed, meaning it does not automatically perform unsafe type conversions.

Example:

```python
"5" + 5
```

This raises a TypeError because Python does not implicitly convert the integer to a string.

---

## 8. What are Python identifiers?

### Answer

Identifiers are names used to identify variables, functions, classes, modules, and other objects.

Rules:

* Must start with a letter or underscore
* Cannot start with a digit
* Cannot use keywords
* Case-sensitive

Valid:

```python
name
_age
total_amount
```

Invalid:

```python
2name
class
```

---

## 9. What are Python keywords?

### Answer

Keywords are reserved words that have predefined meanings in Python and cannot be used as identifiers.

Examples:

```python
if
else
for
while
class
def
return
import
```

To view all keywords:

```python
import keyword
print(keyword.kwlist)
```

---

## 10. What is indentation in Python?

### Answer

Indentation refers to the spaces or tabs used to define blocks of code. Unlike many programming languages, Python uses indentation instead of braces.

Example:

```python
if True:
    print("Hello")
```

Incorrect indentation results in an IndentationError.

Benefits:

* Improves readability
* Enforces clean code structure
* Eliminates the need for braces

---

## 11. What is the difference between a statement and an expression?

### Answer

An expression is a piece of code that evaluates to a value.

Examples:

```python
5 + 3
name.upper()
len([1, 2, 3])
```

A statement performs an action but does not necessarily return a value.

Examples:

```python
x = 10
if x > 5:
    print(x)
```

### Key Interview Points

* Expressions produce values.
* Statements perform actions.
* Every expression can be part of a statement.

---

## 12. What is a variable?

### Answer

A variable is a name that references an object stored in memory.

Example:

```python
name = "Pooh"
age = 22
```

Python variables are references to objects, not containers holding values directly.

### Key Interview Points

* Variables store references to objects.
* No explicit type declaration is required.
* Types are determined at runtime.

---

## 13. How does variable assignment work in Python?

### Answer

Assignment binds a variable name to an object.

Example:

```python
x = 10
y = x
```

Both variables reference the same object until one is reassigned.

### Key Interview Points

* Assignment creates references.
* Python does not copy objects during simple assignment.
* Multiple variables can reference the same object.

---

## 14. What are Python comments?

### Answer

Comments are used to explain code and are ignored by the interpreter.

Single-line comment:

```python
# This is a comment
```

Multi-line comment:

```python
"""
This is a
multi-line comment
"""
```

### Key Interview Points

* Improve code readability.
* Ignored during execution.
* Triple quotes are commonly used for multi-line comments and docstrings.

---

## 15. What is the difference between mutable and immutable objects?

### Answer

Mutable objects can be modified after creation.

Examples:

* list
* dict
* set

Immutable objects cannot be modified after creation.

Examples:

* int
* float
* str
* tuple

Example:

```python
lst = [1, 2]
lst.append(3)

s = "hello"
# s[0] = "H"  # Error
```

### Key Interview Points

* Mutable objects can change in place.
* Immutable objects create new objects when modified.
* Important for understanding memory behavior.

---

## 16. What are Python's built-in data types?

### Answer

Numeric Types:

* int
* float
* complex

Sequence Types:

* str
* list
* tuple

Set Types:

* set
* frozenset

Mapping Type:

* dict

Boolean Type:

* bool

Binary Types:

* bytes
* bytearray
* memoryview

### Key Interview Points

* Python provides multiple built-in data structures.
* Each type serves different use cases.
* Understanding mutability is important.

---

## 17. What is type conversion?

### Answer

Type conversion is the process of converting one data type into another.

Python supports:

1. Implicit conversion
2. Explicit conversion

Example:

```python
x = 5
y = 2.5

result = x + y
```

The integer is automatically converted to a float.

### Key Interview Points

* Implicit conversion is automatic.
* Explicit conversion is performed by the programmer.
* Prevents type mismatch issues.

---

## 18. What is type casting?

### Answer

Type casting is the explicit conversion of one data type into another.

Example:

```python
num = "100"

x = int(num)
y = float(num)
```

Common casting functions:

```python
int()
float()
str()
list()
tuple()
set()
dict()
```

### Key Interview Points

* Controlled by the programmer.
* Useful for data processing and input handling.
* Can raise exceptions for invalid conversions.

---

## 19. What is duck typing?

### Answer

Duck typing is a concept where an object's suitability is determined by the presence of methods and attributes rather than its actual type.

Example:

```python
class Duck:
    def speak(self):
        print("Quack")

class Person:
    def speak(self):
        print("Hello")

def make_sound(obj):
    obj.speak()
```

Both objects work because they provide the required method.

### Key Interview Points

* Focuses on behavior rather than type.
* Supports Python's dynamic nature.
* Commonly asked in OOP interviews.

---

## 20. What is the Zen of Python?

### Answer

The Zen of Python is a collection of guiding principles for writing Python code.

View it using:

```python
import this
```

Some principles include:

* Beautiful is better than ugly.
* Explicit is better than implicit.
* Simple is better than complex.
* Readability counts.
* Errors should never pass silently.

### Key Interview Points

* Represents Python's design philosophy.
* Encourages clean and maintainable code.
* Frequently referenced by experienced Python developers.
