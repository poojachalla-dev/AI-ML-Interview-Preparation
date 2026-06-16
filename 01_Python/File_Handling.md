## 1. What is file handling in Python?

### Answer

File handling is the process of creating, reading, writing, updating, and deleting files using Python.

### Why is it Important?

File handling allows programs to:

* Store data permanently
* Read existing data
* Generate reports
* Process logs
* Work with CSV, JSON, and text files

### Example

```python
file = open("sample.txt", "r")
content = file.read()
file.close()
```

### Key Interview Point

Variables store data temporarily, while files provide persistent storage.

---

## 2. Why do we need file handling?

### Answer

File handling is required because data stored in memory is lost when a program terminates.

### Benefits

* Data persistence
* Configuration storage
* Report generation
* Database backups
* Log management

### Example

```python
with open("users.txt", "w") as file:
    file.write("Pooh")
```

---

## 3. What is a file object?

### Answer

A file object is an object returned by the `open()` function that allows interaction with a file.

### Example

```python
file = open("sample.txt", "r")

print(type(file))
```

### Output

```text
<class '_io.TextIOWrapper'>
```

### Key Interview Point

All file operations are performed through file objects.

---

## 4. What is the open() function?

### Answer

The `open()` function is used to open a file.

### Syntax

```python
open(file_name, mode)
```

### Example

```python
file = open("sample.txt", "r")
```

### Key Interview Point

`open()` does not read the file automatically; it only opens it.

---

## 5. What are the parameters of open()?

### Answer

Common parameters:

| Parameter | Description        |
| --------- | ------------------ |
| file      | File path          |
| mode      | Access mode        |
| encoding  | Character encoding |

### Example

```python
file = open(
    "sample.txt",
    "r",
    encoding="utf-8"
)
```

---

## 6. What are file modes in Python?

### Answer

File modes determine how a file is accessed.

### Common Modes

| Mode | Meaning        |
| ---- | -------------- |
| r    | Read           |
| w    | Write          |
| a    | Append         |
| x    | Create         |
| rb   | Read Binary    |
| wb   | Write Binary   |
| r+   | Read and Write |

### Key Interview Point

Choosing the correct file mode is important.

---

## 7. What is read mode (r)?

### Answer

Read mode opens a file for reading.

### Example

```python
file = open("sample.txt", "r")
```

### Key Interview Point

The file must already exist.

---

## 8. What happens if a file does not exist in read mode?

### Answer

Python raises:

```python
FileNotFoundError
```

### Example

```python
open("missing.txt", "r")
```

### Output

```text
FileNotFoundError
```

---

## 9. What is write mode (w)?

### Answer

Write mode creates a new file or overwrites an existing file.

### Example

```python
file = open("sample.txt", "w")
```

### Key Interview Point

Existing content is erased.

---

## 10. What happens when write mode is used on an existing file?

### Answer

The file contents are deleted before writing.

### Example

Original File

```text
Hello World
```

Code

```python
open("sample.txt", "w")
```

Result

```text
Empty File
```

---

## 11. What is append mode (a)?

### Answer

Append mode adds data to the end of a file.

### Example

```python
file = open("sample.txt", "a")

file.write("Hello")
```

### Key Interview Point

Existing content remains unchanged.

---

## 12. What is exclusive creation mode (x)?

### Answer

Creates a file only if it does not already exist.

### Example

```python
open("data.txt", "x")
```

### Key Interview Point

Raises FileExistsError if the file already exists.

---

## 13. What is binary mode?

### Answer

Binary mode is used for non-text files.

Examples:

* Images
* Videos
* PDFs
* Audio Files

### Example

```python
file = open("photo.jpg", "rb")
```

---

## 14. What is text mode?

### Answer

Text mode treats file contents as strings.

### Example

```python
file = open("notes.txt", "r")
```

### Key Interview Point

Text mode is the default mode.

---

## 15. What is the default mode of open()?

### Answer

The default mode is:

```python
"r"
```

### Example

```python
open("sample.txt")
```

Equivalent to:

```python
open("sample.txt", "r")
```

---

## 16. What is the read() method?

### Answer

`read()` reads the entire file contents.

### Example

```python
file = open("sample.txt", "r")

content = file.read()

print(content)
```

---

## 17. What does read(size) do?

### Answer

Reads a specified number of characters.

### Example

```python
file.read(5)
```

Output

```text
Hello
```

### Key Interview Point

