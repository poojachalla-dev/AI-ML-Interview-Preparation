## 1. What is a decorator in Python?

### Answer

A decorator is a function that modifies or extends the behavior of another function without changing its source code.

### Example

```python
def decorator(func):

    def wrapper():
        print("Before function")

        func()

        print("After function")

    return wrapper
```

### Key Interview Point

Decorators follow the principle:

```text
Functions can be passed as arguments.
```

---

## 2. Why are decorators used?

### Answer

Decorators help:

* Add functionality
* Avoid code duplication
* Improve code reusability
* Implement logging
* Authentication
* Timing
* Caching

---

## 3. What are first-class functions?

### Answer

Python treats functions as objects.

Functions can:

* Be assigned to variables
* Be passed as arguments
* Be returned from functions

### Example

```python
def greet():
    return "Hello"

message = greet
```

---

## 4. Why are first-class functions important for decorators?

### Answer

Decorators rely on functions being treated as objects.

### Example

```python
def display(func):
    func()
```

A function can be passed to another function.

---

## 5. Can functions be assigned to variables?

### Answer

Yes.

### Example

```python
def greet():
    print("Hello")

say_hello = greet

say_hello()
```

Output

```text
Hello
```

---

## 6. Can functions be passed as arguments?

### Answer

Yes.

### Example

```python
def greet():
    print("Hello")

def execute(func):
    func()

execute(greet)
```

---

## 7. Can functions return other functions?

### Answer

Yes.

### Example

```python
def outer():

    def inner():
        print("Hello")

    return inner
```

---

## 8. What is a higher-order function?

### Answer

A function that:

* Accepts another function
* Returns another function

### Example

```python
def execute(func):
    func()
```

---

## 9. What is a nested function?

### Answer

A function defined inside another function.

### Example

```python
def outer():

    def inner():
        print("Inside")

    inner()
```

---

## 10. What is a closure?

### Answer

A closure remembers variables from its enclosing scope even after that scope has finished executing.

### Example

```python
def outer(msg):

    def inner():
        print(msg)

    return inner
```

---

## 11. Why are closures important for decorators?

### Answer

Closures allow wrapper functions to remember the original function.

### Example

```python
def decorator(func):

    def wrapper():
        func()

    return wrapper
```

---

## 12. What is the basic structure of a decorator?

### Answer

```python
def decorator(func):

    def wrapper():
        func()

    return wrapper
```

---

## 13. What is the wrapper function?

### Answer

The wrapper adds extra behavior before or after the original function.

### Example

```python
def wrapper():

    print("Before")

    func()

    print("After")
```

---

## 14. How do decorators work internally?

### Answer

Python transforms:

```python
@decorator
def greet():
    pass
```

into:

```python
greet = decorator(greet)
```

### Key Interview Point

Extremely common interview question.

---

## 15. What is decorator syntax?

### Answer

Using:

```python
@
```

### Example

```python
@decorator
def greet():
    pass
```

---

## 16. Create a simple decorator.

### Answer

```python
def decorator(func):

    def wrapper():

        print("Before")

        func()

        print("After")

    return wrapper
```

---

## 17. Apply a decorator to a function.

### Example

```python
@decorator
def greet():

    print("Hello")
```

Output

```text
Before
Hello
After
```

---

## 18. Can multiple decorators be applied?

### Answer

Yes.

### Example

```python
@decorator1
@decorator2
def greet():
    pass
```

---

## 19. In what order are multiple decorators executed?

### Answer

Bottom to top.

### Example

```python
@A
@B
def greet():
    pass
```

Equivalent to:

```python
greet = A(B(greet))
```

---

## 20. What are common decorator use cases?

### Answer

Common Uses:

* Logging
* Authentication
* Authorization
* Caching
* Validation
* Timing
* Rate Limiting

---

## 21. What is function wrapping?

### Answer

Adding functionality around an existing function.

### Example

```python
def wrapper():

    print("Before")

    func()

    print("After")
```

---

## 22. What happens if a decorated function accepts arguments?

### Answer

