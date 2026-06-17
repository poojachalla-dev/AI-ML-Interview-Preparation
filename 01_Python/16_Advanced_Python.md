## 1. What is Advanced Python?

### Answer

Advanced Python refers to features beyond basic syntax and OOP that help build scalable, efficient, and maintainable applications.

### Topics Include

* Metaclasses
* Descriptors
* Decorators
* Context Managers
* Generators
* Coroutines
* Memory Management
* GIL
* Async Programming

---

## 2. What are Python Internals?

### Answer

Python Internals refer to how Python works behind the scenes.

### Examples

* Bytecode Execution
* Memory Management
* Garbage Collection
* Object Model
* GIL

---

## 3. What is Duck Typing?

### Answer

Duck Typing means object type is determined by behavior rather than inheritance.

### Example

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

---

## 4. Why is it called Duck Typing?

### Answer

Famous rule:

```text
If it walks like a duck
and quacks like a duck,
it is a duck.
```

---

## 5. What are Python Protocols?

### Answer

Protocols define expected behavior through special methods.

### Examples

```python
__iter__()
__len__()
__getitem__()
__enter__()
```

---

## 6. What are Magic Methods?

### Answer

Special methods surrounded by double underscores.

### Examples

```python
__init__()
__str__()
__repr__()
__len__()
```

---

## 7. What is **new**()?

### Answer

Creates an object before initialization.

### Example

```python
class Demo:

    def __new__(cls):
        print("Creating")
        return super().__new__(cls)
```

---

## 8. Difference between **new**() and **init**()?

### Answer

| **new**        | **init**           |
| -------------- | ------------------ |
| Creates object | Initializes object |
| Runs first     | Runs second        |
| Returns object | Returns None       |

---

## 9. What is Method Resolution Order (MRO)?

### Answer

MRO determines the order Python searches for methods in inheritance hierarchies.

### Example

```python
ClassA
ClassB
ClassC
```

---

## 10. How can MRO be viewed?

### Example

```python
print(Class.__mro__)
```

or

```python
print(Class.mro())
```

---

## 11. What algorithm does Python use for MRO?

### Answer

```text
C3 Linearization
```

---

## 12. What is Reflection in Python?

### Answer

Reflection allows inspection and modification of objects at runtime.

### Example

```python
getattr()
setattr()
hasattr()
```

---

## 13. What is Introspection?

### Answer

Examining object properties during runtime.

### Example

```python
dir(object)
```

---

## 14. What does dir() do?

### Example

```python
print(dir(str))
```

Returns available attributes and methods.

---

## 15. What is callable()?

### Answer

Checks whether an object can be called like a function.

### Example

```python
callable(print)
```

Output:

```python
True
```

---

## 16. What is isinstance()?

### Example

```python
isinstance(5, int)
```

Output:

```python
True
```

---

## 17. What is issubclass()?

### Example

```python
issubclass(bool, int)
```

Output:

```python
True
```

---

## 18. What is Dynamic Typing?

### Answer

Variable types are determined at runtime.

### Example

```python
x = 10

x = "Python"
```

---

## 19. What is Strong Typing?

### Answer

Python does not automatically convert unrelated types.

### Example

```python
"10" + 10
```

Produces:

```python
TypeError
```

---

## 20. What is Monkey Patching?

### Answer

Modifying classes or objects at runtime.

### Example

```python
class Demo:
    pass

Demo.say_hi = lambda self: print("Hi")
```

---

## 21. What is Dynamic Attribute Creation?

### Example

```python
class Person:
    pass

p = Person()

p.name = "John"
```

---

## 22. What is getattr()?

### Example

```python
name = getattr(
    obj,
    "name"
)
```

---

## 23. What is setattr()?

### Example

```python
setattr(
    obj,
    "age",
    25
)
```

---

## 24. What is hasattr()?

### Example

```python
hasattr(
    obj,
    "name"
)
```

---

## 25. What Advanced Python topics are commonly asked?

### Answer

Frequently Asked:

* Duck Typing
* MRO
* Reflection
* Introspection
* **new**()
* Magic Methods
* Dynamic Typing
* Monkey Patching

---

## 26. What is a Descriptor in Python?

### Answer

A Descriptor is an object that controls attribute access using special methods.

### Methods

```python id="adv26"
__get__()
__set__()
__delete__()
```

---

## 27. Why are Descriptors important?

### Answer

They provide the foundation for:

* Properties
* Methods
* Static Methods
* Class Methods
* ORM Frameworks

---