Useful for large files.

---

## 18. What is readline()?

### Answer

Reads one line at a time.

### Example

```python
line = file.readline()
```

### Output

```text
First line
```

---

## 19. What is readlines()?

### Answer

Reads all lines into a list.

### Example

```python
lines = file.readlines()
```

Output

```python
[
    "Line1\n",
    "Line2\n",
    "Line3\n"
]
```

---

## 20. What is the difference between read(), readline(), and readlines()?

### Answer

| Method      | Output        |
| ----------- | ------------- |
| read()      | Entire file   |
| readline()  | Single line   |
| readlines() | List of lines |

### Key Interview Point

Frequently asked interview question.

---

## 21. What is the write() method?

### Answer

Writes data to a file.

### Example

```python
file.write("Hello World")
```

### Key Interview Point

Returns the number of characters written.

---

## 22. What is writelines()?

### Answer

Writes multiple lines from an iterable.

### Example

```python
lines = [
    "Python\n",
    "Java\n",
    "C++\n"
]

file.writelines(lines)
```

---

## 23. Does writelines() add newline characters automatically?

### Answer

No.

### Example

```python
file.writelines(
    ["A", "B", "C"]
)
```

Output

```text
ABC
```

### Key Interview Point

You must manually add `\n`.

---

## 24. What is the close() method?

### Answer

Closes the file and releases system resources.

### Example

```python
file.close()
```

### Key Interview Point

Always close files after use.

---

## 25. Why is closing files important?

### Answer

Closing files:

* Prevents memory leaks
* Releases file locks
* Saves buffered data
* Improves performance

### Example

```python
file = open("sample.txt")

file.close()
```

### Key Interview Point

Using `with open()` automatically closes files and is considered the best practice.

---

## 26. What is the with statement in Python?

### Answer

The `with` statement automatically manages resources and ensures files are closed properly.

### Example

```python
with open("sample.txt", "r") as file:
    content = file.read()
```

### Key Interview Point

Using `with` is the recommended way to work with files.

---

## 27. Why is with preferred over open() and close()?

### Answer

Benefits:

- Automatic file closing
- Cleaner code
- Prevents resource leaks
- Exception-safe

### Traditional Approach

```python
file = open("sample.txt")

try:
    data = file.read()

finally:
    file.close()
```

### Better Approach

```python
with open("sample.txt") as file:
    data = file.read()
```

---

## 28. What is a context manager?

### Answer

A context manager automatically handles setup and cleanup operations.

### Example

```python
with open("sample.txt") as file:
    data = file.read()
```

### Key Interview Point

The file object acts as a context manager.

---

## 29. How does with work internally?

### Answer

Internally it uses:

```python
__enter__()
__exit__()
```

### Flow

```text
Enter Context
↓
Execute Block
↓
Exit Context
```

---

## 30. What happens if an exception occurs inside with?

### Answer

The file is still closed automatically.

### Example

```python
with open("sample.txt") as file:
    10 / 0
```

### Key Interview Point

This makes `with` exception-safe.

---

## 31. What is a file pointer?

### Answer

A file pointer indicates the current position inside a file.

### Example

```python
file = open("sample.txt")

print(file.tell())
```

### Output

```text
0
```

---

## 32. What is tell()?

### Answer

`tell()` returns the current file pointer position.

### Example

```python
file.read(5)

print(file.tell())
```

### Output

```text
5
```

---

## 33. What is seek()?

### Answer

`seek()` moves the file pointer to a specific position.

### Example

```python
file.seek(0)
```

Moves pointer to beginning.

---

## 34. Why is seek() useful?

### Answer

Allows re-reading or skipping portions of a file.

### Example

```python
file.read(5)

file.seek(0)

file.read(5)
```

---

## 35. What does seek(0) do?

### Answer

Moves pointer to the beginning of the file.

### Example

```python
file.seek(0)
```

### Key Interview Point

Very commonly asked.

---

## 36. What does seek(0, 2) do?

### Answer

Moves pointer to the end of the file.

### Example

```python
file.seek(0, 2)
```

### Usage

Useful for determining file size.

---

## 37. What is flush()?

### Answer

Forces buffered data to be written immediately.

### Example

```python
file.write("Hello")

file.flush()
```

### Key Interview Point

Useful for logs and real-time systems.

---

## 38. What is buffering?

### Answer

Buffering temporarily stores data before writing it to disk.

