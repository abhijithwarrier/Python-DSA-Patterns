**Programmer:** python_scripts (Abhijith Warrier)

**NOTES ON TRACKING CONNECTED COMPONENTS USING UNION–FIND. 🐍🔗**

The **Disjoint Set** (also called **Union–Find**) data structure efficiently keeps track of **connected components** in a graph.

It answers two core questions very fast:

- Are two elements in the **same group**?
- Can we **merge** two groups?

Union–Find is heavily used in **graph connectivity**, **network problems**, and **minimum spanning tree algorithms**.

---

## **✨ Core Operations**

- **Find(x)** → returns the representative (parent) of element x
- **Union(x, y)** → merges the sets containing x and y
- **Connected(x, y)** → checks if both belong to the same set

---

## **⚡ Why Union–Find is Fast**

Two key optimizations make it extremely efficient:

1. **Path Compression**
    
    During find, nodes directly point to the root.
    
2. **Union by Rank / Size**
    
    Smaller trees are attached under larger ones.
    

With both optimizations:

> Time complexity ≈ **almost O(1)** per operation (amortized)
> 

---

## **📝 Example 1 — Basic Union–Find Structure**

*Track parent relationships between elements.*

```jsx
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0] * n

    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])  # path compression
        return self.parent[x]

    def union(self, x, y):
        rootX = self.find(x)
        rootY = self.find(y)

        if rootX == rootY:
            return

        # union by rank
        if self.rank[rootX] < self.rank[rootY]:
            self.parent[rootX] = rootY
        elif self.rank[rootX] > self.rank[rootY]:
            self.parent[rootY] = rootX
        else:
            self.parent[rootY] = rootX
            self.rank[rootX] += 1
```

---

## **📝 Example 2 — Detect Cycle in an Undirected Graph**

*If two nodes already share the same root, adding an edge creates a cycle.*

```jsx
def has_cycle(edges, n):
    uf = UnionFind(n)

    for u, v in edges:
        if uf.find(u) == uf.find(v):
            return True
        uf.union(u, v)

    return False

edges = [(0,1), (1,2), (2,3), (3,1)]
print("Cycle Exists:", has_cycle(edges, 4))
# Output: True
```

---

## **🧠 Where It Helps**

- 🔗 Detecting cycles in undirected graphs
- 🌐 Finding connected components
- 🛣️ Kruskal’s Minimum Spanning Tree
- 🧩 Dynamic connectivity problems
- 👥 Grouping / clustering problems
- 🧱 Network & social graph analysis

---

## **⚠️ When NOT to Use**

- When relationships change direction frequently (directed graphs)
- When full traversal or ordering is required
- When graph is very small (overkill)

---

## **✅ Takeaways**

- Union–Find efficiently manages **groups of connected elements**
- Path compression + union by rank = near constant time
- Essential for **graph connectivity & MST problems**
- One of the most powerful yet simple DSA tools

---

## **🏋️ Practice Problems**

1. Number of Connected Components
2. Detect Cycle in Undirected Graph
3. Redundant Connection
4. Kruskal’s Minimum Spanning Tree
5. Accounts Merge

---