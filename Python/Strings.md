## 1. What is a string in Python?

### Answer

A string is an immutable sequence of Unicode characters used to represent textual data.

Example:

```python
name = "Python"
```

### Key Interview Points

* Strings are ordered sequences.
* Strings are immutable.
* Strings support indexing and slicing.

---

## 2. Why are strings immutable?

### Answer

Strings are immutable to improve:

* Memory efficiency
* Security
* Hashability
* Thread safety

Once created, a string cannot be modified.

Example:

```python
s = "hello"
# s[0] = "H"  # TypeError
```

### Key Interview Points

* Any modification creates a new string object.
* Enables string interning and hash caching.

---

## 3. What are the advantages of immutable strings?

### Answer

Advantages include:

* Safe dictionary keys
* Thread-safe behavior
* Better memory optimization
* Easier caching
* Predictable behavior

### Key Interview Points

Immutability allows Python to perform internal optimizations.

---

## 4. How are strings stored internally?

### Answer

Python stores strings as Unicode objects.

Internally, Python uses optimized storage based on the largest character present in the string.

Examples:

* ASCII characters use 1 byte.
* Larger Unicode characters may use 2 or 4 bytes.

### Key Interview Points

Modern Python uses PEP 393's flexible string representation.

---

## 5. What is Unicode?

### Answer

Unicode is a universal character encoding standard that assigns a unique code point to every character from every language.

Example:

```python
"A"
"न"
"你"
"😊"
```

### Key Interview Points

Unicode allows multilingual text processing.

---

## 6. What is UTF-8 encoding?

### Answer

UTF-8 is the most widely used Unicode encoding format.

Characteristics:

* Variable length
* Uses 1–4 bytes
* Backward compatible with ASCII

Example:

```python
text = "Python"
data = text.encode("utf-8")
```

---

## 7. What is the difference between ASCII and Unicode?

### Answer

| ASCII          | Unicode                |
| -------------- | ---------------------- |
| 128 characters | Millions of characters |
| English only   | Global languages       |
| 7-bit encoding | Universal standard     |

Example:

```python
ASCII: A
Unicode: 😊
```

---

## 8. What is the difference between str and bytes?

### Answer

`str`

* Human-readable text
* Unicode characters

`bytes`

* Raw binary data
* Used for files and networking

Example:

```python
text = "hello"
data = b"hello"
```

### Key Interview Points

Strings represent text; bytes represent binary information.

---

## 9. What is encoding and decoding?

### Answer

Encoding:

```python
text = "hello"
data = text.encode("utf-8")
```

Converts string → bytes.

Decoding:

```python
data.decode("utf-8")
```

Converts bytes → string.

---

## 10. What is string indexing?

### Answer

Indexing accesses individual characters.

Example:

```python
text = "Python"

text[0]
```

Output:

```python
'P'
```

### Key Interview Points

Strings use zero-based indexing.

---

## 11. What is negative indexing?

### Answer

Negative indices count from the end.

Example:

```python
text = "Python"

text[-1]
```

Output:

```python
'n'
```

### Key Interview Points

Useful for accessing trailing characters.

---

## 12. What is string slicing?

### Answer

Slicing extracts a portion of a string.

Syntax:

```python
string[start:stop]
```

Example:

```python
text = "Python"

text[1:4]
```

Output:

```python
yth
```

---

## 13. Explain slice notation [start:stop:step].

### Answer

Syntax:

```python
sequence[start:stop:step]
```

Example:

```python
text = "Python"

text[0:6:2]
```

Output:

```python
Pto
```

### Key Interview Points

* start is inclusive
* stop is exclusive
* step controls increment

---

## 14. How do you reverse a string?

### Answer

Using slicing:

```python
text = "Python"

text[::-1]
```

Output:

```python
nohtyP
```

### Key Interview Points

Most common interview solution.

---

## 15. What is the difference between shallow copy and string assignment?

### Answer

Strings are immutable.

Example:

```python
a = "Python"
b = a
```

No actual copying is required because the string cannot change.

### Key Interview Points

Shallow/deep copy concepts are more relevant for mutable objects.

---

## 16. Why are strings hashable?

### Answer

Strings are immutable, so their hash values never change during their lifetime.

Example:

```python
hash("Python")
```

