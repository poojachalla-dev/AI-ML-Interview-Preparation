## 1. What is file handling in Python?

### Answer

File handling refers to reading from and writing to files on disk using Python's built-in file operations.

Example:

```python
with open("data.txt", "w") as f:
    f.write("Hello, World!")
```

### Key Interview Points

* Python uses the built-in `open()` function for all file operations.
* Files should always be closed after use to release system resources.

---

## 2. What are the different file modes in Python?

### Answer

```
'r'   — read (default)
'w'   — write (overwrites existing content)
'a'   — append
'x'   — exclusive creation, fails if file exists
'b'   — binary mode (e.g., 'rb', 'wb')
't'   — text mode (default)
'+'   — read and write (e.g., 'r+', 'w+')
```

Example:

```python
f = open("data.txt", "r")
print(f.mode)
f.close()
```

Output:

```
r
```

---

## 3. What is the difference between `'w'` and `'a'` mode?

### Answer

`'w'` mode truncates (erases) the file before writing.

```python
with open("data.txt", "w") as f:
    f.write("New content")
```

`'a'` mode appends to the existing content.

```python
with open("data.txt", "a") as f:
    f.write("\nAppended content")
```

### Key Interview Points

* `'w'` creates the file if it doesn't exist, but destroys existing content.
* `'a'` creates the file if it doesn't exist, but preserves existing content.

---

## 4. What is the difference between `'x'` and `'w'` mode?

### Answer

```python
# 'x' fails if file already exists
with open("new_file.txt", "x") as f:
    f.write("content")
```

Output (if file exists):

```
FileExistsError: [Errno 17] File exists: 'new_file.txt'
```

`'w'` would simply overwrite it instead of raising an error.

---

## 5. How do you open a file using `with` statement and why is it preferred?

### Answer

```python
with open("data.txt", "r") as f:
    content = f.read()

print(f.closed)
```

Output:

```
True
```

### Key Interview Points

* `with` automatically closes the file, even if an exception occurs.
* Equivalent manual approach requires explicit try/finally.

---

## 6. What is the manual equivalent of using `with open()`?

### Answer

```python
f = open("data.txt", "r")
try:
    content = f.read()
finally:
    f.close()
```

### Key Interview Points

* `with` is shorter and less error-prone.
* Forgetting `f.close()` can lead to resource leaks (especially with many open files).

---

## 7. What is the difference between `read()`, `readline()`, and `readlines()`?

### Answer

```python
# Sample file content:
# Line 1
# Line 2
# Line 3

with open("data.txt") as f:
    print(f.read())          # entire file as one string
```

```python
with open("data.txt") as f:
    print(f.readline())      # one line, including \n
```

```python
with open("data.txt") as f:
    print(f.readlines())     # list of all lines
```

Output:

```
Line 1
Line 2
Line 3

Line 1

['Line 1\n', 'Line 2\n', 'Line 3\n']
```

---

## 8. How do you read a file line by line efficiently?

### Answer

```python
with open("data.txt") as f:
    for line in f:
        print(line.strip())
```

### Key Interview Points

* Iterating over the file object directly is the most memory-efficient way.
* Unlike `readlines()`, it doesn't load the entire file into memory at once.

---

## 9. What is the difference between text mode and binary mode?

### Answer

Text mode (`'t'`, default) — decodes bytes into strings using an encoding (default usually UTF-8).

```python
with open("data.txt", "r") as f:
    content = f.read()
    print(type(content))
```

Output:

```
<class 'str'>
```

Binary mode (`'b'`) — returns raw bytes without decoding.

```python
with open("image.png", "rb") as f:
    content = f.read()
    print(type(content))
```

Output:

```
<class 'bytes'>
```

### Key Interview Points

* Use binary mode for non-text files like images, PDFs, or executables.
* Mixing text and binary mode operations causes errors.

---

## 10. How do you specify file encoding when opening a file?

### Answer

```python
with open("data.txt", "r", encoding="utf-8") as f:
    content = f.read()
```

### Key Interview Points

* Always explicitly specify encoding for cross-platform consistency.
* Default encoding depends on the OS/locale if not specified, which can cause subtle bugs.

---

## 11. What happens if you try to read a file that doesn't exist?

### Answer

```python
with open("missing.txt", "r") as f:
    content = f.read()
```

Output:

```
FileNotFoundError: [Errno 2] No such file or directory: 'missing.txt'
```

### Key Interview Points

* Always wrap file operations in try/except when the file's existence isn't guaranteed.

---

## 12. How do you handle file-related exceptions?

### Answer

```python
try:
    with open("missing.txt") as f:
        content = f.read()
except FileNotFoundError:
    print("File not found")
except PermissionError:
    print("Permission denied")
```

Output:

```
File not found
```

---

## 13. How do you write multiple lines to a file?

### Answer

Using `writelines()`:

```python
lines = ["Line 1\n", "Line 2\n", "Line 3\n"]

with open("data.txt", "w") as f:
    f.writelines(lines)
```

Or a loop:

```python
with open("data.txt", "w") as f:
    for line in lines:
        f.write(line)
```

### Key Interview Points

* `writelines()` does NOT add newlines automatically — you must include `\n` yourself.

---

## 14. How do you check if a file exists before opening it?

### Answer

Using `os.path`:

```python
import os

if os.path.exists("data.txt"):
    print("File exists")
else:
    print("File does not exist")
```

Using `pathlib`:

