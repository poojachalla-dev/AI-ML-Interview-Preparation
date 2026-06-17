## 1. What is a list in Python?

### Answer

A list is an ordered, mutable sequence that can hold elements of any data type.

Example:

```python
fruits = ["apple", "banana", "cherry"]
print(fruits)
```

Output:

```
['apple', 'banana', 'cherry']
```

### Key Interview Points

* Lists are ordered — elements maintain insertion order.
* Lists are mutable — elements can be added, removed, or changed.
* Lists allow duplicate values.

---

## 2. What is a tuple in Python?

### Answer

A tuple is an ordered, immutable sequence.

Example:

```python
point = (10, 20)
print(point)
```

Output:

```
(10, 20)
```

### Key Interview Points

* Tuples are immutable — cannot be changed after creation.
* Tuples are faster than lists for iteration.
* Tuples can be used as dictionary keys if they contain only hashable elements.

---

## 3. What is a set in Python?

### Answer

A set is an unordered collection of unique elements.

Example:

```python
s = {1, 2, 3, 2, 1}
print(s)
```

Output:

```
{1, 2, 3}
```

### Key Interview Points

* Sets do not allow duplicates.
* Sets are unordered — no indexing.
* Sets support mathematical operations like union, intersection, difference.

---

## 4. What is a dictionary in Python?

### Answer

A dictionary is an ordered collection of key-value pairs.

Example:

```python
student = {"name": "Alice", "age": 22}
print(student["name"])
```

Output:

```
Alice
```

### Key Interview Points

* Keys must be unique and hashable.
* Values can be of any type.
* Ordered since Python 3.7.

---

## 5. What is the difference between a list and a tuple?

### Answer

| Feature | List | Tuple |
|---|---|---|
| Mutability | Mutable | Immutable |
| Syntax | `[1, 2, 3]` | `(1, 2, 3)` |
| Performance | Slower | Faster |
| Use case | Dynamic data | Fixed data |
| Hashable | No | Yes (if elements are hashable) |

Example:

```python
lst = [1, 2, 3]
lst[0] = 99       # OK

tup = (1, 2, 3)
tup[0] = 99       # TypeError
```

---

## 6. What is the difference between a list and a set?

### Answer

| Feature | List | Set |
|---|---|---|
| Order | Ordered | Unordered |
| Duplicates | Allowed | Not allowed |
| Indexing | Supported | Not supported |
| Lookup | O(n) | O(1) average |

Example:

```python
lst = [1, 2, 2, 3]
s   = {1, 2, 2, 3}

print(lst)
print(s)
```

Output:

```
[1, 2, 2, 3]
{1, 2, 3}
```

---

## 7. What is the difference between a list and a dictionary?

### Answer

| Feature | List | Dictionary |
|---|---|---|
| Access | By index | By key |
| Order | Ordered | Ordered (3.7+) |
| Duplicates | Allowed | Keys must be unique |
| Use case | Sequences | Key-value mappings |

Example:

```python
lst  = ["Alice", 22]
dct  = {"name": "Alice", "age": 22}

print(lst[0])
print(dct["name"])
```

Output:

```
Alice
Alice
```

---

## 8. How do you create an empty list, tuple, set, and dictionary?

### Answer

```python
lst  = []
tup  = ()
s    = set()     # NOT {} — that creates a dict
dct  = {}
```

### Key Interview Points

* `{}` creates a dict, not a set.
* Use `set()` for an empty set.

---

## 9. How do you access elements in a list?

### Answer

Using index (zero-based).

Example:

```python
fruits = ["apple", "banana", "cherry"]

print(fruits[0])
print(fruits[-1])
```

Output:

```
apple
cherry
```

---

## 10. What is list slicing?

### Answer

Slicing extracts a portion of a list.

Syntax:

```python
list[start:stop:step]
```

Example:

```python
nums = [0, 1, 2, 3, 4, 5]

print(nums[1:4])
print(nums[::2])
print(nums[::-1])
```

Output:

```
[1, 2, 3]
[0, 2, 4]
[5, 4, 3, 2, 1, 0]
```

---

## 11. What are common list methods?

### Answer

```python
append()    # add single element at end
extend()    # add multiple elements
insert()    # insert at index
remove()    # remove first occurrence
pop()       # remove and return by index
sort()      # sort in place
reverse()   # reverse in place
index()     # find index of element
count()     # count occurrences
clear()     # remove all elements
copy()      # shallow copy
```

Example:

```python
lst = [3, 1, 4, 1, 5]
lst.append(9)
lst.sort()
print(lst)
```

Output:

```
[1, 1, 3, 4, 5, 9]
```

---

## 12. What is the difference between `append()` and `extend()`?

### Answer

`append()` adds a single element.

```python
lst = [1, 2, 3]
lst.append([4, 5])
print(lst)
```

Output:

```
[1, 2, 3, [4, 5]]
```

`extend()` adds each element of an iterable.

```python
lst = [1, 2, 3]
lst.extend([4, 5])
print(lst)
```

Output:

```
[1, 2, 3, 4, 5]
```

### Key Interview Points

* `append()` — one item added, length increases by 1.
* `extend()` — multiple items added, length increases by n.

---

## 13. What is the difference between `remove()` and `pop()`?

### Answer

`remove()` deletes the first occurrence of a value.

```python
lst = [1, 2, 3, 2]
lst.remove(2)
print(lst)
```

Output:

```
[1, 3, 2]
```

`pop()` removes and returns the element at an index (default: last).

```python
lst = [1, 2, 3]
val = lst.pop()
print(val, lst)
```

Output:

```
3 [1, 2]
```

### Key Interview Points

* `remove()` raises `ValueError` if element not found.
* `pop()` raises `IndexError` if index is out of range.

---

## 14. What is the difference between `sort()` and `sorted()`?

### Answer

`sort()` sorts in place and returns `None`.

```python
lst = [3, 1, 2]
lst.sort()
print(lst)
```

Output:

```
[1, 2, 3]
```

`sorted()` returns a new sorted list and works on any iterable.

```python
lst = [3, 1, 2]
new = sorted(lst)
print(lst)
print(new)
```

Output:

```
[3, 1, 2]
[1, 2, 3]
```

---

## 15. How do you copy a list?

### Answer

Shallow copy:

```python
lst  = [1, 2, 3]
copy = lst[:]          # or lst.copy() or list(lst)
```

Deep copy:

```python
import copy
lst  = [[1, 2], [3, 4]]
deep = copy.deepcopy(lst)
```

### Key Interview Points

* Shallow copy copies only the top-level list — nested lists are still shared.
* Deep copy copies everything recursively.

---

## 16. What is the difference between shallow copy and deep copy?

### Answer

Shallow copy:

```python
import copy

original = [[1, 2], [3, 4]]
shallow  = copy.copy(original)

shallow[0].append(99)
print(original)
```

Output:

```
[[1, 2, 99], [3, 4]]
```

Deep copy:

```python
deep = copy.deepcopy(original)
deep[0].append(99)
print(original)
```

Output:

```
[[1, 2], [3, 4]]
```

### Key Interview Points

* Shallow copy — inner objects are shared.
* Deep copy — inner objects are fully independent.

---

## 17. What is a list comprehension?

### Answer

A concise way to create lists using a single expression.

Syntax:

```python
[expression for item in iterable if condition]
```

Example:

```python
squares = [x**2 for x in range(1, 6)]
print(squares)
```

Output:

```
[1, 4, 9, 16, 25]
```

### Key Interview Points

* Faster and more readable than equivalent for loops.
* Can include an optional `if` filter condition.

---

## 18. What is a nested list comprehension?

### Answer

A list comprehension inside another list comprehension.

Example — flatten a 2D matrix:

```python
matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]
flat   = [num for row in matrix for num in row]
print(flat)
```

Output:

```
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

---

## 19. How do you create a tuple with one element?

### Answer

A trailing comma is required.

```python
single = (42,)
print(type(single))

not_tuple = (42)
print(type(not_tuple))
```

Output:

```
<class 'tuple'>
<class 'int'>
```

### Key Interview Points

* Without the trailing comma, Python treats it as a parenthesized expression.
* Very common interview question.

---

## 20. Why are tuples faster than lists?

### Answer

* Tuples are immutable — Python can optimize their storage.
* Tuples have a smaller memory footprint.
* Tuple creation is faster than list creation.

Example:

```python
import timeit

print(timeit.timeit("(1,2,3,4,5)", number=10_000_000))
print(timeit.timeit("[1,2,3,4,5]", number=10_000_000))
```

### Key Interview Points

* Use tuples for fixed data that does not change.
* Python caches small tuples internally.

---

## 21. Can a tuple be used as a dictionary key?

### Answer

Yes, if all its elements are hashable.

Example:

```python
location = {(10.5, 20.3): "Park", (11.0, 21.0): "School"}
print(location[(10.5, 20.3)])
```

Output:

```
Park
```

### Key Interview Points

* Lists cannot be dictionary keys because they are mutable (and therefore unhashable).
* Tuples containing mutable elements (like lists) also cannot be keys.

---

## 22. What is tuple packing and unpacking?

### Answer

Packing — combining values into a tuple.

```python
point = 10, 20, 30
print(point)
```

Output:

```
(10, 20, 30)
```

Unpacking — extracting tuple values into variables.

```python
x, y, z = point
print(x, y, z)
```

Output:

```
10 20 30
```

---

## 23. What is extended unpacking?

### Answer

Using `*` to capture multiple values during unpacking.

Example:

```python
first, *middle, last = [1, 2, 3, 4, 5]