## 28. Example of a Descriptor.

### Example

```python id="adv28"
class Descriptor:

    def __get__(
        self,
        instance,
        owner
    ):
        return "Value"
```

---

## 29. What is **get**()?

### Answer

Executed when an attribute is accessed.

### Example

```python id="adv29"
obj.attribute
```

---

## 30. What is **set**()?

### Answer

Executed when an attribute is assigned.

### Example

```python id="adv30"
obj.attribute = 100
```

---

## 31. What is **delete**()?

### Answer

Executed when an attribute is deleted.

### Example

```python id="adv31"
del obj.attribute
```

---

## 32. What is the @property decorator?

### Answer

Allows methods to behave like attributes.

### Example

```python id="adv32"
class Person:

    @property
    def name(self):

        return "John"
```

---

## 33. Why use @property?

### Answer

Benefits:

* Encapsulation
* Validation
* Cleaner APIs

---

## 34. Example of property setter.

### Example

```python id="adv34"
class Person:

    def __init__(self):

        self._age = 0

    @property
    def age(self):

        return self._age

    @age.setter
    def age(
        self,
        value
    ):
        self._age = value
```

---

## 35. What is property deleter?

### Example

```python id="adv35"
@age.deleter
def age(self):

    del self._age
```

---

## 36. What is an Abstract Base Class (ABC)?

### Answer

A class that cannot be instantiated directly.

### Example

```python id="adv36"
from abc import ABC
```

---

## 37. Why use Abstract Base Classes?

### Answer

To enforce implementation requirements in subclasses.

---

## 38. What module provides ABC support?

### Example

```python id="adv38"
from abc import ABC
```

---

## 39. What is @abstractmethod?

### Example

```python id="adv39"
from abc import (
    ABC,
    abstractmethod
)

class Shape(ABC):

    @abstractmethod
    def area(self):
        pass
```

---

## 40. What happens if an abstract method is not implemented?

### Answer

Instantiation raises:

```python id="adv40"
TypeError
```

---

## 41. What is Operator Overloading?

### Answer

Giving custom behavior to operators.

### Example

```python id="adv41"
+
-
*
==
```

---

## 42. How is operator overloading implemented?

### Answer

Using magic methods.

### Example

```python id="adv42"
__add__()
__sub__()
__eq__()
```

---

## 43. Example of operator overloading.

### Example

```python id="adv43"
class Point:

    def __init__(
        self,
        x
    ):
        self.x = x

    def __add__(
        self,
        other
    ):
        return Point(
            self.x + other.x
        )
```

---

## 44. What is **str**()?

### Answer

Provides a human-readable string representation.

### Example

```python id="adv44"
def __str__(self):

    return "Object"
```

---

## 45. What is **repr**()?

### Answer

Provides an unambiguous object representation.

### Example

```python id="adv45"
def __repr__(self):

    return "Demo()"
```

---

## 46. Difference between **str**() and **repr**()?

### Answer

| **str**       | **repr**           |
| ------------- | ------------------ |
| User-friendly | Developer-friendly |
| Readable      | Precise            |
| print()       | Debugging          |

---

## 47. What is a Custom Container?

### Answer

A class that behaves like a built-in collection.

### Example

```python id="adv47"
class MyList:
    pass
```

---

## 48. How can a custom container support len()?

### Example

```python id="adv48"
class MyList:

    def __len__(self):

        return 5
```

---

## 49. How can a custom container support indexing?

### Example

```python id="adv49"
class MyList:

    def __getitem__(
        self,
        index
    ):
        return index
```

---

## 50. What Advanced Python concepts are commonly asked in interviews?

### Answer

Frequently Asked:

* Descriptors
* Properties
* Abstract Classes
* ABC Module
* Operator Overloading
* Custom Containers
* **str**()
* **repr**()
* Data Model

---

## 51. What is a Metaclass?

### Answer

A Metaclass is a class whose instances are classes.

### Key Interview Point

```text id="adv51"
Class creates Objects

Metaclass creates Classes
```

---

## 52. Why are Metaclasses used?

### Answer

Metaclasses allow customization of class creation.

### Common Uses

* Frameworks
* ORMs
* Validation Systems
* API Libraries

---

## 53. What is the default Metaclass in Python?

### Answer

```python id="adv53"
type
```

---

## 54. How can you verify a class is created by type?

### Example

```python id="adv54"
class Demo:
    pass

print(type(Demo))
```

Output:

```python id="adv54a"
<class 'type'>
```

---

## 55. Can classes be created dynamically?

