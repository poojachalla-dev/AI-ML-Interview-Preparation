## 1. Reverse a String

### Problem

Reverse a given string.

### Solution

```python
def reverse_string(s):
    return s[::-1]

print(reverse_string("python"))
```

### Output

```python
nohtyp
```

### Time Complexity

```text
O(n)
```

---

## 2. Check Palindrome

### Problem

Check whether a string is a palindrome.

### Solution

```python
def is_palindrome(s):
    return s == s[::-1]

print(is_palindrome("madam"))
```

### Output

```python
True
```

---

## 3. Find Largest Number in a List

### Solution

```python
nums = [10, 25, 8, 50, 12]

print(max(nums))
```

### Output

```python
50
```

---

## 4. Find Smallest Number in a List

### Solution

```python
nums = [10, 25, 8, 50, 12]

print(min(nums))
```

### Output

```python
8
```

---

## 5. Find Sum of List Elements

### Solution

```python
nums = [1, 2, 3, 4, 5]

print(sum(nums))
```

### Output

```python
15
```

---

## 6. Count Vowels in a String

### Solution

```python
def count_vowels(text):

    vowels = "aeiouAEIOU"

    count = 0

    for ch in text:

        if ch in vowels:
            count += 1

    return count

print(count_vowels("Python"))
```

### Output

```python
1
```

---

## 7. Find Factorial

### Solution

```python
def factorial(n):

    if n == 0:
        return 1

    return n * factorial(n - 1)

print(factorial(5))
```

### Output

```python
120
```

---

## 8. Check Prime Number

### Solution

```python
def is_prime(n):

    if n < 2:
        return False

    for i in range(2, int(n**0.5)+1):

        if n % i == 0:
            return False

    return True

print(is_prime(17))
```

### Output

```python
True
```

---

## 9. Generate Fibonacci Series

### Solution

```python
a, b = 0, 1

for _ in range(10):

    print(a, end=" ")

    a, b = b, a+b
```

### Output

```python
0 1 1 2 3 5 8 13 21 34
```

---

## 10. Swap Two Numbers

### Solution

```python
a = 10
b = 20

a, b = b, a

print(a, b)
```

### Output

```python
20 10
```

---

## 11. Remove Duplicates from List

### Solution

```python
nums = [1,2,2,3,4,4,5]

result = list(set(nums))

print(result)
```

---

## 12. Count Character Frequency

### Solution

```python
from collections import Counter

text = "banana"

print(Counter(text))
```

### Output

```python
{'b':1,'a':3,'n':2}
```

---

## 13. Find Second Largest Number

### Solution

```python
nums = [10,20,30,40]

nums.sort()

print(nums[-2])
```

### Output

```python
30
```

---

## 14. Check Anagram

### Solution

```python
def is_anagram(a, b):

    return sorted(a) == sorted(b)

print(
    is_anagram(
        "listen",
        "silent"
    )
)
```

### Output

```python
True
```

---

## 15. Find Common Elements Between Lists

### Solution

```python
a = [1,2,3,4]
b = [3,4,5,6]

print(
    list(set(a) & set(b))
)
```

### Output

```python
[3,4]
```

---

## 16. Merge Two Dictionaries

### Solution

```python
d1 = {"a":1}
d2 = {"b":2}

result = {
    **d1,
    **d2
}

print(result)
```

---

## 17. Sort Dictionary by Value

### Solution

```python
d = {
    "a":3,
    "b":1,
    "c":2
}

result = dict(
    sorted(
        d.items(),
        key=lambda x:x[1]
    )
)

print(result)
```

---

## 18. Find Missing Number

### Solution

```python
nums = [1,2,3,5]

n = 5

missing = (
    n*(n+1)//2
) - sum(nums)

print(missing)
```

### Output

```python
4
```

---

## 19. Check Armstrong Number

### Solution

```python
num = 153

s = str(num)

result = sum(
    int(x)**3
    for x in s
)

print(result == num)
```

### Output

```python
True
```

---

## 20. Count Words in Sentence

### Solution

```python
sentence = "I love Python"

print(
    len(sentence.split())
)
```