The wrapper must accept arguments too.

### Example

```python
def wrapper(*args, **kwargs):
    return func(*args, **kwargs)
```

---

## 23. Why use *args and **kwargs in decorators?

### Answer

To support any number of arguments.

### Example

```python
def wrapper(*args, **kwargs):

    return func(*args, **kwargs)
```

### Key Interview Point

Frequently asked.

---

## 24. Create a decorator supporting arguments.

### Example

```python
def decorator(func):

    def wrapper(*args, **kwargs):

        print("Running")

        return func(*args, **kwargs)

    return wrapper
```

---

## 25. What happens if a decorator does not return the original function result?

### Answer

The original return value is lost.

### Example

```python
def wrapper():

    func()
```

Bad practice.

Correct:

```python
return func()
```

---

## 26. What is functools.wraps?

### Answer

`functools.wraps` preserves the metadata of the original function.

### Example

```python
from functools import wraps

def decorator(func):

    @wraps(func)
    def wrapper():
        return func()

    return wrapper
```

### Key Interview Point

Without `wraps`, function metadata is lost.

---

## 27. Why is functools.wraps important?

### Answer

Preserves:

* Function name
* Docstring
* Module information
* Annotations

### Example

```python
print(func.__name__)
```

Returns original function name.

---

## 28. What happens without functools.wraps?

### Answer

Decorator replaces metadata.

### Example

```python
print(greet.__name__)
```

Output:

```text
wrapper
```

Instead of:

```text
greet
```

---

## 29. What is **name**?

### Answer

Returns function name.

### Example

```python
def greet():
    pass

print(greet.__name__)
```

Output:

```text
greet
```

---

## 30. What is **doc**?

### Answer

Returns function documentation.

### Example

```python
def greet():
    """Greeting Function"""

print(greet.__doc__)
```

---

## 31. What is a parameterized decorator?

### Answer

A decorator that accepts arguments.

### Example

```python
@repeat(3)
def hello():
    pass
```

---

## 32. How many nested functions are needed in a parameterized decorator?

### Answer

Three.

### Structure

```python
decorator arguments
    ↓
actual decorator
    ↓
wrapper
```

---

## 33. Create a simple parameterized decorator.

### Example

```python
def repeat(n):

    def decorator(func):

        def wrapper():

            for _ in range(n):
                func()

        return wrapper

    return decorator
```

---

## 34. How do you apply a parameterized decorator?

### Example

```python
@repeat(3)
def greet():
    print("Hello")
```

Output:

```text
Hello
Hello
Hello
```

---

## 35. What is a logging decorator?

### Answer

Logs function execution.

### Example

```python
def logger(func):

    def wrapper():

        print("Function called")

        return func()

    return wrapper
```

---

## 36. Why are logging decorators useful?

### Answer

Used for:

* Monitoring
* Debugging
* Auditing
* Production systems

---

## 37. What is a timing decorator?

### Answer

Measures execution time.

### Example

```python
import time

def timer(func):

    def wrapper():

        start = time.time()

        result = func()

        end = time.time()

        print(end - start)

        return result

    return wrapper
```

---

## 38. What is a profiling decorator?

### Answer

Tracks performance metrics.

### Example

```python
execution time
memory usage
call count
```

---

## 39. What is an authentication decorator?

### Answer

Verifies user access before executing a function.

### Example

```python
def authenticate(func):

    def wrapper():

        if user_logged_in:
            return func()

    return wrapper
```

---

## 40. Where are authentication decorators commonly used?

### Answer

Commonly used in:

* Django
* Flask
* FastAPI
* Enterprise APIs

---

## 41. What is an authorization decorator?

### Answer

Checks permissions.

### Example

```python
@admin_required
def delete_user():
    pass
```

---

## 42. What is a validation decorator?

### Answer

Validates input before function execution.

### Example

```python
def validate(func):

    def wrapper(age):

        if age < 0:
            raise ValueError

        return func(age)

    return wrapper
```

---

## 43. What is a caching decorator?

### Answer

Stores results to avoid recomputation.

