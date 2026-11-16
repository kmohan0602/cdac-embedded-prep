# Full Mock Test — CDAC DESD Embedded Systems
# Time: 2.5 hours | Total: 60 marks | Each Q = 1 mark

---

## Section A: C Programming (20 Questions)

**Q1.** What is the output?
```c
int a = 5, b = 10;
printf("%d", a++ + ++b);
```
a) 15  b) 16  c) 17  d) Undefined
**Answer: b) 16** — `a++` uses 5 (post), `++b` uses 11 (pre) → 5+11=16

---

**Q2.** `const int *p` means:
a) pointer is constant  
b) value pointed to is constant  
c) both are constant  
d) neither is constant  
**Answer: b)**

---

**Q3.** What is the output?
```c
int arr[] = {1, 2, 3, 4, 5};
int *p = arr + 2;
printf("%d %d", *p, *(p-1));
```
a) 3 2  b) 2 3  c) 3 1  d) Error  
**Answer: a) 3 2**

---

**Q4.** `sizeof` of this struct (32-bit system)?
```c
struct s { char a; int b; char c; };
```
a) 6  b) 9  c) 12  d) 8  
**Answer: c) 12** — padding: 3 after `a`, 3 after `c`

---

**Q5.** `sizeof` of this union?
```c
union u { int a; char b; double c; };
```
a) 4  b) 8  c) 13  d) 1  
**Answer: b) 8**

---

**Q6.** What is the output?
```c
void count() {
    static int x = 0;
    printf("%d ", ++x);
}
int main() { count(); count(); count(); }
```
a) 1 1 1  b) 0 1 2  c) 1 2 3  d) Error  
**Answer: c) 1 2 3**

---

**Q7.** Which segment stores uninitialized global variables?
a) Stack  b) Heap  c) BSS  d) Data  
**Answer: c) BSS**

---

**Q8.** What is the output?
```c
#define SQ(x) x*x
printf("%d", SQ(3+2));
```
a) 25  b) 11  c) 10  d) Error  
**Answer: b) 11** — expands to `3+2*3+2 = 11`

---

**Q9.** Set bit 4 of variable `reg` without affecting other bits:
a) `reg = reg | 4`  
b) `reg = reg | (1 << 4)`  
c) `reg = reg + 4`  
d) `reg = reg | 0x04`  
**Answer: b)**

---

**Q10.** Clear bit 3 of variable `reg`:
a) `reg &= ~(1 << 3)`  
b) `reg |= (1 << 3)`  
c) `reg ^= (1 << 3)`  
d) `reg -= (1 << 3)`  
**Answer: a)**

---

**Q11.** What does `volatile` prevent?
a) Memory leaks  
b) Compiler optimization of variable reads/writes  
c) Stack overflow  
d) Integer overflow  
**Answer: b)**

---

**Q12.** What is a dangling pointer?
a) Pointer to NULL  
b) Pointer to freed/deallocated memory  
c) Uninitialized pointer  
d) Pointer to pointer  
**Answer: b)**

---

**Q13.** Which function pointer declaration is correct for `int add(int, int)`?
a) `int *fp(int, int)`  
b) `int (*fp)(int, int)`  
c) `(*int fp)(int, int)`  
d) `int (fp*)(int, int)`  
**Answer: b)**

---

**Q14.** `malloc(0)` returns:
a) NULL always  
b) Implementation-defined (NULL or unique pointer)  
c) Crash  
d) Allocates 1 byte  
**Answer: b)**

---

**Q15.** What is output?
```c
int x = 0xFF;
printf("%d", x >> 4);
```
a) 15  b) 16  c) 240  d) 0  
**Answer: a) 15** — `0xFF >> 4` = `0x0F` = 15

---

**Q16.** `extern int x;` means:
a) Define and allocate `x`  
b) Declare `x` defined in another file  
c) Make `x` global  
d) Initialize `x` to 0  
**Answer: b)**

---

**Q17.** Which is true about `register` variables?
a) Stored in heap  
b) Cannot take address with `&`  
c) Faster than `volatile`  
d) Persists between function calls  
**Answer: b)**

---

**Q18.** Output?
```c
int a = 5;
int *p = &a;
*p = 10;
printf("%d", a);
```
a) 5  b) 10  c) Address  d) Error  
**Answer: b) 10**

---

**Q19.** `strcpy(dst, src)` vs `strncpy(dst, src, n)` — which is safer?
a) `strcpy` — simpler  
b) `strncpy` — limits copy size, prevents overflow  
c) Both are equal  
d) Neither is safe  
**Answer: b)**

---

**Q20.** What is output of `printf("%d", sizeof('A'))` on 32-bit system?
a) 1  b) 2  c) 4  d) 8  
**Answer: c) 4** — character literal is `int` in C (not `char`)

---

## Section B: Embedded C & RTOS (20 Questions)

