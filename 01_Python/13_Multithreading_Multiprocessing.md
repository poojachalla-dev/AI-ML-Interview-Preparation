## 1. What is Multithreading in Python?

### Answer

Multithreading is a technique where multiple threads execute within a single process.

### Example

```python
import threading

def task():
    print("Thread Running")

t = threading.Thread(target=task)

t.start()
t.join()
```

### Key Interview Point

Threads share the same memory space.

---

## 2. What is a Thread?

### Answer

A thread is the smallest unit of execution within a process.

### Example

```text
Process
├── Thread 1
├── Thread 2
└── Thread 3
```

---

## 3. What is a Process?

### Answer

A process is an independent program execution instance with its own memory space.

### Example

```text
Chrome
VS Code
Python Script
```

Each runs as a separate process.

---

## 4. What is Multiprocessing?

### Answer

Multiprocessing allows multiple processes to execute simultaneously.

### Example

```python
from multiprocessing import Process

def task():
    print("Process Running")

p = Process(target=task)

p.start()
p.join()
```

---

## 5. Why do we use Multithreading?

### Answer

Benefits:

* Concurrent execution
* Better responsiveness
* I/O optimization
* Background tasks

---

## 6. Why do we use Multiprocessing?

### Answer

Benefits:

* True parallelism
* Better CPU utilization
* Faster CPU-bound execution

---

## 7. What is the difference between a Process and a Thread?

### Answer

| Process            | Thread               |
| ------------------ | -------------------- |
| Independent memory | Shared memory        |
| Heavyweight        | Lightweight          |
| Slower creation    | Faster creation      |
| Better isolation   | Easier communication |

---

## 8. What is concurrency?

### Answer

Concurrency means multiple tasks make progress during overlapping time periods.

### Example

```text
Task A
Task B
Task C
```

All progress together.

---

## 9. What is parallelism?

### Answer

Parallelism means tasks execute simultaneously on multiple CPU cores.

### Example

```text
CPU Core 1 → Task A
CPU Core 2 → Task B
```

---

## 10. Difference between concurrency and parallelism?

### Answer

| Concurrency              | Parallelism             |
| ------------------------ | ----------------------- |
| Overlapping execution    | Simultaneous execution  |
| Single or multiple cores | Multiple cores          |
| Task management          | Performance improvement |

---

## 11. What is the Global Interpreter Lock (GIL)?

### Answer

The GIL allows only one thread to execute Python bytecode at a time.

### Key Interview Point

Most frequently asked threading interview question.

---

## 12. Why does Python have a GIL?

### Answer

To simplify memory management and ensure thread safety for Python objects.

---

## 13. How does the GIL affect Multithreading?

### Answer

CPU-bound threads cannot run truly in parallel.

### Example

```text
Thread 1
Thread 2

Only one executes Python bytecode at a time.
```

---

## 14. Does the GIL affect Multiprocessing?

### Answer

No.

Each process gets its own Python interpreter and GIL.

---

## 15. What are CPU-bound tasks?

### Answer

Tasks dominated by CPU computations.

### Examples

* Matrix multiplication
* Model training
* Image processing
* Encryption

---

## 16. What are I/O-bound tasks?

### Answer

Tasks waiting for external resources.

### Examples

* File operations
* API calls
* Database queries
* Network communication

---

## 17. Which is better for CPU-bound tasks?

### Answer

Multiprocessing.

### Reason

Bypasses the GIL.

---

## 18. Which is better for I/O-bound tasks?

### Answer

Multithreading.

### Reason

Threads can wait while other threads execute.

---

## 19. What module provides threading support?

### Answer

```python
threading
```

### Example

```python
import threading
```

---

## 20. What module provides multiprocessing support?

### Answer

```python
multiprocessing
```

### Example

```python
import multiprocessing
```

---

## 21. What is a Thread object?

### Answer

Represents a separate thread of execution.

### Example

```python
t = threading.Thread(
    target=task
)
```

---

## 22. What does start() do?

### Answer

Starts a new thread or process.

### Example

```python
t.start()
```

---

## 23. What does join() do?

### Answer

Waits for a thread or process to finish.

### Example

```python
t.join()
```

---

## 24. What happens if join() is not called?

### Answer

Main program may terminate before child threads/processes finish.

---

## 25. What are the most common Multithreading interview questions?

### Answer

Frequently Asked:

