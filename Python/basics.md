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

---

## 21. What is the difference between == and is?

### Answer

`==` compares the values of two objects, while `is` compares their identities (memory locations).

Example:

```python
a = [1, 2]
b = [1, 2]

a == b  # True
a is b  # False
```

### Key Interview Points

* Use `==` for value comparison.
* Use `is` for identity comparison.
* Commonly used with `None`.

---

## 22. What is the difference between shallow copy and deep copy?

### Answer

A shallow copy creates a new object but references nested objects. A deep copy recursively copies all nested objects.

Example:

```python
import copy

a = [[1, 2]]
b = copy.copy(a)
c = copy.deepcopy(a)
```

### Key Interview Points

* Shallow copy shares nested references.
* Deep copy creates independent copies.
* Important for mutable objects.

---

## 23. What happens when you execute a Python file?

### Answer

1. Source code is parsed.
2. Code is compiled into bytecode.
3. Bytecode is executed by the Python Virtual Machine.
4. Output is produced.

### Key Interview Points

* Python is interpreted but uses bytecode internally.
* Compilation and execution are separate steps.

---

## 24. What is a namespace in Python?

### Answer

A namespace is a mapping between names and objects.

Examples:

* Built-in namespace
* Global namespace
* Local namespace

### Key Interview Points

* Prevents naming conflicts.
* Implemented as dictionaries internally.

---

## 25. What are local and global variables?

### Answer

Local Variable:
Declared inside a function.

Global Variable:
Declared outside a function.

Example:

```python
x = 100

def func():
    y = 10
```

### Key Interview Points

* Local variables exist within a function.
* Global variables are accessible throughout the module.

---

## 26. What is the LEGB Rule?

### Answer

Python resolves names in the following order:

1. Local
2. Enclosing
3. Global
4. Built-in

### Key Interview Points

* Determines variable lookup order.
* Frequently asked in scope-related questions.

---

## 27. What are Python's memory management mechanisms?

### Answer

Python manages memory automatically using:

* Private heap
* Reference counting
* Garbage collection

### Key Interview Points

* Memory allocation handled internally.
* Developers rarely manage memory manually.

---

## 28. What is garbage collection?

### Answer

Garbage collection removes objects that are no longer reachable.

Python uses a cyclic garbage collector to clean up reference cycles.

### Key Interview Points

* Prevents memory leaks.
* Works alongside reference counting.

---

## 29. What are reference counts?

### Answer

Every object keeps track of how many references point to it.

When the count becomes zero, memory can be reclaimed.

Example:

```python
x = []
y = x
```

The list now has two references.

### Key Interview Points

* Core memory management mechanism.
* Managed automatically.

---

## 30. What is object interning?

### Answer

Python reuses certain immutable objects to improve performance and memory usage.

Example:

```python
a = 10
b = 10

a is b
```

Often returns `True`.

### Key Interview Points

* Common for small integers and strings.
* Optimization technique.

---

## 31. What is dynamic memory allocation?

### Answer

Memory is allocated during program execution rather than at compile time.

### Key Interview Points

* Supports flexible object creation.
* Managed automatically by Python.

---

## 32. How are arguments passed in Python?

### Answer

Python uses pass-by-object-reference (also called pass-by-assignment).

Objects are passed by reference, but variable bindings remain local.

### Key Interview Points

* Not pass-by-value.
* Not traditional pass-by-reference.

---

## 33. What is pass-by-object-reference?

### Answer

Function parameters receive references to objects.

Example:

```python
def add_item(lst):
    lst.append(10)
```

Changes affect the original list because lists are mutable.

### Key Interview Points

* Important for understanding side effects.
* Behavior depends on mutability.

---

## 34. What is monkey patching?

### Answer

Monkey patching means modifying classes or modules at runtime.

Example:

```python
class A:
    pass

A.name = "Python"
```

### Key Interview Points

* Useful but should be used carefully.
* Can make code harder to maintain.

