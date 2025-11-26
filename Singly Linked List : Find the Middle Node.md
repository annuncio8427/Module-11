# 📚 Singly Linked List: Find the Middle Node of a Singly Linked List Using Recursion

This Python program demonstrates how to find the middle node of a singly linked list using recursion. The program calculates the middle element by utilizing two pointers, with one pointer moving one step at a time (slow) and the other moving two steps at a time (fast). When the fast pointer reaches the end of the list, the slow pointer will be at the middle node.

---

## 🎯 Aim

To write a Python program that:
- Creates a singly linked list.
- Uses recursion to find the middle node of the list.
- In case of an even number of nodes, it returns the second middle element.

---

## 🔵 Algorithm

1. **Node Class**:
   - Define a `Node` class to represent each node in the singly linked list. Each node has two attributes: `data` and `next`.

2. **LinkedList Class**:
   - Define a `LinkedList` class that manages the linked list with methods to:
     - `append(data)`: Add a new node to the end of the list.
     - `get_middle_recursive(slow, fast)`: A recursive helper function to find the middle node using two pointers (slow and fast).
     - `find_middle()`: A method to call the recursive function and return the middle node's data.

3. **Input**:
   - Take user input for the number of elements and their values.

4. **Output**:
   - Print the middle element of the linked list.

---

## 💻 Program

```python
class Node:
    def __init__(self, data):
        self.data = data
        self.next = None

class LinkedList:
    def __init__(self):
        self.head = None

    def append(self, data):
        new_node = Node(data)
        if self.head is None:
            self.head = new_node
            return
        temp = self.head
        while temp.next:
            temp = temp.next
        temp.next = new_node

    def get_middle_recursive(self, slow, fast):
        if fast is None or fast.next is None:
            return slow
        return self.get_middle_recursive(slow.next, fast.next.next)

    def find_middle(self):
        if self.head is None:
            return None
        return self.get_middle_recursive(self.head, self.head).data

n = int(input())

values = list(map(int, input().split()))

ll = LinkedList()

for v in values:
    ll.append(v)

print(ll.find_middle())
```

---

## 📤 Sample Input & Output

**Input:**
```
5
10 20 30 40 50
```

**Output:**
```
30
```

---

## ✅ Result

The program successfully:
- Creates a singly linked list
- Uses recursion to find the middle node
- Returns the correct middle element (30 for the list [10, 20, 30, 40, 50])