### Example

```python
cache = {}
```

Function results are reused.

---

## 44. What is functools.lru_cache?

### Answer

Built-in caching decorator.

### Example

```python
from functools import lru_cache

@lru_cache
def fibonacci(n):
    pass
```

---

## 45. Why use lru_cache?

### Answer

Benefits:

* Faster execution
* Reduced computation
* Automatic caching

### Key Interview Point

Frequently asked in interviews.

---

## 46. What does LRU stand for?

### Answer

```text
Least Recently Used
```

Old cache entries are removed first.

---

## 47. What is memoization?

### Answer

Storing function results for future reuse.

### Example

```python
f(10)
```

Second call uses cache.

---

## 48. What is a retry decorator?

### Answer

Retries a failed operation.

### Example

```python
@retry
def fetch_data():
    pass
```

Useful for APIs.

---

## 49. What is a rate-limiting decorator?

### Answer

Restricts function calls.

### Example

```python
@rate_limit
def api_call():
    pass
```

---

## 50. What are the most common decorator interview questions?

### Answer

Frequently Asked:

* What is a decorator?
* How do decorators work?
* Why use wraps?
* What is a closure?
* What are parameterized decorators?
* What is lru_cache?
* What is memoization?
* How does @ syntax work?

---

# Python Decorators Interview Questions & Answers (51–75)

---

## 51. What is a class decorator?

### Answer

A class decorator modifies or extends a class without changing its source code.

### Example

```python
def add_method(cls):

    cls.version = "1.0"

    return cls

@add_method
class App:
    pass

print(App.version)
```

Output:

```text
1.0
```

---

## 52. How do class decorators differ from function decorators?

### Answer

| Function Decorator       | Class Decorator       |
| ------------------------ | --------------------- |
| Decorates functions      | Decorates classes     |
| Receives function object | Receives class object |
| Returns function         | Returns class         |

---

## 53. Can multiple decorators be applied to a function?

### Answer

Yes.

### Example

```python
@decorator1
@decorator2
def greet():
    pass
```

---

## 54. In what order are decorators applied?

### Answer

Decorators are applied from bottom to top.

### Example

```python
@A
@B
def greet():
    pass
```

Equivalent to:

```python
greet = A(B(greet))
```

---

## 55. In what order are wrappers executed?

### Answer

Execution occurs from top to bottom.

### Example

```python
@A
@B
def greet():
    pass
```

Execution:

```text
A Before
B Before
Function
B After
A After
```

---

## 56. What are chained decorators?

### Answer

Multiple decorators applied to the same function.

### Example

```python
@authenticate
@log
@timer
def process():
    pass
```

---

## 57. What is a built-in decorator?

### Answer

Decorators provided by Python itself.

### Examples

```python
@property
@staticmethod
@classmethod
@lru_cache
```

---

## 58. What is @property?

### Answer

Converts a method into a read-only attribute.

### Example

```python
class Employee:

    def __init__(self):
        self._salary = 50000

    @property
    def salary(self):
        return self._salary
```

Usage:

```python
emp.salary
```

---

## 59. Why use @property?

### Answer

Benefits:

* Encapsulation
* Cleaner syntax
* Validation support
* Read-only attributes

---

## 60. What is a property setter?

### Answer

Allows controlled assignment.

### Example

```python
class Employee:

    def __init__(self):
        self._salary = 0

    @property
    def salary(self):
        return self._salary

    @salary.setter
    def salary(self, value):
        self._salary = value
```

---

## 61. What is a property deleter?

### Answer

Controls deletion of attributes.

### Example

```python
@salary.deleter
def salary(self):
    del self._salary
```

---

## 62. What is @staticmethod?

### Answer

Creates a method that belongs to the class but doesn't use instance data.

### Example

```python
class Math:

    @staticmethod
    def add(a, b):
        return a + b
```

Usage:

```python
Math.add(2, 3)
```

---

## 63. When should @staticmethod be used?

### Answer

When the method:

* Doesn't use self
* Doesn't use cls
* Performs utility operations

