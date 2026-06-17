## 1. What is an iterable in Python?

### Answer

An iterable is any object that can be iterated over one element at a time.

### Examples

```python
list
tuple
set
string
dictionary
```

### Example

```python
nums = [1, 2, 3]

for num in nums:
    print(num)
```

### Key Interview Point

An iterable can produce an iterator.

---

## 2. What is an iterator?

### Answer

An iterator is an object that keeps track of the current position during iteration.

### Example

```python
nums = [1, 2, 3]

iterator = iter(nums)

print(next(iterator))
```

### Output

```text
1
```

---

## 3. What is the difference between an iterable and an iterator?

### Answer

| Iterable             | Iterator                      |
| -------------------- | ----------------------------- |
| Collection of data   | Object used for iteration     |
| Uses iter()          | Uses next()                   |
| Can create iterators | Produces values one at a time |

### Example

```python
nums = [1, 2, 3]  # Iterable

it = iter(nums)   # Iterator
```

---

## 4. What is the iter() function?

### Answer

`iter()` converts an iterable into an iterator.

### Example

```python
nums = [10, 20, 30]

it = iter(nums)
```

### Key Interview Point

Every iterator is created using `iter()`.

---

## 5. What is the next() function?

### Answer

`next()` retrieves the next value from an iterator.

### Example

```python
nums = [1, 2, 3]

it = iter(nums)

print(next(it))
```

### Output

```text
1
```

---

## 6. What happens when next() reaches the end?

### Answer

Python raises:

```python
StopIteration
```

### Example

```python
nums = [1]

it = iter(nums)

next(it)
next(it)
```

### Output

```text
StopIteration
```

---

## 7. What is StopIteration?

### Answer

An exception raised when no more items remain in an iterator.

### Example

```python
it = iter([1])

next(it)
next(it)
```

### Key Interview Point

Signals iteration completion.

---

## 8. How does a for loop work internally?

### Answer

A `for` loop automatically uses:

```python
iter()
next()
StopIteration
```

### Internal Flow

```python
it = iter(data)

while True:
    try:
        item = next(it)

    except StopIteration:
        break
```

---

## 9. Which objects are iterable?

### Answer

Examples:

```python
list
tuple
set
dict
string
range
```

### Example

```python
for char in "Python":
    print(char)
```

---

## 10. Is a dictionary iterable?

### Answer

Yes.

By default it iterates over keys.

### Example

```python
data = {
    "a": 1,
    "b": 2
}

for key in data:
    print(key)
```

---

## 11. How do you check if an object is iterable?

### Answer

Using:

```python
from collections.abc import Iterable
```

### Example

```python
from collections.abc import Iterable

print(
    isinstance([1,2,3], Iterable)
)
```

### Output

```python
True
```

---

## 12. How do you check if an object is an iterator?

### Answer

Using:

```python
from collections.abc import Iterator
```

### Example

```python
from collections.abc import Iterator

it = iter([1,2,3])

print(
    isinstance(it, Iterator)
)
```

---

## 13. Can an iterator be reused?

### Answer

No.

Once exhausted, it cannot restart automatically.

### Example

```python
it = iter([1,2])

next(it)
next(it)
```

Iterator is exhausted.

---

## 14. How do you restart iteration?

### Answer

Create a new iterator.

### Example

```python
nums = [1,2,3]

it = iter(nums)

it = iter(nums)
```

---

## 15. What methods must an iterator implement?

### Answer

An iterator must implement:

```python
__iter__()
__next__()
```

### Key Interview Point

Core iterator protocol question.

---

## 16. What does **iter**() do?

### Answer

Returns the iterator object itself.

### Example

```python
def __iter__(self):
    return self
```

---

## 17. What does **next**() do?

### Answer

Returns the next item.

### Example

```python
def __next__(self):
    return value
```

### Key Interview Point

Raises StopIteration when finished.

---

## 18. How do custom iterators work?

### Answer

By implementing:

```python
__iter__()
__next__()
```

### Example

```python
class Counter:

    def __iter__(self):
        return self

    def __next__(self):
        pass
```

---

## 19. Create a simple custom iterator.

### Answer

```python
class Counter:

    def __init__(self):
        self.num = 1

    def __iter__(self):
        return self

    def __next__(self):

        if self.num > 3:
            raise StopIteration

        value = self.num
        self.num += 1

        return value
```

---

## 20. What is lazy evaluation?

