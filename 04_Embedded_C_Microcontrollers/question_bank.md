# Module 4: Embedded C & Microcontrollers — Question Bank + Study Guide

## Where to Study
| Resource | URL |
|---|---|
| Sanfoundry Embedded C MCQs | https://www.sanfoundry.com/embedded-c-questions-answers/ |
| Sanfoundry 8051 MCQs | https://www.sanfoundry.com/8051-microcontroller-questions-answers/ |
| Fast Bit Embedded (YouTube) | ARM Cortex-M bare metal, registers, GPIO |
| Fastbit EBA (YouTube) | STM32, timers, UART, SPI, I2C |
| "Embedded C" — Michael Barr | Standard textbook |

---

## Topic 1: volatile keyword (MOST IMPORTANT)

**Q1.** Why is `volatile` critical in embedded systems?
**Answer:** Tells the compiler NOT to cache the variable in a register — always read/write directly from memory. Required when:
1. Variable is modified by hardware (memory-mapped register)
2. Variable is modified in an ISR
3. Variable is shared between threads

**Q2.** What is wrong with this code?
```c
int flag = 0;

void ISR_handler() {
    flag = 1;
}

int main() {
    while (!flag) {
        // wait
    }
    do_something();
}
```
**Answer:** Without `volatile`, compiler may optimize `while(!flag)` to `while(1)` since it sees `flag` never changes in `main`. Fix: `volatile int flag = 0;`

---

## Topic 2: Memory-Mapped I/O (CRITICAL)

**Q3.** What does this code do?
```c
#define GPIOA_ODR  (*(volatile unsigned int*)0x40020014)
GPIOA_ODR |= (1 << 5);
```
**Answer:** Sets bit 5 of the GPIO port A Output Data Register (turns on pin PA5). The cast to `volatile unsigned int*` treats address `0x40020014` as a hardware register.

**Q4.** Write code to read from hardware register at address `0x40000050`.
```c
#define REG (*(volatile unsigned int*)0x40000050)
unsigned int value = REG;
```

---

## Topic 3: Bit Manipulation (VERY COMMON)

**Q5.** Set bit 4, clear bit 2, toggle bit 6 of variable `reg`.
```c
reg |= (1 << 4);    // Set bit 4
reg &= ~(1 << 2);   // Clear bit 2
reg ^= (1 << 6);    // Toggle bit 6
```

**Q6.** Check if bit 3 is set.
```c
if (reg & (1 << 3)) { /* bit 3 is set */ }
```

**Q7.** Extract bits 4-7 (nibble) from a byte.
```c
unsigned char nibble = (reg >> 4) & 0x0F;
```

---

## Topic 4: ISR Rules

**Q8.** List 5 rules for writing a good ISR.
**Answer:**
1. Keep ISR as short as possible
2. No blocking calls (no `printf`, no `sleep`, no `malloc`)
3. Variables shared with ISR must be `volatile`
4. No floating-point operations (unless FPU saved/restored)
5. Disable/enable interrupts around critical sections if needed
6. Set a flag in ISR, process in main loop (deferred processing)

---

## Topic 5: Communication Protocols

### UART
- Asynchronous, no clock line
- 2 wires: TX and RX
- Parameters: baud rate, data bits (8), parity, stop bits
- Common baud rates: 9600, 115200

**Q9.** UART sends "A" (0x41 = 01000001). With 8N1 (8 data bits, no parity, 1 stop bit), how many bits total on wire?
**Answer:** 10 bits — 1 start + 8 data + 1 stop

### SPI
- Synchronous, 4 wires: MOSI, MISO, SCLK, SS/CS
- Full duplex
- Master-slave, can have multiple slaves (one SS per slave)
- Faster than I2C

### I2C
- Synchronous, 2 wires: SDA (data), SCL (clock)
- Open-drain lines (need pull-up resistors)
- Multi-master capable
- 7-bit addressing (up to 127 devices on same bus)
- ACK/NACK bit after each byte

**Q10.** When should you use SPI vs I2C?
**Answer:**
- SPI: High-speed, short distance, few devices (sensors, flash, displays)
- I2C: Lower speed, many devices on same bus, only 2 wires needed

### I2C Protocol Flow
```
START → 7-bit address + R/W bit → ACK → Data bytes → ACK → STOP
```

---

## Topic 6: Interrupts

**Q11.** What is interrupt latency?
**Answer:** Time from interrupt request to first instruction of ISR executing.

**Q12.** What is interrupt nesting? Is it safe?
**Answer:** Higher-priority interrupt preempts lower-priority ISR. Safe if ISR saves/restores context properly. ARM Cortex-M NVIC supports nested interrupts.

**Q13.** What is a watchdog timer?
**Answer:** Hardware timer that resets the MCU if software doesn't "kick" (reset) it within a set period. Used to recover from software hangs/crashes.

---

## Topic 7: 8051 Basics

**Q14.** What are SFRs (Special Function Registers)?
**Answer:** Registers mapped to specific memory addresses that control peripherals — TCON, TMOD (timers), IE (interrupt enable), P0-P3 (ports), SCON (serial).

**Q15.** 8051 has how much RAM and ROM?
**Answer:** 128 bytes internal RAM, 4KB internal ROM (varies by variant).

---

## Topic 8: Bootloader Concept

**Q16.** What is a bootloader in embedded systems?
**Answer:** Small program stored at a fixed memory address (reset vector) that runs first when MCU powers up. It:
1. Initializes hardware (clock, memory)
2. Checks for firmware update
3. Loads/jumps to main application

---

## Checklist Before Exam
- [ ] `volatile` — when and why (3 scenarios)
- [ ] Memory-mapped I/O — write to register at address
- [ ] Set/clear/toggle/check bit — all 4 operations
- [ ] ISR rules — at least 5 points
- [ ] UART parameters (baud, start/stop bit, parity)
- [ ] SPI 4 wires — MOSI, MISO, SCLK, SS
- [ ] I2C 2 wires — SDA, SCL, open-drain, ACK/NACK
- [ ] SPI vs I2C — when to use which
- [ ] Watchdog timer purpose
- [ ] Bootloader role