### Key Interview Points

Hashability allows strings to be:

* Dictionary keys
* Set elements

---

## 17. Can strings be used as dictionary keys?

### Answer

Yes.

Example:

```python
student = {
    "name": "Pooh",
    "age": 22
}
```

### Key Interview Points

Strings are among the most commonly used dictionary keys.

---

## 18. What are common string methods?

### Answer

Examples:

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
"python".upper()
```

Output:

```python
PYTHON
```

---

## 19. What is the difference between upper() and casefold()?

### Answer

`upper()`
Converts text to uppercase.

`casefold()`
Performs more aggressive case normalization for comparisons.

Example:

```python
"straße".casefold()
```

Output:

```python
strasse
```

### Key Interview Points

Use `casefold()` for case-insensitive comparisons.

---

## 20. What is the difference between strip(), lstrip(), and rstrip()?

### Answer

`strip()`
Removes whitespace from both ends.

```python
text.strip()
```

`lstrip()`
Removes from left side only.

```python
text.lstrip()
```

`rstrip()`
Removes from right side only.

```python
text.rstrip()
```

---

## 21. What is string interning?

### Answer

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

### Key Interview Points

Reduces memory usage and improves performance.

---

## 22. How does Python optimize string storage?

### Answer

Python optimizes strings through:

* String interning
* Hash caching
* Compact Unicode representation
* Shared immutable objects

### Key Interview Points

These optimizations improve memory efficiency.

---

## 23. What is the difference between == and is for strings?

### Answer

`==`
Compares values.

```python
a == b
```

`is`
Compares identities.

```python
a is b
```

Example:

```python
a = "Python"
b = "".join(["Py", "thon"])

a == b   # True
a is b   # May be False
```

---

## 24. What happens when two identical string literals are created?

### Answer

Python often interns identical literals.

Example:

```python
a = "Python"
b = "Python"
```

Both variables may reference the same object.

### Key Interview Points

Interning reduces memory consumption.

---

## 25. What is string concatenation?

### Answer

String concatenation combines strings into one.

Example:

```python
first = "Hello"
second = "World"

result = first + second
```

Output:

```python
HelloWorld
```

### Key Interview Points

Concatenation creates a new string because strings are immutable.

---

## 26. Why is repeated string concatenation inefficient?

### Answer

Strings are immutable. Every time you use `+`, Python creates a new string object and copies the contents.

Example:

```python
result = ""

for word in words:
    result += word
```

This repeatedly allocates memory and copies data.

### Key Interview Point

Repeated concatenation can lead to **O(n²)** performance.

---

## 27. Why is `join()` faster than concatenation?

### Answer

`join()` calculates the required memory once and builds the final string in a single operation.

Example:

```python
words = ["Python", "is", "awesome"]

result = " ".join(words)
```

### Key Interview Point

For combining many strings:

```python
"".join(strings)
```

is preferred over repeated `+`.

---

## 28. What is an f-string?

### Answer

An f-string (formatted string literal) allows expressions to be embedded directly inside strings.

Example:

```python
name = "Pooh"

print(f"Hello {name}")
```

Output:

```python
Hello Pooh
```

### Key Interview Point

Introduced in Python 3.6.

---

## 29. What are formatted string literals?

### Answer

Formatted string literals are strings prefixed with `f`.

Example:

```python
age = 22

print(f"Age: {age}")
```

Expressions can also be evaluated:

```python
print(f"{10 + 20}")
```

Output:

```python
30
```

---

## 30. What is the difference between f-strings, format(), and % formatting?

### Answer

### f-string

```python
name = "Pooh"