### Answer

Values are generated only when needed.

### Example

```python
range(1000000)
```

does not store all values immediately.

### Key Interview Point

Generators rely heavily on lazy evaluation.

---

## 21. Why are iterators memory efficient?

### Answer

They generate values one at a time.

### Example

```python
range(1000000000)
```

Consumes very little memory.

---

## 22. What is range()?

### Answer

A built-in iterable that generates numbers lazily.

### Example

```python
for num in range(5):
    print(num)
```

Output

```text
0
1
2
3
4
```

---

## 23. Is range() an iterator?

### Answer

No.

It is an iterable.

### Example

```python
r = range(5)

it = iter(r)
```

---

## 24. Why isn't a list an iterator?

### Answer

Lists support iteration but do not maintain iteration state.

### Example

```python
nums = [1,2,3]

iter(nums)
```

creates an iterator.

---

## 25. What are the advantages of iterators?

### Answer

Benefits:

* Memory efficiency
* Lazy evaluation
* Faster processing
* Useful for large datasets
* Supports streaming data

### Key Interview Point

Iterators are heavily used in Data Engineering and Machine Learning pipelines.

---

## 26. What is a generator in Python?

### Answer

A generator is a special function that produces values one at a time using the `yield` keyword.

### Example

```python
def numbers():
    yield 1
    yield 2
    yield 3
```

### Key Interview Point

Generators are memory-efficient because they generate values lazily.

---

## 27. What is the yield keyword?

### Answer

`yield` pauses function execution and returns a value.

### Example

```python
def greet():
    yield "Hello"
```

### Difference from return

| return              | yield                             |
| ------------------- | --------------------------------- |
| Terminates function | Pauses function                   |
| Returns one value   | Returns multiple values over time |

---

## 28. How does yield work?

### Answer

When `yield` is encountered:

1. Current state is saved
2. Value is returned
3. Execution resumes later

### Example

```python
def demo():
    yield 1
    yield 2
```

---

## 29. What does a generator function return?

### Answer

A generator function returns a generator object.

### Example

```python
def nums():
    yield 1

g = nums()

print(type(g))
```

### Output

```text
<class 'generator'>
```

---

## 30. How do you iterate over a generator?

### Answer

Using a loop.

### Example

```python
def nums():
    yield 1
    yield 2

for num in nums():
    print(num)
```

---

## 31. How do you get values manually from a generator?

### Answer

Using `next()`.

### Example

```python
def nums():
    yield 1
    yield 2

g = nums()

print(next(g))
print(next(g))
```

---

## 32. What happens after the last yield?

### Answer

Python raises:

```python
StopIteration
```

### Example

```python
next(generator)
```

after completion raises the exception.

---

## 33. Why are generators memory efficient?

### Answer

They generate values on demand.

### Example

```python
def million():
    for i in range(1000000):
        yield i
```

### Key Interview Point

Only one value exists in memory at a time.

---

## 34. What is lazy evaluation in generators?

### Answer

Values are produced only when requested.

### Example

```python
g = (x*x for x in range(1000000))
```

No computation occurs until iteration begins.

---

## 35. What is a generator expression?

### Answer

A concise way to create generators.

### Syntax

```python
(expression for item in iterable)
```

### Example

```python
squares = (
    x*x
    for x in range(5)
)
```

---

## 36. Generator expression vs list comprehension?

### Answer

| Generator   | List Comprehension |
| ----------- | ------------------ |
| Uses ()     | Uses []            |
| Lazy        | Eager              |
| Less memory | More memory        |

### Example

```python
(x*x for x in range(5))
```

```python
[x*x for x in range(5)]
```

---

## 37. What is the advantage of generator expressions?

### Answer

Benefits:

* Faster startup
* Lower memory usage
* Better scalability

### Example

Useful for large datasets.

---

## 38. What is an infinite generator?

### Answer

A generator that never ends.

### Example

```python
def count():

    num = 1

    while True:
        yield num
        num += 1
```

---

## 39. How can infinite generators be controlled?

### Answer

Using conditions.

### Example

```python
for num in count():

    if num == 10:
        break
```

---

## 40. What is the send() method?

### Answer

Used to send values into a generator.

### Example

```python
def gen():

    value = yield

    print(value)

g = gen()

next(g)

g.send("Hello")
```

---

## 41. Why is send() useful?

### Answer

Allows two-way communication with generators.

