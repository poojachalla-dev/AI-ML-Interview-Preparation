## 1. What is an exception in Python?

### Answer

An exception is an event that occurs during program execution and disrupts the normal flow of the program.

### Example

```python
print(10 / 0)
```

### Output

```text
ZeroDivisionError: division by zero
```

### Key Interview Point

Exceptions are runtime errors that can be handled gracefully.

---

## 2. Why do exceptions occur?

### Answer

Exceptions occur when Python encounters an unexpected situation during execution.

Common causes:

* Invalid input
* File not found
* Division by zero
* Network failures
* Type mismatches

### Example

```python
int("hello")
```

### Output

```text
ValueError
```

---

## 3. What is the difference between syntax errors and exceptions?

### Answer

| Syntax Error              | Exception               |
| ------------------------- | ----------------------- |
| Detected before execution | Occurs during execution |
| Prevents program start    | Occurs while running    |
| Parsing issue             | Runtime issue           |

### Syntax Error Example

```python
if True
    print("Hello")
```

### Exception Example

```python
10 / 0
```

### Key Interview Point

Syntax errors occur before execution, exceptions occur during execution.

---

## 4. What is exception handling?

### Answer

Exception handling is the process of responding to runtime errors without crashing the program.

### Example

```python
try:
    print(10 / 0)

except ZeroDivisionError:
    print("Cannot divide by zero")
```

### Output

```text
Cannot divide by zero
```

---

## 5. Why is exception handling important?

### Answer

Benefits:

* Prevents program crashes
* Improves user experience
* Simplifies debugging
* Makes applications robust

### Key Interview Point

Production applications should never expose raw exceptions to end users.

---

## 6. What is the purpose of the try block?

### Answer

The `try` block contains code that may raise an exception.

### Example

```python
try:
    result = 10 / 0
```

### Key Interview Point

Only code that might fail should be placed inside `try`.

---

## 7. What is the purpose of the except block?

### Answer

The `except` block handles exceptions raised inside the `try` block.

### Example

```python
try:
    10 / 0

except ZeroDivisionError:
    print("Division error")
```

---

## 8. What happens if an exception is not handled?

### Answer

Python terminates the program and displays a traceback.

### Example

```python
print(10 / 0)
```

### Output

```text
ZeroDivisionError
```

---

## 9. What is a traceback?

### Answer

A traceback is a report showing:

* Where the error occurred
* Function call sequence
* Exception type

### Example

```python
def func():
    return 10 / 0

func()
```

Python displays the complete call stack.

---

## 10. What is ZeroDivisionError?

### Answer

Raised when division or modulo by zero occurs.

### Example

```python
10 / 0
```

### Output

```text
ZeroDivisionError
```

---

## 11. What is NameError?

### Answer

Raised when an undefined variable is referenced.

### Example

```python
print(age)
```

### Output

```text
NameError
```

---

## 12. What is TypeError?

### Answer

Raised when an operation is performed on incompatible types.

### Example

```python
"10" + 5
```

### Output

```text
TypeError
```

---

## 13. What is ValueError?

### Answer

Raised when a function receives the correct type but an invalid value.

### Example

```python
int("hello")
```

### Output

```text
ValueError
```

---

## 14. What is IndexError?

### Answer

Raised when accessing an invalid list index.

### Example

```python
nums = [1, 2, 3]

print(nums[5])
```

### Output

```text
IndexError
```

---

## 15. What is KeyError?

### Answer

Raised when a dictionary key does not exist.

### Example

```python
data = {"name": "Pooh"}

print(data["age"])
```

### Output

```text
KeyError
```

---

## 16. What is AttributeError?

### Answer

Raised when an object does not contain the requested attribute.

### Example

```python
name = "Python"

name.append("3")
```

### Output

```text
AttributeError
```

---

## 17. What is ImportError?

### Answer

Raised when Python cannot import a module.

### Example

```python
import xyzmodule
```

### Output

```text
ImportError
```

---

## 18. What is ModuleNotFoundError?

### Answer

A subclass of ImportError raised when a module cannot be found.

### Example

```python
import fake_module
```

### Output

