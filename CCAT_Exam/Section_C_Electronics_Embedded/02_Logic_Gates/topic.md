# Topic: Logic Gates
# Section C — Electronics & Embedded

---

## What to Read
https://www.geeksforgeeks.org/logic-gates/

---

## All 7 Gates — Truth Tables

### AND Gate (A · B)
| A | B | Out |
|---|---|-----|
| 0 | 0 | 0   |
| 0 | 1 | 0   |
| 1 | 0 | 0   |
| 1 | 1 | 1   |
Output = 1 only when BOTH inputs are 1

### OR Gate (A + B)
| A | B | Out |
|---|---|-----|
| 0 | 0 | 0   |
| 0 | 1 | 1   |
| 1 | 0 | 1   |
| 1 | 1 | 1   |
Output = 1 when AT LEAST ONE input is 1

### NOT Gate (Ā)
| A | Out |
|---|-----|
| 0 | 1   |
| 1 | 0   |
Inverts the input

### NAND Gate (Universal)
Output = NOT(A AND B) → opposite of AND
Output = 0 only when BOTH inputs are 1
→ Can implement ANY logic gate using only NAND gates

### NOR Gate (Universal)
Output = NOT(A OR B) → opposite of OR
Output = 1 only when BOTH inputs are 0
→ Can implement ANY logic gate using only NOR gates

### XOR Gate (A ⊕ B)
| A | B | Out |
|---|---|-----|
| 0 | 0 | 0   |
| 0 | 1 | 1   |
| 1 | 0 | 1   |
| 1 | 1 | 0   |
Output = 1 when inputs are DIFFERENT

### XNOR Gate (Equivalence)
Output = NOT(XOR) → 1 when inputs are SAME
| A | B | Out |
|---|---|-----|
| 0 | 0 | 1   |
| 0 | 1 | 0   |
| 1 | 0 | 0   |
| 1 | 1 | 1   |

---

## De Morgan's Theorem (MUST KNOW)
NOT(A AND B) = NOT(A) OR NOT(B)
NOT(A OR B)  = NOT(A) AND NOT(B)

Practical use: NAND(A,B) = OR(NOT A, NOT B)

---

## Boolean Laws
- A AND 0 = 0, A AND 1 = A
- A OR 0 = A, A OR 1 = 1
- A AND A = A, A OR A = A
- A AND NOT(A) = 0, A OR NOT(A) = 1

---

## Practice Links

IndiaBIX Logic Gates:
https://www.indiabix.com/digital-electronics/logic-gates/

GFG Boolean Algebra:
https://www.geeksforgeeks.org/boolean-algebra/

---

## Target
Memorize all 7 truth tables. Do 20 gate questions on IndiaBIX.
