# Arrays & Hashing

Arrays and hash tables form the foundation of data structures and algorithmic problem-solving. This section covers essential patterns for manipulating arrays and leveraging hash tables for efficient lookups, counting, and grouping operations

## Problems

| Problem | Difficulty | Topics |
|---------|-----------|--------|
| Contains Duplicate | Easy | Hash Set, Array |
| Valid Anagram | Easy | Hash Map, Sorting |
| Two Sum | Easy | Hash Map, Array |
| Group Anagrams | Medium | Hash Map, Sorting |
| Top K Frequent Elements | Medium | Hash Map, Heap |
| Encode and Decode Strings | Medium | String, Array |
| Product of Array Except Self | Medium | Prefix/Suffix Product |
| Valid Sudoku | Medium | Hash Set, Matrix |
| Longest Consecutive Sequence | Medium | Hash Set, Union Find |

## Prerequisites

### Dynamic Arrays

Dynamic arrays (vectors, ArrayLists) are resizable arrays that automatically grow when capacity is exceeded

**Key Concepts:**
- **Amortized O(1) insertion**: When the array is full, create a new array of double size and copy elements 
- **Random access**: O(1) time to access any element by index
- **Resize strategy**: Typically doubles capacity when full to maintain amortized constant time

**Python Implementation:**
```
# Python lists are dynamic arrays
arr = []           # Create empty array
arr.append(5)      # O(1) amortized - adds to end
arr             # O(1) access by index
arr.insert(0, 3)   # O(n) - shifts all elements
arr.pop()          # O(1) - removes from end
arr.pop(0)         # O(n) - removes from start
```

**Common Operations:**
- Append: O(1) amortized
- Access: O(1)
- Insert/Delete at index: O(n)
- Search: O(n)

### Hash Usage

Hash tables provide O(1) average-case lookup, insertion, and deletion by mapping keys to array indices using a hash function

**Key Concepts:**
- **Hash function**: Converts keys to array indices deterministically
- **Collision handling**: Multiple keys can hash to same index (chaining or open addressing)
- **Load factor**: Ratio of entries to buckets; tables resize when load factor exceeds threshold

**Python Implementation:**
```
# Hash Map (Dictionary)
hash_map = {}
hash_map["key"] = "value"    # O(1) insertion
val = hash_map.get("key")    # O(1) lookup
hash_map.pop("key")          # O(1) deletion

# Hash Set
hash_set = set()
hash_set.add(5)              # O(1) insertion
5 in hash_set                # O(1) membership check
hash_set.remove(5)           # O(1) deletion

# Counting with defaultdict
from collections import defaultdict
counter = defaultdict(int)
counter["a"] += 1            # Auto-initializes to 0

# Counter for frequency counting
from collections import Counter
freq = Counter()  # {1: 1, 2: 2, 3: 3}[1][2][3]
```

**Common Use Cases:**
- Checking for duplicates: O(n) with hash set vs O(n²) with nested loops
- Frequency counting: Hash map to store element counts 
- Two Sum pattern: Store complements in hash map
- Grouping elements: Use hash map with lists as values

### Hash Implementation

Understanding hash table internals helps optimize usage and avoid pitfalls

**Core Components:**
- **Buckets**: Array storing key-value pairs
- **Hash function**: Maps keys to bucket indices
- **Collision resolution**: Chaining (linked lists) or open addressing
- **Dynamic resizing**: Rehashing when load factor exceeds threshold

**Simple Hash Function:**
```
def hash_function(key, table_size):
    """Convert key to index in range ```

**Collision Handling - Chaining:**
```
class HashTable:
    def __init__(self, size=10):
        self.size = size
        self.table = [[] for _ in range(size)]  # List of lists
    
    def insert(self, key, value):
        index = hash(key) % self.size
        # Chain: append to list at this index
        for i, (k, v) in enumerate(self.table[index]):
            if k == key:
                self.table[index][i] = (key, value)  # Update
                return
        self.table[index].append((key, value))  # Insert
    
    def get(self, key):
        index = hash(key) % self.size
        for k, v in self.table[index]:
            if k == key:
                return v
        return None
```

**Performance Considerations:**
- Good hash function distributes keys uniformly
- Load factor > 0.75 triggers resize in most implementations
- Worst case O(n) if all keys collide, but O(1) average case

### Prefix Sums

Prefix sums preprocess an array to answer range sum queries in O(1) time

**Key Concepts:**
- **Preprocessing**: Build array where `prefix[i] = sum(arr[0:i+1])`
- **Range query**: Sum from index L to R = `prefix[R] - prefix[L-1]`
- **Time complexity**: O(n) preprocessing, O(1) per query

**Implementation:**
```
def build_prefix_sum(arr):
    """Build prefix sum array"""
    n = len(arr)
    prefix =  * (n + 1)  # Extra space for easier range queries
    
    for i in range(n):
        prefix[i + 1] = prefix[i] + arr[i]
    
    return prefix

def range_sum(prefix, left, right):
    """Query sum from index left to right (inclusive)"""
    return prefix[right + 1] - prefix[left]

# Example
arr =[2][3][4][5][1]
prefix = build_prefix_sum(arr)  #[3][6][7][8][1]
print(range_sum(prefix, 1, 3))  # Sum of arr[1:4] = 2+3+4 = 9
```

**Common Applications:**
- Subarray sum queries
- Product of array except self (prefix/suffix products)
- Running averages and statistics
- 2D matrix range sums

**2D Prefix Sum:**
```
def build_2d_prefix(matrix):
    """Build 2D prefix sum for matrix range queries"""
    m, n = len(matrix), len(matrix)
    prefix = [ * (n + 1) for _ in range(m + 1)]
    
    for i in range(m):
        for j in range(n):
            prefix[i+1][j+1] = (matrix[i][j] + 
                                prefix[i][j+1] + 
                                prefix[i+1][j] - 
                                prefix[i][j])
    return prefix

def range_sum_2d(prefix, r1, c1, r2, c2):
    """Query sum of rectangle from (r1,c1) to (r2,c2)"""
    return (prefix[r2+1][c2+1] - 
            prefix[r1][c2+1] - 
            prefix[r2+1][c1] + 
            prefix[r1][c1])
```

## Common Patterns

### Pattern 1: Frequency Counting
Use hash map to count occurrences
```
from collections import Counter
freq = Counter(nums)
```

### Pattern 2: Complement Lookup
Store values in hash map and check for complement (Two Sum pattern)
```
seen = {}
for i, num in enumerate(nums):
    complement = target - num
    if complement in seen:
        return [seen[complement], i]
    seen[num] = i
```

### Pattern 3: Grouping with Hash
Group elements by computed key (anagrams, etc.)
```
from collections import defaultdict
groups = defaultdict(list)
for item in items:
    key = compute_key(item)
    groups[key].append(item)
```

### Pattern 4: Hash Set for Deduplication
Use set to remove duplicates or check membership.
```
return len(nums) != len(set(nums))  # Has duplicates
```