```text
ModuleNotFoundError
```

---

## 19. What is FileNotFoundError?

### Answer

Raised when attempting to access a file that does not exist.

### Example

```python
open("data.txt")
```

### Output

```text
FileNotFoundError
```

---

## 20. What is EOFError?

### Answer

Raised when `input()` reaches end-of-file unexpectedly.

### Example

Common in automated scripts receiving no input.

---

## 21. What is OverflowError?

### Answer

Raised when a numeric operation exceeds system limits.

### Example

```python
import math

math.exp(1000)
```

### Output

```text
OverflowError
```

---

## 22. What is MemoryError?

### Answer

Raised when Python cannot allocate sufficient memory.

### Example

```python
huge_list = [0] * (10**12)
```

---

## 23. What is RuntimeError?

### Answer

A generic exception raised when no specific exception fits.

### Example

```python
raise RuntimeError("Unexpected state")
```

---

## 24. What is StopIteration?

### Answer

Raised when an iterator has no more items.

### Example

```python
nums = iter([1])

next(nums)
next(nums)
```

### Output

```text
StopIteration
```

---

## 25. What is KeyboardInterrupt?

### Answer

Raised when the user interrupts execution.

Usually:

```text
Ctrl + C
```

### Example

```python
while True:
    pass
```

Pressing Ctrl+C raises:

```text
KeyboardInterrupt
```

---

## 26. What is the syntax of try-except?

### Answer

The basic syntax of exception handling consists of a `try` block followed by one or more `except` blocks.

### Syntax

```python
try:
    # risky code
except ExceptionType:
    # handling code
```

### Example

```python
try:
    result = 10 / 0

except ZeroDivisionError:
    print("Cannot divide by zero")
```

Output

```text
Cannot divide by zero
```

### Key Interview Point

Only code that may raise exceptions should be placed inside the `try` block.

---

## 27. Can a try block exist without an except block?

### Answer

No.

A `try` block must be followed by at least one of:

- except
- finally
- else

### Invalid Example

```python
try:
    print("Hello")
```

Output

```python
SyntaxError
```

---

## 28. Can a try block have multiple except blocks?

### Answer

Yes.

Different exceptions can be handled separately.

### Example

```python
try:
    num = int(input())

except ValueError:
    print("Invalid number")

except KeyboardInterrupt:
    print("Interrupted")
```

### Key Interview Point

Python checks except blocks from top to bottom.

---

## 29. How does Python choose an except block?

### Answer

Python matches the raised exception against except blocks sequentially.

### Example

```python
try:
    int("abc")

except ValueError:
    print("Value Error")

except TypeError:
    print("Type Error")
```

Output

```text
Value Error
```

---

## 30. Can one except block handle multiple exceptions?

### Answer

Yes.

### Example

```python
try:
    value = int("abc")

except (ValueError, TypeError):
    print("Conversion Error")
```

Output

```text
Conversion Error
```

### Key Interview Point

Use tuples to group exceptions.

---

## 31. What is a generic except block?

### Answer

A generic except catches all exceptions.

### Example

```python
try:
    10 / 0

except:
    print("Something went wrong")
```

### Output

```text
Something went wrong
```

### Key Interview Point

Avoid generic except in production code.

---

## 32. Why should generic except be avoided?

### Answer

It hides useful debugging information and may catch unexpected exceptions.

### Bad Example

```python
try:
    process_data()

except:
    pass
```

### Problems

- Difficult debugging
- Silent failures
- Hidden bugs

---

## 33. What is Exception class?

### Answer

`Exception` is the base class for most built-in exceptions.

### Example

```python
try:
    int("abc")

except Exception as e:
    print(e)
```

Output

```text
invalid literal for int()
```

### Key Interview Point

Catching `Exception` is safer than using bare except.

---

## 34. What is exception hierarchy?

### Answer

Python exceptions are organized in a hierarchy.

### Simplified Structure

```text
BaseException
├── Exception
│   ├── TypeError
│   ├── ValueError
│   ├── IndexError
│   ├── KeyError
│   └── RuntimeError
├── KeyboardInterrupt
└── SystemExit
```

