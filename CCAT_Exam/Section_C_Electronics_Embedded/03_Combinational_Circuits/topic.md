# Topic: Combinational Circuits
# Section C — Electronics & Embedded

---

## What to Read
https://www.geeksforgeeks.org/combinational-circuits/

---

## STEP 1: Half Adder
Adds 2 single bits
- Sum = A XOR B
- Carry = A AND B

| A | B | Sum | Carry |
|---|---|-----|-------|
| 0 | 0 | 0   | 0     |
| 0 | 1 | 1   | 0     |
| 1 | 0 | 1   | 0     |
| 1 | 1 | 0   | 1     |

---

## STEP 2: Full Adder
Adds 3 bits (A, B, Carry-in)
- Sum = A XOR B XOR Cin
- Carry-out = (A AND B) OR (Cin AND (A XOR B))

Used to build multi-bit binary adders.

---

## STEP 3: Multiplexer (MUX)
- Many inputs → 1 output
- Select lines choose which input goes to output
- 2:1 MUX has 2 inputs, 1 select line
- 4:1 MUX has 4 inputs, 2 select lines
- 2^n inputs need n select lines

Use: data selector, implement Boolean functions

---

## STEP 4: Demultiplexer (DEMUX)
- 1 input → Many outputs
- Opposite of MUX
- Select lines route input to one of N outputs

---

## STEP 5: Encoder
- 2^N inputs → N output lines
- Converts one active input to binary code
- Example: 8:3 encoder (8 inputs, 3 output bits)

---

## STEP 6: Decoder
- N input lines → 2^N outputs
- Only one output active at a time
- Example: 3:8 decoder (3 inputs, 8 outputs)
- Used in memory addressing, display drivers

---

## Practice Links

IndiaBIX Combinational Circuits:
https://www.indiabix.com/digital-electronics/combinational-circuits/

GFG Combinational Circuits:
https://www.geeksforgeeks.org/combinational-circuits/

---

## Target
Do 20 combinational circuit MCQs on IndiaBIX.
