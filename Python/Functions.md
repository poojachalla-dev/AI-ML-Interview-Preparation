## 1. What is a function in Python?

### Answer

A function is a reusable block of code that performs a specific task and optionally returns a value.

Example:

```python
def greet(name):
    return f"Hello, {name}!"

print(greet("Alice"))
```

Output:

```
Hello, Alice!
```

### Key Interview Points

* Defined using the `def` keyword.
* `return` sends a value back to the caller.
* Without `return`, the function returns `None` implicitly.

---

## 2. Why do we use functions?

### Answer

Functions help in:

* Code reusability
* Better readability
* Easier debugging
* Modular design
* Avoiding repetition (DRY principle)

Example:

```python
def add(a, b):
    return a + b

print(add(2, 3))
print(add(10, 20))
```

Output:

```
5
30
```

### Key Interview Points

* Functions are the building blocks of any Python program.
* They make code maintainable and testable.

---

## 3. What is the difference between a function and a method?

### Answer

A **function** is a standalone callable.

```python
len("Python")
```

A **method** is a function bound to an object.

```python
"Python".upper()
```

### Key Interview Points

* Methods are defined inside a class.
* Internally, methods receive the object as the first argument (`self`).

---

## 4. What does a function return if there is no return statement?

### Answer

It returns `None`.

Example:

```python
def do_nothing():
    pass

result = do_nothing()
print(result)
```

Output:

```
None
```

### Key Interview Points

* `None` is Python's null value.
* This is a common source of bugs when the return statement is accidentally omitted.

---

## 5. Can a Python function return multiple values?

### Answer

Yes. Python packs them into a tuple.

Example:

```python
def min_max(nums):
    return min(nums), max(nums)

lo, hi = min_max([3, 1, 4, 1, 5, 9])
print(lo, hi)
```

Output:

```
1 9
```

### Key Interview Points

* The return value is technically a single tuple.
* Tuple unpacking makes it feel like multiple returns.

---

## 6. What is a docstring?

### Answer

A docstring is a string literal placed at the start of a function to describe its purpose.

Example:

```python
def add(a, b):
    """Return the sum of a and b."""
    return a + b

print(add.__doc__)
```

Output:

```
Return the sum of a and b.
```

### Key Interview Points

* Accessible via `.__doc__` or `help()`.
* Convention is to use triple quotes.
* Tools like Sphinx use docstrings to generate documentation.

---

## 7. What are the types of function arguments in Python?

### Answer

Python supports five types of arguments:

| Type | Example | Notes |
|---|---|---|
| Positional | `f(1, 2)` | Order matters |
| Keyword | `f(a=1, b=2)` | Order-independent |
| Default | `def f(x=10)` | Used if not passed |
| Positional-only (`/`) | `def f(x, /, y)` | Python 3.8+ |
| Keyword-only (`*`) | `def f(*, y)` | Must use name |

Example:

```python
def connect(host, port=8080, *, ssl=False):
    print(host, port, ssl)

connect("example.com")
connect("example.com", 443, ssl=True)
```

Output:

```
example.com 8080 False
example.com 443 True
```

---

## 8. What is a default argument?

### Answer

A default argument provides a fallback value when the caller does not supply one.

Example:

```python
def greet(name="World"):
    return f"Hello, {name}!"

print(greet())
print(greet("Alice"))
```

Output:

```
Hello, World!
Hello, Alice!
```

### Key Interview Points

* Default arguments must come after non-default arguments.
* Default values are evaluated once at function definition time, not at call time.

---

## 9. What is the mutable default argument trap?

### Answer

Using a mutable object like a list or dict as a default argument causes unexpected behavior because it is created once and shared across all calls.

Wrong:

```python
def append_val(val, lst=[]):
    lst.append(val)
    return lst

print(append_val(1))
print(append_val(2))
```

Output:

```
[1]
[1, 2]
```

Correct:

```python
def append_val(val, lst=None):
    if lst is None:
        lst = []
    lst.append(val)
    return lst
```

### Key Interview Points

* Default values are evaluated at definition time, not at call time.
* Always use `None` as a sentinel for mutable defaults.
* One of the most commonly asked Python interview traps.

---

## 10. What are positional arguments?

### Answer

Positional arguments are passed in order. The position determines which parameter receives which value.

Example:

```python
def describe(name, age):
    print(f"{name} is {age} years old.")

describe("Alice", 30)
```

Output:

```
Alice is 30 years old.
```

### Key Interview Points

* Order matters.
* Swapping positions changes the meaning entirely.

---

## 11. What are keyword arguments?

### Answer

Keyword arguments are passed by explicitly naming the parameter.

Example:

```python
def describe(name, age):
    print(f"{name} is {age} years old.")

describe(age=30, name="Alice")
```

Output:

```
Alice is 30 years old.
```

### Key Interview Points

* Order does not matter when using keyword arguments.
* Improves readability for functions with many parameters.

---

## 12. What are *args?

### Answer

`*args` collects extra positional arguments into a tuple.

Example:

```python
def total(*args):
    return sum(args)

print(total(1, 2, 3, 4))
```

Output:

```
10
```

### Key Interview Points

* The name `args` is a convention, not mandatory.
* The `*` is what matters.
* Type is always a tuple.

---

## 13. What are **kwargs?

### Answer

`**kwargs` collects extra keyword arguments into a dictionary.

Example:

```python
def show_info(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")

show_info(name="Alice", age=30, city="Delhi")
```