### Key Interview Point

Understanding inheritance helps catch related exceptions.

---

## 35. What happens if no matching except block exists?

### Answer

Python propagates the exception upward and eventually terminates the program.

### Example

```python
try:
    10 / 0

except ValueError:
    print("Value Error")
```

Output

```python
ZeroDivisionError
```

---

## 36. What is exception propagation?

### Answer

Exception propagation occurs when an exception moves up the call stack looking for a handler.

### Example

```python
def func():
    10 / 0

func()
```

The exception propagates until handled.

---

## 37. What is the else block?

### Answer

The `else` block executes only if no exception occurs.

### Example

```python
try:
    result = 10 / 2

except ZeroDivisionError:
    print("Error")

else:
    print(result)
```

Output

```text
5.0
```

---

## 38. Why use else with try-except?

### Answer

It separates successful execution logic from exception handling logic.

### Example

```python
try:
    value = int("100")

except ValueError:
    print("Invalid")

else:
    print("Success")
```

Output

```text
Success
```

---

## 39. What is the finally block?

### Answer

The `finally` block always executes regardless of exceptions.

### Example

```python
try:
    10 / 0

except ZeroDivisionError:
    print("Error")

finally:
    print("Cleanup")
```

Output

```text
Error
Cleanup
```

---

## 40. When is finally useful?

### Answer

Useful for resource cleanup.

Examples:

- Closing files
- Closing database connections
- Releasing locks
- Network cleanup

### Example

```python
file = open("data.txt")

try:
    process(file)

finally:
    file.close()
```

---

## 41. Does finally execute after return?

### Answer

Yes.

### Example

```python
def test():

    try:
        return 10

    finally:
        print("Cleanup")

print(test())
```

Output

```text
Cleanup
10
```

### Key Interview Point

finally executes before the function actually returns.

---

## 42. Does finally execute after an exception?

### Answer

Yes.

### Example

```python
try:
    raise ValueError

finally:
    print("Cleanup")
```

Output

```text
Cleanup
```

---

## 43. Can finally override return values?

### Answer

Yes.

### Example

```python
def test():

    try:
        return 10

    finally:
        return 20
```

Output

```text
20
```

### Key Interview Point

Avoid returning from finally blocks.

---

## 44. Can try-except-finally be combined?

### Answer

Yes.

### Example

```python
try:
    value = int("10")

except ValueError:
    print("Error")

else:
    print("Success")

finally:
    print("Done")
```

Output

```text
Success
Done
```

---

## 45. What is nested exception handling?

### Answer

Exception handling inside another exception block.

### Example

```python
try:

    try:
        10 / 0

    except ZeroDivisionError:
        print("Inner")

except:
    print("Outer")
```

Output

```text
Inner
```

---

## 46. What is raising an exception?

### Answer

Raising an exception means intentionally triggering an error.

### Syntax

```python
raise ExceptionType
```

### Example

```python
raise ValueError("Invalid age")
```

Output

```python
ValueError: Invalid age
```

---

## 47. Why do we raise exceptions?

### Answer

To enforce business rules and signal invalid situations.

### Example

```python
age = -5

if age < 0:
    raise ValueError("Age cannot be negative")
```

### Key Interview Point

Raising exceptions improves code reliability.

---

## 48. What is AssertionError?

### Answer

Raised when an assert statement fails.

### Example

```python
x = -1

assert x > 0
```

Output

```python
AssertionError
```

---

## 49. What is the assert statement?

### Answer

Used for debugging assumptions.

### Syntax

```python
assert condition
```

### Example

```python
assert 5 > 0
```

No exception is raised.

### Example

```python
assert 5 < 0
```

Raises:

```python
AssertionError
```

---

## 50. What is exception chaining?

### Answer

Exception chaining links one exception to another.

### Example

```python
try:
    int("abc")

except ValueError as e:
    raise RuntimeError("Conversion failed") from e
```

Output

```text
RuntimeError
Caused by ValueError
```

### Key Interview Point

Exception chaining preserves debugging information and is commonly used in production systems.

---

## 51. What is a custom exception?

### Answer