```python
from pathlib import Path

if Path("data.txt").exists():
    print("File exists")
```

### Key Interview Points

* `pathlib` is the modern, object-oriented approach (Python 3.4+).
* Checking existence before opening can introduce race conditions — EAFP (try/except) is often preferred.

---

## 15. What is the difference between `os.path` and `pathlib`?

### Answer

`os.path` — function-based, string paths.

```python
import os

path = os.path.join("folder", "file.txt")
print(os.path.exists(path))
```

`pathlib` — object-oriented, modern approach.

```python
from pathlib import Path

path = Path("folder") / "file.txt"
print(path.exists())
```

### Key Interview Points

* `pathlib` is generally preferred in modern Python code (more readable, chainable).
* `os.path` is still widely used in legacy codebases.

---

## 16. How do you get the size of a file?

### Answer

```python
import os

size = os.path.getsize("data.txt")
print(size, "bytes")
```

Using `pathlib`:

```python
from pathlib import Path

size = Path("data.txt").stat().st_size
print(size, "bytes")
```

---

## 17. How do you delete a file in Python?

### Answer

```python
import os

os.remove("data.txt")
```

Using `pathlib`:

```python
from pathlib import Path

Path("data.txt").unlink()
```

### Key Interview Points

* `os.remove()` raises `FileNotFoundError` if the file doesn't exist.
* `Path.unlink(missing_ok=True)` can suppress the error (Python 3.8+).

---

## 18. How do you rename a file?

### Answer

```python
import os

os.rename("old_name.txt", "new_name.txt")
```

Using `pathlib`:

```python
from pathlib import Path

Path("old_name.txt").rename("new_name.txt")
```

---

## 19. How do you create a directory in Python?

### Answer

```python
import os

os.mkdir("new_folder")            # single directory
os.makedirs("a/b/c", exist_ok=True)  # nested directories
```

Using `pathlib`:

```python
from pathlib import Path

Path("new_folder").mkdir(exist_ok=True)
Path("a/b/c").mkdir(parents=True, exist_ok=True)
```

### Key Interview Points

* `mkdir()` fails if parent directories don't exist; `makedirs()` creates them.
* `exist_ok=True` prevents errors if the directory already exists.

---

## 20. How do you list all files in a directory?

### Answer

```python
import os

files = os.listdir(".")
print(files)
```

Using `pathlib`:

```python
from pathlib import Path

files = list(Path(".").iterdir())
print(files)
```

### Key Interview Points

* `os.listdir()` returns names as strings.
* `Path.iterdir()` returns `Path` objects with richer functionality.

---

## 21. How do you find all files matching a pattern (e.g., all .txt files)?

### Answer

Using `glob`:

```python
import glob

txt_files = glob.glob("*.txt")
print(txt_files)
```

Using `pathlib`:

```python
from pathlib import Path

txt_files = list(Path(".").glob("*.txt"))
print(txt_files)
```

### Key Interview Points

* `Path.rglob("*.txt")` searches recursively through subdirectories.

---

## 22. How do you read and write JSON files?

### Answer

Writing:

```python
import json

data = {"name": "Alice", "age": 30}

with open("data.json", "w") as f:
    json.dump(data, f)
```

Reading:

```python
with open("data.json", "r") as f:
    loaded = json.load(f)

print(loaded)
```

Output:

```
{'name': 'Alice', 'age': 30}
```

---

## 23. What is the difference between `json.dump()`/`json.load()` and `json.dumps()`/`json.loads()`?

### Answer

`dump()`/`load()` — work directly with file objects.

```python
json.dump(data, file_obj)
json.load(file_obj)
```

`dumps()`/`loads()` — work with strings.

```python
text = json.dumps(data)
data = json.loads(text)
```

### Key Interview Points

* The "s" suffix stands for "string."
* Use `dumps`/`loads` when you need the JSON as a string (e.g., for an API response).

---

## 24. How do you read and write CSV files?

### Answer

Writing:

```python
import csv

with open("data.csv", "w", newline="") as f:
    writer = csv.writer(f)
    writer.writerow(["name", "age"])
    writer.writerow(["Alice", 30])
```

Reading:

```python
with open("data.csv", "r") as f:
    reader = csv.reader(f)
    for row in reader:
        print(row)
```

Output:

```
['name', 'age']
['Alice', '30']
```

### Key Interview Points

* `newline=""` prevents extra blank lines on Windows.
* All values are read as strings — manual type conversion is needed.

---

## 25. How do you read a CSV file into a dictionary?

### Answer

```python
import csv

with open("data.csv", "r") as f:
    reader = csv.DictReader(f)
    for row in reader:
        print(row)
```

Output:

```
{'name': 'Alice', 'age': '30'}
```

### Key Interview Points

* `DictReader` uses the first row as field names automatically.
* `DictWriter` is the corresponding tool for writing dict rows.

---

## 26. How do you write a list of dictionaries to a CSV file?

### Answer

```python
import csv

data = [
    {"name": "Alice", "age": 30},
    {"name": "Bob", "age": 25},
]

with open("data.csv", "w", newline="") as f:
    writer = csv.DictWriter(f, fieldnames=["name", "age"])
    writer.writeheader()
    writer.writerows(data)
```

---

## 27. How do you read a file in chunks instead of loading it all at once?

### Answer