---

## 35. What is introspection in Python?

### Answer

Introspection is the ability to examine objects at runtime.

Common functions:

```python
type()
dir()
id()
isinstance()
```

### Key Interview Points

* Useful for debugging.
* Supports Python's dynamic nature.

---

## 36. What are **name** and **main**?

### Answer

`__name__` is a special variable automatically set by Python.

When a file is executed directly:

```python
__name__ == "__main__"
```

When imported:

```python
__name__ == "module_name"
```

### Key Interview Points

* Used to determine execution context.

---

## 37. Why use if **name** == "**main**"?

### Answer

It ensures code runs only when the file is executed directly.

Example:

```python
if __name__ == "__main__":
    main()
```

### Key Interview Points

* Prevents unintended execution during imports.
* Common interview question.

---

## 38. What is the difference between Python 2 and Python 3?

### Answer

Major differences:

* Python 3 uses `print()`
* Better Unicode support
* Different integer division behavior
* Improved libraries and syntax

### Key Interview Points

* Python 2 reached end-of-life in 2020.
* Modern development uses Python 3.

---

## 39. What are annotations in Python?

### Answer

Annotations provide metadata about variables, parameters, and return types.

Example:

```python
x: int = 10
```

### Key Interview Points

* Do not enforce types.
* Used by tools and linters.

---

## 40. What are type hints?

### Answer

Type hints specify expected data types.

Example:

```python
def add(a: int, b: int) -> int:
    return a + b
```

### Key Interview Points

* Improve readability.
* Help static type checkers.

---

## 41. What are descriptors?

### Answer

Descriptors are objects that define how attribute access is handled using:

```python
__get__()
__set__()
__delete__()
```

### Key Interview Points

* Power properties and methods.
* Advanced OOP concept.

---

## 42. What are metaclasses?

### Answer

A metaclass is a class whose instances are classes.

Python uses:

```python
type
```

as the default metaclass.

### Key Interview Points

* Control class creation.
* Rarely used but frequently asked in advanced interviews.

---

## 43. How does Python's import system work?

### Answer

When importing:

1. Checks cache (`sys.modules`)
2. Searches module paths
3. Loads module
4. Executes module code
5. Stores module in cache

### Key Interview Points

* Modules load only once per process.

---

## 44. What happens internally during import?

### Answer

Python:

* Searches module paths
* Compiles if necessary
* Executes module code
* Caches module object

### Key Interview Points

* Cached modules improve performance.

---

## 45. How does Python manage memory internally?

### Answer

Python uses:

* Private heap
* Memory allocator
* Reference counting
* Garbage collector

### Key Interview Points

* Memory is automatically managed.
* Developers rarely handle allocation directly.

---

## 46. Explain Python's garbage collector generations.

### Answer

Python divides objects into generations:

* Generation 0
* Generation 1
* Generation 2

Objects surviving collections move to older generations.

### Key Interview Points

* Older generations are scanned less frequently.
* Improves performance.

---

## 47. What are weak references?

### Answer

Weak references allow referencing an object without increasing its reference count.

Module:

```python
import weakref
```

### Key Interview Points

* Useful for caches.
* Prevent memory retention.

---

## 48. What is the GIL?

### Answer

The Global Interpreter Lock (GIL) ensures only one thread executes Python bytecode at a time.

### Key Interview Points

* Exists in CPython.
* Affects CPU-bound multithreading.

---

## 49. Why does Python have a GIL?

### Answer

The GIL simplifies memory management and reference counting, making the interpreter easier to implement.

### Key Interview Points

* Trade-off between simplicity and parallelism.

---

## 50. How can you overcome GIL limitations?

### Answer

Techniques include:

* Multiprocessing
* Async programming
* Native extensions (C/C++)
* Distributed computing

### Key Interview Points

* Multiprocessing is preferred for CPU-bound tasks.
* Multithreading remains useful for I/O-bound tasks.
