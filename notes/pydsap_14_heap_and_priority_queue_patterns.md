**Programmer:** python_scripts (Abhijith Warrier)

**NOTES ON FAST RETRIEVAL OF MIN/MAX ELEMENTS USING HEAPS & PRIORITY QUEUES. 🐍🔼**

A **Heap** is a specialized tree-based structure used to efficiently get the **minimum** or **maximum** element.

Python provides a **min-heap** through the heapq module — everything is arranged so the smallest element is always on top.

Heaps are essential for **top-K problems**, **greedy scheduling**, **Dijkstra**, **event handling**, and **stream processing**.

---

## ✨ When to Use

- When you need the **smallest/largest element repeatedly**.
- When processing data **in sorted order but without sorting everything**.
- When solving **top-K, Kth largest/smallest**, or **merge sorted lists** problems.
- When you need **priority-based processing**.

---

## ⚡ Advantages

- Insert → **O(log n)**
- Extract-min / extract-max → **O(log n)**
- Build heap → **O(n)**
- Perfect for online/streaming scenarios

---

## ❗ Limitations

- Not designed for random access
- No balanced-tree ordering (not fully sorted)
- Removing arbitrary elements is slow

---

## 📝 Example 1 — Min-Heap Basics

*Push and pop values while maintaining the smallest element at the top.*

```jsx
import heapq

nums = [5, 1, 8, 3, 2]
min_heap = []

for n in nums:
    heapq.heappush(min_heap, n)

print("Min-Heap Pop Order:", [heapq.heappop(min_heap) for _ in range(len(min_heap))])
# Output: [1, 2, 3, 5, 8]
```

---

## 📝 Example 2 — Kth Largest Element (Using Min-Heap)

*Keep a heap of size K — efficient for large inputs.*

```jsx
import heapq

def kth_largest(nums, k):
    heap = []
    for n in nums:
        heapq.heappush(heap, n)
        if len(heap) > k:
            heapq.heappop(heap)
    return heap[0]

print("Kth Largest:", kth_largest([3,2,3,1,2,4,5,5,6], 4))
```

---

## 📝 Example 3 — Merge K Sorted Lists

*Always pick the smallest current element using a heap.*

```jsx
import heapq

def merge_k_lists(lists):
    min_heap = []
    result = []

    # push the first element of each list
    for i, lst in enumerate(lists):
        if lst:
            heapq.heappush(min_heap, (lst[0], i, 0))

    while min_heap:
        val, li, idx = heapq.heappop(min_heap)
        result.append(val)

        # push next element from the same list
        if idx + 1 < len(lists[li]):
            heapq.heappush(min_heap, (lists[li][idx+1], li, idx+1))

    print("Merged:", result)

merge_k_lists([[1,4,5],[1,3,4],[2,6]])
```

---

## 🧠 Max-Heap in Python

Python doesn’t offer one natively — but you can simulate it using **negative values**:

```jsx
max_heap = []
for n in [3,1,5,2]:
    heapq.heappush(max_heap, -n)

print("Max element:", -heapq.heappop(max_heap))
```

---

## 🧠 Where It Helps

- 🔝 Top-K problems (Top-K frequent, Kth largest)
- 🧩 Merging sorted lists
- 🚦 Task scheduling / CPU scheduling
- 🗺️ Dijkstra’s shortest path
- 📦 Streaming data (continuous min/max)
- 💹 Running medians (two-heap method)

---

## **✅** Takeaways

- Heaps give **fast min/max extraction** in O(log n).
- Great for problems where you repeatedly need the **smallest/largest** item.
- Use tuples (value, details…) to store extra info.
- Python = **min-heap only** → simulate max-heap with negatives.

---

## 🏋️ Practice Problems

1. Kth Largest Element
2. Top K Frequent Elements
3. Merge K Sorted Lists
4. Find Median from Data Stream
5. Last Stone Weight

---
