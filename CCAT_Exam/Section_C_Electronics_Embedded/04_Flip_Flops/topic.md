# Topic: Flip-Flops (Sequential Circuits)
# Section C — Electronics & Embedded

---

## What to Read
https://www.geeksforgeeks.org/flip-flop-types-their-conversion-and-applications/

---

## What is a Flip-Flop?
A memory element that stores 1 bit. Output depends on current input AND previous state (sequential, not just combinational).

Triggered by clock edge (rising or falling).

---

## STEP 1: SR Flip-Flop (Set-Reset)
| S | R | Q (next) | Comment |
|---|---|----------|---------|
| 0 | 0 | Q (no change) | Hold state |
| 0 | 1 | 0 | Reset |
| 1 | 0 | 1 | Set |
| 1 | 1 | X (invalid) | Forbidden state |

Problem: S=1, R=1 is undefined → improved by JK flip-flop

---

## STEP 2: D Flip-Flop (Data / Delay)
| D | Q (next) |
|---|----------|
| 0 | 0        |
| 1 | 1        |

Simplest — output follows input on clock edge.
Used in: registers, data storage, shift registers.

---

## STEP 3: JK Flip-Flop (Most Versatile)
| J | K | Q (next) | Comment |
|---|---|----------|---------|
| 0 | 0 | Q (no change) | Hold |
| 0 | 1 | 0 | Reset |
| 1 | 0 | 1 | Set |
| 1 | 1 | Q' (toggle) | Toggle — fixes SR problem |

JK is the most commonly asked flip-flop in exams.

---

## STEP 4: T Flip-Flop (Toggle)
| T | Q (next) |
|---|----------|
| 0 | Q (no change) |
| 1 | Q' (toggle)   |

Used in: counters, frequency dividers.
T = 1 toggles output on every clock edge → divides frequency by 2.

---

## Key Differences

| FF | Problem Solved | Main Use |
|----|----------------|----------|
| SR | Basic storage | Simple latch |
| D  | Eliminates undefined state | Registers |
| JK | Eliminates SR's forbidden state | General purpose |
| T  | Simplified JK with J=K=T | Counters |

---

## Practice Links

IndiaBIX Flip-Flops:
https://www.indiabix.com/digital-electronics/flip-flops/

GFG Flip-Flops:
https://www.geeksforgeeks.org/flip-flop-types-their-conversion-and-applications/

---

## Target
Memorize truth tables of all 4 flip-flops.
Do 20 flip-flop MCQs on IndiaBIX.
