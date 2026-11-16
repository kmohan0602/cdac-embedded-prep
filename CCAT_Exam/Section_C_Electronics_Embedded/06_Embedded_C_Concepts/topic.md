# Topic: Embedded C Concepts (CCAT Level)
# Section C — Electronics & Embedded

---

## What to Read
https://www.geeksforgeeks.org/difference-between-c-and-embedded-c/
https://www.geeksforgeeks.org/volatile-qualifier-in-c/

---

## STEP 1: volatile Keyword
Read: https://www.geeksforgeeks.org/volatile-qualifier-in-c/

What it does: Tells compiler NOT to cache the variable in a register.
Every read/write goes directly to memory.

When to use (3 cases — memorize these):
1. Memory-mapped hardware registers
2. Variables modified in ISR (Interrupt Service Routine)
3. Variables shared between threads

Without volatile — compiler bug:
```c
int flag = 0;
// ISR sets flag = 1
while(!flag) { }  // compiler may optimize this to infinite loop!
```

Fix: volatile int flag = 0;

---

## STEP 2: Memory-Mapped I/O
Read: https://www.geeksforgeeks.org/memory-mapped-io-and-isolated-io/

Concept: Hardware registers have fixed memory addresses.
You write to the address to control hardware.

```c
// Access hardware register at address 0x40020014
#define GPIOA_ODR (*(volatile unsigned int*)0x40020014)
GPIOA_ODR |= (1 << 5);  // Set pin PA5 HIGH
```

Breaking it down:
- 0x40020014 → register address
- (unsigned int*) → treat as pointer to 32-bit register
- volatile → always read/write from actual memory
- * → dereference to access the value at that address

---

## STEP 3: Bitwise Operations (CCAT level)
Read: https://www.geeksforgeeks.org/bitwise-operators-in-c-cpp/

4 patterns — memorize:
```c
reg |= (1 << n);    // Set bit n
reg &= ~(1 << n);   // Clear bit n
reg ^= (1 << n);    // Toggle bit n
if (reg & (1 << n)) // Check if bit n is set
```

---

## STEP 4: Communication Protocols (Conceptual for CCAT)

### UART
Read: https://www.geeksforgeeks.org/universal-asynchronous-receiver-transmitter-uart/
- Asynchronous (no clock wire)
- 2 wires: TX (transmit), RX (receive)
- Parameters: baud rate (speed), data bits, parity, stop bits
- Common config: 9600 8N1 (9600 baud, 8 data, No parity, 1 stop)
- 1 byte = 10 bits on wire (1 start + 8 data + 1 stop)

### SPI
Read: https://www.geeksforgeeks.org/serial-peripheral-interface-spi/
- Synchronous (has clock)
- 4 wires: MOSI, MISO, SCLK, SS/CS
- Full duplex (send and receive simultaneously)
- One SS pin per slave
- Faster than I2C

### I2C
Read: https://www.geeksforgeeks.org/i2c-communication-protocol/
- Synchronous (has clock)
- 2 wires: SDA (data), SCL (clock)
- Open-drain lines (need external pull-up resistors)
- 7-bit addressing → up to 127 devices on same bus
- ACK/NACK after every byte
- Slower than SPI, fewer wires

### Quick Comparison
| Feature | UART | SPI | I2C |
|---------|------|-----|-----|
| Wires | 2 | 4 | 2 |
| Clock | No | Yes | Yes |
| Speed | Medium | Fast | Slow |
| Devices | 2 (point-to-point) | Few | Many (127) |
| Duplex | Full | Full | Half |

---

## STEP 5: ISR Basics
Read: https://www.geeksforgeeks.org/interrupts-and-its-types/

What is an interrupt: Signal to CPU to stop current work and handle urgent event
ISR (Interrupt Service Routine): Function that handles the interrupt

ISR rules for CCAT:
- Keep short and fast
- No printf, sleep, or blocking calls
- Variables shared with ISR must be volatile
- Set a flag in ISR, process in main

---

## Practice Links

Sanfoundry Embedded C MCQs:
https://www.sanfoundry.com/embedded-c-questions-answers/

IndiaBIX Digital Electronics (covers protocols):
https://www.indiabix.com/digital-electronics/questions-and-answers/

---

## Target
Understand volatile + bitwise operations deeply — 10 MCQs each.
Know SPI vs I2C vs UART comparison table by heart.