A custom exception is a user-defined exception created by inheriting from Python's Exception class.

### Example

```python
class InvalidAgeError(Exception):
    pass
```

### Key Interview Point

Custom exceptions make applications more readable and maintainable.

---

## 52. Why create custom exceptions?

### Answer

Benefits:

- Improves readability
- Better error categorization
- Easier debugging
- Better business rule enforcement

### Example

```python
class InsufficientBalanceError(Exception):
    pass
```

Instead of:

```python
raise ValueError("Insufficient balance")
```

---

## 53. How do you create a custom exception?

### Answer

Inherit from Exception.

### Example

```python
class InvalidSalaryError(Exception):
    pass
```

Usage:

```python
raise InvalidSalaryError("Salary cannot be negative")
```

---

## 54. Can custom exceptions contain additional data?

### Answer

Yes.

### Example

```python
class InvalidAgeError(Exception):

    def __init__(self, age):
        self.age = age
        super().__init__(f"Invalid age: {age}")
```

Usage:

```python
raise InvalidAgeError(-5)
```

---

## 55. What is BaseException?

### Answer

BaseException is the root class of all Python exceptions.

### Hierarchy

```text
BaseException
├── Exception
├── KeyboardInterrupt
├── GeneratorExit
└── SystemExit
```

### Key Interview Point

Most custom exceptions should inherit from Exception, not BaseException.

---

## 56. What is the difference between BaseException and Exception?

### Answer

| BaseException | Exception |
|--------------|------------|
| Root class | Most common exception class |
| Includes system exceptions | Used for application errors |
| Rarely inherited directly | Common inheritance choice |

### Key Interview Point

Always inherit custom exceptions from Exception.

---

## 57. What is SystemExit?

### Answer

Raised when Python exits normally.

### Example

```python
import sys

sys.exit()
```

Output

```python
SystemExit
```

---

## 58. What is GeneratorExit?

### Answer

Raised when a generator is closed.

### Example

```python
def gen():
    yield 1

g = gen()

g.close()
```

### Key Interview Point

Usually handled internally.

---

## 59. Can KeyboardInterrupt be caught?

### Answer

Yes.

### Example

```python
try:

    while True:
        pass

except KeyboardInterrupt:
    print("Program stopped")
```

---

## 60. Should KeyboardInterrupt be ignored?

### Answer

No.

Ignoring KeyboardInterrupt prevents users from terminating applications.

### Bad Example

```python
except:
    pass
```

---

## 61. What is exception logging?

### Answer

Exception logging records errors for debugging and monitoring.

### Example

```python
import logging

try:
    10 / 0

except Exception as e:
    logging.error(e)
```

---

## 62. Why is logging better than print statements?

### Answer

Logging provides:

- Timestamps
- Severity levels
- Persistence
- Centralized monitoring

### Key Interview Point

Production systems use logging, not print.

---

## 63. What are logging levels?

### Answer

Common levels:

```text
DEBUG
INFO
WARNING
ERROR
CRITICAL
```

### Example

```python
logging.error("Database connection failed")
```

---

## 64. How do you log exception tracebacks?

### Answer

Using:

```python
logging.exception()
```

### Example

```python
try:
    10 / 0

except Exception:
    logging.exception("Error occurred")
```

---

## 65. What is traceback module?

### Answer

The traceback module provides access to exception tracebacks.

### Example

```python
import traceback

try:
    10 / 0

except:
    traceback.print_exc()
```

---

## 66. What information does a traceback contain?

### Answer

A traceback contains:

- File name
- Line number
- Function calls
- Error type
- Error message

### Key Interview Point

Tracebacks are crucial for debugging.

---

## 67. What is stack unwinding?

### Answer

Stack unwinding occurs when Python removes stack frames while propagating exceptions.

### Example

```python
func1()
→ func2()
→ func3()
```

Exception in func3 causes stack frames to unwind.

---

## 68. What is a context manager?

### Answer

A context manager manages resources automatically.

### Example

```python
with open("file.txt") as f:
    data = f.read()
```

### Key Interview Point

Context managers simplify cleanup.

---

## 69. How does with statement help exception handling?