```python
def read_in_chunks(filepath, chunk_size=1024):
    with open(filepath, "r") as f:
        while True:
            chunk = f.read(chunk_size)
            if not chunk:
                break
            yield chunk

for chunk in read_in_chunks("large_file.txt"):
    process(chunk)
```

### Key Interview Points

* Essential for processing files too large to fit in memory.
* `f.read(n)` reads at most `n` characters/bytes.

---

## 28. What is the difference between `seek()` and `tell()`?

### Answer

`tell()` — returns the current position (in bytes) within the file.

```python
with open("data.txt", "r") as f:
    f.read(5)
    print(f.tell())
```

`seek(offset)` — moves the file cursor to a specific position.

```python
with open("data.txt", "r") as f:
    f.seek(0)         # go back to the beginning
    print(f.read())
```

Output:

```
5
(full file content)
```

---

## 29. What is the role of the third argument in `seek(offset, whence)`?

### Answer

```
whence = 0 — from the start of the file (default)
whence = 1 — from the current position
whence = 2 — from the end of the file
```

Example:

```python
with open("data.bin", "rb") as f:
    f.seek(-10, 2)    # seek 10 bytes before the end
    print(f.read())
```

### Key Interview Points

* `whence=1` and `whence=2` are only supported in binary mode for relative seeking in most implementations.

---

## 30. How do you truncate a file?

### Answer

```python
with open("data.txt", "r+") as f:
    f.truncate(10)    # keep only the first 10 bytes
```

### Key Interview Points

* `truncate()` without an argument truncates at the current position.
* Useful for resizing files without rewriting them entirely.

---

## 31. What is the difference between `os.remove()` and `os.unlink()`?

### Answer

```python
import os

os.remove("data.txt")
os.unlink("data.txt")
```

### Key Interview Points

* They are functionally identical — `os.unlink()` exists for POSIX compatibility/naming.
* Both raise `FileNotFoundError` if the file doesn't exist.

---

## 32. How do you check if a path is a file or a directory?

### Answer

```python
import os

print(os.path.isfile("data.txt"))
print(os.path.isdir("data.txt"))
```

Using `pathlib`:

```python
from pathlib import Path

p = Path("data.txt")
print(p.is_file())
print(p.is_dir())
```

---

## 33. How do you get the absolute path of a file?

### Answer

```python
import os

abs_path = os.path.abspath("data.txt")
print(abs_path)
```

Using `pathlib`:

```python
from pathlib import Path

abs_path = Path("data.txt").resolve()
print(abs_path)
```

---

## 34. How do you split a path into directory and filename?

### Answer

```python
import os

dir_name, file_name = os.path.split("/home/user/data.txt")
print(dir_name, file_name)
```

Output:

```
/home/user data.txt
```

Using `pathlib`:

```python
from pathlib import Path

p = Path("/home/user/data.txt")
print(p.parent)
print(p.name)
```

Output:

```
/home/user
data.txt
```

---

## 35. How do you get a file's extension?

### Answer

```python
import os

_, ext = os.path.splitext("document.pdf")
print(ext)
```

Output:

```
.pdf
```

Using `pathlib`:

```python
from pathlib import Path

print(Path("document.pdf").suffix)
```

---

## 36. How do you copy a file in Python?

### Answer

```python
import shutil

shutil.copy("source.txt", "destination.txt")
```

### Key Interview Points

* `shutil.copy()` copies content and permission bits.
* `shutil.copy2()` also preserves metadata like modification time.
* `shutil.copyfile()` copies content only, no metadata.

---

## 37. How do you move a file or rename it across directories?

### Answer

```python
import shutil

shutil.move("data.txt", "archive/data.txt")
```

### Key Interview Points

* `shutil.move()` works across filesystems, unlike `os.rename()` which can fail across different drives/partitions.

---

## 38. How do you delete an entire directory (with contents)?

### Answer

```python
import shutil

shutil.rmtree("folder_to_delete")
```

### Key Interview Points

* `os.rmdir()` only removes empty directories.
* `shutil.rmtree()` removes a directory and everything inside it recursively.

---

## 39. What is the difference between `os.rmdir()` and `shutil.rmtree()`?

### Answer

```python
import os
import shutil

os.rmdir("empty_folder")        # fails if folder is not empty
shutil.rmtree("folder_with_files")   # removes recursively
```

Output (if `empty_folder` has content):

```
OSError: [Errno 39] Directory not empty: 'empty_folder'
```

---

## 40. How do you create a temporary file?

### Answer

```python
import tempfile

with tempfile.NamedTemporaryFile(delete=True) as tmp:
    tmp.write(b"Temporary data")
    tmp.seek(0)
    print(tmp.read())
```

Output:

```
b'Temporary data'
```

### Key Interview Points

* `delete=True` (default) removes the file automatically when closed.
* Useful for testing and intermediate processing without cluttering the filesystem.

---

## 41. How do you create a temporary directory?

### Answer

```python
import tempfile
import os

with tempfile.TemporaryDirectory() as tmpdir:
    print(tmpdir)
    print(os.listdir(tmpdir))
```

### Key Interview Points

* Automatically cleaned up when the `with` block exits.
* Useful for isolated, disposable test environments.

---

## 42. How do you read a file with a specific buffering strategy?

### Answer

```python
with open("data.txt", "r", buffering=1) as f:    # line buffering
    content = f.read()
```

### Key Interview Points

* `buffering=0` — unbuffered (binary mode only).
* `buffering=1` — line buffered (text mode).
* `buffering=-1` or omitted — uses system default buffer size.

