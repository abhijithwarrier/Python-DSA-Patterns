A **Graph** is a non-linear data structure made of **nodes (vertices)** and **edges (connections)**.

It’s used to represent **relationships**, **networks**, or **connected systems** like maps, social media, or web links.

---

## **✨ Graph Types**

- **Directed vs Undirected** → Edges may have direction.
- **Weighted vs Unweighted** → Edges may have cost/weight.
- **Cyclic vs Acyclic** → Graph may contain cycles or not.
- **Dense vs Sparse** → Based on how many edges exist.

---

## **🧩 Common Representations**

- **Adjacency List** — Dictionary or list of lists (space-efficient).
- **Adjacency Matrix** — 2D matrix (easier to query, more space).

Example adjacency list representation:

```python
graph = {
    'A': ['B', 'C'],
    'B': ['A', 'D', 'E'],
    'C': ['A', 'F'],
    'D': ['B'],
    'E': ['B', 'F'],
    'F': ['C', 'E']
}
```

---

## **⚡ Breadth-First Search (BFS)**

**BFS** explores all neighbors first before moving to the next level — it’s like expanding outward layer by layer.

```python
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    while queue:
        node = queue.popleft()
        if node not in visited:
            print(node, end=" ")
            visited.add(node)
            for neighbor in graph[node]:
                if neighbor not in visited:
                    queue.append(neighbor)

bfs(graph, 'A')  # Output: A B C D E F
```

💡 **BFS is ideal for:**

- Finding **shortest paths** in unweighted graphs.
- **Level-order traversal** (like in trees).
- Problems like “minimum steps” or “degrees of connection”.

---

## **⚙️ Depth-First Search (DFS)**

**DFS** dives as deep as possible before backtracking — perfect for exploring full paths or components.

```python
def dfs(graph, node, visited=None):
    if visited is None:
        visited = set()
    print(node, end=" ")
    visited.add(node)
    for neighbor in graph[node]:
        if neighbor not in visited:
            dfs(graph, neighbor, visited)

dfs(graph, 'A')  # Output: A B D E F C
```

💡 **DFS is ideal for:**

- **Pathfinding** (exploring all possibilities).
- **Cycle detection** and **connected components**.
- Recursive backtracking (e.g., mazes, puzzles).

---

## **🧠 Where It Helps**

- 🌐 Network traversal & shortest path algorithms (BFS).
- 🔁 Cycle detection & connected components (DFS).
- 🧭 Maze and pathfinding problems.
- 🔎 Web crawling and dependency graphs.
- 🧩 Building recommendation systems or analyzing relationships.

---

## **✅ Takeaways**

- **BFS → Queue-based → Layer-by-layer exploration.**
- **DFS → Stack/Recursion → Deep exploration before backtracking.**
- Core foundations for advanced topics like:
    - Dijkstra’s Algorithm
    - Topological Sorting
    - Connected Components
    - Minimum Spanning Trees

---

## **🏋️ Practice Problems**

1. BFS and DFS Traversal of a Graph
2. Count Connected Components
3. Detect Cycle in Undirected / Directed Graph
4. Clone Graph
5. Shortest Path in Unweighted Graph

---