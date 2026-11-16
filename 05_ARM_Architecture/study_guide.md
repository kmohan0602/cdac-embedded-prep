# ARM Architecture — Complete Study Guide (Basics to Advanced)
# Read topics IN THIS ORDER

---

## STEP 1: ARM Basics
1. ARM Processor — overview, features, RISC architecture
   https://www.geeksforgeeks.org/arm-processor-and-its-features/

2. RISC vs CISC — why ARM is RISC
   https://www.geeksforgeeks.org/computer-organization-risc-and-cisc/

   Key RISC properties:
   - Load-Store architecture (ops only on registers, not memory)
   - Fixed instruction length
   - Large number of registers

---

## STEP 2: ARM Cortex-M Variants
3. ARM Cortex-M series overview
   https://developer.arm.com/Processors/Cortex-M0
   https://developer.arm.com/Processors/Cortex-M3
   https://developer.arm.com/Processors/Cortex-M4

   Must know differences:
   | Core       | Key Feature                        |
   |------------|------------------------------------|
   | Cortex-M0  | Smallest, ultra-low power, no FPU  |
   | Cortex-M3  | Hardware divide, more instructions  |
   | Cortex-M4  | DSP instructions, optional FPU     |
   | Cortex-M7  | High performance, dual-issue        |

---

## STEP 3: Registers
4. ARM Cortex-M Registers
   https://developer.arm.com/documentation/ddi0337/e/programmer-s-model/registers

   Must know:
   - R0–R12: General purpose
   - R13 (SP): Stack Pointer
   - R14 (LR): Link Register — stores return address
   - R15 (PC): Program Counter — address of next instruction
   - xPSR: Program Status Register (flags: N, Z, C, V)

---

## STEP 4: ARM vs Thumb Instruction Sets
5. ARM instruction set overview
   https://www.geeksforgeeks.org/introduction-to-arm-instructions-set/

   Must know:
   - ARM mode: 32-bit instructions (more features)
   - Thumb mode: 16-bit instructions (smaller code)
   - Thumb-2: Mix of 16+32 bit (best of both)
   - Cortex-M ONLY supports Thumb/Thumb-2 (no 32-bit ARM mode)

---

## STEP 5: Pipeline
6. ARM Pipeline concept
   https://www.geeksforgeeks.org/arm7-tdmi-processor/

   Must know:
   - ARM7 (classic): 3 stages — Fetch → Decode → Execute
   - Cortex-M3/M4: 3-stage pipeline with branch prediction
   - Because of pipeline, PC is always ahead of current instruction

---

## STEP 6: Exception and Interrupt Handling
7. ARM Cortex-M Exception Model
   https://www.geeksforgeeks.org/exception-handling-arm-cortex-m/

8. NVIC (Nested Vectored Interrupt Controller)
   https://www.geeksforgeeks.org/nvic-nested-vectored-interrupt-controller/

   Must know:
   - NVIC manages interrupt priorities and enable/disable
   - Supports nested interrupts (higher priority preempts lower)
   - Each interrupt has a configurable priority level

9. Vector Table
   https://developer.arm.com/documentation/dui0552/a/the-cortex-m3-processor/exception-model/vector-table

   Must know:
   - Vector table starts at address 0x00000000 (start of flash)
   - Entry 0 = initial Stack Pointer value
   - Entry 1 = Reset_Handler address
   - Each entry = address of the exception handler function

---

## STEP 7: Reset Sequence
10. ARM Cortex-M Startup/Reset process
    https://www.geeksforgeeks.org/arm-cortex-m-startup-code/

    Reset sequence (memorize this):
    1. Load initial SP value from vector_table[0]
    2. Jump to Reset_Handler (vector_table[1])
    3. Reset_Handler copies .data section to RAM
    4. Reset_Handler zeros .bss section
    5. Calls main()

---

## STEP 8: AAPCS Calling Convention
11. ARM Procedure Call Standard (AAPCS)
    https://developer.arm.com/documentation/ihi0042/latest

    Must know:
    - R0–R3: Argument passing and return values
    - R0–R3, R12: Caller-saved (function can trash these)
    - R4–R11: Callee-saved (function must save/restore)
    - R14 (LR): Automatically saved by BL instruction

---

## STEP 9: Endianness
12. Little-endian vs Big-endian
    https://www.geeksforgeeks.org/little-and-big-endian-mystery/

    Must know:
    - ARM Cortex-M is little-endian by default
    - Little-endian: LSB stored at lowest address
    - Example: 0x12345678 → stored as 78 56 34 12 in memory

---

## Practice Links

Sanfoundry ARM MCQs (1000 questions):
- https://www.sanfoundry.com/arm-microcontroller-questions-answers/

Fast Bit Embedded Brain Academy (YouTube — bare metal ARM):
- https://www.youtube.com/@FastbitEmbeddedBrainAcademy/playlists

---

## Study Schedule for ARM (4 days)

| Day | Steps | Topics |
|-----|-------|--------|
| 1   | 1–3   | RISC basics, Cortex-M variants, registers |
| 2   | 4–5   | ARM vs Thumb, pipeline |
| 3   | 6–7   | NVIC, vector table, reset sequence |
| 4   | 8–9   | Calling convention, endianness + MCQ practice |
