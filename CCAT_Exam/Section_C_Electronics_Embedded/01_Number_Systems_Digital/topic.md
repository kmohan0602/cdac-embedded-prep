# Topic: Number Systems and Digital Basics
# Section C — Electronics & Embedded

---

## What to Read
https://www.geeksforgeeks.org/number-system-and-base-conversions/

---

## STEP 1: Number System Conversions

### Binary ↔ Decimal
Binary to Decimal: multiply each bit by 2^position (right to left from 0)
Example: 1011 = 1×2³ + 0×2² + 1×2¹ + 1×2⁰ = 8+0+2+1 = 11

Decimal to Binary: repeatedly divide by 2, read remainders bottom to top
Example: 13 → 13÷2=6 R1, 6÷2=3 R0, 3÷2=1 R1, 1÷2=0 R1 → 1101

### Binary ↔ Hexadecimal
Group 4 binary bits = 1 hex digit
0000=0, 0001=1, ..., 1001=9, 1010=A, 1011=B, 1100=C, 1101=D, 1110=E, 1111=F

Example: 1010 1111 = AF in hex

### Octal ↔ Binary
Group 3 binary bits = 1 octal digit
Example: 101 110 = 56 in octal

---

## STEP 2: 1's and 2's Complement

1's complement: flip all bits
Example: 1011 → 0100

2's complement (used for negative numbers): flip all bits + add 1
Example: 1011 → 0100 + 1 = 0101
This is how negative numbers are stored in computers.

-1 in 8-bit 2's complement = 11111111 (0xFF)
-128 in 8-bit 2's complement = 10000000

---

## Practice Links

IndiaBIX Number Systems:
https://www.indiabix.com/digital-electronics/number-systems-and-codes/

---

## Quick Reference Table
| Decimal | Binary | Hex | Octal |
|---------|--------|-----|-------|
| 0  | 0000 | 0 | 0  |
| 1  | 0001 | 1 | 1  |
| 5  | 0101 | 5 | 5  |
| 9  | 1001 | 9 | 11 |
| 10 | 1010 | A | 12 |
| 15 | 1111 | F | 17 |
| 16 | 10000| 10| 20 |

---

## Target
Do 20 number system conversion questions on IndiaBIX.
