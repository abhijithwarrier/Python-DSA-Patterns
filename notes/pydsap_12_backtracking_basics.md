**Programmer:** python_scripts (Abhijith Warrier)

**NOTES ON GENERATING COMBINATIONS, PERMUTATIONS & SEARCHING USING BACKTRACKING. 🐍🔙**

**Backtracking** is a technique for exploring all possible configurations of a problem.
It builds solutions **step by step**, and whenever a path is invalid, it **backtracks** — undoing the last step and trying something else.

It’s the backbone of problems like **subsets**, **permutations**, **N-Queens**, **Sudoku solving**, and **maze paths**.

---

## **✨ When to Use**

- When the solution must be built **incrementally**.
- When you need to explore **all combinations/permutations**.
- When constraints may **invalidate** partial solutions.
- When brute force exists, but can be pruned with smart decisions.

---

## **⚡ Advantages**

- Finds *all* valid solutions.
- Simple recursive pattern.
- Works great when combined with pruning (constraints to cut branches).

---

## **❗ Limitations**

- Exponential time in worst cases.
- Needs careful pruning to avoid TLE.

---

## **📝 Example 1 — Generate All Subsets**

*Classic backtracking: choose or skip each element.*

```csharp
def subsets(nums):
    result = []
    subset = []

    def backtrack(i):
        if i == len(nums):
            result.append(subset.copy())
            return
        # include element
        subset.append(nums[i])
        backtrack(i + 1)
        # exclude element
        subset.pop()
        backtrack(i + 1)

    backtrack(0)
    print("Subsets:", result)

subsets([1, 2, 3])
# Output: all subsets of [1,2,3]
```

---

## **📝 Example 2 — Generate All Permutations**

*All orderings of elements — swap-based or choose-based pattern.*

```csharp
def permutations(nums):
    result = []
    used = [False] * len(nums)
    current = []

    def backtrack():
        if len(current) == len(nums):
            result.append(current.copy())
            return
        for i in range(len(nums)):
            if not used[i]:
                used[i] = True
                current.append(nums[i])
                backtrack()
                current.pop()
                used[i] = False

    backtrack()
    print("Permutations:", result)

permutations([1, 2, 3])
```

---

## **📝 Example 3 — N-Queens (Conceptual Intro)**

*N-Queens places 1 queen per row so that no two queens attack each other.*

Only showing the structure here — actual solution goes deep, but follows the same backtracking template.

```csharp
# Structure:
# place queen row by row
# try each column
# if safe → recurse to next row
# if unsafe → backtrack
```

This is one of the best problems to **learn pruning**.

---

## **🧠 Backtracking Template (General Form)**

```csharp
def backtrack(path, choices):
    if goal_reached(path):
        save(path)
        return
    
    for choice in choices:
        if is_valid(choice, path):
            apply(choice, path)
            backtrack(path, choices)
            undo(choice, path)   # backtrack step
```

Almost every backtracking problem maps to this template.

---

## **🧠 Where It Helps**

- 🔢 Subsets, Combinations
- 🔀 Permutations
- ♟️ N-Queens, Sudoku, Crossword fill
- 🗺️ Maze solving (all paths)
- 🔤 Word search in grids
- 🧩 Constraint satisfaction problems

---

## **✅ Takeaways**

- Backtracking = recursion + undoing last choice.
- Builds solutions incrementally.
- Use **pruning** to skip invalid paths early.
- Extremely powerful for generation & search problems.

---

## **🏋️ Practice Problems**

1. Subsets
2. Permutations
3. Combination Sum
4. N-Queens
5. Word Search

---