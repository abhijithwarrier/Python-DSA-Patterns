# **Python DSA Patterns — Binary Search Patterns**

**Programmer:** python_scripts (Abhijith Warrier)

**NOTES ON SOLVING SEARCH & OPTIMIZATION PROBLEMS USING BINARY SEARCH PATTERNS. 🐍🔍**

Binary Search is more than just finding an element in a sorted array.

It’s a versatile pattern that applies to **searching, decision-making, and optimization problems** by repeatedly halving the search space.

---

## ✨ When to Use

- The input is **sorted** (array, matrix, or monotonic property).
- The problem asks for **first/last occurrence**, **boundary index**, or **decision-based minimum/maximum**.
- When brute force scanning is O(n) but you need **O(log n)**.

---

## ⚡ Advantages

- Reduces search time from O(n) to O(log n).
- Works not only on arrays, but also on **answer ranges** (binary search on solution space).
- Forms the basis of many advanced algorithms (search trees, parametric search).

---

## 📝 Example 1 — Basic Binary Search

*Find an element in a sorted array.*

```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return -1

# Example
print(binary_search([1, 3, 5, 7, 9], 7))  # Output: 3
```

---

## 📝 Example 2 — First and Last Occurrence

*Return the first index where target appears in a sorted array.*

```python
def first_occurrence(arr, target):
    left, right, result = 0, len(arr) - 1, -1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            result = mid
            right = mid - 1   # keep searching left
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
    return result

print(first_occurrence([1, 2, 2, 2, 3, 4], 2))  # Output: 1
```

---

## 📝 Example 3 — Search in Rotated Sorted Array

*Binary search can handle rotated arrays by checking which side is sorted.*

```python
def search_rotated(arr, target):
    left, right = 0, len(arr) - 1
    while left <= right:
        mid = (left + right) // 2
        if arr[mid] == target:
            return mid
        if arr[left] <= arr[mid]:  # left half sorted
            if arr[left] <= target < arr[mid]:
                right = mid - 1
            else:
                left = mid + 1
        else:  # right half sorted
            if arr[mid] < target <= arr[right]:
                left = mid + 1
            else:
                right = mid - 1
    return -1

print(search_rotated([4,5,6,7,0,1,2], 0))  # Output: 4
```

---

## 📝 Example 4 — Binary Search on Answer Space

*Find the smallest x such that x*x ≥ target (integer square root).*

```python
def integer_sqrt(target):
    left, right, ans = 0, target, -1
    while left <= right:
        mid = (left + right) // 2
        if mid * mid <= target:
            ans = mid
            left = mid + 1
        else:
            right = mid - 1
    return ans

print(integer_sqrt(10))  # Output: 3
```

---

## ✅ Key Takeaways

- **Classic Binary Search** → find elements in sorted arrays.
- **Modified Binary Search** → first/last occurrence, rotated arrays.
- **Answer Space Search** → find minimum/maximum satisfying a condition.
- Think: *Is the search space monotonic?* If yes, binary search applies.

---

## 🏋️ Practice Problems

1. Binary Search (basic element search).
2. First and Last Position of Element in Sorted Array.
3. Search in Rotated Sorted Array.
4. Find Peak Element.
5. Sqrt(x) (binary search on answer space).

---