### Use Cases

* Coroutines
* Event processing
* Pipelines

---

## 42. What is the close() method?

### Answer

Terminates a generator.

### Example

```python
g.close()
```

### Key Interview Point

Raises GeneratorExit internally.

---

## 43. What happens after close()?

### Answer

Further iteration stops.

### Example

```python
g.close()

next(g)
```

Output

```python
StopIteration
```

---

## 44. What is GeneratorExit?

### Answer

Exception raised when a generator is closed.

### Example

```python
try:
    yield

except GeneratorExit:
    print("Closing")
```

---

## 45. What is throw()?

### Answer

Injects an exception into a generator.

### Example

```python
g.throw(ValueError)
```

### Key Interview Point

Advanced interview topic.

---

## 46. Why use throw()?

### Answer

Useful for:

* Error handling
* Coroutine control
* Testing

### Example

```python
generator.throw(Exception)
```

---

## 47. What is yield from?

### Answer

Delegates iteration to another iterable.

### Example

```python
def gen():

    yield from [1, 2, 3]
```

Output

```text
1
2
3
```

---

## 48. Why use yield from?

### Answer

Benefits:

* Cleaner code
* Simpler delegation
* Better readability

### Example

```python
yield from generator()
```

---

## 49. What is generator delegation?

### Answer

Passing iteration responsibility to another generator.

### Example

```python
def child():
    yield 1

def parent():
    yield from child()
```

---

## 50. What are the advantages of generators?

### Answer

Benefits:

* Memory efficient
* Faster startup
* Lazy evaluation
* Infinite sequences
* Streaming support

### Key Interview Point

Generators are heavily used in:

* Data Engineering
* Machine Learning
* Backend Development
* Big Data Processing

---

## 51. What is a coroutine in Python?

### Answer

A coroutine is a special type of generator that can consume values using `send()`.

### Example

```python
def coroutine():

    while True:
        value = yield

        print(value)
```

### Key Interview Point

Coroutines support two-way communication.

---

## 52. How is a coroutine different from a generator?

### Answer

| Generator             | Coroutine             |
| --------------------- | --------------------- |
| Produces values       | Consumes values       |
| Uses yield to return  | Uses yield to receive |
| One-way communication | Two-way communication |

---

## 53. What is generator state preservation?

### Answer

Generators automatically save:

* Local variables
* Instruction pointer
* Execution context

### Example

```python
def demo():

    x = 10

    yield x

    x += 5

    yield x
```

Output:

```text
10
15
```

---

## 54. What are generator pipelines?

### Answer

Multiple generators connected together.

### Example

```python
data
 ↓
filter()
 ↓
transform()
 ↓
output()
```

### Key Interview Point

Common in data engineering systems.

---

## 55. What is lazy processing?

### Answer

Processing data only when needed.

### Example

```python
(x*x for x in range(1000000))
```

### Benefit

Avoids unnecessary computation.

---

## 56. What is itertools?

### Answer

A module providing fast iterator-building tools.

### Example

```python
import itertools
```

### Key Interview Point

Very popular interview topic.

---

## 57. Why use itertools?

### Answer

Benefits:

* Memory efficient
* Fast
* Cleaner code
* Lazy evaluation

---

## 58. What does itertools.count() do?

### Answer

Creates an infinite counter.

### Example

```python
from itertools import count

for num in count(1):
    print(num)
```

Output:

```text
1
2
3
...
```

---

## 59. What does itertools.cycle() do?

### Answer

Repeats items forever.

### Example

```python
from itertools import cycle

colors = cycle(
    ["Red", "Blue"]
)

print(next(colors))
```

---

## 60. What does itertools.repeat() do?

### Answer

Repeats the same value.

### Example

```python
from itertools import repeat

for item in repeat("Python", 3):
    print(item)
```

Output:

```text
Python
Python
Python
```

---

## 61. What is enumerate()?

### Answer

Adds indexes during iteration.

### Example

```python
names = ["A", "B", "C"]

for index, value in enumerate(names):
    print(index, value)
```

Output:

```text
0 A
1 B
2 C
```

---

## 62. Why use enumerate() instead of range(len())?

### Answer

Cleaner and more Pythonic.

### Bad

```python
for i in range(len(names)):
    print(i, names[i])
```

### Better

```python
for i, value in enumerate(names):
    print(i, value)
```

---

## 63. What is zip()?

### Answer