### Output

```python
3
```

---

## 21. Find Maximum Occurring Character

### Solution

```python
from collections import Counter

text = "banana"

print(
    Counter(text).most_common(1)
)
```

---

## 22. Reverse Words in Sentence

### Solution

```python
text = "I love Python"

print(
    " ".join(
        text.split()[::-1]
    )
)
```

### Output

```python
Python love I
```

---

## 23. Flatten Nested List

### Solution

```python
nested = [
    [1,2],
    [3,4],
    [5]
]

flat = [
    item
    for sub in nested
    for item in sub
]

print(flat)
```

---

## 24. Find Intersection of Lists

### Solution

```python
a = [1,2,3]
b = [2,3,4]

print(
    list(
        set(a).intersection(b)
    )
)
```

---

## 25. Find Unique Elements

### Solution

```python
nums = [1,1,2,2,3,4]

unique = [
    x
    for x in nums
    if nums.count(x) == 1
]

print(unique)
```

### Output

```python
[3,4]
```

---

## 26. Two Sum

### Problem

Find two numbers whose sum equals the target.

### Solution

```python
def two_sum(nums, target):

    seen = {}

    for i, num in enumerate(nums):

        diff = target - num

        if diff in seen:
            return [seen[diff], i]

        seen[num] = i

print(
    two_sum(
        [2,7,11,15],
        9
    )
)
```

### Output

```python
[0, 1]
```

### Time Complexity

```text
O(n)
```

---

## 27. Move All Zeros to End

### Solution

```python
nums = [0,1,0,3,12]

result = [x for x in nums if x != 0]

result += [0] * nums.count(0)

print(result)
```

### Output

```python
[1,3,12,0,0]
```

---

## 28. Binary Search

### Solution

```python
def binary_search(arr, target):

    left = 0
    right = len(arr)-1

    while left <= right:

        mid = (left+right)//2

        if arr[mid] == target:
            return mid

        elif arr[mid] < target:
            left = mid + 1

        else:
            right = mid - 1

    return -1

print(
    binary_search(
        [1,2,3,4,5],
        4
    )
)
```

---

## 29. Merge Two Sorted Arrays

### Solution

```python
a = [1,3,5]
b = [2,4,6]

print(
    sorted(a+b)
)
```

### Output

```python
[1,2,3,4,5,6]
```

---

## 30. Find Duplicate Number

### Solution

```python
nums = [1,2,3,4,2]

seen = set()

for n in nums:

    if n in seen:
        print(n)
        break

    seen.add(n)
```

### Output

```python
2
```

---

## 31. Maximum Subarray Sum (Kadane's Algorithm)

### Solution

```python
nums = [-2,1,-3,4,-1,2,1,-5,4]

current = maximum = nums[0]

for num in nums[1:]:

    current = max(
        num,
        current + num
    )

    maximum = max(
        maximum,
        current
    )

print(maximum)
```

### Output

```python
6
```

---

## 32. Find First Non-Repeating Character

### Solution

```python
from collections import Counter

s = "aabbcdde"

count = Counter(s)

for ch in s:

    if count[ch] == 1:

        print(ch)
        break
```

### Output

```python
c
```

---

## 33. Check Balanced Parentheses

### Solution

```python
def balanced(s):

    stack = []

    for ch in s:

        if ch == "(":
            stack.append(ch)

        else:

            if not stack:
                return False

            stack.pop()

    return len(stack) == 0

print(
    balanced("(())")
)
```

### Output

```python
True
```

---

## 34. Reverse Integer

### Solution

```python
num = 12345

print(
    int(
        str(num)[::-1]
    )
)
```

### Output

```python
54321
```

---

## 35. Find Majority Element

### Solution

```python
nums = [2,2,1,1,1,2,2]

count = 0

candidate = None

for num in nums:

    if count == 0:
        candidate = num

    count += (
        1
        if num == candidate
        else -1
    )

print(candidate)
```

### Output

```python
2
```

---

## 36. Rotate Array by K Positions

### Solution