---

## 43. How do you handle Windows vs Unix line endings?

### Answer

```python
with open("data.txt", "r", newline="") as f:
    content = f.read()
```

By default, Python's universal newlines mode translates `\r\n` to `\n` automatically when reading in text mode.

### Key Interview Points

* `newline=""` disables this translation, preserving original line endings exactly.
* `newline="\n"` forces consistent output line endings when writing.

---

## 44. What is universal newline mode?

### Answer

Python automatically recognizes `\n`, `\r`, and `\r\n` as line endings when reading text files, converting them all to `\n` internally.

```python
with open("windows_file.txt", "r") as f:
    for line in f:
        print(repr(line))
```

### Key Interview Points

* This is enabled by default in text mode.
* Binary mode does not perform this translation.

---

## 45. How do you write to a file without overwriting existing content but also not appending?

### Answer

There is no built-in "insert" mode — you must read, modify, and rewrite.

```python
with open("data.txt", "r") as f:
    lines = f.readlines()

lines.insert(0, "New first line\n")

with open("data.txt", "w") as f:
    f.writelines(lines)
```

### Key Interview Points

* File systems don't support true "insertion" — the whole file is effectively rewritten.

---

## 46. How do you read a file and count the number of lines, words, and characters?

### Answer

```python
def file_stats(filepath):
    with open(filepath, "r") as f:
        content = f.read()

    lines = content.splitlines()
    words = content.split()

    return len(lines), len(words), len(content)

print(file_stats("data.txt"))
```

Output:

```
(3, 6, 36)
```

---

## 47. How do you find and replace text in a file?

### Answer

```python
def find_replace(filepath, old, new):
    with open(filepath, "r") as f:
        content = f.read()

    content = content.replace(old, new)

    with open(filepath, "w") as f:
        f.write(content)

find_replace("data.txt", "World", "Python")
```

### Key Interview Points

* Requires reading the entire file into memory — not suitable for huge files.
* For huge files, process and write line by line to a new temp file, then replace the original.

---

## 48. How do you process a very large file line by line and write filtered results to a new file?

### Answer

```python
def filter_large_file(input_path, output_path, keyword):
    with open(input_path, "r") as infile, open(output_path, "w") as outfile:
        for line in infile:
            if keyword in line:
                outfile.write(line)

filter_large_file("large.log", "errors.log", "ERROR")
```

### Key Interview Points

* Processes one line at a time — constant memory usage regardless of file size.
* Standard pattern for log processing pipelines.

---

## 49. How do you read multiple files and merge their content?

### Answer

```python
def merge_files(file_list, output_path):
    with open(output_path, "w") as outfile:
        for filename in file_list:
            with open(filename, "r") as infile:
                outfile.write(infile.read())

merge_files(["part1.txt", "part2.txt"], "merged.txt")
```

---

## 50. How do you safely write to a file atomically (avoiding partial writes on crash)?

### Answer

```python
import os

def atomic_write(filepath, content):
    temp_path = filepath + ".tmp"
    with open(temp_path, "w") as f:
        f.write(content)
    os.replace(temp_path, filepath)    # atomic on most OSes

atomic_write("config.json", '{"key": "value"}')
```

### Key Interview Points

* Writing to a temp file then renaming avoids leaving a half-written file if the process crashes mid-write.
* `os.replace()` is atomic on POSIX and Windows systems.

---

## 51. What is file locking and why is it needed?

### Answer

File locking prevents multiple processes from writing to the same file simultaneously, which could corrupt data.

Example using `fcntl` (Unix-only):

```python
import fcntl

with open("data.txt", "w") as f:
    fcntl.flock(f, fcntl.LOCK_EX)
    f.write("Locked write")
    fcntl.flock(f, fcntl.LOCK_UN)
```

### Key Interview Points

* `fcntl` is Unix-specific; Windows requires `msvcrt` or third-party libraries like `portalocker`.
* Important in multi-process applications writing to shared files.

---

## 52. How do you read a file's last modified time?

### Answer

```python
import os
import datetime

mtime = os.path.getmtime("data.txt")
print(datetime.datetime.fromtimestamp(mtime))
```

Using `pathlib`:

```python
from pathlib import Path

mtime = Path("data.txt").stat().st_mtime
```

---

## 53. How do you check file permissions in Python?

### Answer

```python
import os

print(os.access("data.txt", os.R_OK))    # readable?
print(os.access("data.txt", os.W_OK))    # writable?
print(os.access("data.txt", os.X_OK))    # executable?
```

Output:

```
True
True
False
```

---

## 54. How do you change file permissions in Python?

### Answer

```python
import os
import stat

os.chmod("script.sh", stat.S_IRWXU)    # read/write/execute for owner
```

### Key Interview Points

* `os.chmod()` mirrors the Unix `chmod` command.
* Permission bits behave differently across operating systems (especially Windows).

---

## 55. How do you read a binary file and process it byte by byte?

### Answer

```python
with open("image.png", "rb") as f:
    byte = f.read(1)
    while byte:
        process(byte)
        byte = f.read(1)
```

### Key Interview Points

* Reading byte by byte is slow — usually better to read in larger chunks for performance.

---

## 56. How do you read a binary file in fixed-size chunks?

### Answer

```python
def read_binary_chunks(filepath, chunk_size=4096):
    with open(filepath, "rb") as f:
        while True:
            chunk = f.read(chunk_size)
            if not chunk:
                break
            yield chunk

for chunk in read_binary_chunks("video.mp4"):
    process(chunk)
```

