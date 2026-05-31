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

```
```