```python
nums = [1,2,3,4,5]

k = 2

nums = nums[-k:] + nums[:-k]

print(nums)
```

### Output

```python
[4,5,1,2,3]
```

---

## 37. Check if List is Sorted

### Solution

```python
nums = [1,2,3,4,5]

print(
    nums == sorted(nums)
)
```

### Output

```python
True
```

---

## 38. Find Pair with Given Sum

### Solution

```python
nums = [1,2,3,4,5]

target = 7

seen = set()

for num in nums:

    if target-num in seen:

        print(
            num,
            target-num
        )

    seen.add(num)
```

### Output

```python
4 3
```

---

## 39. Longest Word in Sentence

### Solution

```python
sentence = "I love Python programming"

print(
    max(
        sentence.split(),
        key=len
    )
)
```

### Output

```python
programming
```

---

## 40. Remove Duplicate Characters

### Solution

```python
s = "programming"

result = ""

for ch in s:

    if ch not in result:

        result += ch

print(result)
```

### Output

```python
progamin
```

---

## 41. Merge Intervals

### Solution

```python
intervals = [
    [1,3],
    [2,6],
    [8,10]
]

intervals.sort()

merged = [
    intervals[0]
]

for start, end in intervals[1:]:

    if start <= merged[-1][1]:

        merged[-1][1] = max(
            merged[-1][1],
            end
        )

    else:

        merged.append(
            [start,end]
        )

print(merged)
```

---

## 42. Longest Common Prefix

### Solution

```python
strs = [
    "flower",
    "flow",
    "flight"
]

prefix = strs[0]

for word in strs[1:]:

    while not word.startswith(prefix):

        prefix = prefix[:-1]

print(prefix)
```

### Output

```python
fl
```

---

## 43. Find Missing Positive Integer

### Solution

```python
nums = [3,4,-1,1]

positive = set(nums)

i = 1

while i in positive:

    i += 1

print(i)
```

### Output

```python
2
```

---

## 44. Product of Array Except Self

### Solution

```python
nums = [1,2,3,4]

result = []

for i in range(len(nums)):

    prod = 1

    for j in range(len(nums)):

        if i != j:

            prod *= nums[j]

    result.append(prod)

print(result)
```

### Output

```python
[24,12,8,6]
```

---

## 45. Valid Anagram

### Solution

```python
print(
    sorted("listen")
    ==
    sorted("silent")
)
```

### Output

```python
True
```

---

## 46. Group Anagrams

### Solution

```python
from collections import defaultdict

words = [
    "eat",
    "tea",
    "ate",
    "bat"
]

groups = defaultdict(list)

for word in words:

    groups[
        "".join(
            sorted(word)
        )
    ].append(word)

print(
    list(groups.values())
)
```

---

## 47. Longest Consecutive Sequence

### Solution

```python
nums = [100,4,200,1,3,2]

nums_set = set(nums)

longest = 0

for num in nums_set:

    if num-1 not in nums_set:

        length = 1

        while num+length in nums_set:

            length += 1

        longest = max(
            longest,
            length
        )

print(longest)
```

### Output

```python
4
```

---

## 48. Find Intersection of Two Arrays

### Solution

```python
a = [1,2,2,1]

b = [2,2]

print(
    list(
        set(a) & set(b)
    )
)
```

### Output

```python
[2]
```

---

## 49. Top K Frequent Elements

### Solution

```python
from collections import Counter

nums = [1,1,1,2,2,3]

print(
    [
        x[0]
        for x in
        Counter(nums).most_common(2)
    ]
)
```

### Output

```python
[1,2]
```

---

## 50. Longest Substring Without Repeating Characters

### Solution

```python
s = "abcabcbb"

seen = {}

left = 0

longest = 0

for right in range(len(s)):

    if (
        s[right] in seen
        and
        seen[s[right]] >= left
    ):

        left = seen[s[right]] + 1

    seen[s[right]] = right

    longest = max(
        longest,
        right-left+1
    )

print(longest)
```

### Output

```python
3
```

---

## 51. Reverse a Linked List

### Problem

Reverse a singly linked list.

### Solution