**Q21.** Why must ISR variables be declared `volatile`?
a) To make them faster  
b) To prevent compiler from caching them in registers  
c) To put them in BSS segment  
d) To allow them to be shared across files  
**Answer: b)**

---

**Q22.** Memory-mapped register at 0x40020000. Write to set bit 2:
a) `*0x40020000 |= 4`  
b) `(*(volatile int*)0x40020000) |= (1<<2)`  
c) `0x40020000 |= (1<<2)`  
d) `WRITE(0x40020000, 2)`  
**Answer: b)**

---

**Q23.** UART 8N1 at 9600 baud. Time to transmit 1 byte (10 bits)?
a) ~0.1 ms  
b) ~1.04 ms  
c) ~10 ms  
d) ~0.01 ms  
**Answer: b) ~1.04 ms** — 1/9600 × 10 ≈ 1.04 ms

---

**Q24.** I2C uses:
a) 4 wires  b) 3 wires  c) 2 wires  d) 1 wire  
**Answer: c) 2 wires (SDA, SCL)**

---

**Q25.** SPI uses:
a) 2 wires  b) 3 wires  c) 4 wires  d) 1 wire  
**Answer: c) 4 wires (MOSI, MISO, SCLK, SS)**

---

**Q26.** Which IPC is FASTEST?
a) Pipe  b) Socket  c) Shared Memory  d) Message Queue  
**Answer: c) Shared Memory**

---

**Q27.** Semaphore vs Mutex — which has ownership?
a) Semaphore  b) Mutex  c) Both  d) Neither  
**Answer: b) Mutex**

---

**Q28.** Priority inversion is prevented by:
a) Round-robin scheduling  
b) Priority inheritance  
c) Cooperative scheduling  
d) Increasing all task priorities  
**Answer: b)**

---

**Q29.** Which condition is NOT required for deadlock?
a) Mutual exclusion  
b) Priority inversion  
c) Hold and wait  
d) Circular wait  
**Answer: b) Priority inversion** — it's not a deadlock condition

---

**Q30.** FreeRTOS: `vTaskDelay(100)` blocks a task for:
a) 100 microseconds  
b) 100 milliseconds  
c) 100 RTOS ticks  
d) 1 second  
**Answer: c) 100 ticks** — tick period depends on `configTICK_RATE_HZ`

---

**Q31.** A task in RTOS moves from Running to which state on `vTaskDelay()`?
a) Ready  b) Suspended  c) Blocked  d) Terminated  
**Answer: c) Blocked**

---

**Q32.** Watchdog timer purpose:
a) Measure execution time  
b) Reset MCU if software hangs  
c) Clock the CPU  
d) Measure interrupt latency  
**Answer: b)**

---

**Q33.** Which is true about counting semaphore?
a) Max value is 1  
b) Can have value > 1  
c) Has task ownership  
d) Cannot be given from ISR  
**Answer: b)**

---

**Q34.** ISR should NOT:
a) Set a flag  
b) Clear an interrupt pending bit  
c) Call `printf()`  
d) Return IRQ_HANDLED  
**Answer: c) Call printf()**

---

**Q35.** Bootloader is stored at:
a) End of flash  
b) Heap  
c) Reset vector / beginning of flash  
d) RAM  
**Answer: c)**

---

**Q36.** In ARM Cortex-M, NVIC manages:
a) Memory allocation  
b) Interrupt priorities and enabling  
c) Clock configuration  
d) Stack size  
**Answer: b)**

---

**Q37.** Toggle bit 7 of register `PORT`:
a) `PORT |= 0x80`  
b) `PORT &= ~0x80`  
c) `PORT ^= (1 << 7)`  
d) `PORT = PORT | 128`  
**Answer: c)**

---

**Q38.** `SIGKILL` can be:
a) Caught and handled  
b) Blocked  
c) Ignored  
d) None of the above — cannot be caught/blocked/ignored  
**Answer: d)**

---

**Q39.** Little-endian: value `0x1234` stored at address 0x100:
a) `12 34` at 100, 101  
b) `34 12` at 100, 101  
c) Both same  
d) Depends on OS  
**Answer: b) 34 12** — LSB first

---

**Q40.** `volatile const int *p` means:
a) Read-only hardware register  
b) Writeable hardware register  
c) Constant pointer  
d) Local variable  
**Answer: a) Read-only hardware register** — `const` = no write, `volatile` = always read from memory

---

## Section C: Linux & Device Drivers (20 Questions)

**Q41.** `copy_to_user()` is needed because:
a) User space is slower  
b) Kernel cannot directly access user-space pointers safely  
c) It encrypts data  
d) `memcpy` doesn't work in kernel  
**Answer: b)**

---

**Q42.** `dmesg` command shows:
a) Disk usage  
b) Memory usage  
c) Kernel log messages  
d) Process list  
**Answer: c)**