Output:

```
name: Alice
age: 30
city: Delhi
```

### Key Interview Points

* The name `kwargs` is convention.
* The `**` is what matters.
* Type is always a dict.

---

## 14. What is the correct order of parameters in a function signature?

### Answer

```
def f(positional, *args, keyword_only, **kwargs)
```

Example:

```python
def f(a, b, *args, kw_only=10, **kwargs):
    print(a, b, args, kw_only, kwargs)

f(1, 2, 3, 4, kw_only=99, x="hello")
```

Output:

```
1 2 (3, 4) 99 {'x': 'hello'}
```

### Key Interview Points

* Positional → `*args` → keyword-only → `**kwargs`
* Violating this order raises a `SyntaxError`.

---

## 15. How do you unpack a list or dictionary into a function call?

### Answer

Use `*` to unpack a list into positional arguments.
Use `**` to unpack a dict into keyword arguments.

Example:

```python
def add(a, b, c):
    return a + b + c

nums = [1, 2, 3]
print(add(*nums))

params = {"a": 1, "b": 2, "c": 3}
print(add(**params))
```

Output:

```
6
6
```

---

## 16. What is a lambda function?

### Answer

A lambda is an anonymous, single-expression function.

Example:

```python
square = lambda x: x ** 2
print(square(5))
```

Output:

```
25
```

Equivalent to:

```python
def square(x):
    return x ** 2
```

### Key Interview Points

* Cannot contain statements or multiple expressions.
* Useful for short, throwaway logic passed inline.

---

## 17. When should you use lambda vs def?

### Answer

| Use `lambda` | Use `def` |
|---|---|
| Short inline functions | Reusable named functions |
| Inside `sorted()`, `map()` etc. | Multi-line logic |
| When readability is not harmed | When a docstring is needed |

Example:

```python
data = [{"name": "Bob", "age": 25}, {"name": "Alice", "age": 22}]
sorted_data = sorted(data, key=lambda x: x["age"])
```

### Key Interview Points

* PEP 8 discourages assigning lambdas to variables — use `def` instead.
* Lambdas have no name in tracebacks, making debugging harder.

---

## 18. Can a lambda have default values?

### Answer

Yes.

Example:

```python
greet = lambda name="World": f"Hello, {name}"

print(greet())
print(greet("Bob"))
```

Output:

```
Hello, World
Hello, Bob
```

---

## 19. Can a lambda accept multiple arguments?

### Answer

Yes.

Example:

```python
add = lambda x, y: x + y
print(add(3, 4))
```

Output:

```
7
```

---

## 20. What is the LEGB rule?

### Answer

LEGB describes the order Python uses to resolve variable names.

```
L — Local       (inside the current function)
E — Enclosing   (enclosing function's scope)
G — Global      (module level)
B — Built-in    (Python builtins like len, print)
```

Example:

```python
x = "global"

def outer():
    x = "enclosing"

    def inner():
        x = "local"
        print(x)

    inner()
    print(x)

outer()
print(x)
```

Output:

```
local
enclosing
global
```

### Key Interview Points

* Python walks up the chain until it finds the name.
* If not found anywhere, `NameError` is raised.

---

## 21. What does the `global` keyword do?

### Answer

It allows a function to modify a variable at the module (global) level.

Example:

```python
count = 0

def increment():
    global count
    count += 1

increment()
increment()
print(count)
```

Output:

```
2
```

### Key Interview Points

* Without `global`, assigning to `count` inside the function creates a new local variable.
* Overusing `global` makes code harder to reason about and test.

---

## 22. What does the `nonlocal` keyword do?

### Answer

It allows an inner function to modify a variable in its enclosing (but non-global) scope.

Example:

```python
def outer():
    x = 10

    def inner():
        nonlocal x
        x += 1

    inner()
    print(x)

outer()
```

Output:

```
11
```

### Key Interview Points

* Without `nonlocal`, Python treats the assignment as creating a new local variable.
* Used specifically in closures.

---

## 23. What is a closure?

### Answer

A closure is an inner function that remembers the variables of its enclosing scope even after the outer function has finished executing.

Example:

```python
def make_multiplier(n):
    def multiplier(x):
        return x * n
    return multiplier

double = make_multiplier(2)
triple = make_multiplier(3)

print(double(5))
print(triple(5))
```

Output:

```
10
15
```

### Key Interview Points

Three conditions for a closure:
* There must be a nested function.
* It must refer to a variable from the enclosing scope.
* The outer function must return the inner function.

---

## 24. How do you inspect a closure's captured variables?

### Answer

Use `.__closure__` and `.cell_contents`.

Example:

```python
def make_adder(n):
    def adder(x):
        return x + n
    return adder

add5 = make_adder(5)

print(add5.__closure__[0].cell_contents)
```

Output:

```
5
```

---

## 25. What is the closure loop variable trap?

### Answer

All lambdas in a loop capture the same variable reference, not its value at the time of creation.

Wrong:

```python
funcs = [lambda: i for i in range(3)]
print([f() for f in funcs])
```

Output:

```
[2, 2, 2]
```

Correct — bind the value at definition time using a default argument:

```python
funcs = [lambda i=i: i for i in range(3)]
print([f() for f in funcs])
```

Output:

```
[0, 1, 2]
```

### Key Interview Points

* The variable `i` is looked up when the function is called, not when it is defined.
* A very commonly asked Python interview trap.

