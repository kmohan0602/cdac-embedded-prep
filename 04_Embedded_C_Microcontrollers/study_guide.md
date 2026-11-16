# Embedded C & Microcontrollers — Complete Study Guide (Basics to Advanced)
# Read topics IN THIS ORDER

---

## STEP 1: Embedded C Basics
1. Introduction to Embedded Systems
   https://www.geeksforgeeks.org/introduction-to-embedded-systems/

2. Difference between C and Embedded C
   https://www.geeksforgeeks.org/difference-between-c-and-embedded-c/

3. volatile keyword in Embedded C (MOST IMPORTANT)
   https://www.geeksforgeeks.org/volatile-qualifier-in-c/

   Must know 3 use cases:
   - Memory-mapped hardware registers
   - Variables modified in ISR
   - Shared variables between threads

---

## STEP 2: Memory-Mapped I/O (CRITICAL)
4. Memory-Mapped I/O concept
   https://www.geeksforgeeks.org/memory-mapped-io-and-isolated-io/

   Practice this pattern until it's automatic:
   #define REG (*(volatile unsigned int*)0x40020000)
   REG |= (1 << 5);   // Set bit 5 of hardware register

---

## STEP 3: Bitwise Operations for Embedded
5. Bitwise Operators — embedded context
   https://www.geeksforgeeks.org/bitwise-operators-in-c-cpp/

   4 patterns to memorize:
   Set bit n:    reg |= (1 << n)
   Clear bit n:  reg &= ~(1 << n)
   Toggle bit n: reg ^= (1 << n)
   Check bit n:  if (reg & (1 << n))

---

## STEP 4: Interrupts and ISR
6. Interrupts in Embedded Systems
   https://www.geeksforgeeks.org/interrupts-and-its-types/

7. ISR (Interrupt Service Routine) Rules — study this carefully
   https://www.geeksforgeeks.org/interrupt-service-routine-isr/

   5 ISR rules to remember:
   - Keep ISR short
   - No printf, no malloc, no blocking calls
   - Mark shared variables as volatile
   - Set a flag in ISR, process in main
   - No floating point (unless FPU context saved)

---

## STEP 5: Communication Protocols

8. UART Protocol (Universal Asynchronous Receiver/Transmitter)
   https://www.geeksforgeeks.org/universal-asynchronous-receiver-transmitter-uart/

   Key facts:
   - Asynchronous (no clock wire)
   - 2 wires: TX, RX
   - 8N1 = 8 data bits, No parity, 1 stop bit
   - 10 bits total per byte (1 start + 8 data + 1 stop)

9. SPI Protocol (Serial Peripheral Interface)
   https://www.geeksforgeeks.org/serial-peripheral-interface-spi/

   Key facts:
   - Synchronous, Full duplex
   - 4 wires: MOSI, MISO, SCLK, SS/CS
   - One SS pin per slave device

10. I2C Protocol (Inter-Integrated Circuit)
    https://www.geeksforgeeks.org/i2c-communication-protocol/

    Key facts:
    - Synchronous, Half duplex
    - 2 wires: SDA, SCL
    - Open-drain (needs pull-up resistors)
    - 7-bit addressing → up to 127 devices on same bus
    - ACK/NACK after every byte

---

## STEP 6: Microcontroller Basics — 8051

11. 8051 Microcontroller Architecture
    https://www.geeksforgeeks.org/8051-microcontroller/

12. 8051 Timers and Counters
    https://www.geeksforgeeks.org/timers-and-counters-in-8051-microcontroller/

13. 8051 Interrupts
    https://www.geeksforgeeks.org/interrupts-8051-microcontroller/

    Key facts:
    - 128 bytes internal RAM
    - 4KB internal ROM
    - SFRs (Special Function Registers) control peripherals

---

## STEP 7: Watchdog Timer
14. Watchdog Timer concept
    https://www.geeksforgeeks.org/watchdog-timer/

    Key fact: Resets MCU if software doesn't "kick" it within a timeout.
    Used to recover from software hang/crash.

---

## STEP 8: Bootloader
15. Bootloader in Embedded Systems
    https://www.geeksforgeeks.org/what-is-boot-loader/

    Key facts:
    - First code to run on MCU power-on
    - Stored at reset vector address
    - Initializes hardware → checks for update → jumps to application

---

## STEP 9: Sanfoundry Practice (1000 Questions)

Embedded C MCQs:
- https://www.sanfoundry.com/embedded-c-questions-answers/

8051 MCQs:
- https://www.sanfoundry.com/8051-microcontroller-questions-answers/

Communication Protocols MCQs:
- https://www.sanfoundry.com/computer-network-questions-answers-serial-communication-uart/

---

## YouTube Resources

Fast Bit Embedded (bare metal ARM, GPIO, UART, SPI, I2C):
- https://www.youtube.com/@FastbitEmbeddedBrainAcademy/playlists

Fastbit EBA (STM32 + FreeRTOS):
- https://www.youtube.com/c/FastbitEBA/playlists

---

## Study Schedule for Embedded C (7 days)

| Day | Steps | Topics |
|-----|-------|--------|
| 1   | 1–2   | Embedded C basics, volatile, memory-mapped I/O |
| 2   | 3     | Bitwise operations — drill until automatic |
| 3   | 4     | Interrupts, ISR rules |
| 4   | 5a    | UART — parameters, frame format |
| 5   | 5b–5c | SPI and I2C — wires, differences, when to use |
| 6   | 6–7   | 8051 architecture, watchdog timer |
| 7   | 8–9   | Bootloader + full Sanfoundry MCQ practice |