---

## 57. How do you calculate a file's hash (e.g., MD5 or SHA256)?

### Answer

```python
import hashlib

def file_hash(filepath, algorithm="sha256"):
    hasher = hashlib.new(algorithm)
    with open(filepath, "rb") as f:
        for chunk in iter(lambda: f.read(4096), b""):
            hasher.update(chunk)
    return hasher.hexdigest()

print(file_hash("data.txt"))
```

### Key Interview Points

* Reading in chunks avoids loading the entire file into memory for hashing.
* Useful for verifying file integrity (checksums).

---

## 58. How do you compress and decompress files using `gzip`?

### Answer

Compress:

```python
import gzip
import shutil

with open("data.txt", "rb") as f_in:
    with gzip.open("data.txt.gz", "wb") as f_out:
        shutil.copyfileobj(f_in, f_out)
```

Decompress:

```python
with gzip.open("data.txt.gz", "rb") as f_in:
    with open("data_decompressed.txt", "wb") as f_out:
        shutil.copyfileobj(f_in, f_out)
```

---

## 59. How do you work with ZIP files in Python?

### Answer

```python
import zipfile

# Create a zip file
with zipfile.ZipFile("archive.zip", "w") as zf:
    zf.write("data.txt")

# Extract a zip file
with zipfile.ZipFile("archive.zip", "r") as zf:
    zf.extractall("extracted_folder")

# List contents
with zipfile.ZipFile("archive.zip", "r") as zf:
    print(zf.namelist())
```

Output:

```
['data.txt']
```

---

## 60. How do you read a file's content into memory and process it as a stream using `io.StringIO`?

### Answer

```python
from io import StringIO

data = "line1\nline2\nline3"
stream = StringIO(data)

for line in stream:
    print(line.strip())
```

Output:

```
line1
line2
line3
```

### Key Interview Points

* `StringIO` mimics a file object but operates entirely in memory.
* Useful for testing functions that expect file-like objects without touching the disk.

---

## 61. What is `io.BytesIO` and when is it used?

### Answer

```python
from io import BytesIO

data = b"binary content"
stream = BytesIO(data)

print(stream.read())
```

Output:

```
b'binary content'
```

### Key Interview Points

* In-memory binary stream — useful for testing functions that expect file-like binary objects.
* Commonly used when working with image processing or network data without touching disk.

---

## 62. What is the difference between `io.StringIO`/`io.BytesIO` and actual file objects?

### Answer

| Feature | StringIO/BytesIO | File object |
|---|---|---|
| Storage | In-memory | On disk |
| Speed | Faster | Slower (disk I/O) |
| Persistence | Lost when program ends | Persists |
| Use case | Testing, intermediate processing | Permanent storage |

---

## 63. How do you read user input and write it to a file?

### Answer

```python
name = input("Enter your name: ")

with open("names.txt", "a") as f:
    f.write(name + "\n")
```

### Key Interview Points

* Use `"a"` mode to keep adding entries without overwriting previous ones.

---

## 64. How do you process a configuration file using `configparser`?

### Answer

Sample `config.ini`:

```ini
[database]
host = localhost
port = 5432
```

Reading:

```python
import configparser

config = configparser.ConfigParser()
config.read("config.ini")

print(config["database"]["host"])
print(config.getint("database", "port"))
```

Output:

```
localhost
5432
```

---

## 65. How do you read environment-specific configuration using `.env` files?

### Answer

```python
# .env file content:
# API_KEY=secret123

import os
from pathlib import Path

def load_env(filepath=".env"):
    if Path(filepath).exists():
        with open(filepath) as f:
            for line in f:
                line = line.strip()
                if line and not line.startswith("#"):
                    key, _, value = line.partition("=")
                    os.environ[key] = value

load_env()
print(os.environ.get("API_KEY"))
```

### Key Interview Points

* Production systems typically use the `python-dotenv` library instead of writing this manually.

---

## 66. What is the time complexity of `read()` vs reading line by line?

### Answer

```
read()             — O(n), loads entire file into memory at once
line by line        — O(n) total, but O(1) memory per iteration
```

### Key Interview Points

* Both have the same overall time complexity, but very different memory footprints.
* Line-by-line iteration is preferred for large files.

---

## 67. What is the time complexity of `seek()`?

### Answer

```
O(1)
```

Seeking to a position is constant time — the OS directly repositions the file pointer without scanning.

### Key Interview Points

* This is true for files opened in binary mode with random access; text mode with multi-byte encodings can have subtle complications with non-byte-aligned seeks.

---

## 68. What is the space complexity of `readlines()` vs iterating over the file object?

### Answer

```python
# O(n) space — entire file loaded as a list of strings
lines = open("data.txt").readlines()

# O(1) space per iteration — file streamed line by line
for line in open("data.txt"):
    process(line)
```

### Key Interview Points

* For very large files, prefer direct iteration over `readlines()`.

---

## 69. How do you handle a file that may have inconsistent encoding?

### Answer

```python
def safe_read(filepath):
    encodings = ["utf-8", "latin-1", "cp1252"]
    for enc in encodings:
        try:
            with open(filepath, "r", encoding=enc) as f:
                return f.read()
        except UnicodeDecodeError:
            continue
    raise ValueError("Could not decode file with known encodings")
```

### Key Interview Points