---

## 64. What is @classmethod?

### Answer

Creates a method that receives the class as its first argument.

### Example

```python
class Employee:

    company = "Google"

    @classmethod
    def get_company(cls):
        return cls.company
```

---

## 65. What is the difference between @staticmethod and @classmethod?

### Answer

| @staticmethod  | @classmethod       |
| -------------- | ------------------ |
| No self        | No self            |
| No cls         | Receives cls       |
| Utility method | Class-level method |

---

## 66. What is the difference between instance methods, static methods, and class methods?

### Answer

| Type            | First Parameter |
| --------------- | --------------- |
| Instance Method | self            |
| Class Method    | cls             |
| Static Method   | None            |

---

## 67. What is a descriptor?

### Answer

A descriptor controls attribute access using:

```python
__get__()
__set__()
__delete__()
```

### Key Interview Point

@property is built using descriptors.

---

## 68. How are decorators related to descriptors?

### Answer

Decorators like:

```python
@property
```

internally use descriptor protocols.

---

## 69. What is a singleton decorator?

### Answer

Ensures only one instance of a class exists.

### Example

```python
instances = {}

def singleton(cls):

    def get_instance():

        if cls not in instances:
            instances[cls] = cls()

        return instances[cls]

    return get_instance
```

---

## 70. What is a registration decorator?

### Answer

Registers functions automatically.

### Example

```python
registry = []

def register(func):

    registry.append(func)

    return func
```

---

## 71. Why are registration decorators useful?

### Answer

Used in:

* Plugin systems
* Command handlers
* API routing
* Event systems

---

## 72. What is a route decorator?

### Answer

Maps URLs to functions.

### Example

```python
@app.route("/home")
def home():
    return "Welcome"
```

### Key Interview Point

Common in Flask.

---

## 73. How are decorators used in FastAPI?

### Example

```python
@app.get("/users")
def get_users():
    return []
```

Decorators define API endpoints.

---

## 74. What are production use cases of decorators?

### Answer

Applications:

* Logging
* Authentication
* Authorization
* Caching
* Monitoring
* API Routing
* Validation

---

## 75. What advanced decorator topics are commonly asked?

### Answer

Frequently Asked:

* wraps()
* Closures
* Parameterized Decorators
* Chained Decorators
* Class Decorators
* Property Decorators
* lru_cache
* Descriptor Protocol

---

## 76. What is a decorator factory?

### Answer

A decorator factory is a function that returns a decorator.

### Example

```python
def repeat(times):

    def decorator(func):

        def wrapper():

            for _ in range(times):
                func()

        return wrapper

    return decorator
```

### Key Interview Point

Parameterized decorators are implemented using decorator factories.

---

## 77. What is a stateful decorator?

### Answer

A decorator that maintains state between function calls.

### Example

```python
def counter(func):

    count = 0

    def wrapper():

        nonlocal count

        count += 1

        print(f"Called {count} times")

        return func()

    return wrapper
```

---

## 78. What is the nonlocal keyword?

### Answer

`nonlocal` allows modification of variables in an enclosing scope.

### Example

```python
def outer():

    count = 0

    def inner():

        nonlocal count

        count += 1
```

---

## 79. Why are stateful decorators useful?

### Answer

Applications:

* Call counting
* Rate limiting
* Monitoring
* Analytics

---

## 80. Can a class be used as a decorator?

### Answer

Yes.

### Example

```python
class Decorator:

    def __init__(self, func):
        self.func = func

    def __call__(self):
        return self.func()
```

---

## 81. What is the **call** method?

### Answer

Makes an object callable like a function.

### Example

```python
class Demo:

    def __call__(self):
        print("Called")
```

Usage:

```python
obj = Demo()
obj()
```

---

## 82. Why use class-based decorators?

### Answer

Benefits:

* Better state management
* Cleaner complex logic
* OOP-friendly design

---

## 83. What is functools.partial?

### Answer

Creates a new function with predefined arguments.

### Example

```python
from functools import partial

square = partial(pow, exp=2)
```

---