Combines multiple iterables.

### Example

```python
names = ["A", "B"]
ages = [20, 25]

for pair in zip(names, ages):
    print(pair)
```

Output:

```text
('A', 20)
('B', 25)
```

---

## 64. What happens if zip() receives unequal lengths?

### Answer

Stops at the shortest iterable.

### Example

```python
list(
    zip(
        [1,2,3],
        [10]
    )
)
```

Output:

```python
[(1, 10)]
```

---

## 65. What is map()?

### Answer

Applies a function to every item.

### Example

```python
nums = [1,2,3]

result = map(
    lambda x: x*2,
    nums
)
```

---

## 66. What does map() return?

### Answer

Returns a lazy iterator.

### Example

```python
result = map(
    str,
    [1,2,3]
)

print(type(result))
```

Output:

```text
<class 'map'>
```

---

## 67. What is filter()?

### Answer

Filters elements based on a condition.

### Example

```python
nums = [1,2,3,4]

evens = filter(
    lambda x: x % 2 == 0,
    nums
)
```

---

## 68. What does filter() return?

### Answer

Returns a lazy iterator.

### Example

```python
result = filter(
    lambda x: x > 0,
    data
)
```

---

## 69. What is the difference between map() and filter()?

### Answer

| map()                  | filter()              |
| ---------------------- | --------------------- |
| Transforms data        | Selects data          |
| Function returns value | Function returns bool |

---

## 70. What is a generator pipeline example?

### Answer

```python
nums = range(100)

evens = (
    n for n in nums
    if n % 2 == 0
)

squares = (
    n*n for n in evens
)
```

### Benefit

Processes data lazily.

---

## 71. What are async generators?

### Answer

Generators used with asynchronous programming.

### Example

```python
async def generator():

    yield 1
```

### Key Interview Point

Introduced in Python 3.6.

---

## 72. What is async for?

### Answer

Used to iterate over async generators.

### Example

```python
async for item in generator():
    print(item)
```

---

## 73. When should generators be preferred over lists?

### Answer

Use generators when:

* Data is huge
* Memory matters
* Streaming data
* Infinite sequences

### Example

```python
(x for x in range(100000000))
```

---

## 74. When should lists be preferred?

### Answer

Use lists when:

* Multiple passes required
* Random access needed
* Dataset is small

### Example

```python
[x*x for x in range(100)]
```

---

## 75. What are common real-world uses of generators?

### Answer

Applications:

* Log processing
* File streaming
* ETL pipelines
* API pagination
* Data science workflows
* Machine learning preprocessing

### Key Interview Point

Generators are widely used in production systems handling large datasets.

---

## 76. What is the Iterator Design Pattern?

### Answer

The Iterator Design Pattern provides a way to access elements of a collection sequentially without exposing its internal structure.

### Example

```python
class Numbers:

    def __iter__(self):
        return iter([1, 2, 3])
```

### Key Interview Point

Python's iterator protocol is based on this design pattern.

---

## 77. What is the Iterator Protocol?

### Answer

The Iterator Protocol requires:

```python
__iter__()
__next__()
```

### Example

```python
class MyIterator:

    def __iter__(self):
        return self

    def __next__(self):
        pass
```

---

## 78. Why is the Iterator Protocol important?

### Answer

It allows custom objects to work with:

* for loops
* list()
* tuple()
* set()
* comprehensions

### Example

```python
for item in custom_iterator:
    print(item)
```

---

## 79. What are Generator Best Practices?

### Answer

Best Practices:

* Use generators for large datasets
* Avoid unnecessary list conversions
* Keep generators focused
* Use generator expressions when possible

### Key Interview Point

Generators should be preferred for streaming data.

---

## 80. What are common mistakes with generators?

### Answer

Mistakes:

* Forgetting generators are exhausted
* Converting to list unnecessarily
* Using generators when random access is needed

### Example

```python
g = (x for x in range(3))

list(g)
list(g)
```

Second call returns:

```python
[]
```

---

## 81. Why are generators faster to start?

### Answer

They do not generate all values immediately.

### Example

```python
(x*x for x in range(1000000))
```

Creates instantly.

---

## 82. Why are generators memory efficient?

### Answer

Only one item exists in memory at a time.

### Example

```python
sum(
    x for x in range(1000000)
)
```

### Key Interview Point

Common memory optimization interview topic.

---

## 83. How can you compare memory usage of lists and generators?