```python
class Node:

    def __init__(self, data):

        self.data = data
        self.next = None

def reverse(head):

    prev = None

    curr = head

    while curr:

        nxt = curr.next

        curr.next = prev

        prev = curr

        curr = nxt

    return prev
```

### Time Complexity

```text
O(n)
```

---

## 52. Detect Cycle in Linked List

### Solution

```python
def has_cycle(head):

    slow = fast = head

    while fast and fast.next:

        slow = slow.next

        fast = fast.next.next

        if slow == fast:

            return True

    return False
```

---

## 53. Find Middle of Linked List

### Solution

```python
def middle(head):

    slow = fast = head

    while fast and fast.next:

        slow = slow.next

        fast = fast.next.next

    return slow.data
```

---

## 54. Merge Two Sorted Linked Lists

### Solution

```python
def merge(l1, l2):

    dummy = Node(0)

    tail = dummy

    while l1 and l2:

        if l1.data < l2.data:

            tail.next = l1

            l1 = l1.next

        else:

            tail.next = l2

            l2 = l2.next

        tail = tail.next

    tail.next = l1 or l2

    return dummy.next
```

---

## 55. Remove Nth Node From End

### Solution

```python
def remove_nth(head, n):

    dummy = Node(0)

    dummy.next = head

    slow = fast = dummy

    for _ in range(n + 1):

        fast = fast.next

    while fast:

        slow = slow.next

        fast = fast.next

    slow.next = slow.next.next

    return dummy.next
```

---

## 56. Implement Stack Using List

### Solution

```python
stack = []

stack.append(10)

stack.append(20)

print(stack.pop())
```

Output

```python
20
```

---

## 57. Check Balanced Brackets

### Solution

```python
def valid(s):

    stack = []

    mapping = {
        ")":"(",
        "]":"[",
        "}":"{"
    }

    for ch in s:

        if ch in mapping.values():

            stack.append(ch)

        else:

            if not stack or stack.pop() != mapping[ch]:

                return False

    return not stack
```

---

## 58. Implement Queue Using List

### Solution

```python
queue = []

queue.append(10)

queue.append(20)

print(queue.pop(0))
```

---

## 59. Implement Queue Using deque

### Solution

```python
from collections import deque

queue = deque()

queue.append(10)

queue.append(20)

print(queue.popleft())
```

---

## 60. Next Greater Element

### Solution

```python
nums = [2,1,2,4,3]

stack = []

result = [-1] * len(nums)

for i in range(len(nums)-1,-1,-1):

    while stack and stack[-1] <= nums[i]:

        stack.pop()

    if stack:

        result[i] = stack[-1]

    stack.append(nums[i])

print(result)
```

Output

```python
[4,2,4,-1,-1]
```

---

## 61. Binary Tree Inorder Traversal

### Solution

```python
def inorder(root):

    if root:

        inorder(root.left)

        print(root.val)

        inorder(root.right)
```

---

## 62. Binary Tree Preorder Traversal

### Solution

```python
def preorder(root):

    if root:

        print(root.val)

        preorder(root.left)

        preorder(root.right)
```

---

## 63. Binary Tree Postorder Traversal

### Solution

```python
def postorder(root):

    if root:

        postorder(root.left)

        postorder(root.right)

        print(root.val)
```

---

## 64. Level Order Traversal (BFS)

### Solution

```python
from collections import deque

def bfs(root):

    queue = deque([root])

    while queue:

        node = queue.popleft()

        print(node.val)

        if node.left:

            queue.append(node.left)

        if node.right:

            queue.append(node.right)
```

---

## 65. Maximum Depth of Binary Tree

### Solution

```python
def max_depth(root):

    if not root:

        return 0

    return 1 + max(
        max_depth(root.left),
        max_depth(root.right)
    )
```

---

## 66. Check If Binary Tree is Balanced

### Solution

```python
def balanced(root):

    if not root:

        return True

    left = max_depth(root.left)

    right = max_depth(root.right)

    return (
        abs(left-right) <= 1
        and balanced(root.left)
        and balanced(root.right)
    )
```

