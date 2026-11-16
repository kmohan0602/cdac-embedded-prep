# Topic: Microcontroller Basics
# Section C — Electronics & Embedded

---

## What to Read
https://www.geeksforgeeks.org/8051-microcontroller/
https://www.geeksforgeeks.org/difference-between-microprocessor-and-microcontroller/

---

## STEP 1: Microprocessor vs Microcontroller

| Feature | Microprocessor | Microcontroller |
|---------|----------------|-----------------|
| CPU | Yes | Yes |
| RAM | External | Built-in |
| ROM | External | Built-in |
| I/O Ports | External | Built-in |
| Peripherals | External | Built-in (timer, UART, ADC) |
| Example | Intel 8085, x86 | 8051, AVR, PIC, STM32 |
| Use | General computing | Embedded control systems |
| Cost | Higher | Lower |

---

## STEP 2: 8051 Microcontroller

Read: https://www.geeksforgeeks.org/8051-microcontroller/

Key specs:
- 8-bit CPU
- 128 bytes internal RAM
- 4 KB internal ROM (Program Memory)
- 4 I/O ports (P0, P1, P2, P3) — each 8 bits wide
- 2 Timers (Timer 0 and Timer 1)
- 1 Serial port (UART)
- 5 interrupt sources
- 32 I/O pins

SFRs (Special Function Registers) — control all peripherals:
| SFR | Function |
|-----|---------|
| P0–P3 | I/O port registers |
| TCON | Timer control |
| TMOD | Timer mode |
| IE | Interrupt enable |
| SCON | Serial control |
| ACC | Accumulator |
| PSW | Program status word (flags) |

---

## STEP 3: Memory Types (CCAT favorite)

| Memory | Volatile? | Writable at runtime? | Use |
|--------|-----------|----------------------|-----|
| SRAM | Yes | Yes | Fast cache, registers |
| DRAM | Yes | Yes | Main RAM in computers |
| ROM | No | No | Fixed firmware |
| PROM | No | Once (by programmer) | One-time programmable |
| EPROM | No | Yes (UV light erase) | Older firmware |
| EEPROM | No | Yes (byte-by-byte) | Config data |
| Flash | No | Yes (sector erase) | Modern MCU program storage |

Flash is used in modern microcontrollers (STM32, AVR) for program storage.
EEPROM is used for small config/calibration data.

---

## STEP 4: Basic MCU Concepts

Watchdog Timer:
- Hardware timer that resets MCU if not kicked periodically
- Prevents system hang
Read: https://www.geeksforgeeks.org/watchdog-timer/

ADC (Analog to Digital Converter):
- Converts real-world analog signals (temperature, voltage) to digital
- Resolution in bits: 8-bit ADC = 256 levels, 12-bit = 4096 levels

PWM (Pulse Width Modulation):
- Simulates analog output using digital signal
- Duty cycle = ON time / Period × 100%
- Used for motor speed control, LED dimming

---

## Practice Links

IndiaBIX Microcontrollers:
https://www.indiabix.com/digital-electronics/microprocessors/

Sanfoundry 8051 MCQs:
https://www.sanfoundry.com/8051-microcontroller-questions-answers/

---

## Target
Do 20 microcontroller MCQs.
Memorize 8051 specs (RAM, ROM, ports, timers, interrupts).
