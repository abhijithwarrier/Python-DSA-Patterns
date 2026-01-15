**Programmer:** python_scripts (Abhijith Warrier)

**NOTES ON FAST PREFIX SEARCH & STRING STORAGE USING TRIES. 🐍🌲**

A **Trie** (pronounced *try*) is a tree-like data structure used to store and search **strings efficiently**, especially when dealing with **prefixes**.

Instead of storing whole words, a Trie stores characters **node by node**, sharing common prefixes.

This makes Tries ideal for **autocomplete**, **dictionary search**, and **prefix matching problems**.

---

## **✨ When to Use**

- When you need **fast prefix lookups**.
- When searching words from a **large dictionary**.
- When checking if a word or prefix exists repeatedly.
- When multiple strings share common prefixes.

---

## **⚡ Why Trie is Efficient**

- Search complexity depends on **word length**, not number of words.
- Shared prefixes reduce redundant storage.
- Prefix queries are extremely fast.

Time complexity:

- Insert → **O(L)**
- Search → **O(L)**
- Prefix search → **O(L)**
    
    (where L = length of the word)
    

---

## **🧩 Trie Structure**

Each Trie node contains:

- A **dictionary of children** (character → next node)
- A flag to indicate **end of word**

---

## **📝 Example 1 — Basic Trie Node & Insert**

*Build the structure and insert words character by character.*

```jsx
class TrieNode:
    def __init__(self):
        self.children = {}
        self.is_end = False

class Trie:
    def __init__(self):
        self.root = TrieNode()

    def insert(self, word):
        node = self.root
        for ch in word:
            if ch not in node.children:
                node.children[ch] = TrieNode()
            node = node.children[ch]
        node.is_end = True
```

---

## **📝 Example 2 — Search for a Word**

*Traverse character by character and check end-of-word.*

```jsx
    def search(self, word):
        node = self.root
        for ch in word:
            if ch not in node.children:
                return False
            node = node.children[ch]
        return node.is_end
```

---

## **📝 Example 3 — Prefix Search (Starts With)**

*Check whether any word starts with the given prefix.*

```jsx
    def starts_with(self, prefix):
        node = self.root
        for ch in prefix:
            if ch not in node.children:
                return False
            node = node.children[ch]
        return True
```

---

## **🧠 Where It Helps**

- 🔤 Autocomplete & search suggestions
- 📚 Spell checkers & dictionaries
- 🔎 Prefix-based search (e.g., “all words starting with ‘pre’”)
- 🧩 Word search problems
- 🗂️ Storing large vocabularies efficiently

---

## **⚠️ Limitations**

- Higher memory usage than hash sets
- Not ideal for very short or random strings
- Requires careful memory management for large alphabets

---

## **✅ Takeaways**

- Tries are optimized for **string & prefix problems**
- Operations run in **O(length of word)**
- Perfect for autocomplete & dictionary-based tasks
- One of the most elegant string data structures in DSA

---

## **🏋️ Practice Problems**

1. Implement Trie (Insert, Search, Prefix)
2. Word Search II
3. Design Add and Search Words Data Structure
4. Replace Words
5. Longest Word in Dictionary

---