### Answer

Yes.

Using:

```python id="adv55"
type()
```

---

## 56. Example of dynamic class creation.

### Example

```python id="adv56"
Person = type(
    "Person",
    (),
    {"name": "John"}
)

p = Person()

print(p.name)
```

---

## 57. What is the syntax of type() for class creation?

### Example

```python id="adv57"
type(
    class_name,
    bases,
    attributes
)
```

---

## 58. Example of a custom Metaclass.

### Example

```python id="adv58"
class Meta(type):

    def __new__(
        cls,
        name,
        bases,
        attrs
    ):
        return super().__new__(
            cls,
            name,
            bases,
            attrs
        )
```

---

## 59. How is a Metaclass assigned?

### Example

```python id="adv59"
class Demo(
    metaclass=Meta
):
    pass
```

---

## 60. What is a Class Decorator?

### Answer

A decorator that modifies a class.

### Example

```python id="adv60"
def decorate(cls):

    cls.version = "1.0"

    return cls
```

---

## 61. Applying a Class Decorator.

### Example

```python id="adv61"
@decorate
class App:
    pass
```

---

## 62. What is a Closure?

### Answer

A function that remembers variables from its enclosing scope.

### Example

```python id="adv62"
def outer(x):

    def inner():

        return x

    return inner
```

---

## 63. Why are Closures useful?

### Answer

Uses:

* Data hiding
* Function factories
* Decorators
* State management

---

## 64. What is the LEGB Rule?

### Answer

Python variable lookup order.

### Flow

```text id="adv64"
Local
Enclosing
Global
Built-in
```

---

## 65. Example of LEGB lookup.

### Example

```python id="adv65"
x = "global"

def outer():

    x = "enclosing"

    def inner():

        print(x)

    inner()
```

Output:

```python id="adv65a"
enclosing
```

---

## 66. What is a Namespace?

### Answer

A mapping between names and objects.

### Examples

```python id="adv66"
Global Namespace
Local Namespace
Built-in Namespace
```

---

## 67. What is globals()?

### Example

```python id="adv67"
print(globals())
```

Returns global namespace.

---

## 68. What is locals()?

### Example

```python id="adv68"
print(locals())
```

Returns local namespace.

---

## 69. What is nonlocal?

### Answer

Allows modification of enclosing scope variables.

### Example

```python id="adv69"
def outer():

    count = 0

    def inner():

        nonlocal count

        count += 1
```

---

## 70. What is global?

### Answer

Allows modification of global variables.

### Example

```python id="adv70"
counter = 0

def update():

    global counter

    counter += 1
```

---

## 71. What is **dict**?

### Answer

Stores an object's writable attributes.

### Example

```python id="adv71"
class Demo:

    def __init__(self):

        self.name = "Python"

d = Demo()

print(d.__dict__)
```

---

## 72. What is **class**?

### Answer

Returns the class of an object.

### Example

```python id="adv72"
x = []

print(x.__class__)
```

---

## 73. What is **bases**?

### Answer

Returns base classes.

### Example

```python id="adv73"
print(
    MyClass.__bases__
)
```

---

## 74. What is **mro**?

### Answer

Returns Method Resolution Order.

### Example

```python id="adv74"
print(
    MyClass.__mro__
)
```

---

## 75. What Advanced Python concepts are commonly asked in senior interviews?

### Answer

Frequently Asked:

* Metaclasses
* type()
* Closures
* LEGB Rule
* Namespaces
* **dict**
* Dynamic Class Creation
* Class Decorators
* MRO Internals

---

## 76. What is a Coroutine?

### Answer

A Coroutine is a special function that can pause and resume execution.

### Example

```python id="adv76"
async def fetch():

    return "Data"
```

### Key Interview Point

Coroutines are the foundation of Asyncio.

---

## 77. Difference between Generator and Coroutine?

### Answer

| Generator       | Coroutine           |
| --------------- | ------------------- |
| Uses yield      | Uses async/await    |
| Produces values | Manages async tasks |
| Iteration       | Concurrency         |

---

## 78. What is a Context Variable?

### Answer

A Context Variable stores task-local data in asynchronous programs.

### Example

```python id="adv78"
from contextvars import ContextVar

user_id = ContextVar("user_id")
```

---

## 79. Why are Context Variables useful?

### Answer

They prevent data leakage between async tasks.

### Common Uses

* Request IDs
* User Sessions
* Logging Context
* Tracing

---

## 80. What are Function Annotations?

### Answer