* What is a Thread?
* What is a Process?
* What is GIL?
* Concurrency vs Parallelism?
* CPU-bound vs I/O-bound?
* Threading vs Multiprocessing?

---

## 26. What is the lifecycle of a thread?

### Answer

A thread typically goes through:

```text
New
↓
Runnable
↓
Running
↓
Blocked/Waiting
↓
Terminated
```

---

## 27. What is a Runnable thread?

### Answer

A thread that is ready to execute and waiting for CPU scheduling.

---

## 28. What is a Running thread?

### Answer

A thread currently executing instructions on the CPU.

---

## 29. What is a Blocked thread?

### Answer

A thread waiting for a resource or event.

### Examples

* File access
* Network response
* Lock acquisition

---

## 30. What is a Daemon Thread?

### Answer

A background thread that automatically terminates when the main program exits.

### Example

```python
import threading

def background():
    while True:
        pass

t = threading.Thread(
    target=background,
    daemon=True
)

t.start()
```

---

## 31. What is a Non-Daemon Thread?

### Answer

A regular thread that must complete before the program exits.

---

## 32. How do you check if a thread is alive?

### Example

```python
t.is_alive()
```

Returns:

```python
True
```

or

```python
False
```

---

## 33. What is current_thread()?

### Answer

Returns the currently executing thread.

### Example

```python
import threading

print(
    threading.current_thread().name
)
```

---

## 34. How can you name a thread?

### Example

```python
t = threading.Thread(
    target=task,
    name="Worker-1"
)
```

---

## 35. What is thread synchronization?

### Answer

Synchronization coordinates thread execution to avoid data corruption.

---

## 36. What is a Race Condition?

### Answer

Occurs when multiple threads modify shared data simultaneously.

### Example

```python
counter += 1
```

Multiple threads may produce incorrect results.

---

## 37. Why do race conditions occur?

### Answer

Because thread execution order is unpredictable.

---

## 38. What is shared memory?

### Answer

Memory accessible by multiple threads.

### Example

```python
counter = 0
```

All threads can access it.

---

## 39. How can race conditions be prevented?

### Answer

Using synchronization mechanisms such as:

* Locks
* Semaphores
* Events
* Queues

---

## 40. What is a Lock?

### Answer

A synchronization primitive that allows only one thread to access a resource at a time.

### Example

```python
lock = threading.Lock()
```

---

## 41. How do you acquire a Lock?

### Example

```python
lock.acquire()

try:
    critical_section()

finally:
    lock.release()
```

---

## 42. How do you use a Lock with a Context Manager?

### Example

```python
with lock:
    critical_section()
```

### Key Interview Point

Preferred approach.

---

## 43. What is a critical section?

### Answer

Code that accesses shared resources.

### Example

```python
counter += 1
```

---

## 44. What is a Deadlock?

### Answer

Occurs when two or more threads wait forever for resources held by each other.

### Example

```text
Thread A waits for Lock B
Thread B waits for Lock A
```

---

## 45. How can deadlocks be avoided?

### Answer

Best Practices:

* Acquire locks in a consistent order
* Use timeouts
* Minimize lock usage
* Avoid nested locks

---

## 46. What is RLock?

### Answer

A Reentrant Lock that allows the same thread to acquire the lock multiple times.

### Example

```python
lock = threading.RLock()
```

---

## 47. Why use RLock?

### Answer

Useful when recursive functions require locking.

---

## 48. What is a Semaphore?

### Answer

A synchronization primitive that allows a fixed number of threads to access a resource simultaneously.

### Example

```python
sem = threading.Semaphore(3)
```

Only three threads can enter.

---

## 49. How does a Semaphore differ from a Lock?

### Answer

| Lock             | Semaphore                |
| ---------------- | ------------------------ |
| 1 thread allowed | Multiple threads allowed |
| Binary state     | Counter based            |
| Simpler          | More flexible            |

---

## 50. What are the most important synchronization concepts for interviews?

### Answer

Frequently Asked:

* Race Condition
* Lock
* RLock
* Semaphore
* Deadlock
* Critical Section
* Synchronization

---

## 51. What is an Event in Python threading?

### Answer

An Event is a synchronization primitive used for communication between threads.

### Example

```python
import threading

event = threading.Event()
```

---

## 52. How does an Event work?

### Answer

One thread sets the event while other threads wait for it.

### Flow