f"Hello {name}"
```

### format()

```python
"Hello {}".format(name)
```

### % formatting

```python
"Hello %s" % name
```

### Key Interview Point

Modern preference:

```text
f-string > format() > % formatting
```

because f-strings are faster and more readable.

---

## 31. What are raw strings?

### Answer

Raw strings ignore escape sequence processing.

Example:

```python
path = r"C:\Users\Pooh"
```

Instead of treating `\n` or `\t` specially, Python keeps them as literal characters.

---

## 32. Why are raw strings useful in regular expressions?

### Answer

Regular expressions contain many backslashes.

Without raw strings:

```python
"\\d+"
```

With raw strings:

```python
r"\d+"
```

### Key Interview Point

Raw strings improve regex readability.

---

## 33. What is the difference between `split()` and `partition()`?

### Answer

### split()

Returns a list.

```python
"a,b,c".split(",")
```

Output:

```python
['a', 'b', 'c']
```

### partition()

Returns a tuple.

```python
"a,b,c".partition(",")
```

Output:

```python
('a', ',', 'b,c')
```

### Key Interview Point

`partition()` only splits once.

---

## 34. What is the difference between `find()` and `index()`?

### Answer

### find()

Returns:

```python
-1
```

if not found.

### index()

Raises:

```python
ValueError
```

if not found.

Example:

```python
"Python".find("x")
```

returns:

```python
-1
```

---

## 35. What is the difference between `replace()` and `translate()`?

### Answer

### replace()

Simple substitutions.

```python
text.replace("a", "b")
```

### translate()

Uses translation tables.

```python
table = str.maketrans("abc", "xyz")
text.translate(table)
```

### Key Interview Point

`translate()` is more efficient for many replacements.

---

## 36. What is the difference between `startswith()` and `endswith()`?

### Answer

Checks beginning:

```python
text.startswith("Py")
```

Checks ending:

```python
text.endswith("on")
```

### Key Interview Point

Faster and cleaner than slicing for prefix/suffix checks.

---

## 37. What is string formatting?

### Answer

String formatting inserts values into strings.

Example:

```python
name = "Pooh"

f"Hello {name}"
```

Output:

```python
Hello Pooh
```

---

## 38. What are format specifiers?

### Answer

Format specifiers control output appearance.

Example:

```python
price = 12.3456

f"{price:.2f}"
```

Output:

```python
12.35
```

---

## 39. How do you align text using format specifiers?

### Answer

Left align:

```python
f"{name:<10}"
```

Right align:

```python
f"{name:>10}"
```

Center align:

```python
f"{name:^10}"
```

Example:

```python
name = "Pooh"

print(f"|{name:^10}|")
```

---

## 40. How do you format numbers and dates inside strings?

### Answer

Numbers:

```python
value = 1234.567

f"{value:.2f}"
```

Thousands separator:

```python
f"{value:,.2f}"
```

Dates:

```python
from datetime import datetime

today = datetime.now()

f"{today:%Y-%m-%d}"
```

---

## 41. How does Python represent Unicode internally?

### Answer

Modern Python uses a flexible Unicode representation.

Depending on characters present:

* 1-byte storage
* 2-byte storage
* 4-byte storage

### Key Interview Point

This reduces memory usage significantly.

---

## 42. What is PEP 393?

### Answer

PEP 393 introduced Python's flexible string representation.

Benefits:

* Reduced memory consumption
* Faster operations
* Efficient Unicode handling

### Key Interview Point

Implemented in Python 3.3.

---

## 43. What is compact string representation?

### Answer

Python stores strings using the smallest possible character width.

Example:

```python
"hello"
```

uses less memory than:

```python
"😊"
```

### Key Interview Point

Part of PEP 393 optimization.

---

## 44. What is string memory optimization?

### Answer

Python optimizes strings through:

* Interning
* Compact Unicode storage
* Cached hash values
* Shared immutable objects

### Key Interview Point

Large applications benefit greatly from these optimizations.

---

## 45. How are hash values calculated for strings?

### Answer

Python computes a hash based on string contents.

Example:

```python
hash("Python")
```

The same string produces the same hash during a program run.

### Key Interview Point

Used by dictionaries and sets.

---

## 46. Why does Python cache string hash values?

### Answer

Hash computation can be expensive.

Instead of recalculating:

```python
hash(my_string)
```

Python stores the hash after the first computation.

### Key Interview Point

Makes repeated dictionary lookups faster.

---

## 47. What is the time complexity of string indexing?

### Answer

Example:

```python
text[5]
```

Complexity:

```text
O(1)
```

### Key Interview Point

Strings support constant-time indexing.

---

## 48. What is the time complexity of string slicing?

### Answer

Example:

```python
text[2:8]
```

Complexity:

```text
O(k)
```

where:

```text
k = length of slice
```

### Key Interview Point

Python creates a new string.

---

## 49. What is the time complexity of string concatenation?

### Answer

Example:

```python
a + b
```

Complexity:

```text
O(n + m)
```

where:

* n = length of first string
* m = length of second string

### Key Interview Point

A new string is created.

---

## 50. What is the time complexity of membership testing in strings?

### Answer

Example:

```python
"th" in "Python"
```

Worst-case complexity:

```text
O(n)
```

where:

```text
n = string length
```

### Key Interview Point

Python performs substring searching efficiently, but complexity is still linear in the general case.

---

## 51. What is the time complexity of `replace()`?

### Answer

The `replace()` method scans the string and creates a new string.

Example:

```python
text = "banana"
text.replace("a", "o")
```

Complexity:

```text
O(n)
```

where `n` is the string length.

### Key Interview Point

Strings are immutable, so a new string must be created.

---

## 52. What is the time complexity of `split()`?

### Answer

Example:

```python
text = "a,b,c,d"
text.split(",")
```

Complexity:

```text
O(n)
```

Python scans the entire string to find separators.

---

## 53. What is the time complexity of `join()`?

### Answer

Example:

```python
",".join(words)
```

Complexity:

```text
O(total_characters)
```

### Key Interview Point

`join()` is more efficient than repeated concatenation because memory is allocated only once.

---

## 54. Why are strings considered sequences?

### Answer

Strings are ordered collections of characters.

They support:

* Indexing
* Slicing
* Iteration
* Membership testing

Example:

```python
for ch in "Python":
    print(ch)