* `errors="replace"` or `errors="ignore"` parameters can also handle decode issues gracefully.

```python
with open(filepath, "r", encoding="utf-8", errors="replace") as f:
    content = f.read()
```

---

## 70. What is the difference between `errors="strict"`, `"ignore"`, and `"replace"` when opening files?

### Answer

```python
# strict (default) — raises UnicodeDecodeError on invalid bytes
open("file.txt", encoding="utf-8", errors="strict")

# ignore — silently drops invalid bytes
open("file.txt", encoding="utf-8", errors="ignore")

# replace — substitutes invalid bytes with a placeholder character
open("file.txt", encoding="utf-8", errors="replace")
```

---

## 71. Implement a function that counts word frequency across multiple text files.

### Answer

```python
from collections import Counter
import re

def word_frequency(file_paths):
    counter = Counter()
    for path in file_paths:
        with open(path, "r") as f:
            words = re.findall(r"\w+", f.read().lower())
            counter.update(words)
    return counter

print(word_frequency(["doc1.txt", "doc2.txt"]).most_common(3))
```

---

## 72. Implement a log file rotator (keep only the last N lines).

### Answer

```python
def rotate_log(filepath, max_lines=1000):
    with open(filepath, "r") as f:
        lines = f.readlines()

    if len(lines) > max_lines:
        lines = lines[-max_lines:]
        with open(filepath, "w") as f:
            f.writelines(lines)

rotate_log("app.log", max_lines=500)
```

---

## 73. Implement a function that reads a CSV and returns the average of a numeric column.

### Answer

```python
import csv

def average_column(filepath, column_name):
    total, count = 0, 0
    with open(filepath, "r") as f:
        reader = csv.DictReader(f)
        for row in reader:
            total += float(row[column_name])
            count += 1
    return total / count if count else 0

print(average_column("sales.csv", "amount"))
```

---

## 74. Implement a function that merges multiple CSV files with the same headers.

### Answer

```python
import csv

def merge_csv(file_list, output_path):
    with open(output_path, "w", newline="") as outfile:
        writer = None
        for path in file_list:
            with open(path, "r") as infile:
                reader = csv.reader(infile)
                header = next(reader)
                if writer is None:
                    writer = csv.writer(outfile)
                    writer.writerow(header)
                for row in reader:
                    writer.writerow(row)

merge_csv(["jan.csv", "feb.csv"], "combined.csv")
```

---

## 75. Implement a watch-style function that detects when a file changes (polling-based).

### Answer

```python
import time
import os

def watch_file(filepath, interval=1):
    last_mtime = os.path.getmtime(filepath)
    while True:
        time.sleep(interval)
        current_mtime = os.path.getmtime(filepath)
        if current_mtime != last_mtime:
            print(f"{filepath} changed!")
            last_mtime = current_mtime
```

### Key Interview Points

* Polling is simple but inefficient for large-scale monitoring.
* Real systems use OS-level APIs (`inotify` on Linux, `watchdog` library) for event-driven file watching.

---

## 76. Implement a function to safely append JSON records to a JSON Lines (.jsonl) file.

### Answer

```python
import json

def append_jsonl(filepath, record):
    with open(filepath, "a") as f:
        f.write(json.dumps(record) + "\n")

def read_jsonl(filepath):
    records = []
    with open(filepath, "r") as f:
        for line in f:
            records.append(json.loads(line))
    return records

append_jsonl("events.jsonl", {"event": "login", "user": "alice"})
print(read_jsonl("events.jsonl"))
```

Output:

```
[{'event': 'login', 'user': 'alice'}]
```

### Key Interview Points

* JSON Lines format allows streaming reads/writes — each line is independently valid JSON.
* Common in logging and big-data pipelines.

---

## 77. Implement a function to deduplicate lines in a large file without loading it entirely into memory.

### Answer

```python
def deduplicate_large_file(input_path, output_path):
    seen = set()
    with open(input_path, "r") as infile, open(output_path, "w") as outfile:
        for line in infile:
            if line not in seen:
                seen.add(line)
                outfile.write(line)

deduplicate_large_file("input.txt", "deduped.txt")
```

### Key Interview Points

* `seen` set still grows with the number of unique lines — for truly massive files, use external sorting or a probabilistic structure like a Bloom filter.

---

## 78. Implement a function that splits a large file into smaller chunks of N lines each.

### Answer

```python
def split_file(filepath, lines_per_chunk=1000):
    with open(filepath, "r") as f:
        chunk = []
        chunk_num = 0
        for line in f:
            chunk.append(line)
            if len(chunk) == lines_per_chunk:
                write_chunk(chunk, chunk_num)
                chunk = []
                chunk_num += 1
        if chunk:
            write_chunk(chunk, chunk_num)

def write_chunk(lines, num):
    with open(f"chunk_{num}.txt", "w") as f:
        f.writelines(lines)
```

---

## 79. Implement a function that reads a file and yields it in reverse line order without loading the whole file at once.

### Answer

```python
def reverse_readline(filepath, buf_size=8192):
    with open(filepath, "rb") as f:
        f.seek(0, os.SEEK_END)
        position = f.tell()
        remainder = b""

        while position > 0:
            read_size = min(buf_size, position)
            position -= read_size
            f.seek(position)
            buffer = f.read(read_size) + remainder
            lines = buffer.split(b"\n")
            remainder = lines[0]
            for line in reversed(lines[1:]):
                yield line.decode()

        if remainder:
            yield remainder.decode()

import os
for line in reverse_readline("large_log.txt"):
    print(line)
```