### Benefits

- Faster I/O
- Reduced disk access
- Better performance

---

## 39. What is truncate()?

### Answer

Used to resize a file.

### Example

```python
file.truncate(5)
```

### Output

Only first 5 characters remain.

---

## 40. What is the difference between flush() and close()?

### Answer

| flush() | close() |
|----------|----------|
| Writes buffer | Closes file |
| File remains open | File becomes unusable |
| Can continue writing | Cannot write |

---

## 41. How can you check whether a file is closed?

### Answer

Using:

```python
file.closed
```

### Example

```python
print(file.closed)
```

Output

```text
False
```

---

## 42. How do you check if a file exists?

### Answer

Using os.path.exists().

### Example

```python
import os

os.path.exists("data.txt")
```

Output

```python
True
```

---

## 43. What is the os module?

### Answer

The os module provides operating-system functionality.

### Examples

- File operations
- Directory operations
- Path management

```python
import os
```

---

## 44. How do you delete a file?

### Answer

Using:

```python
os.remove()
```

### Example

```python
import os

os.remove("data.txt")
```

---

## 45. What happens if a deleted file does not exist?

### Answer

Python raises:

```python
FileNotFoundError
```

### Example

```python
os.remove("missing.txt")
```

---

## 46. How do you rename a file?

### Answer

Using:

```python
os.rename()
```

### Example

```python
os.rename(
    "old.txt",
    "new.txt"
)
```

---

## 47. How do you create a directory?

### Answer

Using:

```python
os.mkdir()
```

### Example

```python
os.mkdir("Projects")
```

---

## 48. How do you create nested directories?

### Answer

Using:

```python
os.makedirs()
```

### Example

```python
os.makedirs(
    "Python/Files/Examples"
)
```

---

## 49. How do you remove a directory?

### Answer

Using:

```python
os.rmdir()
```

### Example

```python
os.rmdir("Projects")
```

### Key Interview Point

Directory must be empty.

---

## 50. What is pathlib?

### Answer

`pathlib` is the modern object-oriented path library.

### Example

```python
from pathlib import Path

file = Path("data.txt")

print(file.exists())
```

### Benefits

- Cleaner syntax
- Cross-platform support
- Object-oriented design

---

## 51. Why is pathlib preferred over os.path?

### Answer

`pathlib` provides an object-oriented approach to file and path handling.

### Example

```python
from pathlib import Path

file = Path("data.txt")

print(file.exists())
```

### Advantages

- Cleaner syntax
- More readable
- Cross-platform
- Rich API

### Key Interview Point

Modern Python projects prefer `pathlib`.

---

## 52. How do you get the current working directory?

### Answer

Using `os.getcwd()`.

### Example

```python
import os

print(os.getcwd())
```

### Output

```text
C:\Projects\Python
```

---

## 53. How do you change the current working directory?

### Answer

Using `os.chdir()`.

### Example

```python
import os

os.chdir("Documents")
```

---

## 54. How do you list files in a directory?

### Answer

Using `os.listdir()`.

### Example

```python
import os

print(os.listdir())
```

### Output

```python
['data.txt', 'image.jpg']
```

---

## 55. How do you iterate through directory contents?

### Answer

Using a loop.

### Example

```python
import os

for file in os.listdir():
    print(file)
```

---

## 56. What is shutil?

### Answer

`shutil` is a high-level file operations module.

### Features

- Copy files
- Move files
- Delete directories
- Archive handling

### Example

```python
import shutil
```

---

## 57. How do you copy a file?

### Answer

Using `shutil.copy()`.

### Example

```python
import shutil

shutil.copy(
    "source.txt",
    "backup.txt"
)
```

---

## 58. What is the difference between copy() and copy2()?

### Answer

| copy() | copy2() |
|----------|----------|
| Copies file contents | Copies contents + metadata |
| Faster | Preserves timestamps |

### Example

```python
shutil.copy2(
    "source.txt",
    "backup.txt"
)
```

---

## 59. How do you move a file?

### Answer

Using `shutil.move()`.

### Example

```python
import shutil

shutil.move(
    "data.txt",
    "Archive/data.txt"
)
```

---

## 60. How do you copy an entire directory?

### Answer

Using `shutil.copytree()`.

### Example

```python
shutil.copytree(
    "Project",
    "Project_Backup"
)
```

---

## 61. How do you delete an entire directory?

### Answer

Using `shutil.rmtree()`.