---

**Q43.** Major number in device file identifies:
a) Device instance  
b) Driver  
c) File size  
d) Permissions  
**Answer: b)**

---

**Q44.** Tasklet vs Workqueue — which can sleep?
a) Tasklet  
b) Workqueue  
c) Both  
d) Neither  
**Answer: b) Workqueue**

---

**Q45.** `insmod` does:
a) List modules  
b) Load a kernel module  
c) Remove a module  
d) Show module info  
**Answer: b)**

---

**Q46.** `fork()` return value in child process:
a) PID of child  
b) PID of parent  
c) 0  
d) -1  
**Answer: c) 0**

---

**Q47.** Zombie process is:
a) Process consuming too much CPU  
b) Terminated process whose parent hasn't called wait()  
c) Orphan process  
d) Sleeping process  
**Answer: b)**

---

**Q48.** `/proc/cpuinfo` is located in:
a) Hard disk  
b) Virtual filesystem in memory  
c) `/etc`  
d) RAM disk  
**Answer: b)**

---

**Q49.** `ioctl` is used for:
a) File read/write  
b) Device-specific control commands  
c) Memory allocation  
d) Thread creation  
**Answer: b)**

---

**Q50.** Which IPC allows unrelated processes to communicate via filesystem?
a) Pipe  
b) Named Pipe (FIFO)  
c) Shared Memory  
d) Signal  
**Answer: b)**

---

**Q51.** `strace` command:
a) Traces function calls  
b) Traces system calls made by a process  
c) Shows static analysis  
d) Shows stack trace  
**Answer: b)**

---

**Q52.** `chmod 644 file` gives:
a) rwxr--r--  
b) rw-r--r--  
c) rwxrwxr--  
d) r--r--r--  
**Answer: b) rw-r--r--** — 6=rw, 4=r, 4=r

---

**Q53.** `MODULE_LICENSE("GPL")` is required because:
a) Legal requirement only  
b) Non-GPL modules may not use some kernel symbols  
c) It speeds up compilation  
d) Required for `insmod`  
**Answer: b)**

---

**Q54.** Platform driver is used when:
a) Device is on PCI bus  
b) Device is hardwired on SoC (no auto-discovery)  
c) Device has USB interface  
d) Networking devices  
**Answer: b)**

---

**Q55.** `request_irq()` registers:
a) System call  
b) Interrupt handler  
c) Device file  
d) Kernel thread  
**Answer: b)**

---

**Q56.** Orphan process is adopted by:
a) Grandparent process  
b) Shell  
c) init / systemd (PID 1)  
d) Kernel  
**Answer: c)**

---

**Q57.** `ldd binary` shows:
a) Last debug log  
b) Shared library dependencies  
c) Load address  
d) Linked device drivers  
**Answer: b)**

---

**Q58.** `$?` in shell script:
a) Number of arguments  
b) Script name  
c) Exit status of last command  
d) All arguments  
**Answer: c)**

---

**Q59.** Which signal is sent to a process when Ctrl+Z is pressed?
a) SIGTERM  
b) SIGSTOP  
c) SIGTSTP  
d) SIGKILL  
**Answer: c) SIGTSTP** — terminal stop, can be caught (unlike SIGSTOP)

---

**Q60.** `free_irq(irq, dev_id)` must be called with the SAME `dev_id` as `request_irq` because:
a) Performance optimization  
b) Identifies which handler to unregister (needed for shared IRQs)  
c) Kernel requirement for GPL  
d) Driver cleanup convention only  
**Answer: b)**

---

## Answer Key

| Q | A | Q | A | Q | A | Q | A |
|---|---|---|---|---|---|---|---|
| 1 | b | 16 | b | 31 | c | 46 | c |
| 2 | b | 17 | b | 32 | b | 47 | b |
| 3 | a | 18 | b | 33 | b | 48 | b |
| 4 | c | 19 | b | 34 | c | 49 | b |
| 5 | b | 20 | c | 35 | c | 50 | b |
| 6 | c | 21 | b | 36 | b | 51 | b |
| 7 | c | 22 | b | 37 | c | 52 | b |
| 8 | b | 23 | b | 38 | d | 53 | b |
| 9 | b | 24 | c | 39 | b | 54 | b |
| 10 | a | 25 | c | 40 | a | 55 | b |
| 11 | b | 26 | c | 41 | b | 56 | c |
| 12 | b | 27 | b | 42 | c | 57 | b |
| 13 | b | 28 | b | 43 | b | 58 | c |
| 14 | b | 29 | b | 44 | b | 59 | c |
| 15 | a | 30 | c | 45 | b | 60 | b |

---

## Scoring
- 50-60: Excellent — exam ready
- 40-49: Good — revise weak areas
- 30-39: Moderate — focus on C + Embedded + RTOS
- Below 30: Need more practice — start from question banks
