**Programmer:** python_scripts (Abhijith Warrier)

**NOTES ON ORDERING TASKS & DEPENDENCIES USING TOPOLOGICAL SORT IN DAGs. 🐍📐**

A **Directed Acyclic Graph (DAG)** is a graph with **directed edges** and **no cycles**. **Topological Sorting** produces a linear ordering of nodes such that **every directed edge u → v means u comes before v**. This pattern is fundamental for **dependency resolution**, **task scheduling**, and **build systems**.

---

## ✨ When to Use

- When tasks have **dependencies** (one must finish before another starts).
- When you need a **valid execution order**.
- When the graph is **directed** and **must be acyclic**.

---

## ⚡ Two Common Approaches

### 1️⃣ Kahn’s Algorithm (BFS-based)

- Uses **in-degree counting**.
- Start with nodes having **0 in-degree**.
- Remove them level by level.

### 2️⃣ DFS-based Topological Sort

- Uses **postorder DFS**.
- Push nodes to stack after visiting all neighbors.

---

## 📝 Example 1 — Kahn’s Algorithm (BFS / In-Degree Method)

*Repeatedly process nodes with no incoming edges.*

```jsx
from collections import deque, defaultdict

def topo_sort_bfs(n, edges):
    graph = defaultdict(list)
    indegree = [0] * n

    for u, v in edges:
        graph[u].append(v)
        indegree[v] += 1

    queue = deque([i for i in range(n) if indegree[i] == 0])
    order = []

    while queue:
        node = queue.popleft()
        order.append(node)
        for nei in graph[node]:
            indegree[nei] -= 1
            if indegree[nei] == 0:
                queue.append(nei)

    print("Topological Order (BFS):", order)

topo_sort_bfs(6, [(5,2),(5,0),(4,0),(4,1),(2,3),(3,1)])
```

---

## 📝 Example 2 — DFS-Based Topological Sort

*Push nodes to stack after exploring all outgoing edges.*

```jsx
from collections import defaultdict

def topo_sort_dfs(n, edges):
    graph = defaultdict(list)
    visited = [False] * n
    stack = []

    for u, v in edges:
        graph[u].append(v)

    def dfs(node):
        visited[node] = True
        for nei in graph[node]:
            if not visited[nei]:
                dfs(nei)
        stack.append(node)

    for i in range(n):
        if not visited[i]:
            dfs(i)

    print("Topological Order (DFS):", stack[::-1])

topo_sort_dfs(6, [(5,2),(5,0),(4,0),(4,1),(2,3),(3,1)])
```

---

## 🚨 Cycle Detection (Important)

- **Topological sort exists ONLY if the graph is acyclic**.
- In Kahn’s algorithm:
    - If processed nodes < total nodes → **cycle exists**.

---

## 🧠 Where It Helps

- 🏗️ Build systems & compilation order
- 📚 Course scheduling (prerequisites)
- 🔄 Task dependency resolution
- 🚀 Workflow orchestration
- 🧩 Deadlock detection (indirectly)

---

## ❗ Common Mistakes

- Applying topo sort to **undirected graphs**
- Forgetting to check for **cycles**
- Confusing BFS levels with valid ordering

---

## ✅ Takeaways

- Topological sorting works only on **DAGs**
- BFS method uses **in-degree**
- DFS method uses **postorder traversal**
- Essential for dependency-based problems

---

## 🏋️ Practice Problems

1. Course Schedule
2. Course Schedule II
3. Alien Dictionary
4. Find Eventual Safe States
5. Build Order

---