### Answer

The `with` statement guarantees cleanup even when exceptions occur.

### Example

```python
with open("file.txt") as f:
    process(f)
```

File closes automatically.

---

## 70. What methods define a context manager?

### Answer

A context manager implements:

```python
__enter__()
__exit__()
```

### Example

```python
class MyContext:

    def __enter__(self):
        pass

    def __exit__(self, exc_type, exc_val, exc_tb):
        pass
```

---

## 71. What does __enter__ do?

### Answer

Executed when entering the with block.

### Example

```python
def __enter__(self):
    print("Enter")
```

---

## 72. What does __exit__ do?

### Answer

Executed when leaving the with block.

### Example

```python
def __exit__(self, exc_type, exc_val, exc_tb):
    print("Exit")
```

---

## 73. Can __exit__ suppress exceptions?

### Answer

Yes.

Returning True suppresses exceptions.

### Example

```python
def __exit__(self, exc_type, exc_val, exc_tb):
    return True
```

### Key Interview Point

Use carefully.

---

## 74. What is contextlib?

### Answer

contextlib provides utilities for context managers.

### Example

```python
from contextlib import contextmanager
```

### Key Interview Point

Simplifies context manager creation.

---

## 75. How do you create a context manager using a decorator?

### Answer

Using `@contextmanager`.

### Example

```python
from contextlib import contextmanager

@contextmanager
def file_manager():

    print("Open")

    yield

    print("Close")
```

Usage:

```python
with file_manager():
    print("Working")
```

Output

```text
Open
Working
Close
```

---

## 76. What are exception handling best practices?

### Answer

Best practices include:

- Catch specific exceptions
- Avoid bare except
- Use finally for cleanup
- Log exceptions properly
- Create custom exceptions when necessary

### Example

```python
try:
    value = int(user_input)

except ValueError:
    logging.error("Invalid input")
```

### Key Interview Point

Specific exception handling improves maintainability.

---

## 77. Why should specific exceptions be preferred?

### Answer

Specific exceptions make debugging easier and prevent accidentally catching unrelated errors.

### Bad Example

```python
except:
    pass
```

### Good Example

```python
except ValueError:
    print("Invalid number")
```

---

## 78. Why is swallowing exceptions dangerous?

### Answer

Swallowing exceptions hides bugs.

### Bad Example

```python
try:
    process()

except:
    pass
```

### Problem

Errors become invisible and difficult to debug.

---

## 79. What is defensive exception handling?

### Answer

Defensive exception handling anticipates possible failures and handles them gracefully.

### Example

```python
try:
    file = open("data.txt")

except FileNotFoundError:
    create_default_file()
```

---

## 80. Should exceptions be used for normal program flow?

### Answer

No.

Exceptions should represent exceptional situations.

### Bad Example

```python
try:
    item = data[key]

except KeyError:
    item = None
```

### Better

```python
item = data.get(key)
```

### Key Interview Point

Exceptions are slower than normal control flow.

---

## 81. Are exceptions expensive?

### Answer

Yes.

Raising exceptions requires:

- Stack unwinding
- Object creation
- Traceback generation

### Key Interview Point

Avoid using exceptions in performance-critical loops.

---

## 82. What is EAFP?

### Answer

EAFP stands for:

```text
Easier to Ask Forgiveness than Permission
```

Pythonic style:

```python
try:
    value = data["name"]

except KeyError:
    value = "Unknown"
```

---

## 83. What is LBYL?

### Answer

LBYL stands for:

```text
Look Before You Leap
```

### Example

```python
if "name" in data:
    value = data["name"]
```

---

## 84. EAFP vs LBYL?

### Answer

| EAFP | LBYL |
|--------|--------|
| Try operation first | Check first |
| More Pythonic | Common in C/Java |
| Uses exceptions | Uses conditions |

### Key Interview Point

Python generally prefers EAFP.

---

## 85. What is re-raising an exception?

### Answer

Re-raising passes the exception upward after partial handling.

### Example

```python
try:
    10 / 0

except ZeroDivisionError:
    print("Logged")
    raise
```

### Key Interview Point