### Example

```python
shutil.rmtree("Project")
```

### Warning

Deletes everything permanently.

---

## 62. What is directory traversal?

### Answer

Directory traversal means visiting all files and folders recursively.

### Example

```python
import os

for root, dirs, files in os.walk("."):
    print(root)
```

---

## 63. What does os.walk() return?

### Answer

Returns:

```python
(root, dirs, files)
```

### Example

```python
for root, dirs, files in os.walk("."):
    print(root)
    print(dirs)
    print(files)
```

---

## 64. How can you find all Python files in a directory?

### Answer

Using `os.walk()`.

### Example

```python
for root, dirs, files in os.walk("."):

    for file in files:

        if file.endswith(".py"):
            print(file)
```

---

## 65. What is a temporary file?

### Answer

A temporary file exists for short-term storage.

### Common Uses

- Testing
- Intermediate processing
- Caching

---

## 66. Which module creates temporary files?

### Answer

The `tempfile` module.

### Example

```python
import tempfile
```

---

## 67. How do you create a temporary file?

### Answer

Using `NamedTemporaryFile()`.

### Example

```python
import tempfile

temp = tempfile.NamedTemporaryFile()
```

---

## 68. Why use temporary files?

### Answer

Benefits:

- Automatic cleanup
- Security
- Testing support
- Reduced manual management

---

## 69. What is binary file handling?

### Answer

Binary file handling is used for non-text data.

Examples:

- Images
- Videos
- PDFs
- Audio files

---

## 70. How do you read a binary file?

### Answer

Using `rb` mode.

### Example

```python
with open(
    "image.jpg",
    "rb"
) as file:

    data = file.read()
```

---

## 71. How do you write a binary file?

### Answer

Using `wb` mode.

### Example

```python
with open(
    "copy.jpg",
    "wb"
) as file:

    file.write(data)
```

---

## 72. What is serialization?

### Answer

Serialization converts Python objects into a storable format.

### Example

```python
Python Object
↓
File
```

### Key Interview Point

Serialization is important for persistence.

---

## 73. What is deserialization?

### Answer

Deserialization converts stored data back into Python objects.

### Example

```python
File
↓
Python Object
```

---

## 74. What is Pickle?

### Answer

Pickle is Python's built-in serialization module.

### Example

```python
import pickle
```

### Key Interview Point

Frequently asked in interviews.

---

## 75. Why is Pickle used?

### Answer

Pickle allows saving Python objects directly.

### Example

```python
data = {
    "name": "Pooh",
    "age": 25
}
```

Can be stored and restored without manual conversion.

---

## 76. How do you serialize an object using Pickle?

### Answer

Using `pickle.dump()`.

### Example

```python
import pickle

data = {
    "name": "Pooh",
    "age": 25
}

with open("data.pkl", "wb") as file:
    pickle.dump(data, file)
```

### Key Interview Point

`dump()` writes serialized data to a file.

---

## 77. How do you deserialize an object using Pickle?

### Answer

Using `pickle.load()`.

### Example

```python
import pickle

with open("data.pkl", "rb") as file:
    data = pickle.load(file)

print(data)
```

### Output

```python
{'name': 'Pooh', 'age': 25}
```

---

## 78. What data types can Pickle serialize?

### Answer

Pickle can serialize:

- Lists
- Tuples
- Dictionaries
- Sets
- Functions
- Classes
- Custom Objects

### Example

```python
data = [1, 2, 3]
pickle.dumps(data)
```

---

## 79. Is Pickle secure?

### Answer

No.

### Warning

Never unpickle data from untrusted sources.

### Reason

Pickle can execute arbitrary code during deserialization.

### Key Interview Point

A favorite security interview question.

---

## 80. What is JSON?

### Answer

JSON stands for:

```text
JavaScript Object Notation
```

Used for:

- APIs
- Configuration files
- Data exchange

### Example

```json
{
  "name": "Pooh",
  "age": 25
}
```

---

## 81. Why is JSON preferred over Pickle for data exchange?

### Answer

Benefits:

- Language independent
- Human readable
- Secure
- API friendly

### Key Interview Point

JSON is the industry standard for web applications.

---

## 82. How do you read a JSON file?

### Answer

Using `json.load()`.

### Example

```python
import json

with open("data.json") as file:
    data = json.load(file)
```

---

## 83. How do you write JSON data to a file?

### Answer

Using `json.dump()`.

