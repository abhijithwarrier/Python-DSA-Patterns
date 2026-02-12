**Programmer:** python_scripts (Abhijith Warrier)

**NOTES ON USING HASHMAPS & SETS TO OPTIMIZE LOOKUPS AND COUNTING PROBLEMS. 🐍📊**

Hashing is one of the most powerful and frequently used patterns in DSA. It allows us to replace nested loops with **constant-time lookups**, often converting **O(n²)** solutions into **O(n)**. Most problems involving:

- Counting
- Grouping
- Complements
- Duplicate detection
- Prefix tracking

…are solved using hashing.

---

## **✨ Why Hashing Works**

Python’s:

- dict → HashMap
- set → HashSet

provide **average O(1)** time complexity for insert, delete, and lookup.

That makes them perfect for frequency-based and existence-check problems.

---

## **🧠 Core Hashing Patterns**

### **1️⃣ Frequency Counting**

Count occurrences efficiently.

```jsx
from collections import Counter

def frequency_count(nums):
    freq = Counter(nums)
    print("Frequency Map:", freq)
```

Used in:

- Majority element
- Top K frequent
- Anagram detection

---

### **2️⃣ Complement Lookup (Two Sum Pattern)**

Store previously seen numbers to find a matching pair.

```jsx
def two_sum(nums, target):
    seen = {}
    for i, num in enumerate(nums):
        diff = target - num
        if diff in seen:
            return [seen[diff], i]
        seen[num] = i
```

Pattern:

> Store → Check complement → Insert
> 

---

### **3️⃣ Anagram Grouping**

Sort or use frequency signature as key.

```jsx
from collections import defaultdict

def group_anagrams(words):
    groups = defaultdict(list)
    for word in words:
        key = ''.join(sorted(word))
        groups[key].append(word)
    print("Anagram Groups:", list(groups.values()))
```

Key idea:

> Use a normalized form as hashmap key
> 

---

### **4️⃣ Prefix Sum + HashMap**

Detect subarrays with given sum.

```jsx
def subarray_sum(nums, k):
    prefix = 0
    count = 0
    seen = {0: 1}

    for num in nums:
        prefix += num
        if prefix - k in seen:
            count += seen[prefix - k]
        seen[prefix] = seen.get(prefix, 0) + 1

    print("Subarrays with Sum K:", count)
```

This pattern avoids nested loops.

---

### **5️⃣ Using Sets for Existence & Deduplication**

```jsx
def contains_duplicate(nums):
    seen = set()
    for num in nums:
        if num in seen:
            return True
        seen.add(num)
    return False
```

Set lookup eliminates repeated scans.

---

## **🧠 Where Hashing Patterns Help**

- 🔢 Two Sum & k-Sum variations
- 🔤 Anagram problems
- 📊 Frequency-based logic
- 🧩 Subarray sum problems
- 🔍 Duplicate detection
- 🧠 Graph adjacency storage

---

## **❗ Common Mistakes**

- Forgetting to initialize {0:1} in prefix sum problems
- Using list instead of dict/set for lookup
- Not handling negative numbers in prefix problems
- Sorting unnecessarily when hashing would work

---

## **✅ Takeaways**

- Hashing converts many O(n²) problems into O(n)
- Complement lookup is a reusable pattern
- Prefix sum + hashmap is extremely powerful
- Sets are best for fast existence checks
- Hashing appears everywhere in DSA

---

## **🏋️ Practice Problems**

1. Two Sum
2. Subarray Sum Equals K
3. Group Anagrams
4. Top K Frequent Elements
5. Longest Consecutive Sequence

---