print(first)
print(middle)
print(last)
```

Output:

```
1
[2, 3, 4]
5
```

---

## 24. What are common set operations?

### Answer

```python
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

print(a | b)   # union
print(a & b)   # intersection
print(a - b)   # difference
print(a ^ b)   # symmetric difference
```

Output:

```
{1, 2, 3, 4, 5, 6}
{3, 4}
{1, 2}
{1, 2, 5, 6}
```

---

## 25. What is the difference between `discard()` and `remove()` in sets?

### Answer

`remove()` raises `KeyError` if element not found.

```python
s = {1, 2, 3}
s.remove(5)    # KeyError
```

`discard()` does nothing if element not found.

```python
s = {1, 2, 3}
s.discard(5)   # no error
print(s)
```

Output:

```
{1, 2, 3}
```

---

## 26. What is a frozenset?

### Answer

A frozenset is an immutable version of a set.

Example:

```python
fs = frozenset([1, 2, 3, 2, 1])
print(fs)
```

Output:

```
frozenset({1, 2, 3})
```

### Key Interview Points

* Frozensets are hashable and can be used as dictionary keys.
* Frozensets do not support `add()` or `remove()`.

---

## 27. How do you access values in a dictionary?

### Answer

Using key access or `.get()`.

```python
d = {"name": "Alice", "age": 22}

print(d["name"])
print(d.get("city", "Unknown"))
```

Output:

```
Alice
Unknown
```

### Key Interview Points

* `d[key]` raises `KeyError` if key is missing.
* `d.get(key, default)` returns the default instead.

---

## 28. What are common dictionary methods?

### Answer

```python
keys()       # all keys
values()     # all values
items()      # all key-value pairs
get()        # safe access
update()     # merge another dict
pop()        # remove and return by key
setdefault() # get or set default
clear()      # remove all items
copy()       # shallow copy
```

Example:

```python
d = {"a": 1, "b": 2}

for key, val in d.items():
    print(key, val)