## 84. How can partial be used with decorators?

### Answer

Helps create configurable decorators with less code.

### Example

```python
custom_log = partial(logger, level="INFO")
```

---

## 85. What is a decorator stack?

### Answer

Multiple decorators applied together.

### Example

```python
@timer
@logger
@authenticate
def process():
    pass
```

---

## 86. What is the execution flow of a decorator stack?

### Answer

Application:

```python
process = timer(
            logger(
                authenticate(process)
            )
         )
```

Execution:

```text
timer
 logger
  authenticate
   function
```

---

## 87. What are common decorator interview coding questions?

### Answer

Examples:

* Create a logging decorator
* Create a timing decorator
* Count function calls
* Implement caching
* Validate arguments

---

## 88. Create a call counter decorator.

### Example

```python
def count_calls(func):

    count = 0

    def wrapper(*args, **kwargs):

        nonlocal count

        count += 1

        print(count)

        return func(*args, **kwargs)

    return wrapper
```

---

## 89. Create a timing decorator.

### Example

```python
import time

def timer(func):

    def wrapper():

        start = time.time()

        result = func()

        end = time.time()

        print(end - start)

        return result

    return wrapper
```

---

## 90. Create a simple caching decorator.

### Example

```python
def cache(func):

    memory = {}

    def wrapper(n):

        if n not in memory:
            memory[n] = func(n)

        return memory[n]

    return wrapper
```

---

## 91. What are performance costs of decorators?

### Answer

Every decorator adds:

* Function call overhead
* Additional wrapper execution
* Memory consumption

### Key Interview Point

Usually negligible unless heavily nested.

---

## 92. How do decorators affect debugging?

### Answer

Without `functools.wraps`, debugging becomes harder because metadata is lost.

### Example

```python
print(func.__name__)
```

May return:

```text
wrapper
```

instead of original function name.

---

## 93. What is a common mistake when writing decorators?

### Answer

Forgetting to return the wrapped function result.

### Incorrect

```python
def wrapper():

    func()
```

### Correct

```python
return func()
```

---

## 94. What is another common decorator mistake?

### Answer

Not handling function arguments.

### Incorrect

```python
def wrapper():
    func()
```

### Correct

```python
def wrapper(*args, **kwargs):
    return func(*args, **kwargs)
```

---

## 95. Why should decorators be lightweight?

### Answer

Heavy decorators can:

* Slow execution
* Increase complexity
* Reduce readability

---

## 96. How are decorators used in Machine Learning projects?

### Answer

Applications:

* Logging experiments
* Tracking metrics
* Timing model training
* Monitoring inference

---

## 97. How are decorators used in APIs?

### Answer

Applications:

* Authentication
* Authorization
* Request validation
* Rate limiting
* Logging

---

## 98. What decorator concepts are most important for interviews?

### Answer

Core Topics:

* First-Class Functions
* Closures
* Wrapper Functions
* @ Syntax
* functools.wraps

---

## 99. What advanced decorator concepts are frequently asked?

### Answer

Advanced Topics:

* Parameterized Decorators
* Class Decorators
* Stateful Decorators
* Descriptor Protocol
* lru_cache
* Decorator Factories

---

## 100. What Decorator knowledge is required for Python interviews?

### Answer

### Fundamentals

* First-Class Functions
* Higher-Order Functions
* Nested Functions
* Closures
* Basic Decorators

### Intermediate

* Wrapper Functions
* *args and **kwargs
* functools.wraps
* Parameterized Decorators

### Advanced

* Class Decorators
* Stateful Decorators
* Decorator Factories
* Descriptor Relationship

### Production Concepts

* Logging
* Authentication
* Validation
* Caching
* Monitoring
* API Routing

### Final Interview Tip

If you understand:

* Closures
* Wrapper Functions
* @ Syntax
* wraps()
* Parameterized Decorators
* lru_cache
* Class Decorators

you can confidently answer **95%+ of Python Decorator interview questions** asked in Python, Backend, Data Engineering, Machine Learning, and AI Engineering interviews.






