# Module 1: C Programming — Question Bank + Study Guide

## Where to Study
| Resource | URL / Location |
|---|---|
| Sanfoundry C MCQs (1000 Qs) | https://www.sanfoundry.com/c-programming-questions-answers/ |
| IndiaBIX C Programming | https://www.indiabix.com/c-programming/questions-and-answers/ |
| GeeksforGeeks C Quiz | https://www.geeksforgeeks.org/c-programming-quiz/ |
| K&R Book Chapter 1-8 | Classic reference — pointers, structs, macros |
| Neso Academy (YouTube) | C Programming playlist |

---

## Topic 1: Pointers

### Must Know
- Pointer arithmetic, pointer to pointer (`**p`)
- `const int *p` vs `int * const p` vs `const int * const p`
- Function pointers — declaration and calling
- Array name as pointer — `a` vs `&a` vs `*a`
- `void *` — generic pointer, casting rules

### Question Bank

**Q1.** What is the output?
```c
int a = 10;
int *p = &a;
int **q = &p;
printf("%d %d %d", a, *p, **q);
```
**Answer:** `10 10 10`

---

**Q2.** What is the output?
```c
int arr[] = {10, 20, 30, 40};
int *p = arr;
printf("%d", *(p+2));
```
**Answer:** `30`

---

**Q3.** What is the difference between `const int *p` and `int * const p`?
**Answer:**
- `const int *p` → pointer can change, value pointed to cannot be changed
- `int * const p` → pointer cannot change (fixed address), value can be changed

---

**Q4.** What is the output?
```c
int arr[3] = {1, 2, 3};
printf("%d", *arr + 1);     // Line A
printf("%d", *(arr + 1));   // Line B
```
**Answer:** Line A → `2`, Line B → `2` (same result, different meaning)

---

**Q5.** What does this declare?
```c
void (*fp)(int, int);
```
**Answer:** `fp` is a pointer to a function that takes two `int` parameters and returns `void`.

---

## Topic 2: Memory Layout & Storage Classes

### Must Know
- Stack, Heap, Data (initialized), BSS (uninitialized), Text (code)
- `static` inside function — retains value between calls
- `extern` — declaration only, defined elsewhere
- `volatile` — prevents compiler optimization (critical for embedded)
- `register` — hint to store in CPU register

### Question Bank

**Q6.** Where is each variable stored?
```c
int g = 5;          // ?
static int s = 10;  // ?
int main() {
    int l = 20;     // ?
    int *p = malloc(sizeof(int)); // p on ?, *p on ?
}
```
**Answer:**
- `g` → Data segment (initialized global)
- `s` → Data segment (initialized static)
- `l` → Stack
- `p` (pointer variable) → Stack, `*p` (malloc'd memory) → Heap

---

**Q7.** What is the output?
```c
void counter() {
    static int count = 0;
    count++;
    printf("%d ", count);
}
int main() {
    counter(); counter(); counter();
}
```
**Answer:** `1 2 3`

---

**Q8.** Why is `volatile` important in embedded systems?
**Answer:** Tells compiler NOT to optimize away reads/writes to the variable. Without `volatile`, compiler may cache the value in a register and miss hardware register updates. Essential for:
- Memory-mapped hardware registers
- Variables modified in ISR (Interrupt Service Routines)
- Shared variables in multi-threaded code

---

## Topic 3: Structures, Unions, Bit Fields

### Must Know
- Structure padding and alignment rules
- `sizeof` struct — with and without `#pragma pack`
- Union — all members share same memory, size = size of largest member
- Bit fields — packing multiple values in a single byte

### Question Bank

**Q9.** What is `sizeof(s)`?
```c
struct s {
    char a;    // 1 byte
    int b;     // 4 bytes
    char c;    // 1 byte
};
```
**Answer:** `12` (not 6!) — padding: 3 bytes after `a`, 3 bytes after `c` for alignment

**To get 6:** use `#pragma pack(1)` or `__attribute__((packed))`

---

**Q10.** What is `sizeof(u)`?
```c
union u {
    int a;
    char b;
    double c;
};
```
**Answer:** `8` (size of largest member `double`)

---

**Q11.** What is the output?
```c
union u {
    int i;
    char c[4];
};
union u x;
x.i = 0x01020304;
printf("%x", x.c[0]);
```
**Answer:** On little-endian: `4`, on big-endian: `1`

---

## Topic 4: Preprocessor & Macros

### Must Know
- Macro pitfalls (no type safety, no semicolons, parenthesize!)
- `#ifdef`, `#ifndef`, `#define`, `#undef`
- Stringification `#` and token pasting `##`
- Inline functions vs macros

### Question Bank

**Q12.** What is wrong with this macro?
```c
#define SQUARE(x) x*x
int result = SQUARE(3+2);
```
**Answer:** Result is `3+2*3+2 = 11`, not `25`. Fix: `#define SQUARE(x) ((x)*(x))`

---

**Q13.** What is the output?
```c
#define MAX(a,b) ((a) > (b) ? (a) : (b))
int x = 5, y = 10;
printf("%d", MAX(x++, y++));
```
**Answer:** `11` — but `y` gets incremented **twice** (side effect bug in macro!)

---

## Topic 5: Bitwise Operations (CRITICAL for Embedded)

### Must Know
- Set bit: `reg |= (1 << n)`
- Clear bit: `reg &= ~(1 << n)`
- Toggle bit: `reg ^= (1 << n)`
- Check bit: `if (reg & (1 << n))`

### Question Bank

**Q14.** Set bit 3 of variable `x` without affecting other bits.
```c
x |= (1 << 3);
```

**Q15.** Clear bit 5 of variable `x`.
```c
x &= ~(1 << 5);
```

**Q16.** What is the output?
```c
int x = 0xAB;   // 1010 1011
printf("%d", x >> 2);
```
**Answer:** `42` (logical right shift: `0010 1010`)

---

## Topic 6: Output Prediction (Very Common)

**Q17.**
```c
int i = 0;
printf("%d %d %d", i++, i++, i++);
```
**Answer:** Undefined behavior — but most compilers print `2 1 0` (right to left evaluation)

---

**Q18.**
```c
int x = 5;
printf("%d", x << 1);
```
**Answer:** `10` (left shift by 1 = multiply by 2)

---

**Q19.**
```c
int x = -1;
printf("%u", x);
```
**Answer:** `4294967295` (UINT_MAX on 32-bit — two's complement of -1)

---

## Checklist Before Exam
- [ ] Pointer arithmetic (all combinations)
- [ ] `const` with pointers (4 cases)
- [ ] Memory segments — what goes where
- [ ] `sizeof` struct with padding
- [ ] Union behavior
- [ ] Macro pitfalls (parentheses, side effects)
- [ ] Bitwise set/clear/toggle/check
- [ ] `static`, `volatile`, `extern` behavior
- [ ] `malloc`/`free` — memory leak, dangling pointer
- [ ] Output prediction with `++`, `--`, bitwise ops