---

## 26. What does "first-class function" mean?

### Answer

Functions in Python are first-class objects. They can be:

* Assigned to variables
* Passed as arguments
* Returned from other functions
* Stored in data structures

Example:

```python
def shout(text):
    return text.upper()

say = shout
print(say("hello"))
```

Output:

```
HELLO
```

### Key Interview Points

* This is the foundation for decorators, callbacks, and functional programming in Python.

---

## 27. What is a higher-order function?

### Answer

A function that takes another function as an argument or returns a function.

Example:

```python
def apply_twice(f, x):
    return f(f(x))

print(apply_twice(lambda x: x + 3, 10))
```

Output:

```
16
```

### Key Interview Points

* `map()`, `filter()`, `sorted()` are all built-in higher-order functions.
* Decorators are also higher-order functions.

---

## 28. What is `map()`?

### Answer

`map()` applies a function to every element of an iterable and returns a map object.

Example:

```python
nums = [1, 2, 3, 4, 5]
squares = list(map(lambda x: x ** 2, nums))
print(squares)
```

Output:

```
[1, 4, 9, 16, 25]
```

### Key Interview Points

* Returns a lazy iterator — wrap with `list()` to see all results.
* Can accept multiple iterables.

---

## 29. What is `filter()`?

### Answer

`filter()` returns only the elements for which the function returns `True`.

Example:

```python
nums = [1, 2, 3, 4, 5, 6]
evens = list(filter(lambda x: x % 2 == 0, nums))
print(evens)
```

Output:

```
[2, 4, 6]
```

### Key Interview Points

* Also returns a lazy iterator.
* Passing `None` as the function filters out falsy values.

---

## 30. What is `reduce()`?

### Answer

`reduce()` folds a list into a single value by applying a function cumulatively.

Example:

```python
from functools import reduce

nums = [1, 2, 3, 4, 5]
total = reduce(lambda acc, x: acc + x, nums)
print(total)
```

Output:

```
15
```

### Key Interview Points

* Moved to `functools` in Python 3.
* Often replaceable with a simple loop or built-ins like `sum()`.

---

## 31. What is the difference between `map()`/`filter()` and list comprehensions?

### Answer

### map() / filter()

```python
squares = list(map(lambda x: x**2, range(5)))
evens   = list(filter(lambda x: x % 2 == 0, range(10)))
```

### List comprehensions

```python
squares = [x**2 for x in range(5)]
evens   = [x for x in range(10) if x % 2 == 0]
```

### Key Interview Points

* List comprehensions are generally more readable and Pythonic.
* `map()` and `filter()` are useful when passing an already-named function.

---

## 32. What is recursion?

### Answer

Recursion is when a function calls itself to solve a smaller version of the same problem.

Every recursive function needs:

* A **base case** to stop recursion.
* A **recursive case** that moves toward the base case.

Example:

```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n - 1)

print(factorial(5))
```

Output:

```
120
```

---

## 33. What is the base case in recursion?

### Answer

The base case is the condition under which the function stops calling itself.

Without a base case, recursion runs forever and causes a `RecursionError`.

Example:

```python
def countdown(n):
    if n == 0:        # base case
        print("Done!")
        return
    print(n)
    countdown(n - 1)

countdown(3)
```

Output:

```
3
2
1
Done!
```

---

## 34. What is Python's recursion limit?

### Answer

The default limit is 1000 frames.

```python
import sys
print(sys.getrecursionlimit())
```

Output:

```
1000
```

You can change it:

```python
sys.setrecursionlimit(5000)
```

### Key Interview Points

* Exceeding the limit raises `RecursionError`.
* For deeply recursive problems, prefer an iterative approach.

---

## 35. What is memoization?

### Answer

Memoization caches the results of function calls so repeated calls with the same input are not recomputed.

Example:

```python
from functools import lru_cache

@lru_cache(maxsize=None)
def fib(n):
    if n <= 1:
        return n
    return fib(n - 1) + fib(n - 2)

print(fib(50))
```

Output:

```
12586269025
```

### Key Interview Points

* Without memoization, `fib(50)` makes ~2^50 calls.
* With `lru_cache`, it makes just 50 unique calls.
* `maxsize=None` means unlimited cache size.

---

## 36. Fibonacci — recursive vs iterative

### Answer

### Recursive (without memoization)

```python
def fib(n):
    if n <= 1:
        return n
    return fib(n-1) + fib(n-2)
```

Complexity:

```
Time:  O(2^n)
Space: O(n)
```

### Iterative

```python
def fib(n):
    a, b = 0, 1
    for _ in range(n):
        a, b = b, a + b
    return a
```

Complexity:

```
Time:  O(n)
Space: O(1)
```

### Key Interview Points

* Prefer iterative for performance.
* Use `@lru_cache` to get memoization benefits while keeping recursive style.

---

## 37. What are type hints in functions?

### Answer

Type hints annotate the expected types of arguments and return values.

Example:

```python
def add(a: int, b: int) -> int:
    return a + b
```

### Key Interview Points

* Type hints are **not enforced at runtime**.
* Used by IDEs and tools like `mypy` for static analysis.
* Introduced in Python 3.5 via PEP 484.

---

## 38. How do you use Optional and Union in type hints?

### Answer

```python
from typing import Optional, Union

def greet(name: Optional[str] = None) -> str:
    return f"Hello, {name or 'World'}!"

def process(val: Union[int, float]) -> float:
    return float(val)
```

