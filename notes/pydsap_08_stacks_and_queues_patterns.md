**Programmer:** python_scripts (Abhijith Warrier)

**NOTES ON SOLVING LINEAR ORDER & REVERSAL PROBLEMS USING STACKS & QUEUES. 🐍📦**

**Stacks** and **Queues** are linear data structures that follow specific order principles for adding and removing elements.

They are essential in recursion, parsing, BFS/DFS, scheduling, and expression evaluation problems.

---

## ✨ When to Use

- When order of processing matters (LIFO or FIFO).
- When you need **reversal**, **tracking**, or **processing elements in sequence**.
- Common in **DFS/BFS**, **expression evaluation**, **undo operations**, and **sliding window** problems.

---

## ⚡ Stack (LIFO — Last In, First Out)

- Think of a **plate stack** — last plate placed is the first removed.
- Used in **recursion**, **backtracking**, **bracket validation**, and **reverse traversal**.

---

## 🧱 Queue (FIFO — First In, First Out)

- Think of a **waiting line** — first person in line is served first.
- Used in **scheduling**, **BFS**, **task pipelines**, and **stream processing**.

---

## 📝 Example 1 — Valid Parentheses (Stack)

*Use a stack to ensure brackets are properly opened and closed.*

```python
def is_valid_parentheses(s: str) -> bool:
    stack = []
    mapping = {')': '(', ']': '[', '}': '{'}
    for ch in s:
        if ch in mapping.values():
            stack.append(ch)
        elif ch in mapping:
            if not stack or stack.pop() != mapping[ch]:
                return False
    return not stack

print(is_valid_parentheses("({[]})"))  # Output: True
```

---

## 📝 Example 2 — Evaluate Reverse Polish Notation (Stack)

*Evaluate postfix expressions where operators come after operands.*

```python
def eval_rpn(tokens):
    stack = []
    for token in tokens:
        if token not in "+-*/":
            stack.append(int(token))
        else:
            b, a = stack.pop(), stack.pop()
            if token == '+': stack.append(a + b)
            elif token == '-': stack.append(a - b)
            elif token == '*': stack.append(a * b)
            elif token == '/': stack.append(int(a / b))
    return stack.pop()

print(eval_rpn(["2", "1", "+", "3", "*"]))  # Output: 9
```

---

## 📝 Example 3 — Implement Queue using Two Stacks

*Two stacks can simulate a FIFO queue by reversing order.*

```python
class MyQueue:
    def __init__(self):
        self.stack_in = []
        self.stack_out = []

    def push(self, x: int):
        self.stack_in.append(x)

    def pop(self) -> int:
        if not self.stack_out:
            while self.stack_in:
                self.stack_out.append(self.stack_in.pop())
        return self.stack_out.pop()

    def peek(self) -> int:
        if not self.stack_out:
            while self.stack_in:
                self.stack_out.append(self.stack_in.pop())
        return self.stack_out[-1]

    def empty(self) -> bool:
        return not self.stack_in and not self.stack_out

# Example
q = MyQueue()
q.push(1)
q.push(2)
print(q.peek())  # Output: 1
print(q.pop())   # Output: 1
```

---

## ✅ Key Takeaways

- **Stack → LIFO** → Used for recursion, backtracking, undo/redo, expression parsing.
- **Queue → FIFO** → Used for BFS, scheduling, buffering, real-time streams.
- You can build a **queue from two stacks** or a **stack from two queues**.

---

## 🏋️ Practice Problems

1. Valid Parentheses (Stack).
2. Evaluate Reverse Polish Notation.
3. Implement Queue using Stacks.
4. Daily Temperatures (Monotonic Stack).
5. Sliding Window Maximum (Queue / De-queue).

---