---

## 67. Lowest Common Ancestor

### Solution

```python
def lca(root, p, q):

    if not root:

        return None

    if root == p or root == q:

        return root

    left = lca(root.left,p,q)

    right = lca(root.right,p,q)

    if left and right:

        return root

    return left or right
```

---

## 68. Depth First Search (DFS)

### Solution

```python
def dfs(graph,node,visited):

    if node in visited:

        return

    visited.add(node)

    print(node)

    for neighbor in graph[node]:

        dfs(
            graph,
            neighbor,
            visited
        )
```

---

## 69. Breadth First Search (BFS)

### Solution

```python
from collections import deque

def bfs(graph,start):

    visited = set()

    queue = deque([start])

    while queue:

        node = queue.popleft()

        if node not in visited:

            print(node)

            visited.add(node)

            queue.extend(
                graph[node]
            )
```

---

## 70. Recursive Sum of List

### Solution

```python
def total(nums):

    if not nums:

        return 0

    return nums[0] + total(nums[1:])
```

---

## 71. Tower of Hanoi

### Solution

```python
def hanoi(n, source, target, helper):

    if n == 1:

        print(source, target)

        return

    hanoi(
        n-1,
        source,
        helper,
        target
    )

    print(source, target)

    hanoi(
        n-1,
        helper,
        target,
        source
    )
```

---

## 72. Climbing Stairs (DP)

### Solution

```python
def climb(n):

    if n <= 2:

        return n

    a,b = 1,2

    for _ in range(3,n+1):

        a,b = b,a+b

    return b
```

---

## 73. Coin Change

### Solution

```python
def coin_change(coins, amount):

    dp = [float("inf")] * (amount+1)

    dp[0] = 0

    for coin in coins:

        for i in range(
            coin,
            amount+1
        ):

            dp[i] = min(
                dp[i],
                dp[i-coin] + 1
            )

    return (
        dp[amount]
        if dp[amount] != float("inf")
        else -1
    )
```

---

## 74. Generate All Subsets

### Solution

```python
def subsets(nums):

    result = [[]]

    for num in nums:

        result += [
            curr+[num]
            for curr in result
        ]

    return result

print(subsets([1,2]))
```

Output

```python
[[], [1], [2], [1,2]]
```

---

## 75. Generate Permutations

### Solution

```python
from itertools import permutations

nums = [1,2,3]

print(
    list(
        permutations(nums)
    )
)
```
---

## 76. Word Search (Backtracking)

### Problem

Determine whether a word exists in a 2D board.

### Solution

```python
def exist(board, word):

    rows = len(board)

    cols = len(board[0])

    def dfs(r, c, index):

        if index == len(word):

            return True

        if (
            r < 0 or
            c < 0 or
            r >= rows or
            c >= cols or
            board[r][c] != word[index]
        ):

            return False

        temp = board[r][c]

        board[r][c] = "#"

        found = (
            dfs(r+1,c,index+1) or
            dfs(r-1,c,index+1) or
            dfs(r,c+1,index+1) or
            dfs(r,c-1,index+1)
        )

        board[r][c] = temp

        return found

    for r in range(rows):

        for c in range(cols):

            if dfs(r,c,0):

                return True

    return False
```

---

## 77. N-Queens

### Solution

```python
def solve_n_queens(n):

    result = []

    cols = set()

    diag1 = set()

    diag2 = set()

    board = [["."]*n for _ in range(n)]

    def backtrack(r):

        if r == n:

            result.append(
                ["".join(row) for row in board]
            )

            return

        for c in range(n):

            if (
                c in cols or
                r-c in diag1 or
                r+c in diag2
            ):
                continue

            cols.add(c)

            diag1.add(r-c)

            diag2.add(r+c)

            board[r][c] = "Q"

            backtrack(r+1)

            cols.remove(c)

            diag1.remove(r-c)

            diag2.remove(r+c)

            board[r][c] = "."

    backtrack(0)

    return result
```

---

## 78. Combination Sum

### Solution

