# Module 5: ARM Architecture — Question Bank + Study Guide

## Where to Study
| Resource | URL |
|---|---|
| Sanfoundry ARM MCQs | https://www.sanfoundry.com/arm-microcontroller-questions-answers/ |
| ARM Developer Docs | https://developer.arm.com/documentation |
| Fast Bit Embedded (YouTube) | ARM Cortex-M architecture deep dive |
| "ARM System Developer's Guide" — Sloss | Best book for architecture |

---

## Topic 1: ARM Cortex-M Variants

| Core | Key Feature |
|---|---|
| Cortex-M0/M0+ | Smallest, ultra-low power, 32-bit, no FPU |
| Cortex-M3 | More instructions, hardware divide |
| Cortex-M4 | DSP instructions, optional FPU |
| Cortex-M7 | High performance, dual-issue pipeline |

---

## Topic 2: Registers

**Q1.** How many general-purpose registers does ARM Cortex-M have?
**Answer:** 16 registers: R0–R12 (general purpose), R13 (SP Stack Pointer), R14 (LR Link Register), R15 (PC Program Counter)

**Q2.** What is the Link Register (LR)?
**Answer:** R14 stores the return address when a function is called (`BL` instruction). When function returns (`BX LR`), execution jumps back to caller.

**Q3.** What is the Program Counter (PC)?
**Answer:** R15 holds address of next instruction to execute. Writing to PC causes a branch (jump).

---

## Topic 3: ARM vs Thumb Instruction Sets

**Q4.** What is the difference between ARM and Thumb instruction sets?
**Answer:**
- ARM: 32-bit fixed-width instructions — more features, faster execution
- Thumb: 16-bit instructions — smaller code size, better for memory-constrained devices
- Thumb-2: Mix of 16-bit and 32-bit — best of both (used in Cortex-M)

Cortex-M only supports Thumb/Thumb-2 (no ARM 32-bit mode).

---

## Topic 4: Pipeline

**Q5.** ARM classic (ARM7) has a 3-stage pipeline. What are the stages?
**Answer:** Fetch → Decode → Execute

**Q6.** Why is PC ahead by 8 bytes on ARM7?
**Answer:** Due to 3-stage pipeline, when instruction is executing, PC is already fetching 2 instructions ahead (2 × 4 bytes = 8 bytes ahead).

---

## Topic 5: Exception/Interrupt Handling

**Q7.** What is NVIC?
**Answer:** Nested Vectored Interrupt Controller — ARM Cortex-M hardware block that manages:
- Interrupt priority levels
- Enabling/disabling interrupts
- Nested interrupt support (higher priority can preempt lower)

**Q8.** What is the vector table?
**Answer:** Table at the start of flash memory containing addresses of all exception/interrupt handlers. First entry = initial stack pointer value, second = reset handler address.

**Q9.** What happens on reset in ARM Cortex-M?
**Answer:**
1. Load initial SP from vector table[0]
2. Jump to Reset_Handler (vector table[1])
3. Reset_Handler copies `.data` to RAM, zeros `.bss`, calls `main()`

---

## Topic 6: AAPCS (Calling Convention)

**Q10.** Which registers are caller-saved vs callee-saved in ARM AAPCS?
**Answer:**
- **Caller-saved (scratch):** R0–R3, R12 — function can trash these
- **Callee-saved:** R4–R11 — function must save/restore if used
- R0–R3: argument passing and return values

---

## Topic 7: Endianness

**Q11.** What is little-endian vs big-endian?
**Answer:**
- **Little-endian:** LSB stored at lowest address (ARM default, x86)
- **Big-endian:** MSB stored at lowest address (network byte order)

Example: `0x12345678` stored at address 0x100:
- Little-endian: `78 56 34 12` at addresses 100,101,102,103
- Big-endian: `12 34 56 78`

---

## Topic 8: Load-Store Architecture

**Q12.** What is a Load-Store architecture?
**Answer:** Operations are only performed on registers, not directly on memory. To operate on memory data:
1. Load from memory to register (`LDR R0, [R1]`)
2. Perform operation (`ADD R0, R0, #1`)
3. Store back to memory (`STR R0, [R1]`)

Contrast with CISC (x86) where you can do `ADD [mem], 1` directly.

---

## Checklist Before Exam
- [ ] Cortex-M0 vs M3 vs M4 key differences
- [ ] R13 = SP, R14 = LR, R15 = PC
- [ ] ARM vs Thumb vs Thumb-2
- [ ] Cortex-M only uses Thumb/Thumb-2
- [ ] NVIC purpose
- [ ] Vector table — what it contains
- [ ] Reset sequence: SP load → Reset_Handler → main
- [ ] R0-R3 = args/return, R4-R11 = callee-saved
- [ ] Little-endian = LSB at lowest address
- [ ] Load-Store architecture — no direct memory ops