```text
Thread A → wait()
Thread B → set()
Thread A continues
```

---

## 53. How do you wait for an Event?

### Example

```python
event.wait()
```

The thread blocks until the event is set.

---

## 54. How do you set an Event?

### Example

```python
event.set()
```

All waiting threads are awakened.

---

## 55. How do you clear an Event?

### Example

```python
event.clear()
```

The event returns to the unset state.

---

## 56. What is a Condition object?

### Answer

A Condition combines a Lock with signaling mechanisms.

### Example

```python
condition = threading.Condition()
```

---

## 57. Why use a Condition?

### Answer

Allows threads to wait until a specific condition becomes true.

---

## 58. How do you wait on a Condition?

### Example

```python
with condition:
    condition.wait()
```

---

## 59. How do you notify waiting threads?

### Example

```python
with condition:
    condition.notify()
```

---

## 60. What is notify_all()?

### Answer

Wakes up all threads waiting on the condition.

### Example

```python
condition.notify_all()
```

---

## 61. What is a Queue?

### Answer

A thread-safe data structure used for inter-thread communication.

### Example

```python
from queue import Queue

q = Queue()
```

---

## 62. Why are Queues thread-safe?

### Answer

Internal locking mechanisms prevent race conditions.

---

## 63. How do you add items to a Queue?

### Example

```python
q.put("task")
```

---

## 64. How do you retrieve items from a Queue?

### Example

```python
item = q.get()
```

---

## 65. What is the Producer-Consumer pattern?

### Answer

One thread produces data while another consumes it.

### Flow

```text
Producer
    ↓
 Queue
    ↓
Consumer
```

---

## 66. Example of Producer-Consumer using Queue.

### Example

```python
from queue import Queue

q = Queue()

q.put("job")
job = q.get()
```

---

## 67. What is a Thread Pool?

### Answer

A collection of reusable worker threads.

### Benefits

* Better performance
* Reduced overhead
* Easier task management

---

## 68. What module provides thread pools?

### Answer

```python
concurrent.futures
```

---

## 69. What is ThreadPoolExecutor?

### Answer

A high-level API for managing thread pools.

### Example

```python
from concurrent.futures import ThreadPoolExecutor
```

---

## 70. Example of ThreadPoolExecutor.

### Example

```python
from concurrent.futures import ThreadPoolExecutor

def task():
    return "Done"

with ThreadPoolExecutor(
    max_workers=4
) as executor:

    future = executor.submit(task)

    print(future.result())
```

---

## 71. What is a Future object?

### Answer

Represents a task whose result may not be available yet.

### Example

```python
future = executor.submit(task)
```

---

## 72. How do you get the result of a Future?

### Example

```python
future.result()
```

---

## 73. What is ProcessPoolExecutor?

### Answer

A high-level API for multiprocessing.

### Example

```python
from concurrent.futures import ProcessPoolExecutor
```

---

## 74. Why use ProcessPoolExecutor?

### Answer

Benefits:

* True parallelism
* Simpler multiprocessing code
* Better CPU utilization

---

## 75. Example of ProcessPoolExecutor.

### Example

```python
from concurrent.futures import ProcessPoolExecutor

def square(x):
    return x * x

with ProcessPoolExecutor() as executor:

    results = executor.map(
        square,
        [1,2,3,4]
    )

    print(list(results))
```

Output

```python
[1, 4, 9, 16]
```

---

## 76. What is Inter-Process Communication (IPC)?

### Answer

IPC allows processes to exchange data and coordinate execution.

### Examples

* Pipes
* Queues
* Shared Memory
* Sockets

---

## 77. Why is IPC needed?

### Answer

Processes have separate memory spaces.

Unlike threads, they cannot directly access each other's variables.

---

## 78. What is a multiprocessing Queue?

### Answer

A Queue used for communication between processes.

### Example

```python
from multiprocessing import Queue

q = Queue()

q.put("Hello")

print(q.get())
```

---

## 79. Why use multiprocessing.Queue?

### Answer

Benefits:

* Process-safe
* Easy communication
* Built-in synchronization

---

## 80. What is a Pipe in multiprocessing?

### Answer

A Pipe provides two-way communication between processes.

### Example

```python
from multiprocessing import Pipe

parent_conn, child_conn = Pipe()
```

---

## 81. How do Pipes work?

### Example

