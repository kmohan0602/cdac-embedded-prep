# Module 2: Data Structures — Question Bank + Study Guide

## Where to Study
| Resource | URL |
|---|---|
| Sanfoundry DS MCQs | https://www.sanfoundry.com/data-structure-questions-answers/ |
| GeeksforGeeks DS | https://www.geeksforgeeks.org/data-structures/ |
| Neso Academy (YouTube) | DS playlist — arrays, linked lists, trees |
| IndiaBIX DS | https://www.indiabix.com/data-structure/questions-and-answers/ |

---

## Topic 1: Arrays & Strings

**Q1.** What is the output?
```c
char str[] = "Hello";
printf("%d", strlen(str));
printf("%d", sizeof(str));
```
**Answer:** `5` and `6` — `strlen` excludes null, `sizeof` includes null terminator

---

**Q2.** Reverse a string in-place (write code).
```c
void reverse(char *s) {
    int l = 0, r = strlen(s) - 1;
    while (l < r) {
        char t = s[l]; s[l] = s[r]; s[r] = t;
        l++; r--;
    }
}
```

---

## Topic 2: Linked List

**Q3.** Reverse a singly linked list (write code — very common!).
```c
Node* reverse(Node* head) {
    Node *prev = NULL, *curr = head, *next = NULL;
    while (curr) {
        next = curr->next;
        curr->next = prev;
        prev = curr;
        curr = next;
    }
    return prev;
}
```

---

**Q4.** Detect a cycle in a linked list. What algorithm?
**Answer:** Floyd's cycle detection (slow/fast pointer — tortoise and hare).

---

**Q5.** What is the time complexity of inserting at the beginning of a singly linked list?
**Answer:** O(1)

---

## Topic 3: Stack & Queue

**Q6.** Implement stack using array — push, pop, peek.
```c
int stack[100], top = -1;
void push(int x) { stack[++top] = x; }
int pop()        { return stack[top--]; }
int peek()       { return stack[top]; }
```

**Q7.** What is the output of this stack operation?
```
Push 1, Push 2, Push 3, Pop, Push 4, Pop, Pop
```
**Answer:** Pops: `3`, `4`, `2` (LIFO order)

---

## Topic 4: Trees

**Q8.** Write inorder, preorder, postorder traversal (conceptual — know the pattern).
- **Inorder:** Left → Root → Right (gives sorted order for BST)
- **Preorder:** Root → Left → Right
- **Postorder:** Left → Right → Root

**Q9.** Height of binary tree = ?
**Answer:** `1 + max(height(left), height(right))`

---

## Topic 5: Sorting — Time Complexity

| Algorithm | Best | Avg | Worst | Space |
|---|---|---|---|---|
| Bubble Sort | O(n) | O(n²) | O(n²) | O(1) |
| Selection Sort | O(n²) | O(n²) | O(n²) | O(1) |
| Insertion Sort | O(n) | O(n²) | O(n²) | O(1) |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | O(n) |
| Quick Sort | O(n log n) | O(n log n) | O(n²) | O(log n) |
| Heap Sort | O(n log n) | O(n log n) | O(n log n) | O(1) |

**Q10.** Which sorting algorithm is stable?
**Answer:** Merge Sort, Insertion Sort, Bubble Sort. Quick Sort and Heap Sort are NOT stable.

---

## Checklist Before Exam
- [ ] `strlen` vs `sizeof` for strings
- [ ] Linked list reverse — write from memory
- [ ] Floyd's cycle detection
- [ ] Stack push/pop using array
- [ ] Inorder/Preorder/Postorder — output from a given tree
- [ ] Time complexity of all 6 sorting algorithms
- [ ] BST insert, search, delete concept