### Key Interview Points

* Useful for "tail -r"-style operations on huge log files without loading them entirely.

---

## 80. Implement a simple CSV-to-JSON converter.

### Answer

```python
import csv
import json

def csv_to_json(csv_path, json_path):
    with open(csv_path, "r") as f:
        reader = csv.DictReader(f)
        data = list(reader)

    with open(json_path, "w") as f:
        json.dump(data, f, indent=2)

csv_to_json("data.csv", "data.json")
```

---

## 81. What are the most common file handling exceptions and what do they mean?

### Answer

| Exception | Cause |
|---|---|
| `FileNotFoundError` | File doesn't exist |
| `PermissionError` | Insufficient permissions |
| `IsADirectoryError` | Tried to open a directory as a file |
| `FileExistsError` | File already exists (with `'x'` mode) |
| `UnicodeDecodeError` | File encoding mismatch |

---

## 82. How do you ensure a file is always closed even if multiple exceptions could occur?

### Answer

```python
try:
    with open("data.txt", "r") as f:
        content = f.read()
        result = 10 / 0   # exception inside the block
except ZeroDivisionError:
    print("Math error, but file was still closed properly")

print(f.closed)
```

Output:

```
Math error, but file was still closed properly
True
```

### Key Interview Points

* `with` guarantees `__exit__` (which closes the file) runs regardless of what exception occurs inside the block.

---

## 83. What is the difference between opening a file in `'r+'` vs `'w+'` mode?

### Answer

`'r+'` — read and write, file must already exist, doesn't truncate.

```python
with open("data.txt", "r+") as f:
    content = f.read()
    f.write("appended at end of read position")
```

`'w+'` — read and write, truncates the file first.

```python
with open("data.txt", "w+") as f:
    f.write("fresh content")
    f.seek(0)
    print(f.read())
```

### Key Interview Points

* `'r+'` fails with `FileNotFoundError` if the file doesn't exist.
* `'w+'` always creates a fresh, empty file (destroying old content).

---

## 84. What is the difference between `open()` returning a file object vs using `os.open()`?

### Answer

`open()` — high-level, Pythonic, returns a buffered file object.

```python
f = open("data.txt", "r")
```

`os.open()` — low-level, returns a raw file descriptor (an integer).

```python
import os

fd = os.open("data.txt", os.O_RDONLY)
content = os.read(fd, 100)
os.close(fd)
```

### Key Interview Points

* `open()` is preferred for almost all use cases.
* `os.open()` is used for advanced/low-level scenarios requiring OS-specific flags.

---

## 85. How do you make file writes durable (flush to disk immediately)?

### Answer

```python
with open("data.txt", "w") as f:
    f.write("critical data")
    f.flush()
    os.fsync(f.fileno())
```

### Key Interview Points

* `flush()` pushes data from Python's internal buffer to the OS.
* `os.fsync()` forces the OS to write the data to physical disk, bypassing OS-level caching.
* Important for databases and systems requiring guaranteed durability.

---

## 86. What is buffering and why does Python buffer file writes?

### Answer

Buffering batches small writes into larger chunks before sending them to the OS, improving performance by reducing the number of system calls.

```python
with open("data.txt", "w", buffering=8192) as f:
    f.write("data")
```

### Key Interview Points

* Without buffering, every `write()` call would trigger an expensive system call.
* Buffered data may not be visible to other processes until flushed or the file is closed.

---

## 87. How do you check if a file object is readable, writable, or seekable?

### Answer

```python
with open("data.txt", "r") as f:
    print(f.readable())
    print(f.writable())
    print(f.seekable())
```

Output:

```
True
False
True
```

---

## 88. What is the difference between `file.close()` being called explicitly vs implicitly via garbage collection?

### Answer

```python
f = open("data.txt", "w")
f.write("data")
del f    # may trigger __del__ eventually, but timing is not guaranteed
```

### Key Interview Points

* Relying on garbage collection to close files is unreliable, especially in PyPy or other non-CPython implementations.
* Always close explicitly or use `with` for deterministic cleanup.

---

## 89. What is the difference between a file path being relative vs absolute?

### Answer

```python
import os

relative = "data.txt"
absolute = os.path.abspath(relative)

print(relative)
print(absolute)
```

Output:

```
data.txt
/home/user/project/data.txt
```

### Key Interview Points

* Relative paths depend on the current working directory (`os.getcwd()`).
* Absolute paths always point to the same location regardless of where the script is run from.

---

## 90. What are the most commonly asked file handling coding problems in Python interviews?

### Answer

#### Reading/Writing
* Read large files line by line efficiently
* Read/write JSON and CSV files
* Count word frequency across files

#### Processing
* Filter and write matching lines to a new file
* Merge multiple files
* Deduplicate lines in a large file
* Split a large file into chunks

#### Advanced
* Implement reverse line reading (tail -r style)
* Implement atomic file writes
* Implement a simple log rotator
* Calculate file hash (checksum)

---

## 91. What is the difference between `csv.reader` and `pandas.read_csv` (high level)?

### Answer

```python
import csv

with open("data.csv") as f:
    reader = csv.reader(f)
    for row in reader:
        print(row)
```

```python
import pandas as pd

df = pd.read_csv("data.csv")
print(df.head())
```

### Key Interview Points