### Example

```python
import json

data = {
    "name": "Pooh"
}

with open("data.json", "w") as file:
    json.dump(data, file)
```

---

## 84. What is json.dumps()?

### Answer

Converts a Python object into a JSON string.

### Example

```python
import json

data = {"name": "Pooh"}

json_string = json.dumps(data)

print(json_string)
```

Output

```json
{"name":"Pooh"}
```

---

## 85. What is json.loads()?

### Answer

Converts a JSON string into a Python object.

### Example

```python
import json

data = json.loads(
    '{"name":"Pooh"}'
)
```

---

## 86. What is CSV?

### Answer

CSV stands for:

```text
Comma Separated Values
```

Used for:

- Data analysis
- Reporting
- Excel interoperability

### Example

```csv
Name,Age
Pooh,25
John,30
```

---

## 87. Which module is used for CSV handling?

### Answer

Python provides:

```python
csv
```

module.

### Example

```python
import csv
```

---

## 88. How do you read a CSV file?

### Answer

Using `csv.reader()`.

### Example

```python
import csv

with open("data.csv") as file:

    reader = csv.reader(file)

    for row in reader:
        print(row)
```

---

## 89. How do you write to a CSV file?

### Answer

Using `csv.writer()`.

### Example

```python
import csv

with open(
    "data.csv",
    "w",
    newline=""
) as file:

    writer = csv.writer(file)

    writer.writerow(
        ["Name", "Age"]
    )
```

---

## 90. What is DictReader?

### Answer

Reads CSV rows as dictionaries.

### Example

```python
import csv

with open("data.csv") as file:

    reader = csv.DictReader(file)

    for row in reader:
        print(row["Name"])
```

---

## 91. What is DictWriter?

### Answer

Writes dictionaries into CSV files.

### Example

```python
writer.writerow({
    "Name": "Pooh",
    "Age": 25
})
```

### Key Interview Point

Very useful in ETL pipelines.

---

## 92. How do you process large files efficiently?

### Answer

Read files line-by-line instead of loading everything into memory.

### Example

```python
with open("large.log") as file:

    for line in file:
        process(line)
```

### Key Interview Point

Important for Data Engineering interviews.

---

## 93. Why avoid read() for very large files?

### Answer

`read()` loads the entire file into memory.

### Problem

```python
content = file.read()
```

Large files may cause:

- Slow execution
- High memory usage
- MemoryError

---

## 94. What is memory-efficient file processing?

### Answer

Processing data incrementally.

### Example

```python
for line in file:
    process(line)
```

### Benefits

- Low memory usage
- Faster processing
- Better scalability

---

## 95. How do you safely handle missing files?

### Answer

Using exception handling.

### Example

```python
try:

    with open("data.txt") as file:
        data = file.read()

except FileNotFoundError:
    print("File not found")
```

---

## 96. What file-related exceptions are commonly encountered?

### Answer

Common exceptions:

- FileNotFoundError
- PermissionError
- IsADirectoryError
- NotADirectoryError
- EOFError

### Key Interview Point

Know these for interviews.

---

## 97. How do you check file permissions?

### Answer

Using `os.access()`.

### Example

```python
import os

os.access(
    "data.txt",
    os.R_OK
)
```

---

## 98. What are file handling best practices?

### Answer

Best practices:

- Use `with`
- Handle exceptions
- Use pathlib
- Avoid hardcoded paths
- Process large files incrementally

### Key Interview Point

Frequently discussed in system design interviews.

---

## 99. What are common file handling interview coding questions?

### Answer

Popular questions:

- Count words in a file
- Find duplicate lines
- Merge files
- Copy files
- Parse CSV
- Parse JSON
- Find largest file
- Directory traversal

---

## 100. What file handling concepts should every Python developer know?

### Answer

### Fundamentals

- open()
- read()
- write()
- close()

### Intermediate

- seek()
- tell()
- pathlib
- shutil

### Advanced

- Pickle
- JSON
- CSV
- Temporary files
- Binary files

### Production Concepts

- Logging
- Exception handling
- Large file processing
- Security
- Resource management

### Final Interview Tip

If you understand:

- File modes
- Context managers
- Path handling
- CSV
- JSON
- Pickle
- Large file processing

you can confidently answer **95%+ of Python File Handling interview questions** asked in Software Engineering, Data Engineering, Backend Development, Machine Learning, and AI Engineering interviews.