```

Output:

```
a 1
b 2
```

---

## 29. What is a dictionary comprehension?

### Answer

A concise way to create dictionaries.

Syntax:

```python
{key_expr: val_expr for item in iterable}
```

Example:

```python
squares = {x: x**2 for x in range(1, 6)}
print(squares)
```

Output:

```
{1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
```

---

## 30. How do you merge two dictionaries?

### Answer

Python 3.9+ — using `|` operator:

```python
a = {"x": 1}
b = {"y": 2}

merged = a | b
print(merged)
```

Output:

```
{'x': 1, 'y': 2}
```

Python 3.5+ — using `**` unpacking:

```python
merged = {**a, **b}
```

Using `update()`:

```python
a.update(b)
```

### Key Interview Points

* `|` operator is the most modern and readable approach.
* `update()` modifies in place.

---

## 31. What is `defaultdict`?

### Answer

`defaultdict` automatically creates a default value for missing keys.

Example:

```python
from collections import defaultdict

d = defaultdict(list)

d["fruits"].append("apple")
d["fruits"].append("banana")

print(d)
```

Output:

```
defaultdict(<class 'list'>, {'fruits': ['apple', 'banana']})
```

### Key Interview Points

* Avoids `KeyError` for missing keys.
* Common default factories: `list`, `int`, `set`.

---

## 32. What is `OrderedDict`?

### Answer

`OrderedDict` remembers the insertion order of keys.

Example:

```python
from collections import OrderedDict

od = OrderedDict()
od["a"] = 1
od["b"] = 2
od["c"] = 3

print(od)
```

Output:

```
OrderedDict([('a', 1), ('b', 2), ('c', 3)])
```

### Key Interview Points

* Since Python 3.7, regular `dict` also maintains insertion order.
* `OrderedDict` still has extra methods like `move_to_end()`.

---

## 33. What is `Counter`?

### Answer

`Counter` counts the frequency of elements in an iterable.

Example:

```python
from collections import Counter

c = Counter("banana")
print(c)
print(c.most_common(2))
```

Output:

```
Counter({'a': 3, 'n': 2, 'b': 1})
[('a', 3), ('n', 2)]
```

---

## 34. What is `namedtuple`?

### Answer

`namedtuple` creates a tuple subclass with named fields.

Example:

```python
from collections import namedtuple

Point = namedtuple("Point", ["x", "y"])
p = Point(10, 20)

print(p.x, p.y)
print(p[0], p[1])
```

Output:

```
10 20
10 20
```

### Key Interview Points

* Immutable like a regular tuple.
* Fields accessible by name AND index.
* Useful for structured data without a full class.

---

## 35. How do sets handle duplicates?

### Answer

Sets automatically remove duplicates.

Example:

```python
data = [1, 2, 2, 3, 3, 3, 4]
unique = set(data)
print(unique)
```

Output:

```
{1, 2, 3, 4}
```

### Key Interview Points

* Internally uses hash table — O(1) average lookup.
* Order is not preserved.

---

## 36. What is the time complexity of list operations?

### Answer

| Operation | Complexity |
|---|---|
| `append()` | O(1) amortized |
| `pop()` last | O(1) |
| `pop(i)` middle | O(n) |
| `insert(i, x)` | O(n) |
| `in` (membership) | O(n) |
| `sort()` | O(n log n) |
| Index access | O(1) |

---

## 37. What is the time complexity of dictionary operations?

### Answer

| Operation | Average | Worst |
|---|---|---|
| Get / Set / Delete | O(1) | O(n) |
| `in` (key check) | O(1) | O(n) |
| Iteration | O(n) | O(n) |

### Key Interview Points

* Average O(1) due to hashing.
* Worst case O(n) in case of hash collisions (rare).

---

## 38. What is the time complexity of set operations?

### Answer

| Operation | Average |
|---|---|
| `add()` | O(1) |
| `remove()` | O(1) |
| `in` (membership) | O(1) |
| Union `\|` | O(len(s) + len(t)) |
| Intersection `&` | O(min(len(s), len(t))) |

---

## 39. What is the time complexity of tuple operations?

### Answer

| Operation | Complexity |
|---|---|
| Index access | O(1) |
| Slicing | O(k) |
| `in` (membership) | O(n) |
| Iteration | O(n) |

---

## 40. Why is membership testing faster in sets than lists?

### Answer

Sets use a hash table internally.

List:

```python
5 in [1, 2, 3, 4, 5]   # O(n) — scans each element
```

Set:

```python
5 in {1, 2, 3, 4, 5}   # O(1) — hash lookup
```

### Key Interview Points

* For large collections with frequent membership testing, always prefer sets over lists.

---

## 41. How does a dictionary handle key collisions?

### Answer

Python dictionaries use open addressing with probing to resolve collisions.

When two keys produce the same hash:

* Python computes a new probe position.
* It continues probing until an empty slot is found.

### Key Interview Points

* Python 3.6+ uses a compact dict implementation.
* Good hash functions minimize collisions.
* Worst-case lookup degrades to O(n) with many collisions.

---

## 42. What makes an object hashable?

### Answer

An object is hashable if:

* It has a `__hash__()` method.
* It has an `__eq__()` method.
* Its hash value never changes during its lifetime.

Examples:

```python
hash(42)          # int — hashable
hash("hello")     # str — hashable
hash((1, 2))      # tuple of ints — hashable
hash([1, 2])      # list — TypeError: unhashable
```

---

## 43. Why can't lists be used as dictionary keys?

### Answer

Lists are mutable — their content can change after creation, which would change their hash value.

Dictionaries rely on the hash being stable.

Example:

```python
d = {}
key = [1, 2]
d[key] = "value"   # TypeError: unhashable type: 'list'
```

### Key Interview Points

* Only immutable, hashable types can be dictionary keys.
* Use tuples instead of lists as keys.

---

## 44. How do you iterate over a dictionary?

### Answer

Over keys:

```python
d = {"a": 1, "b": 2}
for key in d:
    print(key)
```

Over values:

```python
for val in d.values():
    print(val)
```

Over key-value pairs:

```python
for key, val in d.items():
    print(key, val)
```

Output:

```
a
b
1
2
a 1
b 2
```

---

## 45. How do you remove a key from a dictionary?

### Answer

Using `del`:

```python
d = {"a": 1, "b": 2}
del d["a"]
print(d)
```

Using `pop()`:

```python
val = d.pop("b")
print(val, d)
```

Output:

```
{'b': 2}
2 {}
```

### Key Interview Points

* `del` raises `KeyError` if key is missing.
* `pop(key, default)` returns a default instead of raising an error.

---

## 46. What is `setdefault()` in dictionaries?

### Answer

`setdefault()` returns the value for a key. If the key is missing, it inserts it with a default value.

Example:

```python
d = {"a": 1}

print(d.setdefault("a", 99))
print(d.setdefault("b", 99))
print(d)
```

Output:

```
1
99
{'a': 1, 'b': 99}
```

---

## 47. How do you sort a list of dictionaries by a key?

### Answer

```python
students = [
    {"name": "Charlie", "age": 20},
    {"name": "Alice",   "age": 22},
    {"name": "Bob",     "age": 19},
]

sorted_students = sorted(students, key=lambda x: x["age"])
print(sorted_students)
```

Output:

```
[{'name': 'Bob', 'age': 19}, {'name': 'Charlie', 'age': 20}, {'name': 'Alice', 'age': 22}]
```

---

## 48. How do you find the most common element in a list?

### Answer

```python
from collections import Counter

lst = [1, 2, 2, 3, 3, 3, 4]
most_common = Counter(lst).most_common(1)[0][0]
print(most_common)
```

Output:

```
3
```

---

## 49. How do you flatten a nested list?

### Answer

```python
nested = [[1, 2], [3, 4], [5, 6]]
flat   = [item for sublist in nested for item in sublist]
print(flat)
```

Output:

```
[1, 2, 3, 4, 5, 6]
```

---

## 50. How do you remove duplicates from a list while preserving order?

### Answer

```python
def remove_duplicates(lst):
    seen   = set()
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

## 51. How do you find common elements between two lists?

### Answer

```python
a = [1, 2, 3, 4, 5]
b = [3, 4, 5, 6, 7]

common = list(set(a) & set(b))
print(common)
```

Output:

```
[3, 4, 5]
```

---

## 52. How do you find the difference between two lists?

### Answer

```python
a = [1, 2, 3, 4, 5]
b = [3, 4, 5, 6, 7]

only_in_a = list(set(a) - set(b))
print(only_in_a)
```

Output:

```
[1, 2]
```

---

## 53. How do you count the frequency of elements in a list?

### Answer

```python
from collections import Counter

lst  = ["apple", "banana", "apple", "cherry", "banana", "apple"]
freq = Counter(lst)
print(freq)
```

Output:

```
Counter({'apple': 3, 'banana': 2, 'cherry': 1})
```

---

## 54. How do you rotate a list?

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

## 55. How do you find the second largest element in a list?

### Answer

```python
def second_largest(lst):
    unique = sorted(set(lst), reverse=True)
    return unique[1]

print(second_largest([10, 20, 4, 45, 99, 99]))
```

Output:

```
45
```

---

## 56. How do you merge two sorted lists?

### Answer

```python
def merge_sorted(a, b):
    result = []
    i = j  = 0
    while i < len(a) and j < len(b):
        if a[i] <= b[j]:
            result.append(a[i]); i += 1
        else:
            result.append(b[j]); j += 1
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

## 57. How do you find all pairs in a list that sum to a target?

### Answer

```python
def find_pairs(lst, target):
    seen  = set()
    pairs = []
    for num in lst:
        complement = target - num
        if complement in seen:
            pairs.append((complement, num))
        seen.add(num)
    return pairs

print(find_pairs([1, 2, 3, 4, 5, 6], 7))
```

Output:

```
[(3, 4), (2, 5), (1, 6)]
```

### Complexity

```
Time:  O(n)
Space: O(n)
```

---

## 58. How do you group elements of a list by a condition?

### Answer

```python
nums  = [1, 2, 3, 4, 5, 6, 7, 8]
evens = [x for x in nums if x % 2 == 0]
odds  = [x for x in nums if x % 2 != 0]

print(evens)
print(odds)
```

Output:

```
[2, 4, 6, 8]
[1, 3, 5, 7]
```

---

## 59. How do you transpose a matrix using lists?

### Answer

```python
matrix = [[1, 2, 3],
          [4, 5, 6],
          [7, 8, 9]]

transposed = list(zip(*matrix))
print(transposed)
```

Output:

```
[(1, 4, 7), (2, 5, 8), (3, 6, 9)]
```

---

## 60. How do you check if a list is sorted?

### Answer

```python
def is_sorted(lst):
    return lst == sorted(lst)

print(is_sorted([1, 2, 3, 4]))
print(is_sorted([1, 3, 2, 4]))
```

Output:

```
True
False
```

---

## 61. How do you invert a dictionary?

### Answer

```python
d       = {"a": 1, "b": 2, "c": 3}
inverted = {v: k for k, v in d.items()}
print(inverted)
```

Output:

```
{1: 'a', 2: 'b', 3: 'c'}
```

### Key Interview Points

* Only works cleanly if values are unique and hashable.

---

## 62. How do you group words by their first letter using a dictionary?

### Answer

```python
from collections import defaultdict

words   = ["apple", "banana", "avocado", "blueberry", "cherry"]
grouped = defaultdict(list)

for word in words:
    grouped[word[0]].append(word)

print(dict(grouped))
```

Output:

```
{'a': ['apple', 'avocado'], 'b': ['banana', 'blueberry'], 'c': ['cherry']}
```

---

## 63. How do you find keys with the maximum value in a dictionary?

### Answer

```python
d = {"alice": 90, "bob": 85, "charlie": 90}

max_val = max(d.values())
top     = [k for k, v in d.items() if v == max_val]
print(top)
```

Output:

```
['alice', 'charlie']
```

---

## 64. How do you check if two dictionaries are equal?

### Answer

```python
a = {"x": 1, "y": 2}
b = {"y": 2, "x": 1}

print(a == b)
```

Output:

```
True
```

### Key Interview Points

* Dictionary equality checks both keys and values, regardless of insertion order.

---

## 65. How do you filter a dictionary by value?

### Answer

```python
scores  = {"alice": 90, "bob": 55, "charlie": 72, "dave": 88}
passing = {k: v for k, v in scores.items() if v >= 70}
print(passing)
```

Output:

```
{'alice': 90, 'charlie': 72, 'dave': 88}
```

---

## 66. How do you find the union of two sets?

### Answer

```python
a = {1, 2, 3}
b = {3, 4, 5}

print(a | b)
print(a.union(b))
```

Output:

```
{1, 2, 3, 4, 5}
{1, 2, 3, 4, 5}
```

---

## 67. How do you find the intersection of two sets?

### Answer

```python
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

print(a & b)
print(a.intersection(b))
```

Output:

```
{3, 4}
{3, 4}
```

---

## 68. What is a set comprehension?

### Answer

```python
squares = {x**2 for x in range(1, 6)}
print(squares)
```

Output:

```
{1, 4, 9, 16, 25}
```

### Key Interview Points

* Returns a set, so duplicates are automatically removed.
* Unordered — output order may vary.

---

## 69. How do you check subset and superset relationships?

### Answer

```python
a = {1, 2, 3}
b = {1, 2, 3, 4, 5}

print(a.issubset(b))
print(b.issuperset(a))
print(a <= b)
print(b >= a)
```

Output:

```
True
True
True
True
```

---

## 70. What is the symmetric difference of two sets?

### Answer

Elements present in either set but not in both.

```python
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

print(a ^ b)
print(a.symmetric_difference(b))
```

Output:

```
{1, 2, 5, 6}
{1, 2, 5, 6}
```

---

## 71. How does Python's list handle dynamic resizing?

### Answer

Python lists are implemented as dynamic arrays.

When the internal array is full:

* Python allocates a larger array (roughly 1.125x growth factor).
* Copies all elements to the new array.
* Discards the old array.

### Key Interview Points

* `append()` is O(1) amortized — most appends are O(1), occasional resizing is O(n).
* You can check allocated size using `sys.getsizeof()`.

---

## 72. What is the memory layout of a Python list?

### Answer

A Python list stores:

* An array of pointers to Python objects.
* Its current length.
* Its allocated capacity.

Example:

```python
import sys

lst = []
for i in range(10):
    lst.append(i)
    print(len(lst), sys.getsizeof(lst))
```

### Key Interview Points

* Each element is a pointer (8 bytes on 64-bit systems).
* The list does not store values directly — it stores references.

---

## 73. How is a Python dict implemented internally?

### Answer

Python dicts use an open-addressing hash table.

* Keys are hashed using `__hash__()`.
* The hash determines the slot index.
* Collisions are resolved using probing.
* Since Python 3.6, dicts use a compact, ordered representation.

### Key Interview Points

* Average O(1) for get, set, delete.
* Ordered by insertion order since Python 3.7.

---

## 74. What happens when you delete an element from the middle of a list?

### Answer

All elements after the deleted index are shifted left.

Example:

```python
lst = [1, 2, 3, 4, 5]
del lst[2]
print(lst)
```

Output:

```
[1, 2, 4, 5]
```

Complexity:

```
O(n)
```

### Key Interview Points

* This is why `pop(0)` is O(n) — all elements shift.
* Use `collections.deque` for efficient front deletion.

---

## 75. What is `collections.deque` and when should you use it?

### Answer

`deque` (double-ended queue) supports O(1) append and pop from both ends.

Example:

```python
from collections import deque

dq = deque([1, 2, 3])

dq.appendleft(0)
dq.append(4)

print(dq)

dq.popleft()
print(dq)
```

Output:

```
deque([0, 1, 2, 3, 4])
deque([1, 2, 3, 4])
```

### Key Interview Points

* Use `deque` when you need O(1) operations at both ends.
* Lists have O(n) `pop(0)` and `insert(0, x)`.

---

## 76. Implement a stack using a list.

### Answer

```python
stack = []

stack.append(1)
stack.append(2)
stack.append(3)

print(stack.pop())
print(stack.pop())
print(stack)
```

Output:

```
3
2
[1]
```

### Key Interview Points

* LIFO — Last In, First Out.
* `append()` = push, `pop()` = pop. Both O(1).

---

## 77. Implement a queue using a list vs deque.

### Answer

Using list (inefficient):

```python
queue = []
queue.append(1)
queue.append(2)
queue.pop(0)       # O(n) — shifts all elements
```

Using deque (efficient):

```python
from collections import deque

queue = deque()
queue.append(1)
queue.append(2)
queue.popleft()    # O(1)
```

### Key Interview Points

* Always use `deque` for queue operations.
* `list.pop(0)` is O(n).

---

## 78. How do you find all duplicates in a list?

### Answer

```python
from collections import Counter

def find_duplicates(lst):
    freq = Counter(lst)
    return [item for item, count in freq.items() if count > 1]

print(find_duplicates([1, 2, 2, 3, 3, 3, 4]))
```

Output:

```
[2, 3]
```

---

## 79. How do you check if a list contains all unique elements?

### Answer

```python
def all_unique(lst):
    return len(lst) == len(set(lst))

print(all_unique([1, 2, 3, 4]))
print(all_unique([1, 2, 2, 3]))
```

Output:

```
True
False
```

---

## 80. How do you find the intersection of multiple lists?

### Answer

```python
from functools import reduce

lists = [[1, 2, 3, 4], [2, 3, 4, 5], [3, 4, 5, 6]]
result = list(reduce(lambda a, b: set(a) & set(b), lists))
print(result)
```

Output:

```
[3, 4]
```

---

## 81. How do you zip two lists into a dictionary?

### Answer

```python
keys   = ["name", "age", "city"]
values = ["Alice", 22, "Delhi"]

d = dict(zip(keys, values))
print(d)
```

Output:

```
{'name': 'Alice', 'age': 22, 'city': 'Delhi'}
```

---

## 82. How do you split a list into chunks of size n?

### Answer

```python
def chunked(lst, n):
    return [lst[i:i+n] for i in range(0, len(lst), n)]

print(chunked([1, 2, 3, 4, 5, 6, 7], 3))
```

Output:

```
[[1, 2, 3], [4, 5, 6], [7]]
```

---

## 83. How do you convert a list of tuples into a dictionary?

### Answer

```python
pairs = [("a", 1), ("b", 2), ("c", 3)]
d     = dict(pairs)
print(d)
```

Output:

```
{'a': 1, 'b': 2, 'c': 3}
```

---

## 84. How do you find the index of the maximum element in a list?

### Answer

```python
lst = [3, 7, 1, 9, 4]
print(lst.index(max(lst)))
```

Output:

```
3
```

---

## 85. How do you create a frequency map using a dictionary?

### Answer

```python
words = ["apple", "banana", "apple", "cherry", "banana", "apple"]
freq  = {}

for word in words:
    freq[word] = freq.get(word, 0) + 1

print(freq)
```

Output:

```
{'apple': 3, 'banana': 2, 'cherry': 1}
```

---

## 86. How do you sort a dictionary by its values?

### Answer

```python
scores  = {"alice": 90, "bob": 75, "charlie": 85}
sorted_ = dict(sorted(scores.items(), key=lambda x: x[1], reverse=True))
print(sorted_)
```

Output:

```
{'alice': 90, 'charlie': 85, 'bob': 75}
```

---

## 87. How do you find the two most frequent elements in a list?

### Answer

```python
from collections import Counter

lst = [1, 1, 2, 2, 2, 3, 3, 4]
top2 = Counter(lst).most_common(2)
print(top2)
```

Output:

```
[(2, 3), (1, 2)]
```

---

## 88. How do you implement a sliding window maximum?

### Answer

```python
from collections import deque

def sliding_max(nums, k):
    dq     = deque()
    result = []

    for i, num in enumerate(nums):
        while dq and dq[0] < i - k + 1:
            dq.popleft()
        while dq and nums[dq[-1]] < num:
            dq.pop()
        dq.append(i)
        if i >= k - 1:
            result.append(nums[dq[0]])

    return result

print(sliding_max([1, 3, -1, -3, 5, 3, 6, 7], 3))
```

Output:

```
[3, 3, 5, 5, 6, 7]
```

---

## 89. How do you implement a two-sum solution using a dictionary?

### Answer

```python
def two_sum(nums, target):
    seen = {}
    for i, num in enumerate(nums):
        complement = target - num
        if complement in seen:
            return [seen[complement], i]
        seen[num] = i

print(two_sum([2, 7, 11, 15], 9))
```

Output:

```
[0, 1]
```

### Complexity

```
Time:  O(n)
Space: O(n)
```

---

## 90. How do you find the longest consecutive sequence in a list?

### Answer

```python
def longest_consecutive(nums):
    num_set  = set(nums)
    best     = 0

    for num in num_set:
        if num - 1 not in num_set:
            curr, length = num, 1
            while curr + 1 in num_set:
                curr  += 1
                length += 1
            best = max(best, length)

    return best

print(longest_consecutive([100, 4, 200, 1, 3, 2]))
```

Output:

```
4
```

---

## 91. What is the difference between `is` and `==` for lists?

### Answer

`==` compares values.
`is` compares identity (same object in memory).

```python
a = [1, 2, 3]
b = [1, 2, 3]
c = a

print(a == b)
print(a is b)
print(a is c)
```

Output:

```
True
False
True
```

---

## 92. What happens when you multiply a list?

### Answer

```python
lst = [0] * 5
print(lst)

nested = [[0] * 3] * 3
nested[0][0] = 99
print(nested)
```

Output:

```
[0, 0, 0, 0, 0]
[[99, 0, 0], [99, 0, 0], [99, 0, 0]]
```

### Key Interview Points

* `[[0]*3]*3` creates three references to the same inner list.
* Modifying one row modifies all rows.
* Use a list comprehension instead: `[[0]*3 for _ in range(3)]`.

---

## 93. How do you safely update a dictionary while iterating over it?

### Answer

Never modify a dict's keys while iterating — it raises `RuntimeError`.

Safe approach — iterate over a copy:

```python
d = {"a": 1, "b": 2, "c": 3}

for key in list(d.keys()):
    if d[key] < 2:
        del d[key]

print(d)
```

Output:

```
{'b': 2, 'c': 3}
```

---

## 94. What is the difference between `dict.update()` and `dict |= ` (Python 3.9+)?

### Answer

Both merge another dict into the current one.

```python
a = {"x": 1}
b = {"y": 2, "x": 99}

a.update(b)
print(a)
```

Output:

```
{'x': 99, 'y': 2}
```

```python
a = {"x": 1}
a |= b
print(a)
```

Output:

```
{'x': 99, 'y': 2}
```

### Key Interview Points

* Both modify in place and the right-hand dict's values win on conflict.
* `|` (not `|=`) creates a new dict without modifying either original.

---

## 95. What is the difference between `list()` and `[]`?

### Answer

Both create lists but in different ways.

`[]` — list literal, slightly faster.

```python
lst = [1, 2, 3]
```

`list()` — constructor, converts any iterable.

```python
lst = list("abc")
print(lst)
```

Output:

```
['a', 'b', 'c']
```

### Key Interview Points

* `list()` is useful for converting other iterables (tuples, sets, generators, strings).
* `[]` is preferred for creating literal lists.

---

## 96. What is the difference between `tuple()` and `()`?

### Answer

`()` — empty tuple literal.

```python
t = ()
```

`tuple()` — constructor, converts any iterable.

```python
t = tuple([1, 2, 3])
print(t)
```

Output:

```
(1, 2, 3)
```

---

## 97. How do you convert between list, tuple, set, and dict?

### Answer

```python
lst  = [1, 2, 3, 2, 1]

print(tuple(lst))
print(set(lst))
print(list(set(lst)))

pairs = [("a", 1), ("b", 2)]
print(dict(pairs))
```

Output:

```
(1, 2, 3, 2, 1)
{1, 2, 3}
[1, 2, 3]
{'a': 1, 'b': 2}
```

---

## 98. What is a heap and how do you use one with lists in Python?

### Answer

Python provides a min-heap via `heapq`.

Example:

```python
import heapq

nums = [5, 1, 8, 3, 2]
heapq.heapify(nums)

print(heapq.heappop(nums))
print(heapq.heappop(nums))
```

Output:

```
1
2
```

### Key Interview Points

* `heapq` implements a min-heap on top of a regular Python list.
* Useful for problems involving the k smallest/largest elements.

---

## 99. What is `bisect` module and how is it used with lists?

### Answer

`bisect` provides binary search functions for sorted lists.

Example:

```python
import bisect

lst = [1, 3, 5, 7, 9]

print(bisect.bisect_left(lst, 5))
print(bisect.bisect_right(lst, 5))

bisect.insort(lst, 6)
print(lst)
```

Output:

```
2
3
[1, 3, 5, 6, 7, 9]
```

### Key Interview Points

* `bisect_left` — index of leftmost position to insert.
* `bisect_right` — index of rightmost position to insert.
* `insort` — inserts while keeping the list sorted in O(n).

---

## 100. What are the most commonly asked list, tuple, set, and dict questions in Python interviews?

### Answer

#### Lists
* Difference between `append()` and `extend()`
* Shallow vs deep copy
* List comprehensions
* Time complexity of operations
* Remove duplicates preserving order
* Two-sum problem
* Sliding window maximum

#### Tuples
* Why are tuples faster than lists
* Single element tuple syntax
* Tuple as dict key
* Named tuples

#### Sets
* O(1) membership testing
* Set operations — union, intersection, difference
* `discard()` vs `remove()`
* Frozenset

#### Dictionaries
* `get()` vs direct access
* `defaultdict` and `Counter`
* Dict comprehension
* Merging dicts
* Sorting by value
* Two-sum using dict
* How hashing works internally

#### Advanced
* Dynamic array resizing
* Hash collisions
* `collections.deque` vs list
* `heapq` for priority queues
* `bisect` for sorted insertion

### Final Interview Tip

If you master:

* Time complexities of all four data structures
* List comprehensions and dict comprehensions
* Set operations for fast lookups
* `Counter`, `defaultdict`, `namedtuple`, `deque`
* Common coding patterns — two-sum, sliding window, frequency map

you will be able to answer **95%+ of Python data structure interview questions** across software engineering, data engineering, and backend development interviews.