```

### Key Interview Point

Strings behave similarly to lists and tuples.

---

## 55. What sequence operations are supported by strings?

### Answer

Supported operations:

```python
len()
indexing
slicing
iteration
membership testing
concatenation
repetition
```

Example:

```python
text = "Python"

len(text)
text[0]
text[1:4]
```

---

## 56. What is lexicographical comparison?

### Answer

Strings are compared character by character based on Unicode values.

Example:

```python
"apple" < "banana"
```

Output:

```python
True
```

### Key Interview Point

Similar to dictionary ordering.

---

## 57. How are strings compared internally?

### Answer

Python compares:

1. First character
2. Second character
3. Continue until a difference is found

Example:

```python
"abc" < "abd"
```

Comparison stops at:

```text
c < d
```

### Key Interview Point

String comparison is lexicographical.

---

## 58. What is locale-aware string comparison?

### Answer

Different languages may have different sorting rules.

Example:

```text
ä
```

may be treated differently depending on locale.

Python provides locale-based sorting through the `locale` module.

### Key Interview Point

Important for internationalized applications.

---

## 59. What problems arise when comparing Unicode strings?

### Answer

Visually identical strings can have different internal representations.

Example:

```text
é
```

can be represented as:

```text
single code point
```

or:

```text
e + accent
```

### Key Interview Point

Unicode normalization solves this issue.

---

## 60. What is Unicode normalization?

### Answer

Normalization converts equivalent Unicode strings into a standard representation.

Example:

```python
import unicodedata

unicodedata.normalize("NFC", text)
```

### Key Interview Point

Essential when comparing international text.

---

# Regular Expressions & Pattern Matching

## 61. What is a regular expression?

### Answer

A regular expression (regex) is a pattern used to search, match, or manipulate text.

Example:

```python
import re

re.search(r"\d+", "abc123")
```

Matches:

```text
123
```

---

## 62. What is the `re` module?

### Answer

The `re` module provides regular expression functionality.

Common functions:

```python
re.match()
re.search()
re.findall()
re.sub()
re.compile()
```

### Key Interview Point

The standard Python library for regex operations.

---

## 63. What is the difference between `match()`, `search()`, and `fullmatch()`?

### Answer

### match()

Checks only at the beginning.

```python
re.match("Py", "Python")
```

### search()

Searches anywhere.

```python
re.search("th", "Python")
```

### fullmatch()

Entire string must match.

```python
re.fullmatch(r"\d+", "123")
```

### Key Interview Point

| Function    | Behavior      |
| ----------- | ------------- |
| match()     | Start only    |
| search()    | Anywhere      |
| fullmatch() | Entire string |

---

## 64. What is `findall()`?

### Answer

Returns all matches as a list.

Example:

```python
import re

