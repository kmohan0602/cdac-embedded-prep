# Section C — Electronics & Embedded Study Guide
# For DESD specialization track in CCAT

---

## What Section C Tests (DESD Track)
- Basic Electronics (Digital logic, gates, flip-flops)
- Microprocessors and Microcontrollers (8085/8051 basics)
- Embedded C basics (volatile, memory-mapped I/O)
- Communication protocols (UART, SPI, I2C — conceptual only)
- Number systems (binary, hex, octal conversions)

Note: Section C is CCAT-level — conceptual MCQs, not deep coding.

---

## PART 1: Number Systems and Digital Basics

### STEP 1: Number Systems
Read: https://www.geeksforgeeks.org/number-system-and-base-conversions/

Must know:
- Binary ↔ Decimal conversion
- Binary ↔ Hex conversion
- Octal ↔ Decimal conversion
- 1's complement and 2's complement (for negative numbers)

Practice: https://www.indiabix.com/digital-electronics/number-systems-and-codes/

---

### STEP 2: Logic Gates
Read: https://www.geeksforgeeks.org/logic-gates/

Must know all 7 gates:
| Gate | Symbol | Output |
|------|--------|--------|
| AND  | A·B    | 1 only when both inputs are 1 |
| OR   | A+B    | 1 when at least one input is 1 |
| NOT  | Ā      | Inverts the input |
| NAND | ¬(A·B) | NOT AND — universal gate |
| NOR  | ¬(A+B) | NOT OR — universal gate |
| XOR  | A⊕B    | 1 when inputs are different |
| XNOR | ¬(A⊕B) | 1 when inputs are same |

Practice: https://www.indiabix.com/digital-electronics/logic-gates/

---

### STEP 3: Boolean Algebra and Laws
Read: https://www.geeksforgeeks.org/boolean-algebra/

Must know:
- De Morgan's theorem: ¬(A·B) = Ā+B̄ and ¬(A+B) = Ā·B̄
- Idempotent, complement, absorption laws

---

### STEP 4: Combinational Circuits
Read: https://www.geeksforgeeks.org/combinational-circuits/

Topics:
- Half adder, Full adder
- Multiplexer (MUX), Demultiplexer (DEMUX)
- Encoder, Decoder

Practice: https://www.indiabix.com/digital-electronics/combinational-circuits/

---

### STEP 5: Flip-Flops (Sequential Circuits)
Read: https://www.geeksforgeeks.org/flip-flop-types-their-conversion-and-applications/

Must know:
- SR flip-flop (Set-Reset)
- D flip-flop (Data)
- JK flip-flop (most versatile)
- T flip-flop (Toggle)
- Truth tables of each

Practice: https://www.indiabix.com/digital-electronics/flip-flops/

---

## PART 2: Microprocessor and Microcontroller Basics

### STEP 6: Microprocessor vs Microcontroller
Read: https://www.geeksforgeeks.org/difference-between-microprocessor-and-microcontroller/

Must know:
- Microprocessor: CPU only, needs external RAM/ROM/peripherals (e.g., Intel 8085)
- Microcontroller: CPU + RAM + ROM + peripherals on one chip (e.g., 8051, AVR, ARM)

---

### STEP 7: 8051 Microcontroller Basics
Read: https://www.geeksforgeeks.org/8051-microcontroller/

Must know:
- 128 bytes internal RAM
- 4KB internal ROM
- 4 ports (P0, P1, P2, P3)
- SFRs — Special Function Registers control peripherals
- 2 timers, 1 serial port, 5 interrupt sources

---

### STEP 8: Memory Types
Read: https://www.geeksforgeeks.org/ram-full-form/

Must know:
| Memory | Full Form | Volatile? | Use |
|--------|-----------|-----------|-----|
| RAM    | Random Access Memory | Yes | Program data at runtime |
| ROM    | Read Only Memory | No | Firmware storage |
| EEPROM | Electrically Erasable Programmable ROM | No | Config data |
| Flash  | Flash Memory | No | Program storage in MCU |
| SRAM   | Static RAM | Yes | Faster, used in cache |
| DRAM   | Dynamic RAM | Yes | Slower, needs refresh |

---

## PART 3: Embedded C Concepts (CCAT Level)

### STEP 9: volatile keyword
Read: https://www.geeksforgeeks.org/volatile-qualifier-in-c/

Must know: prevents compiler from optimizing reads/writes.
Used for hardware registers and ISR-shared variables.

---

### STEP 10: Communication Protocols (Conceptual only for CCAT)
- UART: https://www.geeksforgeeks.org/universal-asynchronous-receiver-transmitter-uart/
  → Asynchronous, 2 wires (TX/RX), baud rate
- SPI: https://www.geeksforgeeks.org/serial-peripheral-interface-spi/
  → Synchronous, 4 wires (MOSI/MISO/SCLK/SS), faster
- I2C: https://www.geeksforgeeks.org/i2c-communication-protocol/
  → Synchronous, 2 wires (SDA/SCL), multi-device on same bus

---

## PART 4: Basic Analog Electronics (Light — just concepts)

### STEP 11: Diode and Transistor
Read: https://www.geeksforgeeks.org/transistor/

Must know:
- Diode: allows current in one direction only
- BJT transistor: NPN and PNP, used as switch or amplifier
- Transistor as switch: saturation (ON), cutoff (OFF)

---

## Practice Links for Section C

IndiaBIX Digital Electronics (all topics):
- https://www.indiabix.com/digital-electronics/questions-and-answers/

IndiaBIX Number Systems:
- https://www.indiabix.com/digital-electronics/number-systems-and-codes/

IndiaBIX Logic Gates:
- https://www.indiabix.com/digital-electronics/logic-gates/

IndiaBIX Flip-Flops:
- https://www.indiabix.com/digital-electronics/flip-flops/

---

## Section C Study Schedule (1 week)

| Day | Topics |
|-----|--------|
| Day 1 | Number systems — binary, hex, 2's complement |
| Day 2 | Logic gates — all 7, truth tables, De Morgan's |
| Day 3 | Combinational circuits — adder, MUX, decoder |
| Day 4 | Flip-flops — SR, D, JK, T |
| Day 5 | Microprocessor vs Microcontroller, 8051 basics |
| Day 6 | Memory types, volatile, UART/SPI/I2C concepts |
| Day 7 | Full IndiaBIX digital electronics practice |
