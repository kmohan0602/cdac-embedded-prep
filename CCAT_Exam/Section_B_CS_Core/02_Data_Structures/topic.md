# Topic: Data Structures — Complete CCAT Level
# Section B — CS Core

---

## Study Order (follow exactly)

---

### STEP 1: Arrays
Read: https://www.geeksforgeeks.org/dsa/array-data-structure-guide/

Must know:
- Access: O(1), Search: O(n), Insert/Delete: O(n)
- 2D array row-major vs column-major storage
- Array passed to function as pointer (changes affect original)

---

### STEP 2: Linked List
Read: https://www.geeksforgeeks.org/dsa/singly-linked-list-tutorial/
Read: https://www.geeksforgeeks.org/dsa/doubly-linked-list/

Must know:
- Insert at head: O(1), Insert at tail: O(n), Search: O(n)
- Singly: one next pointer. Doubly: prev + next pointers
- Reversing singly linked list: 3-pointer technique (prev, curr, next)
- Detecting cycle: Floyd's algorithm (slow + fast pointer)

```
Reverse linked list (know by heart):
Node *prev=NULL, *curr=head, *next=NULL;
while(curr) {
    next = curr->next;
    curr->next = prev;
    prev = curr;
    curr = next;
}
return prev;
```

---

### STEP 3: Stack
Read: https://www.geeksforgeeks.org/dsa/stack-data-structure/

Must know:
- LIFO — Last In First Out
- Operations: push, pop, peek — all O(1)
- Applications: function call stack, undo operation, balanced parentheses
- Balanced parentheses check using stack

---

### STEP 4: Queue
Read: https://www.geeksforgeeks.org/dsa/queue-data-structure/

Must know:
- FIFO — First In First Out
- Enqueue (rear), Dequeue (front) — O(1)
- Circular queue — avoids wasted space
- Deque (double-ended queue): insert/delete at both ends

---

### STEP 5: Trees
Read: https://www.geeksforgeeks.org/dsa/introduction-to-tree-data-structure/
Read: https://www.geeksforgeeks.org/dsa/introduction-to-binary-search-tree/

Must know traversals (memorize output for given tree):
- Inorder (Left-Root-Right) → gives sorted order for BST
- Preorder (Root-Left-Right) → used for tree copy
- Postorder (Left-Right-Root) → used for tree deletion

BST property:
- Left subtree < Root < Right subtree
- Search/Insert/Delete: O(log n) average, O(n) worst (skewed)

---

### STEP 6: Sorting — Memorize Complexities
Read: https://www.geeksforgeeks.org/dsa/sorting-algorithms/

| Algorithm      | Best       | Average    | Worst      | Space  | Stable |
|----------------|------------|------------|------------|--------|--------|
| Bubble Sort    | O(n)       | O(n²)      | O(n²)      | O(1)   | Yes    |
| Selection Sort | O(n²)      | O(n²)      | O(n²)      | O(1)   | No     |
| Insertion Sort | O(n)       | O(n²)      | O(n²)      | O(1)   | Yes    |
| Merge Sort     | O(n log n) | O(n log n) | O(n log n) | O(n)   | Yes    |
| Quick Sort     | O(n log n) | O(n log n) | O(n²)      | O(log n)| No   |
| Heap Sort      | O(n log n) | O(n log n) | O(n log n) | O(1)   | No     |

Key facts:
- Merge sort: always O(n log n), needs extra space O(n)
- Quick sort: worst case O(n²) when pivot is always min/max
- Heap sort: in-place (O(1) space), not stable
- Stable means equal elements maintain original order

---

### STEP 7: Hashing
Read: https://www.geeksforgeeks.org/dsa/hashing-data-structure/

Must know:
- Hash function maps key to index
- Collision resolution:
  - Chaining: linked list at each bucket
  - Open addressing: linear probing, quadratic probing, double hashing
- Average case: O(1) for insert/search/delete

---

## Practice Links

IndiaBIX Data Structures:
https://www.indiabix.com/data-structure/questions-and-answers/

GFG DS Practice (topic-wise quiz):
https://www.geeksforgeeks.org/explore?category=Arrays
https://www.geeksforgeeks.org/explore?category=Linked+List
https://www.geeksforgeeks.org/explore?category=Stack
https://www.geeksforgeeks.org/explore?category=Queue
https://www.geeksforgeeks.org/explore?category=Tree

Video: Neso Academy DS playlist
https://www.youtube.com/playlist?list=PLBlnK6fEyqRh-iy1G8vXDaL7OYHEcYGaV

---

## Daily Target
- Do 15 DS MCQs per day on IndiaBIX
- Write linked list reverse code from memory — once a day