re.findall(r"\d+", "a1 b22 c333")
```

Output:

```python
['1', '22', '333']
```

---

## 65. What is `finditer()`?

### Answer

Returns an iterator of match objects.

Example:

```python
for match in re.finditer(r"\d+", text):
    print(match.group())
```

### Key Interview Point

Memory efficient for large text.

---

## 66. What are regex groups?

### Answer

Groups capture parts of a pattern.

Example:

```python
import re

match = re.search(r"(\d+)-(\d+)", "123-456")
```

Access:

```python
match.group(1)
match.group(2)
```

Output:

```python
123
456
```

---

## 67. What are named groups?

### Answer

Named groups make regex more readable.

Example:

```python
match = re.search(
    r"(?P<area>\d+)-(?P<number>\d+)",
    "123-456"
)
```

Access:

```python
match.group("area")
```

### Key Interview Point

Useful for complex regex patterns.

---

## 68. What are greedy quantifiers?

### Answer

Greedy quantifiers match as much text as possible.

Example:

```python
re.search(r"<.*>", "<a><b>")
```

Matches:

```text
<a><b>
```

### Key Interview Point

Greedy is the default behavior.

---

## 69. What are non-greedy quantifiers?

### Answer

Non-greedy quantifiers match as little text as possible.

Example:

```python
re.search(r"<.*?>", "<a><b>")
```

Matches:

```text
<a>
```

### Key Interview Point

Add `?` after a quantifier.

---

## 70. What are lookaheads and lookbehinds?

### Answer

Lookarounds check conditions without consuming characters.

### Positive Lookahead

```python
\d+(?=USD)
```

Matches digits followed by:

```text
USD
```

### Positive Lookbehind

```python
(?<=USD)\d+
```

Matches digits preceded by:

```text
USD
```

### Key Interview Point

Lookarounds are powerful tools for advanced pattern matching.

---

## 71. Reverse a string without using built-in functions.

### Answer

```python
def reverse_string(s):
    result = ""

    for char in s:
        result = char + result

    return result
```

Example:

```python
reverse_string("Python")
```

Output:

```text
nohtyP
```

### Complexity

* Time: O(n)
* Space: O(n)

---

## 72. Check whether a string is a palindrome.

### Answer

```python
def is_palindrome(s):
    return s == s[::-1]
```

Example:

```python
is_palindrome("madam")
```

Output:

```text
True
```

### Complexity

* Time: O(n)
* Space: O(n)

---

## 73. Find the first non-repeating character.

### Answer

```python
from collections import Counter

def first_non_repeating(s):
    freq = Counter(s)

    for char in s:
        if freq[char] == 1:
            return char

    return None
```

Example:

```python
first_non_repeating("aabbcdde")
```

Output:

```text
c
```

---

## 74. Find duplicate characters in a string.

### Answer

```python
from collections import Counter

def duplicates(s):
    freq = Counter(s)

    return [ch for ch, count in freq.items()
            if count > 1]
```

Example:

```python
duplicates("programming")
```

Output:

```text
['r', 'g', 'm']
```

---

## 75. Count character frequencies.

### Answer

```python
from collections import Counter

def count_frequency(s):
    return Counter(s)
```

Example:

```python
count_frequency("banana")
```

Output:

```python
{
    'b':1,
    'a':3,
    'n':2
}
```

---

## 76. Remove duplicate characters while preserving order.

### Answer

```python
def remove_duplicates(s):
    seen = set()
    result = []

    for ch in s:
        if ch not in seen:
            seen.add(ch)
            result.append(ch)

    return "".join(result)
```

Example:

```python
remove_duplicates("banana")
```

Output:

```text
ban
```

---

## 77. Check if two strings are anagrams.

### Answer

```python
def is_anagram(a, b):
    return sorted(a) == sorted(b)
```

Example:

```python
is_anagram("listen", "silent")
```

Output:

```text
True
```

### Better Approach

```python
from collections import Counter

Counter(a) == Counter(b)
```

---

## 78. Find the longest common prefix.

### Answer

```python
def longest_common_prefix(words):
    prefix = words[0]

    for word in words[1:]:
        while not word.startswith(prefix):
            prefix = prefix[:-1]

    return prefix