### Key Interview Points

* `Optional[str]` is shorthand for `Union[str, None]`.
* Python 3.10+ allows `str | None` syntax instead.

---

## 39. What is `functools.partial`?

### Answer

`partial` creates a new function with some arguments pre-filled.

Example:

```python
from functools import partial

def power(base, exp):
    return base ** exp

square = partial(power, exp=2)
cube   = partial(power, exp=3)

print(square(5))
print(cube(3))
```

Output:

```
25
27
```

### Key Interview Points

* Useful for adapting functions to APIs that expect fewer arguments.
* Common in event handlers and functional pipelines.

---

## 40. What does bare `*` in a function signature mean?

### Answer

A bare `*` forces all arguments after it to be keyword-only.

Example:

```python
def func(a, b, *, c, d):
    print(a, b, c, d)

func(1, 2, c=3, d=4)
```

Output:

```
1 2 3 4
```

Calling with positional arguments after `*`:

```python
func(1, 2, 3, 4)
```

Output:

```
TypeError: func() takes 2 positional arguments but 4 were given
```

### Key Interview Points

* Does not collect extra positional arguments like `*args` does.
* Makes function calls more explicit and self-documenting.

---

## 41. What does `/` in a function signature mean?

### Answer

`/` makes all arguments before it positional-only (Python 3.8+).

Example:

```python
def func(a, b, /, c, d):
    print(a, b, c, d)

func(1, 2, c=3, d=4)
```

Output:

```
1 2 3 4
```

Calling with keyword for positional-only argument:

```python
func(a=1, b=2, c=3, d=4)
```

Output:

```
TypeError: func() got some positional-only arguments passed as keyword arguments: 'a, b'
```

### Key Interview Points

* Used in many Python built-ins like `len()` and `abs()`.
* Prevents callers from relying on internal parameter names.

---

## 42. What is a generator function?

### Answer

A generator function uses `yield` instead of `return` and produces values lazily.

Example:

```python
def count_up(n):
    for i in range(n):
        yield i

gen = count_up(3)

print(next(gen))
print(next(gen))
print(next(gen))
```

Output:

```
0
1
2
```

### Key Interview Points

* State is preserved between `next()` calls.
* Far more memory-efficient than returning a full list.
* Covered in depth in `10_Iterators_Generators.md`.

---

## 43. What is the difference between `return` and `yield`?

### Answer

| | `return` | `yield` |
|---|---|---|
| Function type | Regular | Generator |
| Returns | A value once | Values lazily, one at a time |
| State | Lost after return | Preserved between calls |
| Memory | Full result at once | One value at a time |

Example:

```python
def regular():
    return [1, 2, 3]

def generator():
    yield 1
    yield 2
    yield 3
```

---

## 44. What is an inner function?

### Answer

A function defined inside another function.

Example:

```python
def outer():
    def inner():
        print("I am inner")
    inner()

outer()
```

Output:

```
I am inner
```

### Key Interview Points

* Inner functions are private to the outer function.
* Used to implement closures, decorators, and helper utilities.

---

## 45. How is a function an object in Python?

### Answer

Functions have attributes and can be manipulated at runtime.

Example:

```python
def greet():
    """Says hello."""
    pass

print(type(greet))
print(greet.__name__)
print(greet.__doc__)
```

Output:

```
<class 'function'>
greet
Says hello.
```

### Key Interview Points

* Functions have `__name__`, `__doc__`, `__annotations__`, `__defaults__`, `__code__`.
* This makes decorators, `functools.wraps`, and introspection possible.

---

## 46. What is a decorator in Python?

### Answer

A decorator is a higher-order function that wraps another function to extend or modify its behavior without changing its source code.

Example:

```python
def logger(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

@logger
def add(a, b):
    return a + b

print(add(2, 3))
```

Output:

```
Calling add
5
```

### Key Interview Points

* `@logger` is syntactic sugar for `add = logger(add)`.
* Covered in depth in `11_Decorators.md`.

---

## 47. What is `functools.wraps` and why is it important?

### Answer

`functools.wraps` preserves the original function's metadata when creating a decorator.

Without `wraps`:

```python
def logger(func):
    def wrapper(*args, **kwargs):
        return func(*args, **kwargs)
    return wrapper

@logger
def add(a, b):
    """Adds two numbers."""
    return a + b

print(add.__name__)
print(add.__doc__)
```

Output:

```
wrapper
None
```

With `wraps`:

```python
from functools import wraps

def logger(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        return func(*args, **kwargs)
    return wrapper

@logger
def add(a, b):
    """Adds two numbers."""
    return a + b

print(add.__name__)
print(add.__doc__)
```

Output:

```
add
Adds two numbers.
```

### Key Interview Points

* Always use `@wraps` when writing decorators.
* Preserves `__name__`, `__doc__`, `__annotations__`.

---

## 48. What is the difference between a function call and a function reference?

### Answer

A **function reference** points to the function object.

```python
def greet():
    print("Hello")

ref = greet       # reference — no parentheses
```

A **function call** executes the function.

```python
greet()           # call — with parentheses
```

### Key Interview Points

* Passing `greet` to another function passes the reference.
* Passing `greet()` passes the return value of the function.

---

## 49. What is an anonymous function?

### Answer

An anonymous function has no name. In Python, it is created using `lambda`.

Example:

```python
result = (lambda x, y: x + y)(3, 4)
print(result)
```

