# Module 6: RTOS — Question Bank + Study Guide

## Where to Study
| Resource | URL |
|---|---|
| Sanfoundry RTOS MCQs | https://www.sanfoundry.com/rtos-questions-answers/ |
| FreeRTOS Official Docs | https://www.freertos.org/Documentation/RTOS_book.html |
| Fastbit EBA (YouTube) | FreeRTOS on STM32 — hands on |
| "Real-Time Concepts for Embedded Systems" — Qing Li | Best conceptual book |

---

## Topic 1: Task States

**Q1.** Draw and explain the task state machine in RTOS.
```
         xTaskCreate()
              |
           [Ready] ←──────────────────────────────┐
              |  (scheduler picks it)              |
              ↓                                    |
          [Running] ── vTaskDelay() / wait ──→ [Blocked]
              |         semaphore/queue           |
              |  vTaskSuspend()               unblocked
              ↓                                    |
         [Suspended] ←──────────────────────────────┘
              |  vTaskResume()
              ↑──────────────────
```

---

## Topic 2: Scheduling

**Q2.** What is preemptive scheduling?
**Answer:** Higher-priority task immediately preempts (interrupts) a lower-priority running task. Lower-priority task goes back to Ready state.

**Q3.** What is round-robin scheduling?
**Answer:** Tasks of equal priority share CPU time in time slices (ticks). Each gets a fixed time quantum before the next runs.

**Q4.** What is cooperative scheduling?
**Answer:** A running task must explicitly yield CPU (`taskYIELD()` or blocking call). No involuntary preemption. Simpler but risky — one bad task can starve others.

---

## Topic 3: Semaphore vs Mutex (MOST ASKED!)

| Feature | Semaphore | Mutex |
|---|---|---|
| Ownership | No owner | Has owner (task that locked it) |
| Use case | Signaling / counting resources | Mutual exclusion (protecting shared resource) |
| Release | Any task can release | Only owner can release |
| Recursive | No | Yes (recursive mutex) |
| Priority inheritance | No | Yes (prevents priority inversion) |
| Binary semaphore | Yes (0 or 1) | Similar to binary semaphore |
| Counting semaphore | Yes (0 to N) | No |

**Q5.** Can a semaphore be released by a task that didn't acquire it?
**Answer:** Yes — semaphore has no ownership. Any task (or ISR) can give/release a semaphore. This is key for ISR-to-task signaling.

**Q6.** Can a mutex be released by a different task?
**Answer:** No — mutex has ownership. Only the task that took (locked) it can give (release) it.

---

## Topic 4: Priority Inversion (VERY IMPORTANT)

**Q7.** Explain priority inversion with an example.
**Answer:**
- Task H (high priority), Task M (medium), Task L (low priority)
- Task L holds mutex M
- Task H tries to take mutex M → blocked
- Task M preempts Task L (M > L)
- Now M is running, but H is blocked waiting for L, which can't run!
- **Result:** High-priority task is effectively blocked by medium-priority task

**Fix:** Priority inheritance — L temporarily gets H's priority while holding the mutex, so M can't preempt L.

---

## Topic 5: Deadlock

**Q8.** What is deadlock? What are the 4 necessary conditions?
**Answer:** Two or more tasks permanently blocked, each waiting for a resource held by the other.

**4 Conditions (Coffman):**
1. **Mutual Exclusion** — resource can't be shared
2. **Hold and Wait** — task holds one resource while waiting for another
3. **No Preemption** — resource can't be forcibly taken
4. **Circular Wait** — circular chain of waiting (A waits for B, B waits for A)

**Prevent by:** breaking any one condition (e.g., always acquire mutexes in the same order to break circular wait)

---

## Topic 6: Message Queue

**Q9.** What is a message queue? When to use?
**Answer:** FIFO buffer for passing data between tasks (or ISR to task). Unlike semaphore, it transfers actual data, not just a signal.

```c
// FreeRTOS example
QueueHandle_t q = xQueueCreate(10, sizeof(int));

// Producer task
int val = 42;
xQueueSend(q, &val, portMAX_DELAY);

// Consumer task
int recv;
xQueueReceive(q, &recv, portMAX_DELAY);
```

---

## Topic 7: FreeRTOS Key APIs

**Q10.** Match FreeRTOS API to purpose:

| API | Purpose |
|---|---|
| `xTaskCreate()` | Create a new task |
| `vTaskDelay(ticks)` | Block task for N ticks |
| `xSemaphoreCreateMutex()` | Create mutex |
| `xSemaphoreTake(sem, timeout)` | Lock/wait on semaphore |
| `xSemaphoreGive(sem)` | Release semaphore |
| `xQueueCreate(len, size)` | Create message queue |
| `xQueueSend(q, &data, timeout)` | Send to queue |
| `xQueueReceive(q, &buf, timeout)` | Receive from queue |
| `vTaskSuspend(handle)` | Suspend a task |
| `vTaskResume(handle)` | Resume suspended task |

---

## Topic 8: Stack Overflow in Tasks

**Q11.** How does FreeRTOS detect stack overflow?
**Answer:** Two methods:
1. **Method 1:** Check stack pointer at context switch — if SP outside valid range, call `vApplicationStackOverflowHook()`
2. **Method 2:** Fill stack with known pattern (0xA5) at creation; periodically check if pattern is corrupted

---

## Checklist Before Exam
- [ ] 4 task states: Ready, Running, Blocked, Suspended
- [ ] Preemptive vs Cooperative scheduling
- [ ] Semaphore vs Mutex — 5 differences
- [ ] Semaphore: no ownership, any task can release
- [ ] Mutex: has ownership, only owner releases
- [ ] Priority inversion — scenario + fix (priority inheritance)
- [ ] Deadlock — 4 Coffman conditions
- [ ] Message queue — FIFO, transfers data
- [ ] FreeRTOS: `xTaskCreate`, `vTaskDelay`, semaphore APIs
- [ ] Stack overflow detection methods