```

Example:

```python
["flower", "flow", "flight"]
```

Output:

```text
fl
```

---

## 79. Find the longest substring without repeating characters.

### Answer

Sliding Window Technique:

```python
def longest_unique_substring(s):
    seen = {}
    left = 0
    max_len = 0

    for right, ch in enumerate(s):
        if ch in seen and seen[ch] >= left:
            left = seen[ch] + 1

        seen[ch] = right
        max_len = max(max_len, right-left+1)

    return max_len
```

Example:

```python
longest_unique_substring("abcabcbb")
```

Output:

```text
3
```

### Complexity

```text
O(n)
```

---

## 80. Implement string compression.

### Answer

Input:

```text
aaabbcccc
```

Output:

```text
a3b2c4
```

Solution:

```python
def compress(s):
    result = []
    count = 1

    for i in range(1, len(s)):
        if s[i] == s[i-1]:
            count += 1
        else:
            result.append(s[i-1] + str(count))
            count = 1

    result.append(s[-1] + str(count))

    return "".join(result)
```

---

## 81. Count vowels and consonants.

### Answer

```python
def count_vowels_consonants(s):
    vowels = "aeiouAEIOU"

    v = c = 0

    for ch in s:
        if ch.isalpha():
            if ch in vowels:
                v += 1
            else:
                c += 1

    return v, c
```

Example:

```python
count_vowels_consonants("Python")
```

Output:

```text
(1, 5)
```

---

## 82. Check whether one string is a rotation of another.

### Answer

```python
def is_rotation(a, b):
    return len(a) == len(b) and b in (a + a)
```

Example:

```python
is_rotation("abcd", "cdab")
```

Output:

```text
True
```

---

## 83. Find all permutations of a string.

### Answer

```python
from itertools import permutations

def all_permutations(s):
    return ["".join(p)
            for p in permutations(s)]
```

Example:

```python
all_permutations("abc")
```

Output:

```text
abc
acb
bac
bca
cab
cba
```

### Complexity

```text
O(n!)
```

---

## 84. Determine if a string contains only unique characters.

### Answer

```python
def all_unique(s):
    return len(set(s)) == len(s)
```

Example:

```python
all_unique("abc")
```

Output:

```text
True
```

---

## 85. Convert a string to an integer without `int()`.

### Answer

```python
def string_to_int(s):
    result = 0

    for ch in s:
        result = result * 10 + (ord(ch) - ord('0'))

    return result
```

Example:

```python
string_to_int("123")
```

Output:

```text
123
```

---

## 86. Implement `strstr()` functionality.

### Answer

```python
def strstr(text, pattern):
    n = len(text)
    m = len(pattern)

    for i in range(n-m+1):
        if text[i:i+m] == pattern:
            return i

    return -1
```

Example:

```python
strstr("Python Programming", "gram")
```

Output:

```text
10
```

---

## 87. Find the most frequent character.

### Answer

```python
from collections import Counter

def most_frequent(s):
    return Counter(s).most_common(1)[0]
```

Example:

```python
most_frequent("banana")
```

Output:

```text
('a', 3)
```

---

## 88. Reverse words in a sentence.

### Answer

Input:

```text
I love Python
```

Output:

```text
Python love I
```

Solution:

```python
def reverse_words(sentence):
    return " ".join(sentence.split()[::-1])
```

---

## 89. Remove all whitespace from a string.

### Answer

```python
def remove_spaces(s):
    return "".join(s.split())
```

Example:

```python
remove_spaces("I love Python")
```

Output:

```text
IlovePython
```

---

## 90. Validate an email address using regex.

### Answer

```python
import re

def valid_email(email):
    pattern = r'^[\w\.-]+@[\w\.-]+\.\w+$'

    return bool(re.match(pattern, email))
```

Example:

```python
valid_email("pooh@gmail.com")
```

Output:

```text
True
```

### Key Interview Point

In production systems, email validation is usually more sophisticated than a simple regex.

---

## 91. Why are strings immutable but lists mutable?

### Answer

Strings are immutable because:

* They are heavily used throughout programs.
* Immutability enables string interning.
* Immutability allows hash caching.
* Immutable objects are thread-safe.
* Strings can be used as dictionary keys.

Lists are mutable because they are designed for dynamic data manipulation.

Example:

```python
name = "Python"

name = name + "3"
```

A new string object is created.

Example:

```python
nums = [1, 2]