Output:

```
7
```

### Key Interview Points

* Lambda functions are anonymous because they are not bound to a name via `def`.
* Can be defined and immediately called (IIFE pattern).

---

## 50. What is the difference between `sorted()` and `.sort()`?

### Answer

`sorted()` returns a new sorted list and works on any iterable.

```python
nums = [3, 1, 4, 1, 5]
print(sorted(nums))
print(nums)
```

Output:

```
[1, 1, 3, 4, 5]
[3, 1, 4, 1, 5]
```

`.sort()` sorts in-place and returns `None`.

```python
nums.sort()
print(nums)
```

Output:

```
[1, 1, 3, 4, 5]
```

### Key Interview Points

* `sorted()` — non-destructive, works on any iterable.
* `.sort()` — in-place, list only, more memory-efficient.

---

## 51. How do you pass a function as an argument?

### Answer

Simply pass the function name without parentheses.

Example:

```python
def square(x):
    return x ** 2

def apply(func, value):
    return func(value)

print(apply(square, 5))
```

Output:

```
25
```

---

## 52. How do you return a function from another function?

### Answer

Return the function object (without calling it).

Example:

```python
def make_greeter(greeting):
    def greeter(name):
        return f"{greeting}, {name}!"
    return greeter

hello = make_greeter("Hello")
hi    = make_greeter("Hi")

print(hello("Alice"))
print(hi("Bob"))
```

Output:

```
Hello, Alice!
Hi, Bob!
```

---

## 53. What is a recursive data structure example with functions?

### Answer

Calculating the sum of a nested list using recursion.

Example:

```python
def nested_sum(lst):
    total = 0
    for item in lst:
        if isinstance(item, list):
            total += nested_sum(item)
        else:
            total += item
    return total

print(nested_sum([1, [2, [3, 4], 5], 6]))
```

Output:

```
21
```

---

## 54. What is tail recursion? Does Python support it?

### Answer

Tail recursion is when the recursive call is the very last operation in the function.

Example in tail-recursive style:

```python
def factorial(n, acc=1):
    if n == 0:
        return acc
    return factorial(n - 1, acc * n)
```

### Key Interview Points

* Python does **not** optimize tail recursion.
* Each call still adds a new frame to the call stack.
* Guido van Rossum has explicitly stated this is intentional.

---

## 55. What is the call stack?

### Answer

The call stack is the data structure Python uses to track active function calls.

Example:

```python
def c():
    print("In c")

def b():
    c()

def a():
    b()

a()
```

Call stack at deepest point:

```
a → b → c
```

### Key Interview Points

* Each function call pushes a frame onto the stack.
* When the function returns, the frame is popped.
* Stack overflow in recursion raises `RecursionError`.

---

## 56. What is the difference between `pass`, `return`, and `return None`?

### Answer

`pass` — does nothing, used as a placeholder.

```python
def empty():
    pass
```

`return` — exits the function and returns `None`.

```python
def early_exit(x):
    if x < 0:
        return
    print(x)
```

`return None` — explicitly returns `None`.

```python
def explicit():
    return None
```

### Key Interview Points

* All three result in `None` being returned.
* `pass` does not exit the function; `return` does.

---

## 57. What is function composition?

### Answer

Function composition is the process of combining functions where the output of one becomes the input of another.

Example:

```python
def double(x):
    return x * 2

def increment(x):
    return x + 1

def compose(f, g):
    return lambda x: f(g(x))

double_then_increment = compose(increment, double)
print(double_then_increment(5))
```

Output:

```
11
```

---

## 58. What is the `zip()` function and how is it used with functions?

### Answer

`zip()` pairs elements from multiple iterables.

Example:

```python
names  = ["Alice", "Bob", "Charlie"]
scores = [90, 85, 92]

for name, score in zip(names, scores):
    print(f"{name}: {score}")
```

Output:

```
Alice: 90
Bob: 85
Charlie: 92
```

### Key Interview Points

* Returns a lazy iterator.
* Stops at the shortest iterable.

---

## 59. What is `enumerate()` and how is it used?

### Answer

`enumerate()` adds a counter to an iterable.

Example:

```python
fruits = ["apple", "banana", "cherry"]

for i, fruit in enumerate(fruits, start=1):
    print(i, fruit)
```

Output:

```
1 apple
2 banana
3 cherry
```

### Key Interview Points

* Avoids manually tracking index variables.
* `start` parameter sets the beginning counter value.

---

## 60. How do you write a function that accepts any number of arguments of any type?

### Answer

Combine `*args` and `**kwargs`.

Example:

```python
def flexible(*args, **kwargs):
    print("Positional:", args)
    print("Keyword:", kwargs)

flexible(1, "hello", True, name="Alice", age=30)
```

Output:

```
Positional: (1, 'hello', True)
Keyword: {'name': 'Alice', 'age': 30}
```

---

## 61. What is a pure function?

### Answer

A pure function always produces the same output for the same input and has no side effects.

Example (pure):

```python
def add(a, b):
    return a + b
```

Example (impure — has side effect):

```python
total = 0

def add_to_total(x):
    global total
    total += x
```

### Key Interview Points

* Pure functions are easier to test, debug, and parallelize.
* Functional programming favors pure functions.

---

## 62. What is a side effect in a function?

### Answer

A side effect is any change a function makes outside its own scope.

Examples of side effects:

* Modifying a global variable
* Writing to a file
* Printing to the console
* Mutating a list passed as an argument

Example:

```python
def append_item(lst, item):
    lst.append(item)    # mutates the caller's list — side effect

my_list = [1, 2, 3]
append_item(my_list, 4)
print(my_list)
```

Output:

```
[1, 2, 3, 4]
```

---

## 63. How do you prevent a function from modifying a passed list?

### Answer

Pass a copy of the list.

Example:

```python
def process(lst):
    lst = lst[:]        # work on a copy
    lst.append(99)
    return lst

original = [1, 2, 3]
result = process(original)

print(original)
print(result)
```

Output:

```
[1, 2, 3]
[1, 2, 3, 99]
```

---

## 64. What is function introspection?

### Answer

Inspecting a function's properties at runtime.

Example:

```python
def add(a: int, b: int) -> int:
    """Return sum."""
    return a + b

print(add.__name__)
print(add.__doc__)
print(add.__annotations__)
print(add.__defaults__)
```

Output:

```
add
Return sum.
{'a': <class 'int'>, 'b': <class 'int'>, 'return': <class 'int'>}
None
```

---

## 65. What is `inspect` module used for?

### Answer

The `inspect` module provides detailed information about live objects including functions.

Example:

```python
import inspect

def add(a, b=10):
    return a + b

print(inspect.signature(add))
print(inspect.getfullargspec(add))
```

Output:

```
(a, b=10)
FullArgSpec(args=['a', 'b'], varargs=None, varkw=None, defaults=(10,), ...)
```

### Key Interview Points

* Used in frameworks, testing tools, and documentation generators.

---

## 66. What is the difference between `getfullargspec` and `signature`?

### Answer

`inspect.getfullargspec()` — returns a named tuple with raw argument details.

`inspect.signature()` — returns a modern `Signature` object supporting rich inspection.

Example:

```python
import inspect

def func(a, b=5, *args, **kwargs):
    pass

print(inspect.signature(func))
```

Output:

```
(a, b=5, *args, **kwargs)
```

### Key Interview Points

* `signature()` is preferred in modern Python (3.3+).
* `getfullargspec()` is older but still widely used.

---

## 67. Implement factorial without recursion.

### Answer

```python
def factorial(n):
    result = 1
    for i in range(2, n + 1):
        result *= i
    return result

print(factorial(5))
```

Output:

```
120
```

### Complexity

```
Time:  O(n)
Space: O(1)
```

---

## 68. Implement a function that flattens a nested list.

### Answer

```python
def flatten(lst):
    result = []
    for item in lst:
        if isinstance(item, list):
            result.extend(flatten(item))
        else:
            result.append(item)
    return result

print(flatten([1, [2, [3, 4]], 5]))
```

Output:

```
[1, 2, 3, 4, 5]
```

---

## 69. Implement a memoization decorator from scratch.

### Answer

```python
def memoize(func):
    cache = {}
    def wrapper(*args):
        if args not in cache:
            cache[args] = func(*args)
        return cache[args]
    return wrapper

@memoize
def fib(n):
    if n <= 1:
        return n
    return fib(n-1) + fib(n-2)

print(fib(30))
```

Output:

```
832040
```

---

## 70. Implement `map()` from scratch.

### Answer

```python
def my_map(func, iterable):
    result = []
    for item in iterable:
        result.append(func(item))
    return result

print(my_map(lambda x: x**2, [1, 2, 3, 4]))
```

Output:

```
[1, 4, 9, 16]
```

---

## 71. Implement `filter()` from scratch.

### Answer

```python
def my_filter(func, iterable):
    result = []
    for item in iterable:
        if func(item):
            result.append(item)
    return result

print(my_filter(lambda x: x % 2 == 0, [1, 2, 3, 4, 5, 6]))
```

Output:

```
[2, 4, 6]
```

---

## 72. Implement `reduce()` from scratch.

### Answer

```python
def my_reduce(func, iterable):
    it = iter(iterable)
    acc = next(it)
    for item in it:
        acc = func(acc, item)
    return acc

print(my_reduce(lambda a, b: a + b, [1, 2, 3, 4, 5]))
```

Output:

```
15
```

---

## 73. Write a function that returns another function (counter example).

### Answer

```python
def make_counter():
    count = 0
    def counter():
        nonlocal count
        count += 1
        return count
    return counter

c1 = make_counter()
c2 = make_counter()

print(c1())
print(c1())
print(c2())
```

Output:

```
1
2
1
```

### Key Interview Points

* Each call to `make_counter()` creates an independent counter.
* Classic closure example.

---

## 74. Write a function to calculate the power of a number using recursion.

### Answer

```python
def power(base, exp):
    if exp == 0:
        return 1
    return base * power(base, exp - 1)

print(power(2, 10))
```

Output:

```
1024
```

### Complexity

```
Time:  O(n)
Space: O(n)
```

---

## 75. Write a function to find the GCD of two numbers.

### Answer

```python
def gcd(a, b):
    while b:
        a, b = b, a % b
    return a

print(gcd(48, 18))
```

Output:

```
6
```

---

## 76. Write a function to check if a number is prime.

### Answer

```python
def is_prime(n):
    if n < 2:
        return False
    for i in range(2, int(n**0.5) + 1):
        if n % i == 0:
            return False
    return True

print(is_prime(17))
print(is_prime(18))
```

Output:

```
True
False
```

### Complexity

```
Time: O(√n)
```

---