* `csv` module is built-in, lightweight, returns plain lists/dicts.
* `pandas` provides powerful DataFrame operations but adds an external dependency and more overhead for simple tasks.

---

## 92. How do you handle very large CSV files without loading them entirely into memory?

### Answer

```python
import csv

def process_large_csv(filepath):
    with open(filepath, "r") as f:
        reader = csv.reader(f)
        next(reader)    # skip header
        for row in reader:
            process(row)
```

### Key Interview Points

* `csv.reader` is inherently a generator-like iterator — it doesn't load the whole file at once.
* For pandas, use `chunksize` parameter in `read_csv()` to process in batches.

---

## 93. What is the difference between opening a file with `'rb'` vs `'r'` when the content includes non-ASCII characters?

### Answer

```python
# Text mode — decodes using the specified/default encoding
with open("data.txt", "r", encoding="utf-8") as f:
    content = f.read()    # returns str

# Binary mode — no decoding happens
with open("data.txt", "rb") as f:
    content = f.read()    # returns bytes
```

### Key Interview Points

* Binary mode is encoding-agnostic — you decode manually if/when needed.
* Mixing the two modes in the same workflow can cause subtle bugs (e.g., comparing `str` to `bytes`).

---

## 94. How would you design a system to safely process thousands of files in parallel?

### Answer

```python
from concurrent.futures import ProcessPoolExecutor

def process_file(filepath):
    with open(filepath, "r") as f:
        return len(f.readlines())

def process_all(file_list):
    with ProcessPoolExecutor() as executor:
        results = list(executor.map(process_file, file_list))
    return results
```

### Key Interview Points

* Use `ProcessPoolExecutor` for CPU-bound file processing.
* Use `ThreadPoolExecutor` for I/O-bound tasks (since I/O releases the GIL).
* Be mindful of file descriptor limits when processing thousands of files concurrently.

---

## 95. What is the difference between synchronous and asynchronous file I/O in Python?

### Answer

Synchronous (blocking):

```python
with open("data.txt", "r") as f:
    content = f.read()
```

Asynchronous (using `aiofiles`):

```python
import aiofiles
import asyncio

async def read_file(filepath):
    async with aiofiles.open(filepath, "r") as f:
        return await f.read()

asyncio.run(read_file("data.txt"))
```

### Key Interview Points

* Python's built-in `open()` is always blocking/synchronous.
* True async file I/O requires third-party libraries like `aiofiles`, since most OS file APIs aren't natively async.

---

## 96. How do you safely handle file paths across different operating systems?

### Answer

```python
from pathlib import Path

path = Path("folder") / "subfolder" / "file.txt"
print(path)
```

Output on Windows:

```
folder\subfolder\file.txt
```

Output on Linux/Mac:

```
folder/subfolder/file.txt
```

### Key Interview Points

* `pathlib` automatically uses the correct path separator for the current OS.
* Avoid hardcoding `/` or `\` directly in path strings.

---

## 97. What is the difference between symbolic links and regular files, and how do you detect them?

### Answer

```python
import os

print(os.path.islink("shortcut.txt"))
```

Using `pathlib`:

```python
from pathlib import Path

print(Path("shortcut.txt").is_symlink())
```

### Key Interview Points

* Symbolic links point to another file/directory rather than containing data directly.
* `os.path.realpath()` resolves a symlink to its final target.

---

## 98. How do you create a symbolic link in Python?

### Answer

```python
import os

os.symlink("original.txt", "link.txt")
```

Using `pathlib`:

```python
from pathlib import Path

Path("link.txt").symlink_to("original.txt")
```

### Key Interview Points

* Creating symlinks on Windows may require administrator privileges.

---

## 99. What is the difference between `shutil.copy()`, `shutil.copy2()`, and `shutil.copyfile()`?

### Answer

```python
import shutil

shutil.copy("a.txt", "b.txt")        # content + permission bits
shutil.copy2("a.txt", "b.txt")       # content + permission bits + metadata (timestamps)
shutil.copyfile("a.txt", "b.txt")    # content only, no metadata
```

### Key Interview Points

* `copy2()` is the closest to a full "preserve everything" copy.
* `copyfile()` is the most minimal/fastest option.

---

## 100. What are the most commonly asked file handling questions in Python interviews?

### Answer

#### Fundamentals
* File modes (`r`, `w`, `a`, `x`, `b`, `+`)
* Why `with` is preferred over manual `open()`/`close()`
* Text mode vs binary mode

#### Reading/Writing
* `read()` vs `readline()` vs `readlines()`
* Reading large files efficiently (line by line, in chunks)
* Writing JSON and CSV files

#### Path Handling
* `os.path` vs `pathlib`
* Absolute vs relative paths
* Checking file existence, type, and permissions

#### Advanced
* Atomic writes
* File locking
* Buffering and flushing
* Encoding/decoding issues and `errors` parameter
* Async file I/O with `aiofiles`

#### Coding Problems
* Word frequency counter across files
* Log rotator
* CSV/JSON converters
* Deduplicate lines in large files
* Reverse line reading

### Final Interview Tip

If you master:

* All file modes and when to use each
* `with` statement and why it matters for resource management
* Efficient reading strategies for large files
* `pathlib` for path handling
* JSON/CSV reading and writing
* Atomic writes and file locking concepts

you will be able to answer **95%+ of Python file handling interview questions** asked in software engineering, data engineering, and backend development interviews.