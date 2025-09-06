# **Python DSA Patterns — Two Pointers**

**Programmer:** python_scripts (Abhijith Warrier)

**NOTES ON SOLVING ARRAY & STRING PROBLEMS USING THE TWO POINTERS PATTERN. 🐍👆👇**

The **two pointers** technique uses two indices that move through an array or string, often from opposite ends or at different speeds.

It helps reduce nested loops and optimizes many problems from **O(n²)** to **O(n)**.

---

## **✨ When to Use**

- When the problem involves **pairs** or **subarrays**.
- When the array/string is **sorted** or can be sorted.
- When we need to find **relationships between two elements**.

---

## **⚡ Advantages**

- Simplifies problems that would normally require nested loops.
- Often reduces time complexity from quadratic to linear.
- Easy to implement with just a few variables.

---

## **📝 Example 1 — Sorted Array: Two Sum Problem**

*Given a sorted array and a target, find if two numbers add up to the target.*

```python
def two_sum_sorted(arr, target):
    left, right = 0, len(arr) - 1
    
    while left < right:
        current = arr[left] + arr[right]
        
        if current == target:
            return (left, right)
        elif current < target:
            left += 1
        else:
            right -= 1
    
    return None

# Example
print(two_sum_sorted([1, 2, 4, 6, 10], 8))  # Output: (1, 3) -> 2+6
```

---

## **📝 Example 2 — Removing Duplicates from Sorted Array**

*Compact the array in place so each element appears only once.*

```python
def remove_duplicates(arr):
    if not arr:
        return 0
    
    left = 0
    
    for right in range(1, len(arr)):
        if arr[right] != arr[left]:
            left += 1
            arr[left] = arr[right]
    
    return left + 1

# Example
nums = [1, 1, 2, 2, 3]
length = remove_duplicates(nums)
print(nums[:length])  # Output: [1, 2, 3]
```

---

## **📝 Example 3 — Valid Palindrome Check**

*Check if a string is a palindrome, ignoring non-alphanumeric characters.*

```python
def is_palindrome(s: str) -> bool:
    s = "".join(ch.lower() for ch in s if ch.isalnum())
    left, right = 0, len(s) - 1
    
    while left < right:
        if s[left] != s[right]:
            return False
        left += 1
        right -= 1
    
    return True

# Example
print(is_palindrome("A man, a plan, a canal: Panama"))  # Output: True
```

---

## **✅ Key Takeaways**

- Use **two pointers** when working with pairs, palindromes, or deduplication.
- Works best on **sorted arrays** or **linear scans**.
- A simple yet powerful way to eliminate nested loops.

---

## **🏋️ Practice Problems**

1. Pair with Target Sum (classic 2-sum in sorted array).
2. Remove Duplicates from Sorted Array.
3. Valid Palindrome (string cleaning + two pointers).
4. Container With Most Water (two pointers moving inward).

---