## 77. Write a function to generate all prime numbers up to n (Sieve of Eratosthenes).

### Answer

```python
def sieve(n):
    primes = [True] * (n + 1)
    primes[0] = primes[1] = False

    for i in range(2, int(n**0.5) + 1):
        if primes[i]:
            for j in range(i*i, n+1, i):
                primes[j] = False

    return [i for i, p in enumerate(primes) if p]

print(sieve(30))
```

Output:

```
[2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
```

---

## 78. Write a binary search function.

### Answer

```python
def binary_search(arr, target):
    lo, hi = 0, len(arr) - 1

    while lo <= hi:
        mid = (lo + hi) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            lo = mid + 1
        else:
            hi = mid - 1

    return -1

print(binary_search([1, 3, 5, 7, 9, 11], 7))
```

Output:

```
3
```

### Complexity

```
Time:  O(log n)
Space: O(1)
```

---

## 79. Write a function to count occurrences of each element in a list.

### Answer

```python
from collections import Counter

def count_elements(lst):
    return Counter(lst)

print(count_elements([1, 2, 2, 3, 3, 3, 4]))
```

Output:

```
Counter({3: 3, 2: 2, 1: 1, 4: 1})
```

---

## 80. Write a function to remove duplicates from a list while preserving order.

### Answer

```python
def remove_duplicates(lst):
    seen = set()
    result = []
    for item in lst:
        if item not in seen:
            seen.add(item)
            result.append(item)
    return result

print(remove_duplicates([1, 3, 2, 1, 4, 3, 5]))
```

Output:

```
[1, 3, 2, 4, 5]
```

---

## 81. Write a function to find the second largest element in a list.

### Answer

```python
def second_largest(lst):
    unique = list(set(lst))
    unique.sort()
    return unique[-2]

print(second_largest([10, 20, 4, 45, 99, 99]))
```

Output:

```
45
```

---

## 82. Write a function to rotate a list by k positions.

### Answer

```python
def rotate(lst, k):
    k = k % len(lst)
    return lst[-k:] + lst[:-k]

print(rotate([1, 2, 3, 4, 5], 2))
```

Output:

```
[4, 5, 1, 2, 3]
```

---

## 83. Write a function to merge two sorted lists.

### Answer

```python
def merge_sorted(a, b):
    result = []
    i = j = 0

    while i < len(a) and j < len(b):
        if a[i] <= b[j]:
            result.append(a[i])
            i += 1
        else:
            result.append(b[j])
            j += 1

    result.extend(a[i:])
    result.extend(b[j:])
    return result

print(merge_sorted([1, 3, 5], [2, 4, 6]))
```

Output:

```
[1, 2, 3, 4, 5, 6]
```

---

## 84. Write a function to check if two lists are equal ignoring order.

### Answer

```python
def equal_ignoring_order(a, b):
    return sorted(a) == sorted(b)

print(equal_ignoring_order([1, 2, 3], [3, 1, 2]))
print(equal_ignoring_order([1, 2, 3], [1, 2, 4]))
```

Output:

```
True
False
```

---

## 85. Write a function that caches results with a size limit.

### Answer

```python
from functools import lru_cache

@lru_cache(maxsize=5)
def expensive(n):
    print(f"Computing {n}")
    return n * n

print(expensive(3))
print(expensive(3))
print(expensive(4))
```

Output:

```
Computing 3
9
9
Computing 4
16
```

### Key Interview Points

* The second call for `expensive(3)` does not recompute.
* When cache is full, least recently used entry is evicted.

---

## 86. What is the time complexity of calling a function?

### Answer

Function call overhead is:

```
O(1)
```

Creating the stack frame and binding arguments is constant time.

### Key Interview Points

* The complexity of the function body is separate from call overhead.
* Deeply nested recursion adds O(n) stack frame overhead.

---

## 87. What is the space complexity of recursion?

### Answer

Each recursive call adds a frame to the call stack.

Example — factorial:

```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n - 1)
```

Space complexity:

```
O(n)
```

### Key Interview Points

* n frames are live on the stack simultaneously.
* This is why deep recursion causes `RecursionError`.

---

## 88. What is the time complexity of `map()` and `filter()`?

### Answer

Both iterate over every element once.

```
O(n)
```

where n is the length of the iterable.

### Key Interview Points

* They are lazy — the computation happens only when values are consumed.
* Wrapping with `list()` triggers full evaluation in O(n).

---

## 89. What is the time complexity of `functools.lru_cache` lookups?

### Answer

Cache lookup is a dictionary lookup:

```
O(1) average
```

### Key Interview Points

* Cache key is built from the function arguments.
* Arguments must be hashable to use `lru_cache`.

---

## 90. How does Python handle function argument passing — by value or by reference?

### Answer

Python uses **pass by object reference** (also called pass by assignment).

* Immutable objects (int, str, tuple) — cannot be changed inside the function.
* Mutable objects (list, dict, set) — can be mutated inside the function.

Example:

```python
def modify(lst, num):
    lst.append(99)   # mutates the original
    num += 1         # rebinds local variable only

my_list = [1, 2, 3]
my_num  = 10

modify(my_list, my_num)

print(my_list)
print(my_num)
```

Output:

```
[1, 2, 3, 99]
10
```

### Key Interview Points

* Python does not copy objects when passing to functions.
* Reassigning the parameter variable does not affect the caller.

---

## 91. Why is it wrong to say Python passes by value or by reference?