Function annotations allow metadata to be attached to parameters and return values.

### Example

```python id="adv80"
def add(
    a: int,
    b: int
) -> int:

    return a + b
```

---

## 81. Do Type Hints enforce types?

### Answer

No.

Python ignores type hints at runtime.

### Example

```python id="adv81"
def add(
    a: int,
    b: int
):
    return a + b
```

Still accepts:

```python id="adv81a"
add("A", "B")
```

---

## 82. Why use Type Hints?

### Answer

Benefits:

* Better readability
* IDE support
* Static analysis
* Easier maintenance

---

## 83. What is **annotations**?

### Answer

Stores function annotations.

### Example

```python id="adv83"
def add(
    a: int,
    b: int
) -> int:

    return a + b

print(add.__annotations__)
```

---

## 84. What is a Dataclass?

### Answer

A Dataclass automatically generates boilerplate methods.

### Example

```python id="adv84"
from dataclasses import dataclass

@dataclass
class Employee:

    name: str
    salary: int
```

---

## 85. What methods does Dataclass generate?

### Answer

Common methods:

```python id="adv85"
__init__()
__repr__()
__eq__()
```

---

## 86. Why use Dataclasses?

### Answer

Benefits:

* Less code
* Better readability
* Easier maintenance

---

## 87. What is a Frozen Dataclass?

### Example

```python id="adv87"
@dataclass(
    frozen=True
)
class User:

    name: str
```

Objects become immutable.

---

## 88. Can Dataclasses be used with **slots**?

### Answer

Yes.

### Example

```python id="adv88"
@dataclass(
    slots=True
)
class User:

    name: str
```

---

## 89. Benefits of slots=True in Dataclasses?

### Answer

Benefits:

* Reduced memory usage
* Faster attribute access
* Better scalability

---

## 90. What is Multiple Inheritance?

### Answer

A class inheriting from multiple parent classes.

### Example

```python id="adv90"
class A:
    pass

class B:
    pass

class C(A, B):
    pass
```

---

## 91. What is the Diamond Problem?

### Answer

Occurs when multiple inheritance introduces ambiguous method resolution.

### Example

```text id="adv91"
     A
    / \
   B   C
    \ /
     D
```

---

## 92. How does Python solve the Diamond Problem?

### Answer

Using:

```text id="adv92"
C3 Linearization
```

through MRO.

---

## 93. What is Cooperative Inheritance?

### Answer

Classes cooperate using:

```python id="adv93"
super()
```

to ensure proper method execution.

---

## 94. Why is super() important?

### Answer

It avoids duplicate method calls in complex inheritance hierarchies.

---

## 95. What is the Python Data Model?

### Answer

The set of protocols that define object behavior.

### Examples

```python id="adv95"
__len__()
__iter__()
__getitem__()
__call__()
```

---

## 96. What makes an object callable?

### Answer

Implementing:

```python id="adv96"
__call__()
```

### Example

```python id="adv96a"
class Adder:

    def __call__(
        self,
        x,
        y
    ):
        return x + y
```

---

## 97. What makes an object iterable?

### Answer

Implementing:

```python id="adv97"
__iter__()
```

or

```python id="adv97a"
__getitem__()
```

---

## 98. What Advanced Python topics are most important for senior interviews?

### Answer

Core Topics:

* Descriptors
* Metaclasses
* Closures
* LEGB Rule
* Dataclasses
* Type Hints
* MRO

---

## 99. What Advanced Python topics are frequently asked in FAANG-level interviews?

### Answer

Advanced Topics:

* Metaclasses
* Data Model
* Descriptors
* Context Variables
* Cooperative Inheritance
* Dynamic Class Creation
* Python Internals

---

## 100. What Advanced Python knowledge is required for Python interviews?

### Answer

### Fundamentals

* Duck Typing
* Magic Methods
* Reflection
* Introspection

### Intermediate

* Properties
* Descriptors
* Closures
* MRO
* Dataclasses

### Advanced

* Metaclasses
* Context Variables
* Data Model
* Multiple Inheritance
* Dynamic Class Creation

### Production Concepts

* Type Hints
* Dataclasses
* Memory Optimization
* Framework Internals
* API Design

### Final Interview Tip

If you understand:

* MRO
* Descriptors
* Metaclasses
* Closures
* Dataclasses
* Type Hints
* Python Data Model

you can confidently answer **95%+ of Advanced Python interview questions** asked in Senior Python, Backend, Data Engineering, Machine Learning, MLOps, and AI Engineering interviews.


