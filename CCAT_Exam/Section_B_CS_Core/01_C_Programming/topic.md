# Topic: C Programming — Complete CCAT Level
# Section B — CS Core | Highest Weight Topic

---

## Study Order (follow exactly)

---

### STEP 1: Variables, Data Types, Format Specifiers
Read: https://www.geeksforgeeks.org/c/variables-in-c/
Read: https://www.geeksforgeeks.org/c/data-types-in-c/
Read: https://www.geeksforgeeks.org/c/basic-input-and-output-in-c/

Must know:
- int = 4 bytes, char = 1 byte, float = 4 bytes, double = 8 bytes
- Format specifiers: %d (int), %c (char), %f (float), %s (string), %u (unsigned), %ld (long)
- Signed range of int (32-bit): -2147483648 to 2147483647
- unsigned int range: 0 to 4294967295

Practice: https://www.indiabix.com/c-programming/data-types/

---

### STEP 2: Operators
Read: https://www.geeksforgeeks.org/c/operators-in-c/

Must know:
- Pre-increment (++x): increment THEN use
- Post-increment (x++): use THEN increment
- Ternary: condition ? true_val : false_val
- sizeof operator: sizeof(int) = 4, sizeof('A') = 4 (char literal is int in C!)
- Operator precedence (left to right vs right to left)

Practice: https://www.indiabix.com/c-programming/operators/

---

### STEP 3: Control Flow (if/else, switch, loops)
Read: https://www.geeksforgeeks.org/c/decision-making-in-c/
Read: https://www.geeksforgeeks.org/c/c-loops/

Must know:
- switch: only int and char cases, break needed to stop fall-through
- for loop: all 3 parts optional — for(;;) = infinite loop
- do-while: executes at least once

Practice: https://www.indiabix.com/c-programming/control-instructions/

---

### STEP 4: Functions
Read: https://www.geeksforgeeks.org/c/c-functions/
Read: https://www.geeksforgeeks.org/c/parameter-passing-techniques-in-c-cpp/
Read: https://www.geeksforgeeks.org/c/c-recursion/

Must know:
- Call by value: changes inside function don't affect original
- Call by reference (via pointer): changes affect original
- Recursion: base case + recursive case
- static function: visible only in current file

Practice: https://www.indiabix.com/c-programming/functions/

---

### STEP 5: Arrays and Strings
Read: https://www.geeksforgeeks.org/c/c-arrays/
Read: https://www.geeksforgeeks.org/c/strings-in-c/
Read: https://www.geeksforgeeks.org/c/string-functions-in-c/

Must know:
- Array index starts at 0
- Array name = pointer to first element
- strlen("Hello") = 5 (excludes null)
- sizeof("Hello") = 6 (includes null terminator \0)
- strcpy, strcmp, strcat, strlen — usage and return values
- strcmp returns 0 if equal, <0 if s1<s2, >0 if s1>s2

Practice:
https://www.indiabix.com/c-programming/arrays/
https://www.indiabix.com/c-programming/strings/

---

### STEP 6: Pointers — MOST IMPORTANT
Read: https://www.geeksforgeeks.org/c/c-pointers/
Read: https://www.geeksforgeeks.org/c/pointer-arithmetics-in-c-with-examples/
Read: https://www.geeksforgeeks.org/c/c-pointer-to-pointer-double-pointer/
Read: https://www.geeksforgeeks.org/c/function-pointer-in-c/
Read: https://www.geeksforgeeks.org/c/const-qualifier-in-c/

Must know:
- int *p = &a → p holds address of a, *p gives value at that address
- p+1 moves by sizeof(int) = 4 bytes, NOT by 1 byte
- const int *p → value is const, pointer can change
- int *const p → pointer is const, value can change
- void *p → generic pointer, must cast before dereferencing
- NULL pointer → points to address 0, dereferencing causes segfault

Practice:
https://www.indiabix.com/c-programming/pointers/

---

### STEP 7: Storage Classes and Memory
Read: https://www.geeksforgeeks.org/c/storage-classes-in-c/
Read: https://www.geeksforgeeks.org/c/memory-layout-of-c-program/
Read: https://www.geeksforgeeks.org/c/dynamic-memory-allocation-in-c-using-malloc-calloc-free-and-realloc/
Read: https://www.geeksforgeeks.org/c/what-is-memory-leak-how-can-we-avoid/

Must know memory segments:
| Segment | Stores | Example |
|---------|--------|---------|
| Text    | Compiled code | Function instructions |
| Data    | Initialized globals/statics | int x = 5; (global) |
| BSS     | Uninitialized globals/statics | int x; (global) |
| Stack   | Local variables, function calls | int x = 5; (inside main) |
| Heap    | Dynamic allocation | malloc() |

Storage classes:
- auto: default for local variables, dies after function returns
- static (local): retains value between calls, initialized once
- extern: declared here, defined in another file
- register: hint to store in CPU register, cannot take address

---

### STEP 8: Structures, Unions, Sizeof
Read: https://www.geeksforgeeks.org/c/structures-c/
Read: https://www.geeksforgeeks.org/c/structure-member-alignment-padding-and-data-packing/
Read: https://www.geeksforgeeks.org/c/c-unions/

Must know sizeof calculation with padding:
- Members aligned to their own size
- struct { char a; int b; char c; } → size = 12 (not 6)
  → 1 byte (a) + 3 padding + 4 bytes (b) + 1 byte (c) + 3 padding = 12
- union size = size of largest member

Practice: https://www.indiabix.com/c-programming/structures/

---

### STEP 9: Preprocessor and Macros
Read: https://www.geeksforgeeks.org/c/cc-preprocessors/
Read: https://www.geeksforgeeks.org/c/macros-and-its-types-in-c-cpp/

Must know:
- #define MAX(a,b) ((a)>(b)?(a):(b)) → always parenthesize!
- Without parens: #define SQ(x) x*x → SQ(3+2) = 3+2*3+2 = 11, not 25
- Macros have no type safety, no scope
- #ifdef / #ifndef for conditional compilation (include guards)

---

### STEP 10: Bitwise Operators
Read: https://www.geeksforgeeks.org/c/bitwise-operators-in-c-cpp/

Must know output prediction:
- 5 & 3 = 1 (0101 & 0011 = 0001)
- 5 | 3 = 7 (0101 | 0011 = 0111)
- 5 ^ 3 = 6 (0101 ^ 0011 = 0110)
- ~5 = -6 (bitwise NOT, two's complement)
- 5 << 1 = 10 (shift left = multiply by 2)
- 20 >> 2 = 5 (shift right = divide by 4)

---

## Output Prediction Practice (Do Daily — Most Common in CCAT)
https://www.indiabix.com/c-programming/output-of-c-programs/

All C topics combined:
https://www.indiabix.com/c-programming/questions-and-answers/

Video: Neso Academy C playlist
https://www.youtube.com/playlist?list=PLBlnK6fEyqRggZZgYpPMUxdY1CYkZtARR

---

## Daily Target
- 20 C output prediction questions per day (IndiaBIX)
- This single practice gives highest CCAT score improvement