```python
def combination_sum(nums, target):

    result = []

    def dfs(start, path, total):

        if total == target:

            result.append(path[:])

            return

        if total > target:

            return

        for i in range(start, len(nums)):

            dfs(
                i,
                path+[nums[i]],
                total+nums[i]
            )

    dfs(0, [], 0)

    return result
```

---

## 79. Kth Largest Element

### Solution

```python
import heapq

nums = [3,2,1,5,6,4]

k = 2

print(
    heapq.nlargest(k, nums)[-1]
)
```

### Output

```python
5
```

---

## 80. Top K Frequent Words

### Solution

```python
from collections import Counter

words = [
    "i",
    "love",
    "python",
    "i",
    "love"
]

print(
    Counter(words).most_common(2)
)
```

---

## 81. Merge K Sorted Lists

### Solution

```python
import heapq

lists = [
    [1,4,5],
    [1,3,4],
    [2,6]
]

merged = list(
    heapq.merge(*lists)
)

print(merged)
```

---

## 82. Implement Min Heap

### Solution

```python
import heapq

heap = []

heapq.heappush(heap, 10)

heapq.heappush(heap, 5)

heapq.heappush(heap, 20)

print(
    heapq.heappop(heap)
)
```

### Output

```python
5
```

---

## 83. Number of Islands

### Solution

```python
def islands(grid):

    rows = len(grid)

    cols = len(grid[0])

    count = 0

    def dfs(r,c):

        if (
            r < 0 or
            c < 0 or
            r >= rows or
            c >= cols or
            grid[r][c] == "0"
        ):
            return

        grid[r][c] = "0"

        dfs(r+1,c)

        dfs(r-1,c)

        dfs(r,c+1)

        dfs(r,c-1)

    for r in range(rows):

        for c in range(cols):

            if grid[r][c] == "1":

                count += 1

                dfs(r,c)

    return count
```

---

## 84. Course Schedule (Cycle Detection)

### Solution

```python
from collections import defaultdict

def can_finish(num, prerequisites):

    graph = defaultdict(list)

    for a,b in prerequisites:

        graph[a].append(b)

    visiting = set()

    visited = set()

    def dfs(course):

        if course in visiting:

            return False

        if course in visited:

            return True

        visiting.add(course)

        for pre in graph[course]:

            if not dfs(pre):

                return False

        visiting.remove(course)

        visited.add(course)

        return True

    for course in range(num):

        if not dfs(course):

            return False

    return True
```

---

## 85. Clone Graph

### Solution

```python
def clone(node):

    old_to_new = {}

    def dfs(node):

        if node in old_to_new:

            return old_to_new[node]

        copy = Node(node.val)

        old_to_new[node] = copy

        for neigh in node.neighbors:

            copy.neighbors.append(
                dfs(neigh)
            )

        return copy

    return dfs(node)
```

---

## 86. Spiral Matrix Traversal

### Solution

```python
matrix = [
    [1,2,3],
    [4,5,6],
    [7,8,9]
]

result = []

while matrix:

    result += matrix.pop(0)

    matrix = list(zip(*matrix))[::-1]

print(result)
```

---

## 87. Search in Rotated Sorted Array

### Solution

```python
def search(nums, target):

    left = 0

    right = len(nums)-1

    while left <= right:

        mid = (left+right)//2

        if nums[mid] == target:

            return mid

        if nums[left] <= nums[mid]:

            if nums[left] <= target < nums[mid]:

                right = mid-1

            else:

                left = mid+1

        else:

            if nums[mid] < target <= nums[right]:

                left = mid+1

            else:

                right = mid-1

    return -1
```

---

## 88. LRU Cache

### Solution

```python
from collections import OrderedDict

class LRUCache:

    def __init__(self, capacity):

        self.cache = OrderedDict()

        self.capacity = capacity

    def get(self, key):

        if key not in self.cache:

            return -1

        self.cache.move_to_end(key)

        return self.cache[key]

    def put(self, key, value):

        self.cache[key] = value

        self.cache.move_to_end(key)

        if len(self.cache) > self.capacity:

            self.cache.popitem(last=False)
```

---