Useful for logging while preserving behavior.

---

## 86. Why re-raise exceptions?

### Answer

Reasons:

- Logging
- Monitoring
- Partial recovery
- Preserving traceback

### Example

```python
except Exception:
    logging.exception("Error")
    raise
```

---

## 87. What is fail-fast design?

### Answer

Fail-fast systems stop execution immediately when critical errors occur.

### Example

```python
if config is None:
    raise RuntimeError("Missing configuration")
```

### Key Interview Point

Fail fast reduces hidden bugs.

---

## 88. What is graceful degradation?

### Answer

Graceful degradation allows systems to continue functioning after failures.

### Example

```python
try:
    load_recommendations()

except:
    show_default_recommendations()
```

---

## 89. What is exception-safe code?

### Answer

Exception-safe code leaves the system in a valid state even when errors occur.

### Example

Database transaction rollback.

```python
try:
    transaction.commit()

except:
    transaction.rollback()
```

---

## 90. What are exception-safe resource management techniques?

### Answer

Common techniques:

- Context managers
- finally blocks
- Database transactions
- Resource pools

### Example

```python
with open("data.txt") as f:
    process(f)
```

---

## 91. How does exception handling affect performance?

### Answer

Exception handling itself is inexpensive.

Raising exceptions is expensive because:

- Traceback creation
- Stack unwinding
- Object allocation

### Key Interview Point

Avoid exceptions inside hot loops.

---

## 92. What is exception transparency?

### Answer

Exception transparency means allowing callers to understand what exceptions may occur.

### Example

```python
def read_file(path):
    return open(path).read()
```

Caller knows FileNotFoundError may occur.

---

## 93. What is exception wrapping?

### Answer

Exception wrapping converts low-level exceptions into domain-specific exceptions.

### Example

```python
try:
    connect_db()

except ConnectionError as e:
    raise DatabaseError() from e
```

---

## 94. What is exception translation?

### Answer

Exception translation converts one exception type into another.

### Example

```python
try:
    int("abc")

except ValueError:
    raise InvalidInputError()
```

---

## 95. What are common exception handling mistakes?

### Answer

Common mistakes:

- Bare except
- Ignoring exceptions
- Catching Exception everywhere
- Returning from finally
- Excessive nesting

### Key Interview Point

These are frequently discussed during code reviews.

---

## 96. What exception questions are commonly asked in interviews?

### Answer

Popular questions:

- try vs except
- else vs finally
- raise keyword
- custom exceptions
- exception hierarchy
- context managers
- EAFP vs LBYL

---

## 97. How would you design custom exceptions for a banking system?

### Answer

Example hierarchy:

```python
BankError
├── InsufficientFundsError
├── InvalidAccountError
├── TransactionLimitError
└── AccountFrozenError
```

### Key Interview Point

Domain-specific exceptions improve clarity.

---

## 98. How would you handle API failures?

### Answer

Techniques:

- Retry mechanisms
- Timeouts
- Logging
- Fallback responses

### Example

```python
try:
    response = api_call()

except TimeoutError:
    retry()
```

---

## 99. How would you handle database exceptions?

### Answer

Typical strategy:

```python
try:
    transaction.commit()

except DatabaseError:
    transaction.rollback()
    raise
```

### Key Interview Point

Never leave transactions partially completed.

---

## 100. What exception handling knowledge is required for Python interviews?

### Answer

Candidates should master:

### Fundamentals

- Exceptions
- Tracebacks
- try/except

### Intermediate

- else
- finally
- raise
- assertions

### Advanced

- Custom exceptions
- Context managers
- Exception chaining
- Logging
- EAFP vs LBYL

### Production Concepts

- Resource cleanup
- Transactions
- Fail-fast design
- Graceful degradation

### Coding Problems

- File handling
- Input validation
- API retries
- Database transactions

### Final Interview Tip

If you understand:

- Exception hierarchy
- try/except/else/finally
- raise
- custom exceptions
- context managers
- logging

you can confidently answer **95%+ of Python exception handling interview questions** asked in Software Engineering, Data Engineering, Backend Development, Machine Learning, and AI Engineering interviews.