### Answer

* **By value** — Python does not copy objects.
* **By reference** — Python does not allow full reference replacement like C++.

The correct term is **pass by object reference**:

* The reference to the object is passed.
* You can mutate a mutable object through the reference.
* You cannot make the caller's variable point to a new object.

Example:

```python
def try_replace(lst):
    lst = [99, 100]   # rebinds local variable, caller unchanged

data = [1, 2, 3]
try_replace(data)
print(data)
```

Output:

```
[1, 2, 3]
```

---

## 92. What is function overloading? Does Python support it?

### Answer

Function overloading means having multiple functions with the same name but different parameter types or counts.

Python does **not** support traditional overloading.

Python's approach:

```python
def process(value, multiplier=1):
    return value * multiplier

print(process(5))
print(process(5, 3))
print(process("Hi ", 3))
```

Output:

```
5
15
Hi Hi Hi
```

### Key Interview Points

* Python achieves similar behavior using default arguments, `*args`, `**kwargs`.
* The `functools.singledispatch` decorator enables type-based dispatch.

---

## 93. What is `functools.singledispatch`?

### Answer

`singledispatch` allows different function implementations to be selected based on the type of the first argument.

Example:

```python
from functools import singledispatch

@singledispatch
def process(value):
    print(f"Default: {value}")

@process.register(int)
def _(value):
    print(f"Integer: {value * 2}")

@process.register(str)
def _(value):
    print(f"String: {value.upper()}")

process(10)
process("hello")
process([1, 2])
```

Output:

```
Integer: 20
String: HELLO
Default: [1, 2]
```

---

## 94. How do you time a function's execution?

### Answer

Using `time` module:

```python
import time

def slow():
    time.sleep(0.5)

start = time.time()
slow()
end = time.time()

print(f"Elapsed: {end - start:.3f}s")
```

Output:

```
Elapsed: 0.500s
```

Using `timeit`:

```python
import timeit

print(timeit.timeit("sum(range(1000))", number=10000))
```

---

## 95. What is a stub function?

### Answer

A stub is a placeholder function used during development or testing.

Example:

```python
def send_email(to, subject, body):
    pass   # stub — not implemented yet
```

### Key Interview Points

* Allows calling code to be written before the function is implemented.
* In testing, stubs return fixed values to isolate behavior.

---

## 96. What is the difference between a function and a callable?

### Answer

A **callable** is any object that can be called with `()`.

Functions are callables, but so are:

* Classes
* Instances with `__call__`
* Built-in functions
* Lambda expressions

Example:

```python
class Multiplier:
    def __init__(self, n):
        self.n = n
    def __call__(self, x):
        return x * self.n

double = Multiplier(2)
print(double(5))
```

Output:

```
10
```

### Key Interview Points

* `callable(obj)` returns `True` if the object can be called.
* This is how class instances can behave like functions.

---

## 97. What is `callable()`?

### Answer

`callable()` returns `True` if the object appears callable.

Example:

```python
def greet():
    pass

print(callable(greet))
print(callable(42))
print(callable(print))
```

Output:

```
True
False
True
```

---

## 98. How do you create a function dynamically at runtime?

### Answer

Using `exec()` or `types.FunctionType`.

Example using `exec()`:

```python
code = """
def dynamic_add(a, b):
    return a + b
"""

exec(code)
print(dynamic_add(3, 4))
```

Output:

```
7
```

### Key Interview Points

* `exec()` is powerful but dangerous — avoid with untrusted input.
* Rarely needed in production code.

---

## 99. What are commonly asked function coding problems in Python interviews?

### Answer

#### Recursion Problems
* Factorial
* Fibonacci
* Power of a number
* Sum of digits
* Flatten nested list

#### Functional Programming
* Implement `map()` from scratch
* Implement `filter()` from scratch
* Implement `reduce()` from scratch
* Build a memoization decorator

#### Closure Problems
* Counter using closure
* Make multiplier / adder factory
* Loop variable trap fix

#### Higher-Order Functions
* Function composition
* Apply function n times
* Pipeline of functions

#### Utility Functions
* Binary search
* GCD
* Check prime
* Merge sorted lists

---

## 100. What function-related questions are commonly asked in Python interviews?

### Answer

#### Fundamentals
* `def`, `return`, `None`
* Docstrings
* Arguments: positional, keyword, default, `*args`, `**kwargs`

#### Traps
* Mutable default argument
* Closure loop variable capture
* Pass by reference vs pass by object reference

#### Scope
* LEGB rule
* `global` and `nonlocal`

#### Closures
* What is a closure
* Three conditions for a closure
* Inspecting `__closure__`

#### Functional Programming
* First-class functions
* Higher-order functions
* `map()`, `filter()`, `reduce()`
* `lambda`
* `functools.partial`
* `functools.singledispatch`

#### Recursion
* Base case
* Recursion limit
* Memoization with `lru_cache`

#### Advanced
* Decorators and `functools.wraps`
* Positional-only (`/`) and keyword-only (`*`) parameters
* Generator functions
* `callable()` and `__call__`
* Pass by object reference

### Final Interview Tip

If you master:

* LEGB scope and closures
* `*args` and `**kwargs`
* Mutable default argument trap
* First-class and higher-order functions
* Recursion and memoization
* Decorators

you will be able to answer **95%+ of Python function interview questions** asked in software engineering, data engineering, backend development, and AI engineering interviews.