## 89. Trapping Rain Water

### Solution

```python
height = [4,2,0,3,2,5]

left = 0

right = len(height)-1

left_max = right_max = 0

water = 0

while left < right:

    if height[left] < height[right]:

        left_max = max(
            left_max,
            height[left]
        )

        water += left_max-height[left]

        left += 1

    else:

        right_max = max(
            right_max,
            height[right]
        )

        water += right_max-height[right]

        right -= 1

print(water)
```

---

## 90. Median of Two Sorted Arrays

### Solution

```python
nums1 = [1,3]

nums2 = [2]

merged = sorted(nums1+nums2)

n = len(merged)

print(
    merged[n//2]
)
```

---

## 91. Trie Implementation

### Solution

```python
class TrieNode:

    def __init__(self):

        self.children = {}

        self.end = False

class Trie:

    def __init__(self):

        self.root = TrieNode()
```

---

## 92. Word Break Problem

### Solution

```python
def word_break(s, words):

    dp = [False]*(len(s)+1)

    dp[0] = True

    for i in range(1,len(s)+1):

        for j in range(i):

            if (
                dp[j]
                and
                s[j:i] in words
            ):

                dp[i] = True

                break

    return dp[-1]
```

---

## 93. Longest Increasing Subsequence

### Solution

```python
nums = [10,9,2,5,3,7,101,18]

dp = [1]*len(nums)

for i in range(len(nums)):

    for j in range(i):

        if nums[i] > nums[j]:

            dp[i] = max(
                dp[i],
                dp[j]+1
            )

print(max(dp))
```

---

## 94. Edit Distance

### Solution

```python
def min_distance(a,b):

    m = len(a)

    n = len(b)

    dp = [
        [0]*(n+1)
        for _ in range(m+1)
    ]

    for i in range(m+1):

        dp[i][0] = i

    for j in range(n+1):

        dp[0][j] = j

    for i in range(1,m+1):

        for j in range(1,n+1):

            if a[i-1] == b[j-1]:

                dp[i][j] = dp[i-1][j-1]

            else:

                dp[i][j] = 1 + min(
                    dp[i-1][j],
                    dp[i][j-1],
                    dp[i-1][j-1]
                )

    return dp[m][n]
```

---

## 95. Maximum Product Subarray

### Solution

```python
nums = [2,3,-2,4]

cur_max = cur_min = result = nums[0]

for num in nums[1:]:

    temp = cur_max

    cur_max = max(
        num,
        cur_max*num,
        cur_min*num
    )

    cur_min = min(
        num,
        temp*num,
        cur_min*num
    )

    result = max(
        result,
        cur_max
    )

print(result)
```

---

## 96. Find Duplicate Using Floyd Cycle

### Solution

```python
nums = [1,3,4,2,2]

slow = fast = nums[0]

while True:

    slow = nums[slow]

    fast = nums[nums[fast]]

    if slow == fast:

        break

slow2 = nums[0]

while slow != slow2:

    slow = nums[slow]

    slow2 = nums[slow2]

print(slow)
```

---

## 97. Serialize Binary Tree

### Solution

```python
def serialize(root):

    if not root:

        return "null"

    return (
        str(root.val)
        + ","
        + serialize(root.left)
        + ","
        + serialize(root.right)
    )
```

---

## 98. Deserialize Binary Tree

### Solution

```python
def deserialize(data):

    values = iter(data.split(","))

    def build():

        val = next(values)

        if val == "null":

            return None

        node = TreeNode(int(val))

        node.left = build()

        node.right = build()

        return node

    return build()
```

---

## 99. Design a Rate Limiter

### Solution

```python
from collections import deque

class RateLimiter:

    def __init__(self, limit):

        self.limit = limit

        self.requests = deque()
```

### Interview Concepts

* Queue
* Sliding Window
* System Design

---

## 100. Design a URL Shortener

### Solution

```python
import hashlib

def shorten(url):

    return hashlib.md5(
        url.encode()
    ).hexdigest()[:6]
```

### Interview Concepts

* Hashing
* Databases
* Distributed Systems
* Scalability
