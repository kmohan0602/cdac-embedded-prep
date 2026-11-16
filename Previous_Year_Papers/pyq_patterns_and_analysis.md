# Previous Year Question Papers — CDAC DESD

## Important Note
Official CDAC DESD exam papers are NOT publicly released by CDAC.
This file compiles:
1. Questions reported by past students (Quora, Reddit, Telegram)
2. Pattern analysis from coaching institutes
3. Most frequently tested topics

---

## Reported Question Patterns (from past batches)

### From C Programming (most frequent)

**Batch 2023 reported:**
- "What is the output?" — pointer arithmetic with arrays (5-6 questions)
- `sizeof(struct)` with padding — 2 questions
- `volatile` — when to use (MCQ)
- `static` variable behavior across function calls
- Macro with side effects — `MAX(x++, y++)`

**Batch 2022 reported:**
- `const int *p` vs `int *const p` — which can be changed
- Memory leak detection — which code snippet leaks
- `fork()` — how many times "hello" prints
- Bitwise operations — predict output

---

### From Embedded C (frequent)

- "Write code to set bit 5 of a register at address 0x40020014"
- "Why is volatile used with hardware registers?"
- "What is the difference between SPI and I2C?"
- "Explain ISR best practices" (descriptive — 5 marks)
- "What does a watchdog timer do?"

---

### From RTOS (frequent)

- "Explain priority inversion with an example"
- "Difference between semaphore and mutex — with ownership"
- "4 conditions of deadlock"
- "Task states in FreeRTOS — draw state diagram"
- "What happens when two tasks of same priority run?"

---

### From Linux (moderate)

- "What is a zombie process?"
- "Difference between pipe and named pipe"
- "`fork()` return value — what does parent get, what does child get?"
- "What signal is sent by Ctrl+C?"
- "`chmod 755` — explain permissions"

---

### From Device Drivers (moderate)

- "Why use `copy_to_user` instead of direct pointer access?"
- "Major number vs minor number"
- "Difference between tasklet and workqueue"
- "What is `ioctl` used for?"

---

## Where to Find Actual Papers

### Online Communities
1. **Quora** — Search: "CDAC DESD exam questions 2022 2023"
2. **Telegram** — Search groups: "CDAC embedded", "CDAC DESD preparation"
3. **GitHub** — Search: "CDAC DESD question bank"
4. **YouTube** — Search: "CDAC DESD exam experience" (students share paper patterns)

### Coaching Institutes with Mock Papers
- **Maven Silicon** (Bangalore) — specialized embedded coaching, has mock tests
- **Emertxe** (Bangalore) — embedded systems prep, practice papers
- **Vector Institute** (Pune/Bangalore) — VLSI + embedded, question banks

### Direct Links to Try
- https://www.mavensemiconductor.com (search resources section)
- https://emertxe.com (blogs section)

---

## Year-wise Topic Frequency (estimated from reports)

| Topic | 2021 | 2022 | 2023 | Trend |
|---|---|---|---|---|
| C Pointers | High | High | High | Constant |
| Volatile/ISR | Medium | High | High | Increasing |
| RTOS semaphore/mutex | Medium | Medium | High | Increasing |
| Linux process | Medium | Medium | Medium | Stable |
| ARM architecture | Low | Medium | Medium | Increasing |
| Device Drivers | Low | Low | Medium | Increasing |
| Protocols (SPI/I2C/UART) | Medium | Medium | High | Increasing |