### Example

```python
import sys

nums_list = [
    x for x in range(1000)
]

nums_gen = (
    x for x in range(1000)
)

print(sys.getsizeof(nums_list))
print(sys.getsizeof(nums_gen))
```

### Result

Generators use significantly less memory.

---

## 84. What is generator exhaustion?

### Answer

Once all values are consumed, the generator cannot be reused.

### Example

```python
g = (x for x in range(3))

for x in g:
    print(x)

for x in g:
    print(x)
```

Second loop produces no output.

---

## 85. How can a generator be recreated?

### Answer

Call the generator function again.

### Example

```python
def nums():
    yield 1

g1 = nums()
g2 = nums()
```

---

## 86. What is the performance benefit of lazy evaluation?

### Answer

Benefits:

* Lower memory consumption
* Faster startup
* Better scalability

### Example

```python
(x for x in huge_dataset)
```

---

## 87. What is a real-world generator use case in Machine Learning?

### Answer

Batch data loading.

### Example

```python
def data_loader():

    for batch in dataset:
        yield batch
```

### Key Interview Point

Widely used in TensorFlow and PyTorch.

---

## 88. What is a real-world generator use case in Data Engineering?

### Answer

Processing large files.

### Example

```python
def read_logs():

    with open("logs.txt") as file:

        for line in file:
            yield line
```

---

## 89. What is a real-world generator use case in APIs?

### Answer

Handling paginated responses.

### Example

```python
def fetch_pages():

    while has_next:
        yield page_data
```

---

## 90. Why are generators useful for streaming?

### Answer

Data can be processed continuously without storing everything.

### Example

```python
for packet in network_stream:
    process(packet)
```

---

## 91. What interview coding problem involves iterators?

### Answer

Create a custom iterator that returns numbers from 1 to N.

### Example

```python
class Counter:

    def __init__(self, n):
        self.n = n
        self.current = 1
```

---

## 92. What interview coding problem involves generators?

### Answer

Generate Fibonacci numbers using yield.

### Example

```python
def fibonacci():

    a, b = 0, 1

    while True:
        yield a

        a, b = b, a + b
```

---

## 93. How can generators be used for infinite sequences?

### Example

```python
def natural_numbers():

    n = 1

    while True:
        yield n
        n += 1
```

### Key Interview Point

Common interview example.

---

## 94. What happens if StopIteration is raised manually?

### Example

```python
def gen():

    yield 1

    raise StopIteration
```

### Result

Generator terminates.

### Key Interview Point

Modern Python prefers `return`.

---

## 95. What is the preferred way to terminate a generator?

### Answer

Use:

```python
return
```

instead of manually raising:

```python
StopIteration
```

---

## 96. What are common iterator interview traps?

### Answer

Common Traps:

* Iterator vs Iterable confusion
* Exhausted generators
* Misunderstanding lazy evaluation
* Assuming generators support indexing

---

## 97. Can generators be indexed?

### Answer

No.

### Example

```python
g = (
    x for x in range(5)
)

g[0]
```

Output:

```python
TypeError
```

---

## 98. What concepts are most important for Python interviews?

### Answer

Core Concepts:

* Iterable
* Iterator
* iter()
* next()
* StopIteration
* Generator
* yield
* Generator Expressions

---

## 99. What advanced concepts are frequently asked?

### Answer

Advanced Topics:

* send()
* throw()
* close()
* yield from
* itertools
* Async Generators
* Lazy Evaluation

### Key Interview Point

Frequently asked in senior Python interviews.

---

## 100. What Iterators & Generators knowledge is required for Python interviews?

### Answer

### Fundamentals

* Iterable
* Iterator
* iter()
* next()
* StopIteration

### Intermediate

* Generator Functions
* yield
* Generator Expressions
* enumerate()
* zip()
* map()
* filter()

### Advanced

* send()
* close()
* throw()
* yield from
* itertools
* Async Generators

### Production Concepts

* Streaming
* Data Pipelines
* Batch Processing
* Memory Optimization
* Lazy Evaluation

### Final Interview Tip

If you understand:

* Iterable vs Iterator
* iter()
* next()
* StopIteration
* yield
* Generator Expressions
* itertools
* send()
* yield from

you can confidently answer **95%+ of Python Iterators & Generators interview questions** asked in Software Engineering, Backend Development, Data Engineering, Machine Learning, and AI Engineering interviews.



