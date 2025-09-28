**Programmer:** python_scripts (Abhijith Warrier)

**NOTES ON SOLVING OPTIMIZATION PROBLEMS USING THE GREEDY TECHNIQUE. 🐍💰**

The **Greedy technique** builds a solution step by step, always choosing the **locally optimal choice** at each step.

If the problem satisfies the **greedy-choice property** and **optimal substructure**, this approach often leads to the **global optimum**.

---

## ✨ When to Use

- Problem can be solved by **making a sequence of choices**.
- Each choice depends only on the **current state**, not future consequences.
- The problem shows **optimal substructure** (optimal solution can be built from optimal subproblems).

---

## ⚡ Advantages

- Usually faster and simpler than DP.
- Efficient for many **optimization problems**.
- Requires less memory (no large DP tables).

---

## ❗ Limitations

- Greedy doesn’t always guarantee the correct global optimum.
- Must verify the problem satisfies greedy-choice property.

---

## 📝 Example 1 — Activity Selection Problem

*Select the maximum number of non-overlapping activities given start & end times.*

```python
def activity_selection(activities):
    # activities: list of (start, end) times
    # sort by end time
    activities.sort(key=lambda x: x[1])
    result = []
    last_end = 0

    for start, end in activities:
        if start >= last_end:
            result.append((start, end))
            last_end = end
    return result

print(activity_selection([(1,3),(2,4),(3,5),(0,6),(5,7),(8,9)]))
# Output: [(1,3),(3,5),(5,7),(8,9)]
```

---

## 📝 Example 2 — Coin Change (Minimum Coins)

*Given coin denominations, make change for an amount with the fewest coins (works when greedy is optimal, e.g., standard currencies).*

```python
def coin_change(coins, amount):
    coins.sort(reverse=True)  # pick largest first
    result = []
    for coin in coins:
        while amount >= coin:
            amount -= coin
            result.append(coin)
    return result

print(coin_change([1,2,5,10], 27))
# Output: [10, 10, 5, 2]
```

---

## 📝 Example 3 — Huffman Coding (Conceptual)

*Greedy is used to build optimal prefix codes by repeatedly combining the lowest-frequency nodes.*

(Usually implemented with a min-heap — beyond basics, but shows greedy’s reach).

---

## ✅ Key Takeaways

- Greedy = choose the best option available at each step.
- Works only when **local choices → global optimum**.
- Common in scheduling, interval problems, minimum spanning trees, Huffman coding, coin change.

---

## 🏋️ Practice Problems

1. Activity Selection (classic scheduling).
2. Coin Change (minimum coins).
3. Fractional Knapsack.
4. Minimum Spanning Tree (Prim’s / Kruskal’s).
5. Huffman Coding.

---