```python
parent_conn.send("Hello")

print(
    child_conn.recv()
)
```

---

## 82. Queue vs Pipe?

### Answer

| Queue                        | Pipe                            |
| ---------------------------- | ------------------------------- |
| Multiple producers/consumers | Usually two endpoints           |
| Easier to use                | Faster for simple communication |
| Thread-safe                  | Direct connection               |

---

## 83. What is Shared Memory?

### Answer

Memory accessible by multiple processes.

### Example

```python
from multiprocessing import Value
```

---

## 84. What is multiprocessing.Value?

### Answer

Allows a single shared value between processes.

### Example

```python
from multiprocessing import Value

counter = Value('i', 0)
```

---

## 85. What is multiprocessing.Array?

### Answer

Allows sharing arrays between processes.

### Example

```python
from multiprocessing import Array

arr = Array('i', [1,2,3])
```

---

## 86. What is a Manager in multiprocessing?

### Answer

A Manager creates shared objects between processes.

### Example

```python
from multiprocessing import Manager

manager = Manager()
```

---

## 87. What objects can Manager create?

### Answer

Examples:

* List
* Dict
* Queue
* Namespace

### Example

```python
shared_list = manager.list()
```

---

## 88. What is process synchronization?

### Answer

Coordinating multiple processes to avoid conflicts.

---

## 89. What synchronization primitives exist in multiprocessing?

### Answer

Common tools:

* Lock
* RLock
* Semaphore
* Event
* Condition

---

## 90. What is multiprocessing.Lock?

### Example

```python
from multiprocessing import Lock

lock = Lock()
```

Used to protect shared resources.

---

## 91. What is a Pool in multiprocessing?

### Answer

A Pool manages a group of worker processes.

### Example

```python
from multiprocessing import Pool
```

---

## 92. Why use a Pool?

### Answer

Benefits:

* Process reuse
* Reduced overhead
* Better scalability

---

## 93. Example of Pool.map().

### Example

```python
from multiprocessing import Pool

def square(x):
    return x*x

with Pool() as pool:

    result = pool.map(
        square,
        [1,2,3,4]
    )

print(result)
```

Output

```python
[1, 4, 9, 16]
```

---

## 94. What is Pool.apply()?

### Answer

Executes a single function call.

### Example

```python
result = pool.apply(
    square,
    (5,)
)
```

---

## 95. Difference between map() and apply()?

### Answer

| map()               | apply()               |
| ------------------- | --------------------- |
| Multiple inputs     | Single input          |
| Parallel processing | One execution         |
| Returns list        | Returns single result |

---

## 96. What are real-world Multithreading use cases?

### Answer

Examples:

* Web scraping
* API calls
* Chat applications
* Background jobs
* File downloads

---

## 97. What are real-world Multiprocessing use cases?

### Answer

Examples:

* Machine Learning training
* Image processing
* Video rendering
* Scientific computing
* Data analytics

---

## 98. What are common interview mistakes in Threading and Multiprocessing?

### Answer

Mistakes:

* Ignoring the GIL
* Using threads for CPU-bound tasks
* Not using locks
* Creating race conditions
* Excessive process creation

---

## 99. What concepts are most important for interviews?

### Answer

Core Topics:

### Threading

* Thread
* Lock
* Semaphore
* Event
* Queue
* ThreadPoolExecutor

### Multiprocessing

* Process
* Pool
* Queue
* Pipe
* Shared Memory
* Manager

---

## 100. What Multithreading & Multiprocessing knowledge is required for Python interviews?

### Answer

### Fundamentals

* Thread vs Process
* Concurrency vs Parallelism
* GIL
* CPU-bound vs I/O-bound

### Intermediate

* Locks
* Race Conditions
* Deadlocks
* Semaphores
* Events
* Queues

### Advanced

* ThreadPoolExecutor
* ProcessPoolExecutor
* IPC
* Pipes
* Shared Memory
* Managers

### Production Concepts

* Web Scraping
* API Processing
* Data Pipelines
* Machine Learning
* Distributed Systems

### Final Interview Tip

If you understand:

* GIL
* Thread vs Process
* Lock
* Semaphore
* Queue
* ThreadPoolExecutor
* ProcessPoolExecutor
* IPC

you can confidently answer **95%+ of Multithreading & Multiprocessing interview questions** asked in Python, Backend, Data Engineering, Machine Learning, and AI Engineering interviews.