nums.append(3)
```

The same list object is modified.

### Key Interview Point

Immutability is a deliberate design choice for performance, safety, and hashability.

---

## 92. How does immutability affect thread safety?

### Answer

Immutable objects cannot be modified after creation.

Therefore:

```text
Multiple threads can safely read the same string.
```

Example:

```python
text = "Machine Learning"
```

Thousands of threads can access this string simultaneously without synchronization.

### Key Interview Point

Immutable objects reduce race conditions and locking requirements.

---

## 93. How does string interning improve performance?

### Answer

String interning stores only one copy of identical strings.

Example:

```python
a = "Python"
b = "Python"
```

Python may store both variables in the same memory location.

Benefits:

* Reduced memory usage
* Faster comparisons
* Better cache utilization

### Key Interview Point

Comparing references is often faster than comparing characters.

---

## 94. What are rope data structures?

### Answer

A Rope is a tree-based string data structure optimized for:

* Frequent insertions
* Frequent deletions
* Very large strings

Instead of storing:

```text
"HelloWorld"
```

as one contiguous block,

a Rope stores:

```text
        Root
       /    \
   Hello    World
```

### Key Interview Point

Ropes are commonly used in text editors and document processing systems.

---

## 95. Why doesn't Python use ropes for strings?

### Answer

Most Python programs:

* Read strings frequently
* Modify strings infrequently

Standard string representation provides:

* Faster indexing
* Faster slicing
* Lower overhead
* Simpler implementation

### Key Interview Point

Python optimizes for the common case rather than heavy editing workloads.

---

## 96. What are the trade-offs of immutable strings?

### Answer

### Advantages

* Thread safety
* Hashability
* Memory sharing
* Predictable behavior

### Disadvantages

* String modifications create new objects
* Heavy concatenation can be expensive

Example:

```python
result = ""

for word in words:
    result += word
```

May create many temporary strings.

### Key Interview Point

Use `join()` when performing large-scale string assembly.

---

## 97. How would you design a high-performance string class?

### Answer

Requirements:

* Efficient indexing
* Efficient slicing
* Low memory usage
* Unicode support
* Fast hashing

Potential optimizations:

* Interning
* Hash caching
* Compact Unicode storage
* Lazy copying
* Rope-like structures for editing

### Key Interview Point

Real-world string implementations involve trade-offs between speed, memory, and complexity.

---

## 98. How would you process gigabyte-sized text files efficiently?

### Answer

Never load the entire file into memory.

Bad:

```python
with open("large.txt") as f:
    data = f.read()
```

Good:

```python
with open("large.txt") as f:
    for line in f:
        process(line)
```

Alternative:

```python
readline()
chunks
generators
```

### Key Interview Point

Streaming data is critical for large-scale systems.

---

## 99. How would you optimize heavy string manipulation workloads?

### Answer

Techniques:

### Use `join()`

```python
"".join(parts)
```

### Use generators

```python
(word.upper() for word in words)
```

### Avoid repeated concatenation

Bad:

```python
result += word
```

### Use compiled regex

```python
pattern = re.compile(...)
```

### Use efficient data structures

```python
list
deque
StringIO
```

### Key Interview Point

Most performance gains come from reducing unnecessary string copies.

---

## 100. What string-related questions are commonly asked in Python interviews?

### Answer

Most frequently asked topics:

#### Fundamentals

* String immutability
* String interning
* Unicode
* UTF-8

#### Methods

* split()
* join()
* replace()
* strip()
* format()

#### Comparisons

* `==` vs `is`
* Lexicographical ordering

#### Complexity

* Indexing
* Slicing
* Concatenation
* Membership testing

#### Regular Expressions

* search()
* match()
* findall()
* Groups
* Lookaheads

#### Coding Problems

* Palindrome check
* Anagram detection
* Longest substring without repetition
* String compression
* Frequency counting
* First non-repeating character

#### Advanced Topics

* PEP 393
* Unicode normalization
* Hashing
* Memory optimization
* Rope data structures

### Final Interview Tip

If you master:

* String fundamentals
* Complexity analysis
* Unicode handling
* Regex
* Common coding problems

you will be able to answer **95%+ of Python string interview questions** asked in software engineering, data engineering, machine learning, and AI engineering interviews.



